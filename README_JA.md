# markdown-editor

IntelliJ プラットフォーム向けの WYSIWYG マークダウンエディタプラグインです。本フォークでは、macOS RubyMine 等で日本語フォントが中華フォントにフォールバックしてしまう問題を修正しています。

- [English Document](./README.md)
- [中文文档](https://github.com/shuzijun/markdown-editor/blob/main/README_ZH.md)
- 関連リンク
  - [カスタムスタイル](./assets/CustomStyle_JA.md)

# 機能

* 3つの編集モードに対応: WYSIWYG / インスタントレンダリング / 分割ビュー
* アウトライン、数式、マインドマップ、チャート、フローチャート、ガントチャート、タイミングチャート、見出しアンカー、コードハイライト、graphviz レンダリングに対応
* 画像のペースト、ファイルのアップロード、ドラッグ＆ドロップによる挿入に対応
* IDE からのファイル高速オープンに対応
* その他の機能は [vditor features](https://github.com/Vanessa219/vditor/blob/master/README_en_US.md#--features) を参照

# 使い方

* プラグインをインストールしたあと、`.md` ファイルを開き、エディタ下部の **Markdown Editor** タブを選択します。
* デフォルトの Markdown プラグインをアンインストールする必要はありません。本プラグインのエディタはデフォルトエディタの隣に追加されます。
* JCEF をサポートする IDE を使用してください。

# デモ

![demo.gif](https://raw.githubusercontent.com/shuzijun/markdown-editor/main/assets/demo.gif)

# このフォークについて

本フォーク（`hnishide/markdown-editor`）は、本家 [shuzijun/markdown-editor](https://github.com/shuzijun/markdown-editor) をベースに、日本語環境向けの修正を加えた個人利用版です。主な変更点は次の通りです。

* プレビュー本文のフォントチェーンから中国語フォント（Hiragino Sans GB / Microsoft Yahei）を除外し、日本語フォント（Hiragino Sans / Hiragino Kaku Gothic ProN / Yu Gothic / Meiryo）を優先するように変更

# 謝辞

* [vditor](https://github.com/Vanessa219/vditor)
* [shuzijun/markdown-editor](https://github.com/shuzijun/markdown-editor)（本家）
