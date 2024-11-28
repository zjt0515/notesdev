# 基本引用类型

### 

> ES中，引用类型指的是把==数据和功能组织到一起的结构==，不能与类混淆

## 原始包装类型

1. Boolean
2. Number
3. String

```js
const bo = new Boolean(true);
const no = new Number(2);
const s = new String("hello")
```

| 方法         |                        |      |
| ------------ | ---------------------- | ---- |
| `valueOf()`  |                        |      |
| `toString()` |                        |      |
|              |                        |      |
| `charAt()`   | 返回给定索引位置的字符 |      |

### 字符串String

| 方法                       | 作用                           | 参数和返回值                                 |
| -------------------------- | ------------------------------ | -------------------------------------------- |
| `startsWith()`             | 判断是否包含                   | (subs, i)<br />可以指定开始搜索位置          |
| `endsWith()`               |                                | (subs, end)<br />可以指定结束位置            |
| `includes()`               |                                | (subs, i)                                    |
| `trim()`                   | 返回删除前后空格符的字符串副本 | trimLeft()/trimRight()                       |
| `repeat()`                 | 返回重复n次的拼接字符串副本    | (n)                                          |
| `padStart()`               | 填充字符串                     | (length, string)<br />结果长度，填充的字符串 |
| `toLowerCase()toUpperCase` | 大小写转换                     | 注：toLocalexxxCase是更通用的函数            |
| `match()`                  | 匹配正则                       | 接收正则<br />返回一个数组                   |
| `replace()`                | 替换字符                       | 使用正则全局标记替换字符                     |
|                            |                                |                                              |

## 单例内置对象



## Date

```js
let now = new Date();
Date.parse("d/m/y");
Date.parse("Month day, year");

```

## RegExp

```js
const p1 = /at/g
const p2 = /[bc]at/i
```





# 集合引用类型

## Object

1. 创建 new或者字面量
2. 属性名 数值或者字符串, 数值最终还是会转为字符串



> [!warning]
>
> 字面量和new的区别：
>
> 字面量创建不会调用Object构造函数
>
> 字面量创建的好处：
>
> 1. 属性一目了然
> 2. 代码更少
> 3. 封装数据的感觉
> 4. 流行用于传递大量可选参数的方式

> {}的含义确定：表达式上下文还是语句上下文

## 数组Array



```js
// 首尾增删
arr.push()
arr.pop()
arr.unshift()
arr.shift()
```



### 搜索和位置

按照严格相等搜索，必须先拿到数组中的值才能搜索

1. `indexOf、lastIndexOf、includes`
2. 参数：`data，[startIndex]`
3. 返回值：index、boolean

> indexOf和lastIndexOf：搜索顺序相反
>
> includes：返回boolean而不是索引，是否找到至少一个

按照定义的断言函数搜索



### splic

从start开始删除count个元素，并新增之后的元素

```js
arr.splice(start，deleteCount, [elem1, ..., elemN])
```



### slice切片

顾名思义，将`[start,end)`之间的元素包装为一个新数组返回

```js
arr.slice(start, end)
// 不加参数：返回整个副本
arr.slice()
```

### concat拼接

将参数复制到原数组的副本中，返回

```js
arr.concat(arg1, arg2...)
```

> 可以传入数组，会自动解构

### forEach遍历

```js
arr.forEach(function(item, index, array){})
```

为每个元素运行一个函数

### 转换数组

```js
arr.map(function(item, index, array){})
arr.map(item => item.length)
// 原址排序
arr.sort(functionName)
arr.sort((a,b) => a-b)
// 颠倒顺序
arr.reserve()
// 将字符串转化为数组
const name = names.split(', ')
// string -> 字符数组
names.split('')
```

> 比较函数：返回正数表示大于，返回负数表示小于

## 日期和时间



## JSON

```js
// 将对象转化为string
let json = JSON.stringify(student);
```

> [!caution]
>
> 对象中不得出现循环引用：即引用了另一个对象，它又引用了该对象
>
> `stringify`会跳过的属性：
>
> 1. 函数属性
> 2. Symbol类型
> 3. 存储undefined的属性

