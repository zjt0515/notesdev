###  let & var

`let 标识符 = ...,标识符='s',标识符=[]`

> 同名变量不能重复声明，防止变量被污染
> 支持块级作用域：全局、函数、eval、{ }
> 不影响作用域链，即子作用域可以访问父作用域的数据
> 不存在变量提升，即变量声明之前不允许使用

```js
let items = document.getElementByClassName('item')
for(var i = 0; i< items.length;i++){
    item[i].onclick = function(){
        items[i].style.background = 'black'
    }
}
// var没有块级作用域概念，最终被赋为length
// let有块级作用域概念，可以在for循环的不同块级中担任不同的值
```

### const 常量

> 声明后必须赋初始值，之后不能修改
> 常量命名使用全大写
> 支持块级作用域
> 对于数组和对象常量，只要保存的地址值不变就可以
>
> 因此使用const声明数组和对象，可以避免误操作(不是常量可以不大写)

```js
const SCHOOL = 'NJUPT'
const TEAM = ['Z','G']
```

### Destructuring 解构赋值

从对象中获取数据

- 使用{}
- 名称对应(变量名提取对应的属性名)

从数组中获取数据

- 使用[]
- 顺序对应，不依赖属性名称

```js
let [p1,p2] = TEAM;
let {name, age, study} = {
    name: '我',
    age: 123,
    study: function(){
    }
}
```





### ...操作符(rest/spread for数组/对象)

...只能放在解构模式的最后一个

```jsx
// 数组
// 将第三个及之后的元素创建为一个新的数组
let [p1,p2,...otherPlayers] = Team.getPlayers();
const newBooks = [...Books, "Book1"]
```



```jsx
// 对象
const updateBook = {
  ...Book,
  newProp: "test", // 添加新属性
  pages: 1 // 对原属性进行覆盖(后面的覆盖前面的)
}
```



### Template Literals 模板字符串

> 字符串中可以出现换行符
> 模板字符串内可以使用 ${} 进行变量拼接

```js
let str = `我是模板
字符串`
let output = `我的学校是 ${SCHOOL}`
```

### Ternaries三元运算符

```jsx
pages > 100 ? 'over a hundred  ' : 'less than 100'
```





### (对象简化写法)

> 要求已有的变量名和属性名是一致的，因为简化写法中变量名会直接成为对象里的属性名

```js
let name = '
let changeName = function(){
    
}
const people = {
    name,//name:name,
    changeName//changeName:changeName
    improve(){//improve: function(){ }
    }
}
```

### ArrowFunction箭头函数

```jsx
const year = (str) => str.split('-')[0];
```



