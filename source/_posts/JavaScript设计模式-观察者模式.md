---
title: JavaScript设计模式-观察者模式
date: 2019-05-24 23:31:27
tags: 设计模式
categories: 设计模式
thumbnail: img/desert.jpg
---
<p style="text-indent:30px">概念：观察者模式也称发布者-订阅者模式（publisher-subscriber pattern)，用于让对象对事件进行监听以便对其作出响应。</p>

<!-- more -->

<p style="text-indent:30px">观察者模式可谓无处不在，无论是自行构建，还是用框架中封装好的，都极其常见。深入的理解和学习显得尤为重要。当出现问题时，也可更快速准确的定位问题的根源。</p>

<p style="text-indent:30px">为了更深刻的理解观察者模式，举个例子。在报纸行业中，发布和订阅的顺利进行，依赖于两个角色，报社和订阅者。报社在出版报纸后，将报纸投递至订阅者。订阅者可订阅多家报刊，报刊可投递给多个订阅者，则这是个多对多的关系。投递的方式可为两种：推和拉。订阅者可订阅和退订。报社可“送”也可“订阅者取”。</p>

<p style="text-indent:30px">此例子来源《JavaScript设计模式》。注：网上普遍认为该模式为“一对多”的关系，此书解释为“多对多”的对应关系。我认为也更为恰当一些。</p>

<p style="text-indent:30px">目前，前端实践上，主流框架AngularJs、Vue、React、BackBone等中均广泛应用。RxJS更是使用Observables的响应式编程的库.观察者模式能够松耦合，在模块化设计当中扮演着非常重要的角色。MVC、MVVM模式中最底层的就是观察者模式。</p>

<p style="text-indent:30px">此处举个简单常用的例子，组件间的传值。</p>

<p style="text-indent:30px">实现方式：为了便捷简明的说明此模式，此处举例为“一对一”的对应关系，同时借用jquery框架。用jquery实现类似vue、Angular的$emit(事件触发),$on(事件绑定)的设计。<p>


``` 
// 发布者
function Publisher() {
    var self = this;
    self.dispatcher = $({});
}

// 触发send操作时，发布信息
Publisher.prototype.send = function (){
    var self = this
    self.dispatcher.trigger("sendMessage", ["Yes"]);
}

// 订阅者
var subscribe = new Publisher()

// 订阅者获取信息
subscribe.dispatcher.on('sendMessage',function(data){
    console.log(data);  // 输出“Yes”
});

// 发送信息触发
subscribe.send();


```
<h4>注：</h4>
<ol>
    <li>部分观点认为观察者模式and发布者-订阅者模式是两种不同的模式。待考证</li>
    <li>复杂业务场景“一对多”、“多对一”、“多对多”模式。待补充</li>
</ol>

<p style="margin-top: 60px;color: #666;font-size: 1.2rem;">#未完待续#</p>