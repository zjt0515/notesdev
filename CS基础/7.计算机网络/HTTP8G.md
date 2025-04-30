# HTTP

## HTTP

### 无状态protocol

不保存请求和响应的通信状态：能够更快处理大量事务，可伸缩性

可以用Cookie管理状态

### 应用层协议

TCPIP模型中的应用层

### URL定位



超文本传输协议，HyperText Transfer Protocol

1. 超文本：文字图片视频的混合体，还有超链接
2. 双向协议
3. 可以用于服务器之间，服务器和客户端之间
4. 应用层协议核心 
5. 无状态协议
6. 互联网核心协议

## HTTP报文



1. 

### 请求报文

1. 请求行：请求方法/URL/版本
2. 首部字段：
3. 请求体：

```http
GET/HTTP/1.1
Host: hacker.jp
User-Agent: Mozilla/5.0
```

## HTTP状态码

1. 1xx 提示信息
2. 2xx 成功
3. 3xx 重定向
4. 4xx 客户端错误
5. 5xx 服务器错误

### 2xx成功

1. 200 OK
2. 204NC No Content 无资源可返回
3. 206PC Partial Content 范围请求

### 3xx重定向

1. 301MP Moved Permanently永久重定向
2. 302F Found 临时重定向
3. 303SO See Other希望客户以GET方法重定向到另一个URL
4. 304NM Not Modified 未符合条件(**和重定向无关**)
5. 307TP Temporary Redirect临时重定向

### 4xx 客户端错误

1. 401U Unauthorized 认证失败
2. 403F Forbidden 不允许访问
3. 404NF Not Found 无法找到请求资源

### 5xx服务器错误

1. 500ISE Internal Server Error 服务器端错误
2. 503SU Service Unavailable 超负载/停机维护

## HTTP字段

1. Host 服务器域名
2. Content-Length 返回数据长度
3. Connection 
4. Content-Type 数据格式
5. Content-Encoding 数据压缩方法

## Get和Post

1. Get 从服务器获取指定资源

   请求参数位置：一般是在URL中（URL规定只能支持ASCII

2. Post 根据请求负荷 对于指定资源做出处理

   携带数据位置：一般报文body，格式无限制

> url中的查询参数和body都不是get和post独有的，实际情况可以灵活使用

## Get和Post方法的安全性和幂等性

1. 安全：请求方法不会破坏服务器上的资源
2. 幂等：多次执行相同操作，结果相同

Get是安全且幂等的，Post请求是不安全且不幂等的

> 根据以上性质，可以对get请求数据做缓存，存到浏览器上或者代理上，减少发送次数
>
> 同时可以将get请求保存为书签

> [!caution]
>
> 以上内容是根据RFC规范定义，实际情况和开发者实现的接口有关
>
> 1. 用get实现增删数据的请求
> 2. 用post方法实现查询数据的请求

> [!caution]
>
> 信息泄露？
>
> get和post都无法避免数据被窃取，一个是在url上，另一个通过抓报就可以看到post提交的boidy数据
>
> 本质上是因为HTTP是明文传输内容
>
> 解决办法：HTTPS协议

## HTTP缓存

1. 强制缓存
   只要没有过期，直接使用浏览器本地缓存
   HTTP响应头部字段`Cache-Control`相对时间``Expires`绝对时间
   优先级：Cache-Control > Expires
2. 协商缓存



强制缓存过程细节：
第一次请求，返回时在Response头部加上`Cache-Control`设置过期时间大小
再次访问，比较时间和`Cache-Control`计算是否过期，没过期，使用缓存
过期，服务器返回时再次更新`Cache-Control`



协商缓存：与服务端协商之后，判断是否使用本地缓存

## HTTP1.1/2/3

1.0 -> 1.1

1. 长连接方式改善性能开销
2. 支持管道网络传输，请求发送不用等待，减少响应时间



1.1 -> 2

1. 头部压缩
2. 二进制格式
3. 并发传输
4. 服务器主动推送资源



## HTTP VS HTTPS

1. 在TCP三次握手之后，HTTPS还需进行SSL/TLS的握手过程，才能进入加密报文传输
2. HTTPS默认端口并非80，是443
3. HTTPS协议需要申请数字证书，保证服务器身份可信



HTTPS解决了？

1. 窃听风险
2. 篡改风险
3. 冒泡风险

> xai-rAmZ7dVrWY3sJAjyqYXkbq0LTJSsn2i83kQ91z4NMMObFJv028zLSbRfQV6O2szvX9m3cvemDoLYUJAb

## HTTP vs RPC

> Socket编程，A电脑进程到B电脑进程进行通信
>
> `fd = socket(AF_INET, SOCK_STREAM, 0)`
>
> TCP的三个特点：面向连接、可靠、基于字节流 
>
> 基于字节流，纯裸TCP的缺点：
> 粘包问题：

解决方法：自定义规则用于区分消息边界