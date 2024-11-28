# 进阶路由

> 路由对象的属性和方法：
>
> 1. fullPath
> 2. path
> 3. href
> 4. hash
> 5. matched 匹配到的路由数组
> 6. meta matched数组中所有meta合并
> 7. name
> 8. params
> 9. query
>
> ```ts
> 
> ```
>
> 

## 导航守卫

1. 限制路由跳转
2. 更改路由跳转路径
3. 路由的生命周期钩子，在不同时期调用

配置方式：

1. 全局配置，即router中
2. 按路由配置，即routes中
3. 组件中配置

全局配置的守卫类型

1. beforeEach 导航触发时，组件还未加载，适合取消导航
2. beforeResolve 组件加载完毕，且导航实际跳转前执行
3. afterEach 导航确认并实际跳转之后执行

按路由配置的守卫类型

1. beforeEnter (/post/1跳转到/post/2不触发)

组件中配置的守卫

1. beforeRouteEnter 导航跳转时，组件创建前 
2. beforeRouteUpdate 导航跳转时，且复用组件 (例如从/post/1跳转到/post/2)
3. beforeRouteLeave 导航跳转时、组件销毁前 (可以用来提示未保存的操作)

> 参数：
>
> 1. to 跳转到的路由对象
> 2. from 跳转前的路由对象
> 3. next(不推荐使用)
>
> 返回值：
>
> 1. false 阻止导航
> 2. 无返回值/undefined/true 继续导航
> 3. 路由导航对象 跳转到新的路径 

> [!tip]
>
> 触发顺序：
>
> 1. 组件中的beforeRouteLeave
> 2. 全局的beforeEach
> 3. 组件中的beforeRouteUpdate
> 4. 路由对象的中的beforeEnter
> 5. 解析异步的导航守卫
> 6. 组件中的beforeRouteEnter
> 7. 全局的beforeResolve
> 8. 确认导航，页面发生跳转
> 9. 全局的afterEach
> 10. 更新DOM
> 11. beforeRouterEnter中的next()回调函数中的回调

### beforeRouteLeave守卫

## 全局导航守卫

1. beforeEach 导航触发时，组件还未加载，适合取消导航
2. beforeResolve 组件加载完毕，且导航实际跳转前执行
3. afterEach 导航确认并实际跳转之后执行

### 全局前置守卫beforeEach

```ts
// router.ts

const router = createRouter({ ... })
router.beforeEach((to, from, next) => {
  // ...
  // 取消导航
  return false
  // 重定向导航
  return "/login";
  return { name: 'Login' }
   if (to.name !== 'Login' && !isAuthenticated) next({ name: 'Login' })
  else next()//必须保证next都只被严格调用一次
})
```

### 全局解析守卫beforeResolve

> 解析守卫刚好会在导航被确认之前、**所有组件内守卫和异步路由组件被解析之后**调用。
>
> 用于获取数据或执行任何其他操作（如果用户无法进入页面时你希望避免执行的操作）

```js
router.beforeResolve(async to => {
  if (to.meta.requiresCamera) {
    try {
      await askForCameraPermission()
    } catch (error) {
      if (error instanceof NotAllowedError) {
        // ... 处理错误，然后取消导航
        return false
      } else {
        // 意料之外的错误，取消导航并把错误传给全局处理器
        throw error
      }
    }
  }
})
```

### 全局后置钩子afterEach

路由跳转后执行

> 这些钩子不会接受 `next` 函数也不会改变导航本身
>
> 用于分析、更改页面标题、声明页面等辅助功能以及许多其他事情

```js
router.afterEach((to, from, failure) => {
  if (!failure) sendToAnalytics(to.fullPath)
})
```





### beforeRouteUpdate守卫

## 路由独享守卫beforeEnter(路由内)

> 直接在路由配置上定义
>
> **只在进入路由时触发**，不会在 `params`、`query` 或 `hash` 改变时触发。
>
> 对所有子路由也会生效

```js
const routes = [
  {
    path: '/users/:id',
    component: UserDetails,
    beforeEnter: (to, from) => {
      // reject the navigation
      return false
    },
  },
]
```

> [!tip]
>
> beforeEnter支持多个函数，即接受多个回调函数
>
> ```ts
> const routes = [
>   {
>     path: '/users/:id',
>     component: UserDetails,
>     beforeEnter: [auth1, auth2]
>   },
> ]
> ```



> [!caution]
>
> 对于含有动态参数的url，在相同的路由之间跳转时，因为是组件复用，路由没有发生跳转，
> 所以beforeEnter导航守卫不会执行

## 组件导航守卫

> 这里的组件指的是页面组件，即在routes中配置的component，其他一般组件不能使用导航守卫

### beforeRouteEnter

不能直接访问组件实例，可以通过next访问组件vm实例

> [!caution]
>
> 在第一次渲染该组件时才会执行，动态参数复用同一个组件不会执行

```vue
// xxxPage.vue
<script>
beforeRouteEnter(to, from){
  next((vm) => {
    vm.blog = getBlostPostById(to.params.postId); 
  })
}
</script>
```

### beforeRouteUpdate

> 不同于Enter, Update会在动态参数变化时执行

### beforeRouteLeave

离开当前页面前，组件失活前调用

## 导航解析流程

1. 导航被触发。
2. 在失活的组件里调用 `beforeRouteLeave` 守卫。
3. 调用全局的 `beforeEach` 守卫。
4. 在重用的组件里调用 `beforeRouteUpdate` 守卫(2.2+)。
5. 在路由配置里调用 `beforeEnter`。
6. 解析异步路由组件。
7. 在被激活的组件里调用 `beforeRouteEnter`。
8. 调用全局的 `beforeResolve` 守卫(2.5+)。
9. 导航被确认。
10. 调用全局的 `afterEach` 钩子。
11. 触发 DOM 更新。
12. 调用 `beforeRouteEnter` 守卫中传给 `next` 的回调函数，创建好的组件实例会作为回调函数的参数传入。





## 路由元信息meta

将更多自定义信息附加到路由上，即路由的meta属性

```ts
const routes = [
  {
    path: '/posts',
    children: [
      {
        path: 'new',
        // 只有经过身份验证的用户才能创建帖子
        meta: { requiresAuth: true },
      },
      {
        path: ':id',
        // 任何人都可以阅读文章
        meta: { requiresAuth: false },
      }
    ]
  }
]
```



访问meta

`route.meta`访问路由匹配到的所有路有记录的meta字段

> [!warning]
>
> route.meta会将route匹配到的所有路由的meta属性都合并
>
> 因此一般只在父路由中写一遍meta属性即可，子路由会自动合并父路由的meta
>
> meta的合并是浅合并的，子对象不会递归合并，相同的属性会被后面的路由替代

```ts
// 访问meta
router.beforeEach((to,from) =>{
  // 使用
  to.meta
})
// 下面两条作用一样
to.matched.some(record => rocord.meta.private && !loggedin)
// matched中所有路由的meta
to.meta.private && !loggedin
```



## 路由之后：信息获取

进入某个路由后，通常需要从后端获取数据

1. 导航完成后获取
2. 导航完成前获取

### 导航后获取

导航 → 加载组件 → (展示loading动画) → 获取数据 → 数据响应式加载

获取数据写在组件的挂载生命周期钩子里

### 导航前获取

## 控制滚动条

```ts
const router = createRouter({
  ...,
  scrollBehavior(to,from,savedPosition) {
   	return {
      top: 0
    }
	}
})
```

