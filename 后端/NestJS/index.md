## 链接

1. https://nestjs.com/
2. https://nest.nodejs.cn/
3. https://docs.nestjs.cn/11/introduction

## 环境搭建

1. 项目需求(需求文档/技术选型/环境准备)
2. 功能模块(接口开发/数据库/性能要求/版本控制)
3. 接口测试(测试用例/压力测试/缺陷控制/接口文档)
4. 上线部署(自动化流程/多环境部署/灰度更新)

安装nvm，安装node，配置国内源

编辑器配置，vscode拓展

```shell
```

### 数据库搭建

## 装饰器

## nest cli命令

```shell
npm i -g @nestjs/cli
```



```shell
nest --help
// 生成模块
nest g mo demo
nest g co demo
nest g s demo
nest g resource user
```

## Restful风格

一个接口，不同请求方式实现不同功能
使用/而不是?

```http
// 增删改查
http://localhost:8080/api/get_list/1
```

- 查询GET
- 提交POST
- 更新PUT PATCH
- 删除DELETE
