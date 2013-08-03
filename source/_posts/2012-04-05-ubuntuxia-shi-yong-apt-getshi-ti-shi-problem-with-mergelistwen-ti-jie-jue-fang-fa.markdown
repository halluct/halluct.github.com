---
layout: post
title: "Ubuntu下使用apt-get时提示Problem With MergeList问题解决方法"
date: 2012-04-05 22:27
comments: true
categories: ubuntu
---

下午安装软件包时遇到一个小问题，使用apt-get安装时提示错误，关键字为“Problem with MergeList”，应该是源的问题。上网搜了一下，很快就找到答案了。方法如下：

```
$sudo rm /var/lib/apt/lists/* -vf  #删除mergelist
$sudo apt-get update  #更新源
```