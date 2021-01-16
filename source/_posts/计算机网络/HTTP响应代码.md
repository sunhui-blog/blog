---
title: HTTP响应代码
date: 2021-01-09 21:30:27
tags: 网络知识
categories: 计算机网络
---

<p>简述前端常见HTTP响应代码对应网络状态。</p>

<!-- more -->

<ol>
  <li>100-199：信息性状态码，通常和url协议相关，表示接收的请求正在处理</il>
  <li>200-299：成功状态码，用于表示请求正常处理完毕</il>
  <li>300-399：重定向状态码，表示要么有缓存，要么做了重定向用于跳转</il>
  <li>400-499：客户端错误状态码，表示服务器无法处理请求</il>
  <li>500-599：服务器错误状态码，表示服务器处理请求出错</il>
</ol>

<h5 style="margin-top: 40px;">常见code码：</h5>
<ol>
  <li>101 Switching Protocol: 该代码是响应客户端的 Upgrade 标头发送的，并且指示服务器也正在切换的协议。</li>
  <li>200 OK: 请求成功。</li>
  <li>301 Moved Permanently: 永久重定向，表示请求的资源已被分配了新的 URI，以后应使用资源现在所指的 URI。</li>
  <li>302 Found: 临时重定向，表示资源仍然可以访问，这个重定向只是临时地从旧地址 A 跳转到地址 B。</li>
  <li>304 Not Modified: 协商缓存。</li>
  <li>400 Bad Request: 请求参数有误。</li>
  <li>403 Forbidden: 服务器已经理解请求，但是拒绝执行它。</li>
  <li>404 Not Found: 请求失败。</li>
  <li>500 Internal Server Error: 服务器遇到了不知道如何处理的情况。</li>
</ol>

<h5 style="margin-top: 40px;">Protocol</h5>
<ol>
  <li>https</li>
  <li>wss</li>
  <li>blob</li>
</ol>

<h4 style="margin-top:50px;"><附></h4>
<ol>参考：
  <li>https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status</li>
</ol>
