## 回调callback

将函数作为参数传递给另一个函数，在合适的时候调用这个函数

```js
function f(callback){
  callback();
}
```





## Promise

作为异步操作的未来结果的一个占位符，未来值的容器

build a promise



> 一个由 executor 完成的工作只能有一个结果或一个 error
> 即只能调用一次resolve或者一次reject，剩余的都会被忽略

### promise属性

![image-20250322135826181](./images/image-20250322135826181.png)

1. state
    1. pending：初始值
    2. settled
        1. fulfilled：调用resolve后
        2. rejected：调用reject后
2. result
    1. undefined：初始值
    2. value：调用resolve(value)后
    3. error：调用reject(error)后

> state和result都是内部属性，外部不能访问



### consume（then、catch）

```js
promise.then(
    function(result){},
    function(error){},
)
promise.catch(function(error){})
promise.then(null, function(error){})
```

then
第一个函数参数在resolved且接收到value后执行
第二个函数参数在rejected且接收到error后执行

catch
接收的函数参数在rejected且接收到error后执行

### finally

​	

## 同步Synchronous

1. 大部分代码都是同步的
2. 同步代码一行一行执行
3. 每行代码都等待前一行完成
4. 一行需要长时间运行的代码就会阻塞代码的正常运行

## 异步Async

coordinating behavior of a program

1. 不是同时发生

```js
const img = doucu
```

### AJAX

Async Javascript And Xml

[ajax](../前后端请求/Ajax.md) 

