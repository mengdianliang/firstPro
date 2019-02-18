### 1. es6 set去重
``` python
Array.from()方法就是将一个类数组对象或者可遍历对象转换成一个真正的数组。
var set1 = Array.from(new Set([1,1,2,2,33,'33',44,'44'
]))
// [1,2,33,'33',44,'44'];
```
### 2. es6 reduce()
``` python

reduce中回调函数的参数，函数有4个参数，意思分别是：
prev: 第一项的值或者上一次叠加的结果值
cur: 当前会参与叠加的项
index: 当前值的索引
arr: 数组本身


function formatNumber(str) {
// ["0", "9", "8", "7", "6", "5", "4", "3", "2", "1"]
    return str.split("").reverse().reduce((prev, next, index) => {
        console.log(prev, next)
        return ((index % 3) ? next : (next + ',')) + prev
    })
}

console.log(formatNumber("1234567890")) // 1,234,567,890
```
### 3. es6 set去重
``` python
Array.from()方法就是将一个类数组对象或者可遍历对象转换成一个真正的数组。
var set1 = Array.from(new Set([1,1,2,2,33,'33',44,'44'
]))
// [1,2,33,'33',44,'44'];
```