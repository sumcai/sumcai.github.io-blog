---
title: picgo+oracle cloud图床
layout: post
permalink: /other/picgooracle/
date: 2022-04-13 21:20:23
categories:
  - 建站
tags:
  - picgo
---

原文地址：https://www.eber.vip/res/52.html

### 1、PicGo简介

项目地址：https://github.com/Molunerfinn/PicGo

作者对于PicGo的简介：一个用于快速上传图片并获取图片 URL 链接的工具

支持的储存厂家：【下表为默认，且作者不再打算支持新的厂家，不过支持安装插件】

| 厂商                       | 最低版本      |
| -------------------------- | :------------ |
| 七牛云 云储存 (S3类型)     | v1.0          |
| 腾讯云 COS v4/v5 (S3类型)  | v1.1 / v1.5.0 |
| 阿里云 OSS (S3类型)        | v1.6.0        |
| 又拍云 云储存 (S3类型)     | v1.2.0        |
| GitHub 仓库 (类似代码提交) | v1.5.0        |
| SM.MS V2 (没用过)          | v2.3.0-beta.0 |
| Imgur (没用过)             | v1.6.0        |

### 2、PicGo安装

直接[点击此处](https://github.com/Molunerfinn/PicGo/releases)进入releases界面选择合适的版本以及合适的系统安装包进行下载安装即可。

### 3、插件安装

因为默认不支持AWS S3(含各厂家衍生版)的储存接入而我这里想接入Oracle Cloud的对象储存，所以就需要去找一个可以接入基于S3通用类型的插件。

⚠️：Oracle Cloud的对象储存是S3 Signature V4类型

直接在软件的插件设置界面搜索 s3

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/eee61b66d89882e6f71edec8dd2690ea.png)

名称为s3的这个插件即可以对接Oracle Cloud，我们直接点击安装即可。

### 4、插件设置

安装完成后图床设置下拉菜单会显示Amazon S3的子菜单【如果没有则进入PicGo设置开启显示】

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/874d4dbf71855c2cc1a4ff0a94f680f8.png)

- **S3应用密钥：**

  1、在Oracle Cloud控制台如图所示找到用户设置

  ![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/1415158bb6b85e4bc1bd7c89b866d55d.png)

  2、客户密钥-访问密钥 即为这里的应用密钥ID【如果之前没有创建过，就先看下一步生成密钥，然后在过来复制访问密钥】

  ![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/677f810ebc8096a30c5d46009fc76aea.png)

- **应用密钥：**

  在上一步客户密钥那里点击生成密钥，随便输入一个名字然后生成即可，注意这里的密钥只显示一次，请妥善保存，如果丢失就只能删除后重新创建一个。【这里的密钥和上面的访问密钥要是同一条记录】

  ![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/695cd4c589c71bad6540ffcc00904039.png)

- **桶名称和权限这俩比较简单，都是创建储存桶时定义的，这里重点介绍一下自定义节点的这个URL是如何获取的：**

  1、首先我们在控制台进入到储存桶界面，然后随便上传一个小文件。

  ![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/7bd784f75392a89093a86d2fc51d5702.png)

  这里查看对象详细信息里面有个URL路径，比如我这个是`https://objectstorage.us-phoenix-1.oraclecloud.com/n/axhsnkdv56py/b/bucket-oss/o/111.pdf` 我们取链接的 `objectstorage.us-phoenix-1.oraclecloud.com` 域名这一部分【同一个区域下这个域名是相同的】然后再这个域名前面拼上自己的桶名称空间和compat 格式应该是这样的 `桶名称空间.compat.objectstorage.us-phoenix-1.oraclecloud.com` 这里的桶名称空间在储存桶信息里面可以找到。

  ![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/5436626eb6ea4d9a3c4e9add83ed369a.png)

  那么我这个最终拼出来的自定义节点就是 `https://axhsxxxx56py.compat.objectstorage.us-phoenix-1.oraclecloud.com` 

- **自定义域名：**

  1、首先获取到我们要301或302的目标链接

  ![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/7398e5a81cf178fced0e7d039fda9eb1.png)

  依旧是随便打开一个文件的对象相信信息找到URL路径，我这边是`https://objectstorage.us-phoenix-1.oraclecloud.com/n/axhsnkdv56py/b/bucket-oss/o/111.pdf`

  我们需要用301或302的方式去实现自定义域名访问文件，那么肯定是要把我们的子域名比如`s3.eber.vip` 替代掉文件名之前的链接，也就是`https://objectstorage.us-phoenix-1.oraclecloud.com/n/axhsnkdv56py/b/bucket-oss/o`

  2、有了链接，那么直接拼上请求的文件名即可，所以我们可以使用nginx去配置301或者302的跳转

  首先我们要把`s3.eber.vip`解析到我们nginx所在的服务器IP上，然后在nginx中创建一个s3.eber.vip.conf配置文件【主配置文件需要引入该文件，否则不生效】。

  我的配置文件如下：

  

  ```nginx
  server {
    listen 80;
    listen [::]:80;
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    ssl_certificate /usr/local/nginx/conf/ssl/s3.eber.vip.crt;
    ssl_certificate_key /usr/local/nginx/conf/ssl/s3.eber.vip.key;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;
    ssl_ciphers TLS13-AES-256-GCM-SHA384:TLS13-CHACHA20-POLY1305-SHA256:TLS13-AES-128-GCM-SHA256:TLS13-AES-128-CCM-8-SHA256:TLS13-AES-128-CCM-SHA256:EECDH+CHACHA20:EECDH+AES128:RSA+AES128:EECDH+AES256:RSA+AES256:EECDH+3DES:RSA+3DES:!MD5;
    ssl_prefer_server_ciphers on;
    ssl_session_timeout 10m;
    ssl_session_cache builtin:1000 shared:SSL:10m;
    ssl_buffer_size 1400;
    add_header Strict-Transport-Security max-age=15768000;
    ssl_stapling on;
    ssl_stapling_verify on;
    server_name s3.eber.vip;
    access_log /data/wwwlogs/s3.eber.vip_nginx.log combined;
    index index.html index.htm index.php;
    root /data/wwwroot/s3.eber.vip;
    if ($ssl_protocol = "") { return 301 https://$host$request_uri; }
  
    location / {
      return 302 https://objectstorage.us-phoenix-1.oraclecloud.com/n/axhsnkdv56py/b/bucket-oss/o$request_uri; # 我这里不想让地址栏变成oracle的一大串链接，所以使用的是302重定向。
    }
  }
  ```

OK！配置相关的教程已经结束，如需要使用教程则直接访问[PicGo官方文档](https://picgo.github.io/PicGo-Doc/zh/guide/)进行查询。



======



上面是原作者的配置，我基于上面的配置是可以成功的，附带上本人自己的配置

![image-20220410213837817](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/10890e4b7a4e59799303b6b2301fef8a.png)

![image-20220410213924097](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/3bb5959d3ee3c67a071433282b7d86f8.png)



配置的自定义节点是桶的地址`https://axxxxxxxr.compat.objectstorage.ap-osaka-1.oraclecloud.com`

自定义域名可选，如果想换成自己的域名可配置如下：

```yaml
server {
    listen 80;
    server_name up.iogl.cn;
    return 301 https://objectstorage.ap-osaka-1.oraclecloud.com/n/axxxxxxxr/b/bucket-blog/o$request_uri;
}
```



