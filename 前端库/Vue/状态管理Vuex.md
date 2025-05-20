# Vuex

## 项目结构

```
├── index.html
├── main.js
├── api
│   └── ... # 抽取出API请求
├── components
│   ├── App.vue
│   └── ...
└── store
    ├── index.js          # 我们组装模块并导出 store 的地方
    ├── actions.js        # 根级别的 action
    ├── mutations.js      # 根级别的 mutation
    └── modules
        ├── cart.js       # 购物车模块
        └── products.js   # 产品模块
```

## store





## createState

```js
```



## State

获取state

```vue
<script setup>
  import { useStore } from 'vuex'
  const store = useStore()
  // 使用computed封装
  // state中的count数据变化，本地count也会变化
  const count = computed(() => {
    return store.state.count
  })
  store.commit('increment'),
	store.dispatch('asyncIncrement')
</script>
```



## Getter

从state中派生出的状态，相当于state的计算属性

组件中使用

```vue
<script setup>
  import { useStore } from 'vuex'
  const store = useStore()
  store.getters.
</script>
```



## Mutation

更改state的唯一方法

定义mutation

```js
mutations: {
  increment (state, n) {
    state.count += n
  }
}
mutations: {
  increment (state, payload) {
    state.count += payload.n
  }
}
```

提交mutation

```js
store.commit('increment', {
  amount: 10
})
store.commit({
  type: 'increment',
  amount: 10
})
```



## Action

> 处理异步操作
>
> 1. 不直接更改state，而是提交mutation
> 2. 可以包含任意异步操作
> 3. 封装多个mutation

action函数：

接受一个与store实例有相同方法属性的context对象
如果只需要用到commit方法提交mutation，可以用解构赋值

```js
actions: {
  incrementAsync ({ commit }, { ...}) {
    setTimeout(() => {
      commit('increment')
    }, 1000)
  }
}
export function selectPlay({ commit }, { list, index }) {
  commit('setPlayMode', PLAY_MODE.seqeuence)
  commit('setSequenceList', list)
  commit('setPlayingState', true)
  commit('setFullScreen', true)
  commit('setPlaylist', list)
  commit('setCurrentIndex', index)
}
```

组件中分发action

```vue
<script setup>
	store.dispatch('...', {})
</script>
```

