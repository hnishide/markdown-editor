# カスタムスタイル

* [English Document](https://github.com/shuzijun/markdown-editor/blob/main/assets/CustomStyle.md)
* [中文文档](https://github.com/shuzijun/markdown-editor/blob/main/assets/CustomStyle_ZH.md)

- [日本語ドキュメント](#概要)

## 概要

レンダリング用のエディタは1つの HTML ページとして実装されています。デフォルトでは jar 内のリソースとスタイルが読み込まれており、ダーク／ライトの2テーマにのみ最適化されています。それ以外の配色テーマを使用していると見た目が崩れることがあります。

そのため、外部テーマを読み込む仕組みが用意されています。固定パス配下に置いた HTML ページとスタイルを読み込ませることが可能です。*File | Settings | Tools | Markdown Editor* からプラグイン設定画面を開くと、テンプレートパスと同期ボタンが確認できます。

同期ボタンを押すと、デフォルトのページとテーマが当該パス配下にコピーされます。現状このパスはプラグインのインストールパス固定で変更できず、再インストールごとに初期化されるため、必要に応じてバックアップしてください。

ここからは Chrome の DevTools と CSS の知識が必要になります。エディタ上で右クリックすると *open DevTools* が表示されるので、それを開き、要素を選択して現在適用されているスタイルを確認しながら、目的に合わせて修正してください。

以下、同期されるフォルダの構成について説明します。

## template/default.html

レンダリングエディタのメインページで、すべての設定値がこのファイル内にあります。各設定項目の詳細は [vditor](https://github.com/Vanessa219/vditor) のドキュメントを参照してください。より高度なカスタマイズが必要であれば、ここを直接編集します。

テーマ関連の設定は次のようになっています。

* `"theme": darcula ? "dark" : "light"`
* `"current": darcula ? "idea-dark" : "idea-light"`

`darcula` 変数は現在の IDE が Darcula テーマを使用しているかどうかを表します。`idea-dark` と `idea-light` がデフォルトで読み込まれるテーマです。

## vditor/content-theme

テーマファイルを格納するディレクトリです。テーマを丸ごと差し替えたい場合は、ここに独自の CSS を追加し、`default.html` のテーマ名を変更します。一部のスタイルだけを修正したいなら、後述の `userStyle.css` の利用を推奨します。

## vditor/userStyle.css

ユーザー独自のスタイル上書き用ファイルです。一部のスタイルのみ変更したいときは、DevTools で要素を特定し、対象のスタイルをこのファイル内で再定義してください。

## 最後に

vditor のテーマに関する公式ドキュメントは見当たらないため、結局はブラウザの DevTools で要素を特定して書き換えるのが現実的です。

書き換え手順、要素の意味、書き換えたテーマやファイルなどはぜひ共有していただけると嬉しいです :smile:
