## 对象的隐藏属性 __ proto __ 



	1. null
	1. 另一个对象的引用

> 从对象中读取一个缺失属性，会自动从原型中获取该属性
>
> 原型链可以很长

> [!caution]
>
> 原型链不能形成闭环
>
> __ proto __ 的值只能是对象/null，其他值被忽略

##  原型继承

### 构造函数的prototype属性

Son.prototype区别于son.__  proto  __

```js	
Son.prototype = new Father()
// 以后每次创建Son的实例，都会将其__proto__指向Son.prototype，也就是这里赋值的父类实例
```

函数默认的prototype属性：一个包含 指向函数本身的constructor属性 的对象

`{constructor: Function}`

```js
console.log(Bus.prototype.constructor === Bus); // true
```

> [!warning]
>
> 普通对象的prototype属性只是普通的属性
> prototype属性仅当设置在一个构造函数上，且通过new调用该构造函数时，才有这种影响