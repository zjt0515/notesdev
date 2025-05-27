## 基础构建

### 获取请求body数据

实现相应数据获取逻辑

promise包装化，返回res对象(AxiosResponse)

```ts
export interface AxiosResponse {
  data: any
  status: number
  statusText: string
  headers: any
  config: AxiosRequestConfig
  request: any
}
```

```ts
export default function xhr(config: AxiosRequestConfig): AxiosPromise {
  return new Promise(resolve => {
    const { data = null, url, method = 'get', headers, responseType } = config

    const request = new XMLHttpRequest()

    if (responseType) {
      request.responseType = responseType
    }

    request.open(method.toUpperCase(), url, true)

    request.onreadystatechange = function handleLoad() {
      if (request.readyState !== 4) {
        return
      }
      const responseHeaders = request.getAllResponseHeaders()
      const responseData =
        responseType !== 'text' ? request.response : request.responseText

      const response: AxiosResponse = {
        data: responseData,
        status: request.status,
        statusText: request.statusText,
        headers: responseHeaders,
        config,
        request
      }

      resolve(response)
    }

    // 设置请求头
    Object.keys(headers).forEach(key => {
      if (data === null && key.toLowerCase() === 'content-type') {
        // 没有数据时content-type无意义
        delete headers[key]
      } else {
        request.setRequestHeader(key, headers[key])
      }
    })

    request.send(data)
  })
}
```



### headers对象化

即解析`xhr.getAllResponseHeaders`返回的字符串

```
connection: keep-alive
content-length: 13
content-type: application/json; charset=utf-8
date: Tue, 20 May 2025 21:26:44 GMT
etag: W/"d-talgBZSHcQOay+ud5zDrtp+2VNk"
keep-alive: timeout=5
x-powered-by: Express
```

分析：每行以`\r\n`结尾

### 处理响应数据



### 处理响应header

1. 通过`request.getAllResponseHeaders()`获取响应头string
2. 定义辅助方法`parseHeaders`解析header为对象
3. headers作为response一部分一起返回

### 处理响应data

获取响应data

```ts
const responseData =
        responseType !== 'text' ? request.response : request.responseText
```

data作为response一部分返回

## 错误处理

### 处理网络错误

```js
request.onerror = function handleError() {
  reject(new Error('Network Error'))
}
```

### 处理超时

1. AxiosRequestConfig 添加可选字段timeout
2. open之前：request.timeout设置为timeout

```js
request.ontimeout = function handleTimeout() {
  reject(new Error(`Timeout of ${timeout} ms exceeded`))
}
```

### 处理异常状态码

reslove响应时检查状态码

```ts
function handleResponse(response: AxiosResponse): void {
  if (response.status >= 200 && response.status < 300) {
    resolve(response)
  } else {
    reject(new Error(`Request failed with status code ${response.status}`))
  }
}
```

### 错误信息增强

自定义`AxiosError`类，替换`new Error(msg)`

```ts
export class AxiosError extends Error {
  isAxiosError: boolean
  config: AxiosRequestConfig
  code?: string | null
  request?: any
  response?: AxiosResponse

  constructor(
    message: string,
    config: AxiosRequestConfig,
    code?: string | null,
    request?: any,
    response?: AxiosResponse
  ) {
    super(message)

    this.config = config
    this.code = code
    this.request = request
    this.response = response
    this.isAxiosError = true

    // 修复ts class继承Error的坑
    Object.setPrototypeOf(this, AxiosError.prototype)
  }
}
```

同时定义工厂函数，方便直接使用

## 接口拓展

axios从单一方法拓展到拥有多个方法属性的混合对象

### 借口类型定义

### 混合对象实现

1. 该对象是一个函数
2. 该对象要包括Axios类的所有原型属性和实例属性

### axios函数重载

需求：

支持url参数从config分离，即类似函数重载的效果

```ts
Axios('url', {})
Axios({
  url
  method
})
```

1. 拓展AxiosInstance接口
2. 利用any+类型判断，修改request方法实现

```js
request(url: any, config?: any): AxiosPromise {
    if (typeof url === 'string') {
      if (!config) {
        config = {}
      }
      config.url = url
    } else {
      config = url
    }
    return dispatchRequest(config)
  }

```

