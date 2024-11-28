## 父工程pom.xml

阿里云镜像创建的maven

```xml
<properties>
        <java.version>1.8</java.version>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <spring-boot.version>2.7.6</spring-boot.version>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-dependencies</artifactId>
                <version>${spring-boot.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                    <encoding>UTF-8</encoding>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <version>${spring-boot.version}</version>
                <configuration>
                    <mainClass>com.genshinya.weblogspringboot.WeblogSpringbootApplication</mainClass>
                    <skip>true</skip>
                </configuration>
                <executions>
                    <execution>
                        <id>repackage</id>
                        <goals>
                            <goal>repackage</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
```

不知道什么意思，但这不是我们想要的，我们现在修改一个多模块项目父工程的`pom.xml`文件

## 创建web访问模块

勾选上 `Lombok` 和 `Spring Web` 依赖

在父项目的 `pom.xml` 中添加该子模块，以及添加 `spring-boot-maven-plugin`

## 创建Admin后台管理模块

勾选上 `Lombok`

在父项目的 `pom.xml` 文件中添加该子模块：

将 `resource` 目录下的配置文件，和 `Application` 启动类删除掉。配置文件统一放在 `weblog-web` 入口模块中来管理：

## 创建 common 通用功能子模块





## 父项目统一版本管理

```xml
<!-- 版本号统一管理 -->
    <properties>
        ...

        <!-- 依赖包版本 -->
        <lombok.version>1.18.28</lombok.version>
        <guava.version>31.1-jre</guava.version>
        <commons-lang3.version>3.12.0</commons-lang3.version>
    </properties>
    
<!-- 统一依赖管理 -->
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>com.quanxiaoha</groupId>
                <artifactId>weblog-module-admin</artifactId>
                <version>${revision}</version>
            </dependency>

            <dependency>
                <groupId>com.quanxiaoha</groupId>
                <artifactId>weblog-module-common</artifactId>
                <version>${revision}</version>
            </dependency>

            <!-- 常用工具库 -->
            <dependency>
                <groupId>com.google.guava</groupId>
                <artifactId>guava</artifactId>
                <version>${guava.version}</version>
            </dependency>

            <dependency>
                <groupId>org.apache.commons</groupId>
                <artifactId>commons-lang3</artifactId>
                <version>${commons-lang3.version}</version>
            </dependency>
        </dependencies>
    </dependencyManagement>    
```

## 子模块之间的依赖关系



## 多环境配置

### Spring Profile 介绍

Spring Profile 是 Spring 框架用于处理不同环境配置的解决方案。Profile 可以帮助我们在不改变应用代码的情况下，根据当前环境动态地激活或者切换不同的配置。

当你激活一个特定的 Profile 时，Spring Boot 会查找名为 `application-{profile}.properties` 的文件，并把其中的属性加载到 Spring Environment 中。

## 配置框架增强(依赖)

### Mybatis-Plus

配置p6spy打印SQL，在本地开发环境提前发现慢SQL，生产环境禁用

1. 添加依赖
2. 修改配置文件中的数据库driver和url
3. 添加spy.properties配置

```java
// 主环境
<properties>
    // 省略...
    <p6spy.version>3.9.1</p6spy.version>
</properties>
<dependencyManagement>
    <dependencies>
  // 省略...
        <dependency>
            <groupId>p6spy</groupId>
            <artifactId>p6spy</artifactId>
            <version>${p6spy.version}</version>
        </dependency>

    </dependencies>
</dependencyManagement>
// common模块
<dependency>
  <groupId>p6spy</groupId>
  <artifactId>p6spy</artifactId>
</dependency>
```

```yml
spring:
  datasource:
    driver-class-name: com.p6spy.engine.spy.P6SpyDriver
    url: jdbc:p6spy:mysql://127.0.0.1:3306/weblog?useUnicode=true&characterEncoding=UTF-8&autoReconnect=true&useSSL=false&zeroDateTimeBehavior=convertToNull
```

### SpringSecurity

新建子模块

```xml
<parent>
    <groupId>com.quanxiaoha</groupId>
    <artifactId>weblog-springboot</artifactId>
    <version>${revision}</version>
</parent>	
<dependencies>
    <!-- 免写冗余的 Java 样板式代码 -->
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <optional>true</optional>
    </dependency>

    <!-- 单元测试 -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
```



为admin模块添加jwt模块依赖

```xml
 <dependency>
    <groupId>com.quanxiaoha</groupId>
    <artifactId>weblog-module-jwt</artifactId>
</dependency>
```

同时添加ss依赖



自定义配置

```java
// admin.config
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http.authorizeHttpRequests()
                .mvcMatchers("/admin/**").authenticated() // 认证所有以 /admin 为前缀的 URL 资源
                .anyRequest().permitAll().and() // 其他都需要放行，无需认证
                .formLogin().and() // 使用表单登录
                .httpBasic(); // 使用 HTTP Basic 认证
    }
}
```

在yml文件添加security用户名和密码配置





### lombok

在属性上加上 `@Getter` 和 `@Setter` 注解，Lombok 就会为你自动生成这些方法。

通过 `@NoArgsConstructor`、`@RequiredArgsConstructor` 或 `@AllArgsConstructor` 注解，你可以快速生成无参构造函数、带有必需参数的构造函数或者带有全部参数的构造函数。

通过 `@EqualsAndHashCode` 注解，Lombok 会根据类的字段自动生成 `equals()` 和 `hashCode()` 方法，让你的类更易于比较和使用在集合中。

`@Slf4j` 注解，你可以直接在类中使用 `log` 对象，而无需手动创建日志记录器。

