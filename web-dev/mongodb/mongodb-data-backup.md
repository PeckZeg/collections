MongoDB 数据备份/恢复
=====================

## MongoDB 数据备份

使用 [`mongodump`][mongodump] 进行备份，比较常用的形式如下：

```
mongodump -d [数据库] -o [导出路径]
```

导出数据之后我们可以使用 7z 进行打包，常用的命令如下：

```
7za a [压缩包名].7z [导出路径]
```

## MongoDB 数据恢复

使用 [`mongorestore`][mongorestore] 命令进行数据恢复，常用形式如下：

```
mongorestore -d [数据库] [数据路径]
```



[mongodump]: https://docs.mongodb.org/manual/reference/program/mongodump/
[mongorestore]: https://docs.mongodb.org/manual/reference/program/mongorestore/