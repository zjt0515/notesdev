## 参数传递

### query params

```js
axios.get('url', {
    params: {
        id: 123
    }
})
```

> @Query

### body params

```js
axios.post('url', {
    id:123
})
```

> @Body() *updateUserDto*: UpdateUserDto

### 路径参数

```js
axios.delete('/url/123')
```

> @Delete(':id')
>
>   remove(@Param('id') *id*: *string*) {
>
> ​    return *this*.userService.remove(+id);
>
>   }

### headers

```
Authorzation: token
```

