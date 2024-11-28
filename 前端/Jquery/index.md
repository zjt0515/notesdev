### 入口函数

```js
// 入口函数
$(function(){
  
})
```

### 顶级对象$



### DOM和Jquery对象

jquery对象本质：对DOM对象包装后产生的对象(伪数组形式存储)

> 不同对象方法不能混用

```js
let mydiv=document.querySelector('div')
let mydiv2=$('div');
mydiv.
//dom和jquery对象转化, 有些属性和方法jquery没有封装，需要转换为dom对象
$(mydiv);
$(mydiv2)[0];//$(mydiv2).get(0)
```

## 常用API

### 选择器

| 选择器                         | 用法                                       | 描述         |
| ------------------------------ | ------------------------------------------ | ------------ |
| ID选择器、类选择器、标签选择器 |                                            |              |
| 全选选择器                     | `*`                                        |              |
| 并集选择器                     | `div,span`                                 | 选取多个元素 |
| 交集选择器                     |                                            |              |
| 层级选择器                     | `ul > li`和`ul li`                         |              |
| 筛选选择器                     | `ul li:first`，`ul li:eq(0)`，`:odd,:even` |              |

### 方法

方法选择器

| 方法                  | 用法                       | 描述                         |
| --------------------- | -------------------------- | ---------------------------- |
| 获取直接父级、子级    | `parent()，children() `    |                              |
| 获取子孙              | `find('') `                | 相当于后代选择器             |
| 获取兄弟们            | `siblings('')`             |                              |
| 获取之前/之后的兄弟们 | `nextAll('')，prevAll('')` |                              |
| 筛选                  | `eq(0)`                    | 相比于选择器，可以进行软编码 |



| 方法      | 用法                       | 描述         |
| --------- | -------------------------- | ------------ |
| 修改css   | `css('background','pink')` | 支持隐式迭代 |
| 检查class | `hasclass`                 |              |



### 嗯嗯

| 方法       | 用法      | 描述           |
| ---------- | --------- | -------------- |
| 获取索引号 | `index()` | 配合`eq()`使用 |
|            |           |                |
|            |           |                |
|            |           |                |
|            |           |                |
|            |           |                |
|            |           |                |
|            |           |                |
|            |           |                |

### 绑定事件

| 事件           | 用法                                  | 描述                                     |
| -------------- | ------------------------------------- | ---------------------------------------- |
| 鼠标经过+移开  | `hover(function(){},fn(){})`          | 如果只写一个函数，经过和离开触发同一个fn |
| 鼠标经过、移开 | `mouseover(fn(){})，mouseout(fn(){})` |                                          |
|                |                                       |                                          |
|                |                                       |                                          |
|                |                                       |                                          |
|                |                                       |                                          |
|                |                                       |                                          |
|                |                                       |                                          |
|                |                                       |                                          |



### 链式编程思想

```js
$(this).css('color','red')
  .siblings().css('color','')
```

### 样式操作

1. css

    > `'属性名','属性值'`修改css
    >
    > 只写属性名，则返回属性值
    > 修改多个属性，传入对象`{width: 400}`，属性名可以不用加引号
    >
    > 属性名不是css写法，而是小写驼峰

2. 操作类

    | 方法      | 用法                        | 描述 |
    | --------- | --------------------------- | ---- |
    | 添加/移除 | `addClass()，removeClass()` |      |
    | 切换      | `toggleClass()`             |      |

    > addClass是添加类名，一个标签可以有多个类名



## Animation

### 动画效果

| 动画                     | 用法                                          | 描述                                       |
| ------------------------ | --------------------------------------------- | ------------------------------------------ |
| 显示隐藏                 | `hide()，show([speed],[easing],[fn])`         | 一般省略参数，默认动画很丑                 |
| 切换                     | `toggle()`                                    | 如果被隐藏了，那就显示，如果显示，那就隐藏 |
| 上/下/切换滑动           | `slideDown()、slideUp()、sliceToggle()`       |                                            |
| 淡入淡出/切换/修改透明度 | `fadeIn()、fadeOut()、fadeToggle()、fadeTo()` |                                            |
| 停止动画                 | `stop`                                        | 可以取消动画派对，写在下面要执行的动画前面 |
| 自定义动画               | `animate()`                                   |                                            |
|                          |                                               |                                            |
|                          |                                               |                                            |

## 文本属性值

### 属性操作

