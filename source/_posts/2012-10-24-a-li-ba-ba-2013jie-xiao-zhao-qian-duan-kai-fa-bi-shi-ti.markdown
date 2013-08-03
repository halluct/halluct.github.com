---
layout: post
title: "阿里巴巴2013届校招前端开发笔试题"
date: 2012-10-24 20:33
comments: true
categories: 前端
---

###阿里巴巴2013届校招前端开发笔试题

OCT 24TH, 2012

1. 指出下面代码的问题，并写出优化后的代码

```
<!--start-->
 <div style="font-size:16px;font-weight:bold">标题文本</div>
 <div style="font-size:12px;">这是一段文本<span style="background-color: blue;color:white">关键字</span></div>
<!--end-->
```

html:

```
<h3>标题文本</h3>
<p>这是一段文本<span>关键字</span></p>
```

css:

```
p{
	font-size: 12px;
}
p span{
    background: blue;
    color: white;
}
```
可能会问的：

（1）为何要用h3标签？

  首先，h标签是标明标题的符合规范的最佳选择，而且它对页面seo也有帮助。选择h3是因为在没有上下文的条件下，我觉得该标题的样式和h3的最接近，不过后来我回去查看了一下，发现如果没有特殊声明，h3标签的字体大小应该是1.17em,即 19px，所以应该选用h4或者给h3特别声明样式。

  知识点：
      - h1到h6，最大到最小的标题，在使用h标签过程中应该是完整有序没有断层的。如h1, h2, h3, h4，而不是h1, h2, h4, h5。一个结构良好的网页，h标签可以组织起一个网页的大纲。strong标签是起到强调局部的意思，同样可以强调一个架构关系。
      - h标签对于关键字排名有帮助，只是对于网页优化，对于蜘蛛手抓取起了帮助。但是并不是h标签用的越多越好，用多了反而会降低页面的权值，而且搜索引擎可能会认为你作假。
      - 标签权重为title>h1>h2>.....>h6>strong。
  使用技巧：
      - h1标签一个页面最多使用一个，用多了会冲淡主题，而且易被搜索引擎当作欺骗；
      - 灵活使用h标签及strong标签，使得网页有个好的布局及架构，条理清晰；
      - 头部logo一个h3标签，下面权重一样大的栏目标题，用一个h3标签。如果想体现页面主题的栏目，可以用一个h2标签。如果有一栏权值在网页中很重。页脚用一个h3标签。没有使用h1标签是想让title标签起决定作用，而不让h1减少title标签的作用。
（2）为何将结构和表现分离？有何好处？
  - 去掉或样式丢失的时候也能让页面呈现清晰的结构
  - 数据的多样显示。通过不同的样式表适应不同的设备，做到内容与设备无关
  - 保持整个站点的视觉一致性变得简单，修改样式表就可以轻松改版
  - 由于结构清晰，数据的集成、更新和处理更加方便灵活
  - 更有意义的搜索，搜索引擎的爬虫也依赖于标记来确定各个关键字的权重
  - 便于团队开发和维护
（3）还有什么可以改进的地方没？
  关键字用strong标签，strong标签是起到强调局部的意思。
  
2. 使页面上的链接全部在新窗口中打开的最快捷方式是？

 		<base target="_blank" />
 		
3. css选择器有哪些？优先级分别是？

元素选择器，类选择器，通配符选择器，属性选择器，后代选择器，伪类选择器，子对象选择器，伪元素选择器。

（1）改进

 答题时缺少一个伪元素选择器
 - 优先级是!important最高（重要声明分为一组，其特殊性冲突会在重要声明内部解决，而不会与非重要声明想混。若重要声明和非重要声明冲突，则重要声明总是胜出）。
 - 内联样式特殊性1,0,0,0
 - 各个ID属性值，加0,1,0,0
 - 各个类属性值、属性选择或伪类，加0,0,1,0
 - 各个元素和伪元素，加0,0,0,1
 - 通配符选择器的特殊性为0,0,0,0，高于根本没有特殊性
 - 结合符于根本没有特殊性

4. 用javascript实现对象的复制（要求：b=a.clone(); b的改变不影响到a）
（1）定义clone函数

```
function clone(myObj){
	if(typeof(myObj) != 'object') return myObj;
   	if(myObj == null) return myObj;

   	var myNewObj = new Object();

   	for(var i in myObj)
     	myNewObj[i] = clone(myObj[i]);

   	return myNewObj;
}
```

（2）通过prototype扩展

```
 Object.prototype.clone = function(){
     var objClone;
     if ( this.constructor == Object ) objClone = new this.constructor(); 
     else objClone = new this.constructor(this.valueOf()); 
     for ( var key in this )
     {
         if ( objClone[key] != this[key] )
         { 
             if ( typeof(this[key]) == 'object' )
             { 
                 objClone[key] = this[key].clone();
             }
             else
             {
                 objClone[key] = this[key];
             }
         }
     }
     objClone.toString = this.toString;
     objClone.valueOf = this.valueOf;
     return objClone; 
 }
```

 Javascript中的对象赋值与Java中一样，都为引用传递。就是说，在把一个对象赋值给一个变量时，那么这个变量所指向的仍旧是原来对象的地址。
 一个对象A，在某一时刻A中已经包含了一些有效值，此时可能会需要一个和A完全相同的新对象B，并且此后对B的任何改动都不会影响到A中的值。也就是说，A与B是两个独立的对象，但B的初始值是由A对象确定的。
 - 浅复制（影子克隆）：只复制对象的基本类型，对象类型仍属于原来的引用。
 - 深复制（深度克隆）：不仅复制对象的基本类，同时也复制对象中的对象。
基类People，子类Student，完善其属性和方法

```
 function People() {
     this.species = "people";
 }

 function Student(name, age) {
     this.name = name;
     this.age = age;
 }
```

(1)用apply(call)继承

```
 function Student(name, age) {
     People.apply(this, arguments);
     this.name = name;
     this.age = age;
 }

 var summer = new Student('summer', 21);
 console.log(summer.species);    //people
```

(2)用prototype继承

```
 Student.prototype = new People();
 Student.prototype.constructor = Student;
 var summer = new Student('summer', 21);
 console.log(summer.species);    //people
```

(3)封装函数

```
 function extend(Child, Parent) {
     var D = function() {};
     D.prototype = Parent.prototype;
     Child.prototype = new D();
     Child.prototype.constructor = Child;
 }

 extend(Student, People);
 var summer = new Student('summer', 21);
 console.log(summer.species);    //people
 console.log(People.prototype.constructor);  //People
```

5. 用html，css实现以下布局（淘宝购物车内的商品件数那块），并用js实现其功能（1-28件）
支付宝验证手机号部分的html和js（手机号是以1开头的11位数字）
 `var reNumber = /^1\d{10}/;`
 
6. 谈谈你对网页性能的看法？优化网页性能的措施有哪些？