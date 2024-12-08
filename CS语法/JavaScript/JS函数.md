## 箭头函数

```js
function fun() {
  // func body  
}
```

## ...rest

rest参数
实现任意数量参数的函数

`...变量名`声明一个数组，同时将剩余参数收集起来，存入这个数组

```js
function test(...args){
  for(let arg of args) {}
}
```

> [!tip]
> rest参数只能放到参数列表的末尾

> [!warning]
> 区分：另一个...spread
> 在其他地方使用...arr：表示将一个可迭代对象arr展开
> 展开到参数列表/另一个可迭代对象/浅拷贝....

## 弃用？arguments

可以在函数内部访问的
一个类数组，存储了所有的函数参数值

## 嵌套函数

在一个函数中可以创建同时调用一个新的函数

```js
function sayHiBye(firstName, lastName) {
  // 辅助嵌套函数使用如下
  function getFullName() {
    return firstName + " " + lastName;
  }
  alert( "Hello, " + getFullName() );
  alert( "Bye, " + getFullName() );
}
```

## 词法环境

> 在 JavaScript 中，每个运行的函数，代码块 {...} 以及整个脚本，都有一个被称为 词法环境（Lexical Environment） 的内部（隐藏）的关联对象。

1. 环境记录对象，属性：所有局部变量
2. 外部词法环境的引用(没有就为null)

## 调度，计划调用

```js
// (func, delay(ms))
let returnedTimeId = setTimeout(()=>{}, 3000)

// (func, interval)
let timeId = setInterval(()=>{}, 2000)
// 取消调度
clearTimeout(timeId)
```

> [!caution]
> 不要这样做
> `setTimeout(say(), 3000)`
> func()表示调用函数，这里希望得到一个函数的引用
> 因为调用函数，所以传入的实际上是该函数的返回值
