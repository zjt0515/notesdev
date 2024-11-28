异步js和xml，无刷新获取数据，实现懒加载、动态加载

没有浏览历史，不能回退。存在跨域问题(不同服务之间的请求)。SEO不友好(爬不到？。

## 工具

express服务端

nodemon热更新node

## XML()

可拓展标记语言，用于存储传输数据，使用自定义标签格式

## JSON

更简洁，数据转换更容易

## HTTP协议

### 请求

```
//请求行 GET/POST + url + HTTP版本
//请求头
Host: 
Cookie:
Content-type:
User-Agent:
……
空行
请求体
```

get：请求行中有url参数，请求体为空

### 响应

```
行 HTTP版本 + 状态码
头

空行
体(一般是服务器返回的html内容)
```





## json数据响应

客户端

```js
btn_json.onclick = function () {
      const xhr = new XMLHttpRequest();
      //设置响应体数据类型
      xhr.responseType = "json";

      // 设置 get 请求 和 url
      xhr.open("GET", "http://127.0.0.1:8000/json-server");
      xhr.send("");
      xhr.onreadystatechange = function () {
        if (xhr.readyState === 4) {
          // 2xx 成功
          if (xhr.status >= 200 && xhr.status < 300) {
            //获取行 头 空行 体
            //console.log(xhr.status + " " + xhr.statusText);
            //console.log("响应头：" + xhr.getAllResponseHeaders()); // 所有响应头
            //console.log("响应体：" + xhr.response); // 响应体
            printXHR(xhr);
            //let data = JSON.parse(xhr.response);
            result.innerHTML =
              "ResponseHeaders: " +
              xhr.getAllResponseHeaders() +
              "response: " +
              xhr.response;
          } else {
            result.innerHTML = " 失败 ";
          }
        }
      };
    };
```

服务端

```js
// json
app.all("/json-server", (request, response) => {
  // 设置响应头，设置允许跨域
  response.setHeader("Access-Control-Allow-Origin", "*");
  // 接受所有类型的请求头信息
  response.setHeader("Access-Control-Allow-Headers", "*");
  // 设置响应体并发送
  const data = {
    name: "genshinya",
    password: "123456",
  };
  let str = JSON.stringify(data);
  response.send(str);
});
```

