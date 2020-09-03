---
title: 如何手动实现form表单提交的url
date: 2019-09-04 03:41:50
tags:
categories: 总结
---
<p>这个问题比较有趣，记录一下！</p>

<!-- more -->

<p>遇到这个问题很多人的第一反应就是这不就是拼接个字符串吗？是的，没有错！</p>
<p>但当需要拼接的参数非常多时，比如是个对象，对象中的属性有十几二十个，手动一个个写“&”看起来并不那么smart~而且费时费力，容易出错，代码维护性也不高。</p>
<p>那该如何去写呢？</p>

<p>方法: Object.entries(for...in) + map</p>
```
const params = {
  a: 1,
  b: 2,
  c: 3,
  d: 4
}

const paramsString = Object.entries(params).map(item => {
  return item[0] + '=' + item[1]
}).join('&')

const url = 'https://www.google.com?' + paramsString

// output: https://www.google.com?a=1&b=2&c=3&d=4

```

<h4 style="margin-top: 40px;"><附></h4>
<ol>
  <li>Object.entries()方法返回一个给定对象自身可枚举属性的键值对数组，其排列与使用 for...in 循环遍历该对象时返回的顺序一致（区别在于 for-in 循环也枚举原型链中的属性）</li>
  <li>Object.entries()示例
  ```
  const obj = { foo: 'bar', baz: 42 };
  console.log(Object.entries(obj)); // [ ['foo', 'bar'], ['baz', 42] ]

  ```
  </li>
  <li>Object.entries()和for...in对比
    <div>Object.entries()不支持IE，其他浏览器支持性也没for...in好，故用的也比较少。for...in兼容性除ie6以下都兼容，兼容性好很多。应优先选用for...in</div>
  </li>
</ol>
