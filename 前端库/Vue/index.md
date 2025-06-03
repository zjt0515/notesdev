## Vue面试

- https://vue3js.cn/interview
- https://www.bilibili.com/video/BV11i4y1Q7H2

# 环境配置

## 相关链接

[vue官网](https://cn.vuejs.org)

## 创建项目

### 基于 [vite](https://vitejs.cn) 创建

```shell
 npm create vue@latest

npm i vue-router pinia axios

// css
npm install -D sass
```

![image-20240525200235148](./images/image-20240525200235148.png)

## 项目结构

| 目录/文件         | 作用       |      |
| ----------------- | ---------- | ---- |
| index.html        | 入口文件   |      |
| package-lock.json | 包管理文件 |      |
| package.json      | 包管理文件 |      |
| vite.config.ts    |            |      |
| src               | 源代码     |      |

### src

```ts
// main.ts
import { createApp } from "vue"; //用于创建引用
import App from './App.vue'//App根组件
createApp(App).mount('#app')//创建一个应用实例
```

```vue
<!-- App.vue -->
<!-- 组件结构 -->
<template>
</template>
<!-- 组件脚本 -->
<script lang="ts">
    //默认暴露
    export default {
        name:'App' //组件名
    }
</script>
<!-- 组件样式 -->
<style>
</style>
```

### vuecli

```shell
```











## 配置杂项

### 配置路径别名@

```json
// tsconfig.app.json
{
	"include": ["src/**/*.ts", "src/**/*.tsx", "src/**/*.vue", "vite.config.ts"]
}
```

vite


```js
// vite.config.ts
import path from 'path'
import {join} from 'path'

export default defineConfig({
  plugins: [
    vue(),
  ],
  resolve: {
    alias: {
      '@': path.resolve(__dirname, './src') // 路径别名
      // '@': path.join(__dirname, '/src')
    }
  }
})
```

```ts
// vite.config.ts
import { fileURLToPath, URL } from 'node:url'

import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import vueDevTools from 'vite-plugin-vue-devtools'

// https://vite.dev/config/
export default defineConfig({
  plugins: [
    vue(),
    vueDevTools(),
  ],
  resolve: {
    alias: {
      '@': fileURLToPath(new URL('./src', import.meta.url))
    },
  },
})

```



## Vue工具链

参考资料https://devtools.vuejs.org/

### 项目脚手架

- Vite
- VueCLI

### 格式化工具

- [Vue - Official](https://github.com/vuejs/language-tools) VS Code 插件为 Vue 单文件组件提供了开箱即用的格式化功能。
- [Prettier](https://prettier.io/) 也提供了内置的 Vue 单文件组件格式化支持。
- eslint-plugin-vuehttps://eslint.vuejs.org/
- js标准规则https://standardjs.com/rules



## 样式解决方案

### 组件库

Element Plus：[ElementPlus](https://element-plus.org/zh-CN/guide/installation.html)按照官网安装后，再完成按需导入配置

### css框架

bootstrap：https://getbootstrap.com/docs/5.3/getting-started/vite/

整合Tailwind CSS

```shell
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```
