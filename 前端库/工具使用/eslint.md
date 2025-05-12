## ESLINT

```js
eslint \"{src,apps,libs,test}/**/*.ts\" --fix
```



## 校验作用域

.eslintignore

```
README.md

dist/*

public/*.js
```

```
/* eslint-disable */		// 文件最顶部  整个文件都不校验
console.log('Hello Word')

/* eslint-disable */		
console.log('Hello Word')
/* eslint-enable */		// 忽略被注释包起来的代码

/* eslint-disable no-console */
console.log('Hello Word')		// 全局针对指定规则进行禁用

// 只针对当前行  eslint-disable-next-line 后跟规则
console.log('Hello Word')	 // eslint-disable-next-line no-console

// eslint-disable-next-line no-console 
console.log('Hello Word')
```

