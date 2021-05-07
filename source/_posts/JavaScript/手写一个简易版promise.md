---
title: 手写一个简易版promise
date: 2021-01-13 23:58:42
tags: 编程语言
categories: JavaScript
---

<p>promise解决的问题：javascript是单线程，避免阻塞。</p>

<style type="text/css">
.red {color: red;}
.blue {color: blue;}
</style>
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

<ol>
  <li>
    <p>Promise.all：按队列依次返回结果</p>
    ```
    const promise1 = new Promise((resolve, reject) => {
      setTimeout(resolve, 1000, 'promise1')
    })

    const promise2 = new Promise((resolve, reject) => {
      setTimeout(resolve, 2000, 'promise2')
    })

    const promise3 = new Promise((resolve, reject) => {
      setTimeout(resolve, 3000, 'promise3')
    })

    Promise.all([promise1, promise2, promise3]).then((result) => {
      console.log(result) // ["promise1", "promise2", "promise3"]
    }).catch((error) => {
      console.log(error)
    })
    ```

    <p>手写一个Promise.all</p>
    ```
    function all (promises) {
      return new Promise((resolve, reject) => {
        var result = []
        promises.forEach((promise) => {
          promise.then((values) => {
            result.push(values)
            result.length === promises.length && resolve(result)
          }, (error) => {
            reject(error)
          })
        })
      })
    }
    ```

    <p>测试一下：</p>
    ```
    all([promise1, promise2, promise3]).then((result) => {
      console.log(result) // ["promise1", "promise2", "promise3"]
    }).catch((error) => {
      console.log(error)
    })
    ```
  </li>
  <li>
    <p>Promise.race：采用<span class="red">第一个promise的值</span>作为它的值。无论堆栈中后面的promise是resolve还是reject都会取第一个返回的结果</p>
    <ol>
      <li>返回结果与<span class="red">Promise的结果(resolve和reject)</span>无关，仅与返回的顺序。</li>
      <li>promise中存在<span class="red">setTimeout</span>，会影响返回结果。</li>
    </ol>
    <div>
      <p>手写一个Promise.race</p>
      ```
      function race (promises) {
        var hasValue = false
        var hasError = false
        return new Promise((resolve, reject) => {
          promises.forEach(promise => {
            promise.then((value) => {
              !hasValue && !hasError && resolve(value)
              hasValue = true
            }, (error) => {
              !hasValue && !hasError && reject(error)
              hasError = true
            })
          })
        })
      }
      ```
      <p>测试一下：</p>

      ```
      race([promise1, promise2, promise3]).then(values => {
        console.log(values) // "promise1"
      })
      ```
    </div>
  </li>
  <li>
    <p>Promise.allSettled：返回一个在所有给定的promise都已经fulfilled或rejected后的promise，并带有一个对象数组，每个对象表示对应的promise结果。</p>
    ```
      Promise.allSettled([promise1, promise2, promise3]).then((result) => {
        result.forEach(item => console.log(item))
        // {status: "fulfilled", value: "promise1"}
        // {status: "fulfilled", value: "promise2"}
        // {status: "fulfilled", value: "promise3"}
      })
    ```
  </li>
  <li>
    <p>只要其中的一个 promise 成功，就返回那个已经成功的 promise：只要其中的一个 promise 成功，就返回那个已经成功的 promise。</p>
    ```
      Promise.any([promise1, promise2, promise3]).then((value) => {
        console.log(value);
      })
    ```
  </li>
  <li>
    <p>Promise.resolve：</p>
    ```
      Promise.resolve(5).then((values) => {console.log(values)}) // "5"
    ```
  </li>
  <li>
    <p>Promise.reject：</p>
    ```
      Promise.reject('error').then(()=>{}, (error)=> {console.log(error)}) // "reject"
    ```
  </li>
</ol>



<h4 style="margin-top:50px;"><附></h4>
<ol>
  <li>https://promisesaplus.com/</li>
  <li>https://github.com/promises-aplus</li>
  <li>https://www.promisejs.org/patterns/</li>
</ol>
