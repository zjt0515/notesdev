## 链接

https://v2.cn.vuejs.org/v2/cookbook/editable-svg-icons.html



## 图标字体

 准备资源：

1. icon.ttf + icon.woff

```scss
// 引入图标字体
@font-face {
  font-family: 'music-icon';
  font-family: 'music-icon';
  src: url('../fonts/music-icon.eot?2qevqt');
  src: url('../fonts/music-icon.eot?2qevqt#iefix') format('embedded-opentype'),
  url('../fonts/music-icon.ttf?2qevqt') format('truetype'),
  url('../fonts/music-icon.woff?2qevqt') format('woff'),
  url('../fonts/music-icon.svg?2qevqt#music-icon') format('svg');
  font-weight: normal;
  font-style: normal;
}
[class^="icon-"], [class*=" icon-"] {
  /* use !important to prevent issues with browser extensions that change fonts */
  font-family: 'music-icon' !important;
  speak: none;
  font-style: normal;
  font-weight: normal;
  font-variant: normal;
  text-transform: none;
  line-height: 1;

  /* Better Font Rendering =========== */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

// 图标伪类
.icon-ok:before {
  content: "\e900";
}

.icon-close:before {
  content: "\e901";
}

.icon-add:before {
  content: "\e902";
}

.icon-play-mini:before {
  content: "\e903";
}

.icon-playlist:before {
  content: "\e904";
}

.icon-music:before {
  content: "\e905";
}

.icon-search:before {
  content: "\e906";
}

.icon-clear:before {
  content: "\e907";
}

.icon-delete:before {
  content: "\e908";
}

.icon-favorite:before {
  content: "\e909";
}

.icon-not-favorite:before {
  content: "\e90a";
}

.icon-pause:before {
  content: "\e90b";
}

.icon-play:before {
  content: "\e90c";
}

.icon-prev:before {
  content: "\e90d";
}

.icon-loop:before {
  content: "\e90e";
}

.icon-sequence:before {
  content: "\e90f";
}

.icon-random:before {
  content: "\e910";
}

.icon-back:before {
  content: "\e911";
}

.icon-mine:before {
  content: "\e912";
}

.icon-next:before {
  content: "\e913";
}

.icon-dismiss:before {
  content: "\e914";
}

.icon-pause-mini:before {
  content: "\e915";
}
```

```vue
<template>
	<i class="icon-back"></i>
</template>
```