> this 是静态的，始终指向函数声明时所在作用域下的 this
> 不能作为构造函数实例化对象
> 不能使用 arguments 变量，(函数内部的 arguments 是用来保存实参的
>
> 可省略的情况：
>
> 1. 形参只有一个，可以省略 ( )
> 2. 返回值只有一个，可以省略 { return }
>
> 建议：
>
> 1. 单行函数建议使用
> 2. 回调函数建议使用

```js
let fn1 = function(){
    
}
let fn2 = () => {
    return this.name;
}
//使用call命令让school对象调用，检查this是否改变
fn1.call(school)//this从window变成school
fn2.call(school) //this不变，还是全局对象window

// 下面的方法是不被允许的
let Person = (name) => {
    this.name = name;
}
```

```js
// 箭头函数的应用
let ad = document.getElementById('id')
ad.addEventListener("click",function(){
    //保存this的值
    let  self = this
    setTimeout(function(){
        //setTimeout的this是window
        self.style.background = 'pink'
    },2000)
    
    //箭头函数，this指向声明时所在作用域的this
    setTimeout(()=>{
        this...
    },2000)
})
    
const arr = [1,2,3,4,5,6]
//filter筛选一个数组，返回被筛选的数组
const result = arr.filter(function(item){
    if(item % 2 === 0){
        return true
    }else return false
})
const result = arr.filter(item=> item%2 === 0)
// 箭头函数适合与this无关的回调，如定时器，数组的方法回调
// 不适合 与this有关的回调，如事件回调，对象的方法(箭头函数中的this不会指向本对象)
```

### OptionalChaining可选链

当?前面不是undefined或null，链才会继续

### 空值合并运算符??



?? 后面添加默认值

```jsx
const op = book.review?.reviewsCount ?? 0;
```



### 函数参数初始值

> 不传参数且没有初始值，默认是undefined
> 具有默认值的参数，一般位置靠后
>
> 解构赋值式函数参数

```js
function add(a,b,c=10){
  return a+b+c
}

//解构赋值式函数参数
function connect({host="127.0.0.1", username,password,port}){
  let {host,username} = options
}
connect({
  host:'localhost',
  username:;'root',
  password:'root',
  port:3306
})
```

### rest参数

> 函数中 arguments对象 自动保存了函数的实参，
>
> rest参数必须手动放到形参末尾
>
> rest参数形式：...args
> 调用方式：args
> args本质上是数组，可以使用数组相关的方法

```js
function date(a,b,...args){
  console.log(args);
}
date('123','321')
```

### ...拓展运算符(spread)

将数组转换为，逗号分隔的参数序列

```js
const sbs = ['Zmjkk', 'nobody']
...sbs 等价于'Zmjkk', 'nobody'
```

数组合并、克隆

```js
const nju = ['1','2']
const njupt = ['3']
const njunjupt = [...nju,...njupt]
const njupt2 = [...njupt]
```

将伪数组转化为真正的数组

```apl
#example1
const divs = document.querySelectorAll('div')
console.log(divs)
const divList = [...divs]
#example2
function add(a,b,c){
	const arguList = [...arguments]
}
```



## Array Function Method

### map

返回一个映射数组
传入一个回调函数，每个元素都会调用该函数，得到新元素组成新数组

```jsx
const s = [1, 2, 3].map((n) => n + 1);
const titles = books.map(book => book.title);
const newObj = books.map(book=>(
	{
    title: book.title,
    author:book.author
  }
))
```

### filter

筛选元素组成新数组





### reduce

将整个数组简化为一个值

初始值根据不同用途可以是任意类型

1. 第一个参数是累加器，存储迭代的中间值

```js
books.reduce((acc, book) => acc + book.pages, 0);

```

### sort

返回负数，以升序排列

返回正数，以降序排列

> 会更改原数组数据

```js
array.sort((a,b) => a-b)
// 不改变原数组的方法
const newArr = arr.slice().sort();
```





### Symbol



### 迭代器 Iterator

为不同数据结构提供统一访问机制
如Array、Arguments、Set、String、TypedArray、NodeList

使用`for let value of ...`

```js
const List = ['1','2','3','4']
for(let x of List){}

let iterator = List[Symbol.iterator]()
```

工作原理：

1. `symbol,iteraoter` 函数创建指针
2. 第一次调用`next()`方法，指针自动指向第一个成员
3. 不断调用`next()`，直到指向最后一个成员
4. 每次调用`next()`返回一个包含`value`和`done`属性的对象

 ```js
 const cls = {
   name:'一',
   stus:[
     '123',
     '132',
     '321',
   ],
   [Symbol.iterator](){
     let index = 0
     return {
       next: ()=>{
         if(index < this.stus.length){
         	const result = { value:this.stus[index],done:'false' }
           index ++;
           return result;  
         } else {
           return { value: undefined, done: true}
         }
       }
     }
   }
 }
 for(let v of cls){
   cla.stus.forEach();
 }
 ```

### 生成器

生成器是一个进行异步编程的特殊的函数

> 生成器函数中一般有 `yield xxx`，yield是一个函数的分隔符
>
> 生成器的不同部分代码的执行由函数返回的迭代器的`next()`操作，next()每次返回一个对象，包含yield后的内容和迭代器的done

```js
function * gen(){
  console.log("hello generator")
  yield '1';
}
let iterator = gen();
iterator.next();
iterator.next();
iterator.next();
```





## 通过`bind()`函数绑定this值

```js
const talk = person.talk.bind(person); // 为talk绑定this
talk(); //如果没有bind， 输出window 没有东西调用talk，默认是window调用
```





## `export default`

import的时候不能加大括号，且`export default`唯一



## 分号争论

可以不写分号，但是遇到换行必须要加小括号



## key和value相同

可以只写key

# 类

```js
class Person {
  constructor() {}
  get name(){ return this.name }
  static test() {}
}
const me = 
```

new的细节：

1. 内存中创建新对象
2. prototype指针赋值为构造函数的同名属性
3. 内部this指向新对象
4. 执行构造函数
5. 返回对象

类就是一种特殊的函数

```js
class Person {} 
console.log(Person);         // class Person {} 
console.log(typeof Person);  // function
```

使用instanceof操作符检查一个对象与类构造函数，以确定这个对象是不是类的实例

```js
class Person {} 
let p = new Person(); 
console.log(p instanceof Person); // true
```

