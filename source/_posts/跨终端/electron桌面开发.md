---
title: electron桌面开发
date: 2021-11-05 00:04:34
tags:
---
<p>Electron开发桌面应用，日常练习。</p>
<!-- more -->
<ol>
  <li>
    <p>Electron开发环境的搭建</p>
    <div style="margin-bottom: 10px;">
      <p>前置环境： npm、node</p>
      <p>创建空文件夹： practice-electron</p>
      <p>在文件夹目录，在终端中输入安装命令： npm install electron --save-dev</p>
      <p>查看electron版本： npx electron -v</p>
    </div>
  </li>
  <li>
    <p>Electron第一个Hello world程序</p>
    <div>
      <p>在项目的根目录中新建一个index.html文件：</p>
      ```
        <!DOCTYPE html>
        <html lang="en">
        <head>
          <meta charset="UTF-8">
          <meta name="viewport" content="width=device-width, idivnitial-scale=1.0">
          <title>Document</title>
        </head>
        <body>
          Hello World!
        </body>
        </html>
      ```
    </div>
  </li>
  <li>
    <p>新建main.js文件</p>
    ```
    // 引入electron模块
    var electron = require('electron')

    // 创建electron引用
    var app = electron.app

    // 创建窗口引用
    var BrowserWindow = electron.BrowserWindow;

    // 声明要打开的主窗口
    var mainWindow = null ;

    app.on('ready',()=>{
      // 设置打开的窗口大小
      mainWindow = new BrowserWindow({
        width: 500,
        height: 500,
        webPreferences: {
          nodeIntegration:true
        }
      })

      // 加载那个页面
      mainWindow.loadFile('index.html')

      // 监听关闭事件，把主窗口设置为null
      mainWindow.on('closed',()=>{
        mainWindow = null
      })
    })
    ```
  </li>
  <li>
    <p>创建package.json文件, 写完后直接使用npm init来初始化package.json文件，文件生成后如下：</p>
    ```
    {
      "name": "practice-electron",
      "version": "1.0.0",
      "description": "",
      "main": "main.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "keywords": [],
      "author": "",
      "license": "ISC"
    }
    ```
  </li>
  <li>
    <p>查看效果：</p>
    ```
    electron .
    ```
  </li>
</ol>

<h4 style="margin-top:50px;"><附></h4>
参考：
<ol>
  <li>Electron开发桌面应用：https://zhuanlan.zhihu.com/p/151006366</li>
</ol>
