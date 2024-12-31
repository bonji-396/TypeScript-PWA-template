# TypeScript + PWA のテンプレート

TypeScriptでPWAのフロントエンドアプリを作るためのテンプレートです。
`WebPack`や`Vite`、`esbuild`を、あえて導入していないパターンで構成しました。

## 主な技術構成

- Node.js
- TypeScript
- PWA
- Sass
- RxJS

## 行いたいこと

基本的には、PWAのフロントエンドをTypeScriptで記述し作成するためのテンプレートとして利用したい。
最低限以下の導入が済んだ状態を条件としています。

- `manifest.json`  
まずは、拡張機能やプログレッシブウェブアプリ（PWA）の動作を定義するJSON形式のファイルを初期で導入。
- `serivce-worker.ts`  
TypeScriptにて、service-worker.tsを書き、service-worker.jsをにコンパイルして利用する。またキャッシュ戦略や同期処理なども、PWAライブラリ等を利用せずに、自身で実装したいため最低限のコードのみを記載。
- `sass`  
scssの利用に慣れているので、sassの導入はしたかった。
- `rxjs`  
機能として利用するJavaScript用ライブラリをサンプル導入例として、リアクティブプログラミングライブラリを選択。

また、開発効率を上げるため、開発サーバーでの自動更新で反映させたい。

ここでは、それに関連するユーティリティとしてのライブラリを導入している。（concurrently、rimraf、etc...）


## 導入

以下を実行
```zsh
npm install
```

### 開発利用パッケージ
これらのパッケージは主に開発環境の構築とビルドプロセスの自動化に使用されています。

|パッケージ|説明|
|---|---|
|@types/serviceworker|Service Workerのための TypeScript型定義ファイル。PWAの開発において、Service WorkerのAPIを型安全に利用するために必要です。|
|chokidar-cli|ファイルやディレクトリの変更を監視し、指定したコマンドを自動的に実行するシンプルな CLI ツールです。|
|concurrently|複数のコマンドを並行して実行するためのツール。例えば、TypeScriptのコンパイル監視とサーバー起動を同時に行うのに使用しています。|
|lite-server|軽量な開発用Webサーバー。ブラウザの自動リロード機能を備えており、SPAの開発に適しています。|
|rimraf|Node.jsで`rm -rf`コマンドと同等の機能を提供するツール。ビルド前のdistディレクトリのクリーンアップなどに使用します。|
|sass|SASSプリプロセッサのNode.js実装。SCSSファイルをCSSにコンパイルするために使用します。
|typescript|JavaScriptに静的型付けを追加するプログラミング言語。型安全性とIDEのサポートを強化します。|
|rxjs|JavaScriptのリアクティブ拡張ライブラリで、開発依存関係として追加（型定義のためだけに使用）|

## 開発用ローカルサーバー実行

```zsh
npm run clean # distディレクトリを完全にクリーン
npm run dev # 開発サーバーを起動
```

## ビルド

```zsh
npm run build
```