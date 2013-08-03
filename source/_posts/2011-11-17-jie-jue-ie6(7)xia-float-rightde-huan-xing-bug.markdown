---
layout: post
title: "解决IE6（7）下float right的换行bug"
date: 2011-11-17 13:20
comments: true
categories: 前端
---

一条title bar里包含了左边按钮和右边按钮，思路是，给li元素加float:left，再给右边元素加个div，设置float:right；

这样应该就可以了。但是问题来了，在Chrome，FF，Opera，Safari，IE8，IE9浏览器下都是正常显示的，但是IE6和IE7下都出现了换行bug。

用了很多办法在css里做调整，完全没用，后来终于被我在网上查到了！真心简单，如下： 只要将需要float:right的元素放置在其他元素前面即可，如：

```
<ul>
      <div id="right" style="float: right;">
        <li id="newer"><a href="#"><p>较新</p></a></li>
        <li id="older"><a href="#"><p>较旧</p></a></li>
      </div>
      <li id="refresh"><a href="#"><p>刷新</p></a></li>
</ul>
```
