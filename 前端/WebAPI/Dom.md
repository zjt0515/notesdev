# DOM

> Document Object Model
> 文档对象模型，HTML文档的结构化表示
>
> 跨平台、语言无关的表示、 操作网页
>
> 可以通过jsdom操作来改变文本内容、html属性、css属性

> [!tip]
>
> 1. https://developer.mozilla.org/zh-CN/docs/Web/API/HTML_DOM_API

dom入口：DOCUMENT

根元素：`<html></html>`

> DOM是webapi的一部分，而不是js的一部分，只是可以通过js访问，webapi是js库

## dom本质



## DOM树和DOM节点

html → dom：https://software.hixie.ch/utilities/js/live-dom-viewer/

DOM树结构：标签为元素节点，构成一个树状结构
元素内部节点：文本节点

1. 节点层级：document根节点，html文档元素、其他元素
1. 每个节点都有nodeType属性：表示节点类型

```mermaid
classDiagram
    class Node {
        +Node parentNode
        +Node firstChild
        +Node lastChild
        +Node previousSibling
        +Node nextSibling
        +Node append/remove/replaceChild(Node)
        +Node insertBefore(Node, Node)
        +Node cloneNode(boolean)
    }

    class Element {
        +string tagName
        +DOMTokenList classList
        +string getAttribute(string)
        +void setAttribute(string, string)
        +void removeAttribute(string)
        +boolean hasAttribute(string)
    }

    class Document {
        +Element createElement(string)
        +Text createTextNode(string)
        +Element getElementById(string)
        +Node querySelector(string)
        +NodeList querySelectorAll(string)
    }

    class Text {
        +string data
        +int length
    }

    class DOMTokenList {
        +void add(string)
        +void remove(string)
        +boolean contains(string)
        +void toggle(string)
        +int length
    }

<<<<<<< Updated upstream
<<<<<<< Updated upstream
    Node <|-- Element
    Node <|-- Text
    Node <|-- Document
    Element "1" o-- "1" DOMTokenList
=======
| NodeType值 | 节点类型            | 描述                      | 示例             |
| ---------- | ------------------- | ------------------------- | ---------------- |
|            | Node接口            | 所有节点类型都继承Node    |                  |
|            |                     |                           |                  |
| 9          | Document            | 文档节点                  | 全局变量document |
| 1          | Element             | 最常用类型，DOM元素基础类 | div              |
|            | 抽象类CharacterData |                           |                  |
|            |                     |                           |                  |
|            | HTMLElement         |                           |                  |
|            |                     |                           |                  |
| 3          | Text                | 元素内部文本，文本节点    | 我是文本         |
| 8          | Comment             |                           |                  |
>>>>>>> Stashed changes

```

### Node

属性：

1. `childNodes`: 实时的子节点NodeList
2. `first/lastChild`: 第一/最后一个子节点Node || null
3. `previous/nextSibling`: 同级的上/下一个节点 || null
4. `parentNode`: 父节点 || null
5. `parentElement`: 父节点Element
6. `textContent`: 所有子节点及其后代的文本内容
7. `nodeName`
8. `nodeType`
9. `nodeValue`

方法：

1. `append/remove/replaceChild()`
1. 
1. `contains()`

nodeType

| const                         | NodeType值 | 节点类型            | 描述                      | 示例             |
| ----------------------------- | ---------- | ------------------- | ------------------------- | ---------------- |
| ``                            |            | Node接口            | 所有节点类型都继承Node    |                  |
| `Node.ELEMENT_NODE`           | 1          | Element             | 最常用类型，DOM元素基础类 | div span         |
| `Node.TEXT_NODE`              | 3          | Text                |                           |                  |
| `Node.COMMENT_NODE`           | 8          | Comment             |                           |                  |
| `Node.DOCUMENT_NODE`          | 9          | Document            | 文档节点                  | 全局变量document |
| `Node.DOCUMENT_TYPE_NODE`     | 10         | DocumentType        |                           |                  |
| `Node.DOCUMENT_FRAGMENT_NODE` | 11         |                     |                           |                  |
| ``                            |            | 抽象类CharacterData |                           |                  |
| ``                            |            | HTMLElement         |                           |                  |
| ``                            | 3          | Text                | 元素内部文本，文本节点    | 我是文本         |
=======
| NodeType值 | 节点类型            | 描述                      | 示例             |
| ---------- | ------------------- | ------------------------- | ---------------- |
|            | Node接口            | 所有节点类型都继承Node    |                  |
|            |                     |                           |                  |
| 9          | Document            | 文档节点                  | 全局变量document |
| 1          | Element             | 最常用类型，DOM元素基础类 | div              |
|            | 抽象类CharacterData |                           |                  |
|            |                     |                           |                  |
|            | HTMLElement         |                           |                  |
|            |                     |                           |                  |
| 3          | Text                | 元素内部文本，文本节点    | 我是文本         |
| 8          | Comment             |                           |                  |
dom元素对象常见属性

