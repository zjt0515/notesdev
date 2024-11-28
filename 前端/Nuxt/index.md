# nuxt

## 参考资料

1. https://nuxt.com.cn/
2. https://ezdoc.cn/docs/nuxtjs/getting-started/introduction
3. https://nuxt.zhcndoc.com/

- 客户端和服务端渲染https://juejin.cn/post/7012492790642769934



后台管理应用：适合单页面模式+客户端渲染

内容多+seo：nuxt

不需要seo：多页面就不需要了

## 单页面和多页面开发模式

vue一般适合SPA单页面应用，不利于SEO优化

只有几个页面的应用建议使用多页面应用

单页面模式SPA：

1. 只有一个页面，一个head，不利于seo优化
2. 首页加载慢（首次加载），后序内容直接替换，加载快

多页面应用：

1. 利于SEO优化
2. 每次切换页面重新加载，加载慢

## 客户端和服务端渲染

> [!tip]
>
> 本质区别：谁来完成html文件的完整拼接
>
> 

客户端渲染：

1. 爬取内容是`{{content}}`不利于seo优化
2. 



服务端渲染：

1. 直接返回内容，利于SEO优化
2. 客户端耗时少，减少占用资源，只需解析标准的html页面，尤其是移动端
3. 不利于前后端分离，开发效率低
4. 占用服务器端资源

##  

## 快速入门

服务端内容会在ide以及浏览器（显示为SSR）中输出

触发服务端：重新请求页面 

启动`npm run dev -- -o`

## 配置



## 路由

基于vuerouter，所有pages中的vue组件最终会生成一个routes路由数组，每个vue文件都会对应一条url



> [!tip]
>
> 1. `<NuxtPage/>` 代替 `<RouterView/>`
> 2. ``<NuxtLink to="/"/>` 代替 `<RouterLink/>`

### NuxtLink链接组件

```vue
<ul>
  <li><NuxtLink to="/about">About</NuxtLink></li>
  <li><NuxtLink to="/posts/1">Post 1</NuxtLink></li>
  <li><NuxtLink to="/posts/2">Post 2</NuxtLink></li>
</ul>
```

### 导航参数

```vue
<script setup lang="ts">
const route = useRoute()

// When accessing /posts/1, route.params.id will be 1
console.log(route.params.id)
</script>
```

### 路由中间件

```vue

```

切换路由是客户端渲染，仅仅在本地切换了内容
