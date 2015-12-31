2015 总结 - 撸码篇 2
====================

之前已经写过一篇对过去一年内的总结，不过感觉这个月功力大增，故又开了一篇来总结下这俩个月所经历的练功心得。顺带再展望下对明年的规划。

在这个月内抽空把 Backbone 的最后一块骨头 `Router` 给完全啃了下来，基本上已经把 Backbone 的技能点满。现在的 `jQuery` / `Zepto` + `Lodash` / `Underscore` + `Backbone` + `RequireJS` 组合拳已经耍的飞起，攻击力估计有去年同期的 5 倍威力。

趁着这股风头再加上项目需要进行重构，顺势把这个组合拳也用上，也把以前的 Snake Case 风格的代码改成了 JavaScript 推荐的 Camel Case 风格。

在 12 月也尝试了各种各样的代码库，比如 [AngularJS][angularjs]、[Highcharts][highcharts]。使用 [AngularJS][angularjs] 的感觉就像是在捏个皮球，你怎么捏它都是个球，也不能把球捏成个杯子。所以使用场景比较有限，而且接口需要前后端一致，定制度不是特别高。作为通用组件党，也就食之无味了。[Highcharts][highcharts] 是个简单粗暴的图表库，基本上官网所带的 Demo 稍微改改就能满足我的大部分需求，这也是我最终把它用在项目上的原因。

在 NodeJS 方面，这个月碰触到许多十分有用的模块包，比如这款 [app-root-path][app-root-path] 就是其中很赞的一个模块包，它提供了一个 `require()` 方法，能够根据运行文件的相对位置去加载文件，这解决了老夫在深层次目录里的文件加载位于另外一个位置上的深层次目录里的文件的问题。

## 关于 2016

对 2016 其实也并没有抱什么太大期望，该干嘛干嘛，争取继续这份工作，毕竟这年头想找再找到能够个 Node 项目也不是一件易事。不过还是抱着持续学习的心态，想说能够做好下面几个点，估计 16 年也无憾了：

* 对 JavaScript 的常用框架和库的源码进行研究，顺带重新研究下源生 BOM
* 继续研究 NodeJS，对底层的实现机制进行深刻的探究
* 对 ES6、ES7 进行探索实验，择其重点探究之
* 对 C++ 这门底层语言进行学习
    - 希望能在第一季度结束对基础的学习
    - 在第二季度能够进行简单 Node 组件的开发（或者能看懂源码）

嘛，生活不易，不爽的时候就看看 [MinggeJS][minggejs] 的各种神奇 issues，就会立即进入 233 模式。也算是不错的娱乐吧。






[angularjs]: https://angularjs.org/
[highcharts]: http://www.highcharts.com/
[app-root-path]: https://www.npmjs.com/package/app-root-path
[minggejs]: https://github.com/drduan/minggeJS/issues