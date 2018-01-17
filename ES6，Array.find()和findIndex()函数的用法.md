### 1.概念

```python
find()函数用来查找目标元素，找到就返回该元素，找不到返回undefined。
    [1, 2, 3, 4].find((value, index, arr) => {
  
})
查找函数有三个参数:
    value：每一次迭代查找的数组元素。
    index：每一次迭代查找的数组元素索引。
    arr：被查找的数组。



findIndex()函数也是查找目标元素，找到就返回元素的位置，找不到就返回-1。
```
### 2.查找元素，返回找到的值，找不到返回undefined。
```python
   const arr1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
var ret1 = arr1.find((value, index, arr) => {
  return value > 4
})

var ret2 = arr1.find((value, index, arr) => {
  return value > 14
})
console.log('%s', ret1)  // 5
console.log('%s', ret2)  // undefine
```
### 3.查找元素，返回找到的index，找不到返回-1。
```python
   var ret3 = arr1.findIndex((value, index, arr) => {
  return value > 4
})

var ret4 = arr1.findIndex((value, index, arr) => {
  return value > 14
})
console.log('%s', ret3)  // 4
console.log('%s', ret4)  // -1
```
### 4.查找NaN。
```python
   const arr2 = [1, 2, NaN, 4, 5, 6, 7, 8, 9, 10, 11]
var ret5 = arr2.find((value, index, arr) => {
  return Object.is(NaN, value)
})

var ret6 = arr2.findIndex((value, index, arr) => {
  return Object.is(NaN, value)
})
console.log('%s', ret5)  // NaN
console.log('%s', ret6)  // 2
```