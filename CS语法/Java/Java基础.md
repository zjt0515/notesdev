## Character字符

Character类方法

| 方法              | 作用             |                     |
| ----------------- | ---------------- | ------------------- |
| isDigit()         | 是否是数字       |                     |
| isLetter()        | 是否是字母       |                     |
| isLetterOrDigit() | 是否是数字或字母 | 都可以用ACSII码计算 |
| toLowerCase(ch)   | 大写转小写       |                     |



## String字符串

字符串是引用类型，可以为null，也可以是空值""

```java
// 多行字符串 @Java13
String s = """ xxx
           xxx
           """;
```

字符串不可变：字符串内容不可变
字符串变量还是可以改变指向的字符串的

| 方法            | 作用                                                         |                   |
| --------------- | ------------------------------------------------------------ | ----------------- |
| `CharAt(index)` | 返回对应字符                                                 |                   |
| `toCharArray()` | 转换为字符数组                                               |                   |
| `indexOf()`     | 返回指定字符的index                                          |                   |
| `length()`      | 长度                                                         |                   |
| `replace()`     | 旧字符替换为新字符                                           |                   |
| `substring()`   | 返回[l, r)子串                                               |                   |
| `split()`       | 通过分隔符分割字符串为数组                                   |                   |
| `concat()`      | 返回连接字符串                                               | 或者使用 + 运算符 |
| `compareto()`   | 返回第一个不等字符的ACSII差值，找不到不等字符，返回字符串长度差值 |                   |

> 字符串 字面量创建和new创建的区别
>
> new总是会创建
>
> 字面量：编译器检查字符串池，存在和字面量相同的值，就指向对应的值

### StringBuffer

相对String，StringBuffer和StringBuilder长度都是可变的，相对于String消耗内存少

```java
StringBuffer sb = new StringBuffer("sb");
sb.append("sb");
sb.reverse();
sb.delete(start, end);
sb.insert();
sb.replace(start, end, str);
// 最终转换为字符串使用
sb.toString();
```



### StringBuilder

与buffer区别：不是线程安全的，不能同步访问，但是有速度优势

在循环拼接字符串时，你应该使用它

```java
StringBuilder sb = new StringBuilder(10);
sb.append("sb");
sb.insert(index, "new");
sb.delete(5, 8);
// 最终转换为字符串使用
sb.toString();
```



## Array数组

效率高，实用性差，长度固定

数组的本质是对象

> [!note]
>
> - capacity：固定
> - getValue：[index]
> - getSize：`.length`
> - **Java 数组的数组维度可以是常量、变量、表达式**，包括字符，会自动转化为整数

```java
// 初始化
String[] arrayWithFixedCap = new String[10];
int[] aWithValue = new int[] {1,2,3}
// 多维数组
int[][] ns = {
    {1,2},
    {3,4},
};
ns.length() == 2; // 二维数组的长度是行数
```

### 数组工具类Arrays

| 方法         | 作用       | 参数 | 返回                 |
| ------------ | ---------- | ---- | -------------------- |
| sort         | 排序       |      |                      |
| toString     | 输出字符串 | []   | "[item, item, item]" |
| fill         | 填充       |      |                      |
| binarySearch | 查找       |      |                      |
| asList       | 转为List   |      |                      |
| hash         |            |      |                      |

> 细节
>
> `Arrays.sort()`对int数组排序后，数组内容在内存中的顺序变化，对字符串数组排序时，数组每个元素的指向改变，但内存顺序不变

### 多维数组

```java
double[][] a = new double[5][5]
```





## 输入输出IO

输入整数

```java
Scanner scanner = new Scanner(System.in);
int m = scanner.nextInt();
```

### 循环、条件

```java
switch (){
  case 1:
    break;
  default:
}
```

## 命名

方法、变量：驼峰

类名：大写驼峰

