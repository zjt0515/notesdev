## Promise构造函数

```
var Promise: PromiseConstructor
new <unknown>(executor: (resolve: (value: unknown) => void, reject: (reason?: any) => void) => void) => Promise<unknown>
Creates a new Promise.

@param executor
A callback used to initialize the promise. This callback is passed two arguments: a resolve callback used to resolve the promise with a value or the result of another promise, and a reject callback used to reject the promise with a provided reason or error.

Promise(executor: (resolve: (value: unknown) => void, reject: (reason?: any) => void) => void): Promise<unknown>
```

