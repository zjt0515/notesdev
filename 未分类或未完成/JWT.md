## 参考资料

- https://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html
- https://jwt.io/
- https://www.bilibili.com/video/BV1i54y1m7cP

## JSON Web Token

安全标准，提供加密算法，令牌 

以Json形式作为web应用中的令牌，用于将信息安全传输，传输过程中完成数据加密、签名等处理

### 做什么

1. 授权 用户登录后，后续请求包含jwt，限制用户访问该令牌允许的资源
2. 单点登录中广泛应用，开销小，完成跨域
3. 信息交换，签名，验证内容是否被篡改，保证数据安全

### why

http协议无状态，每次用户都需要用户认证登录

**传统session认证：**

服务器：user → session 位于服务器

客户端：sessionid → cookie 存在浏览器

登陆时，服务器存储一份session，同时将JSESSIONID通过响应传给客户端浏览器，保存为cookie

传统session认证的问题：

1. 服务端session保存在内存中，用户多开销大
2. 在分布式应用中，客户端每次请求第一个保存session的服务器，限制了负载均衡器的能力，限制应用拓展能力
3. cookie被拦截，用户就会遭到跨站请求伪造的攻击
4. 在前后端分离系统，部署复杂性增加
    1. 用户一次请求就要转发多次
    2. sessionid是一个特征值，表达信息不够丰富，不容易拓展
    3. 如果后端是多节点部署，还需要实现session共享机制，不方便集群应用 

**jwt认证**：

1. 简洁，数据量小传输快
2. 自暴寒，payload中包含了用户信息，避免了多次查询数据库
3. 跨语言：JSON加密形式保存在客户端
4. 不需要在服务端保存session。适用于微服务

### JWT认证流程

1. 前端Http Post请求，建议SSL加密传输
2. 后端校验成功后，将用户id等其他信息作为payload，并将payload与header进行Base64编码拼接后签名，形成一个JWT（token）
3. 返回JWT给前端，前端将其保存在localStorage中，如果退出登录就删除保存内容
4. 前端每次请求时，将JWT放入Http Header中的Authorization位
5. 后端检查是否存在，验证JWT有效性，检查签名正确，token是否过期，检查token的接收方是否为自己

## JWT结构

token → string → header.payload.signature

1. 标题
    1. 令牌类型
    2. 使用的签名算法
2. 有效载荷
    1. 不放用户敏感信息
    
    2. 7个官方字段
    
        ```json
        iss (issuer)：签发人
        exp (expiration time)：过期时间
        sub (subject)：主题
        aud (audience)：受众
        nbf (Not Before)：生效时间
        iat (Issued At)：签发时间
        jti (JWT ID)：编号
        ```
3. 签名
    1. header+payload+密钥 → header中指定的签名算法签名

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

经过base64编码得到header：ewogICJhbGciOiAiSFMyNTYiLAogICJ0eXAiOiAiSldUIgp9

```json
{
  "sub": "1234567890",
  "name": "Zjt",
  "admin": true
}
```

经过base64得到payload

> 因为base64不是加密算法，所以不在header和payload中加入敏感信息





## JWT使用

 流程：

1. 前端用户发送登录请求，服务端接口处理
2. 服务端生成令牌，返回前端
3. 前端保存到浏览器中或者cookie中
4. 用户访问其他资源，如果token未失效，就能携带令牌
5. 服务器接受令牌，验证合法性

异常：

1. 签名不一致异常
2. 令牌过期异常
3. 算法不匹配异常
4. 失效payload异常



## JWT库

https://jwt.io/libraries

1. java-jwe：maven: com.auth0 / java-jwt / 3.3.0https://github.com/auth0/java-jwt
2. jose4j：maven: org.bitbucket.b_c / jose4j / 0.9.3
3. jjwt：maven: io.jsonwebtoken / jjwt-root / 0.11.1
4. nimbus-jose-jwt：
5. fusionauth-jwt
6. vertx-auth-jwt

### auth0.jwt

```java
<dependency>
  <groupId>com.auth0</groupId>
  <artifactId>java-jwt</artifactId>
  <version>4.4.0</version>
</dependency>
```



