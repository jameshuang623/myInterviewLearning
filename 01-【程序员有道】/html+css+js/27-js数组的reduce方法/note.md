# js 数组的 reduce 方法
```js
arr.reduce(function (prev, cur, index, arr) {
    ...
}, init)

// 或者

arr.reduce(function (prev, cur, index, arr) {
    ...
},)
```

- arr 表示原数组；
- prev 表示上一次调用回调时的返回值，或者初始值 init；
- cur 表示当前正在处理的数组元素；
- index 表示当前正在处理的数组元素的索引，若提供 init 值，则索引为0，否则索引为1；
- init 表示初始值。

常用的参数只有两个：prev 和 cur

- 数组求和，求乘积
