主要介绍vue3中的响应式数据

## ref

### ref 基本类型

```vue
<template>
  <div class="person">
    <h2>姓名：{{ name }}</h2>
  </div>
</template>
<script setup>
let initName = "张三"
let name = ref(initname)
function changeName(){
    name.value = 'zhangsan'
}
</script>

```

> ref返回refimpl类型，ref.value返回proxy
>
> value属性是基于原始数据创建的代理（proxy），因此`name.value === initName // false`
>
> 模板中不需要使用.value，直接使用ref返回的结果，**因为在模板中访问value属性是自动的**

### ref 对象类型

对象的所有属性和嵌套的属性都会变成响应式的

```ts
  let car = ref({
    brand: '奔驰',
    price: 100,
  })
  let games = ref([
    {id: '1', name: '王者'},
    {id: '2', name: '元神'},
  ])
  function changePrice(){
    car.value.price++;
  }
  function changeFirstGame(){
    games.value[0].name = 'cf'
  }
```



![image-20240308163951905](./images/image-20240308163951905.png)

使用ref对象生成响应式数据
script中需要.value
模板中无需.value

- 对象类型的ref的value值是 Proxy 对象，所以ref实现对象类型响应式数据的**底层原理仍然是reactive**

## reactive 对象类型

只接受**广义的对象类型**作为参数

嵌套的属性也会转为响应式数据

```vue
<template>
  <div class="person">
    <h2>brand：{{ car.brand }}</h2>
    <h2>price：{{ car.price }}</h2>
    <button @click="changePrice">修改价格</button>
  </div>
</template>

<script setup lang="ts" name="Person">
  import { reactive } from 'vue';
  let car = reactive({
    brand: '奔驰',
    price: 100,
  })
  let games = reactive([
    {id: '1', name: '王者'},
    {id: '2', name: '元神'},
  ])
  function changePrice(){
    car.price++;
  }
  function changeFirstGame(){
    games[0].name = 'CF'
  }
</script>
```

> reative直接返回proxy

![image-20240308164901310](./images/image-20240308164901310.png)

## ref 对比 reactive

> reactive：
>
> 1. ###### 一个响应式对象，层次较深
>
> 2. 一次定义多个响应式数据
>
> ref：
>
> 1. **需要一个基本类型的响应式数据，必须用ref**
> 2. 

> 1. ref 创建的变量必须使用 `.value` (可以使用volar自动添加)
> 2. reactive 重新分配一个新对象，会失去响应

```ts
function changeCar(){
    let car1 = {brand:'宝马',price:123}
    //car = car1;car = reactive(car1);// 无响应性
    Object.assign(car, car1)//用car1的属性批量修改car的属性
    // 本质上car的地址没有发生改变
}
```

> 1. 

### 解构赋值和 toRefs

toRefs() 传入一个reactive对象，将对象的每一组键值对转换成ref响应式数据，但值还是和原reactive对象是一致的

toRef(person,'age') 指定person对象中的age属性，转化为ref

## computed计算属性

> 使用**计算属性**来描述依赖响应式状态的复杂逻辑

- 计算属性有缓存
    只有当依赖的数据发生变化时才会重新计算计算属性，重新return
- **计算属性是只读的**
- 可以多次复用，更灵活
- 每个计算属性都是一个函数
- 模板中直接使用函数名访问计算属性的value

> [!caution]
>
> 回调函数参数必须要有返回值，不然默认返回undefined

```ts
// 接受一个不带参数的回调函数
let fullName = computed(()=>{
    return firstName.value.slice(0, 1).toUpperCase() + firstName.value.slice(1) + '-' + lastName.value
})
```

```ts
//可读可写的计算属性的写法(很少用到)
  let fullName = computed({
    get(){
      return firstName.value.slice(0, 1).toUpperCase() + firstName.value.slice(1) + '-' + lastName.value
    },
    set(val){
      const [s1, s2] = val.split('-')
      firstName.value = s1;
      lastName.value = s2;
    }
  })
  function changeFullName(){
    fullName.value = 'li-si'
  }
```

> 被依赖的属性不能是一个const的本地变量，它永远不会发生变化

## 标签的ref属性

根据id获取dom`document.getElementById('title')`
如果不同组件id冲突，获取到的dom也会发生冲突

对于普通html标签使用 ref

```vue
<template>
    <h2 ref="title2">你好</h2>
    <button @click="showLog">展示你好</button>
    <Person/>
</template>
<!-- 组件脚本 -->
<script setup lang="ts" name="App">
    import Person from './components/Person.vue'
    import {ref} from 'vue'
    let title2 = ref()
    function showLog(){
        console.log(title2.value)
    }
</script>
```

```vue
<!-- 组件结构 -->
<template>
    <h2 ref="title2">你好</h2>
    <button @click="showLog">展示你好</button>
    <Person ref="ren"/>
</template>
<!-- 组件脚本 -->
<script setup lang="ts" name="App">
    import Person from './components/Person.vue'
    import {ref} from 'vue'
    let title2 = ref()
    let ren = ref()
    function showLog(){
        console.log(ren.value)
    }
</script>
```

用在组件标签上，获取的是组件实例对象

```vue
<Person ref="ren"/>

let ren = ref()
    function showLog(){
        console.log(ren.value)
    }
// 子组件需要定义可以输出的内容才能输出
<script setup lang="ts" name="Person">
  import { ref, defineExpose } from 'vue';
  // 用于存储ref标记的内容
  let title2 = ref()
  let a = ref(0)
  let b = ref(1)
  let c = ref(2)
  function showLog(){
    console.log(title2.value)
  }
  defineExpose({a,b,c})
</script>

```





