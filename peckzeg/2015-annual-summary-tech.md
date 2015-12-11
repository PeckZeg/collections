2015 总结 - 撸码篇
==================

> 以铜为镜，可以正衣冠；以古为镜，可以知兴替；以人为镜，可以明得失。

## 序

在今年的旅程中，系统的学习了 Node，对~~回调地狱~~异步编程有了深刻的理解。Node 是一个很有潜力的运行环境。这货的底层是使用 C++ 编写的，基于这点，在 11 月份开始了 C++ 的学习之旅。毕竟 JavaScript 还不能直接编译成二进制文件，不能达到真正的高效率执行。

在工作的期间，又点亮了 MongoDB 数据库的技能，MongoDB 是一个基于分布式文件存储的数据库，这底层吗，也是使用 C++ 写的（玛德，这更让我对学习 C++ 的必要性又提高了一个级别）。MongoDB 提供了一个类似于 JSON 的文件格式，名曰 BSON，它是一种对于 JSON 的二进制映射，因为 BSON 的存在让 MongoDB 加速了查询指令，像普通的计数，对于数十万条的数据 `count` 操作只需要数毫秒就能返回结果。

## NodeJS & JavaScript

在过去 2 年中，对 NodeJS 的学习越发的加深，先后尝试了子线程 `child_process`、控制流 `async/await`、流 `stream` 等 NodeJS 的概念和库。深感 NodeJS 坑还是蛮深的。对这些坑的第三方填埋，比如 `async`、`co`、`Q` 等填埋库也有了比较深刻的理解。

在 JavaScript 脚本方面，对 `RequireJS` 进行了系统的学习，对 `r.js` 工具的构建也进行了初步的理解，不过最后还是喜欢使用 `Grunt` 进行构建（因为个人的文件构建结构和 `r.js` 所要求的相差甚远，不好直接使用工具进行构建）。为了弥补源生 JavaScript 的不足，又学习使用了 `moment`、`lodash` / `underscore`、`jquery` / `zepto` 等~~内裤~~类库或框架。在 MV* 的框架方面，对 `backbone` 的喜爱超过了 `aunglarjs` 。

说了一堆毫无逻辑的话之后，稍作整理，将今年所新学习和又有新心得的工具集稍作整理，以备往后查询。

### Resource

* [`Moment`][moment] JavaScript 日期处理类库
* [`Underscore`][underscore] 一个 JavaScript 实用库
* [`Lodash`][lodash] 推荐使用的 JavaScript 实用库，该库的执行效率比 `underscore` 快上数倍
* [`jQuery`][jquery] 优秀的 JavaScript 类库
* ['Zepto'][zepto] 为移动端设计的轻量级 `jQuery` 的类库
* ['Backbone'][backbone] 强大的 MVC 框架，知乎上有人评价，如果说 `AunglarJS` 是没有明显 bug，那么 `Backbone` 则是明显没有 bug
* [`RequireJS`][requirejs] 十分给力的模块加载器
* [`Async`][async] 为 NodeJS 设计的流程控制库，当然，在浏览器端也能很好的使用
* [`Co`][co] 大神 `jongleberry` 撰写的关于 ES6 `async/await` 的 ES6 实现版本
* [`thunkify`][thunkify] Generator 的包装器
* [`Q`][q] 轻量级的 Promise

## CSS & Less & Sass/Scss





[moment]: http://momentjs.com/
[underscore]: http://underscorejs.org/
[lodash]: https://lodash.com/
[jquery]: http://jquery.com/
[zepto]: http://zeptojs.com/
[backbone]: http://backbonejs.org/
[requirejs]: http://requirejs.org/
[async]: https://github.com/caolan/async
[thunkify]: https://www.npmjs.com/package/thunkify