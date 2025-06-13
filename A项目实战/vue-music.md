## 第三方库

`npm config set registry https://registry.npmmirror.com/`

https://www.npmjs.com/package/pinyin

https://www.npmjs.com/package/js-base64

## 轮播图

https://better-scroll.github.io/docs/en-US/guide/how-to-install.html#npm

获取vue dom节点

Vue2\3的生命周期狗子 

## scss mixin

解决不同ppi展示不同分辨率图片

## 图标字体

## css learn

tab组件flex样式实现

## 前后端数据

## getSingerList

```json
{
  singers: [
    {
      title:
      list: [
        {
          id: ...,
          mid: ...,
          name: ...,
          pic: ...
        },
        {},...
      ]
    },
    {
      title: ...
      list: ...
    },...
  ]
}
```

song

```json
{
  id: 123212,
  mid: "0023sad232",
  name: "",
  singer: "",
  duration: 300,
  url: "http://...",
  pic: "",
  album: "",
}
```



## 播放器内核组件

### 歌曲播放/暂停

### 歌曲前进/后退



### 增强：播放模式切换

在player/use-mode.js实现，利用hook函数拆分功能 

1. 根据state展示不同的播放模式icon
2. 封装changeMode Action，改变播放模式、歌曲列表，固定当前歌曲不变

### 增强：歌曲收藏

