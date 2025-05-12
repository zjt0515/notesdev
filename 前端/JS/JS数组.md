## 数组Array

> 数组就是对象，可以调用数组方法，

js数组是无类型的

索引可以从0-2^32^-2

数组大小动态，创建时无需声明固定大小，数组大小变化时不用重新分配空间

- 稀疏数组：索引不连续
- 非稀疏数组：索引连续，length属性就是数组元素个数

```js
// 创建数组
let empty = [];
let arr = [1, 2];
let misc = [1.1, true, 'a'];
let arr2 = [base, base + 1];
// 省略值为undefined，允许可选的结尾逗号
let undefinedArr = [,,1,]

let a = new Array();
// 首尾增删
arr.push()
arr.pop()
arr.unshift()
arr.shift()
```



## 搜索和位置

按照严格相等搜索，必须先拿到数组中的值才能搜索

1. `indexOf、lastIndexOf、includes`
2. 参数：`data，[startIndex]`
3. 返回值：index、boolean

> indexOf和lastIndexOf：搜索顺序相反
>
> includes：返回boolean而不是索引，是否找到至少一个

按照定义的断言函数搜索



## 数组方法

| 数组方法                                                     | 描述                                               | 返回值         | mutated?<br />是否改变原数组 | 额外用法             |
| ------------------------------------------------------------ | -------------------------------------------------- | -------------- | ---------------------------- | -------------------- |
| `slice(start?: number, end?: number)`                        | 提取子数组                                         | 子数组         | NO                           | 不写参数用于获取副本 |
| `splice(start: number, deleteCount?: number)`                | 删除子数组                                         | 被删除的子数组 | Y                            |                      |
| `splice(start: number, deleteCount: number, ...items: string[])` | 删除元素的同时，添加元素<br />一般deleteC ount = 0 |                | Y                            |                      |
| `concat(...items: ConcatArray<T>[]):`                        | 连接数组                                           | 连接后的新数组 | NO                           |                      |
| `sort(compareFn?: ((a: string, b: string) => number) `       | 数组排序                                           | 排序后的原数组 | Y                            |                      |
| `reverse()`                                                  | 翻转                                               | 被改变的数组   | Y                            |                      |
| `join(separator?:T)`                                         | 数组元素链接为字符串                               | 连接后的字符串 | NO                           |                      |

### splice拼接

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

### concat连接

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

## 遍历数组

1. for of 循环
2. forEach数组方法

```js
for (const movement of movements) {
	
}
movements.forEach(function(movement){
})
```

> [!tip]
>
> 区别：
>
> forEach loop中无法使用continue和break



遍历中的索引访问

```js
for(const [i, movement] of movements.entries()){
  
}
movements.forEach(function(movement, index, array){

})

```

> 写法上，关键在于默认传入参数的顺序
>
> entries()方法返回值
>
> 回调函数参数

### map和set中的forEach

```js
const currencies = new Map([
  ['USD', 'United States dollar'],
  ['EUR', 'Euro'],
  ['GBP', 'Pound sterling'],
]);

currencies.forEach(function(value, key, map){
  
}) 
```

> [!tip]
>
> set的forEach方法的回调函数参数中，第二个参数和第一个参数重复
>
> 可以使用_名称，意味着是一个throwaway variable，代表占位符，没有意义