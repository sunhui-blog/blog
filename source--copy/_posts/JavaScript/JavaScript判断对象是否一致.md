---
title: JavaScript判断对象是否一致
date: 2019-09-04 04:33:31
tags:
categories: JavaScript
---
<p>总结一下这个问题！可用于判断用户在form表单编辑页面是否变更了数据内容。减少编辑form接口请求~当然这个比对的意义随需求变化而变化。</p>
<style type="text/css">
.red{color:red;}
</style>

<!-- more -->

<p>方法：Object.keys ＋ some()(或者every())</p>

<ol>
  <li>Array.prototype.some()
    <div>some() 为数组中的每一个元素执行一次 callback 函数，直到找到一个使得 callback 返回一个“真值”（即可转换为布尔值 true 的值）。<span class="red">有一个为"真"，则返回真</span>
    ```
    const a = {age: 1, name: 'a'}
    const b = {age: 1, name: 'b'}
    function isObjEqual (objA, objB) {
      return Object.keys(objA).some(key => { return objA[key] !== objB[key] })
    }
    isObjEqual(a, b) // true:不一致 false:一致 
    ```
    </div>
  </li>
  <li>Array.prototype.every()
    <div>every 方法为数组中的每个元素执行一次 callback 函数，直到它找到一个会使 callback 返回 false 的元素。如果发现了一个这样的元素，every 方法将会立即返回 false。否则，callback 为每一个元素返回 true，every 就会返回 true。<span class="red">有一个为"假"，则返回假</span>
    ```
    const a = {age: 1, name: 'a'}
    const b = {age: 1, name: 'b'}
    function isObjEqual (objA, objB) {
      return Object.keys(objA).every(key => { return objA[key] === objB[key] })
    }
    isObjEqual(a, b) // true:一致 false:不一致 
    ```
    </div>
  </li>
</ol>


<h4 style="margin-top: 40px;"><附></h4>
<ol>
  <li>此处也可用for...in来实现</li>
  <li>循环中断参考：https://juejin.im/entry/5884717a1b69e6005919f0d3</li>
</ol>