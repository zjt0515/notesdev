# Express

最小的nodejs框架

https://expressjs.com/

##  路由

```js
app.<method>('url', (req, res) => {
  res.end('请求数据')
})

// 匹配所有方法、所有url
app.all('*', (req, res) => {
  res.end('404 not found')
})

// 获取请求参数

```

### 请求报文req

1. method
2. url
3. httpVersion 1.1
4. req.headers
    1. host
    2. connection
    3. accept



```js
  // 原生
  console.log(req.method)
  console.log(req.url)
  console.log(req.httpVersion)
  console.log(req.headers)

  // express
  console.log(req.path)
  console.log(req.query)
```

### 提取路由参数

  