---
title: 发布npm包
article: false
categories: 
  - 工具使用
tags: 
  - npm
date: 2021-12-25 22:32:01
permalink: /other/npm/
---

# 发布npm包

## 什么是npm

npm是javascript的包管理工具，可以通过npm下载已有的js模块，类似于android的maven.

## 如何发布自己的npm包

以修改已有的npm包，发布我们自己的包为例

1. 在 [npm官网](https://www.npmjs.com/) 注册账号

2. 创建目录，放入插件相关的代码、readme，删除原来的`package.json`

3. 查看npm源是否是官方地址，不是的话要切换成官方地址

   > 查看npm镜像地址：npm config get registry
   >
   > 修改为官方地址：npm config set registry https://registry.npmjs.org/
   >
   > 修改为淘宝地址：npm config set registry http://registry.npm.taobao.org/    

4. 在命令行下执行 `npm login`，使用刚才注册的账户信息进行登录

5. 执行`npm init`，可以一路回车，会生成`package.json`文件，生成后再修改包名、地址等信息

6. 在命令行下进入项目根目录，执行 `npm public`，发布成功后会收到一份 [npm官网](https://www.npmjs.com/) 发送的通知邮件。

7.  如果包名称带有 `@xx` 前缀，默认被当做私有库进行发布。而私有库是需要额外收费的，所以在发布这种库时需要指定其为公开库，不过仅仅是第一次发布需要，后续更新再发布可以不用加参数了，执行指令：

   ```js
   npm publish --access public
   ```

8. 在 [npm官网](https://www.npmjs.com/) 搜索包名应该就能看到了。



例如这是我发布的自己修改的插件：[@sumcai/vuepress-plugin-comment](https://www.npmjs.com/package/@sumcai/vuepress-plugin-comment)

