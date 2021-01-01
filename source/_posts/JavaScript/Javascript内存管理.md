---
title: Javascript内存管理
date: 2019-08-29 00:00:05
tags: 编程语言
categories: JavaScript
---
<p>总结Javascript内存相关知识，加深学习和理解。</p>
<style type="text/css">
.red{color:red;}
</style>

<!-- more -->

<h5>回顾基础知识:</h5>
<ol>
  <li>基本数据类型：Undefined、Null、Boolean、Number、String、<span class="red">Symbol</span></li>
  <li>引用数据类型：Function、Array、Object</li>
</ol>

<h5>重点:</h5>
<ol>
  <li>基本类型值在内存中占据固定大小的空间，因此被保存在<a href="#index">栈内存</a>中。</li>
  <li>从一个变量向另一个变量复制基本类型的值，会创建这个值的一个<span class="red">副本</span>。</li>
  <li>引用类型的值是对象，保存在<a href="#index">堆内存</a>中。</li>
  <li>包含引用类型值的变量实际上包含的并不是对象本身，而是一个指向该对象的<span class="red">指针</span>。</li>
  <li>从一个变量向另一个变量复制引用类型的值，复制的其实是指针，因此两个变量最终都指向同一个对象。</li>
  <li>确定一个值是哪种基本类型可以使用typeof操作符，而确定一个值是哪种引用类型可以使用instanceof操作符</li>
</ol>

<h5>优化内存:</h5>
<ol>
  <li>为执行中的代码只保存必要的数组。一单数据不再有用，最好通过将其值设置为null来释放其引用－－<span class="red">解除引用</span>。适用于大多数全局变量和全局对象的属性。局部变量会在离开执行环境时自动被解除引用。
  ```
  let obj = new dialog()
  obj = null
  ```
  注：解除引用的真正作用是让值脱离执行环境，以便垃圾收集器下次运行时将其回收。
  </li>
  <li>浏览器中提供window全局方法来手动启用垃圾回收机制，但不建议使用。</li>
</ol>


<h5>补充</h5>
<h5 name="index">堆内存(heap)和栈内存(stack)区别:</h5>
<ol>
  <li>在栈内存的数据的大小及生存周期是必须确定的、其优点是寄存速度快、栈数据可以共享、缺点是数据固定、不够灵活</li>
  <li>只要是用new()来新建对象的，都会在堆中创建，而且其字符串是单独存值的，即使与栈中的数据相同，也不会与栈中的数据共享</li>
</ol>

<h5>思考&扩展</h5>
<ol>
  <li>副本？</li>
  <li>指针？</li>
  <li>堆栈？</li>
  <li>变量生命周期？</li>
  <li>传值还是引用？</li>
  <li>深浅拷贝</li>
</ol>

#未完待续#