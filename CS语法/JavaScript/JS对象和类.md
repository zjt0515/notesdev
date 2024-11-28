# 对象

```js
// 字面量
const user = {
  key: value,
  "Multi Words": value
}

user.key
delete user.key
// 循环遍历key
for (key in object){
}
// 判断属性是否存在
alert("key" in user)
```

> **访问属性的其他方式**
>
> 点符号要求 `key` 是有效的变量标识符
>
> 可以使用`user.[key], user.["Multi Words"]`，同时可以使用变量来指定key，形式上更加灵活



> **key的顺序**
>
> 整数属性key按照从小到大，其他属性按照创建顺序显示
>
> “整数属性”指的是一个可以在不做任何更改的情况下与一个整数进行**相互**转换的字符串或整数。
>
> **访问到不存在的key**
>
> user.key === undefined，不会报错

## 对象引用和复制

> **赋值了对象的变量存储的不是对象本身，而是该对象“在内存中的地址” —— 换句话说就是对该对象的“引用”。**
>
> **当一个对象变量被复制 —— 引用被复制，而该对象自身并没有被复制。**

```js
// 克隆与合并
Object.assign(dest, [src1, src2...])

// 深层克隆
// 自行递归或者采用现有实现lodash
let user = {
  name: "John",
  sizes: {
    height: 182,
    width: 50
  }
};


```

## 内存管理

```js
let user ={ name: "zjt"}
user = null
//此时{ name: "zjt"}变为不可达，垃圾回收器回收释放内存
```

# 类

```js
class Person {
  // 构造器
  constructor(){
    
  }
}
```

## 构造器

new的过程：

1. 在内存中创建一个新对象。
2. 这个新对象内部的[[Prototype]]指针被赋值为构造函数的prototype属性。
3. 构造函数内部的this被赋值为这个新对象（即this指向新对象）。
4. 执行构造函数内部的代码（给新对象添加属性）。
5. 如果构造函数返回非空对象，则返回该对象；否则，返回刚创建的新对象。

> [!caution]
>
> 如果没有什么引用新创建的this对象，那么这个对象会被销毁





> [!tip]
>
> ```js
> class Person{}
> typeof Person; // function
> ```
>
> 类是一种特殊函数
>
> 

## 类继承

```js
class Bus extends Vehicle {}
```

