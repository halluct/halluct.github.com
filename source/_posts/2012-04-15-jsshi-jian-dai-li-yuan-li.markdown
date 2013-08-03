---
layout: post
title: "Js事件代理原理"
date: 2012-04-15 22:13
comments: true
categories: 前端
---
周六参加蘑菇街笔试，很不幸的考得一团糟。其中前端附加题的第二题是“简述js中事件代理的原理”，我看到就蒙了。也怪自己，平时写代码从来不怎么关注原理，这也算是次惩罚吧。以后得多关注原理性的东西了。

回来之后立马查资料

什么时候需要用到事件代理

当我们需要同时绑定多个对象时。

事件代理的实现原理

利用浏览器中事件的冒泡（event bubbling）和事件源（target || srcElement）。

在javascript中实现事件代理

```
ul.onclick = function{
var e = e || window.event;
clickedLi = e.srcElement || e.target;
//do something
}
```

在jQuery中实现事件代理

```
$ul.onclick(function() {
var $clickedLi = $(e.target);
//do something
}
```

某些场景中特别适合使用事件代理，它有如下好处

需要管理的handler更少。 占用的内存更少（创建的驻留在内存中的handler少了）。 DOM元素与代码更少的绑定。 DOM变更后（如添加dom节点）无须重新绑定事件处理器。 它也有如下不足

并非所有的事件都能冒泡，如load, change, submit, focus, blur(jQuery间接的实现了focus和blur的事件代理)。 代理元素的handler管理复杂。 不好模拟用户触发事件（jQuery实现了）。