---
title: npm包打包发布
date: 2021-08-08 00:39:15
tags:
categories: 工程化
---

<p>记录封装一个npm包，发布与下载过程。</p>

<!-- more -->

<p>默认已有https://www.npmjs.com/ 账号</p>
<ol>
  <li>
    <p>创建本地文件夹，并`npm init`初始化包信息；</p>
    ```
    mkdir test // 创建test文件夹
    npm init // 完善包文件信息
    ```
  </li>
  <li>
    <p>登录npm:</p>
    ```
    npm login 或 npm adduser(adduser为login别名)

    // 输入Username、Password、Email
    // 使用whoami命令将会显示用户名
    ```

  </li>
  <li>
    <p>发布npm包:</p>
    ```
    npm publish
    ```
  </li>
  <li>
    <p>npm包更新:</p>
    ```
    npm update // 注：此处需要更新package.json文件中的版本号version
    ```
  </li>
  <li>
    <p>撤销发布npm包:</p>
    ```
     npm unpublish <package>@0.0.1 // 撤销具体某一版本发布
     npm unpublish <package> --force // 撤销整个包
    ```
  </li>
  <li>
    <p>退出登录npm:</p>
    ```
    npm logout
    ```
  </li>
</ol>

<p>npm包发布使用:</p>
<ol>
  <li>
    <p>npm包安装：</p>
    ```
    npm install <package>
    ```
  </li>
</ol>
