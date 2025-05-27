## 字体font



## 背景background

background属性

1. background-image——指定一个文件或者生成的颜色渐变作为背景图片。 
2. background-position——设置背景图片的初始位置。 
3. background-size——指定元素内背景图片的渲染尺寸。 
4. background-repeat——决定在需要填充整个元素时，是否平铺图片。 
5. background-origin——决定背景相对于元素的边框盒、内边距框盒（初始值）或内容盒子来定位。 
6. background-clip——指定背景是否应该填充边框盒（初始值）、内边距框盒或内容盒子。 
7. background-attachment——指定背景图片是随着元素上下滚动（初始值），还是固定在视口区域。注意，使用fixed值会对页面性能产生负面影响。 
8. background-color——指定纯色背景，渲染到背景图片下方。





渐变 linear-gradient函数

1. 角度
   1. to bottom right
   2. 1/pi
   3. 0.25turn
   4. 100grad
2. 起始颜色
3. 终止颜色

```css
.fade {
  background-image: linear-gradient(to right, white, blue)
}
```

## 阴影

 