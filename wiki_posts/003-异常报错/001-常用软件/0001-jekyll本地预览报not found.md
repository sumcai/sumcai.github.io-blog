---
layout: post
title: Jekyll新增文章本地预览时报 not found
author: sumcai
header-style: text
article: false
tags: 
  - website
date: 2021-01-08 15:23:40
categories: 
  - 工具使用
  - 建站
url: /other/jekyllerror/
---

# Jekyll新增文章本地预览时报 not found

## <i class="fa fa-question-circle"></i> 问题描述
使用jekyll博客，本地新增了一篇文章，`jekyll server`启动本地服务预览时，文章列表里能显示，点击进去时报错not found，但_site文件夹下存在对应文件。

![](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/e551b6a16e8a18ad3b6050b40e64a733.png)

## <i class="fa fa-bullseye"></i> 查找原因
编码格式的问题，导致server无法正确找到对应的文章

## <i class="fa fa-check-circle"></i> 解决方法
找到Ruby安装目录下的`D:/Ruby27-x64/lib/ruby/2.7.0/webrick/httpservlet/filehandler.rb`，按如下图示修改内容

此处修改`path = req.path_info.dup.force_encoding("UTF-8")`
![](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/275b2f7bc2d87d8f43dea4c903d2cd08.png)

此处新增`base.force_encoding("UTF-8")`
![](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/5daf98987e355ea3949bc0adb161063a.png)

修改保存后重新执行`jekyll server`，能正常跳转。