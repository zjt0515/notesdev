## 运算符

### 空值合并运算符??

为null或undefined的未定义值提供默认值

```js
a ?? b // if a is null or undefined, a = b
```

> [!caution]
>
> 禁止将?? 和&&和||一起使用，除非括号明确指定优先级

## 数组

```js
let arr = []
let arr = [1, 2, 3]
let arr = new Array[]
```

| 属性/方法     | 作用                       |     |
| ------------- | -------------------------- | --- |
| length        |                            |     |
| at            | []增强版，可以出现负数索引 |     |
| push/pop      | 尾部增删                   |     |
| unshift/shift | 头部增删，同时其他元素前移 |     |
|               |                            |     |