| 方法                   | 用法                        | 描述                 |
| ---------------------- | --------------------------- | -------------------- |
| 获取固有属性值         | `element.prop('属性名')`    |                      |
| 修改固有属性值         | `prop('属性名','属性值')`   |                      |
| 获取或设置自定义属性值 | `attr('属性名',['属性值'])` |                      |
| 数据缓存               | `data('属性名'[,'属性值'])` | 放在内存里，类似变量 |
|                        |                             |                      |

### 内容文本值

## 元素操作

遍历创建添加删除元素
（隐式迭代无法对同类元素做不同操作）

遍历元素

```js
// 回调函数第一个参数:索引,第二个参数：dom元素对象，必须转化为jq对象
$('div').each(function(index, domELe) {
  $(domELem).css("color",arr[i])
})
```

遍历数据，处理数据

```js
$.each('div',function(index, domELe) {
  $(domELem).css("color",arr[i])
})
$.each(arr,function(index, ele) {
  console.log(ele)
})
$.each({name:'tom',age:12},function(key, value) {
  console.log(key,value)
})
```

创建元素

```js
var li = $('<li>动态创建li</li>')
// 内部添加，放到匹配元素内部最后面/最前面，父子关系
element.append(li);
element.prepend(li);
// 外部添加，兄弟关系
element.after(li)
element.before(li)
```

删除元素

```js
// 删除元素
$('ul').remove();
// 删除所有孩子
$('ul').empty();
$('ul').html("");
```



## 尺寸、位置操作

参数为空，返回对应值，否则修改相应值

```js
// 只包含width/height
$('div').width()/height();
// 包含paading值
$('div').innerWidth()/innerHeight()
// 再包含border值
$('div').outerWidth()/outerHeight()
// 再包含margin
$('div').outerWidth(true)/outerHeight(true)
```

位置

```js
// 总位置坐标(距离文档的位置便宜)
$('div').offset().left/top
$('div').offset({left:200,top:200})
// 距离带有定位父级位置偏移，不能修改值
$('div').postion()

```

被卷去头部
当被卷去头部到达顶部位置，显示返回顶部

```js
// 滚动事件
$(window).scroll(function(){
  if($(document).scrollTop() >= ...){}
})
// 设置被卷去头部
$(window).scrollTop(100)
```



## 事件

单事件注册`element.事件(function(){})`

| 事件 | 用法         | 描述 |
| ---- | ------------ | ---- |
| 鼠标 | `click`      |      |
|      | `mouseenter` |      |
|      |              |      |
|      |              |      |
|      |              |      |
|      |              |      |
|      |              |      |
|      |              |      |

`on({})`绑定多个事件

```js
$('div').on({
  mouseenter: function(){
    
  },
  click: function(){
  
	}
})
// 多个事件同一个回调函数
$('div').on('mouseenter' 'mouseleave', funciton(){
  
})
```

事件委派（子元素事件委派给父元素

```js
// 绑定在父元素，实际触发在子元素
$('ul').on('click', 'li', function(){
  
});
```

> 老方法bind()live()delegate()弃用了？

**为未来动态创建的元素绑定事件**

`one()`绑定一次性事件触发

`off()`移除on

```js
// 解除所有
$('div').off()
// 解除某个
$('div').off('click')
// 解除事件委托
$('ul').off('click','li')
```

### 自动触发事件

```js
$('div').on('click',function(){
  
})
// 自动触发
$('div').click();
$('div').trigger('click')
// 自动触发，但不会触发元素的默认行为，如表单的光标闪烁行为
$('div').triggerHandler('click')
```

### 事件对象

```js
$function('div').on('click', function(event){
  // 阻止默认行为
  event.preventDefault()
  return false
  // 阻止冒泡
  event.stopPropagation()
})
```

## 拷贝对象、多库共存、插件

没有命名冲突，不会覆盖已有数据
如果存在命名冲突，浅拷贝会覆盖target的数据，深拷贝不会覆盖 

```js
$.extend([true], target, obj1 [, obj2])
```

浅拷贝和深拷贝针对的都是对象中的对象，对象本身的一般属性都是深拷贝



### 多库共存

1. 将$改为jQuery

2. 自定义\$，同时释放jQuery对$的控制权

    `let % = jQuery.noConflict()`



### 插件

[1](http://www.jq22.com/)
[jq之家](http://www.htmleaf.com/)

流程：引入js、css文件，复制相关代码

## 案例

### 手风琴

![image-20240325210829953](./images/image-20240325210829953.png)

### 购物车

### 返回顶部

```js
// 滚动事件
$(window).scroll(function(){
  if($(document).scrollTop() >= ...){}
})
// 设置被卷去头部
$(window).scrollTop(100)
$('.back').click(function(){
  $("body,html").animate({
    scrollTop:0
  })
})
```

