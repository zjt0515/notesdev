## 组件缓存keep-alive

> 场景：频繁切换，但不需要重复渲染，组件如果多次创建/销毁浪费资源

```vue
<keep-alive>
	<KeepAliveA v-if="statge === 'A'"></KeepAliveA>
  <KeepAliveB v-if="statge === 'B'"></KeepAliveB>
  <KeepAliveC v-if="statge === 'C'"></KeepAliveC>
</keep-alive>
```

## computed

当多次（>1）取到响应式变量时，应该使用本地变量缓存，防止重复发生依赖收集
