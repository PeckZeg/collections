设置 Sass 的编码为 UTF8
=======================

在编译 Sass 文件时经常会碰到中文乱码亦或注释乱码，有时还会出现如下的错误

```powershell
Syntax error: Invalid GBK character "\xE5"
        on line 8 of E:\work\sass\sass\_big_box.scss
        from line 16 of E:\work\sass\sass\main.scss
  Use --trace for backtrace.

Syntax error: Invalid GBK character "\xE5"
        on line 2 of E:\work\sass\sass\main.scss
  Use --trace for backtrace.
```

几经折腾终于在 [ruby环境sass编译中文出现Syntax error: Invalid GBK character错误解决方法](http://www.cnblogs.com/zhidong123/p/3902270.html) 文章中获取了解决的方法。

 1. 查找 Ruby 的安装路径，如 `C:\Ruby\lib\ruby\gems\1.9.1\gems\sass-3.3.14\lib\sass`
 2. 在文件夹中找出 `engine.rb`
 3. 在 `require()` 块之后添加如下代码

    ```
    Encoding.default_external = Encoding.find('utf-8')
    ```
