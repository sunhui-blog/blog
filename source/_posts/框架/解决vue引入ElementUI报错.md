---
title: 解决vue引入ElementUI报错
date: 2021-03-08 11:47:08
tags:
---
<p>报错信息ERROR in ./node_modules/element-ui/lib/theme-chalk/fonts/element-icons.ttf</p>

<!--more-->

<p>解决方式：在webpack.config.js的module/rules中加上</p>

```
{
  test: /\.(eot|svg|ttf|woff|woff2)(\?\S*)?$/,
  loader: 'file-loader'
}
```
