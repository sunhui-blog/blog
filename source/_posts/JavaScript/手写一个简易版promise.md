---
title: 手写一个简易版promise
date: 2021-01-13 23:58:42
tags: 编程语言
categories: JavaScript
---

promise的简易实现
<!-- more -->

<h5>解决的问题有：</h5>
<ol>
  <li>嵌套调用，第一个函数的输出往往是第二个函数的输入；</li>
  <li>处理多个异步请求并发，开发时往往需要同步请求最终的结果。</li>
</ol>

<h5>运用到的设计模式：</h5>
<p>发布订阅模式：收集依赖 -> 触发通知 -> 取出依赖执行</p>


```
const PENDING = 'PENDING'
const FULFILLED = 'FULFILLED'
const REJECTED = 'REJECTED'

class Promise {
  constructor (executor) {
    this.status = PENDING
    this.value = null
    this.reason = null
    // 存放依赖
    this.onRejectedCallbacks = []
    this.onResolvedCallbacks = []

    // 触发通知
    const resolve = (value) => {
      if (this.status === PENDING) {
        this.status = FULFILLED
        this.value = value

        // 执行依赖
        this.onResolvedCallbacks.forEach((fn) => fn())
      }
    }

    // 触发通知
    const reject = (value) => {
      if (this.status === PENDING) {
        this.status = REJECTED
        this.reason = value

        // 执行依赖
        this.onRejectedCallbacks.forEach((fn) => fn())
      }
    }

    try {
      executor(resolve, reject)
    } catch (error) {
      reject(error)
    }
  }

  then (onFulfilled, onRejected) {
    if (this.status === FULFILLED) {
      onFulfilled(this.value)
    }

    if (this.status === REJECTED) {
      onRejected(this.reason)
    }

    // 收集依赖
    if (this.status === PENDING) {
      this.onResolvedCallbacks.push(() => {
        onFulfilled(this.value)
      })

      this.onRejectedCallbacks.push(() => {
        onRejected(this.reason)
      })
    }
  }
}
```

<h5>测试一下：</h5>
```
new Promise((resolve, reject) => {
  resolve('success')
}).then((data) => {
  console.log(data) // 'success'
}, (err) => {
  console.log(err)
})
```


```
new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('success')
  }, 100)
}).then((data) => {
  console.log(data) // 'success'
}, (error) => {
  console.log(error)
})
```