`@SneakyThrows` 注解，你可以在方法中抛出受检异常，而无需显式地在方法上声明或捕获它们。

`@Data` 注解，Lombok 会为你自动生成所有常用方法，如 Getter、Setter、`toString()` 等，让你的数据类更加简洁。

 使用 `@Builder` 注解，Lombok 可以帮你创建一个更优雅的构建器模式，让你的对象初始化更加流畅。

### 日志框架logback

在 `pom.xml` 中加入 `spring-boot-starter-web` 依赖时，它会自动包含 Logback 相关依赖

日志生效profile：`logging:  config: classpath:logback-weblog.xml`

自定义logback配置

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration >
    <jmxConfigurator/>
    <include resource="org/springframework/boot/logging/logback/defaults.xml" />

    <!-- 应用名称 -->
    <property scope="context" name="appName" value="weblog" />
    <!-- 自定义日志输出路径，以及日志名称前缀 -->
    <property name="LOG_FILE" value="/app/weblog/logs/${appName}.%d{yyyy-MM-dd}"/>
    <property name="FILE_LOG_PATTERN" value="%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{50} - %msg%n"/>
    <!--<property name="CONSOLE_LOG_PATTERN" value="${FILE_LOG_PATTERN}"/>-->

    <!-- 按照每天生成日志文件 -->
    <appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <!-- 日志文件输出的文件名 -->
            <FileNamePattern>${LOG_FILE}-%i.log</FileNamePattern>
            <!-- 日志文件保留天数 -->
            <MaxHistory>30</MaxHistory>
            <!-- 日志文件最大的大小 -->
            <TimeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                <maxFileSize>10MB</maxFileSize>
            </TimeBasedFileNamingAndTriggeringPolicy>
        </rollingPolicy>
        <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">
            <!-- 格式化输出：%d 表示日期，%thread 表示线程名，%-5level：级别从左显示 5 个字符宽度 %errorMessage：日志消息，%n 是换行符-->
            <pattern>${FILE_LOG_PATTERN}</pattern>
        </encoder>
    </appender>

    <!-- dev 环境（仅输出到控制台） -->
    <springProfile name="dev">
        <include resource="org/springframework/boot/logging/logback/console-appender.xml" />
        <root level="info">
            <appender-ref ref="CONSOLE" />
        </root>
    </springProfile>

    <!-- prod 环境（仅输出到文件中） -->
    <springProfile name="prod">
        <include resource="org/springframework/boot/logging/logback/console-appender.xml" />
        <root level="INFO">
            <appender-ref ref="FILE" />
        </root>
    </springProfile>
</configuration>
```



### 测试日志

```c++
@SpringBootTest
@Slf4j // 自动生成日志实例
class WeblogWebApplicationTests {
    @Test
    void testLog(){
        log.info("Info 级别日志");
        log.warn("Warn 级别日志");
        log.error("Error 级别日志");

        String author = "genshinya";
        log.info("作者：{}", author);
    }
}
```

再切换到生产环境，将日志配置中的日志输出目录修改，再次测试输出到文件是否成功

###  自定义注解，实现 API 请求日志切面

看不懂一点



### 



### 通过MDC实现日志跟踪

1. 日志切面中，在请求开始设置MDC值，请求结束时清楚MDC中的值
2. 在日志配置文件中，使用%X引用MDC中的值，如`$X{traceId}$`
3. 



### 优雅的参数校验

SpingBoot能够让我们利用Java校验API JSR380（ Bean Validation 2.0）中定义的注解来进行参数校验

1. 添加依赖





```java
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-validation</artifactId>
</dependency>
```



### 自定义响应工具类

1. 设计接口返回参数
2. 根据参数设计响应工具类

```java
{
	"success": true,
	"data": null
}
{
	"success": false,
	"errorCode": "10000"
	"message": "用户名不能为空"
}
```

自定义响应工具类细节：

1. 需要存响应数据，类型是由接口传入的，使用泛型支持所有类型

### 全局异常管理

1. 定义基础异常内容接口
2. 定义业务异常类，和上述接口的关系：组合
3. 定义全局异常处理类



业务异常处理流程

1. `@ControllerAdvice`注解全局异常处理类，该类拦截异常，并返回响应
2. 响应接受异常参数，设置响应内容，返回





### Knife4j 接口调试工具

1. 添加依赖
2. 添加配置文件
3. 启动



Swagger注解

1. `@Api(tags="")`
2. `@ApiOperation(value = "")`

### 内置Jackson JSON框架





## SS整合JWT

JWT：

1. 无状态
2. 灵活性
3. 安全性
4. 跨平台跨语言



# 数据库表

文章类型

```sql
CREATE TABLE `t_category` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT COMMENT '分类id',
  `name` varchar(60) NOT NULL DEFAULT '' COMMENT '分类名称',
  `create_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '最后一次更新时间',
  `is_deleted` tinyint(2) NOT NULL DEFAULT '0' COMMENT '逻辑删除标志位：0：未删除 1：已删除',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE KEY `uk_name` (`name`) USING BTREE,
  KEY `idx_create_time` (`create_time`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 ROW_FORMAT=DYNAMIC COMMENT='文章分类表';

```

用户角色表 用户role

```sql
CREATE TABLE `t_user_role` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT COMMENT 'id',
  `username` varchar(60) NOT NULL COMMENT '用户名',
  `role` varchar(60) NOT NULL COMMENT '角色',
  `create_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  PRIMARY KEY (`id`) USING BTREE,
  KEY `idx_username` (`username`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 ROW_FORMAT=DYNAMIC COMMENT='用户角色表';

```





# 接口开发

## 文章分类接口



## 分页接口
