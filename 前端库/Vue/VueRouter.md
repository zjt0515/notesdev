# Vue Router

## 代码参考



## 介绍

SPA：single page web application 单页面应用
点击一个导航项，页面路径变化，被路由器检测到后，路由器进行规则匹配，挂载对应的组件

### 参考资料

- https://router.vuejs.org/zh/guide/

`npm install vue-router`

```vue
//main.ts
app.use(router)
```

### 如果不使用VueRouter

不适合大型应用

如果自己写得不好，会导致 页面整个刷新，vue应用重新加载，浪费性能，组建状态和全局状态会重置

解决办法：historyAPI

## 定义router

```js
//@/router/index.js：路由管理器
import { createMemoryHistory, createRouter } from 'vue-router'
import HomeView from './HomeView.vue'
import AboutView from './AboutView.vue'
// 创建路由器
const router = createRouter({
  history: createMemoryHistory(), // 路由器工作模式
  routes,
})
//导出router方式: 默认导出
export default router

const routes = [
  { path: '/', component: HomeView },
  { path: '/about', component: AboutView },
]
```

createRouter

1. history → 配置router处理url变化的方式
    1. createWebHistory
2. 



> [!note]
>
> 1. [全局注册](https://cn.vuejs.org/guide/components/registration.html#global-registration) `RouterView` 和 `RouterLink` 组件。
> 2. 添加全局 `$router` 和 `$route` 属性。
> 3. 启用 `useRouter()` 和 `useRoute()` 组合式函数。
> 4. 触发路由器解析初始路由。



### 访问路由器

`const router = useRouter()`

> [!caution]
>
> 如果使用 DOM 内模板，那么需要[注意](https://cn.vuejs.org/guide/essentials/component-basics.html#in-dom-template-parsing-caveats)：组件名字必须使用 kebab-case 风格且不支持自闭合标签。因此你不能直接写 `<RouterView />`，而需要使用 `<router-view></router-view>`。

### 定义视图组件(路由页面组件)

@/pages(views)/admin/AdminView：存放后台页面
@/pages(views)/frontend/：前台页面

### 路由器工作模式

```ts
history:createWebHistory()
hash:createWebHashHistory()
```

- history模式
    - url更美观，不带'#'
    - 项目上线需要服务端配合处理路径问题，否在刷新会有404错误
- hash模式
    - 兼容性更好，不需要服务端处理路径
    - #不美观而且SEO优化方面相对较差(适合于后台管理项目)

## 定义路由记录routes

routes是一个路由记录的数组，每个路由记录都是一个对象`RouteRecordRaw`



routes中定义路由数组，将url路径映射到视图组件

```js
export const routes: Array<RouteRecordRaw> = [
  {
    { path: '/', component: HomePage },
  	{ path: '/about', component: AboutPage },
  }
]
```

### 嵌套路由(子路由)

```json
const routes = [
  {
    path: '/user/:id',
    component: User,
    children: [
      {
        // 当 /user/:id/profile 匹配成功
        // UserProfile 将被渲染到 User 的 <router-view> 内部
        path: 'profile',
        component: UserProfile,
      },
      {
        // 当 /user/:id/posts 匹配成功
        // UserPosts 将被渲染到 User 的 <router-view> 内部
        path: 'posts',
        component: UserPosts,
        // 设置路由path别名，增加路径匹配项，如果原名中有路径参数，别名中也要有
        alias: ['postList']
      },
    ],
  },
]
```

父路由组件中引入RouterLink、RouterView，link中的路由url必须从父级开始写，不能单写子路径

访问子路由：

```st
<router-link to="/user/22/proile"/>
```





### 路由组件懒加载

使用import函数异步加载

```ts
const AddMarkdownPage = () => import('@/views/add/AddMarkdownPage.vue')
export const routes = [
  {
    path: '/add/markdown',
    name: '新建笔记',
    component: AddMarkdownPage,
  },
    {
    path: '/add/markdown',
    name: '新建笔记',
    component: () => import('@/views/add/AddMarkdownPage.vue'),
  },
]
```



## 路由导航

1. 导航信息与特定组件绑定`<router-link to="/about">Go to About</router-link>`
2. 编程式导航

### 声明式导航

声明式导航：`<route-link :to="...">`

### 命名路由精确跳转

1. 对于相同的路径，但是组件不同，可以通过命名路由精确匹配
2. 避免路径匹配出现歧义
3. 防止一长串的路径参数填写错误

```vue
<router-link :to="{ name: 'post', params: {id:50}, query:{...}}"/>
```

### 编程式导航useRouter

编程式路由导航使用频率大于直接用RouterLink，登录往往需要用到
RouterLink组件，但是浏览器认的是标签
脱离RouterLink实现自动路由跳转

`<button @click="$router.push()">`

> `router.push()`
>
> 参数：path字符串或者对象(path/name,params)
>
> 1. 会在浏览器历史记录中追加一条记录
>
> `router.replce()`
>
> 1. 替换掉历史记录最新的一条路由，即调用replace之前的路径
> 2. 再次发生跳转后，再返回，返回到调用replace之前的页面
>
> `router.go()` 前进后退
>
> 参数：int 前进后退步数

```ts
 const router = useRouter();
function push(){
  router.push('/members')
}
```

编程式导航传参，同to，push/replace参数传递一个对象或者一个字符串

```vue
<script setup lang="ts" name="Members">
import { reactive } from 'vue';
import { RouterLink, useRouter } from 'vue-router';

  const membersList = reactive([
    {id:'1',name:'Steve',identity:'农民'},
    {id:'2',name:'Alex',identity:'图书管理员'},
    {id:'3',name:'Snowman',identity:'铁匠'}
  ])
  const router = useRouter()
  interface MemberInter {
    name: string,
    identity: string
  }

  function showMember(member:MemberInter){
  router.push(
    {
      path: '/members/member',
      query:{
        name: member.name,
        identity: member.identity
      }
    }
  )
}
</script>
```

直接传入member会提示类型，可以直接用any，但不会检查对象属性
可以写一个接口来检查

## 动态路由匹配

```ts
{
      path: '/app/:appId',
      component: appDetail,
}
```

组件中使用`this.$route.params.appId`获取动态参数的值

> [!warning]
>
> 使用带有参数的路由时需要注意的是，当用户从 `/users/johnny` 导航到 `/users/jolyne` 时，**相同的组件实例将被重复使用**。因为两个路由都渲染同个组件，比起销毁再创建，复用则显得更加高效。**不过，这也意味着组件的生命周期钩子不会被调用**。

> VueRouter对于同组件中的路由跳转（**动态路由组件复用问题**）：
>
> 不会重新销毁和创建组件，而是复用组件实例，提高性能
>
> 但也造成生命周期钩子失效的问题
>
> 解决办法：使用watch监听



## 路由页面组件渲染

> 需求：
> 将`/users/johnny` 和 `/users/jolyne` 这样的 URL 映射到同一个路由。

```js
const routes = [
  // 动态字段以冒号开始
  { path: '/users/:id', component: User },
]
```

使用`<router-view></router-view>`

> 根据路由自动渲染对应的组件



## VueRouter内置组件

```vue
// 配置导航
<router-link to="/">主页</router-link>
<router-link to="/about">关于</router-link>
<router-link :to="">关于</router-link>
<router-link :to="{ name: 'post', params: {id:50}, query:{...}}"/>
// 展示页面组件
<router-view></router-view>
```

### routerlink路由切换

1. 导航区、展示区
2. 路由器
3. 路由的具体规则，路由-组件
4. 形成class.vue、subject.vue

### 路由跳转

1. 
2. 编程式导航



在`App.vue`中引入`RouterView`(最新版无需引入)并在展示区content添加对应标签`<RouterView />`
再引入`RouterLink`并添加对应标签`<RouterLink to="/home" active-class="active"></RouterLink>`注意要加上`.active`选择器

1. 路由组件通常`pages`或`views`文件夹
2. 一般组件通常放在`components`文件夹
3. 如何区分路由组件和一般组件？
    1. 路由组件靠路由组件的规则渲染出来
    2. 一般组件是亲手写出来的



#### 使用onMounted和unonMounted监测路由组件的挂载和卸载



#### RouterLink to的多种写法

字符串和对象两种写法，区别

1. 字符串写法不写冒号
2. 对象写法引号里加一个对象，包括name/path和要传递的参数等属性

```html
// 字符串写法
<RouterLink to="/home" active-class="active">首页</RouterLink>
// 对象写法
<RouterLink :to="{path:'/home'}" active-class="active">首页</RouterLink>
<RouterLink :to="{name:'zhuye'}" active-class="active">首页</RouterLink>
```

#### 命名路由

```ts
routes:[
    {
        name:'zhuye',
        path:'/home',
        component:Home
    }
    {
		name:'guanyu',
    	path:'/about',
    	component:About
    }
]
```

### 命名视图





## 路由组件传参



### 路由query传参

query传参

```vue
<template>
	<router-link :to="`/Members/member?name=${member.name}&identity=${member.identity}`">{{  member.name }}</router-link>
</template>
```

接受参数 useRoute

```vue
<template>
  <div class="member">
    <h2>姓名: {{ route.query.name }}</h2>
    <h2>身份: {{ route.query.identity }}</h2>
    <br>
  </div>
</template>

<script setup lang="ts" name="member">
  import { useRoute } from 'vue-router';
  import { toRefs } from 'vue';
  const route = useRoute()
  let { query } = toRefs(route)
</script>
```

### 路由params传参

传递params参数时，路由器中的路由参数需要提前占位

不确定需不需要传参可以加问号

```ts
{
  name: 'member',
  path: '/members',
  component: Members,
  children:[
    {
      path: 'member/:name/:identity？',
      component: Member
    }
  ]
}
```

模板字符串
```ts
:to="`/members/member/${member.name}/${member.identity}`"
```

对象参数写法

- 传递params参数时，如果使用to的对象写法，必须使用name配置项，不能用path
- 不能传数组

```vue
<script>
<li v-for="member in membersList" :key="member.id">
    <RouterLink :to="{
        name: 'member',
        params:{
          name:member.name,
          identity: member.identity,
        }
      }"
      >
    {{  member.name }}
  </RouterLink>  
</li>
</script>

```

接受参数
使用解构赋值减少

```vue
const route = useRoute()
let { params } = toRefs(route)
```

## 路由的props配置

第一种写法 props+params

`props:true`只能处理params参数
接受props参数` defineProps(['name','identity'])`

```ts
{
      name: 'members',
      path: '/members',
      component: Members,
      children:[
        {
          name: 'member',
          path: 'member/:name/:identity',
          component: Member,
          // 将路由收到的所有params参数，作为props传给路由组件
          props:true
        }
      ]
}
```

第二种写法 props+query

```ts
props(route){
    return route.query
}

// 接受参数
defineProps(['name','identity'])
```

第三种写法

```ts
// 基本不用，这样只能写死
props:{
    a:100,
    b:200
}
```

## replace属性

push模式
链接由栈保存，浏览器可以前进后退

replace模式
直接替换，浏览器不能前进后退





## 重定向和别名

### 重定向

让指定的路径重新定位到另一个路径, 重定向是指当用户访问 `/home` 时，URL 会被 `/` 替换，然后匹配成 `/`

```js
routes: [
    {
      path:'/home',
      redirect: '/'
      redirect: {
      	name : 'homepage'
    	}
  		//相对重定向
  		redirect: to => {
  			return 'profile'
  		}
    },
]
```

> 重定向属性可以是路径字符串，也可以是一个含有命名的路由对象





### 别名

> **将 `/` 别名为 `/home`，意味着当用户访问 `/home` 时，URL 仍然是 `/home`，但会被匹配为用户正在访问 `/`。**
>
> 通过别名，你可以自由地将 UI 结构映射到一个任意的 URL，而不受配置的嵌套结构的限制。使别名以 `/` 开头，以使嵌套路径中的路径成为绝对路径。你甚至可以将两者结合起来，用一个数组提供多个别名：

```js
const routes = [
  {
    path: '/users',
    component: UsersLayout,
    children: [
      // 为这 3 个 URL 呈现 UserList
      // - /users
      // - /users/list
      // - /people
      { path: '', component: UserList, alias: ['/people', 'list'] },
    ],
  },
]
```

