## Proxy

代理一个对象，得到一个代理对象，拥有被代理对象的所有属性

修改属性时，应该对代理对象的属性修改，进而触发代理对象定义的handler中的getter和setter，

```js
let product = {
  price: 10,
  quantity: 2
}

let total = 0

let effect = () => {
  total = proxyProduct.price * proxyProduct.quantity
}

const proxyProduct = new Proxy(product, {
  set(target, key, newVal, receiver) {
    // console.log('setter')
    target[key] = newVal
    effect()

    return true
  },
  get(target, key, receiver) {
    // console.log('getter')
    return target[key]
  }
})
// 通过代理对象触发
proxyProduct.price
proxyProduct.price = 20

console.log(total)
```

## Reflect

拦截js操作的方法