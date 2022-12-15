---
title: zotero+bookxnote
article: false
categories: 
  - 工具使用
tags: 
  - zotero
date: 2022-01-02 21:18:13
permalink: /other/zotero/
---

# 使用方式

实现一个多端同步的使用方式

## zotero

### 插件安装

- QuickLook

  快速预览，空格快速预览文件，不用打开文件了

  ![1641129859458](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/df8f1d2534886465333f384755785a01.png)

- zotfile

  重命名文件、设置附件文件保存位置

  先配置文件保存位置，并按照zotero的层级保存

  ![1641129956439](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/a4c4924f08770bea4ac21a669cbc8971.png)

  

  设置文件命名方式，类似`2009_Predictive-corrective incompressible SPH-(Solenthaler_Pajarola).pdf`

  ![1641130039800](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/5bf3d10cf92fe959910674cea22584d1.png)

- Sci-hub

  让zotero可以根据文献信息下载pdf等附件， 选项 - 高级 - 设置编辑器，

  搜索：
  `extensions.zotero.findPDFs.resolvers`

  将下面的复制到对话框：
  
  ```html
    {
        "name":"Sci-Hub",
        "method":"GET",
        "url":"https://sci-hub.ren/{doi}",
        "mode":"html",
        "selector":"#pdf",
        "attribute":"src",
        "automatic":true
    }
  ```
  
  

- jasminum

  茉莉花插件，据说是中文文献用的，暂时还没用到

### 配置

1. 配置同步

   只同步数据， 不同步文件

   ![1641130953545](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/7b2963ed52e1f3293d6688ba66ead39c.png)

2. 配置文件目录

   设置附件根目录，这个是保存pdf文件的目录，后面需要用坚果云云同步保存。

   数据存储位置可设置也可不设置，因为本来就是在zotero里云同步的。

   ![1641131268177](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/7789f07310fd60db56d23ad91394ba40.png)



## bookxnote

设置如图所示

![1641132116647](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/b2e7f52578b11087ab7475b24f5ded08.png)

1. 设置笔记数据目录

   这下面有两个目录，

   `notebooks`：用来保存笔记

   `bookmarks`：用来保存书签

2. 设置工作目录

   这是保存pdf文件的目录，也是上面zotfile设置的目录，这样所有的附件都存放到这里

## 坚果云

1. 同步目录

坚果云分别设置同步上面三个目录，这样所有的数据我们都存储到云上了，可以实现多端同步

![1641132763486](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/84951780ced6f59e8ff61a278dad815f.png)

2. 开启WebDav

   网页版 - 账户信息 - 添加应用

## 使用

如果在另外一台设备上使用，步骤为：

1. 安装zotero，登录账号，同步文献数据
2. 安装坚果云，将上面提到的三个目录同步到本地
3. 分别在zotero、bookxnote里反向设置这些目录
4. 手机端安装booxnote，在选项里填入WebDav信息
5. 按上面的操作后，即可实现多端数据同步



参考： 

[用 Zotero+坚果云搞定多设备文献管理](https://sspai.com/post/64283)

[文献管理软件——Zotero以及实用插件介绍](https://www.bilibili.com/video/BV1KQ4y1i7VP/?spm_id_from=autoNext)

[Bookxnote Pro 手机端坚果云同步](https://www.bilibili.com/read/cv13682566)

