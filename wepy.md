### 1.自定义事件：
``` python
1.4.8新增
可以通过使用.user修饰符为自定义组件绑定事件，如：@customEvent.user="myFn"
其中，@表示事件修饰符，customEvent 表示事件名称，.user表示事件后缀。
目前总共有三种事件后缀：
.default: 绑定小程序冒泡型事件，如bindtap，.default后缀可省略不写；
.stop: 绑定小程序捕获型事件，如catchtap；
.user: 绑定用户自定义组件事件，通过$emit触发。注意，如果用了自定义事件，则events中对应的监听函数不会再执行。
```
### 2.vscode 使用iView时标签报错 Parsing error:
``` python
 x-invalid-end-tag
https://blog.csdn.net/jiaqingge/article/details/80498536
```
### 3. js中3e3相当于3000毫秒
``` python 

```
### 4. :属性.sync相当于动态传递父组件的属性值
``` python

```
### 5. 微信小程序框架 wepy 具体在什么地方要用this.$apply()？
``` python
在你为data里面的数据进行绑定的时候，是需要的。
比如data里面你定义了一个x=''，然后你在自定义的方法里面用this.x=200 之后，需要用this.$apply()来进行数据绑定。这样你在view中绑定data中的x变量时，才会有200，不然就是空
不过有个前提，method里面的方法是不用这个的，但methods里面只能放bindtap这类方法，所以你自己定义的其他方法，或者写在onshow里面，就必须得用this.$apply()。
```
### 6. wepy 条件
``` python
wx:if wx:elif wx:else
```
### 7.阿拉丁：
``` python
https://www.aldwx.com/?source=baidu_pc&plan=tongji&creative=XCXTJPTXG&keyword=XCXTJPTXG031
```
### 8.wepy里边的订阅发布插件pubsub-js
``` python

```
### 9.wepy最常见的问题：
``` python
 （1)时而200，时而500，最可能是调用接口顺序的问题，最难处理的问题
```
### 10.wepy的canvas动画：
``` python
（1)画圆形的话，可以用CanvasContext.clip()
支持版本 >= 1.6.0
从原始画布中剪切任意形状和尺寸。一旦剪切了某个区域，则所有之后的绘图都会被限制在被剪切的区域内（不能访问画布上的其他区域）。可以在使用 clip 方法前通过使用 save 方法对当前画布区域进行保存，并在以后的任意时间通过restore方法对其进行恢复。
const ctx = wx.createCanvasContext('myCanvas')

wx.downloadFile({
  url: 'http://is5.mzstatic.com/image/thumb/Purple128/v4/75/3b/90/753b907c-b7fb-5877-215a-759bd73691a4/source/50x50bb.jpg',
  success: function(res) {
    ctx.save()
    ctx.beginPath()
    ctx.arc(50, 50, 25, 0, 2*Math.PI)
    ctx.clip()
    ctx.drawImage(res.tempFilePath, 25, 25)
    ctx.restore()
    ctx.draw()
  }
})
```
### 11.wepy的swiper
``` python
(1) 如果不是变量，尽量别用{{}}
vertical="{{true}}" circular="{{true}}"    错误
vertical="true" circular="true" 正确
```
### 12.wepy父子组件传递 
``` python
(1) 值得传递：
只能一级一级的传
(2) emit事件传递
可以直接传到祖先级
```
### 13.wepy经验体验
``` python
(1) 最难处理的问题：由于异步原因，导致接口调用顺序问题
```
### 14.h5向小程序传递参数
``` python
(1) 只有在小程序回退，组件销毁，分享的时候才会执行
```