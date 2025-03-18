## 状态



```react
function App(){
  // 定义状态
  const { count, setCount } = useState(0);
  <button onClick={ setCount(count + 1) }></button>
}
```

## 更新数组类型

不能直接修改源数组，需要修改原数组的副本，然后用副本代替原数组

```react
function App() {
	const [list, setList]	 = useState([1,2,3])
  function handleAdd(){
  	setList([...list, ])  
  }
  function handleEdit(index){
    const newList = [...list];
    newList[index] += 1;
    setList(newList);
  }
  function handleDelete(index){
    const newList = [...List];
    newList.splice(index, 1);
    setList(newList);
  }
}
```

## 更新对象类型

```react
function App(){
  const [person setPerson] = useState({})
  
  function handleAdd(){
    setPerson({
      ...Person,
      gender: '男'
    })
  }
  function handleEdit(){
    setPerson({
      ...Person,
      gender: '女'
    })
  }
  function handleDelete(){
    const newPerson = {...person};
    delete newPerson.age;
    setPerson(newPerson);
    const {age, ...newPerson} = person;
    setPerson(newPerson);
  }
}
```

## 组件之间共享state

1. 将state抽离出来，分别传入各自组件



## state原理

### 状态更新是异步

e.target.value可以访问最新值

向更新状态函数传入一个函数，可以准确获取上一次的值

```react
function handleNoteInput(e) {
  // 准确获取上一次的值
  setNote((preValue) => {
    console.log(preValue);
    return e.target.value;
  });
}
```

> [!note]
>
> 严格模式下更新状态函数会运行2次

## useReducer

