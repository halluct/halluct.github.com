---
layout: post
title: "ubuntu下搭建LAMP环境后修改/var/www文件夹权限"
date: 2012-04-05 22:42
comments: true
categories: ubuntu
---

LAMP环境搭好后默认的文件目录为/var/www，而该文件夹需要权限访问。可在Terminal中输入以下命令：

```
$sudo passwd root  #设置root密码
$su root  #进入最高权限用户root模式
$chown username /var/www  #username为你当前用户的用户名
$exit
```