### 1.HTML 和静态资源：
``` python
public/index.html 文件是一个会被 html-webpack-plugin 处理的模板。在构建过程中，资源链接会被自动注入。
```
### 2.插值：
``` python
因为 index 文件被用作模板，所以你可以使用 lodash template 语法插入内容。

<%= VALUE %> 用来做不转义插值；
<%- VALUE %> 用来做 HTML 转义插值；
<% expression %> 用来描述 JavaScript 流程控制。
```
### 3. Preload：
``` python
<link rel="preload"> 是一种 resource hint，用来指定页面加载后很快会被用到的资源，所以在页面加载的过程中，我们希望在浏览器开始主体渲染之前尽早 preload。
```
### 4. Prefetch：
``` python
<link rel="prefetch"> 是一种 resource hint，用来告诉浏览器在页面加载完成后，利用空闲时间提前获取用户未来可能会访问的内容。
```
### 5. Preload：
``` python
<link rel="preload"> 是一种 resource hint，用来指定页面加载后很快会被用到的资源，所以在页面加载的过程中，我们希望在浏览器开始主体渲染之前尽早 preload。
```