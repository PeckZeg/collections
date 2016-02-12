Vimium 快捷键指南
================

用了这么久的 Chrome 插件 - [Vimium][vimium] 总是对其快捷键懵懵懂懂，现根据其 options 中的 commands 进行一些整理和翻译。以便日后查询：

## 页面导航

Command    | Note
:--------- | :----
`,`, `<c-e>` | 向下滚动
`k`, `<c-y>` | 向上滚动
`h`         | 向左滚动
`l`         | 向右滚动
`gg`        | 滚动到页面顶部
`G`         | 滚动到页面底部
`zH`        | 滚动到页面最左边
`zL`        | 滚动到页面最右边
`d`         | 向下滚动（相当于 `PageDown` 键）
`u`         | 向上滚动（相当于 `PageUp` 键）
`r`         | 重载页面
`gs`        | 查看页面源代码
`yy`        | 复制当前 URL 到剪贴板
`yf`        | 复制一个 URL 链接到剪贴板
`p`         | 打开剪贴板中的 URL 到当前标签页
`P`         | 打开剪贴板中的 URL 到新标签页
`gu`        | 跳转到当前 URL 的上一层
`gU`        | 跳转到当前 URL 的最高层
`i`         | 进入插入模式
`v`         | Enter visual mode (beta feature) (enterVisualMode)
`V`         | Enter visual line mode (beta feature) (enterVisualLineMode)
`gi`        | 焦点第一个文本输入框。使用 `tab` 可以在文本输入框之间循环跳转
`f`         | 在当前标签页中打开一个链接
`F`         | 在新标签页中打开一个链接
`<a-f>`     | 在新标签页中打开多个链接
`[[`        | Follow the link labeled previous or < (goPrevious)
`]]`        | Follow the link labeled next or > (goNext)
`gf`        | Cycle forward to the next frame on the page (nextFrame)
`gF`        | Select the tab's main/top frame (mainFrame)
`m`         | 创建新标记

## 使用 Vomnibar

Command | Note
:------ | :----
`o`      | 打开 URl、书签或历史记录
`O`      | 在新标签页中打开 URl、书签或历史记录
`T`      | 搜索已打开的标签页
`b`      | 打开书签
`B`      | 在新窗口中打开书签
`ge`     | 编辑当前 URL
`gE`     | 编辑当前 URL 并在新标签页中打开

## 使用查询

Command | Note
:------ | :----
`/`      | 进入查询模式
`n`      | 下一个已查询到的值（页面内循环查找）
`N`      | 上一个已查询到的值（页面内循环查找）

## 导航历史

Command | Note
:------ | :----
`H`      | 根据浏览历史后退一页
`L`      | 根据浏览历史前进一页


## 标签操纵

Command  | Note
:------- | :----
`K`, `gt`  | 向右移动一个标签页
`J`, `gT`  | 向左移动一个标签页
`g0`      | 移动到第一个标签页
`g$`      | 移动到最后一个标签页
`t`       | 创建一个新标签页
`yt`      | 复制当前标签页
`x`       | 关闭当前标签页
`X`       | 恢复已关闭的标签页
`W`       | 将标签页移动到新窗口
`<a-p>`   | 固定/取消固定当前标签页
`<<`      | 向左移动标签页
`>>`      | 向右移动标签页


## 其他

Command | Note
:------ | :----
`?`      | 显示帮助





[vimium]: https://chrome.google.com/webstore/detail/dbepggeogbaibhgnhhndojpepiihcmeb