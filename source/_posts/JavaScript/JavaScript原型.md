---
title: JavaScript原型
date: 2019-10-28 00:33:25
tags:
categories: 9.JavaScript
---
<style type="text/css">
.l30{text-indent:30px;}
</style>

<p>加深此处理解。</p>

<!-- more -->

以下内容出自《你不知道的JavaScript》上卷、《JavaScript高级程序设计》。

<p class="l30">“类是基于复制的，原型是基于关联的”</p>

<p class="l30">在面向类的语言中，类可以被复制(或者说实例化)多次，就像用模具制作东西一样。之所以会这样是因为实例化(或者继承)一个类就意味着“把类的行为复制到物理对象中”，对于每一个新实例来说都会重复这个过程。</p>

<p class="l30">JavaScript中并没有类似的复制机制。你不能创建一个类的多个实例，只能创建多个对象，它们[[Prototype]]关联的是同一个对象。但是在默认情况下并不会进行复制，因此这些对象之间并不会完全失去联系，它们是相互关联的。</p>

<p class="l30">利用函数的特殊特性：所有的函数(如函数A)都会拥有一个名为prototype的公有且不可枚举的属性，它会指向另一个对象，这个对象通常被称为A的原型。我们通过A.prototype来访问它。</p>

```
function A() {}

const a = new A(); // new 并没有直接关联，间接关联(意外的副作用)

Object.getPrototypeOf(a) === A.prototype // true
```

<p class="l30">Object.create(...): 创建一个对象并把这个对象的[[Prototype]]关联到指定的对象。缺点:需要创建一个新对象然后把旧对象抛弃掉，不能直接修改已有的默认对象。</p>

<p class="l30">e.g.把A.prototype关联到B.prototype的方法：</p>

```
// ES6之前需要抛弃默认的A.prototype
A.prototype = Object.create(B.prototype)

// ES6开始可以直接修改现有的B.prototype
Object.setPrototypeOf(A.prototype, B.prototype)

```
<p class="l30">Object.create(null)会创建一个拥有空(null)[[Prototype]]链接的对象，这个对象无法进行委托。由于这个对象没有原型链，instanceof操作符无法进行判断(始终为false)，这些特殊的空[[Prototype]]对象通常被称作"字典"，它们完全不会受到原型链的干扰，因此非常适合用来存储数据。</p>

<h4 style="margin-top:50px;"><附></h4>
<ol>
    <li>函数的特殊特性？
    </li>
</ol>

#未完待续#
