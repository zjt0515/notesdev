# CSS基础

1. 属性
2. 值
3. 关键字
4. 变量
5. 单位
6. 功能符
7. 声明和声明块

一些css中比较细节但影响小的东西不会在这列出

## 层叠、优先级

### 规则冲突（优先级）

> [!caution]
>
> 如果你在 CSS 里写了一个声明，但是没有生效，一般是因为被更高优先级的规则覆盖了。
>
> 解决方案： 
>
> 1. `!important;` 直接高效，缺点是不利于后续代码维护
>     破窗效应，第一个important出现了，随之而来的是更多important
> 2. 提升优先级，例如加入几个ID选择器
> 3. 降低优先级，减去几个id选择器
>
> 处理优先级容易发展为一种**军备竞赛**

层叠决定了如何解决冲突

1. 样式表的来源
    1. 作者样式表
    2. 用户样式表
    3. 用户代理样式表(浏览器默认样式)
2. 选择器优先级
    1. ID选择器数量 > 类数量 > 标签数量
3. 源码顺序
    1. 更晚引入的声明优先级更高


> 伪类选择器和属性选择器的优先级：与一个类选择器优先级相同
>
> 通用选择器*和组合器对优先级无影响
>
> 源码顺序对于链接样式的影响：按照"LoVe/HAte"顺序，即
>
> 1. link
> 2. visited
> 3. hover
> 4. active



> [!note]
>
> 可以使用3个数值标记选择器的优先级：
>
> 例如，`#page-header #page-title`有 2 个 ID，没有类，也没有标签，它的优先级可以用`2,0,0`
>
> 或者4个：
>
> 第一个位置用0或1代表是否为行内样式
>
> `0/1, 2, 0, 0`



层叠值：在层叠中最终胜出的属性值

经验法则：

1. 选择器中不要使用id选择器
2. 不要使用!important
3. 这两条都会大幅提升优先级，下次想要覆盖时会变得困难

## 继承

特定属性能够被继承, 继承属性会顺序传递给后代元素，直到它被层叠值覆盖。

1. 文字相关
2. 列表相关
3. ...

## 特殊值

### inherit



### initial

## 简写属性

用于给多个属性赋值的属性

| 简写属性       | 可覆盖的多个属性 | 描述 |
| -------------- | ---------------- | ---- |
| `font`         |                  |      |
| `background`   |                  |      |
| `border`       |                  |      |
| `border-width` |                  |      |
|                |                  |      |

> [!caution] 
>
> 简写属性可以省略一些值，被省略的属性会被**隐式地设置为初始值**
>
> 配合层叠优先级的问题，一些优先级低的属性会被简写属性的省略值覆盖掉！
> “font的问题最严重，因为它设置的属性值太多了。因此，要避免在`<body>`元素的通用样式以外使用font。”



简写属性的顺序：

1. 上右下左（可以每省略一个值，末尾的属性使用对应方向的值）
2. 水平、垂直（笛卡尔网格，先指定x坐标）
3. 

## 相对单位

> [!note]
>
> 一般会用 rem 设置字号：这是可直接预测的，同时避免了em的一些问题
>
> 用 px 设置边框
>
> 用 em 设置其他大部分属性，尤其是内边距、外边距和圆角：当元素字号改变时，em能够自动缩放
>
> （不过我有时用百分比设置容器宽度）。

> 像素级完美 → 相对值
>
> 屏幕和网页的大小根据不同用户不同行为都是在动态变化的
>
> css中的响应性：样式能够根据浏览器窗口的大小有不同的响应
>
> 像素和显示单位长度的换算： `1in = 25.4mm = 2.54cm = 6pc = 72pt = 96px`

### em

1em等于当前元素的`font-size`

> 当设置padding、height、width、border-radius等属性时，使用 em 会很方便。这是因为当元素继承了不同的字号，或者用户改变了字体设置时，这些属性会跟着元素均匀地缩放

1. 使用em定义`font-size`：根据继承的字号进一步计算
2. 使用em声明字号后，同时用于指定其他属性：其他属性使用该字号计算em
3. 嵌套的em：`font-size`在嵌套中不断继承，导致字体大小倍增倍减

### rem

root em的缩写，相对于根元素`font-size`的单位

> [!caution]
>
> 停止像素思维！
>
> 反模式：全局充值字号为10px，虽然可以简化单位换算，例如想要14px就是1.4em
>
> ```css
> html{ font-size: 0.625em;}
> ```
>
> 缺点：
>
> 1. 被迫写重复代码，10px太小了，每处都要覆盖它
> 2. 本质还是像素思维
>
> 合理做法：
>
> 1. 设置合理的默认字号
> 2. 

## 定位

使用定位后，必须配合四个属性定位，很多情况不写是不显示的

### 固定定位fixed

==元素相对于视口定位==
此时 元素的**包含块**：视口

搭配top right bottom left四个属性一起使用, 设置固定位置元素j离浏览器视口边缘的位置

> [!warning]
>
> 如果同时指定了两个对应方向的属性：会隐性地设置元素的宽/高
>

### 绝对定位

元素的包含块：最近的祖先==定位==元素

属性top、right、bottom和left决定了元素的边缘在包含块里的位置。

### 相对定位

同样可以搭配四个属性使用，但不能同时使用对应方向的属性（1个会被忽略），也不能使用zhe改变定位元素的大小

## 层叠上下文

## CSS变量

1. 声明变量`--n`
2. 读取变量`var(--n)`

```css
body {
  --header-font: '';
  --main-bg: rgb(123,123,123)
}
```

> [!caution]
>
> 1. 变量值是数值：不能与数值单位连用，要用`callc(var(), * 1px)`
> 2. 变量值带有单位：不能写成字符串
> 3. 变量值是字符串：可以与其他字符串拼接✅

### 作用域

多个同名变量的优先级：和层叠优先级规则一致

> [!tip]
>
> 类似全局变量的实现
>
> ```css
> root {
>   --main-color: #06c;
>   --main-gap: 1.45rem;
> }
> ```
>
> 

### 其他细节

1. 变量默认值`var(--n, defaultValue)`
2. 





















