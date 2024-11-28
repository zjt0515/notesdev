- https://www.tailwindcss.cn/



## 环境配置

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



