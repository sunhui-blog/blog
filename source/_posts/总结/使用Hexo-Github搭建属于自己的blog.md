---
title: 使用Hexo+Github搭建属于自己的blog
date: 2019-02-18 22:24:22
toc: true
categories: 总结
tags:
---
<p>一直想搭建属于自己的blog，经过查看多方资料比较后，采用Hexo+Github搭建一套免费的blog.(当然你也可以买域名租服务器来实现)</p>
<!-- more -->
<p>网上的教程很多，就不罗列了，感兴趣的小伙伴可以多方查看参考。</p>

<p>主要参考文章有：</p>
<ul>
    <li><a href="https://hexo.io/" target="_blank">hexo官网</a></li>
    <li><a href="https://www.cnblogs.com/fengxiongZz/p/7707219.html"  target="_blank">使用Hexo+Github一步步搭建属于自己的博客（基础）</a></li>
</ul>

<p>优化</p>
<ul>
    <li>热更新：https://github.com/hexojs/hexo-browsersync</li>
</ul>

<h4 style="margin-top:50px;"><附></h4>
<h4>常用命令</h4>
<ol>
    <li>hexo server #Hexo 会监视文件变动并自动更新，无须重启服务器。</li>
    <li>hexo clean #清除缓存 网页正常情况下可以忽略此条命令</li>
    <li>hexo new "postName" #新建文章</li>
    <li>hexo d -g #生成部署git</li>
</ol>

<h4>配置文件</h4>
<ol>
    <li>config.xml里的per_page，这个设置成0就全都没有分页了。</li>
</ol>

<h4>Questions</h4>
<ol>
    <li>
        <p>解决hexo渲染的html页面中有br的问题<p>
        <p>只需要在_config.yml里增加如下配置即可</p>
        ```
        marked:
            breaks: false
        ```
        <p>参考：http://1900.live/rep-hexo-marked/<p>
    </li>
    <li>
        <p>md文件插入代码片段</p>
        <p>参考：https://www.jianshu.com/p/366ff564a8f2</p>
    </li>
    <li>
        <p>后期完善(评论、站点统计)参考：https://segmentfault.com/a/1190000016267344</p>
    </li>
    <li>
      <p>node版本：12.14.1</p>
    </li>
</ol>

<div style="margin-bottom:50px"></div>
