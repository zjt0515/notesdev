## 模块系统

1. AMD
2. CommonJS
3. UMD
4. ES6模块

## ES6模块核心功能

1. 始终use strict
2. 模块级作用域
3. 只通过http(s)工作

## export default

默认导出，无需用户提前知道模块内的变量名和函数名

```js
// 导出 out.js
export default function sayHi(){}
// 导入
import say from './out.js'
```

此时，import命令无需`{}`，可以使用任意名称

1. 一个模块只能有1个默认导出

> [!note]
>
> 本质上，`export default`就是输出一个叫做`default`的变量或方法，然后系统允许你为它取任意名字。所以，下面的写法是有效的。
>
> `import { default as foo } from 'modules';`

## export

1. 可以导出函数、变量、类
2. 可以处于模块的顶层任意位置，不能出现在块级作用域
3. 该接口可以取到模块内部实时的值

```js
// 导出 out.js
export function sayHi(){}

// 导入
import { sayHi } from './out.js'
```

## import

```js
import { old as new } from './xxx.js'


```

1. 自动提升到模块头部
2. 静态执行，不能使用表达式和变量(他们只有在运行时才能得到结果)
3. 

### from指定模块文件地址

1. 相对
2. 绝对
3. 模块名，需要有配置文件告诉js引擎位置

