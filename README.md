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


# TypeScriptの導入

以下のコマンドでインストール

```
npm install --save-dev @nuxt/typescript-build @nuxt/types
```

# 設定

`nuxt.config.js`内の`buildModules`に`@nuxt/typescript-build`を追加すること。

```js
export default {
    buildModules: ['@nuxt/typescript-build']
}
```

そして、以下に`tsconfig.json`を用意する。

```json
{
  "compilerOptions": {
    "target": "ES2018",
    "module": "ESNext",
    "moduleResolution": "Node",
    "lib": [
      "ESNext",
      "ESNext.AsyncIterable",
      "DOM"
    ],
    "esModuleInterop": true,
    "allowJs": true,
    "sourceMap": true,
    "strict": true,
    "noEmit": true,
    "baseUrl": ".",
    "paths": {
      "~/*": [
        "./*"
      ],
      "@/*": [
        "./*"
      ]
    },
    "types": [
      "@types/node",
      "@nuxt/types"
    ]
  },
  "exclude": [
    "node_modules"
  ]
}
```

また、以下の型宣言を追加して、Vueファイルの型を提供する必要がある。

```ts
// vue-shim.d.ts
declare module "*.vue" {
    import Vue from 'vue'
    export default Vue
}
```

このファイルはルートディレクトリに配置する。(新規作成する必要がある)

# Runtimeのインストール

インストールコマンド

```
npm install @nuxt/typescript-runtime
```

`package.json`を更新。

```json
"scripts": {
  "dev": "nuxt-ts",
  "build": "nuxt-ts build",
  "generate": "nuxt-ts generate",
  "start": "nuxt-ts start"
},
"dependencies": {
  "@nuxt/typescript-runtime": "latest",
  "nuxt": "latest"
},
"devDependencies": {
  "@nuxt/types": "latest",
  "@nuxt/typescript-build": "latest"
}
```

これで`nuxt.config.js`、ローカルの`modules`や`serverMiddleware`でTypeScriptを動かせる。基本設定は終了。

# TOP画面のコード

`pages/index.vue`

NuxtのWEBサイトで表示されるTOP画面。

```html
<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
        <NuxtLogo />
        <VuetifyLogo />
      </v-card>
      <v-card>
        <v-card-title class="headline">
          Welcome to the Vuetify + Nuxt.js template
        </v-card-title>
        <v-card-text>
          <p>Vuetify is a progressive Material Design component framework for Vue.js. It was designed to empower developers to create amazing applications.</p>
          <p>
            For more information on Vuetify, check out the <a
              href="https://vuetifyjs.com"
              target="_blank"
              rel="noopener noreferrer"
            >
              documentation
            </a>.
          </p>
          <p>
            If you have questions, please join the official <a
              href="https://chat.vuetifyjs.com/"
              target="_blank"
              rel="noopener noreferrer"
              title="chat"
            >
              discord
            </a>.
          </p>
          <p>
            Find a bug? Report it on the github <a
              href="https://github.com/vuetifyjs/vuetify/issues"
              target="_blank"
              rel="noopener noreferrer"
              title="contribute"
            >
              issue board
            </a>.
          </p>
          <p>Thank you for developing with Vuetify and I look forward to bringing more exciting features in the future.</p>
          <div class="text-xs-right">
            <em><small>&mdash; John Leider</small></em>
          </div>
          <hr class="my-3">
          <a
            href="https://nuxtjs.org/"
            target="_blank"
            rel="noopener noreferrer"
          >
            Nuxt Documentation
          </a>
          <br>
          <a
            href="https://github.com/nuxt/nuxt.js"
            target="_blank"
            rel="noopener noreferrer"
          >
            Nuxt GitHub
          </a>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/inspire"
          >
            Continue
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
```

# 今後の課題

NuxtやTypeScriptについてはまだ初心者なので、これから焦らずゆっくりとフロントエンド開発を進めていきたい。


# 完成デモ

▼初期設定画面

![](demo.png)

# 開発環境

* Nuxtjs 4.0.0
* Vuetify 2.6.2
* Axios
* TypeScript 4.5.4