## 组件基础


### 定义单文件 SFC组件

SFC组件命名规范`PascalCase `

```vue
// 使用构建步骤定义SFC
<template>
</template>
<script setup lang="ts" name="">
</script>
```

### 组件注册

一般使用局部注册，只要在父组件中直接引用即可：

```vue
// 这种方法必须要使用setup
<script setup>
import ComponentA from './ComponentA.vue'
</script>
```


### 使用组件

> 如果直接在DOM中书写模板，使用`<PascalCase>`或者`<kebab-case />`都是可以的

```vue
<template>
	<Posts />
  <post />
</template>
<script>
import Posts from '@/components/posts.vue'
</script>
```





## props

```vue
const props = defineProps(['foo'])
```

### Setup

配置项，值为一个函数



### Setup语法糖

```vue
// 配置组件名
<script lang="ts">
  export default {
    name: 'Person',
  }
</script>
// 配置组件组合式api(使用setup语法糖)
<script setup lang="ts">
  // data
  let name = '张三'
  let age = 19
  let tel = '12345678'
  let address = '南京'
  // methods
  function changeName(){
    name = 'zhangsan'
  }
  function changeAge(){
    age++
  }
  function showTel(){
    alert(tel)
  }
</script>
```



### 使用开发依赖合并2个script

`npm i vite-plugin-vue-setup-extend -D`

```ts
//vite.config.ts中引入拓展
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import VueSetupExtend from 'vite-plugin-vue-setup-extend'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    vue(),
    VueSetupExtend()
  ],
})
```

```vue
<script setup lang="ts" name="Person1234">
  // data
  let name = '张三'
  let age = 19
  let tel = '12345678'
  let address = '南京'
  // methods
  function changeName(){
    name = 'zhangsan'
  }
  function changeAge(){
    age++
  }
  function showTel(){
    alert(tel)
  }
</script>
```



### OptionsAPI & CompositionAPI

vue2选项式API

```vue
<script lang="ts">
    export default {
	//OptionsAPI
    name: 'Person',
    data(){
      return {
        name: '张三',
        age: 18,
        tel: '13812811888'
      }
    },
    // methods后面加冒号再加大括号
    methods:{
      showTel(){
        alert(this.tel)
      },
      changeName(){
        this.name = 'zhangsan'
      },
      changeAge(){
        this.age +=1;
      }
    }
  }
</script>
```

vue3组合式API

```vue
<script lang="ts">
  export default {
    name: 'Person',
    beforeCreate() {
      console.log('beforcreate')
    },
    setup(){
      console.log(this) //setup中的this是undefine， vue3中弱化this
      // data
      let name = '张三'
      let age = 19
      let tel = '12345678'
      //此时的数据并不是响应的
      // methods
      function changeName(){
        name = 'zhangsan' //这样修改name，页面无变化，虽然name确实变化了，但不是响应式的
      }
      function changeAge(){
        age++ //这样修改age，无变化
      }
      function showTel(){
        alert(tel)
      }
        //前后一致时，可以简写为一个单词
      return {name:name, age:age, tel, changeAge, changeName, showTel}
    }
  }
</script>
```

新旧写法兼容性问题

- setup和data和methods可以共存
- setup中用不了this
- data和methods中可以用this，且可以用this读取setup中的内容，因为setup的生命周期更靠前，执行得更早
- setup中不可以读取data和methods的信息，因为setup初始化的时候data还没有初始化



## 获取组件实例



`this.$refs`为一个对象，包含所有ref属性值的属性名，属性值为对应的实例

 ```vue
 <input ref="input" type="text">
 <script>
 onMounted(()=>{
   // 获取原生实例
   this.$refs.input.focus();
   // 获取组件实例，并调用内部方法并获取内部值
   this.$refs.input.inputText
   this.$refs.input.testFunction();
 })
 </script>
 ```

> [!caution]
>
> 组件完全加载之后才能获取实例，不能在template中使用
>
> 可能产生的问题：会破坏组件数据流向，打破单项数据流规则，让错误难以发现



## 自定义组件



```vue
```



