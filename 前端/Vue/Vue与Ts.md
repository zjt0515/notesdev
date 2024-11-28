

# TS简易基础

编译型语言，最终编译成js







## 类型定义

https://cn.vuejs.org/guide/typescript/composition-api#typing-ref

类型定义

1. ref
2. props
3. emits
4. computed
5. provide
6. inject

> [!caution]
>
> vue组件不支持外部导入接口，所有接口必须在组件内部定义

### ref

```ts
import { type Ref } from "vue"
// 不标注：ref会自动推导
const year = ref(2020)
// 标注复杂类型：使用Ref<>类型
const year: Ref<string | number> = ref('2020')
// ref也支持传入泛型参数
const year = ref<string | number>('2020')
// 给出泛型参数，但没有赋默认值的情况 Ref<number | undefined>
const n = ref<number>()
// 使用接口
interface Product {
  id: number;
  title: string;
  imageUrl?: string;
}
const products = ref<Product[]>([]);
```

### props

```ts
// 无法确定类型
defineProps(["id", "title", "imageUrl"]);

// 使用接口和泛型参数
interface Props {
  id: number;
  title: string;
  imageUrl?: string;
}
defineProps<Props>()

// js方式，不推荐
defineProps({
  id: {
    type: String,
  }
})
```

`传递props：<Child v-bind="product">`或者`:title="product.title"`



### reactive

```ts
// 不标注自动推导
const book = reactive({ title: 'Vue 3 指引' })
// 使用接口标注
interface Book {
  title: string
  year?: number
}
const book: Book = reactive({ title: 'Vue 3 指引' })
// 不推荐使用泛型参数
```

### computed

```ts
// 自动推导
// 泛型参数，显示指定
const double = computed<number>(() => {
  // 若返回值不是 number 类型则会报错
})
```

