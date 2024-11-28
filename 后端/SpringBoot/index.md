## 参考资料

- 黑马https://www.bilibili.com/video/BV14z4y1N7pg
- [Springboot](https://docs.spring.io/spring-boot)



## 入门

1. Spring Init
2. 选择spring web
3. 编写Controller
4. 创建启动类

### 手动创建工程

1. 创建Maven Archetype，(选quickstart)
2. 引入依赖(继承父工程sbsp、引入web(sbsw)依赖等，不需要版本)
3. 提供启动项`SpringBootCreateManualApplication`
4. main目录下手动生成resources以及子配置文件`application.properties`

## 配置文件

`application.properties`

```pro
server.port=9090
server.servlet.context-path=/start
```

`application.yml`
层级表示更清晰

```yml
server:
	port:9090
	servlet:
		context-path:/start
```

### yml配置信息书写获取

三方技术配置信息

自定义配置信息

```yml
email:
	user: 8767@qq.com
	code: asdasd
	host: smtp.qq.com
	auth: true
hobbies:
	- 唱
	- 跳
	- rap
```

> - 键值以空格符作为分隔符
> - 缩进表示层级关系

使用注解获取配置信息：`@Value("${email.user}")`
少写一点前缀`@ConfigurationProperties(prefix="eamil")`

## 整合mybatis

## Bean

### Bean扫描



