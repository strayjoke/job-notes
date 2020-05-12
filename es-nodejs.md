## 全栈知识点梳理

### json

- json 可以表示三种类型的值：简单值，对象，数组

- 简单值必须使用双引号

- 对象属性必须加双引号

- 没有末尾的分号


### js中模块化编程的规范

[commonJS, AMD, CMD](https://www.cnblogs.com/chenguangliang/p/5856701.html)

- commonJS 
  NodeJS是CommonJS规范的实践。commonJS主要为了JS在后端的表现制定的，不适合前端。

- AMD 
  AMD（异步模块定义）出现了，主要为前端JS的表现制定规范。
  RequireJS实现了AMD的规范

- CMD seaJS （玉伯）


### js运行机制详解：再谈Event Loop

[http://www.ruanyifeng.com/blog/2014/10/event-loop.html](http://www.ruanyifeng.com/blog/2014/10/event-loop.html)

> 单线程降低了复杂度，单线程意味着，所有任务需要排队，前一个任务结束，才会执行后一个任务。
>
> 任务分为：同步任务， 异步任务。
>
> 同步任务是指在主线程上排队执行的任务，所有同步任务都在主线程上执行，形成一个执行栈；异步任务是指不进入主线程，进入任务队列的任务；
>
> 主线程空闲时，会去任务队列读取事件。有四种会放入异步任务队列：1.setTimeout()和setInterval()2.dom事件3.promise 4.ajax异步请求



### 任务队列： microtask 和 macrotask

- 参考资料：[microtask 和 macrotask](<https://zhuanlan.zhihu.com/p/24460769>)
- [事件循环机制详解与实践应用](<https://juejin.im/post/59afc6adf265da2485360168>)

![marcotask and microtask](C:\Users\matteao_03\Desktop\future\imgs\task-job.jpg)

- 至少需要一个macrotask 队列，和一个 microtask 队列。
- 基于两个原则：1.同一时间只能执行一个任务；2.任务一直执行到完成，不能被其他任务抢断。
- microtask 和 macrotask 的不同之处：在单次循环中，一次最多处理一个 macrotask（其他的仍然驻留在队列中），然而，却可以处理完所有的 microtask。
- 当 microtask 队列为空时，event loop 检查是否要执行 UI 重渲染。



#### 离线应用与客户端存储

- 离线检测	
  1. navigator.onLine  : true 表示设备能上网，false 表示设备离线

1. online和offline 两个HTML5事件

- 数据存储

  `cookie`:在浏览器和服务器间来回传递。4kb 大小

  web 存储机制：以windows对象属性的形式存在。clear(), getItem(), key(index),removeItem(), setItem() , length 。不会自动把数据发给浏览器。 5MB大小



  `sessionStorage` 和 `localStorage`  只保存字符串

  `sessionStorage`:保存到浏览器窗口关闭。

> 1. sessionStorage是页面级别的，仅在一个标签页生效，如果同一个浏览器同时打开多个标签页，且都访问同一个域名，sessionStorage是不会在这多个标签页共用的，即每个标签页都有自己的sessionStorage。
>
> > 1. sessionStorage 在子窗口是共享父窗口的sessionStorage

  `localStorage`:同一域名，同一协议，同一端口

  `storage`事件 ，对Storage对象修改会触发storage事件。

  引申 `会话` 概念：多个http连接间维护用户与同一用户不同请求之间关联的情况，叫做维护一个会话。



#### module 加载

- `<script>` 标签

- ES6 模块

  >ES6 模块是动态引用

- CommonJS 模块

  >CommonJS 输出的是值的复制
  >
  >CommonJS 输出的是一个对象



#### express 和 koa 中间件机制分析

[中间件机制分析（一）](https://juejin.im/post/5c88d4bce51d4504743cf56f)

[中间件机制分析（二）](<https://juejin.im/post/5c9877b06fb9a070e25a706e>)

[为什么放弃express却使用koa](https://juejin.im/post/5b3c9830f265da0f8524c7b2)

- express 是线性模型， koa 是洋葱模型
- express中间件不会等待下一个中间件完成, Koa会等待下一个中间完成, Koa解决了异步问题

