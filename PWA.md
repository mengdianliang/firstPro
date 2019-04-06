### 1.介绍：
``` python
一个新的前端技术，PWA（ 全称：Progressive Web App ）也就是说这是个渐进式的网页应用程序。
```
### 2.关键技术：
``` python
(1) Service Worker （可以理解为服务工厂）

SW 是什么呢？这个是离线缓存文件。我们 PWA 技术使用的就是它！SW 是浏览器在后台独立于网页运行的脚本，它打开了通向不需要网页或用户交互的功能的大门，因为使用了它，才会有的那个 Reliable 特性吧，SW 作用于 浏览器于服务器之间，相当于一个代理服务器。
目前只能在 HTTPS 环境下才能使用SW，因为SW 的权利比较大，能够直接截取和返回用户的请求，所以要考虑一下安全性问题。

(2) Manifest （应用清单）

Web App Manifest 是一个 W3C 规范，它定义了一个基于 JSON 的 List 。Manifest 在 PWA 中的作用有：          
. 能够将你浏览的网页添加到你的手机屏幕上
. 在 Android 上能够全屏启动，不显示地址栏 （ 由于 Iphone 手机的浏览器是 Safari ，所以不支持哦）
. 控制屏幕 横屏 / 竖屏 展示
. 定义启动画面                 
. 可以设置你的应用启动是从主屏幕启动还是从 URL 启动              . . 
. 可以设置你添加屏幕上的应用程序图标、名字、图标大

(3) Push Notification（推送通知）

Push 和 Notification 是两个不同的功能，涉及到两个 API 。
. Notification 是浏览器发出的通知消息。
. Push 和 Notification 的关系，Push：服务器端将更新的信息传递给 SW ，Notification： SW将更新的信息推送给用户。
```
### 3.serviceworker详细介绍：
``` python
Service Worker 讲道理是由两部分构成，一部分是 cache，还有一部分则是 Worker。所以，SW（Service Worker） 本身的执行，就完全不会阻碍当前 js 进程的执行，确保性能第一。那 SW 到底是怎么工作的呢？

后台进程: SW 就是一个 worker 独立于当前网页进程。
网络代理: SW 可以用来代理请求，缓存文件
灵活触发: 需要的时候吊起，不需要的时候睡眠（这个是个坑）
异步控制: SW 内部使用 promise 来进行控制。
```
### 3.serviceworker生命周期：
``` python
首先，SW 并不是你网页加载就与生俱来的。如果，你需要使用 SW，你首先需要注册一个 SW，让浏览器为你的网页分配一块内存空间来。并且，你能否注册成功，还需要看你缓存的资源量决定（有可能失败，真的有可能）。如果，你需要缓存的静态资源全部保存成功，那么恭喜您，SW 安装成功。如果，其中有一个资源下载失败并且无法缓存，那么这次吊起就是失败的。不过，SW 是由重试机制的，这点也不算特别坑。
当安装成功之后，此时 SW 就进入了激活阶段（activation）。然后，你可以选择性的检查以前的文件是否过期等。
检查完之后，SW 就进入待机状态。此时，SW 有两种状态，一种是 active，一种是 terminated。就是激活/睡眠。激活是为了工作，睡眠则为了节省内存。这是一开始设计的初衷。如果，SW 已经 OK，那么，你网页的资源都会被 SW 控制，当然，SW 第一次加载除外。
```
### 4.serviceworker生命周期：
``` python
首先，SW 并不是你网页加载就与生俱来的。如果，你需要使用 SW，你首先需要注册一个 SW，让浏览器为你的网页分配一块内存空间来。并且，你能否注册成功，还需要看你缓存的资源量决定（有可能失败，真的有可能）。如果，你需要缓存的静态资源全部保存成功，那么恭喜您，SW 安装成功。如果，其中有一个资源下载失败并且无法缓存，那么这次吊起就是失败的。不过，SW 是由重试机制的，这点也不算特别坑。
当安装成功之后，此时 SW 就进入了激活阶段（activation）。然后，你可以选择性的检查以前的文件是否过期等。
检查完之后，SW 就进入待机状态。此时，SW 有两种状态，一种是 active，一种是 terminated。就是激活/睡眠。激活是为了工作，睡眠则为了节省内存。这是一开始设计的初衷。如果，SW 已经 OK，那么，你网页的资源都会被 SW 控制，当然，SW 第一次加载除外。
```
### 5.Register：
``` python
SW 实际上是挂载到 navigator 下的对象。在使用之前，我们需要先检查一下是否可用：

if ('serviceWorker' in navigator) {
  // ....
}

如果可用，我们就要使用 SW 进行路由的注册缓存文件了。不过，这里有点争议。啥时候开始执行 SW 的注册呢？上面说过，SW 就是一个网络代理，用来捕获你网页的所有 fetch 请求。那么，是不是可以这么写？

window.addEventListener('DOMContentLoaded', function() {
    // 执行注册
    navigator.serviceWorker.register('/sw.js').then(function(registration) {
      
    }).catch(function(err) {
      
    }); 
  });
  
  SW 的作用域不同，监听的 fetch 请求也是不一样的。 例如，我们将注册路由换成: /example/sw.js，那么，SW 后面只会监听 /example 路由下的所有 fetch 请求，而不会去监听其他，比如 /jimmy,/sam 等路径下的。
  
  监听安装 SW ：
  当安装成功后，我们能使用 SW 做什么呢？ 那就开始缓存文件了。
  self.addEventListener('install', function(event) {
  event.waitUntil(
    caches.open('mysite-static-v1').then(function(cache) {
      return cache.addAll([
        '/css/whatever-v3.css',
        '/css/imgs/sprites-v6.png',
        '/css/fonts/whatever-v8.woff',
        '/js/all-min-v4.js'
      ]);
    })
  );
});
```
### 6.不稳定加载：
``` python
如果其中一个文件下载失败的话，那么这次你的 SW 启动就告吹了，即，如果其中有一个 Promise 是使用 reject 的话，那就代表着–您这次启动是 GG 的。那，有没有其他办法在保证一定稳定性的前提下，去加载比较大的文件呢？ 有的，那你别返回 cache.addAll 就ok了。什么个意思呢？ 就这样：

self.addEventListener('install', function(event) {
  event.waitUntil(
    caches.open('mygame-core-v1').then(function(cache) {
    // 不稳定文件或大文件加载
      cache.addAll(
        //...
      );
      // 稳定文件或小文件加载
      return cache.addAll(
        // core assets & levels 1-10
      );
    })
  );
});

```
### 7.缓存捕获：
``` python
该阶段就是事关整个网页能否正常打开的一个阶段–非常关键。在这一阶段，我们将学会，如何让 web 使用缓存，如何做向下兼容。 先看一个简单的格式：

self.addEventListener('fetch', function(event) {
  event.respondWith(
    caches.match(event.request)
      .then(function(response) {
        // Cache hit - return response
        if (response) {
          return response;
        }
        return fetch(event.request);
      }
    )
  );
});

首先看一下，第一个方法–event.respondWith，用来包含响应主页面请求的代码。当接受到 fetch 请求时，会直接返回 event.respondWith Promise 结果。我们在 worker 中，捕获页面所有的 fetch 请求。可以看到 event.request ，这个就是 fetch 的 request 流。我们通过 caches.match 捕获，然后返回 Promise 对象，用来进行响应的处理。

那现在有个问题，如果没有找到缓存，那么应该怎么做呢？

手动添加： 很简单，自己发送 fetch，然后使用 caches 进行缓存即可。不过，这里又涉及到另外一个概念，Request 和 Response 流。这是在 fetch 通信方式 很重要的两个概念。fetch 不仅分装了 ajax，而且在通信方式上也做了进一步的优化，同 node 一样，使用流来进行重用。众所周知，一个流一般只能使用一次，可以理解为喝矿泉水，只能喝一次，不过，如果我知道了该水的配方，那么我就可以量产该水，这就是流的复制。下面代码也基本使用到这两个概念，基本代码为：

self.addEventListener('fetch', function(event) {
  event.respondWith(
    caches.match(event.request)
      .then(function(response) {
        if (response) {
          return response;
        }

        // 因为 event.request 流已经在 caches.match 中使用过一次，
        // 那么该流是不能再次使用的。我们只能得到它的副本，拿去使用。
        var fetchRequest = event.request.clone();

        // fetch 的通过信方式，得到 Request 对象，然后发送请求
        return fetch(fetchRequest).then(
          function(response) {
            // 检查是否成功
            if(!response || response.status !== 200 || response.type !== 'basic') {
              return response;
            }

            // 如果成功，该 response 一是要拿给浏览器渲染，而是要进行缓存。
            // 不过需要记住，由于 caches.put 使用的是文件的响应流，一旦使用，
            // 那么返回的 response 就无法访问造成失败，所以，这里需要复制一份。
            var responseToCache = response.clone();

            caches.open(CACHE_NAME)
              .then(function(cache) {
                cache.put(event.request, responseToCache);
              });

            return response;
          }
        );
      })
    );
});
```
### 8.Update：
``` python
在 SW 中的更新涉及到两块，一个是基本静态资源的更新，还有一个是 SW.js 文件的更新。
(1) SW.js 的更新:
首先更新 SW.js 文件，这是最主要的。只有更新 SW.js 文件之后，之后的流程才能触发。SW.js 的更新也很简单，直接改动 SW.js 文件即可。浏览器会自动检查差异性（就算只有 1B 的差异也行），然后进行获取。
新的 SW.js 文件开始下载，并且 install 事件被触发
此时，旧的 SW 还在工作，新的 SW 进入 waiting 状态。注意，此时并不存在替换
现在，两个 SW 同时存在，不过还是以前的 SW 在掌管当前网页。只有当 old SW 不工作，即，被 terminated 后，新的 SW 才会发生作用。具体行为就是，该网页被关闭一段时间，或者手动的清除 service worker。然后，新的 SW 就度过可 waiting 的状态。
一旦新的 SW 接管，则会触发 activate 事件。

如果上述步骤成功后，原来的 SW.js 就会被清除。但是，以前版本 SW.js 缓存文件没有被删除。针对于这一情况，我们可以在新的 SW.js 里面监听 activate 事件，进行相关资源的删除操作。当然，这里主要使用到的 API 和 caches 有很大的关系（因为，现在所有缓存的资源都在 caches 的控制下了）。比如，我以前的 SW 缓存的版本是 v1，现在是 v2。那么我需要将 v1 给删除掉，则代码为：

self.addEventListener('activate', function(event) {
  var cacheWhitelist = ['v1'];
  event.waitUntil(
  // 遍历 caches 里所有缓存的 keys 值
    caches.keys().then(function(cacheNames) {
      return Promise.all(
        cacheNames.map(function(cacheName) {
          if (cacheWhitelist.includes(cacheName)) {
          // 删除 v1 版本缓存的文件
            return caches.delete(cacheName);
          }
        })
      );
    })
  );
});

不过，sw.js 文件的更新是一个非常坑爹的过程。因为，它的替换是当 older SW 不工作的时候，new SW 才能发生作用。并且，浏览器何时关闭对应的 SW 又是一个未知数。不过，Service Worker 本身就是这么设计的，╮(╯▽╰)╭ (；′⌒`)

