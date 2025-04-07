## 参考资料

文档

-  **TypeScript 教程 b ryf**https://wangdoc.com/typescript/intro
- ts中文手册https://typescript.bootcss.com/classes.html
- ts文档：https://www.tslang.cn/docs/home.html
- https://ts.xcatliu.com/
- https://github.com/xcatliu/typescript-tutorial/?tab=readme-ov-file

书籍

- 深入理解TShttps://jkchao.github.io/typescript-book-chinese/typings/indexSignatures.html

## 介绍

融合了后端面向对象思想的超级版js

```shell
// 生成package.json
npm init -y
// 项目安装ts
npm install typescript -D
// 生成tsconfig.json
tsc --init
```

ts项目配置文件：`tsconfig.json`



1. 编译时静态类型检测
2. TS特有类型和泛型
3. d.ts声明文件
4. 灵活性，anyscript

## 环境配置

### 编译ts

```
// 1
ts-node index.ts
// 2
tsc index.ts
node index.js
// 3
"scripts": {
  "start": "ts-node yourFile.ts"
}
```







## 类型推断

对于没有指定类型的变量，会自动根据值来推断类型，同时在使用该变量时，ide会自动提示对应的方法
且修改变量为其他类型时时会报错，
对于字面量创建的对象、数组同样会自动进行类型推断

如果类型不匹配（对于对象类型，属性名和属性值的个数和类型都要一一匹配），就会报错

## 类型标注

适合用于复杂对象类型，对于基本类型使用ts的自动推断就足够

```ts
// 变量:类型
let n:number = 1
let product: {
  title: string;
  price: number;
} = {
  title: "car",
  price: 21000
}
```



### interface

拓展interface

多个同名的inerface自动合并

```ts
interface Product {
	title: string;
	price: number;
}
interface Product {
  count: number
}
```

### 嵌套对象类型标注

```ts
interface Product {
	title: string;
	price: number;
  position: Position;
}
interface Position {
  x: number;
  y: number;
}
```

### 数组类型标注

```ts
let nums1: number[] = [1,2]
let nums2: Array<number> = [1,2]
let products: Product[] = [{...}]
```

### 标注多种类型（联合类型）

```ts
let numOrString: number|string = "gg"
```

### (联合)类型别名

```ts
type Price = number | string;
interface Product {
  price: Price
}
```

### 值的限定

限定值的类型

限定了特定的值，和枚举类型差不多，不是该值就报错

```ts
type Size = "s" | "m" | "l";
```

### 函数的类型标注(参数和返回值)

ts也会自动推断参数和返回值的类型，也可以手动类型标注

```ts
function test(price:Price | undefined): number{
  if(typeof price === Price){
    
  }else{
    
  } 
  return 1;
}
const f = (a:number):number => a;
```



###  标注函数类型

```ts
function test(callback: (result:string) => void){
  callback("success");
}
// 使用type来定义函数类型，实现函数类型别名
type TestCallBack = (result: string) => void;
interface Product {
  getPrice: () => number;
}
```

### 函数调用签名??

```ts
type/interface CallBack = {
  (result: string):void;
  code: string;
}
const callback: CallBack = (request) => console.log(result);
callback.code = "200";
```

定义时使用对象，返回值放在冒号后面，而不是箭头

可以为函数添加额外属性

## 类型转换(类型断言)

```ts
let str:any = "123"
// 使用as类型转换
let str2 = str as string
// 使用泛型
let str3 = <string>str;

```

## 泛型

```ts
function join<T>(arr1: T[], arr2: T[]): T[]{
  return [...arr1,...arr2];
}
const res = join<number>([1],[2]);
res.map(x => x * x)
```

