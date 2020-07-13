# 面试

## 目录

* [通识](#通识)
    * [web 标准的理解](#web-标准的理解)
* [HTML](#HTML)
    * [字符实体](#字符实体)
    * [`cellpadding` 与 `cellspacing`](#cellpadding-与-cellspacing)
* [CSS](#CSS)
    * [选择器](#选择器)
    * [选择器优先级与覆盖规则](#选择器优先级与覆盖规则)
    * [`display`, `visiblity`, `opacity`](#display-visiblity-opacity)
    * [`position`](#position)
* [排序算法](Sort.md)
* [LeetCode 算法题](LeetCode.md)
    

## 通识

### web 标准的理解

<details>
<summary>答案</summary>

Web标准经过精心设计，旨在让广大用户享有最佳的上网体验，同时也确保在网上发布的文件经久不衰。由这些标准设计、构建的网站简化并降低了开发成本，同时又可以让更多人访问，并适应更多的上网设备。随着传统桌面浏览器的进化、新型互联网设备进入市场，经由这些准则开发的网站将继续正常运作。
    
**参考**

* [MDN - Web 标准](https://developer.mozilla.org/zh-CN/docs/Archive/Web_%E6%A0%87%E5%87%86)
* [对web标准的理解](https://www.jianshu.com/p/b9147262ef8e)
* [web前端面试题第一道—web标准](https://www.jianshu.com/p/14c5b7ca56b8)
</details>

## HTML

### 字符实体

<details>
<summary>答案</summary>

在 HTML 中，某些字符是预留的。

在 HTML 中不能使用小于号（`<`）和大于号（`>`），这是因为浏览器会误认为它们是标签。

如果希望正确地显示预留字符，我们必须在 HTML 源代码中使用字符实体（character entities）。 字符实体类似这样：

```html
&entity_name;
&#entity_number;
```

如需显示小于号，我们必须这样写：`&lt;` 或 `&#60;` 或 `&#060;`

> :bulb: 提示: 使用实体名而不是数字的好处是，名称易于记忆。不过坏处是，浏览器也许并不支持所有实体名称（对实体数字的支持却很好）。

#### 不间断空格 <small>(Non-breaking Space)</small>

HTML 中的常用字符实体是不间断空格(`&nbsp;`)。

浏览器总是会截短 HTML 页面中的空格。如果您在文本中写 10 个空格，在显示该页面之前，浏览器会删除它们中的 9 个。如需在页面中增加空格的数量，您需要使用 `&nbsp;` 字符实体。

#### 结合音标符

发音符号是加到字母上的一个"glyph(字形)"。

一些变音符号, 如 尖音符 (` `̀) 和 抑音符 (` `́) 。

变音符号可以出现字母的上面和下面，或者字母里面，或者两个字母间。

变音符号可以与字母、数字字符的组合来使用。

#### HTML 字符实体

> :bulb: 实体名称对大小写敏感！

#### 参考

* [RUNOOB - HTML 字符实体](https://www.runoob.com/html/html-entities.html)
* [W3school - HTML 字符实体](https://www.w3school.com.cn/html/html_entities.asp)

</details>

### `cellpadding` 与 `cellspacing`

<details>
<summary>答案</summary>

> HTML5 不支持 `<table />` 的 `cellpadding` 与 `cellspacing` 属性，请使用 CSS 代替。

`cellspacing` 属性规定单元之间的空间，而 `cellpadding` 规定单元边沿与单元内容之间的空间。两个属性均以 `px` 为单位。

#### 引用

* [MDN - `table`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table)
* [RUNOOB - HTML `<table>` `cellspacing` 属性](https://www.runoob.com/tags/att-table-cellspacing.html)
</details>

## CSS

### 选择器

<details>
<summary>答案</summary>

> 摘抄自 [MDN - CSS 选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Selectors)

#### 基本选择器

##### 通用选择器 <small>Universal selector</small>

选择所有元素。（可选）可以将其限制为特定的名称空间或所有名称空间。

* 语法: `*` `ns|*` `*|*`
* 例子：`*` 将匹配文档的所有元素。

##### 类型选择器 <small>Type selector</small>

按照给定的节点名称，选择所有匹配的元素。

* 语法：`elementname`
* 例子：`input` 匹配任何 `<input>` 元素。

##### 类选择器 <small>Class selector</small>

按照给定的 `class` 属性的值，选择所有匹配的元素。

* 语法：`.classname`
* 例子：`.index` 匹配任何 `class` 属性中含有 `index` 类的元素。

##### ID 选择器 <small>ID selector</small>

按照 id 属性选择一个与之匹配的元素。需要注意的是，一个文档中，每个 ID 属性都应当是唯一的。

* 语法：`#idname`
* 例子：`#toc` 匹配 ID 为 `toc` 的元素。

##### 属性选择器 <small>Attribute selector</small>

按照给定的属性，选择所有匹配的元素。

* 语法：`[attr]` `[attr=value]` `[attr~=value]` `[attr|=value]` `[attr^=value]` `[attr$=value]` `[attr*=value]`
* 例子：`[autoplay]` 选择所有具有 `autoplay` 属性的元素（不论这个属性的值是什么）。

#### 分组选择器 <small>Grouping selectors</small>

##### 选择器列表 <small>Selector list</small>

`,` 是将不同的选择器组合在一起的方法，它选择所有能被列表中的任意一个选择器选中的节点。

* 语法：`A, B`
* 示例：`div, span` 会同时匹配 `<span>` 元素和 `<div>` 元素。

#### 组合器 <small>Combinators</small>

##### 后代组合器 <small>Descendant combinator</small>

` `（空格）组合器选择前一个元素的后代节点。

* 语法：`A B`
* 例子：`div span` 匹配所有位于任意 `<div>` 元素之内的 `<span>` 元素。

##### 直接子代组合器 <small>Child combinator</small>

`>` 组合器选择前一个元素的直接子代的节点。

* 语法：`A > B`
* 例子：`ul > li` 匹配直接嵌套在 `<ul>` 元素内的所有 `<li>` 元素。

##### 一般兄弟组合器（General sibling combinator）

`~` 组合器选择兄弟元素，也就是说，后一个节点在前一个节点后面的任意位置，并且共享同一个父节点。

* 语法：`A ~ B`
* 例子：`p ~ span` 匹配同一父元素下，`<p>` 元素后的所有 `<span>` 元素。

##### 紧邻兄弟组合器 <small>Adjacent sibling combinator</small>

`+` 组合器选择相邻元素，即后一个元素紧跟在前一个之后，并且共享同一个父节点。

* 语法：`A + B`
* 例子：`h2 + p` 会匹配所有紧邻在 `<h2>` 元素后的 `<p>` 元素。

##### 列组合器 <small>Column combinator</small>

`||` 组合器选择属于某个表格行的节点。

* 语法：`A || B`
* 例子：`col || td` 会匹配所有 `<col>` 作用域内的 `<td>` 元素。

#### 伪选择器 <small>Pseudo</small>

##### 伪类

`:` 伪选择器支持按照未被包含在文档树中的状态信息来选择元素。

* 例子：`a:visited` 匹配所有曾被访问过的 `<a>` 元素。

##### 伪元素

`::` 伪选择器用于表示无法用 HTML 语义表达的实体。

* 例子：`p::first-line` 匹配所有 `<p>` 元素的第一行。

#### 引用

* [MDN - CSS 选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Selectors)
* [阮一峰的网络日志 - CSS选择器笔记](http://www.ruanyifeng.com/blog/2009/03/css_selectors.html)
* [W3school - CSS 选择器参考手册](https://www.w3school.com.cn/cssref/css_selectors.asp)
* [CSS参考手册](http://css.doyoe.com/)
</details>

### 选择器优先级与覆盖规则

<details>
<summary>答案</summary>

> 基于 [RUNOOB - CSS 样式优先级](https://www.runoob.com/w3cnote/css-style-priority.html) 整理

#### 选择器优先级

1. ID 选择器
2. 类选择器
3. 属性选择器
4. 伪类选择器
5. 伪元素选择器
6. 标签选择器
7. 通配选择器

#### 覆盖规则

1. 最近的祖先样式比其他祖先样式优先级高
2. "直接样式"比"祖先样式"优先级高
3. 优先级关系
4. 权重一样的情况下则就近原则
5. 属性后插有 `!important` 的属性拥有最高优先级。若同时插有 `!important`，则再利用规则 3、4 判断优先级

#### 引用

* [RUNOOB - CSS 样式优先级](https://www.runoob.com/w3cnote/css-style-priority.html)
* [MDN - 优先级](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity)
* [CSS Specifishity](https://specifishity.com/)
</details>

### `display`, `visiblity`, `opacity`

<details>
<summary>答案</summary>

> 来自 [stackoverflow](https://stackoverflow.com/a/273076/4662191)

css                    | collapse | events | taborder
---------------------- | -------- | ------ | ----
`opacity: 0`           | No       | Yes    | Yes
`visibility: hidden`   | No       | No     | No
`visibility: collapse` | Yes*     | No     | No
`display: none`        | Yes      | No     | No

#### 引用

* [stackoverflow](https://stackoverflow.com/a/273076/4662191)
* [segmentfault - CSS中用 opacity、visibility、display 属性将 元素隐藏 的 对比分析](https://segmentfault.com/a/1190000015116392)
* [RUNOOB - CSS Display(显示) 与 Visibility（可见性）](https://www.runoob.com/css/css-display-visibility.html)
</details>

### `position`

<details>
<summary>答案</summary>

> 来自 [MDN - `position`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position)

CSS `position` 属性用于指定一个元素在文档中的定位方式。

#### `static`

该关键字指定元素使用正常的布局行为，即元素在文档常规流中当前的布局位置。

此时 `top`, `right`, `bottom`, `left` 和 `z-index` 属性无效。

#### `relative`

该关键字下，元素先放置在未添加定位时的位置，再在不改变页面布局的前提下调整元素位置（因此会在此元素未添加定位时所在位置留下空白）。

`position: relative` 对 `table-*-group`, `table-row`, `table-column`, `table-cell`, `table-caption` 元素无效。

#### `absolute`

元素会被移出正常文档流，并不为元素预留空间，通过指定元素相对于最近的非 `static` 定位祖先元素的偏移，来确定元素位置。

绝对定位的元素可以设置外边距（margins），且不会与其他边距合并。

#### `fixed`

元素会被移出正常文档流，并不为元素预留空间，而是通过指定元素相对于屏幕视口（viewport）的位置来指定元素位置。元素的位置在屏幕滚动时不会改变。打印时，元素会出现在的每页的固定位置。

`fixed` 属性会创建新的层叠上下文。当元素祖先的 `transform`, `perspective` 或 `filter` 属性非 `none` 时，容器由视口改为该祖先。

#### `sticky`


元素根据正常文档流进行定位，然后相对它的最近滚动祖先（nearest scrolling ancestor）和 containing block (最近块级祖先 nearest block-level ancestor)，包括 `table-related` 元素，基于 `top`, `right`, `bottom`, 和 `left` 的值进行偏移。偏移值不会影响任何其他元素的位置。

该值总是创建一个新的层叠上下文（stacking context）。注意，一个 `sticky` 元素会“固定”在离它最近的一个拥有“滚动机制”的祖先上（当该祖先的 `overflow` 是 `hidden`, `scroll`, `auto`, 或 `overlay` 时），即便这个祖先不是真的滚动祖先。这个阻止了所有“sticky”行为（详情见 [Github issue on W3C CSSWG](https://github.com/w3c/csswg-drafts/issues/865) ）。

#### 引用

* [MDN - `position`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position)
* [学习CSS布局 - `position`](https://zh.learnlayout.com/position.html)
</details>