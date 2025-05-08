# Vue内置组件

## transition

进入/离开的触发条件：

- 由 `v-if` 所触发的切换
- 由 `v-show` 所触发的切换
- 由特殊元素 `<component>` 切换的动态组件
- 改变特殊的 `key` 属性

```vue
<template>
	<Transition name="fade"></Transition>
</template>
<style>
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.5s ease;
  }

  .fade-enter-from,
  .fade-leave-to {
    opacity: 0;
  }
</style>
```

css样式移除时机：animationend事件触发后

动态的过渡效果，即name属性也可以是响应式的

```vue
<Transition :name="transitionName">
  <!-- ... -->
</Transition>
```



### transition的子元素



> [!warning]
>
> 过渡 class 仅能应用在 `<Transition>` 的直接子元素上

元素间过渡：任意时刻内部只有一个元素被渲染

```vue
<Transition>
  <button v-if="docState === 'saved'">Edit</button>
  <button v-else-if="docState === 'edited'">Save</button>
  <button v-else-if="docState === 'editing'">Cancel</button>
</Transition>
```

组件间过渡，同理

```vue
<Transition name="fade" mode="out-in">
  <component :is="activeComponent"></component>
</Transition>
```



### props传递css

配合第三方css动画库使用

```vue
<Transition
  name="custom-classes"
  enter-active-class="animate__animated animate__tada"
  leave-active-class="animate__animated animate__bounceOutRight"
>
  <p v-if="show">hello</p>
</Transition>
```

### js钩子

### 二次封装transition

实现可复用的过渡效果组件

```vue
<!-- MyTransition.vue -->
<script>
// JavaScript 钩子逻辑...
</script>

<template>
  <!-- 包装内置的 Transition 组件 -->
  <Transition
    name="my-transition"
    @enter="onEnter"
    @leave="onLeave">
    <slot></slot> <!-- 向内传递插槽内容 -->
  </Transition>
</template>

<style>
/*
  必要的 CSS...
  注意：避免在这里使用 <style scoped>
  因为那不会应用到插槽内容上
*/
</style>
```

```vue
<MyTransition>
  <div v-if="show">Hello</div>
</MyTransition>
```

