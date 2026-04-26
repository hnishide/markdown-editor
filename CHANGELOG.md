<!-- Keep a Changelog guide -> https://keepachangelog.com -->

# Markdown Editor Changelog

## 2.0.5-jp.2

### Removed

- ツールバーのドネーションボタンと、未使用になったアイコン SVG を削除
- info（ⓘ）ポップアップ内の Donate リンクも削除

## 2.0.5-jp.1

hnishide フォークの初回リリース。日本語環境向けの修正と、テレメトリ／設定UIの削除を含む。

### Added

- 日本語ドキュメント (`README_JA.md`, `assets/CustomStyle_JA.md`)

### Changed

- プレビューのフォントチェーンを日本語フォント優先 (Hiragino Sans / Hiragino Kaku Gothic ProN / Yu Gothic / Meiryo) に変更し、中国語フォント (Hiragino Sans GB / Microsoft Yahei) を除外
- `.vditor` / `.vditor-sv` にも同フォントチェーンを適用
- プラグインメタデータ (id / vendor / 説明 / homepage) を hnishide フォーク向けに更新

### Removed

- Sentry によるエラーレポート機能 (`ErrorReportHandler`, `SentryUtils`, `io.sentry:sentry` 依存)
- プラグイン設定UI (`SettingConfigurable`, `SettingUI`)。jsdelivr.com への通信ルートも併せて排除

## 2.0.5

### Added

- Support Absolute Path。[#84](https://github.com/shuzijun/markdown-editor/issues/84)

### Changed

- Optimize text action menu.
- Upgrade vditor to `3.9.1`

### Fixed

- fix [#62](https://github.com/shuzijun/markdown-editor/issues/62)

### Removed

## 2.0.4

### Added

- Open file wait for animation

### Changed

### Fixed

- fix [#81](https://github.com/shuzijun/markdown-editor/issues/81)
- fix [#72](https://github.com/shuzijun/markdown-editor/issues/72)
- fix [#65](https://github.com/shuzijun/markdown-editor/issues/65)

### Removed

- Remove the shortcut key to close the search box by default

## 2.0.2

### Added

### Changed

- fix [#68](https://github.com/shuzijun/markdown-editor/issues/68)

### Fixed

### Removed

## 2.0.1

### Added

### Changed

- Upgrade vditor to `3.8.17`

### Fixed

### Removed

## 2.0.0

### Added

### Changed

- Upgrade vditor to `3.8.14`
- Modify upload file directory selection and overwrite reminder. [#43](https://github.com/shuzijun/markdown-editor/issues/43)
- Modify export file directory selection and overwrite reminder.
- Modify compatible to version 221

### Fixed

### Removed
