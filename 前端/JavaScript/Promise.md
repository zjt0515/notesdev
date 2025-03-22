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





### promise对象

![image-20250322135826181](./images/image-20250322135826181.png)

属性，不同的状态

1. state
    1. pending
    2. settled
        1. fulfilled
        2. rejected
2. result
    1. undefined
    2. value 
    3. error

### consume a promise



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

