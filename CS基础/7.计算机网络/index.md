## 参考资料

1. https://javabetter.cn/sidebar/sanfene/network.html#_1-%E8%AF%B4%E4%B8%8B%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C%E4%BD%93%E7%B3%BB%E7%BB%93%E6%9E%84
2. https://javaguide.cn/cs-basics/network/computer-network-xiexiren-summary.html
3. https://xiaolincoding.com/network/5_learn/learn_network.html



# 补充内容

## Cookie、Session、Token

登录一次后，一段时间内不用再输入用户名和密码，实现核心概念：存储 

http无状态：再次访问，服务器是无意识的

### cookie的基本流程

1. 浏览器发起HTTP请求，服务器进行Set-Cookie
2. cookie返回给浏览器，浏览器保存
3.  以后每次发送请求，带上这个cookie 