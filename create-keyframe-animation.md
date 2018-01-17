###   使用JavaScript在浏览器中动态生成CSS关键帧动画
``` python
    github地址：https://github.com/HenrikJoreteg/create-keyframe-animation
```
###   install
``` python
    npm install create-keyframe-animation
```
###   引入动画
``` python
    import animations from 'create-keyframe-animation'
```
###   vue使用该动画
``` python
    enter(el, done) {
    // 设置动画帧数
    let animation = {
            0: {
              transform: `translate3d(${x}px, ${y}px, 0) scale(${scale})`
            },
            60: {
              transform: 'translate3d(0, 0, 0) scale(1.2)'
            },
            100: {
              transform: 'translate3d(0, 0, 0) scale(1)'
            }
          }

    // 注册动画
    animations.registerAnimation({
      name: 'move',
      // 插入自定义的动画
      animation,
      // 参数配置
      presets: {
        duration: 1000, // 持续时间
        easing: 'linear', // 过度效果
        delay: 500 // 延迟时间
        terations: 1, // 实现动画的次数
    　　　delay: 0, // 延迟 
    　　　direction: ‘normal‘, // 方向
    　　　resetWhenDone: false, // if true ：将最后动画状态应用为“变换”属性
    　　　　clearTransformsBeforeStart: false // 是否在动画开始之前清除现有的转换
      }
    })

    animations.runAnimation(el, 'move', function () {
        // callback gets called when its done
    })
},
afterEnter() {
    // 取消动画
   animations.unregisterAnimation('move')
    this.$refs.cdWrapper.style.animation = ''
    }
```