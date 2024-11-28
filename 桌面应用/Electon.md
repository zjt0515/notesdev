## 介绍

Chromium + Nodejs + Native API

Web

## Electron流程模型

1. 基于node环境的主进程
2. 多个Render渲染进程（基于浏览器环境）
3. 主进程和渲染进程之间通信：  渲染环境中使用预处理脚本



### 主进程

> 唯一性，入口点，node环境



### 渲染器进程





### 预加载脚本

> 1. 执行与渲染器进程
> 2. 先于网页内容加载
> 3. 通过在全局window中暴露任意API来增强渲染器

使用 [`contextBridge`](https://www.electronjs.org/zh/docs/latest/api/context-bridge) 模块实现安全交互





### 效率进程

效率进程主要用于托管

## 上下文隔/离

qq

## 进程间通信IPC

`contextBridge` API 来选择要从预加载脚本中暴露哪些 API

### 渲染器进程 → 主进程

1. 发送消息：`ipcRenderer.send`
2. 接受消息：`ipcMain.on`

```js
//main
ipcMain.on('file-save', writeFile())
function writeFile(event, data)
loadFile()
//preload
contextBridge.exposeInMainWorld('testAPI',{
  v:,
  saveFile: (file)=>{
  	ipdRenderer.send('file-save', file)
}
})
//renderer
testAPI.saveFile();
```



### 渲染器进程 双向 主进程 

1. 使用 `ipcMain.handle` 监听事件
2. 通过预加载脚本暴露` ipcRenderer.invoke`



```js
//main

//preload

//renderer
```



### 主进程到渲染进程

1. 使用` webContents `模块发送消息

```js
//main

//preload

//renderer
```

