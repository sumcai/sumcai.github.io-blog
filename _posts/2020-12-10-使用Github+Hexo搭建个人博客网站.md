---
layout: post
title: 用Github+Hexo搭建个人博客
author: sumcai
header-style: text
article: false
tags: 
  - website
date: 2020-12-10 15:23:39
permalink: /other/hexoblog/
categories: 
  - 工具使用
  - 建站
---

继上篇【使用Github+Jekyll搭建个人博客网站】，因为再windows平台安装Jekyll相当繁琐，而且经常出现安装失败的情况，这种情况，与力求简单快速高效的时代主题相悖，大家都需要一种简单高效快速的搭建博客方案，此时Hexo横空而出，只需简单安装一个Nodejs，马上就能搭建好博客。

## 一、安装 Nodejs

下载 安装nodejs：`https://nodejs.org/en/`，安装直接点击下一步、下一步就可以了。

## 二、安装 Hexo 博客框架

官方源下载东西慢，国内切换到淘宝源

```shell
npm config set registry http://registry.npm.taobao.org
```

安装Hexo

```shell
npm install -g hexo-cli
```

## 三、使用 Hexo 搭建博客（本地启动）

创建blog目录，cmd进入blog目录，执行如下指令

`hexo new [layout] <title>` #新建文章，如果title含有空格，则需使用双引号包围 
`hexo clean` #清理缓存文件 
`hexo generate`	#生成静态文件 
`hexo server` #启动本地服务器

- 初始化博客

  ```shell
  hexo init
  ```

- 新建文章

  ```shell
  hexo new <title>
  ```

- 清理缓存

  ```shell
  hexo clean
  ```

- 生成静态文件

  ```shell
  hexo generate
  ```

- 启动本地服务器

  ```shell
  hexo server 
  ```

- 访问网站查看 http://localhost:4000

- 国内网速较慢时，可使用如下

  ```shell
  git clone https://gitee.com/sumcai/hexo-starter.git  blog
  cd blog
  npm config set registry http://registry.npm.taobao.org
  npm i
  git clone https://gitee.com/maoxuner/hexo-theme-hexone.git themes/one
  hexo s
  ```
  
## 四、部署到远端（Github）上公开使用

安装hexo-deployer

```shell
npm install --save hexo-deployer-git
```

在`_config.ymal`文件里增加git仓库地址

```ymal
deploy:
  type: git
  repository: https://github.com/qinghan586/qinghan586.github.io.git
  branch: master
```

部署到远端

```shell
hexo d
```

## 五、切换主题

使用如下指令下载主题到themes目录下

```shell
git clone https://gitee.com/maoxuner/hexo-theme-hexone.git themes/one
```

修改`_config.yml`文件切换主题:

```shell
theme: one
```

## 六、问题

主题不显示，只有信息`extends '_layout.swig'`
![图 1](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/3a95a935f97787bf48b20e907806772a.png)  

原因是hexo在新版本把swig删了，需要手动安装:

```cmd
npm i hexo-renderer-swig
```
