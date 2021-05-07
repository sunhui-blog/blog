---
title: JavaScript的set和get
date: 2021-01-11 10:48:32
tags: 编程语言
categories: JavaScript
---

<p>JavaScript如何定义赋值？赋值的方式有哪些？</p>

<!-- more -->

<ol>
  <li>ES6的set和get：
    <div>
      ```
      class MyClass {
        constructor () {
          this.data = {}
        }

        set prop (value) {
          this.data = value
        }

        get prop () {
          return this.data
        }
      }

      const test = new MyClass()
      test.prop = 123
      test.prop // output:'123'
      ```
    </div>
  </li>
  <li>ES6的set和get：
    <div>
    ```
    let book = {
      _year: 2020,
      edition: 1
    }
    Object.defineProperty(book, 'year', {
      get: function () {
        return this._year
      },
      set: function (newValue) {
        this._year = newValue
        this.edition++
      }
    })
    ```
    </div>
  </li>
</ol>

<h4 style="margin-top:50px;"><附></h4>
<ol>
  <li>
    ES6的Symbol的key的实现
  </li>
</ol>