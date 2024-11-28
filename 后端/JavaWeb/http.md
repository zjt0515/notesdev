## quickstart

1. 填写模块信息后勾选web开发依赖
2. 编写请求处理类和请求处理方法，添加注解

## http

 超文本传输协议

- 基于TCP协议：面向连接，安全
- 基于请求-响应模型，一次请求对应一次响应
- 无状态协议：对于事物处理没有记忆能力，每次请求响应都是独立，多次请求间不能共享数据，但是速度快

Response Header：响应数据

### 请求协议格式

Request Header：请求数据
第一行是请求行：请求方式请求路径请求协议
其余行是请求头，名字：值的键值对

```
//请求行，请求方式GET，资源路径，协议
GET /hello HTTP/1.1
//请求头，格式key：value
Accept:text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7//浏览器能接受的资源类型
Accept-Encoding: gzip, deflate, br, zstd//浏览器支持的压缩类型
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7//浏览器偏好语言
Cache-Control: max-age=0
Connection: keep-alive
Host: localhost:8080//
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) lAppleWebKit/537.36 (KHTML, like Gecko) Chrome/122.0.0.0 Safari/537.36//浏览器版本，用于浏览器兼容性处理
sec-ch-ua: "Chromium";v="122", "Not(A:Brand";v="24", "Google Chrome";v="122"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
//如果是Post请求，这里有请求体
```

Post请求的最后一行是请求体，存放请求参数

GET：请求参数在请求行中，?key=value&key=value，没有请求体，请求大小有限制。
POST：请求参数在请求体中，POST请求大小没有限制，浏览器中在payload中可以看到

### 响应格式

```
//响应行，协议，状态码200，描述
HTTP/1.1 200
//响应头
Content-Type: text/html;charset=UTF-8//响应内容的类型
Content-Length: 12//响应内容的长度(字节数)
Content-Encoding: gzip//响应压缩算法
Cache-Control: //客户端如何缓存，max-age=300表示最多缓存300s
Set-Cookie: //告诉浏览器为当前页面所在的域设置cookie
Date: Wed, 28 Feb 2024 12:20:15 GMT
Keep-Alive: timeout=60
Connection: keep-alive
//响应体
[{id: 1, brandName: "阿里巴巴"}]
```

- 1xx：响应中-临时状态码
- 2xx：成功
- 3xx：重定向
- 4xx：客户端错误
- 5xx：服务端错误

| 状态码  | 英文描述                               | 解释                                                         |
| ------- | -------------------------------------- | ------------------------------------------------------------ |
| ==200== | **`OK`**                               | 客户端请求成功，即**处理成功**，这是我们最想看到的状态码     |
| 302     | **`Found`**                            | 指示所请求的资源已移动到由`Location`响应头给定的 URL，浏览器会自动重新访问到这个页面 |
| 304     | **`Not Modified`**                     | 告诉客户端，你请求的资源至上次取得后，服务端并未更改，你直接用你本地缓存吧。隐式重定向 |
| 400     | **`Bad Request`**                      | 客户端请求有**语法错误**，不能被服务器所理解                 |
| 403     | **`Forbidden`**                        | 服务器收到请求，但是**拒绝提供服务**，比如：没有权限访问相关资源 |
| ==404== | **`Not Found`**                        | **请求资源不存在**，一般是URL输入有误，或者网站资源被删除了  |
| 405     | **`Method Not Allowed`**               | 请求方式有误，比如应该用GET请求方式的资源，用了POST          |
| 428     | **`Precondition Required`**            | **服务器要求有条件的请求**，告诉客户端要想访问该资源，必须携带特定的请求头 |
| 429     | **`Too Many Requests`**                | 指示用户在给定时间内发送了**太多请求**（“限速”），配合 Retry-After(多长时间后可以请求)响应头一起使用 |
| 431     | **` Request Header Fields Too Large`** | **请求头太大**，服务器不愿意处理请求，因为它的头部字段太大。请求可以在减少请求头域的大小后重新提交。 |
| ==500== | **`Internal Server Error`**            | **服务器发生不可预期的错误**。服务器出异常了，赶紧看日志去吧 |
| 503     | **`Service Unavailable`**              | **服务器尚未准备好处理请求**，服务器刚刚启动，还未初始化好   |

状态码大全：https://cloud.tencent.com/developer/chapter/13553 

## 协议解析

浏览器接受响应数据后，内置解析工具自动解析