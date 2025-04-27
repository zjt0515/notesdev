后端/服务端：计算数据、持久化数据、减少客户端计算量

前端/客户端：接受后端数据，展示

前后端通信：http(s)协议

## HTTP构成

两个实体：客户端（浏览器）、服务端

资源定位：URL

1. 协议
2. 域名Host
3. 路径
4. 查询参数Query

HTTP请求内容

1. 请求方式 Get/Post/Put/Delete
2. 请求路径和查询参数
3. http版本
4. 请求头
    1. 
5. 请求体



Http响应内容

1. HTTP版本
2. 响应状态码

## Axios

https://axios-http.com/zh/docs/intro

### json-server

全局安装`npm i -g json-server`

`json-server`

新建文件`db.json`

```json
{
    "users":[
        {
            "id": 1,
            "name": 'Genshinya',
        }
    ]
}
```

`npm i axios`

有`await`的函数，函数头前面必须加上`async`

```vue
<script>
	async function getDog(){
        try {
            let result = await axios.get('')
	        dogList.push(result.data.message)
        } catch(errror) {
            alert(error)
        }
    }
</script>
```

axios对服务器返回的结果会包装成一个对象，必须使用`result.data`才能取出服务器返回的对象

## Fetch

浏览器内置Http请求工具

## 前端自动生成请求

https://github.com/ferdikoomen/openapi-typescript-codegen



`openapi --input http://localhost:8121/api/v2/api-docs --output ./generated --client axios`

`npx openapi-typescript-codegen --input http://localhost:8121/api/v2/api-docs --output ./generated --client axios`

