ES6新引入的异步编程解决方案

可以在启动异步任务后再绑定回调函数 
解决回调地狱问题，支持链式调用

## Promise基本使用

构造函数
`Promise(excutor){}`

```js
let x = new promise((resolve,reject)=>{
  // 这里的代码是立即调用的（同步执行
  if(){
    reslove()
  }else{
    reject()
  }
})
x.then
```



指定成功和失败的回调
`Promise.prototype.then(onResolved, onRejected ) =>{}`

```js
p.then(
  (value) => {
    alert("成功" + value);
  },
  (reason) => {
    alert("失败" + reason);
  }
);
```



指定失败的回调
`Promise.prototype.catch(onRejected) =>{}`

```js
p.catch( reason =>{})
```



### 静态方法

返回一个成功或失败的Promise对象
`Promise.resolve(value)=>{}`

```js
//传入非Promise对象，返回成功promise对象
//传入Promise对象，这个Promise的结果决定 resolve结果
let basep = Promise.resolve(521);
let p2 = Promise.resolve(new Promise((reslove,reject)=>{
  resolve('OK')/reject('Error')
}))
//PromiseResult == 'OK'/'Error'
console.log(p2)
```



返回一个失败的Promise
`Promise.reject(reason)=>{}`

> [!caution]
>
> 对于失败的Promise，一般要有失败回调，否则会报错



## Promise理解

### 状态PromiseState

- pending
- resolved / fulfilled
- rejected

状态改变(只能改变一次)

- pending -> resloved
- pending -> fulfilled



### 结果PromiseResult

保存异步任务成功或者失败的结果

 只有resolve/reject函数可以修改result