(2) skipWaiting:
那有没有什么办法能够让 new SW 立即生效呢？有的，可以在 install 阶段使用 self.skipWaiting(); API。因为上面说到 new SW 加载后会触发 install 然后进入 waiting 状态。那么，我们可以直接在 install 阶段跳过等待，直接让 new SW 进行接管。

self.addEventListener('install', event => {
  self.skipWaiting();

  event.waitUntil(
    // caching etc
  );
});

不过，这样有个弊端是，此时用户正在当前网页中，此时，older SW 会触发 activate 事件，删除相关的资源，这样会造成资源丢失，只能通过网络获取。并且后面的网络请求都会交给 new SW 进行捕获和处理。所以，用不用还得根据具体业务来看。

(3) 手动更新：
上面的 SW 更新都是在一开始加载的时候进行的，那么，如果用户需要长时间停留在你的网页上，有没有什么手段，在间隔时间检查更新呢？

有的，可以使用 registration.update() 来完成。

navigator.serviceWorker.register('/sw.js').then(reg => {
  // sometime later…
  reg.update();
});

另外，如果你一旦用到了 sw.js 并且确定路由之后，请千万不要在更改路径了，因为，浏览器判断 sw.js 是否更新，是根据 sw.js 的路径来的。如果你修改的 sw.js 路径，而以前的 sw.js 还在作用，那么你新的 sw 永远无法工作。除非你手动启用 update 进行更新。
```
### 9.文件更新：
``` python
只需要在这里简单的写下一下 prefetch 代码即可。

