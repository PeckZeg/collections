# 面试

## 目录

* [通识](#通识)
    * [web 标准的理解](#web 标准的理解)
* [HTML](#HTML)
    * [字符实体](#字符实体)
    * [`cellpadding` 与 `cellspacing`](#-cellpadding-与-cellspacing)

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
