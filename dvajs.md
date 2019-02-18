### 1. dvajs链接
``` python
https://dvajs.com/guide/getting-started.html#安装-dva-cli
```
### 1. dva-loading的使用
``` python
(1)之前对 dva-loading 理解存在误区，认为只要在 index.js 中配置一下就没事了，事实上 dva-loading 只是提供当前异步加载方法的状态（异步加载中状态为 true，异步加载完成状态为 false），对应加载样式由各自组件自己控制，如：Antd 中 Table 组件自身的 loading 属性。并添加完整流程示例代码。
(2)作用：
该组件仅仅监听异步加载状态，这从它的调用方式就可以看出来 const isLoading = loading.effects['user/query']，其中 user/query 是 model 中的异步请求方法。
loading 在异步请求发出那一刻会持续监听该异步请求方法的状态，在异步请求结束之前 isLoading 的值一直是 true，当此次异步请求结束时 isLoading 的值变成 false，同时 loading 对象停止监听。
(3)配置：

dva 项目的 index.js 文件：
import createLoading from 'dva-loading';
const app = dva();
app.use(createLoading());

配置完成后，在任何一个 dva 的 routes 组件中就都会有一个 loading 对象，如果你对 dva 稍有了解的话，应该不难知道它在哪。比如下面这行代码中的 loading 对象就是由于上面的配置。

export default connect(({ app, loading }) => ({ app, loading }))(App);

打印一下 loading 对象，可看到内容如下：
loading: {
  global: false,
  models: {app: false},
  effects: {app: false}
}

loading 有三个方法，其中 loading.effects['user/query'] 为监听单一异步请求状态，当页面处于异步加载状态时该值为 true，当页面加载完成时，自动监听该值为 false。

如果同时发出若干个异步请求，需求是当所有异步请求都响应才做下一步操作，可以使用 loading.global() 方法，该方法监听所有异步请求的状态。
(4)怎么用？
使用 Antd 的 Table 组件 时，查阅 API 可以看到有个 loading 的属性。如果该属性值为 true，Table 组件自身会显示加载效果，该值为 false，加载效果消失。可以通过 loading 对象判断当前是否有异步加载。具体示例代码如下：


```
