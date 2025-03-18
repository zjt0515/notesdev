# 集中式状态管理

类似工具：reudx、vuex、pinia

链接：[pinia](https://pinia.vuejs.org/zh/)

vuex：
- state 存放数据
- Getters 类似计算属性
- Mutations 修改状态
- Actions 异步操作

pinia：mutations是自动的

- state
- Getters
- Actions 同步异步都支持

各个组件之间信息共享
将共享的数据交给集中式状态管理

引入创建并安装pinia

```ts
// main.ts
import {createPinia} from 'pinia'
const pinia = createPinia()
app.use(pinia)
```

分类

新建`store`文件夹，新建文件`xxx.ts`
文件内定义常量`const useXxxStore=define('xxx',state(){return{}})`



## store

所有组件共享store

内置state函数，该函数返回一个对象

> [!caution]
>
> 容器 id 需唯一
>
> state必须是函数，箭头函数为了更好地ts数据推导



创建store

```ts
export const useCounterStore = defineStore('counter', () => {
  // 具体内容
  const count = ref(0)
  const doubleCount = computed(() => count.value * 2)
  function increment() {
    count.value++
  }
  return { count, doubleCount, increment }
})
export const useUserStore = defineStore('user', () => {
  const user = ref({
		userId: undefined,
   	username: undefined,
    userRole: 
  })
  // 返回对象
  return { user }
})
```

使用store中的state

```ts
const userSotre = useUserStore()
userStore.user
```

修改state

```ts
const userStore = useUserStore()
// 直接修改
uesrStore.user = {... }
```



> state是数据
> getters是计算属性
> actions是方法
>
> ref就是state属性
> computed() 就是getters()
> function() 就是actions
>
> 同时，要添加返回的参数



> option
>
> ```ts
> // option store
> import { defineStore } from 'pinia'
> export const useXxxStore = defineStore('id',{
>   //数据存储全局状态
>   state: ()=>{
>     return {
>         sum: 20
>     }
> 	},
>   //类似于计算属性，有缓存功能，函数接受一个可选参数state
>   //可以不用state，直接在函数体内用this，但是要手动指定返回值
>   getters: {
>     count10 (state) {
>       return state.count + 10
>     }
>   },
>   // 封装业务逻辑，修改state
> 	actions:{
>     	// 不能使用箭头函数定义action(因为箭头函数绑定外部)
>       increment(value:any){
>         this.sum += value
>         console.log(this.$state.sum)
>       },
>     	updateUser (User:user) {
>         this.User = User
>       }
>  	 },
> 	// 真正存储数据的地方
> })
> ```



## state

state 被定义为一个返回初始状态的函数

### 直接修改 state

> 不过，用这种语法的话，有些变更真的很难实现或者很耗时：任何集合的修改（例如，向数组中添加、移除一个元素或是做 `splice` 操作）都需要你创建一个新的集合。因此，`$patch` 方法也接受一个函数来组合这种难以用补丁对象实现的变更。

```vue
<template>
	{{ countStore.sum }}
</template>
<script>
	import { useCountStore } from '@/store/count'
    const countStore = useCountStore() // 此时开发者工具中出现count
    console.log(countStore.sum)
    console.log(countStore.$state.sum)
  	// 直接使用解构赋值就没有响应式，需要用官方给的API
  	const {a, b} = storeToRefs(conutStore)
    function add(){
        // 第一种修改方式
        countStore.sum += 1
        // 2. 使用$patch批量更新，修改多个数据
        countStore.$patch({
            sum:888,
            school:'njupt'
        })
      	// $patch 一个函数,批量更新,支持更复杂的操作
      	countStore.$patch(state => {
            state.sum++
          	state.arr.push(4)
        })
        // 3. 逻辑比较多，封装到actions中
        countStore.increment(20)
    }
</script>
```

> 通用规则，写到store共享区域
>
> 组件复用的逻辑写到外面，自己组件的逻辑写组件内



### $patch()修改多个state

调用store的$patch函数，传入

```ts
noteStore.$patch({
	notesState: [],
	searchTerm: "",
})
```

### actions修改状态

方便组件之间复用状态修改逻辑，不用在每个组件中单独写修改的逻辑，每个组件触发action即可修改状态
action就是将函数封装到store内部

```ts

```

### 异步的action

方便进行远程的数据加载和一些比较耗时的业务逻辑操作来修改状态

```ts
```



## getters(computed)

getters就是computed

比如要通过筛选某个属性查询全局状态，就可以将相关逻辑直接将getters写在store里，方便服用

> [!tip]
>
> pinia支持直接修改state，因此可以使用vmodel直接绑定state 

```
export const useUserStore = defineStore('user', () => {
  const user = ref({
		userId: undefined,
   	username: undefined,
    userRole: 
  })
  const searchName = ref("")
  
  const searchedUser = computed(()=>{
  	if(searchName.value === ""){
  		return user.vaue;
  	} else {
  		return user.value.filter(user => user.userName === )
  	}
  })
  // 返回对象
  return { user, searchName, searchedUser  }
})
```





## 底层/原理

pinia将state封装成reactive对象

