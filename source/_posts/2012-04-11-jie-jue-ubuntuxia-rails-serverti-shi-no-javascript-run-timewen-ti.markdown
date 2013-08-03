---
layout: post
title: "解决ubuntu下rails Server提示no Javascript Run Time问题"
date: 2012-04-11 23:33
comments: true
categories: ubuntu
---
推荐方法2，简单有效。

解决方法1（其实说的不太明白）：

添加以下gem文件：

```
gem ‘execjs’, gem ‘therubyracer’
```

这里需要先

```
bundle install therubyracer
```

然后

```
bundle install
```

解决方法2：

安装nodejs:

```
$ sudo apt-cache search nodejs
```