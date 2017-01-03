在 Mac OS 中制作 zip 包时不打包 `.DS_Store` 文件
============================================

大部分情况适用如下的命令：

```
zip -r filename.zip filename -x "*.DS_Store"
```

其中 `filename.zip` 是打包后的文件名，`filename` 是待打包的目录。

### Reference

* [How to Zip Files in Mac OS X](http://osxdaily.com/2012/01/10/how-to-zip-files-in-mac-os-x/)
* [Linux 下zip包的压缩与解压](https://www.cnblogs.com/chinareny2k/archive/2010/01/05/1639468.html)
* [Mac OS X中打zip包时去除.DS_Store等指定文件](http://www.1mima.com/mac-os%E4%B8%AD%E6%89%93zip%E5%8C%85%E6%97%B6%E5%8E%BB%E9%99%A4-ds_store%E7%AD%89%E6%8C%87%E5%AE%9A%E6%96%87%E4%BB%B6/)
