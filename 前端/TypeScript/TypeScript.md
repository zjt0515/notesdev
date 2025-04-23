### 三种暴露方法

1. 默认暴露

    `export`

2. 分别暴露

3. 同一暴露

### 接口

```ts
//@/types
// 定义一个接口，用于限制person对象的具体属性
export interface PersonInter{
  id: string,
  name: string,
  age: number
  x?:number
}
// 一个自定义类型
export type Persons = Array<PersonInter>
// export type Persons = PersonInter[]
```

```ts
<script setup lang="ts" name="Person">
  import {type PersonInter } from '@/types'
  import {type Persons } from './types';
  import { ref } from 'vue'
  let person:PersonInter = {id:'1', name:'steve', age:10}
  let personList:Array<PersonInter> = [
    { id: '0', name: '张三', age:20 },
    { id: '1', name: '张三', age:201 },
    { id: '2', name: '张三', age:2022}
  ]
  
    let personList = reactive<Persons>([
        {id:'1', name:'张三',age:19},
        {id:'12', name:'张三',age:19},
        {id:'013', name:'张三',age:19,x=123},
    ])
    console.log(personList)
</script>
```


