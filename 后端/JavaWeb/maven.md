apache

项目对象模型POM  

### pom.xml

坐标

```xml
<groupId>com.genshinya</groupId>
<artifactId>maven-pro01</artifactId>
<version>1.0-SNAPSHOT</version>
```

  

### 安装Maven

![image-20240227150217272](./images/image-20240227150217272.png)

### idea配置

1. 构建执行部署中设置maven路径和settings路径
2. 设置运行程序jdk
3. 设置java编译器中的项目字节码版本
4. 设置项目的2个java版本

![image-20240227154943451](./images/image-20240227154943451.png)

![image-20240227155220077](./images/image-20240227155220077.png)

### 导入和移除Maven项目

略

### 依赖管理

```xml
<dependencies>
    <dependency>
        <groupId>组织名</groupId>
        <artifactId>模块名</artifactId>
        <verson>版本号</verson>
    </dependency>
</dependencies>
```

1. 引入依赖不存在，将连接中央仓库
2. 不知道依赖的坐标信息，在mvnrepository网站中搜索

### 依赖传递

依赖具有传递性

同时可以主动排除依赖

```xml
<exclusions>
	<exclusion>
    	<groupId>组织名</groupId>
        <artifactId>模块名</artifactId>
    </exclusion>
</exclusions>
```

### 依赖范围

main、test、