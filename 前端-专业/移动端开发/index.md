1. 原生App
   1. iOS/android
   2. RN
   3. uniapp
   4. Flutter
2. 小程序开发
3. web页面

## 自适应和响应式

自适应：不同屏幕大小自动调整尺寸

响应式：随着屏幕实时变动，自动调整

响应式是一种自适应

## 核心思想

布局更多使用flex，尺寸使用rem、vw、vh

不同屏幕不同布局：

1. 检测屏幕更换不同的站点
2. 媒体查询，多套css



## rem

1rem=html字体大小，配合js根据屏幕大小重新设置html字体大小

html字体大小=(js获取到的html字体大小/设计图宽度)*设计图下1rem大小

元素的rem值=设计图中元素宽度/设计图1rem大小

```js
let width = Math.min(document.body.clientWidth, 750);
let fontsize = (width/750)*100
document.documentElement.style.fontSize = `${fontsize}px`
```

## vw vh

1vw = 1%视口宽度
1vh =  1%视口高度
