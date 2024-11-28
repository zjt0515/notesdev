

## 概述

javaee开源框架

广义Spring：Spring为核心的所有技术栈

狭义Spring：Spring Framework

核心模块 IOC AOP

- 非侵入式
- 控制反转
- 面向切面编程
- 容器
- 组件化
- 一站式

### Start

jdk17

1. 创建Maven工程spring6，删除src

2. 创建子模块spring-firrst

3. 引入spring相关依赖

    ```xml
    <dependency>
    	<groupId>org.springframework</groupId>
        <artifactId>spring-context</artifactId>
        <version>6.0.2</version>
    </dependency>
    
    <dependency>
    	<groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-api</artifactId>
        <version>5.6.3</version>
    </dependency>
    ```

4. 创建类，定义属性和方法

    ```java
    // com.genshinya.spring6.User.java
    public class User {
        public void add() {
            System.out.println("add...");
        }
    }
    ```

    

5. 按照spring要求创建配置文件

    ```xml
    // resources.bean.xml
    // 使用bean标签完成user对象创建
    <bean id="user" class="com.genshinya.spring6.User"></bean>
    ```

    

6. 在spring配置文件配置信息

7. 最终测试类

    ```java
    public class TestUser {
        @Test
        public void testUserObject() {
            // 加载spring配置文件, 对象创建
            ApplicationContext context
                    = new ClassPathXmlApplicationContext("bean.xml");
    
    
            // 获取创建对象
            User user = (User) context.getBean("user");
            System.out.println("1:" + user);
    
            //使用对象调用方法进行测试
            System.out.print("2:");
            user.add();
        }
    }
    ```

如何使用返回创建的对象

1. 加载bean.xml配置文件
2. 对xml文件解析
3. 获取bean标签属性值
4. 使用反射创建对象(根据类的全路径)

创建对象存放在哪？

`Map<String, BeanDefinition> beanDefinitionMap`

key 唯一标识
value 类的定义(描述信息)

## Log4j2日志框架

日志级别

1. TRACE 追踪
2. DEBUG 调试
3. INFO 信息
4. WARN 警告
5. ERROR 错误
6. FATAL 严重错误

日志输出目的地

日志信息输出格式



1. 引入Log4j2依赖
2. 类的根路径下建立log4j2.xml配置文件

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<configuration>
    <loggers>
<!--        debug级别-->
        <root level="DEBUG">
            <appender-ref ref="spring6log"/>
            <appender-ref ref="RollingFile"/>
            <appender-ref ref="log"/>
        </root>
    </loggers>

    <appenders>
<!--        输出到控制台-->
        <console name="spring6log" target="SYSTEM_OUT">
<!--            输出格式-->
            <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss SSS} [%t] %-3level %logger{1024} - %msg%n"/>
        </console>
<!--        输出到文件-->
        <File name="log" fileName="e:/spring6_log/test.log" append="false">
            <PatternLayout pattern="%d{HH:mm:ss.SSS} %-5level %class{36} %L %M - %msg%xEx%n"/>
        </File>

        <RollingFile name="RollingFile" fileName="e:/spring6_log/app.log"
                     filePattern="log/$${date:yyyy-MM}/app-%d{MM-dd-yyyy}-%i.log.gz">
            <PatternLayout pattern="%d{yyyy-MM-dd 'at' HH:mm:ss z} %-5level %class{36} %L %M - %msg%xEx%n"/>
            <SizeBasedTriggeringPolicy size="50MB"/>
<!--            文件夹下最多20个文件-->
            <DefaultRolloverStrategy max="20"/>
        </RollingFile>
    </appenders>
</configuration>

```



```java
// 使用log4j2手动输出日志
private Logger logger = LoggerFactory.getLogger(TestUser.class);
logger.info("logger.info执行调用");
```

