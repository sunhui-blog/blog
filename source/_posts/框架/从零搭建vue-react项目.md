---
title: 从零搭建vue/react项目
date: 2021-01-16 17:24:01
tags: 框架
categories: 框架
---

不借助vue-cil脚手架，基于webpack+vue搭建开发环境

github:
<ul>
  <li>vue-demo地址：
    <a href="https://github.com/sunhui-blog/vue-demo" target="_blank">
      https://github.com/sunhui-blog/vue-demo
    </a>
  </li>
  <li>react-demo地址：
    <a href="https://github.com/sunhui-blog/react-demo" target="_blank">
      https://github.com/sunhui-blog/react-demo
    </a>
  </li>
</ul>

<!--more-->

<h4 style="margin-top:50px;">具体步骤:</h4>
<ol>
  <li>project初始化：npm init生成package.json</li>
  <li>安装依赖包：npm i webpack vue vue-loader</li>
  <li>实例化vue：index.js文件中实例化vue</li>
  <li>配置webpack.config.js：plugins和loader及开发环境</li>
</ol>

<h4 style="margin-top:50px;"><附></h4>
<p>
  参考：
  <a href="https://blog.csdn.net/u013368397/article/details/86467581">
    不使用cli脚手架搭建vue项目工程(webpack简单配置)
  </a>
</p>
遇到的问题：
<ol>
  <li>
    <p>vue+webpack 执行npm run dev后访问首页显示目录结构的原因</p>
    <p>参考解决：<a href="https://blog.csdn.net/rpf1234/article/details/103205173" target="_blank">https://blog.csdn.net/rpf1234/article/details/103205173</a></p>
  </li>
  <li>
    <p>webpack-dev-server启动报错Error: Cannot find module ‘webpack-cli/bin/config-yargs‘</p>
    <p>参考解决：
      <a href="https://juejin.cn/post/6883375553395720199" target="_blank">
        https://juejin.cn/post/6883375553395720199
      </a>
    </p>
  </li>
</ol>
