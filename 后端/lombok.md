https://projectlombok.org/

https://www.bilibili.com/video/BV1gb421J7ok

## 安装Lombok

```java
<dependencies>
	<dependency>
		<groupId>org.projectlombok</groupId>
		<artifactId>lombok</artifactId>
		<version>1.18.34</version>
		<scope>provided</scope>
	</dependency>
</dependencies>
```

Lombok插件

## 原理

1. 源文件被解析成语法树
2. 调用注解处理器，注解处理器产生新的源文件，对新的源文件进行编译
3. 语法树被分析转换成类文件

## 自动生成GetterSetter和构造方法

1. 用于类上，生成所有Getter
2. 用于字段上，生成对应Getter

```java
@Getter
@Setter
@AllArgsConstructor
```

> Getter命名规则：
>
> 1. 首字母大写，前面加上get
> 2. 对于boolean，首字母大写，前面加上is

### @Getter源码

```java
@Target({ElementType.FIELD, ElementType.TYPE})
@Retention(RetentionPolicy.SOURCE)
public @interface Getter {
    AccessLevel value() default AccessLevel.PUBLIC; // 控制Getter的访问权限或者不生成某个字段的Getter

    AnyAnnotation[] onMethod() default {}; // 为自动生成的Getter方法添加特定注解

    boolean lazy() default false; // 为字段添加懒加载(在调用Getter时再初始化)

    /** @deprecated */
    @Deprecated
    @Retention(RetentionPolicy.SOURCE)
    @Target({})
    public @interface AnyAnnotation {
    }
}
```

> 对于手动实现的Getter和Setter，lombok不会覆盖，但可以通过@Tolerate注解使手动和自动的同时存在
>
> java17的record也可以，但只能生成getter

### @Setter源码

```java
@Target({ElementType.FIELD, ElementType.TYPE})
@Retention(RetentionPolicy.SOURCE)
public @interface Setter {
    AccessLevel value() default AccessLevel.PUBLIC;

    AnyAnnotation[] onMethod() default {};

    AnyAnnotation[] onParam() default {}; // 为自动生成的Setter方法添加特定注解?

    /** @deprecated */
    @Deprecated
    @Retention(RetentionPolicy.SOURCE)
    @Target({})
    public @interface AnyAnnotation {
    }
}
```

### 

### @AllArgsConstructor源码

```java
@Target({ElementType.TYPE})
@Retention(RetentionPolicy.SOURCE)
public @interface AllArgsConstructor {
  	// 用于生成一个静态构造方法 (new变成.xxx，本质还是调用构造方法)
  	// 适合用作泛型的类型推断，同时简化代码
    String staticName() default "";
		// 用于在构造方法上加注解
    AnyAnnotation[] onConstructor() default {};
		// 设置构造方法的权限等级
    AccessLevel access() default AccessLevel.PUBLIC;

    /** @deprecated */
    @Deprecated
    @Retention(RetentionPolicy.SOURCE)
    @Target({})
    public @interface AnyAnnotation {
    }
}
```

### @NoArgsConstructor源码

```java
@Target({ElementType.TYPE})
@Retention(RetentionPolicy.SOURCE)
public @interface NoArgsConstructor {
    String staticName() default "";

    AnyAnnotation[] onConstructor() default {};

    AccessLevel access() default AccessLevel.PUBLIC;
		// 强制生成无参构造，对字段赋默认初始值(final必须赋值导致)
    boolean force() default false;

    /** @deprecated */
    @Deprecated
    @Retention(RetentionPolicy.SOURCE)
    @Target({})
    public @interface AnyAnnotation {
    }
}
```



### @RequiredArgsConstructor

对所有final字段放入构造参数列表中，使用构造方法必须传入final对应得字段

