---
title: 手写一个compose
date: 2021-01-13 23:58:42
tags: 编程语言
categories: JavaScript
---

<p>从右到左循环调用</p>

<!-- more -->

```
function compose (...args) {
  return function (x) {
    return args.reduceRight((prev, cur) => {
      return cur(prev)
    }, x)
  }
}
```

测试一下：
```
function toUpperCase (str) {
  return str.toUpperCase()
}

function add (str) {
  return str += '!'
}

const fn = compose(add, toUpperCase)
console.log(fn('hello')) // 'HELLO!'
```