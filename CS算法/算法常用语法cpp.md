## 博客资源

- [[正在填坑\] ACM模版集（个人自用，随缘更新中） (xiaoxiauwu.github.io)](https://xiaoxiauwu.github.io/post/acm/)
- [GitHub - zstuACM22/ICPC-useful-template: 浙江理工大学ACM集训队22届队员整理的一些ACM-ICPC板子](https://github.com/zstuACM22/ICPC-useful-template)
- [GitHub - threeFeetCat123/ACM-ICPC_CCPC: 收集了各类ACM算法板子，从起步到区域赛金牌](https://github.com/threeFeetCat123/ACM-ICPC_CCPC)
- https://github.com/F0RE1GNERS/template
- https://github.com/soulmachine/acm-cheat-sheet?tab=readme-ov-file
- [Algorithms used in Competitive Programming](https://github.com/matthewsamuel95/ACM-ICPC-Algorithms?tab=readme-ov-file)
- [灵茶山艾府·高质量题解精选](https://github.com/EndlessCheng/codeforces-go/blob/master/leetcode/SOLUTIONS.md)
- [灵茶山艾府题单](https://leetcode.cn/problems/find-longest-special-substring-that-occurs-thrice-i/solutions/2585837/fei-bao-li-zuo-fa-fen-lei-tao-lun-python-p1g2/?envType=daily-question&envId=2024-05-29)

## 普通数组[]

```c++
int a[n+1];
```

> 初始化：
> 全局默认0，否则必须手动初始化，不然是随机值

## 数组Vector

### 一维数组

```c++
//初始化，vector默认值为0
vector<int> v(m+1, 1e8);//为所有元素赋相同的初始值
vector<int> v = [1,2,3];
vector<vector<int>> v(n);

// 首尾、索引、判空、个数、容量
v.front/back();v[i];
v.empty();
v.size();
v.capacity();

// 改变大小(多删少补)
v.resize(n+1,[value]);

// 末尾插入删除
v.push_back();
v.pop_back();
// 清空
v.clear()
```

### 二维数组

```c++
//初始化n行、m列全为0的二维数组
vector<vector<int>> v(n, vector<int>(m,0));
//一行一行初始化
vv[i].resize(i+1,0);

//获取行数
v.size();
//删除一行
v.erase(a.begin(), a.begin()+1);//删除第一行
//添加一行
v.insert(a.begin(), vector<int> add)
```



### 遍历

##  String

参考资料：[C++中的String的常用函数用法总结_string函数-CSDN博客](https://blog.csdn.net/qq_37941471/article/details/82107077)

```c++
//拼接字符串(append方法或者+操作符)
s.append("xxx");s1+=s2.c_str();

//遍历字符: index/迭代器

//分割字符串/子串
const char *split = ",; !";char *p2 = strtok(str,split);
s.substr(startIndex, length);

//删除
//删除最后一个
s.pop_back();
//删除多个
s.erase(pos);
s.erase(pos,nums);

//大小写转换
tolower/toupper(s[i]);
//排序
sort(s.begin(), s.end())
```



## 队列queue

```c++
queue<int> q;
q.push(); q.pop();

```

## 栈stack



## 技巧性

### 初始化正无穷

`memset(v,0x3f,sizeof(v))`

### 字母转int

`int b = 'b' - 'a'` 两个字母相减，得到的就是ACSII码的差值。

利用这个技巧可以将26个字母映射到26个数字上，
比如说，字母不能作为数组参数，数字可以。

## Lambda表达式(匿名函数/闭包)

函数内定义lambda函数

```c++
//定义(一般直接在函数内定义)
function<int(int)> dfs = [&](int x, int y) -> int {
  return outerVa+x+y;
};
//调用
dfs(1,2);
```

> []内的参数：OuterVar
>
> OuterVar是捕获外部变量，使匿名函数可以访问甚至修改外部变量，使用&捕获可以修改外围的值
> [&]：按照引用方式捕获所有封闭范围内的变量
> [=]：所有变量按值捕获
> [&, =N]：按值捕获N，其他变量按引用捕获
>
> 然后是参数列表，返回值(可以忽略，编译器自动推断)

```c++
//定义
function<int(int, int)> dfs = 匿名函数;
//调用
dfs();
```


第一个参数是返回类型，括号内的参数是形参类型

## 前戏算法

有些算法必须要有一些……前戏算法加持下，才能进行下一步

比如排序

但是这一步又不是该算法的核心，因此使用内置算法即可

排序：`sort(A.begin(), A.end(),[func]);`
```c++
// 按照自己想要的顺序排列
static bool func(int a, int b){
        return abs(a) > abs(b);
}
static bool func(vector<int> a, vector<int> b){
        return a[0] > b[0];
}
```

## 按库分类

### cstring

`stoi()`string*转int，会自动检查范围，**超出报错**，简单处理办法时调用前判断大小或者位数？

`atoi`chat*转int，不会检查范围，超出上/下界只会输出上/下界，

`s.c_str()`string * 转char *

### cmath

`abs() fabs()`整数和浮点的绝对值

### algorithm

`sort(a.begin(),a.end())`默认从小到大排序

如果对二维数组进行sort，排序按照第一列的数字大小进行  行排序

### numeric

`iota(begin, end, start)`批量递增赋值vector元素

## bug

> [!caution]
>
> `if( ans.size() == 0 || ans.back()[1] < l)`
>
> 两个条件不能交换，![image-20240603083113469](./images/image-20240603083113469.png)
>
> vector为0时调用back()报错