| prop        |                            |      |
| ----------- | -------------------------- | ---- |
| innerHTML   | 将元素中的html获取为string |      |
| outerHTML   | innerHTML+元素本身=>string |      |
| textContent | 文字内容                   |      |

> 修改outerHTML会在dom中用新的值替换，但是旧的获取的值不会改变，如果还要操作替换的dom，需要重新获取dom

<<<<<<< Updated upstream
### Element

 ### Document

```
document.all
document.images
document.forms
document.scripts
document.links
document.fonts

document.cookie
```

### XMLDocument

```js
var parser = new DOMParser();
var xmlDoc = parser.parseFromString(``)
```



### HTMLCollection/NodeList

HTMLCollection：Element子类集合

获取节点的子节点：

1. .children，返回HtmlCollection
2. .childNodes，返回NodeList

### 文本节点/注释节点

| prop           | 描述     |      |
| -------------- | -------- | ---- |
| nodeValue/data | 文本内容 |      |
|                |          |      |
|                |          |      |

## DOM机制

1. 自动修正
2. 如果一些内容存在于 HTML 中，那么它也必须在 DOM 树中。

## DOM操作

每个HTML标签及其内容都是对象，可以通过js访问修改

### 获取dom节点

| dom                                               | 描述                          | 返回值                   |                                |
| ------------------------------------------------- | ----------------------------- | ------------------------ | ------------------------------ |
| `getElementById("id")`                            | 根据id获取唯一元素            | 单个元素Element          |                                |
| `getElementByClassName("className [className2]")` | 根据class获取元素集合         | HTMLCollection（动态的） | `HTMLCollection[0]`            |
| `getElementByName("name")`                        | 根据name属性获取节点列表      | NodeList                 | 可以查询不能解析的节点         |
| `getElementByTagName("tagName")`                  | 根据标签名查询                | 元素集合                 |                                |
| `querySelector("#container")`                     | css选择器选择第一个匹配的元素 | 单个元素Element          |                                |
| `document.querySelectorAll(".title")`             | css选择器                     | 静态NodeList             | 可能返回非预期值（:scope解决） |
=======
=======
```js
document.all
document.images
document.forms
document.scripts
document.links
document.fonts
```

查询伪元素：不可以
只能通过`window.getComputeStyle(className, "before")["content"]`获取对应的样式

特殊查询属性

### 节点遍历

1. for/while
2. NodeList.prototype.forEach
3. 转为数组遍历：Array.from

```js
for(int i = 0; i < xxx.length; i++){
  
}
```

遍历子元素

1. children/childNodes
2. NodeIterator vs TreeWalker

```js
const iterator = document.createNodeIterator(
  document.getElementById("id"),
  NodeFilter.SHOW_ELEMENT,
  {
    acceptNode(node){
      return node.tagName === 'LI' ? NodeFilter,
			FILTER_ACCEPT : NodeFilter.FILTER_REJECT
    }
  }
)
```



### 创建node

| api                                       | 描述         | 返回值 |
| ----------------------------------------- | ------------ | ------ |
| `document.createElement("div")`           | 创建         |        |
| `document.createTextNode/Comment("文本")` |              |        |
| `new Text("文本")`                        | 直接new      |        |
| `document.body.append()`                  | 挂载         |        |
| `node.appendChild()`                      | 尾插         |        |
| `node.insertBefore()`                     | 前插         |        |
| `node.replaceChild()`                     | 替换         |        |
| `node.textContent()`                      | 替换内容节点 |        |
| `element.after()`                         |              |        |
| `element.before()`                        |              |        |
| `element.append()`                        |              |        |
| `element.after()`                         |              |        |
| `element.after()`                         |              |        |



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

### 删除node



## dom树操作

1. 新增节点
2. 获取子元素列表
3. 获取父元素
4. 删除子元素




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

## Dom性能优化

### dom查询缓存



### 频繁操作改为一次性操作
