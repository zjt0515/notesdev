`npm install element-ui@2.15.3`

```vue
import...
```



注意使用组件时，精简源代码的时候，不要把一些看似没有用的标签删掉



## 侧边栏折叠功能

### 使用pinia

1. 定义store，包含一个侧边栏宽度的属性
    还有一个根据当前侧边栏宽度切换宽度的action
2. 为header组件中的按钮添加事件，调用store中的action
3.  折叠内部文字：为菜单项添加`collapse`属性，这里是elementui组件的使用，collapse属性为true就会折叠菜单项内部 span标签内的文字
4. 调整组件宽度后，需要同时动态调整父标签的宽度





## vue的样式处理

```css
//有scoped，所有选择器都只能选中本组件中的标签，否则会污染别的组件的样式
<style scoped>
  .person {
    background-color: skyblue;
    box-shadow: 0 0 10px;
    border-radius: 10px;
    padding: 20px;
  }
  button {
    margin: 0 10px;
  }
</style>
```

