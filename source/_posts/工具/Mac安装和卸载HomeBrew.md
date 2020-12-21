---
title: Mac安装和卸载HomeBrew
date: 2019-07-21 18:09:50
tags: 工具
categories: 工具
---

<a href="https://brew.sh/">Homebrew(to:official website)</a>:是一款Mac OS平台下的软件包管理工具，拥有安装、卸载、更新、查看、搜索等很多实用的功能。

<!-- more -->

<p>最近不小心动了这个，把Homebrew本地包删成了个残缺包，so 想办法重装，遇到了些许问题，记录下来。</p>

<h4>安装</h4>
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" 
```

<h4>卸载</h4>
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"
```

<h4 style="margin-top: 40px;"><附></h4>
<h4>二次安装中遇到的问题</h4>

<p style="text-indent:30px">当遇到 Error: Checksum mismatch. 类似校验不匹配的错误报错信息时:</p>
![报错信息](/img/HomeBrew/1.png)
<p>如图所示，出现这种报错信息时，直接使用控制台命令，删除已经下载的文件(红色箭头处)。</p>

<p>如：rm -rf /Users/sunhui/Library/Caches/Homebrew/portable-ruby-2.3.7.mavericks.bottle.tar.gz</p>

然后重新安装即可。
