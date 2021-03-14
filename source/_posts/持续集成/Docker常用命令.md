---
title: Docker常用命令
date: 2021-03-04 13:43:20
tags: 持续集成
categories: 持续集成
---

<!-- more -->

<ol>
  <li>
    <p>查看容器的运行状态</p>
    ```
    docker ps
    ```
  </li>
  <li>
    <p>与容器进行交互</p>
    ```
    docker exec -t -i <容器 ID> /bin/bash
    ```
  </li>
  <li>
    <p>停止一个容器</p>
    ```
    docker stop <容器 ID>
    ```
  </li>
  <li>
    <p>重启一个容器</p>
    ```
    docker restart <容器 ID>
    ```
  </li>
</ol>


<h4 style="margin-top:50px;"><附></h4>
<ol>参考：
  <li>https://www.jianshu.com/p/dbc59702f0dd</li>
</ol>