self.addEventListener('install', function(event) {
  var now = Date.now();
  // 事先设置好需要进行更新的文件路径
  var urlsToPrefetch = [
    'static/pre_fetched.txt',
    'static/pre_fetched.html',
    'https://www.chromium.org/_/rsrc/1302286216006/config/customLogo.gif'
  ];
  
  event.waitUntil(
    caches.open(CURRENT_CACHES.prefetch).then(function(cache) {
      var cachePromises = urlsToPrefetch.map(function(urlToPrefetch) {
      // 使用 url 对象进行路由拼接
        var url = new URL(urlToPrefetch, location.href);
        url.search += (url.search ? '&' : '?') + 'cache-bust=' + now;
        // 创建 request 对象进行流量的获取
        var request = new Request(url, {mode: 'no-cors'});
        // 手动发送请求，用来进行文件的更新
        return fetch(request).then(function(response) {
          if (response.status >= 400) {
            // 解决请求失败时的情况
            throw new Error('request for ' + urlToPrefetch +
              ' failed with status ' + response.statusText);
          }
          // 将成功后的 response 流，存放在 caches 套件中，完成指定文件的更新。
          return cache.put(urlToPrefetch, response);
        }).catch(function(error) {
          console.error('Not caching ' + urlToPrefetch + ' due to ' + error);
        });
      });

      return Promise.all(cachePromises).then(function() {
        console.log('Pre-fetching complete.');
      });
    }).catch(function(error) {
      console.error('Pre-fetching failed:', error);
    })
  );
});

当成功获取到缓存之后， SW 并不会直接进行替换，他会等到用户下一次刷新页面过后，使用新的缓存文件。
```

### 10.介绍：
``` python
我们简单介绍一下， client 和 service worker 相互通信。首先， service worker 向 client 发送消息很容易。

self.addEventListener('message', function(event){
    console.log("SW Received Message: " + event.data);
    event.ports[0].postMessage("SW Says 'Hello back!'");
});


```
### 11.介绍：
``` python
一个新的前端技术，PWA（ 全称：Progressive Web App ）也就是说这是个渐进式的网页应用程序。
```
### 12.介绍：
``` python
一个新的前端技术，PWA（ 全称：Progressive Web App ）也就是说这是个渐进式的网页应用程序。
```