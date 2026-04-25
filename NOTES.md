# 日本語フォント修正メモ

このメモは前回の Claude Code セッション（本家 `shuzijun/markdown-editor` での調査）からの引き継ぎ。新しいセッションはこのフォーク先 `hnishide/markdown-editor` で開始すること。

## 背景・課題

RubyMine でこのプラグインのマークダウンプレビューを表示すると、フォントが日本語ではなく中華フォントで描画されてしまう。自分の RubyMine で快適に使えるように修正してローカルにインストールしたい。

## 根本原因

フォント指定が3階層あり、最後に勝つのは Java から動的注入されるスタイル。プレビュー本文クラス `.vditor-reset` のフォントチェーンに `Hiragino Sans GB`（中国語簡体字）と `Microsoft Yahei`（中国語）が含まれていて、日本語フォントが指定されていないため macOS で中華 Hiragino にフォールバックしている。

主なフォント指定箇所:

1. **Vditor バンドル CSS** `src/main/resources/vditor/dist/index.css`
   - L530 `.vditor`
   - L834 `.vditor-reset`
   - L1729 `.vditor-sv`
2. **Java からの動的注入**（最優先で勝つ）`src/main/java/com/shuzijun/markdown/editor/MarkdownPreviewFileEditor.java` L287–289
3. **コンテンツテーマ CSS**（`wechat.css` のみ明示指定あり）

## 修正方針

### Step 1（必須）: `MarkdownPreviewFileEditor.java` L287–289 のフォントチェーンを日本語優先に変更

現状:
```
[IDEのエディタフォント], "Helvetica Neue", "Luxi Sans", "DejaVu Sans",
"Hiragino Sans GB", "Microsoft Yahei", sans-serif, ...emoji...
```

変更後（案）:
```
[IDEのエディタフォント], "Helvetica Neue", "Hiragino Sans",
"Hiragino Kaku Gothic ProN", "Yu Gothic", "Meiryo",
"Luxi Sans", "DejaVu Sans", sans-serif, ...emoji...
```

ポイント:
- `Hiragino Sans GB`（中国語）→ `Hiragino Sans`（日本語、macOS 標準）
- `Microsoft Yahei`（中国語）→ `Yu Gothic` / `Meiryo`（Windows 用日本語）
- IDE 側のエディタフォント設定は引き続き最優先で尊重

### Step 2（保険）: `.vditor` と `.vditor-sv` への上書きも追加

`getStyle()` 内のスタイル文字列に、`.vditor-reset` と同じ `font-family` を `.vditor`, `.vditor-sv` にも適用する CSS を追記。エディタモード（WYSIWYG/IR）で `.vditor` 系が見えるケースに備え、index.css の中華フォントを完全に潰す。

## ローカル RubyMine へのデプロイ手順

1. リポジトリ ルートで `./gradlew buildPlugin`
2. 生成物 `build/distributions/markdown-editor-*.zip` を取得
3. RubyMine → Settings → Plugins → ⚙ → **Install Plugin from Disk...** で zip 指定
4. RubyMine 再起動 → 既存の markdown-editor プラグインは無効化（同名プラグイン競合回避）

初回ビルドは IntelliJ SDK ダウンロードのため 5–10 分かかる。失敗したら `gradle.properties` の IntelliJ プラットフォームバージョンを RubyMine に合わせて調整。

## Git 準備（新セッション最初にやる）

```sh
# upstream リモート追加（本家更新の取り込み用）
git remote add upstream https://github.com/shuzijun/markdown-editor.git
git remote -v

# 作業ブランチを切る
git switch -c fix/japanese-font
```

## 任意の発展

- **ユーザー設定化**: `PluginConstant.java` にフォントキー追加 + `SettingUI.java` でテキスト入力欄を提供 → upstream PR 候補
- **テーマ系 CSS の整理**: `wechat.css` の中華固定フォントも PR 対象になり得る（自分用なら無視で OK）

## 新セッションでの再開トリガー

「`NOTES.md` の方針で日本語フォント修正を進めて」で続きから着手可能。
