## 定义函数

### 函数声明

函数声明提升，JS引擎先读取函数声明，再执行代码

```js
sayHi();  
function sayHi() { 
  console.log("Hi!"); 
}
```

### 函数表达式

没有提升，需要先赋值给一个变量，再调用

```js
// 匿名函数的函数表达式
let functionName = function(arg0, arg1, arg2) { 
  // 函数体  
};
```

立即调用的函数表达式(立即调用的匿名函数)

```js
// IIFE模拟块级作用域
(function() { 
  // 块级作用域  
})();
// ES6
```



## 参数

### 默认参数default parameters

```js
const bookings = [];

const createBooking = function (
  flightNum,
  numPassengers = 1,
  price = 100 * numPassengers
) {
  // es5 方式参数默认值
  // numPassengers = numPassengers || 1;
  // price = price || 100;

  const booking = {
    flightNum,
    numPassengers,
    price
  };
  console.log(booking);
  bookings.push(booking);
};
// 没有传递的参数，默认为undefined
createBooking('LH123');
createBooking('LH123', 2);
createBooking('LH123', 2, 200);
createBooking('LH123', undefined, 1000);

```

### 参数传递(值传递)

JS中只有值传递，没有引用传递

原始类型传递值的拷贝，不会改变原来的值

引用类型传递地址，会改变原来的值

## higher-order函数

> 函数也是value，可以存储到变量中



 





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

## 函数内部

### arguments

function关键字定义时，在函数内部访问的一个类数组对象，存储了所有的函数参数值

同时还有一个callee属性，指向arguments对象所在函数的指针

```js
function factorial(num) { 
  if (num <= 1) {  
    return 1; 
  } else { 
    // 递归函数，与函数名解耦
    return num * arguments.callee(num - 1); 
  } 
}
```

### this

标准函数，this引用：把函数当成方法调用的上下文对象

```js
window.color = 'red';  
let o = { 
  color: 'blue' 
}; 
 
function sayColor() { 
  console.log(this.color); 
} 
// 全局上下文调用，this指向window
sayColor();    // 'red' 
// 对象方法调用，this指向该对象
o.sayColor = sayColor; 
o.sayColor();  // 'blue'
```

箭头函数，this引用：**定义箭头函数**的上下文

```js
window.color = 'red';  
let o = { 
  color: 'blue' 
}; 
// 在window上下文中定义箭头函数
let sayColor = () => console.log(this.color); 
 
// 一旦定义固定了，和方法调用的上下文无关
sayColor();    // 'red' 
 
o.sayColor = sayColor; 
o.sayColor();  // 'red'
```

> 在事件回调或定时回调中调用某个函数时，this值指向的并非想要的对象。此时将回调函数写成箭头函数就可以解决问题。这是因为箭头函数中的this会保留定义该函数时的上下文
>
> ```js
> function King() {  
>   this.royaltyName = 'Henry'; 
>   // this 引用 King 的实例 
>   setTimeout(() => console.log(this.royaltyName), 1000); 
> } 
> 
> function Queen() { 
>   this.royaltyName = 'Elizabeth'; 
>  
>   // this 引用 window 对象 
>   setTimeout(function() { console.log(this.royaltyName); }, 1000); 
> } 
>  
> new King();  // Henry 
> new Queen(); // undefined
> ```
>
> 

### new.target

## 函数对象的属性和方法

### length

命名参数的个数

### prototype

保存引用类型所有实例方法，由所有实例共享

### apply(this, Array实例/aruguments)

以指定的this值来调用函数

主要用于控制函数调用上下文，即函数体内this值



### call(this, ...argArray)

以指定的this值来调用函数，区别是参数要逐个传递

## 闭包closure



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
