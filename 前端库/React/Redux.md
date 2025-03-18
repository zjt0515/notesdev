## Redux

全局状态管理工具https://redux.js.org/

```react
npm install @reduxjs/toolkit react-redux
```

- redux可以单独运行

## 核心概念

1. Store 状态来源 Single Source of Truth
2. reducer 修改状态



## 使用过程

### 定义state

```react
// 初始状态
const initialState = {
  selectedLang: "en"
}

/**
 * 调用createSlice
 * name唯一，(发送action时加入name前缀)
 * 设置初始状态
 */
export const settingsSlice = createSlice({
  name: "settings",
  initialState,
  reducers: {
    // 只能访问修改本slice定义的状态
    // 参数1用于访问自身state，参数2用于传入的参数
    setLang: (state, action) => {
      // 访问当前属性并修改为action.payload (immer库自动包装)
      state.selectedLang = action.payload
    }
  }
})

export const { setLang } = settingsSlice.actions;
export default settingsSlice.reducer;
```

### 访问state

```react
// state状态
  const lang = useSelector(state => state.settings.selectedLang)
```

### 修改state

```react
const dispatch = useDispatch();
dispatch(setLang(new))
```

