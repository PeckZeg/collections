# LeetCode 算法题

## 目录

* [146. LRU 缓存机制](#lru-缓存机制)

## LRU 缓存机制

> [146. LRU 缓存机制](https://leetcode-cn.com/problems/lru-cache/)

运用你所掌握的数据结构，设计和实现一个  [LRU (最近最少使用) 缓存机制](https://baike.baidu.com/item/LRU)。它应该支持以下操作： 获取数据 `get` 和 写入数据 `put` 。

获取数据 `get(key)` - 如果关键字 (key) 存在于缓存中，则获取关键字的值（总是正数），否则返回 `-1`。

写入数据 `put(key, value)` - 如果关键字已经存在，则变更其数据值；如果关键字不存在，则插入该组「关键字/值」。当缓存容量达到上限时，它应该在写入新数据之前删除最久未使用的数据值，从而为新的数据值留出空间。

**示例:**

```java
LRUCache cache = new LRUCache( 2 /* 缓存容量 */ );

cache.put(1, 1);
cache.put(2, 2);
cache.get(1);       // 返回  1
cache.put(3, 3);    // 该操作会使得关键字 2 作废
cache.get(2);       // 返回 -1 (未找到)
cache.put(4, 4);    // 该操作会使得关键字 1 作废
cache.get(1);       // 返回 -1 (未找到)
cache.get(3);       // 返回  3
cache.get(4);       // 返回  4
```

<details>
<summary>源码</summary>

> [力扣官方题解](https://leetcode-cn.com/problems/lru-cache/solution/lruhuan-cun-ji-zhi-by-leetcode-solution/)

```js
/**
 * @param {number} key
 * @param {number} value
 * @return {DLinkedNode}
 */
function DLinkedNode(key, value) {
  this.key = key;
  this.value = value;
  this.prev = null;
  this.next = null;
}

/**
 * @param {number} capacity
 */
var LRUCache = function(capacity) {
  this.capacity = capacity;
  this.cache = {};
  this.size = 0;
  this.head = new DLinkedNode();
  this.tail = new DLinkedNode();

  this.head.next = this.tail;
  this.tail.prev = this.head;
};

/** 
 * @param {number} key
 * @return {number}
 */
LRUCache.prototype.get = function(key) {
  if (!(key in this.cache)) {
    return -1;
  }

  let node = this.cache[key];
  this.moveToHead(node);
  return node.value;
};

/** 
 * @param {number} key 
 * @param {number} value
 * @return {void}
 */
LRUCache.prototype.put = function(key, value) {
  if (!(key in this.cache)) {
    const node = new DLinkedNode(key, value);

    this.cache[key] = node;
    this.addToHead(node);
    this.size += 1;

    if (this.size > this.capacity) {
      const node = this.removeTail();
      delete this.cache[node.key];
      this.size -= 1;
    }

    return;
  }

  node = this.cache[key];
  node.value = value;
  this.moveToHead(node);
};

LRUCache.prototype.addToHead = function(node) {
  node.prev = this.head;
  node.next = this.head.next;
  this.head.next.prev = node;
  this.head.next = node;
}

LRUCache.prototype.removeNode = function (node) {
  node.prev.next = node.next;
  node.next.prev = node.prev;
}

LRUCache.prototype.moveToHead = function (node) {
  this.removeNode(node);
  this.addToHead(node);
}

LRUCache.prototype.removeTail = function() {
  let node = this.tail.prev;
  this.removeNode(node);
  return node;
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * var obj = new LRUCache(capacity)
 * var param_1 = obj.get(key)
 * obj.put(key,value)
 */
```
</details>