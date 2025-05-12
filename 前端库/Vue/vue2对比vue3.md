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
      return {
        isShow: false,
				countDown: null,
      }
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

### props

vue2

```vue
<script>
  export default {
  props: {
    // 基础类型检查
    //（给出 `null` 和 `undefined` 值则会跳过任何类型检查）
    propA: Number,
    // 多种可能的类型
    propB: [String, Number],
    // 必传，且为 String 类型
    propC: {
      type: String,
      required: true
    },
    // 必传但可为 null 的字符串
    propD: {
      type: [String, null],
      required: true
    },
    // Number 类型的默认值
    propE: {
      type: Number,
      default: 100
    },
    // 对象类型的默认值
    propF: {
      type: Object,
      // 对象或者数组应当用工厂函数返回。
      // 工厂函数会收到组件所接收的原始 props
      // 作为参数
      default(rawProps) {
        return { message: 'hello' }
      }
    },
    // 自定义类型校验函数
    // 在 3.4+ 中完整的 props 作为第二个参数传入
    propG: {
      validator(value, props) {
        // The value must match one of these strings
        return ['success', 'warning', 'danger'].includes(value)
      }
    },
    // 函数类型的默认值
    propH: {
      type: Function,
      // 不像对象或数组的默认，这不是一个
      // 工厂函数。这会是一个用来作为默认值的函数
      default() {
        return 'Default function'
      }
    }
  }
}
</script>
```

Vue3

