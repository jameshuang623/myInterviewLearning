# js的运行机制
js离不开用户的操作  
是单线程，同一时间做同一件事情  
学习文章：[这一次，彻底弄懂 JavaScript 执行机制](https://juejin.cn/post/6844903512845860872#heading-8)

# arguments 对象是什么？
```js
function get(){
    console.log(arguments)
}

get(1,2,3)
Array.prototype.slice.call(arguments)
// 在 ES5 中将类数组转化成数组的方法
```
是类数组对象（有length属性但没有数组的方法）
- 箭头函数是没有 arguments 对象的

# 为什么在调用这个函数时，代码中的`b`会变成一个全局变量
```js
function fun(){
    let a = b = 0
    // 等价于
    // let a = (b = 0)
    // 把 0 赋值给 b 时没有 b
    // 则 js 引擎和创建一个 b
    // 由于 b 没有被声明
    // 所以 b 会变成一个全局变量
}
```

# 哪些操作会造成内存泄露？
- 闭包
- 意外的全局变量
- 被遗忘的定时器
- 脱离 dom 的引用

# 什么是高阶函数
- 将函数作为参数或者返回值的函数
```js
function highOrder(params, callBack){
    
    return callBack(params)
}

let fn = function(){}
// 将函数作为变量
```

# 手动实现`Array.prototype.map`方法

