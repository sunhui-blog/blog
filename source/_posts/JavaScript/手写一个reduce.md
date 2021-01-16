---
title: 手写一个reduce
date: 2021-01-13 19:05:14
tags: 编程语言
categories: JavaScript
---

reduce累加器的js实现
<!-- more -->

```
Array.prototype.myReduce = function (callback, initVal) {
  const arr = this

  arr.forEach((item) => {
    initVal = callback(item, initVal)
  })

  return initVal
}
```

测试一下：
```
const datas = [4, 8, 15, 16, 23, 42]

const sum = datas.myReduce(function (prev, next) {
  return prev + next
}, 0)

console.log(sum) // 108
```
