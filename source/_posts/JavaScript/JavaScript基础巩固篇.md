---
title: JavaScript基础巩固篇
date: 2019-06-25 16:50:28
tags: 编程语言
categories: JavaScript
thumbnail: img/basic.jpg
---
<p>“好记性不如烂笔头”夯实基础，提高效率，深耕底层，精细打磨，优化产出。</p>

<!-- more -->

<ol>
    <li>如何区分数组和对象？
        <div style="margin-top:10px;">
            <p>通过Object.prototype.toString.call()方法来识别</p>
            ```
            Object.prototype.toString.call([])  // "[object Array]"
            Object.prototype.toString.call({})  // "[object Object]"
            ```
            <p>通过ES6中的Array.isArray()方法来识别</p>
            ```
            Array.isArray([])  // true
            Array.isArray({})  // false
            ```
            <p>通过instanceof运算符来识别</p>
            ```
            console.log({} instanceof Array) // false 
            console.log([] instanceof Array) // true
            ```
            <p>通过原型方式，检测A是否继承自Object.prototype或Array.prototype来识别</p>
            ```
            Array.prototype.isPrototypeOf({}) // false
            Array.prototype.isPrototypeOf([]) // true
            Object.prototype.isPrototypeOf({}) // true
            Object.prototype.isPrototypeOf([]) // false
            ```
            <p>通过constructor属性来区别</p>
            ```
            [].constructor // ƒ Array() { [native code] }
            ({}).constructor // ƒ Object() { [native code] }
            ```
        </div>
    </li>
    <li>判断是否为空空对象？
        <div style="margin-top:10px;">
          <p>通过Object.keys()来区别</p>
          ```
          const a = {}
          Object.keys(a).length // 是否为0
          ```
        </div>
    </li>
    <li>数组的迭代方法有哪些？
        <div>
            参考：http://www.imooc.com/article/277859
        </div>
    </li>
    <li>遍历对象的方式有哪些？
        <div>
            参考：https://www.cnblogs.com/wangdashi/p/9606182.html
        </div>
    </li>
    <li>字符串转化
        <div style="margin-top:10px;">
          <p>'abcd'变为{d:{c:{b:"a"}}}</p>
          ```
          const str = 'abcd'
          const newObj = str.split('').reduce(function(prev, next){
              const obj = {}
              obj[next]=prev
              return obj
          })
          console.log(newObj) //{d:{c:{b:"a"}}}
          ```
        </div>
    </li>
    <li>实现继承的几种方式：
        <div style="word-wrap:break-word;">
        参考：<a href="https://sunhui-blog.github.io/2019/06/09/JavaScript/JavaScript%E5%AE%9E%E7%8E%B0%E7%BB%A7%E6%89%BF%E7%9A%84%E5%87%A0%E7%A7%8D%E6%96%B9%E5%BC%8F/" target="_blank">实现继承的几种方式</a>
        </div>
    </li>
    <li>闭包:
        <div>
        ```
        ```
        </div>
    </li>
    <li>严格模式：
        <ul style="margin: 10px 10px;">
          <li>严格模式下对保留字增加限制；</li>
          <li>给未声明的变量赋值在严格模式下会导致抛出ReferenceError错误；</li>
          <li>在严格模式下不能定义名为eval或arguments的变量，否则会导致语法错误；</li>
        </ul>
    </li>
    <li>数据类型：
        <div style="margin-top:10px;">
          Undefined、Null、Object、Number、String、Boolean
        </div>
    </li>
    <li>对象转数组:
        <div>
        ```
        var obj = {
          a: 1,
          b: 2,
          c: 3
        }
        var arr = []
        for (let i in obj) {
          let o = {};
          o[i] = obj[i];
          arr.push(o)
        }
        console.log(arr) // [{a: 1}, {b: 2}, {c: 3}]
        ```
        </div>
    </li>
    <li>数组转对象：
      <div>
        ```
        
        ```
      </div>
    </li>
</ol>

<p style="margin-top: 60px;color: #666;font-size: 1.2rem;">#未完待续#</p>