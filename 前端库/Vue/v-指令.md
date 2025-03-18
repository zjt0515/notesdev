# 指令

## 条件渲染





## 列表渲染 v-for

### vfor与数组

> 在 `v-for` 块中可以完整地访问父作用域内的属性和变量。`v-for` 也支持使用可选的第二个参数表示当前项的位置索引。即`(item,index) = items`

```vue
//渲染数组
const items = ref([{ message: 'Foo' }, { message: 'Bar' }])
<li v-for="(item,[index]) in items">
  {{ item.message }}
</li>
//多层嵌套
<li v-for="item in items">
  <span v-for="childItem in item.children">
    {{ item.message }} {{ childItem }}
  </span>
</li>
```

> 可以使用 of 作为分隔符代替 in

```vue
//定义 `v-for` 的变量别名时使用解构，和解构函数参数类似：
<li v-for="({name,path},index) of items">
 {{ name }}, {{ path }}
</li>
```



### v-for与对象

## v-if v-else-if v-else

v-if被触发时，元素及其包含的指令和组件都会销毁并重构

当条件为false，内部内容不会被渲染

可用于template

### v-else-if

上一个兄弟元素必须有v-if或v-else-if

### v-else

上一个兄弟元素必须有v-if或v-else-if

## v-for

适用于：`Array | Object | number | string | Iterable`

```vue
<div v-for="(item, index) in items" :key="item.id"></div>
<div v-for="(value, key) in object" :key="item.id"></div>
<div v-for="(value, name, index) in object"></div>
```

> 必须加上`:key="id"`，否则报错
> 同时这个特殊属性key 提供了排序提示



`<li v-for="p in list" :key="p.id">`

如果不加key，默认以索引值为key，容易导致数据错乱
一般后端传入的值中由unique_id，就以他作为key，否则才用index

详见[列表渲染]()

## v-on / @

绑定事件监听器

绑定值类型：`Function | Inline Statement | Object (不带参数)`

```vue
// 监听原生DOM事件
<button v-on:click="doThis"></button>
// 监听子组件触发的自定义事件
<MyComponent @my-event="handleThis" />
```

## v-bind / : / .



## v-model

在表单输入元素或组件上创建双向绑定。



## 自定义指令

参数

1. el：指令绑定的元素
2. binding：对象
    1. value 传递给指令的值
    2. oldValue 之前的值
    3. arg 指令参数
    4. 

```ts

const myDirective = {
  // 在绑定元素的 attribute 前
  // 或事件监听器应用前调用
  created(el, binding, vnode) {
    // 下面会介绍各个参数的细节
  },
  // 在元素被插入到 DOM 前调用
  beforeMount(el, binding, vnode) {},
  // 在绑定元素的父组件
  // 及他自己的所有子节点都挂载完成后调用
  mounted(el, binding, vnode) {},
  // 绑定元素的父组件更新前调用
  beforeUpdate(el, binding, vnode, prevVnode) {},
  // 在绑定元素的父组件
  // 及他自己的所有子节点都更新后调用
  updated(el, binding, vnode, prevVnode) {},
  // 绑定元素的父组件卸载前调用
  beforeUnmount(el, binding, vnode) {},
  // 绑定元素的父组件卸载后调用
  unmounted(el, binding, vnode) {}
}
```


> [!tip]
>
> 只有当所需功能只能通过直接的 DOM 操作来实现时，才应该使用自定义指令。其他情况下应该尽可能地使用 `v-bind` 这样的内置指令来声明式地使用模板，这样更高效，也对服务端渲染更友好。


> [!warning]
>
> 不推荐在组件上使用自定义指令。当组件具有多个根节点时可能会出现预期外的行为。
>
> 当在组件上使用自定义指令时，它会始终应用于组件的根节点，和[透传 attributes](https://cn.vuejs.org/guide/components/attrs.html) 类似。



# 面试题

## v-if和v-for优先级

实践中不能把两个放在一起

vue2和vue3的优先级是相反的，vue2是v-for优先级更高，vue3是vif优先级更高

正确实践：定义计算属性，将希望杯渲染的数据提前过滤一遍