Lodash 中文文档 (v3.10.1)
=========================

> Translated by PeckZeg

## “Array” 方法



### `_.chunk(array, [size=1])`

> 创建一个每组具有 `size` 个元素的数组。如果 `collection` 不能被均匀分割，则最后一个分块将包含剩余的元素。

#### 参数

* `array` (_Array_): 待处理的数组
* `[size=1]` (_number_): 每个分块的长度

#### 返回
(_Array_): 返回包含分块的新数组

#### 示例

```
_.chunk(['a', 'b', 'c', 'd'], 2);
// → [['a', 'b'], ['c', 'd']]

_.chunk(['a', 'b', 'c', 'd'], 3);
// → [['a', 'b', 'c'], ['d']]
```


### `_.compact(array)`

> 创建一个不包含假值的数组。假值包括 `false`、`null`、`0`、`""`、`undefined` 和 `NaN`。

#### 参数

* `array` (_Array_): 待压数组。

#### 返回
(_Array_): 返回已过滤的新数组。

#### 示例

```javascript
_.compact([0, 1, false, 2, '', 3]);
// → [1, 2, 3]
```



### `_.difference(array, [values])`

> Creates an array of unique array values not included in the other provided arrays using SameValueZero for equality comparisons.

> 不包含在另外一个数组中（使用 `SameValueZero` 进行相等性比较）

#### Arguments

* `array` (_Array_): 待检查的数组.
* `[values]` (_…Array_): 排除值的数组.

#### Returns

* (_Array_): 返回过滤后的新数组。

#### 示例

```
_.difference([1, 2, 3], [4, 2]);
// → [1, 3]
```