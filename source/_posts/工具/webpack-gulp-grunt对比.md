---
title: webpack vs gulp vs grunt对比
date: 2021-01-01 19:26:40
tags: 工具
categories: 工具
---

<!-- more -->

<p>Webpack loader和plugin的区别</p>

<ol>
  <li>webpack loader是用来加载文件的，webpack plugin是用来扩展功能的。</li>
  <li>loader主要是用来加载一个个文件的，比如它可以加载js文件并把js文件转译成低版本浏览器可以支持的js文件；也可以用来加载css文件，可以把css文件变成页面上的style标签；还可以加载图片文件，可以对文件进行优化。</li>
  <li>plugin是用来加强webpack功能的，比如HTML webpack plugin是用来生成一个html文件的；再比如mini css extract plugin是用来抽取css代码并把它变成一个css文件的。</li>
</ol>

<p>webpack基础配置：</p>
<ol>
  <li>Entry：入口，Webpack 执行构建的第一步将从 Entry 开始，可抽象成输入。</li>
  <li>Output：输出结果，在Webpack经过一系列处理并得出最终想要的代码后输出结果。</li>
  <li>Module：模块，在 Webpack里一切皆模块，一个模块对应着一个文件。Webpack会从配置的 Entry 开始递归找出所有依赖的模块。</li>
  <li>Chunk：代码块，一个 Chunk 由多个模块组合而成，用于代码合并与分割。</li>
  <li>Loader：模块转换器，用于把模块原内容按照需求转换成新内容。</li>
  <li>Plugin：扩展插件，在Webpack构建流程中的特定时机注入扩展逻辑来改变构建结果或做你想要的事情。</li>
</ol>
