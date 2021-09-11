代码分析过程：
1. 点击 loginBtn 按钮时，调用 create() 函数
2. 调用 create() 函数也就是调用 getSingle() 函数
3. getSingle() 函数中传入的参数为 createLogin 函数(形参为 fn)，返回的是
```js
function (){
    return result || (result = fn.apply(this, arguments))
}
```
即1中调用 create() 函数，也就是最终在3中调用上述函数

<hr>
闭包分析：

getSingle() 把回调函数createLogin传入到里面来，它会返回一个函数，保存到create变量里面（所以调用 create() 函数，也就是调用

```js
function (){
    return result || (result = fn.apply(this, arguments))
}
```
）

所以这一步

```js
let create = getSingle(createLogin)
```
就满足了闭包中【内部的函数被保存到了外部】  
所以以后在调用 create() 的时候，result 变量并没有被销毁会一直保存在内存当中  
第一次调用时，result 变量为 undefined
```js
return result || (result = fn.apply(this, arguments))
```
如果 result 为 undefined 则走后面的逻辑，result 获得 createLogin 函数中的返回值  
后面调用时，result 为上一次 result = fn.apply(this, arguments) 的值，则其他按钮调用时也能获得该值（组件的思想）