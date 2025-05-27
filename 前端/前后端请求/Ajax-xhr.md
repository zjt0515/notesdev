## xhr对象属性

### readyState 代理状态

| 值   | 状态               | 描述                                                |
| :--- | :----------------- | :-------------------------------------------------- |
| `0`  | `UNSENT`           | 代理被创建，但尚未调用 open() 方法。                |
| `1`  | `OPENED`           | `open()` 方法已经被调用。                           |
| `2`  | `HEADERS_RECEIVED` | `send()` 方法已经被调用，并且头部和状态已经可获得。 |
| `3`  | `LOADING`          | 下载中；`responseText` 属性已经包含部分数据。       |
| `4`  | `DONE`             | 下载操作已完成。                                    |

```js
var xhr = new XMLHttpRequest();
console.log("UNSENT", xhr.readyState); // readyState 为 0

xhr.open("GET", "/api", true);
console.log("OPENED", xhr.readyState); // readyState 为 1

xhr.onprogress = function () {
  console.log("LOADING", xhr.readyState); // readyState 为 3
};

xhr.onload = function () {
  console.log("DONE", xhr.readyState); // readyState 为 4
};

xhr.send(null);

```

### responseType 响应数据类型

| 值            | 描述                                                         |
| ------------- | ------------------------------------------------------------ |
| ""            | "text"                                                       |
| "arraybuffer" | 包含二进制数据的 JavaScript [`ArrayBuffer`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) |
| "blob"        | 包含二进制数据的 [`Blob`](https://developer.mozilla.org/zh-CN/docs/Web/API/Blob) 对象 |
| "document"    |                                                              |
| "json"        |                                                              |
| "text"        |                                                              |
| "Ms-stream"   |                                                              |

### response 响应正文

### responseText

当请求状态 [`readyState`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/readyState) 变为 `XMLHttpRequest.DONE` (`4`)，且 [`status`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/status) 值为 200（"OK"）时，`responseText` 是全部后端的返回数据

### status 状态码 ｜ statusText 对应文本信息

1. 请求完成前：0
2. 载入中：200
3. 完成：200
4. 。。。

## xhr方法

### open()

```js
xhrReq.open(method, url[, async, user, password]);

xhrReq.open('get', 'url', true)
```

### send()

```js
xhr.send()
xhr.send(body)
```

### getResponseHeader()

获取响应头报文项