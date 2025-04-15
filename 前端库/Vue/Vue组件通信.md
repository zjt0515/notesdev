需求：如果只有2个组件需要共用1组值，如何通信

1. 动态路由 → 给路由组件传参
2. props → 组件属性方式
3. 

## props声明和传递

### 组件定义数据props

显式声明接受的props

`defineProps()`传入参数：**字符串数组或对象**
返回值：一个对象 ，包含传递给组件的所有props

```js
// 字符数组
const props = defineProps(['title','context'])
console.log(props.title)
console.log(props.context)
// 限制类型
const x = defineProps<{list:Persons}>()
// TS+setup 泛型类型标注，不用
const props = defineProps({
  greetingMessage: String
  likes?: string
})
const props = defineProps<{
    title: String
}>()
//默认值写法
const props = withDefaults(defineProps<Props>(), {
  value: () => '',
  language: 'javascript',
  handleChange: (v: string) => {
},
// 使用props
 props.key
    
/**
 * vue2
*/
props: {
    menus: {
        type: Array as PropType<Array<MenuItem>>,
        default: () => [] as MenuItem[]
	}
    title: String	
}
```

>defineProps不需要显式导入
>defineProps仅在`<script setup>`中可以使用
>
>prop属性命名规范：camelCase
>向子组件传递的形参名：kebab-c

### 父组件传入Prop数据

```vue
// 父组件中为子组件传递数据
<template>
	// 静态prop
	<BlogPost greeting-message="my first blog" />
	// 动态prop，:就是v-bind缩写
	<BlogPost :greeting-message="message" />
	<BlogPost :greeting-message="56" />
	<BlogPost :greeting-message="false" />
	// 动静结合
	<BlogPost :greeting-message="'str' + message" />
</template>
```

> [!note]
>
> 传入prop命名：为了和 HTML attribute 对齐，我们通常会将其写为 kebab-case 形式
>
> 如果传入的值不是字符串，那么就要加上 : 或 v-bind 代表是一个表达式



```vue
//一个对象绑定多个prop的语法糖
<script>
  const post = {
  id: 1,
  title: 'My Journey with Vue'
}
</script>
<template>
<BlogPost v-bind="post" />//等价于下面的式子
<BlogPost :id="post.id" :title="post.title" />
</template>
```



## 单向数据流

props遵循单向绑定原则，因父组件更新而变化，将新状态向下流向子组件，不会逆向传递，避免子组件意外修改父组件状态的情况

### 为组件props标注类型



### ：解析变量

```ts
<h2 a="1+1" :b="1+1" c="x" :d="x" ref="qwe"></h2>
```

要在变量前加上冒号，引号内的内容才能是表达式，否则只是字符串
但是ref是个特例

## v-model

实现双向绑定



子组件

```vue
<script setup>
const model = defineModel()//返回一个ref，同时可以起到在父组件和当前变量之间双向绑定的作用

function update() {
  model.value++;//与父组件的v-model值同步
}
</script>
```



父组件

```vue
<!-- Parent.vue -->
<Child v-model="model" />
```

## 插槽

插槽可以为子组件传递模板片段

内部内容由父组件提供，子组件用于渲染插槽外层的布局样式

```vue
// FancyButton.vue
<button class="fancy-btn">
  <slot></slot> <!-- 插槽出口 -->
</button>

<FancyButton>
	click me!
</FancyButton>

//最终效果：
<button class="fancy-btn">
  Click me!
</button>
```

