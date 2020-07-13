# 排序算法

## 目录

* [冒泡排序 <small>(Bubble Sort)</small>](#冒泡排序-bubble-sort)

## 冒泡排序 <small>(Bubble Sort)</small>

> * [维基百科 - 冒泡排序](https://zh.wikipedia.org/wiki/%E5%86%92%E6%B3%A1%E6%8E%92%E5%BA%8F)

### 运作

1. 比较相邻的元素。如果第一个比第二个大，就交换他们两个。
2. 对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。这步做完后，最后的元素会是最大的数。
3. 针对所有的元素重复以上的步骤，除了最后一个。
4. 持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

### 实现

<details>
<summary>源代码</summary>

```js
function bubbleSort(arr) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[i] > arr[j]) {
        const tmp = arr[i];
        arr[i] = arr[j];
        arr[j] = tmp;
      }
    }
  }

  return arr;
}

// [ -427, -31, 15, 213, 233, 10086, 5201314 ]
bubbleSort([233, 10086, -31, 15, 213, 5201314, -427]);
```
</details>

### 改进 1

设置一个标记 `pos`，用于记录每趟排序中最后一次进行交换的位置。由于 `pos` 位置之后的记录均已交换到位，故在进行下一趟排序时只要扫描到 `pos` 位置即可。

<details>
<summary>源代码</summary>

```js
function bubbleSort(arr) {
  let i = arr.length - 1;

  while (i > 0) {
    let pos = 0;

    for (let j = 0; j < i; j++) {
      if (arr[j] > arr[j + 1]) {
        let tmp = arr[j];

        arr[j] = arr[j + 1];
        arr[j + 1] = tmp;
        pos = j;
      }
    }

    i = pos;
  }

  return arr;
}

// [ -427, -31, 15, 213, 233, 10086, 5201314 ]
bubbleSort([233, 10086, -31, 15, 213, 5201314, -427]);
```
</details>

### 改进 2

每次排序进行正向/反向 2 次排序，每次均可获得一个最大值与最小值，缩短时间。

<details>
<summary>源代码</summary>

```js
function bubbleSort(arr) {
  let left = 0;
  let right = arr.length - 1;

  while (left < right) {
    for (let i = left; i < right; i++) {
      if (arr[i] > arr[i + 1]) {
        const tmp = arr[i];

        arr[i] = arr[i + 1];
        arr[i + 1] = tmp;
      }
    }

    right--;

    for (let i = right; i > left; i--) {
      if (arr[i] < arr[i - 1]) {
        const tmp = arr[i];

        arr[i] = arr[i - 1];
        arr[i - 1] = tmp;
      }
    }

    left++;
  }

  return arr;
}

// [ -427, -31, 15, 213, 233, 10086, 5201314 ]
bubbleSort([233, 10086, -31, 15, 213, 5201314, -427]);
```
</details>