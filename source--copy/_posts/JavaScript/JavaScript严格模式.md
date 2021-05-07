---
title: JavaScript严格模式
date: 2020-01-03 14:10:10
tags:
categories: JavaScript
---

<p>严格模式为了修复Javascript语法的不严谨性。</p>

<!-- more -->

<ol>
  <li>初始化未经声明的变量会导致错误。</li>
  <li>arguments.callee/arguments.caller会导致错误。</li>
  <li>不能为函数的caller属性赋值，否则会导致错误。</li>
  <li>严格模式下，在外部访问不到eval()中创建的任何变量或函数，为eval赋值也会导致错误；

  ```
  // 非严格模式
  eval("function sayHi () { alert('hi'); }")
  sayHi() // "hi"

  eval("var msg= 'hello world'; ")
  alert(msg) // "hello world"

  // 严格模式
  "use strict"
  eval = 'hi' // 抛出error 创建变量和函数类似
  ```
  </li>
  <li>Object.defineProperty()的writable(Configurable)设置为false时，再对属性做赋值(delete属性)时，严格模式会抛出异常，非严格模式不会；

  ```
  Object.defineProperty(person, "name", {
    writable: false,
    value: 'Nicholas'
  })
  console.log(person.name) // 'Nicholas'
  person.name = 'lilei'
  console.log(person.name) // 'Nicholas'

  "use strict"
  Object.defineProperty(person, "name", {
    writable: false,
    value: 'Nicholas'
  })
  console.log(person.name) // Nicholas
  person.name = 'lilei' // 抛出error
  console.log(person.name)
  ```
  </li>
  <li>访问器属性：在严格模式下，尝试写入只指定了getter函数的属性抛出错误；(类似地，只指定setter函数的属性也不能读，否则在非严格模式下会返回undefined，在严格模式下会抛出错误??)。
  
  ```
  "use strict";
  let book = {
    _year: 2020,
    edition: 1
  }
  Object.defineProperty(book, "year", {
    get: function () {
      return this._year
    }
  })

  book.year = 2021 // 抛出错误

  "use strict";
  let book = {
    _year: 2020,
    edition: 1
  }
  Object.defineProperty(book, "year", {
    set: function (newValue) {
      this._year = newValue
      this.edition++
    }
  })

  book.year // 非严格模式下 undefined
  ```
  </li>
  <li>call() 方法使用一个指定的 this 值和单独给出的一个或多个参数来调用一个函数。

  <p>
  <em style="display:block;background: #eee;line-height: 32px;margin: 10px 0;">function.call(thisArg, arg1, arg2, ...)</em>
  <em style="display:block;">thisArg:</em>可选的。在 function 函数运行时使用的 this 值。请注意，this可能不是该方法看到的实际值：如果这个函数处于非严格模式下，则指定为 null 或 undefined 时会自动替换为指向全局对象，原始值会被包装。</p>

  ```
  "use strict"
  window.color = "red"
  let o = { color: "blue" }

  function sayColor() {
    console.log(this.color)
  }
  sayColor.call(null); // error 非严格：red
  sayColor.call(undefined); // error 非严格：red
  ```
  </li>
</ol>