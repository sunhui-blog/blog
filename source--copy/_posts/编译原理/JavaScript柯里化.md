---
title: JavaScript柯里化
date: 2021-01-01 20:04:18
tags: 编译原理
categories: 编译原理
---

<p>Currying：把接受多个参数的函数变换成接受一个单一参数（最初函数的第一个参数）的函数，并且返回接受余下的参数而且返回结果的新函数。</p>

<!-- more -->

```
function add (x, y) {
  return (x + y)
}

console.log(add(1, 2))

function curriedAdd (x) {
  return function (y) {
    return x + y
  }
}

console.log(curriedAdd(1)(3))
console.log(curriedAdd(1)(3) === 4)

function add (x, y) {
  return (x + y)
}

function currying (fn, ...args1) {
  return function (...args2) {
    return fn(...args1, ...args2)
  }
}

currying(add, 1)
currying(add, 1)(2)
```

