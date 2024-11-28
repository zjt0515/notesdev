# 计划

## 前端页面开发

1. 用户注册页面
2. 创建题目页面
3. 题目管理页面
4. 题目列表页面
5. 做题页面
6. 题目提交列表页面
7. 个人主页
8. 提交统计页面

## 工程化配置

vscode 中安装插件

- vue-official
- IntelliJ IDEA Keybindings

eslint?



配置@，`npm install @types/node -D`

```json
//tsconfig.json
{
  "compilerOptions": {
    //add
    "baseUrl": ".",
    "paths": {
      "@/*":["src/*"]
    },

    /* Bundler mode */
    //change
    "moduleResolution": "node",
```

```ts
resolve: {
    alias: {
      "@": path.resolve(__dirname, "src"),
    },
  },
```

不会好像。。

### 新建布局文件夹layouts

新建文件`BasicLayout.vue`

app.vue中引入基本布局

最外层div

使用布局组件示例代码，一般是header content footer

为每个部分添加样式，使用颜色能够清晰观察结构

### 页面布局

导航栏
中间内容
底栏



### 引入icon

记得美化样式，先在浏览器中调试

## 开发导航栏组件

提取通用路由文件

菜单组件读取路由，动态渲染菜单

1. routes中有什么name就渲染什么
2. routes中如果有隐藏标志就不渲染什么，用过滤，还可以设置根据权限过滤显示菜单

跳转路由

bug1：选中一个菜单项目，刷新后高亮消失

```ts
const router = useRouter()
// 监听路由变化，响应式渲染
const activeIndex = ref('/')
router.afterEach((to, from, faliure) => {
  activeIndex.value = to.path
})
```





## 全局状态管理

所有页面全局共享的变量

### 定义用户信息，并实现登录修改信息

展示用户信息

### 权限管理

路由中使用元数据定义权限等级

使用路由守卫控制路由权限

## 菜单组件开发



## 全局权限管理

1. 构建权限枚举值
2. 公用权限校验方法
3. 利用计算属性 动态计算过滤菜单

## 整合Md编辑器

https://github.com/bytedance/bytemd

安装
引入css

新建MdEdit.vue一般组件
定义响应式数据，用于保存输入的值

定义组件props，让父级来控制组件内部状态

### 使用父组件操作子组件，给子组件传值方式

withdefaluts：

定义属性类型`defineProps<Props>()`

```vue
//父组件
<template>
    <MdEdit :value="value" :handleChange="onChange" />
</template>
<script setup lang="ts" name="GameView">
import { ref } from 'vue'
import MdEdit from '../components/MdEdit.vue'
const value = ref('')
const onChange = (v: string) => {
  value.value = v;
}
</script>
```

```vue
//子组件
<script setup lang="ts" name="MdEdit">
import gfm from '@bytemd/plugin-gfm'
import highlight from '@bytemd/plugin-highlight'
import { Editor, Viewer } from '@bytemd/vue-next'
import 'bytemd/dist/index.css'
import { ref } from 'vue';

interface Props {
  value: string;
  handleChange: (v: string) => void
}
const props = withDefaults(defineProps < Props > (), {
  value: () => '',
  handleChange: () => { },
})
const plugins = [
  gfm(),
  highlight()
  // Add more plugins here
]
</script>
```

## 整合代码编辑器

https://github.com/microsoft/monaco-editor

https://github.com/microsoft/monaco-editor/blob/main/docs/integrate-esm.md#using-vite

monaco editor的坑：
读写值时，要使用toRaw(编辑器示例)的语法来执行操作，否则会卡死1





## 页面开发

### 创建题目页面

### 题目管理页面

### 在线做题页面

## 判题机页面

​	
