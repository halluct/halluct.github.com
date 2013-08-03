---
layout: post
title: "各个浏览器下对TextArea中字符解析的差别"
date: 2012-02-02 22:10
comments: true
categories: 前端
---

1. 换行符： 在textarea中“\n”和“\r\n”均可被浏览器解析为换行符，就这一点来说，各个浏览器之间并没有差异。 而当我们需要用js从textarea中取字符时，IE和opera会传入“\r\n”，而chrome、ff、safari则只传入“\n” 。 避免这种差异的方法就是用“\n”去替换掉文本域中的全部“\r\n”。这个用正则表达式很容易实现： 

```
var reNewLine = /\r\n/g; var isNewLine = textArea.value.replace(reNewLine, “\n”);
```

2. 取字符： 写好一部分功能之后，在chrome、ff、safari、opera下均通过测试，IE8下的问题也用上述方法解决了，然后就是头疼的IE7了（忽略IE6）。 IE7及以下版本，无法用string[0]这样的方法取到字符，而必须用string.charAt(2)。 后来发现所有浏览器都可以用string.charAt(2)方法取到字符，以后只要记住这个就可以了。