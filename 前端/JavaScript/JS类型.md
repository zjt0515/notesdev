# 数据类型

1. Number
2. BigInt
3. String
4. Boolean
5. null
6. undefined
7. Object
8. Symbol

typeof运算符 以字符串的形式返回类型

> function类型属于object，但是typeof会对function区分对待
>
> js没有char类型
>

## Number

```js
let billion = 1e9;
let billion = 1_000_000_000;
let a = 0b1101;
let b = 0o777;
let c = 0xff;

let nan = NaN;
let inf1 = Infinity;
let inf2= -Infinity;

alert( 1e500 ); // 溢出 Infinity
```



1. 1
2. 1.0
3. 1.5
4. NaN（特殊值）
5. (-)Infinity（特殊值）

> NaN
>
> 不等于任何东西，包括自身
>
> 可以通过`isNaN`函数将参数转化为Number，然后判断是否为NaN



> Object.is(a,b)和a===b
>
> 前者可以比较NaN和NaN，返回true，同时可以区分0和-0

```js

// 判断是否为整数
Number.isInteger(10);    // true
Number.isInteger(10.0);  // true
Number.isInteger(10.5);  // false
Number.isInteger('10');  // false，'10' 是字符串
Number.isInteger(NaN);   // false
```

| Number类方法 |                                                              |
| ------------ | ------------------------------------------------------------ |
| isNaN        | 将其参数转换为数字，然后测试它是否为 `NaN`                   |
| isFinite     | 将其参数转换为数字，如果是常规数字而不是 `NaN/Infinity/-Infinity`，则返回 `true` |
| isInteger    | 判断是否为整数                                               |

| Math类方法 |              |                                             |
| ---------- | ------------ | ------------------------------------------- |
| max        | 最大值       | 强制转换为数字类型，但不会解析，结果会为NaN |
| min        | 最小值       |                                             |
| sqrt       | 平方根       | 使用幂等`25 ** 1/2`                         |
| PI         | 常数π        |                                             |
| random     | 0-1的随机数  |                                             |
| trunc      | 截断小数部分 |                                             |

### 不精确

> 基于64位格式IEEE-754表示的PHP、Java、Perl、Ruby都有
>
> 二进制数字无法精确存储十进制中的0.1、0.2，IEEE-754 通过将数字舍入到最接近的可能数字来解决这个问题，

## 引用类型

> ES中，引用类型指的是把==数据和功能组织到一起的结构==，不能与类混淆

## String

| 方法         |                        |     |
| ------------ | ---------------------- | --- |
| `valueOf()`  |                        |     |
| `toString()` |                        |     |
|              |                        |     |
| `charAt()`   | 返回给定索引位置的字符 |     |

```js
// 定义字符串
let single = '123';
let double = "123";
let backticks = `123`;
const s = new String("hello");

// 字符串跨行
let xxx = `
	1
	2
	3
`;

// 获取字符串长度属性
xxx.length;
// 没有找到字符，[]返回undefined
str[index];
// 没有找到，返回第一个空字符
str.charAt(index);
// 遍历字符
for(let char of "hello"){
  
}

```

> [!caution]
>
> 字符串不可修改
>
> ```js
> str[0] = "z"; //error
> 
> str = 'h' + srt[1];
> ```
>
> 



### 转义字符

| 字符     | 描述 |
| -------- | ---- |
| \n       |      |
| \r       |      |
| \ ', \ " |      |
| \ \      |      |
| \t       |      |
| \b \f \v |      |
| \xXX     |      |
| \uXXXX   |      |

### String方法

| 方法                       | 作用                                 | 参数和返回值                                 |
| -------------------------- | ------------------------------------ | -------------------------------------------- |
| `indexof()`                | 从pos位置查找子字符串substr          | (substr, pos)<br />没有找到返回-1            |
| `startsWith()`             | 判断是否包含                         | (subs, i)<br />可以指定开始搜索位置          |
| `endsWith()`               |                                      | (subs, end)<br />可以指定结束位置            |
| `includes()`               |                                      | (subs, i)                                    |
| `trim()`                   | 返回删除前后空格符的字符串副本       | trimLeft()/trimRight()                       |
| `repeat()`                 | 返回重复n次的拼接字符串副本          | (n)                                          |
| `padStart()`               | 填充字符串                           | (length, string)<br />结果长度，填充的字符串 |
| `toLowerCase()toUpperCase` | 大小写转换                           | 注：toLocalexxxCase是更通用的函数            |
| `match()`                  | 匹配正则                             | 接收正则<br />返回一个数组                   |
| `replace()`                | 替换字符                             | 使用正则全局标记替换字符                     |
| `slice(start[,end])`       | 获取字串<br />返回start到end(不包括) | 允许负数                                     |
| `substr(start[, length])`  | 获取子串<br />允许指定长度           | 允许start负数                                |
| `substring(strat, end)`    |                                      | 负数视为0                                    |

## Boolean

假值：

1. 0, -0
2. "" 空字符串
3. null
4. undefined
5. NaN

真值：

1. 1, -1
2. "hello" 非空字符串
3. [] {} 空数组 空对象
4. function(){}
5. Inf

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

## 类型转换

### 显示类型转换

```js
// 自动类型转换(隐式)
'4' - '3' // 1
"String" + 2 // 当+的一个操作数是字符串
!!x // 等价于Boolean()

// 显式类型转换 使用函数
Number() // 返回数值或NaN
String() //
Boolean()
```

### Number()

示例

 ```
 parseInt('42 cats') // 42
 Number('42 cats') // NaN
 Number({a: 1}) // NaN  
 Number([1, 2, 3]) // NaN
 Number([5]) // 5
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

> 

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
