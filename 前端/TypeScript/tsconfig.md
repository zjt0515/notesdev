# tsconfig.json

TS项目配置文件

`tsc --init`

## compilerOptions

编译器选项

| 属性              | 作用                                                         | 值                                    |
| ----------------- | ------------------------------------------------------------ | ------------------------------------- |
| target            | 选择编译版本                                                 | es5、es6                              |
| module            | 编译规范                                                     | commonjs<br />ESNext                  |
|                   |                                                              |                                       |
| rootDir           | 要编译的文件目录                                             | "./src/"                              |
| outDir            | 编译后的存放目录                                             | "./dist/"                             |
| moduleResolution  | 引入库的查找路径规范                                         | "node"从内部往外部查找<br />"classic" |
| resolveJsonModule | 是否可以引入json文件                                         | true                                  |
| allowJs           | ts中可以引入js                                               | true                                  |
| checkJs           | 对js文件类型检查                                             | true                                  |
| declaration       | 生成.d.ts声明文件                                            | true                                  |
| sourceMap         | 生成.js.map文件，自动匹配ts文件，在html引入js文件启动后，可以调试ts文件 | true                                  |
| isolatedModules   | 对ts专属类型(interface)导出时约束，开启后导出时要用type关键字 | true                                  |
| esModuleInterop   | commonjs和amd规范统一<br />export =                          | true                                  |

type checking 相关

| 属性                         | 作用                                   | 值   |
| ---------------------------- | -------------------------------------- | ---- |
| strict                       | 严格模式总开关                         | true |
| 其他为子项                   |                                        |      |
| noImplicitAny                | 对any类型严格检查                      | true |
| strictNullChecks             |                                        | true |
| strictPropertyInitialization | 类属性必须初始化                       | true |
| noImolicitReturns            | 函数可能出现没有返回值的返回路径是报错 | true |
| removeComments               | 编译后删除注释                         | true |
| noUnusedLocals               | 对没有使用的本地变量报错               | true |
| noUnusedParameters           | 没有使用参数时报错                     | true |
| skipLibCheck                 | 跳过.d.ts的类型检查                    |      |
| typeRoots                    |                                        |      |
| types                        |                                        |      |

