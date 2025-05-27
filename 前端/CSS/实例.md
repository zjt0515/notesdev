## 黏性定位

```css
nav{
  position: sticky,
  top: 0
}
```

黏性定位看起来似乎像固定定位，但是底层的渲染规则和固定定位没有任何关系，而是相对定位的延伸。

## 字体

1. 普通字体族
    1. serif衬线字体
    2. sans-serif无衬线字体
    3. monospace等宽字体
    4. cursive手写字体
    5. fantasy奇幻字体
2. 通用字体族
    1. system-ui
    2. emoji 
        `font-family: Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;`
    3. math
    4. fangsong

> emoji字体 设置应该放在系统字体设置后面，否则会影响普通文本的渲染

自定义字体族群

```css
// 定义
@font-face {
    font-family: Emoji;
    src: local("Apple Color Emoji"),
       local("Segoe UI Emoji"), 
       local("Segoe UI Symbol"),
       local("Noto Color Emoji");
}
// 使用
.emoji {
    font-family: Emoji;
}
```

## 模糊效果

### `backdrop-filter`



