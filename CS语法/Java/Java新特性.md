## Java 8 新特性

### Lambda表达式

```java
// 匿名内部类写法
Thread thread = new Thread(new Runnable(){
  @Override
  public void run() {
    sout
  }
});
// Lambda表达式
Thread thread = new Thread(() -> {
	sout
})
```

底层：不是简单语法糖

> 和匿名内部类不同：Lambda仅支持接口，不支持抽象类
> 接口内部必须有且仅有**一个抽象方法**
>
> 

## Java17新特性



## Java21新特性