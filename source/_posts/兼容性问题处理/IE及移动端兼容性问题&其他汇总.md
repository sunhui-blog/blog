---
title: IE及移动端兼容性&其他问题汇总
date: 2019-03-06 23:30:28
toc: true
categories: 兼容性问题处理
tags:
---
<p>此篇用于总结遇到的兼容性问题，便于积累和提升</p>
<!-- more -->
<h2>css</h2>
<ol>
  <li>透明度opacity:filter:alpha(opacity=50);可支持ie8</li>
  <li>尾类::before和::after在ie8下失效</li>
  <li>图表绘制：highcharts在绘制图表时，高版本用"canvas"，ie8及低版本用"shape形状"</li>
  <li>a标签兼容性问题：
    ```
    <a href="javascript:void(0);" target="_blank"></a>
    ```
    firfox会新开空白页面，避免使用这种写法
  </li>
  <li>overflow:hidden会清除浮动</li>
  <li>@media可用做响应式布局。通常会用到的media type会是all 和screen，然后是print，一些网站会专门通过print类型为页面的打印格式提供更友好的界面。媒体类型支持not和only关键字，它们可以用来更方便的定位某个媒体设备。
    <div>详细了解：https://www.cnblogs.com/august-8/p/4537685.html</div>
  </li>
  <li>由于历史原因及某些特殊原因，需通过CSS清除定位position:
    ```
    position: static;
    ```
  </li>
</ol>
<h2>javascript</h2>
<ol>
  <li>字符串比较大小会产生失真;</li>
  <li>js在比较数字的时候一定不要直接比较。而是要转换，因为JS里面的是var 这种是弱的类型，默认是string，所有比较的时候会出现错误。js里面有两种转换的，parseFloat和parseInt。</li>
  <li>number变字符串: ''+123 左侧加空字符串</li>
  <li>向上取整：Math.ceil() 向下取整：Math.floor()</li>
  <li>JS去掉字符串中的空格：
    <p>去除所有空格: 
    ```
    str = str.replace(/\s+/g,"");
    ```
    </p>
    <p>去除两头空格:
    ```
    str = str.replace(/^\s+|\s+$/g,"");
    ```
    </p>
    <p>去除左空格：
    ```
    str = str.replace( /^\s/, '');
    ```
    </p>
    <p>去除右空格：
    ```
    str = str.replace(/(\s$)/g, "");
    ```
    </p>
  </li>
  <li>页面种cookie：
    ```
     document.cookie = 'userId=123;test=456'
    ```
  </li>
  <li>for循环性能比对：
    <p>for>forEach>for...in</p>
    <p>性能优化：</p>
    <ol>
        <li>break/continue语句，适时运用</li>
        <li>缓存变量（如数组长度）</li>
    </ol>
  </li>
</ol>
<h2>jquery</h2>
<ol>
  <li>实时监听input输入框值变化:
      ```
      $("#input1").bind("input propertychange",function(event){
        console.log($("#input1").val())
      });
      ```
  </li>
</ol>
<h2>hybrid內嵌h5</h2>
<ol>
  <li>Android、IOS的webview均可通过Chrome来仿真，调试兼容性。（html2canvas组件调试在真机测试分享到微信朋友圈时，存在分享页乱掉问题，问题原因定位时，未能及时排除浏览器兼容性问题，造成各端反复定位问题的时间浪费。此处埋个钩子，需要深入学习了解）</li>
  <li>多页面跳转时，注意路径问题。（返回路径到指定页面）</li>
  <li>多页面跳转时，涉及表单业务时，需考虑页面数据存储。例如：vue框架下可选用vux做数据存储。</li>
  <li>for...in慎用：在ios低版本下会循环两次。</li>
  <li>textArea/input键盘收缩：在iphone7及以上会出现键盘关闭后，页面不下拉的情况。此时需用blur事件（失去焦点时触发），window.scroll(0,0)做置顶，将页面手动下拉。</li>
  <li>a标签中慎用target="_blank"打开新窗口，会导致链接看起来跳转了两次。</li>
</ol>
<h2>微信公众号</h2>
<ol>
  <li>页面开发需经appid身份认证之后，在微信开发者工具中进行开发。</li>
</ol>
<h2>Commit message 和 Change log 编写指南</h2>
<ol>
  <li>http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html</li>
</ol>

<p style="margin-top: 60px;color: #666;font-size: 1.2rem;">#未完待续#</p>