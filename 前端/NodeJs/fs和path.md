使用node 执行js文件`node .\文件名`

## fs模块file system

```js
import fs from 'fs'//const fs = require('fs')
```

import是异步，require是同步

### 写入

需要持久化保存数据时，需要用到文件写入

```js
// 异步写入，效率更高
fs.writeFile('./文件.md','写入内容', err => {
  if(err){
    console.log('写入失败');
    return;
  }
})
// 同步写入，更容易理解
fs.writeFileSync()
```



追加写入

```js
fs.appendFile('文件路径','\r\n写入内容',err => {
  if(err){
    console.log('写入失败')
    return;
  }
})
// 同步追加写入
fs.appendFileSync()
// writeFile也能实现追加写入
fs.writeFile(,,{flag:'a'},err)
```



流式写入
适合多次写入和大文件写入场景

```js
const ws = fs.createWriteStream('文件路径')
ws.write('\r\n')
ws.write('')
ws.close()//关闭写入
```

###  读取

```js
// 异步读取
fs.readFile('./xxx',(err,data) =>{
  if(err){
    console.log('失败')
    return;
  }
  console.log(data.toString())
})
// 同步读取
let data = fs.readFileSync('./xxx')
console.log(data.toString())
```

### 文件夹操作

```js
// 创建文件夹
fs.mkdir('./path', err =>{})
fs.mkdir('./path/a/b/c', {recursive: true} err =>{})
// 文件夹读取，读取文件夹内部的文件夹或文件
fs.readdir('../xxx', (err,data)=>{})
// 删除文件夹，只能删除空文件夹
fs.rmdir('', err =>{})
```



## path模块

> \_\_dirname是全局变量，保存所在文件夹路径
> \_\_filename是保存文件的路径

```js
//拼接规范的绝对路径
path.resolve(__dirname, 'xxx') //__dirname是全局变量，保存所在文件夹路径
// 获取路径所在文件夹的名称
path.dirname('')
//获取文件名
path.basename('')
//获取路径的拓展名
path.extname('')
```



其他

```js
// 获取操作系统的分隔符，windows:\，linux:/
path.sep
// 解析路径并返回对象
path.parse('')
{
  root: 'D:\\',
  dir: '',
  base: '',
  ext: '',
  name: ''
}
```

## Path

- https://nodejs.cn/api/path.html#pathbasenamepath-suffix

| 方法名                             | 作用                             | 返回值        |
| ---------------------------------- | -------------------------------- | ------------- |
| `path.basename('/xxx/quux.html');` | 返回path的最后一部分             | `'quux.html'` |
| ``path.dirname('/xxx/quux.html')`` | 返回path的目录名                 | `'/xxx'`      |
| `path.extname(path)`               | 返回path的拓展名                 | `'.md'`       |
| `path.format()`                    | 传入对象返回path字符串           |               |
| ``path.isAbsolute(path)``          | 判断是否为绝对路径               |               |
| `path.join('/dir', 'filename')`    | 规范化生成路径                   | `/dir/file`   |
| `path.normalize(path)`             | 规范化path                       |               |
| ``path.parse(path)``               | 从path字符串到对象               |               |
| `path.resolve(path1, path2)`       | 将多个路径片段解析为一个绝对路径 |               |

```js
const pathObject = {
  root: '/',
  dir: '/home/user/dir',
  base: 'file.txt',
  name: 'file',
  ext: '.txt',
  } 
}
```



## FS

| 方法名                        | 作用         | 返回值 |
| ----------------------------- | ------------ | ------ |
| ``.readdir(path[, options])`` | 读取目录内容 |        |
|                               |              |        |
|                               |              |        |

