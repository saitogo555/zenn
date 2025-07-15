---
title: "環境構築"
---

## この章のゴール

この章では、Reactの開発に必要なNode.jsとnpmのインストール方法を学びます。
自分のPCに開発環境を整え、Reactプロジェクトを作成できる状態にすることがゴールです。

## Node.jsとは

![Node.jsロゴ](/images/bb6718046a5840/nodejs-logo-dark.webp)

Node.jsは、JavaScriptをサーバーサイドで実行できるようにするランタイム環境です。
もともとWebブラウザ上で動作していたJavaScriptを、サーバーやPC上でも動かせるようにしたことで、フロントエンド・バックエンドの両方で同じ言語を使った開発が可能になりました。

Node.jsには「npm（Node Package Manager）」というパッケージ管理ツールが付属しており、Reactをはじめとする多くのライブラリやツールを簡単にインストールできます。

## npmとは

![npmロゴ](/images/bb6718046a5840/npm-logo.webp)

npm（Node Package Manager）は、Node.jsに標準で付属しているパッケージ管理ツールです。npmを使うことで、Reactやその他のライブラリ・ツールを簡単にインストール・管理できます。

例えば、Reactをインストールする場合は以下のようなコマンドを使います。

```sh
npm install react
```

npmは、プロジェクトごとに依存関係を管理するための`package.json`ファイルを作成し、必要なパッケージを自動的にダウンロードしてくれます。

:::details package.json

`dependencies`がアプリを動作させるために必要なパッケージ一覧です。
`devDependencies`が開発時に必要なパッケージ一覧です

```json:package.json
{
  "name": "react",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  },
  "dependencies": {
    "@headlessui/react": "^2.2.4",
    "react": "^19.1.0",
    "react-dom": "^19.1.0",
    "react-router-dom": "^7.6.2"
  },
  "devDependencies": {
    "@eslint/js": "^9.25.0",
    "@types/react": "^19.1.2",
    "@types/react-dom": "^19.1.2",
    "@vitejs/plugin-react": "^4.4.1",
    "eslint": "^9.25.0",
    "eslint-plugin-react-hooks": "^5.2.0",
    "eslint-plugin-react-refresh": "^0.4.19",
    "globals": "^16.0.0",
    "vite": "^6.3.5"
  }
}
```

:::

> **ポイント:**  
> npmは世界中の開発者が作成したパッケージを共有する巨大なリポジトリ（[npm公式サイト](https://www.npmjs.com/)）と連携しています。  
> 必要なライブラリを検索して、すぐに導入できるのが特徴です。

## セットアップ手順

### Windows

1. **インストーラーのダウンロード**
   - [Node.js公式ダウンロードページ](https://nodejs.org/ja/download/)にアクセスします。
   - 「LTS（推奨版）」を選択してください。

   ![Node.jsダウンロードオプション](/images/bb6718046a5840/nodejs-download-options.webp =800x)
   ![Node.jsダウンロードボタン](/images/bb6718046a5840/nodejs-download-button.webp =800x)

2. **インストーラーの実行**
   - ダウンロードしたインストーラー（例: `node-vxx.x.x-x64.msi`）をダブルクリックして実行します。
   - 画面の指示に従い、「Next」や「同意する」を選択して進めます。

   ![Node.jsインストール画面](/images/bb6718046a5840/nodejs-install-win-1.webp =800x)
   *Nextをクリック*

   ![Node.jsインストール画面](/images/bb6718046a5840/nodejs-install-win-2.webp =800x)
   *「I accept the terms in the License Agreement」にチェックを入れてNextをクリック*

   ![Node.jsインストール画面](/images/bb6718046a5840/nodejs-install-win-3.webp =800x)
   *Nextをクリック*

   ![Node.jsインストール画面](/images/bb6718046a5840/nodejs-install-win-4.webp =800x)
   *Nextをクリック*

   ![Node.jsインストール画面](/images/bb6718046a5840/nodejs-install-win-5.webp =800x)
   *Nextをクリック*

   ![Node.jsインストール画面](/images/bb6718046a5840/nodejs-install-win-6.webp =800x)
   *Installをクリック*

   ![Node.jsインストール画面](/images/bb6718046a5840/nodejs-install-win-7.webp =800x)
   *進捗バーが100%になるまで待機*

   ![Node.jsインストール画面](/images/bb6718046a5840/nodejs-install-win-8.webp =800x)
   *インストールが完了したのでFinishをクリック*

3. **インストール完了の確認**
   - インストールが完了したら、コマンドプロンプトを開きます。
   - 以下のコマンドでバージョンを確認します。

   ```sh
   node -v
   npm -v
   ```

   - 正常にバージョンが表示されればセットアップ完了です。

   ![nodejsのバージョン確認](/images/bb6718046a5840/nodejs-version-check.webp =800x)
   ![npmのバージョン確認](/images/bb6718046a5840/npm-version-check.webp =800x)

### Linux

Linuxでは、Node.jsバージョンマネージャー「n」を使うことで、簡単かつ柔軟にNode.jsとnpmをセットアップできます。
この方法なら、複数バージョンの切り替えや最新LTS版のインストールもスムーズです。

:::message
`apt`を使ってインストールすると、Node.jsとnpmのバージョンが古すぎるため非推奨。
必ず**n**や**nvm**などのバージョンマネージャーを使いましょう。
:::

1. **makeのインストール**

   - ターミナルを開き、以下のコマンドを実行します。

   ```sh
   sudo apt install make
   ```

2. **nのインストール**

   - 続いて、以下のコマンドを実行します。

   ```sh
   curl -L https://bit.ly/n-install | bash
   ```

   - インストール中に「n」本体と最新のLTS版Node.jsが自動でセットアップされます。
   - インストールが完了したら、**新しいターミナルを開く**か、`source ~/.bashrc`や`source ~/.zshrc`などでシェル設定を再読み込みしてください。

3. **Node.jsとnpmのバージョン確認**

   - 以下のコマンドでバージョンを確認します。

   ```sh
   node -v
   npm -v
   ```

   - 正常にバージョンが表示されればセットアップ完了です。

   ![nodejsとnpmバージョン確認](/images/bb6718046a5840/nodejs-and-npm-version-check-linux.webp =800x)

:::details 他のバージョンをインストールしたい場合

最新版（LTS以外）や特定バージョンを使いたい場合は、次のようにコマンドを実行します。

```sh
n latest      # 最新版をインストール
n lts         # 最新LTS版をインストール
n 20.12.2     # バージョンを指定してインストール
```

バージョンを切り替えた後は、再度`node -v`で反映されているか確認しましょう。

:::

> **ポイント:** nの詳しい使い方は公式の[n-installリポジトリ](https://github.com/mklement0/n-install)も参考にしてください。

---

お疲れさまでした！これで開発環境の準備が整いました。

次のステップではReactプロジェクトのセットアップについて説明します。
