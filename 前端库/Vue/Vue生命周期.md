## 生命周期阶段(函数/钩子)

Vue组件实例 从创建到销毁的过程，会经历一系列初始化步骤：数据侦听，模板编译，挂载实例，数据变化时更新dom，过程中可以运行函数（生命周期钩子函数），因此我们可以在特定的阶段执行自定义函数

参数：接受一个回调函数，在对应的生命周期中执行

1. 创建前后 before create | created
2. 挂载前后 before mount | mounted
3. 更新前后 before update | updated
4. 销毁前后 before unmout | unmounted



| 生命周期 | 钩子              | 参数描述(回调函数)                            | 其他 |
| -------- | ----------------- | --------------------------------------------- | ---- |
| 创建前   |                   |                                               |      |
| 创建后   |                   |                                               |      |
| 挂载前   | onBeforeMount()   | 挂载前调用                                    |      |
| 挂载后   | onMounted()       | 挂载完成后调用                                |      |
| 更新前   | onBeforeUpdate()  | 即将因为响应式状态变更而更新其 DOM 树之前调用 |      |
| 更新后   | onUpdated()       |                                               |      |
| 销毁前   | onBeforeUnmount() | 被卸载之前调用                                |      |
| 销毁后   | onUnmounted()     | 卸载后调用                                    |      |



### Vue3注册周期钩子

钩子应当在组件初始化时被**同步**注册。

```ts
//挂载前后
onBeforeMount(()=>{})
onMounted(()=>{})

//更新前后
onBeforeUpdate(()=>{})
onUpdated(()=>{})

//卸载前后
onBeforeUnMount(()=>{})
onUnMounted(()=>{})
```

所有子组件挂载完成后，父组件才会挂载完成

 ![组件生命周期图示](./images/lifecycle_zh-CN.W0MNXI0C.png)

## hooks



新建文件夹hooks
新建文件useXxx.ts

```ts
import
export default function(){
    //数据
    //方法
    //钩子
    onMounted(()=>{
        
    })
    //向外部提供东西
    return {数据名，方法名}
}
```

```vue
<script>
	const {数据名,方法名} = useXxx()
</script>
```



