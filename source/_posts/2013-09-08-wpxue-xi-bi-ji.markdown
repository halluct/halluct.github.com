---
layout: post
title: "wp学习笔记"
date: 2013-09-08 19:20
comments: true
categories: wordpress
---
####问题：
1. query(array('post_type' => 'type_projects', 'showposts' => '-1', 'order' => 'ASC', 'orderby' => 'menu_order'))

2. get_post_meta($post_id, 'x_project_excerpt', true);

3. register_post_type  : 'supports' => array( 'title', 'editor' )


4. the_permalink ? get_permalink

5. comments_template

6. page-contact的表单
7. page 和 single page是怎么对应的

####答案：
1. 'showpost' => '-1'
2. 'x_project_excerpt'是在custome_meta.php文件里自定义的
3. 'title', 'editor'就是在dashboard里添加post时给用户提供自定义内容的输入框
4. get_permalink需要指定对应的post ID
5. 如果样式区别很大就自定义
6. contact form  7插件
7. 通过slug或id对应（slug在post_type.php中定义）


####笔记：
1. meta在functions/custom_meta.php中设置
2. post_type在function/post_type.php中设置
3. page中可以挑选一个作为默认模板
4. 页脚的版权信息要用<?php options('of_copyright') ?>替换