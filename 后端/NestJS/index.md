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

docker

```shell
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql
docker ps

```

docker-compose 针对配置文件

```yml
# Use root/example as user/password credentials
version: '3.1'

services:

  db:
    image: mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: 123456
    # (this is just an example, not intended to be a production configuration)

```

`docker-compose up -d`

打印`docker inspect [imageName]`

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

## 最佳实践

src

1. core
2. common
    1. middleware
    2. interceptors
    3. guard
3. user
4. store



1. https://github.com/CatsMiaow/nestjs-project-structure

风格指南：

https://v2.angular.cn/docs/ts/latest/guide/style-guide

## hot reload

对比代码变化，不需要重新编译整个项目

## 模板

1. https://github.com/nestjs/awesome-nestjs
