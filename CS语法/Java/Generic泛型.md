# Generics泛型

## 入门

需求：创建一个IntegerPrinter的类，用于打印Integer的变量，如果换一种类型，又要创建一个对应的Printer类
解决办法：用泛型，只需创建一个Printer类

```java
public class Printer<T> {
	T content;
	Printer(T content) {
		this.content = content;
	}
	public void print() {
		System.out.println(content);
	}
}

// main
Printer<Integer> printer = new Printer(123);
printer.print();
```

> 定义泛型类中的T是任意的
> 定义泛型类，可以定义多个类型

> [!caution]
>
> 调用时，填入泛型不能使用基本数据类型（primitive type），必须用包装过后的引用类型



### 类型参数的约束bounded generics

限制传入的类型必须为某个类的子类

```java
public class Printer<T extends Father> {
}
```

类型参数必须是实现了某个接口

```java
public class Printer<T extends oneInterface> {
}
```

两者合用：为某个类的子类且实现了某个接口

```java
public class Printer<T extends Father & oneInterface > {
}
// 注： class必须写在interface前面
```

### 应用

```java
List<String> list = new ArrayList<>();
```

### type safe类型安全问题

```java
// 不建议这样做！
List<Object> list = new ArrayList<>();
list.add("hello");
list.add(1234);
String item = (String) list.get(1);
```

> 上述代码在运行时会报错，
> 因为泛型的工作方式是在编译阶段进行类型检查，

### generic method

```java
private static <T> void print(T content){
  sout(content);
}

```

类型约束同样适用，同样能传入多个类型

### ?通配符

```java
private static void print(List<?> content){
  sout(content)
}

List<String> list = new ArrayList<>();
print(list)
```

`List<String>` 不是`List<Object>`的子类，不能用

> ?后面同样可以加上extends 进行类型约束
>
> 同时还可以使用super约束必须为某类的父类或本身

## 简述

对于不同数据类型的成绩，如何设计Score类？

```java
public class Score<T>{
    String name;
    String id;
    T value;
}

Score<String> score = new Socre<>("数学", "123", "优秀");

```

## 什么是泛型？

?通配符：表示任意类型
`Score<?> everyScore = 

## 细节

- 静态字段不能使用泛型

## 泛型和多态

