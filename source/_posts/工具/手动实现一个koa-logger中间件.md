---
title: 手动实现一个koa-logger中间件
date: 2021-01-19 21:04:46
tags: 工具
categories: 工具
---

<p>koa2对async/await支持。</p>

<style>
.red {
  color: red;
}
</style>

<!-- more -->

<ol>
  <li>
    <p>编写koa-logger.js文件</p>
    ```
      module.exports = async (ctx, next) => {
        const start = new Date().getTime()
        // 中间件异步处理
        await next()
        const end = new Date().getTime()
        // 打印出耗时还有长度
        console.log(ctx.request.url, end - start, ctx.body.length, 'log')
      }
    ```
  </li>
  <li>
    <p>注册koa-logger中间件</p>
    ```
    const Koa = require('koa')

    const app = new Koa()

    const logger = require('./koa-logger')

    // 注册中间件
    app.use(logger)
    ```
  </li>
</ol>

<ul>
  <li>koa2核心原理：compose通过递归对中间件队列进行了<span class="red">反序遍历</span></li>
</ul>


<h4 style="margin-top: 40px;"><附></h4>
<ol>
  <li>Node.js中间件模式: https://juejin.cn/post/6844903619209199624</li>
</ol>
