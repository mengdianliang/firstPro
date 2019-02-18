### 1. 先说一下async的用法，它作为一个关键字放到函数前面，用于表示函数是一个异步函数，因为async就是异步的意思， 异步函数也就意味着该函数的执行不会阻塞后面代码的执行。 写一个async 函数
``` python
async function timeout() {
　　return 'hello world';
}
```
### 2. 语法很简单，就是在函数前面加上async 关键字，来表示它是异步的，那怎么调用呢？async 函数也是函数，平时我们怎么使用函数就怎么使用它，直接加括号调用就可以了，为了表示它没有阻塞它后面代码的执行，我们在async 函数调用之后加一句console.log;
``` python
async function timeout() {
    return 'hello world'
}
timeout(); // 2
console.log('虽然在后面，但是我先执行');  // 1
```
### 3.原来async 函数返回的是一个promise 对象，如果要获取到promise 返回值，我们应该用then 方法， 继续修改代码
``` python
async function timeout() {
    return 'hello world'
}
timeout().then(result => {
    console.log(result);
})
console.log('虽然在后面，但是我先执行');
```
### 4.原来async 函数返回的是一个promise 对象，如果要获取到promise 返回值，我们应该用then 方法， 继续修改代码
``` python
async function timeout() {
    return 'hello world'
}
timeout().then(result => {
    console.log(result);
})
console.log('虽然在后面，但是我先执行');
```
### 5.async 和 await,await离不开async，适当时候需要await去阻塞代码执行
``` python
async function timeout() {
    return 'hello world'
}
例如以下：
await timeout().then(result => {
    console.log(result);
})
console.log('虽然在后面，但是我先执行');
```