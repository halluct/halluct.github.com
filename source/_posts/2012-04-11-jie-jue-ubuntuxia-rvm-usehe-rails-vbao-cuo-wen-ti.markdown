---
layout: post
title: "解决ubuntu下rvm Use和rails -v报错问题"
date: 2012-04-11 23:52
comments: true
categories: ubuntu
---

使用gem安装完rails之后功能都完好，但重启terminal之后再输入rails -v之后却提示“rails尚未安装”。后来又发现rvm use命令也出错，提示“rvm is not a function…”。在网上找了好久才找到解决方法。

第一次需要输入：

```
echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm" # Load RVM function' >> ~/.bash_profile
```

再重启terminal，输入：

```
source .bash_profile #之后每次重启都需要再输一遍