### 1. koa2概念：
``` python
koa是基于nodejs平台的下一代web开发框架
(1) express原班人马打造，更精简;
(2) Async + await处理异步;
(3) 洋葱圈型的中间件机制
```
### 2. 疑问：
``` python
const Koa = require('koa');
const app = new Koa();

app.use(async(ctx,next) =>{
  ctx.body = 'hello koa';
});
app.listen(3000);

(1) ctx封装了request和response的上下文;
(2)next是下一个中间件；
(3)App是启动应用
```