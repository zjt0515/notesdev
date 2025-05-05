# CSS常用布局

只关注布局整体，对于具体的属性用法请参看附录

https://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html


## 浮动

浮动能将一个元素（通常是一张图片）拉到其容器的一侧，这样文档流就能够包围它，这种布局在报纸和杂志中很常见。





> [!tip]
>
> 双容器，用于网页内容居中
>
> ```css
> .container {  
>   max-width: 1080px; 
>   margin: 0 auto; 
> }
> ```

## Flex布局 :rainbow_flag:

弹性容器FlexContainer`display: flex`

### 弹性子元素大小

弹性元素大小的确定： 

1. `flex-basis/ width`确定元素大小基准值
2. 在主轴方向按照`flex-grow+flex-shrink`决定缩放规则

`flex`控制flex items在主轴方向上的大小，即元素宽度

> [!tip]
>
> 推荐使用简写属性flex，省略子属性，默认值在大部分情况都是所需要的

![实际应用布局](./images/image-20241029202059776.png)

### 弹性方向

给弹性容器设置`flex-direction`
切换主轴方向

> 内部的弹性盒子的弹性方向为column，因此主轴发生了旋转，现在变成了从上到下（副轴变成了从左到右）。也就是对于弹性子元素而言，flex-basis、flex-grow和flex-shrink
>
> 现在作用于元素的高度而不是宽度。由于指定了flex: 1，因此在必要的时候子元素的高度会扩展到填满容器。无论哪边更高，主板块的底部和右边第二个小板块的底部都会对齐。

> [!warning]
>
> 水平和垂直弹性盒子的区别：
>
> 在 CSS 中处理高度的方式与处理宽度的方式在本质上不一样。弹性容器会占
> 据 100%的可用宽度，而高度则由自身的内容来决定， 即弹性子元素决定， 弹性子元素会正好填满容器。即使改变主轴方向，也不会影响这一本质。
>
> 因此，在垂直的弹性盒子里，子元素的flex-grow和flex-shrink不会起作用

### 对齐、间距等细节





- 换行包裹`flex-wrap`
- `flex-flow`
- 项目在主轴的对齐方式`justify-content`
- 交叉轴上的对齐方式`align-items`
- 多根轴线的对齐方式???`align-content`

### 项目

- 排列顺序`order`
- 单独的对齐方式`align-self`





display: flex 

主轴居中 justify-content: center

侧轴居中 align-items: center







## flex+margin

[flex+margin](https://www.bilibili.com/video/BV12N4y1U7jq/?spm_id_from=333.337.search-card.all.click&vd_source=a6f0ee69351d992f6798c937a32c9968)

(在弹性项中设置)子元素居中 margin: auto
用margin吃掉剩余空间

## Grid网格布局:checkered_flag:

1. 容器 布局最外层
2. 项目 容器的直接子元素
3. 网格线 单元格 行和列
4. 区域多个单元格组成

划分网格后，项目按照顺序先行后列自动放置

### 容器属性

| Grid容器属性                                                 |                                |                                                       |
| ------------------------------------------------------------ | ------------------------------ | ----------------------------------------------------- |
| display: grid                                                | 指定容器采用grid布局           |                                                       |
| display: inline-grid;                                        | 行内元素，元素内部采用网格布局 |                                                       |
| grid-template-columns: 100px 100px 100px;                    | 定义每一列/行的宽度            |                                                       |
| `grid-template-columns: repeat(12, 1fr);`                    | 十二网格布局                   |                                                       |
| row-gap: 20px;   column-gap: 20px;<br />gap: 20px 20px       | 设置行列之间的间隔             |                                                       |
| grid-template-areas: "header header header"                      "main main sidebar"                      "footer footer footer"; | 单元格 -> 区域                 | 区域的命名会影响网格线的命名，不需要用到的区域用.表示 |
| grid-auto-flow: column;                                      | 项目元素放置顺序               |                                                       |
| justify-items align-items  place-items:                      | 单元格内容的水平/垂直位置      |                                                       |
| justify-content align-content place-content                  | 整个内容在容器的位置           |                                                       |
|                                                              |                                |                                                       |

1. 百分比 `33.33% 33.33% 33.33%;`
2. 重复函数 `repeat(3, 33.33%);` `repeat(2, 100px 20px 80px);`
3. auto-fill 根据容器大小自动填充项目 `repeat(auto-fill, 100px);`
4. 倍数关系 `150px 1fr 2fr;`
5. 长度范围minmax `1fr 1fr minmax(100px, 1fr);`
6. auto 自动  ` 100px auto 100px;`
7. 指定网格线名称 `[r1] 100px [r2] 100px [r3] auto [r4];`



- start：对齐单元格的起始边缘。
- end：对齐单元格的结束边缘。
- center：单元格内部居中。
- stretch：拉伸，占满单元格的整个宽度（默认值）。
- space-evenly - 项目与项目的间隔相等，项目与容器边框之间也是同样长度的间隔。

- space-around - 每个项目两侧的间隔相等。所以，项目之间的间隔比项目与容器边框的间隔大一倍。
- space-between - 项目与项目的间隔相等，项目与容器边框之间没有间隔。

1. 根据多余的括号 → 得到多余括号类型和数量
2. 源代码中删除对应括号，检查，加入答案
