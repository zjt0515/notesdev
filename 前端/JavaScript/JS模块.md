## 模块系统

1. AMD
2. CommonJS
3. UMD
4. js module



## 模块核心功能

1. 始终use strict
2. 模块级作用域
3. 只通过http(s)工作

## export default

```js
// 导出 out.js
export default function sayHi(){}
// 导入
import say from './out.js'
```



## export

```js
// 导出 out.js
export function sayHi(){}

// 导入
import { sayHi } from './out.js'
```

