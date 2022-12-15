---
layout: post
title: 用Github+Jekyll搭建个人博客
author: sumcai
header-style: text
article: false
tags: 
  - website
date: 2020-12-11 15:23:39
permalink: /other/jekyllblog/
categories: 
  - 工具使用
  - 建站
---

在信息爆炸的当今社会，技术发展日新月异，不时刻保持学习很快就会跟不上时代步伐。我很久之前就希望有一个自己的个人网站来收集平时看到的一些好的文章、教程，把这些零碎的信息都变成自己的收藏，当下一次需要查阅时，不至于穷死苦想在哪看过。如果有了自己的网站，加上分类和搜索，能快速查到自己想找的内容，那该多么令人兴奋呀！经过一段时间的摸索，找到了一个免费而且便捷的方式搭建个人博客，具备分类和查找功能，而且还免费、稳健可靠，那就是通过 Github/Gitee + jekyll 搭建。

# 准备工作
考虑到国内的网速问题，我们使用 Gitee 作为平台。实现过程的思路是：在本地编写jekyll网站源码，上传至Gitee，由Gitee生成并托管整个博客网站。

- [Gitee账号](https://gitee.com)
- [安装Ruby](http://www.ruby-lang.org/zh_cn/)
- [安装jekyll](https://www.cnblogs.com/mingyue5826/p/11533978.html)

## 环境部署

### 安装文件下载

我的开发环境是win7 64位，下载如下安装程序：
- [rubyinstaller-devkit-2.7.1-1-x64.exe](https://download.csdn.net/download/smcnjyddx0623/13457483?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160723504119215668841683%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fdownload.%2522%257D&request_id=160723504119215668841683&biz_id=1&utm_medium=distribute.pc_search_result.none-task-download-2~download~first_rank_v2~rank_dl_default-1-13457483.pc_v2_rank_dl_default&utm_term=rubyinstaller-devkit-2.7.1%20windows64%E4%BD%8D%E5%AE%89%E8%A3%85%E5%8C%85&spm=1018.2118.3001.4451)
  
- [DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe](https://rubyinstaller.org/downloads/archives/)

### 安装Ruby
运行安装`rubyinstaller-devkit-2.7.1-1-x64.exe`，所有的选项都勾选上，最后的MSYS2一定要安装。

`DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe`运行解压到一个单独目录，打开cmd，进入到解压目录，执行命令：

```ruby
ruby dk.rb init    #初始化
ruby dk.rb review  # 审查（非必须）
ruby dk.rb install  # 安装
gem -v  # 查看gem是否正常安装
```

### 安装jekyll

- 先切换到国内的镜像源：

    ```gem
    gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
    gem sources -l
    ```

- 安装Jekyll
  
    ```gem
    gem install jekyll
    ```

- 安装jekyll-paginate
  
    ```gem
    gem install jekyll-paginate
    jekyll -v
    ```

- 安装 Bundler
  
  ```gem
  gem install bundler
  ```

- 查看安装版本

    ```gem
    jekyll --version
    ```

### 创建博客

```ruby
jekyll new blog     #创建新项目
cd blog
jekyll server       #运行服务器
```

上面的`jekyll new blog`可能会很慢，使用`jekyll new blog --skip-bundle`跳过bundle环节，然后修改新blog目录中的Gemfile，将第一行改成`source "https://gems.ruby-china.com"`，再运行`bundle install`即可完成项目创建。

访问测试：http://127.0.0.1:4000/
![](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/9587fdb0fc918f47e195c309d3d11151.png)

---


参考：
[windows安装jekyll步骤及问题](https://blog.csdn.net/mouday/article/details/79300135)
[windows安装jekyll](https://www.cnblogs.com/mingyue5826/p/11533978.html)