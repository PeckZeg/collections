2015 总结 - 撸码篇
==================

> 以铜为镜，可以正衣冠；以古为镜，可以知兴替；以人为镜，可以明得失。

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

回顾一年的撸码之路，主要都在使用 Less 进行 CSS 的预处理，对 Less 的混入、条件控制、循环、函数等进行了深入的研究和探讨，并对 Less 的局限性有了深刻的了解。比如要基于颜色 `#eee` 生成一个 `rgba` 颜色需要经过繁琐的步骤：首先要使用 `red()`、`green()` 和 `blue()` 将颜色 `#eee` 的 RGB 值提取出来，再置入 `rgba()` 之中。Less 本身是个工具，但工具只是定义了最基本最原始的使用规则，就像 Ruby 和 Ruby on Rails 的关系一样，相爱相杀。Less 虽然好用，但在实际的开发过程之中，我们却又必不可少的会用到 CSS3，而事实上的 CSS3，又需要受制于浏览器的实现，而浏览器的实现又必不可免的会在属性的前缀加上渲染引擎的烙印，比如 Webkit 系对 `border-radius` 的实验性支持就打上了 `-webkit-` 的烙印，而 Mozilla 系的支持则打上了 `-moz-` 的烙印。平时使用这些属性就已经捉襟见肘，现在面对事实标准的浏览器则又得记住更加庞大的前缀集，这不禁让我菊花一紧。不过还在有 [`LessHat`][lesshat] 这样的存在。使得我们不必记住每个浏览器是否已经实现了某个属性。我们只需记住标准上的属性是如何。当然 [`LessHat`][lesshat] 也有它的局限，比如使用 `.keyframes` 混入类的时候，它要求我们传入一个不能编译的字符串 `~""`。但这和我们习惯上定义 `@keyframes` 不相符合。这又导致了我们需要 fork [`LessHat`][lesshat]，然后进行一些改造的蛋疼事儿。

```
//  LessHat .keyframes
.keyframes(~'animationName, 0%{ transform: scale(1.5); color: blue; } 100%{ transform: scale(2); color: red }');

//  My Habit .keyframes
.keyframes(animationName, {
    0%{ transform: scale(1.5); color: blue; }
    100%{ transform: scale(2); color: red }
});
```

在深秋时节，开始接触了 Sass/Scss，虽然对以 `$` 开头的反人类变量命名方式略有不满，不过还是被其强大的编程风格给吸引，其 `@function`、`@mixin`、`@if`、`@else` 等预处理语句都令我深深地感觉到在这方面弥补了 Less 的不足，又有诸如 `compass`、`autoprefixer` 等框架赋予了其更强大的生命力。

```
//  Scss 示例
@mixin size($size...) {
  $size: if(length($size) > 0, $size, auto);
  $width: nth($size, 1);
  $height: nth($size, length($size));

  @if $width != auto {
    $width: if(unitless($width), $width + px, $width);
  }
  @if $height != auto {
    $height: if(unitless($height), $height + px, $height);
  }

  width: $width;
  height: $height;
}
```

### Resourece

* [`Less`][less] 一个 CSS 预处理器
    - [`LessHat`][lesshat] Less 混入库
* [`Sass/Scss`][sass-scss] 领一个 CSS 预处理器
    - [`Compass`][compass] 基于 Sass/Scss 的 CSS 框架
* [`AutoPrefixer`][autoprefixer] 为 CSS 添加更多的浏览器前缀

## Other

今年主要也是围绕前端方面展开工作，比较详细的总结已经归纳成大点，比较零散的诸如对 C++ 的学习和对数据库 MongoDB 的学习也在开头就已经总结。下面会将一些零碎的知识做一些回顾并对明年的一些学习愿景做一些规划。

虽然技术是第一生产力，不过像产品解读、研究和对人性的洞悉，却也能反过来干预技术的提升。毕竟方向错了，做什么都是徒劳的。为此，在后半年都在学习如何多快好省的开发出不是特别难用的产品模块。

一个功能的最终开发需要受到多方面的牵制，也需要动员诸如需求、辩证、确定、细化以及执行各个方面，其中一环掉了链子，就会产生难以估计的后果。比如在开发后台的时候，想当然的使用视觉上更好的“横排”布局而无视了工作人员对“竖排”操作的习惯，最终导致了我开发出用户体验极度不好的创建功能。而这块功能因为时间的不充裕至今也还未重新设计和排布。



[moment]: http://momentjs.com/
[underscore]: http://underscorejs.org/
[lodash]: https://lodash.com/
[jquery]: http://jquery.com/
[zepto]: http://zeptojs.com/
[backbone]: http://backbonejs.org/
[requirejs]: http://requirejs.org/
[async]: https://github.com/caolan/async
[thunkify]: https://www.npmjs.com/package/thunkify

[sass-scss]: http://sass-lang.com/
[less]: http://lesscss.org/
[lesshat]: http://lesshat.madebysource.com/
[compass]: http://compass-style.org/