# Day1

`npx create-react-app react-basic`

`npm create vite@latest`

`npm start`



https://react.dev/

## 配置环境

1. 下载软件
2. vscode插件、设置、代码片段



## 在单html页面中使用react

react-dom：渲染层，将组件渲染到Dom中

## 杂谈

> 过去的网页构建
>
> Server-Side-Rendering
>
> Client-Side-Rendering
>
> 显示正确的数据并确保其在一段时间内保持正确
>
> SINGLE-PAGE APPLICATION WITH VANILLA JS不能有效地处理海量数据：
>
> 1. 代码会非常复杂
> 2. 简单文本和数字通常直接存储在Dom中，Dom状态会被经常访问和修改，更难以理解，更容易出错
>
> 根本原因：让用户界面和数据保持同步很难，工作量大 
>
> 框架优点：规范了编写代码地正确方式和结构



## 基础入门



### Vite or create-react-app?

Vite may better for real world!

![image-20240920201300847](./images/image-20240920201300847.png)



### 项目结构

- node_modules 软件包
- public 静态文件
- src 源文件
- package-lock
- package.json
    - 项目名称版本依赖
    - 命令 


> 在js中使用xml语法，通过BABEL将JSX转化成js写法

通过{}识别 js 中的表达式（变量函数方法调用)

- 引号传递字符串
- js变量
- 函数调用和方法调用
- 使用js对象

### 组件

组件就是一个函数，返回jsx

>  组件名命名：驼峰
>
> 函数式组件只能返回一个根节点

```jsx
export default () => {
  return (
    <View className="indexPage">
    </View>
  );
};
```



### State

状态是react最基本的概念，需要改变界面内容->改变状态

useState：返回一个数组，重构后，第一个位置是状态值，第二个是setter函数，用于更新状态

```jsx
// 传入什么类型的数据，state就是什么类型的
const [state, setState] = useState("");
```



###  useEffect

 开始执行的函数+依赖关系数组



### props

## useState

数据驱动视图， 状态变量变化，视图跟着变化

```react
  const [count, setCount] = useState(0)
  const handleClickButton = () => {
    //用传入的新值修改count，并重新使用新的count渲染UI
    setCount(count + 1)
  }
  return (
    <div>
      <button onClick={handleClickButton}>{count}</button>
    </div>
  )
```

## 基础样式分离

行内样式或者抽离成`const style`不推荐

class类名控制

```react
<div>
        <span className='foo'>this is class </span>
</div>
```
