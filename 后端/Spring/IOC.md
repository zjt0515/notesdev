## 概述

Inversion of Control 控制反转，将对象的创建、维护关系都交给容器

通过IOC容器管理对象的实例化和初始化，控制对象和对象之间的依赖关系，
IOC容器管理的 java 对象称为 Spring Bean

容器存储bean对象，使用map集合

![image-20240305194353662](./images/image-20240305194353662.png)

![image-20240305194341123](./images/image-20240305194341123.png)

### 依赖注入Dependency Injection

spring创建对象时，将对象依赖属性通过配置进行注入

实现方式

- set注入
- 构造注入

### IOC容器在Spring中的 实现

ApplicationContext为BeanFactory的子接口



ApplicationContext的实现类 

`ClassPathXmlApplicationContext` 通过读取类路径下的XML配置创建IOC容器对象

`FileSystemXmlApplicationContext` 通过文件系统读取XML配置创建IOC容器对象
`ConfigurableApplicationContext`ApplicationContext的子接口，`refresh()、close()`让ApplicationContext具有启动关闭刷新上下文的能力

`WebApplicationContext`专门为web开发使用

![image-20240305195828175](./images/image-20240305195828175.png)

## 基于XML管理bean

### 获取bean

1. 根据id
2. 根据class类型
3. 根据id和类型

```java
ApplicationContext context = new
        ClassPathXmlApplicationContext("bean.xml");
//1.获取id获取bean对象
User user1 = (User)context.getBean("user");
System.out.println("id获取bean对象：" + user1);
//2.根据类型获取bean，要求同一个全路径对应的bean只能有1个
User user2 = context.getBean(User.class);
System.out.println("类型获取bean对象：" + user2);
//3.根据id和类型
User user3 = context.getBean("user", User.class);
System.out.println("第三种：" + user3);
```

组件类实现了接口，根据**接口类型**可以获取bean
如果一个接口有多个实现类，多个实现类都配置了bean，根据接口类型不可以获取bean



### 依赖注入DI

1. 基于setter注入

    1. 创建类，定义属性，生成属性set方法

        ```java
        package org.example.spring.di;
        public class Book {
            private String bname;
            private String author;
            public Book() {
            }
            @Override
            public String toString() {
                return "Book{" +
                        "bname='" + bname + '\'' +
                        ", author='" + author + '\'' +
                        '}';
            }
        
        // 生成属性的
            public void setBname(String bname) {
                this.bname = bname;
            }
            public void setAuthor(String author) {
                this.author = author;
            }
            public static void main(String[] args) {
                // set方法注入
                Book book  = new Book();
                book.setBname("kava");
                book.setAuthor("我");
                // 构造器注入
                Book book1 = new Book("名字","作者");
            }
        }
        ```

    2. 创建对象过程中，向属性设置值

        ```xml
        <bean id="book" class="org.example.spring.di.Book">
            <property name="bname" value="编译原理"></property>
            <property name="author" value="Aho"></property>
        </bean>
        ```

        

2. 基于构造器注入

    1. 创建类，定义属性，生成有参构造方法

        ```java
            public Book(String bname, String author) {
                this.bname = bname;
                this.author = author;
            }
        ```

    2. 进行配置

        ```xml
        <!--    构造方法注入-->
            <bean id="bookCon" class="org.example.spring.di.Book">
                <constructor-arg name="bname" value="java"></constructor-arg>
                <constructor-arg name="author" value="我"></constructor-arg>
            </bean>
        ```

        

### 特殊值处理

1. 字面量赋值

    `<property name="bname" value="编译原理"></property>`

2. null

    `<property name="bname"><null/></property>`

3. xml实体

    `<property name="bname" value="&lt;&gt;"></property>`

4. CDATA节

    ```xml
    <property name="bname">
        <value><![CDATA[a < b]]></value>
    </property>
    ```

    

### 特殊类型属性注入

1. 对象类型属性注入
2. 





### bean的作用域和生命周期



### 基于xml自动



## 基于注解管理Bean

