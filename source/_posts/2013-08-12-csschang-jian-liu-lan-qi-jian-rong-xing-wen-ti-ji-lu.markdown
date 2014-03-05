---
layout: post
title: "css常见浏览器兼容性问题记录"
date: 2013-08-12 18:48
comments: true
categories: 前端
---

1. 元素居中：一般使用margin:auto;方法，在IE6下不起作用，需要在父元素上声明text-align:center;在居中元素上声明text-align:left;
	
2. list导航出现阶梯形状：一般浏览器下给li a添加float:left;即可，IE6下会出现阶梯状，解决方法是，给li添加display:inline;或将li float:left;
	
3. float元素双边距：解决方法是，给该元素设置display:inline;
	
4. 无法设置很小的高度：因为IE6下不能设置比默认字体高度小的高度，所以可以通过font-size:0;这种方法解决，或者设置overflow:hidden;
	
5. 溢出边界：overflow:auto;的元素内的元素超出边界的部分会溢出外元素。解决方法，给外元素设置position:relative;
	
6. min-height和min-width不起作用：解决方法，给元素设置和min-height值一样的height，再添加一个height:auto!important;
	
7. list项目间存在空白间隙：解决方法，给li加上display:inline;或给li a加上float: left;clear:left;或给li a设置高度。