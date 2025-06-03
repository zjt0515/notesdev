## vite

https://vite.dev/



## 跨域

```js
// vite.config.js
 // 代理配置
  server: {
    proxy: {
      // 代理所有 /api的请求
      '/api': {
        // 代理请求之后的请求地址
        target: 'https://api.imooc-front.lgdsunday.club/',
        // 跨域
        changeOrigin: true
      }
    }
  }
```



## env

.env.development

.env.product

```js
# .emv.development
# 开发env

VITE_BASE_URL = '/api'
```

获取env`console.log(import.meta.env.VITE_BASE_URL);`

