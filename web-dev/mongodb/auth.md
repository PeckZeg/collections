为 MongoDB 添加 auth 验证
=========================

更新了 MongoDB 3.2 之后发现原来的 `addUser` 命令已经失效了，借着这个机会正好撸一把关于开启 MongoDB 验证的文章。

## 创建系统管理员

MongoDB 对数据库的操作是分[角色（Role）][built-in-roles] 的，可以使用内置的角色，也可以自己搞个角色使用。

先使用不带任何参数的 `mongod` 启动 MongoDB 数据库。

在数据库 `admin` 中使用 [`createUser()`][db.createUser] 建立一个能够管理其他数据库的“炒鸡用户”，以创建各个数据库的管理用户。

```
use admin

db.createUser({
    //  用户名
    user: 'root',

    //  密码
    pwd: 'root',
    
    //  角色，因为是可选项，可以等到后面再设置
    roles: [
        {
            role: 'userAdminAnyDatabase',
            db: 'admin'
        }
    ]
});
```

## 开启验证

开启验证比较简单，在开启 `mongod` 的时候附加参数 `--auth` 就可以了。

```
$   mongod --auth
```

在开启验证之后，我们就可以使用 `-u` 和 `-p` 模式来开启 `mongod` 了。

```
$   mongod admin -u root -p root
```

## 为具体的数据库创建管理者

在开启了验证之后的 `mongod`，因为我们登陆的是具有 `userAdminAnyDatabase` (管理所有数据库) 权限的用户，所以我们可以为其他数据库开设其他的用户（使用 `root` 不能直接操作）。

```
use test_project

db.createUser({
    user: 'testAdmin',
    pwd: 'impwd',
    roles: [
        {
            role: 'dbOwner',
            db: 'test_project'
        }
    ]
});
```

## 番外：使用 Mongoose 登陆 auth 验证的 MongoDB

只讨论 `connection` 的建立，其他的创建 `schema`, `model` 等基础知识移步 [Mongoose Docs][mongoose-docs]。

建立 auth 连接的 `createConnection` 有若干种写法，个人比较喜欢的写法是：

```js
const mongoose = require('mongoose');

module.exports = mongoose.createConnection('localhost', 'test_project', 27017, {
    user: 'testAdmin',
    pass: 'impwd'
});
```





[built-in-roles]: https://docs.mongodb.org/manual/reference/built-in-roles/#built-in-roles
[db.createUser]: https://docs.mongodb.org/manual/reference/method/db.createUser/
[mongoose-docs]: http://mongoosejs.com/docs/guide.html
[Mongoose#createConnection]: http://mongoosejs.com/docs/api.html#index_Mongoose-createConnection