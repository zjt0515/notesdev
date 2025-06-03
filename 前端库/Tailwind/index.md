## 链接

- https://tailwindcss.com/docs/installation/using-vite
- https://www.tailwindcss.cn/

## 传统css痛点

1. 统一变量维护困难
2. 大量的className负担
3. html、css分离造成滚动问题
4. 响应式、主题切换实现复杂

## 环境配置

vscode插件：Tailwind CSS IntelliSense

prettier插件：https://github.com/tailwindlabs/prettier-plugin-tailwindcss

安装

```bash
// vite
npm install tailwindcss @tailwindcss/vite
```



```js
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{vue,js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

在main.ts中引入main.css

```css
//main.css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 基于Tailwind的组件库

- `npm install flowbite`https://flowbite.com/docs/components/accordion/



