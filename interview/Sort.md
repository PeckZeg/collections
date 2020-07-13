# 排序算法

## 目录

* [冒泡排序 <small>(Bubble Sort)</small>](#冒泡排序-bubble-sort)
* [插入排序 <small>(Insertion Sort)</small>](#插入排序-insertion-sort)
* [希尔排序 <small>(Shell Sort)</small>](#希尔排序-shell-sort)
* [归并排序 <small>(Merge Sort)</small>](#归并排序-merge-sort)
* [快速排序 <small>(Quick Sort)</small>](#快速排序-quick-sort)

## 冒泡排序 <small>(Bubble Sort)</small>

> * [维基百科 - 冒泡排序](https://zh.wikipedia.org/wiki/%E5%86%92%E6%B3%A1%E6%8E%92%E5%BA%8F)

### 运作

1. 比较相邻的元素。如果第一个比第二个大，就交换他们两个。
2. 对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。这步做完后，最后的元素会是最大的数。
3. 针对所有的元素重复以上的步骤，除了最后一个。
4. 持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

### 实现

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

### 改进 1

设置一个标记 `pos`，用于记录每趟排序中最后一次进行交换的位置。由于 `pos` 位置之后的记录均已交换到位，故在进行下一趟排序时只要扫描到 `pos` 位置即可。

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

### 改进 2

每次排序进行正向/反向 2 次排序，每次均可获得一个最大值与最小值，缩短时间。

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

## 插入排序 <small>(Insertion Sort)</small>

> [维基百科 - 插入排序](https://zh.wikipedia.org/wiki/%E6%8F%92%E5%85%A5%E6%8E%92%E5%BA%8F)

### 算法

1. 从第一个元素开始，该元素可以认为已经被排序
2. 取出下一个元素，在已经排序的元素序列中从后向前扫描
3. 如果该元素（已排序）大于新元素，将该元素移到下一位置
4. 重复步骤 3，直到找到已排序的元素小于或者等于新元素的位置
5. 将新元素插入到该位置后
6. 重复步骤 2 ~ 5

### 实现

```js
/**
 * Insertion Sort
 * @param {number[]} arr
 * @returns {number[]}
 */
function insertionSort(arr) {
  for (let i = 1; i < arr.length; i++) {
    let key = arr[i];
    let j = i - 1;

    while (j >= 0 && arr[j] > key) {
      arr[j + 1] = arr[j];
      j--;
    }

    arr[j + 1] = key;
  }

  return arr;
}

// [ -427, -31, 15, 213, 233, 10086, 5201314 ]
insertionSort([233, 10086, -31, 15, 213, 5201314, -427]);
```

## 希尔排序 <small>(Shell Sort)</small>

> [维基百科 - 希尔排序](https://zh.wikipedia.org/wiki/%E5%B8%8C%E5%B0%94%E6%8E%92%E5%BA%8F)

### 算法

1. 选择一个增量序列 t1, t2, …, tk，其中 `ti > tj`，`tk = 1`
2. 按增量序列个数 `k`，对序列进行 `k` 趟排序
3. 每趟排序，根据对应的增量 `ti`，将待排序列分割成若干长度为 `m` 的子序列，分别对各子表进行直接插入排序。仅增量因子为1 时，整个序列作为一个表来处理，表长度即为整个序列的长度。

### 实现

```js
/**
 * Insertion Sort
 * @param {number[]} arr
 * @returns {number[]}
 */
function shellSort(arr) {
  let gap = 1;

    while(gap < arr.length / 5) {
      gap = gap * 5 + 1;
    }

    for (; gap > 0; gap = Math.floor(gap / 5)) {
        for (let i = gap; i < arr.length; i++) {
            const temp = arr[i];
            let j = i - gap;

            for (; j >= 0 && arr[j] > temp; j -= gap) {
                arr[j + gap] = arr[j];
            }

            arr[j + gap] = temp;
        }
    }

  return arr;
}

// [ -427, -31, 15, 213, 233, 10086, 5201314 ]
shellSort([233, 10086, -31, 15, 213, 5201314, -427]);
```

## 归并排序 <small>(Merge Sort)</small>

> [维基百科 - 归并排序](https://zh.wikipedia.org/wiki/%E5%BD%92%E5%B9%B6%E6%8E%92%E5%BA%8F)

### 实现

```js
function merge(left, right) {
  let result = [];

  while (left.length > 0 && right.length > 0) {
    if (left[0] < right[0]) {
      result.push(left.shift());
    }

    else {
      result.push(right.shift());
    }
  }

  return result.concat(left, right);
}

function mergeSort(arr) {
  if (arr.length < 2) {
    return arr;
  }

  let mid = Math.floor(arr.length / 2);
  let left = arr.slice(0, mid);
  let right = arr.slice(mid);

  return merge(mergeSort(left), mergeSort(right));
}

// [ -427, -31, 15, 213, 233, 10086, 5201314 ]
mergeSort([233, 10086, -31, 15, 213, 5201314, -427]);
```

## 快速排序 <small>(Quick Sort)</small>

> [维基百科 - 快速排序](https://zh.wikipedia.org/wiki/%E5%BF%AB%E9%80%9F%E6%8E%92%E5%BA%8F)

### 实现

```js
function quickSort(arr, left, right) {
  left = left || 0;
  right = right || arr.length - 1;

  if (left < right) {
    let x = arr[right];
    let i = left - 1;
    let temp;

    for (let j = left; j <= right; j++) {
      if (arr[j] <= x) {
        i++;
        temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
      }
    }

    quickSort(arr, left, i - 1);
    quickSort(arr, i + 1, right);
  }

  return arr;
}

// [ -427, -31, 15, 213, 233, 10086, 5201314 ]
quickSort([233, 10086, -31, 15, 213, 5201314, -427]);
```