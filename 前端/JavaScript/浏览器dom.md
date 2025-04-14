# DOM

> Document Object Model
> 文档对象模型，HTML文档的结构化表示
>
> 跨平台、语言无关的表示、 操作网页
>
> 可以通过jsdom操作来改变文本内容、html属性、css属性



dom入口：DOCUMENT

根元素：`<html></html>`

> DOM是webapi的一部分，而不是js的一部分，只是可以通过js访问，webapi是js库



## DOM树和DOM节点

html → dom：https://software.hixie.ch/utilities/js/live-dom-viewer/

DOM树结构：标签为元素节点，构成一个树状结构
元素内部节点：文本节点

1. 节点层级：document根节点，html文档元素、其他元素
1. 每个节点都有nodeType属性：表示节点类型



| 节点公共属性 | 描述         |      |
| ------------ | ------------ | ---- |
| nodeType     | 表示节点类型 |      |
| nodeName     |              |      |
| nodeValue    |              |      |
|              |              |      |



| 节点类型            | 描述                      | 示例             |
| ------------------- | ------------------------- | ---------------- |
| 抽象类Node          | 所有节点类型都继承Node    |                  |
|                     |                           |                  |
| Document            | 文档节点                  | 全局变量document |
| Element             | 最常用类型，DOM元素基础类 | div              |
| 抽象类CharacterData |                           |                  |
|                     |                           |                  |
| HTMLElement         |                           |                  |
|                     |                           |                  |
| Text                | 元素内部文本，文本节点    |                  |
| Comment             | 注释                      |                  |
|                     |                           |                  |
|                     |                           |                  |

dom元素对象常见属性

| prop        |                            |      |
| ----------- | -------------------------- | ---- |
| innerHTML   | 将元素中的html获取为string |      |
| outerHTML   | innerHTML+元素本身=>string |      |
| textContent | 文字内容                   |      |

> 修改outerHTML会在dom中用新的值替换，但是旧的获取的值不会改变，如果还要操作替换的dom，需要重新获取dom

## DOM机制

1. 自动修正
2. 如果一些内容存在于 HTML 中，那么它也必须在 DOM 树中。

## 文本节点/注释节点

| prop           | 描述     |      |
| -------------- | -------- | ---- |
| nodeValue/data | 文本内容 |      |
|                |          |      |
|                |          |      |



## DOM操作

每个HTML标签及其内容都是对象，可以通过js访问修改

### 获取dom元素

| dom                                   | 描述                           | 返回值         |
| ------------------------------------- | ------------------------------ | -------------- |
| `getElementById("")`                  | 根据id选择唯一元素             |                |
| `getElementByClassName("className")`  | 根据class选择元素              | HTMLCollection |
|                                       |                                |                |
| `querySelector("#container")`         | 通过选择器选择第一个匹配的元素 | Element        |
| `document.querySelectorAll(".title")` | 选择全部元素                   | NodeList       |

### 创建dom元素

| api                           | 描述 | 返回值 |
| ----------------------------- | ---- | ------ |
| `document.createElement("");` |      |        |
|                               |      |        |
|                               |      |        |



```js
// 访问节点
document.documentElement;
document.body;
document.head;
// 所有子节点
.childNodes[i]

// 创建节点
let s = 
s.src = "";
document.body.appendChild(s)

```

### 修改dom元素

| api              |                            |                        |
| ---------------- | -------------------------- | ---------------------- |
| textContent      | 元素内的文本，去掉所有tags |                        |
| innerHTML        | 将元素中的html获取为string |                        |
| outerHTML        | innerHTML+元素本身=>string |                        |
| nodeName/tagName | 标签名                     | tagName仅适用于Element |
|                  |                            |                        |



## 事件监听

`addEventListener(eventName, listener)`

### 事件

1. 简单事件
2. 复杂事件：由简单事件组成

| Event         |               |                     |
| ------------- | ------------- | ------------------- |
| mousedown/up  | 鼠标按下/释放 |                     |
| click         | 鼠标点击      | down -> up -> click |
| contextmenu   | 鼠标右键元素  | down -> cm          |
| dblclick      | 鼠标双击元素  |                     |
| mouseover/out | 鼠标移入/移出 |                     |
| mousemove     | 鼠标移动      |                     |
| keydown/up    | 键盘按下/松开 |                     |



| Event  |          |
| ------ | -------- |
| submit | 提交form |
| focus  | 聚焦元素 |

### 事件处理器

> 在事件发生时运行的函数

**分发处理器的方法**

1. html元素属性，本质上还是写入dom属性
2. dom属性： `dom.on<event>`
3. addEventListener

```html
<input onclick="alert('clicked!')">
<input onclick="func()">
```

```js
elem.onclick = function(){ alert('clicked!') }
elem.onclick = func;
```

```js
elem.addEventListener(event, handler,[phase]);
elem.removeEventListener(event, handler, [phase]);
```

事件处理器中的this值：当前元素

## BOM

Browser Object Model 浏览器对象模型

### window

window 浏览器实例

- ES中的Global对象
- 浏览器窗口的JS接口



1. 通过var声明的全局变量和函数，成为window对象的属性和方法

### location

http://foouser:barpassword@www.wrox.com:80/WileyCDA/?q=javascript#contents

| 属性 | 值   | 说明 |
| ---- | ---- | ---- |
| hash |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |

