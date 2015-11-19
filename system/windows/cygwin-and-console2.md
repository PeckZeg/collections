Cygwin + Console2
=================

## 下载 cygwin 与 console2

* [Cygwin](https://www.cygwin.com/)
* [Console2](http://sourceforge.net/projects/console/)

## 在 console2 中配置 cygwin

1. 使用 `edit` → `settings` 进入设置界面
2. 在 `Console` 标签页中的 `Shell` 中键入 `%cygwin%\bin\bash.exe --login -i -c 'cd /cygdrive/%打开时候的目录%; exec /bin/bash'`
3. 在 `Tabs` 标签页中，使用 `add` 按钮新建一个标签页，在 `Shell` 子标签页中的 `Shell` 字段中将上面的命令填至该处。