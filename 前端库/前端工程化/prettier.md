## Prettier

1. https://prettier.io/docs
2. https://prettier.nodejs.cn/docs/

```js
prettier --write \"src/**/*.ts\" \"test/**/*.ts\"

// 设置为scripts脚本：
"format": "prettier --write \"src/**/*.ts\" \"test/**/*.ts\"",
```

## prettier配置

```
{

}
```



## eslint-plugin-prettier

https://github.com/prettier/eslint-plugin-prettier#options

### eslint.config.js配置

关闭和prettier冲突的eslint规则

```js
const eslintPluginPrettierRecommended = require('eslint-plugin-prettier/recommended');

module.exports = [
  // Any other config imports go at the top
  eslintPluginPrettierRecommended,
];
```

