# 使用 ObjectId 查询某个时间范围的数据

## 使用下面的查询语句

```javascript
db.collection.count({
    _id: {
        $gte: ObjectId(~~((new Date('2016-04-29 00:00:00') / 1000).toString(16)) + '0000000000000000'),
        $lte: ObjectId(~~((new Date('2016-04-29 00:00:00') / 1000).toString(16)) + '0000000000000000')
    }
});
```

不过……MongoDB 在 3.2 的 `Date` 对象只能够创建 `YYYY-MM-DD` 的日期对象，所以，可以在外部把查询条件撸好再上传