```java
@Target({ElementType.TYPE})
@Retention(RetentionPolicy.SOURCE)
public @interface RequiredArgsConstructor {
    String staticName() default "";

    AnyAnnotation[] onConstructor() default {};

    AccessLevel access() default AccessLevel.PUBLIC;

    /** @deprecated */
    @Deprecated
    @Retention(RetentionPolicy.SOURCE)
    @Target({})
    public @interface AnyAnnotation {
    }
}
```



## ToString

@ToString

```java
@Target({ElementType.TYPE})
@Retention(RetentionPolicy.SOURCE)
public @interface ToString {
  	// 是否带上字段名
    boolean includeFieldNames() default true;

    String[] exclude() default {};

    String[] of() default {};
		// 调用父类toString进行拼接
    boolean callSuper() default false;
		// 是否使用Getter的结果
    boolean doNotUseGetters() default false;
		// 开启白名单模式
    boolean onlyExplicitlyIncluded() default false;
		// 子注解：排除某些字段
    @Target({ElementType.FIELD})
    @Retention(RetentionPolicy.SOURCE)
    public @interface Exclude {
    }
		// 白名单模式的子注解，也可以作用在方法上
    @Target({ElementType.FIELD, ElementType.METHOD})
    @Retention(RetentionPolicy.SOURCE)
    public @interface Include {
      	// 打印顺序优先级
        int rank() default 0;
				// 配置字段别名
        String name() default "";
    }
}
```

## @EqualsAndHashCode

> equls实现
>
> 1. 判断地址是否相等
> 2. 判断类是否不同
> 3. 对每个值依次比较
>     1. 如果是引用类型，先看是否都为null，再调用对应类型的equals比较

> hashCode

```java
@Target({ElementType.TYPE})
@Retention(RetentionPolicy.SOURCE)
public @interface EqualsAndHashCode {
    String[] exclude() default {};

    String[] of() default {};
		// 调用父类equals
    boolean callSuper() default false;
		// 是否使用Getters
    boolean doNotUseGetters() default false;

    CacheStrategy cacheStrategy() default EqualsAndHashCode.CacheStrategy.NEVER;

    AnyAnnotation[] onParam() default {};

    boolean onlyExplicitlyIncluded() default false;

    /** @deprecated */
    @Deprecated
    @Retention(RetentionPolicy.SOURCE)
    @Target({})
    public @interface AnyAnnotation {
    }
		// 控制hashCode结果的缓存
  	// 对于属性值不会变化的实体，适合优化性能
  	// 如果字段值会改变，不能使用！
    public static enum CacheStrategy {
        NEVER,
        LAZY;

        private CacheStrategy() {
        }
    }
		// 子注解：排除某些字段的比较
    @Target({ElementType.FIELD})
    @Retention(RetentionPolicy.SOURCE)
    public @interface Exclude {
    }
		// 白名单子注解
    @Target({ElementType.FIELD, ElementType.METHOD})
    @Retention(RetentionPolicy.SOURCE)
    public @interface Include {
      	// 将字段的比较替换为某个方法的返回结果的比较
        String replaces() default "";
				// 比较顺序
        int rank() default 0;
    }
}
```

## @Data

相当于@Getter@Setter@RequiredArgsConstructor@Tostring@EqualsAndHashCode

## @Value

类的数据不可修改，将所有字段变为final，只提供get

等价于@Getter@FieldDefaults(makeFinal=true, level=AccessLevel.PRIVATE)@AllArgsConstructor

@ToString@EqualsAndHashCode

> 相当于java17的 record类，直接用record即可

## 实验性内容



## @Accessors

指导生成gettersetter的格式

```java
@Target({ElementType.TYPE, ElementType.FIELD})
@Retention(RetentionPolicy.SOURCE)
public @interface Accessors {
  	// 删去前缀getset
    boolean fluent() default false;
		// 支持链式调用的setter
    boolean chain() default false;
		// 所有生成的方法前+final
    boolean makeFinal() default false;
		// 对于长命名字段，去掉字段的前缀
  	// 注意：所有字段命名格式必须一致，例如id和userName，ci'shi
    String[] prefix() default {};
}
```



