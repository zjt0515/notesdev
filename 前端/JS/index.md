## 参考资料

### 文档

1. https://es6.ruanyifeng.com/#docs/array
2. https://liaoxuefeng.com/books/javascript/quick-start/index.html
3. https://zh.javascript.info/
4. https://wangdoc.com/javascript/basic/
5. https://github.com/javascript-tutorial/zh.javascript.info
6. ECMA：https://262.ecma-international.org/15.0/index.html


### 视频

1. jonas https://www.bilibili.com/video/BV1vA4y197C7
    1. https://github.com/jonasschmedtmann/complete-javascript-course/blob/master/11-Arrays-Bankist/starter/script.js

### 书籍


1. 犀牛书
2. 红宝书



目录

- [ ] 121-125 string
- [ ] 126-139 func
- [ ] 140-167 数组

## js引入

内部脚本：在html中任意位置(一般是body底部)任意数量使用script

外部脚本：
```html
<script src="js/demo.js"></script>
```



## 常量变量运算符

常量`const y = 4;`

### 变量

`let x = 3;`

变量类型：

1. number
2. string string里的每个都是只可读
3. boolean
4. object
5. undefined

### 运算符

** 乘方
== 等于
!== 不等于

## 输入输出

- 通过html
- 通过Ajax与WebSocket从服务器端获取输入
- 标准输入

```js
let fs = require('fs');
let buf = '';
process.stdin.on('readable', function () {
    let chunk = process.stdin.read();
    if (chunk) buf += chunk.toString();
});

process.stdin.on('end', function () {
    let q = buf.split('\n');
    let a = parseInt(q[0]), b = parseInt(q[1]), c = parseInt(q[2]), d = parseInt(q[3]);
    console.log(a + b + c + d);
    
    //求和
    buf.split('\n').forEach(function(line) {
        let tokens = line.split(' ').map(function(x) { return parseInt(x); });
        if (tokens.length != 2) return;
        console.log(tokens.reduce(function(a, b) { return a + b; }));
    });
    
    //求差
    let [a, b, c, d] = buf.split("\n").map(x => {return parseInt(x)});
    console.log(`DIFERENCA = ${a*b-c*d}`);
    
    //求距离
    let lines = buf.split('\n');
    let [x1, y1] = lines[0].split(' ').map(x => {return parseFloat(x)});
    let [x2, y2] = lines[1].split(' ').map(x => {return parseFloat(x)});
    
    let dx = x1 - x2;
    let dy = y1 - y2;
    
    console.log(Math.sqrt(dx * dx + dy * dy).toFixed(4));
    
    
});
```



## 判断循环

同C++

```js
//对于枚举对象或者数组
for (let p of money) {
	let cnt = parseInt(n / p);
    console.log()


}
```

- of：枚举值
- in ：枚举下标

## 对象

类似C++中的map

key : value,

- key是字符串

- value 可以是变量数组对象函数

```js
let person = {
	name: "zjt",
    age: 18,
    money: 0,
    friends: ['bob', 'alice'],
    add_money: function (x) {
		this.money += x;
    },
    clothes: {
        color: "red",
        price: 20,
    },
    eat: function() {
		alert("eating~");
    }
}
```

### Array

`let a = [1, 2, 'op', [4, 5]];`

变量、数组、对象、函数。

- [index]
- length
- push()
- pop()
- splice(a, n) 删除从a开始的n个元素
- sort() 排序

### String

### Json

json：javascript object notation

所有的key必须外加双引号

value：1145，"imstring"，[1,2,3]，{}



### BOM

### DOM

## 函数

```js
定义方式
function add(a, b) {
    return a + b;
}

let add = function (a, b) {
    return a + b;
}

let add = (a, b) => {
    return a + b;
}
```

箭头函数和普通函数



## 类

不存在私有成员 

```js
class Point {
    constructor(x, y) {
        this.x = x;
        this.y = y;

        this.init();
    }
    init() {
        this.sum = this.x + this.y;
    }
    toString(){
        return `(${this.x}, ${this.y})`;
    }
}
```

静态变量和函数 都用类名访问

### 继承

```js
class ColorPoint extends Point {
    constructor(x, y, color) {
        super(x, y);
        this.color = color;
    }
}
```

## 事件

`addEventListener`函数为元素绑定事件的触发函数

### 鼠标

`click`：鼠标左键点击
`dblclick`：鼠标左键双击
`contextmenu`：鼠标右键点击

`mousedown`：鼠标按下，包括左键、滚轮、右键
`mouseup`：鼠标弹起，包括左键、滚轮、右键

- `event.button`：0表示左键，1表示中键，2表示右键

### 键盘

`keydown`：某个键是否被按住，事件会连续触发
 `event.code`：返回按的是哪个键
`event.altKey、event.ctrlKey、event.shiftKey`分别表示是否同时按下了alt、ctrl、shift键。
`keyup`：某个按键是否被释放
event常用属性同上
keypress：紧跟在keydown事件后触发，只有按下字符键时触发。适用于判定用户输入的字符。
event常用属性同上
keydown、keyup、keypress的关系类似于鼠标的mousedown、mouseup、click

### 表单

focus：聚焦某个元素
blur：取消聚焦某个元素
change：某个元素的内容发生了改变

### 窗口

需要作用到window元素上。

resize：当窗口大小放生变化
scroll：滚动指定的元素
load：当元素被加载完成





## Jquery
