## vue2

选项式API

- 属于同一个逻辑功能的代码分散，可读性差

```vue
<template>
	{{appId}}
</template>
<script>
	export default {
    data(){
      isShow: false,
			countDown: null,
    },
    props: ['appId']
    computed: {
      this.appId
    },
    methods: {
      doPushPage(){
        
      },
    },
    watch: {
      isShow(newVal, oldVal){
        
      },
    }
  })
</script>
```

创建组件

```ts
app.component('WordCount', {
  template: `
   <div>
    <input v-model="content"/>
   </div>
  `,
  data() {
    return {
      content: '',
    }
  },
  computed: {
    count() {
      return this.content.length
    },
  },
})
```





## vue3

### setup函数

setup函数中可以返回一个对象，对象中的属性可以直接在template中访问

```vue
<script>
	export default {
    setup(){
      return { messages: messages }
    }
  }
</script>
```



### 组合式API 

- 可以将一个功能的代码统一到一起 
- 可以抽离组件功能代码到单独的文件，提高复用性
- 可以与选项式API共存
- 建议逐步替换选项式API

```vue
<script setup>
  const data = ref(0);
  
  const doPushPage = () =>{};
  
  const isShowLable =  computed(()=>{ isShow ? "显示":"隐藏"});
  
</script>
```



## 总览

### 生命周期

vue3中没有beforeCreate和create，因为被setup函数取代了
API名称变化：前面加了on
