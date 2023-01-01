https://typescriptbook.jp/overview/ecosystem

# 2023/01/01

## TypeScript とエコシステム

![sample](https://typescriptbook.jp/assets/files/typescript-ecosystem-map-01fad23076509d150b7395ec107dc4d4.svg)

https://typescriptbook.jp/assets/files/typescript-ecosystem-map-01fad23076509d150b7395ec107dc4d4.svg


### 実行環境
- JavaScriptの実行環境は大きく分けてブラウザとサーバーの2種類がある

ブラウザ
- ブラウザは画面描画を行うコンポーネントとしてレンダリングエンジンを持つ
- レンダリングエンジンの内部にJavaScriptエンジンがある

サーバー
- DenoはTypeScriptがそのまま実行することができる

### モジュールバンドラー
- 複数のJavaScriptファイルを一つのファイルに結合するためのツール。
- 複数のJSファイルに依存関係がある場合、読み込み順を指定しないとアプリケーションが壊れる
- 🤔 Ruby の Bundler のファイルバージョン的な？

## なぜTypeScriptを使うべきか
- TypeScriptはJavaScriptのスーパーセット（JSの機能はそのままに、TSならではの新しい機能や利点を追加したもの）

## 静的型付け
- 動的型付けは「実行時」に型が定まる
  - 変数の型はプログラムを実行するまで定まらない
- 静的型付けは「コンパイル時」じ型が定まる
  - 変数の型は実行前のコンパイル時に定まる

## [ECMAScript](https://typescriptbook.jp/overview/ecmascript)
- ECMAScriptはJavaScriptの仕様（決まりごと）を定義したもの

### ECMAScriptとブラウザの関係性
