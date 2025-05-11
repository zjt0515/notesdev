## watch

监视数据的变化

1. ref定义的数据
2. reactive定义的数据
3. 函数，返回一个值 
4. 一个包含上述内容的数组

```vue
<script setup>
	watch(
    // 监听对象
  	data,
    // 监听回调
    (newData, old) => {}
    // 配置参数对象
    {
    	deep:,
    	immediate:
    }
  )

</script>
```



### 监听ref基本数据类型

ref定义的基本数据类型，直接写数据名，监视其value值的变化

```ts
<script setup lang="ts" name="Person">
  import { ref, watch} from 'vue'
  let sum = ref(0)
  function changeSum(){
    sum.value += 1
  }
// watch返回一个取消监视函数
  const stopWatchSum = watch(sum, (newValue, oldValue)=>{
    console.log('sum改变',newValue, oldValue)
    if(newValue >= 5) stopWatchSum()
  })
  console.log(stopWatchSum)
</script>
```

- watch的第一个参数是refImpl类型，不用.value
- 如果要用.value，必须使用回调函数`()=> data.value`

### 监听整个ref对象数据类型

监听整个对象 → watch比较的是每个对象的引用值
修改对象属性不会创建新的对象 → watch无法监听到对象属性变化
解决办法：开启deep，**但是**new和old都是修改后的proxy(不能访问修改前的值)

进一步解决无法访问修改前的值：使用(深度)拷贝，监听新拷贝的对象

1. `...`浅拷贝，适合只有一层的对象
2. `JSON.parse(JSON.stringify(data.value))`

```ts
<script setup lang="ts" name="Person">
  import { ref, watch} from 'vue'
  let person = ref({
    name:'张三',
    age: 19
  })
  function changeName(){
    person.value.name += '~'
  }
  function changePerson(){
    person.value = { name: '李四', age: 199}
  }
  // 监视ref对象，监视的是对象的地址值
  // 监视ref对象内部属性，手动开启深度监视
  // immdiate作用是:被监测的对象生命周期开始时就会被watch一遍
  const stopWatch = watch(
    person,
		(newValue, oldValue)=>{
    	console.log(newValue,oldValue)
    },
    {
    	deep:true,immediate:true
    }
	)
</script>
```

- 修改整个ref定义的对象，对象地址改变了，newValue和oldValue不同

### 监听reactive对象数据类型

1. 直接watch对象本身

```ts
<script setup lang="ts" name="Person">
  import { reactive, ref, watch} from 'vue'
  let person = reactive({
    name:'张三',
    age: 19
  })
  function changeAge(){
    person.age += 1
  }
  function changeName(){
    person.name += '~'
  }
  // function changePerson(){
  //   person = { name: '李四', age: 199}
  // }
  function changePerson(){
    Object.assign(person, {name:'李四',age:199})
  }
  // reactive默认开启深度监视
  const stopWatch = watch(person,(newValue, oldValue)=>{
    console.log(newValue,oldValue)
  })
</script>
```

- 深度监测，仅仅修改对象的属性值，newValue和oldValue都是新值

### 监视对象类型中的某个属性

监视对象中的属性，都可以写成函数式

```ts
<script setup lang="ts" name="Person">
  import { reactive, ref, watch} from 'vue'
  // 数据
  let person = reactive({
    name:'张三',
    age: 18,
    car:{
      c1:'宝马',
      c2:'奥迪'
    }
  })
  function changeName(){
    person.name += '~'
  }
  function changeAge(){
    person.age += 1
  }
  function changeCar1(){
    person.car.c1 = '迈凯伦'
  }
  function changeCar2(){
    person.car.c2 = '大众'
  }
  function changeCar(){
    person.car = {c1:'电竞整车1',c2:'电竞整车2'}
  }
  watch(()=>person.name, (newValue,oldValue)=>{
    console.log(newValue,oldValue)
  })
  watch(()=>person.car, (newValue,oldValue)=>{
    console.log(newValue,oldValue)
  },{deep:true})
</script>
```

- 监视对象中的基本类型属性，写成函数式
- 监视对象中的对象属性，**也建议写成函数式，同时必须开启深度监视**
    - 如果不写成函数式，**修改被监视的对象地址后，监视失效**



### 监视上述的多个数据

使用数组包裹即可

若上述的情况处于同一个数组中，数组中的值也必须满足上述条件

```vue
<script>
watch(
	[],
  (news, olds) => {},
	{}
)
</script>
```



### watchEffect

参数：接受一个回调函数
只要回调函数中的响应性数据发生变化，回调函数就会重新执行

1. 不用明确监听的响应性数据，自动判断
2. 会先执行一次
3. **不能访问数据修改前的值**

```ts
<script setup lang="ts" name="Person">
let height = ref(0)
let temp = ref(0)
function changeHeight(){
  height.value += 10
}
function changeTemp(){
  temp.value += 10
}
// watch实现
// watch([temp, height],(val)=>{
//   let [tempVal, heightVal] = val
//   if(tempVal >= 100 || heightVal >= 30){
//     console.log('不能再升高了')
//   }
// })
// watchEffect实现
watchEffect(()=>{
  if(height.value >= 30 || temp.value >= 100){
    console.log('不能再高了')
  }
})
</script>
```

watchEffect 不用明确指出监视的数据，只要函数中用到哪些**响应性**数据就监视哪些数据

### onInvalidate

监听中做一些清理操作

```vue
<script>
watch(
	data,
  (new,old, onInvalidate)=>{
    
    onInvalidate(() => {
      // 清理操作
    })
  }
)
</script>
```

第一