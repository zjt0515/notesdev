## 同步和异步概念

### 同步Synchronous

1. 大部分代码都是同步的
2. 同步代码一行一行执行
3. 每行代码都等待前一行完成
4. 一行需要长时间运行的代码就会阻塞代码的正常运行

### 异步Async

coordinating behavior of a program

没有得到结果之前，可以继续执行后续代码，
异步任务完成后，一般通过回调通知调用者

异步代码牵扯到多个线程

异步代码， 一般都需要耗时：

1. `setTimeout(fn, n)`：ns后运行时将fn推到消息队列上等待执行
2. setInterval
3. Ajax/Fetch
4. 事件绑定



1. 不是同时发生

```js
const img = doucu
```

### AJAX

Async Javascript And Xml

[ajax](../前后端请求/Ajax.md) 



## Event Loop机制

事件循环机制

1. js是单线程运行的，为了防止代码阻塞，代码分为同步和异步
2. 异步要基于回调来实现
3. eventloop是异步回调的实现原理

JS如何执行：

1. 从前到后，一行一行同步执行
2. 某一行报错，停止下面代码执行
3. 先将(调用栈的)同步代码执行完，再执行异步代码

调用栈/执行栈(同步代码)

回调队列/任务队列(异步代码)

同步代码执行完毕，内核启动event loop，每次循环在回调队列中寻找，有则放入调用栈执行

```js
console.log(1)
setTimeout(function(){ console.log(2) }, 0)
console.log(3)
// 1 3 2
```



 ```js
 document.body.appendChild(el)
 el.style.display = 'none'
 ```

> 会不会一闪而过？
>
> 取决于有无竞争条件？

主线程

网页上大部分活动都具有确定性顺序，不会同时运行多段代码区修改同一处DOM

> 总结
>
> 1. 同步代码，一行一行放入调用栈执行
> 2. 遇到异步，先记录下来(在宿主环境 )，等待时机（定时/网络请求/事件触发）
> 3. 时机一到，放入回调函数队列
> 4. 等到调用栈为空，eventloop开始工作,
> 5. 循环查找回调队列，如有则移动到调用栈执行，
> 6. 然后继续循环查找

## 异步编程模式

为了让后续代码能够使用 x，异步执行的函数需要在更新 x 的值以后通知其他代码。

```js
let x = 3;
setTimeout(() => x = x + 4, 1000);
```

设计一个能够知道 x 什么时候可以读取的系统是非常难的。



## 回调callback 

将函数作为参数传递给另一个函数，在合适的时候调用这个函数

```js
function f(callback){
  callback();
}
```

回调函数的缺点：

1. 高度耦合，维护差
2. 不能直接return

## 事件驱动

> 优点：
>
> 1. 去耦合
> 2. 便于模块化实现
>
> 缺点：
>
> 1. 运行流程不清晰
> 2. 代码阅读不便

## Promise

现代异步编程的核心，将嵌套的回调变成链式调用，本质上还是回调

> 优点：
>
> 1.链式调用，流程清晰
>
> 缺点：
>
> 1. 代码冗余，看起来不简洁
> 2. 无法取消promise
> 3. 错误需要通过回调函数捕获

作为异步操作的未来结果的一个占位符，未来值的容器

build a promise



> 一个由 executor 完成的工作只能有一个结果或一个 error
> 即只能调用一次resolve或者一次reject，剩余的都会被忽略

### promise.state

![image-20250322135826181](./images/image-20250322135826181.png)

1. 等待状态 pending：初始值
1. 成功态 fulfilled：调用resolve后
1. 失败态 rejected：调用reject后



### promise.result

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
promise.all()
promise.
```

then
第一个函数参数在resolved且接收到value后执行
第二个函数参数在rejected且接收到error后执行

catch
接收的函数参数在rejected且接收到error后执行

### finally



## Generator

可以控制函数执行

## async/await

> 语义更好
>
> async蝴蝶效应

```js
async functikon fn() { return 100 }
(async function () {
  const a = fn()
  const b = await fn()
})()
```

