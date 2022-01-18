# Nuxt✕TypeScriptのチュートリアルアプリ

NuxtをTypeScriptで実装するアプリ

# 基本設定

まずは以下のコマンドを入力する。

```
npm init nuxt-app nuxt-ts
```

## プロジェクト設定

Nuxtのプロジェクトをつくる際に様々な命令が出るので、その実装方法を以下に示す。

```
create-nuxt-app v4.0.0
✨  Generating Nuxt.js project in nuxt-ts
? Project name: nuxt-ts
? Programming language: TypeScript
? Package manager: Npm
? UI framework: Vuetify.js
? Nuxt.js modules: Axios - Promise based HTTP client
? Linting tools: (Press <space> to select, <a> to toggle all, <i> to invert selection)
? Testing framework: None
? Rendering mode: Universal (SSR / SSG)
? Deployment target: Server (Node.js hosting)
? Development tools: (Press <space> to select, <a> to toggle all, <i> to invert selection)
? What is your GitHub username? shota-nukumizu
? Version control system: Git
```

## 開発者サーバ立ち上げ

Nuxtのプロジェクトが完成したら、以下のコマンドを入力してNuxtサーバを立ち上げる。

```
cd nuxt-ts
npm run dev
```

`http://localhost:3000/`が出力されていたら成功。


# 完成デモ

▼初期設定画面

![](demo.png)