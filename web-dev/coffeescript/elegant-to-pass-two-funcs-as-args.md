# 优雅的传入两个参数函数

在学习 AngularJS 的 [`$http`](https://docs.angularjs.org/api/ng/service/$http) 的时候，发现如下代码在使用 [CoffeeScript](http://coffeescript.org/) 编写的时候需要一个优雅的方式来重新组织。

```javascript
// Simple GET request example:
$http({
  method: 'GET',
  url: '/someUrl'
}).then(function successCallback(response) {
    // this callback will be called asynchronously
    // when the response is available
  }, function errorCallback(response) {
    // called asynchronously if an error occurs
    // or server returns response with an error status.
  });
```

在查阅了一些资料之后，发现可以在调用 `.then` 后加一个反斜杠 `\` 来进行折行，使得代码更加优雅。

```coffeescript
# Simple GET request example:
$http
  method: 'GET'
  url: '/someUrl'
.then \
  (response) ->
    # this callback will be called asynchronously
    # when the response is available
  ,
  (response) ->
    # called asynchronously if an error occurs
    # or server returns response with an error status.
```
