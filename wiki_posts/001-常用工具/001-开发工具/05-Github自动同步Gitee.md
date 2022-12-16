# GitHub自动同步到Gitee

对于广大程序员来说，github已成为每天必不可少的工具，但是在国内又难以忍受龟速，有一个不错的解决方法是使用Gitee作为桥梁，从Github导入仓库到Gitee，直接在Gitee上进行操作。今天我要介绍的是提交到Github时怎么触发代码自动同步到Gitee，这个功能主要用在Gitee Page的更新，因为Github Page是自动更新的，即博客更新了markdown文件后网站是自动更新的，而Gitee page需要手工更新才行，只有Pro版本才可以自动更新（当然是收费的），这里不得不吐槽一下国内的厂商，对于广大开发者来说，白嫖太难。

在多方探索后终于找到一个解决方案，使用[gitee-pages-action](https://github.com/yanglbme/gitee-pages-action)可实现推送到Github时，自动同步更新到Gitee，这样Gitee page也会自动更新，而不用再去手动更新了。

## 使用方式

在你的 GitHub 仓库新建 .github/workflows/ 文件夹，并在里面创建一个 .yml 文件，如 sync.yml，内容如下：

```ymal
name: Sync

on: page_build

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Sync to Gitee
        uses: wearerequired/git-mirror-action@master
        env:
          # 注意在 Settings->Secrets 配置 GITEE_RSA_PRIVATE_KEY
          SSH_PRIVATE_KEY: ${{ secrets.GITEE_RSA_PRIVATE_KEY }}
        with:
          # 注意替换为你的 GitHub 源仓库地址
          source-repo: git@github.com:doocs/advanced-java.git
          # 注意替换为你的 Gitee 目标仓库地址
          destination-repo: git@gitee.com:Doocs/advanced-java.git

      - name: Build Gitee Pages
        uses: yanglbme/gitee-pages-action@main
        with:
          # 注意替换为你的 Gitee 用户名
          gitee-username: yanglbme
          # 注意在 Settings->Secrets 配置 GITEE_PASSWORD
          gitee-password: ${{ secrets.GITEE_PASSWORD }}
          # 注意替换为你的 Gitee 仓库，仓库名严格区分大小写，请准确填写，否则会出错
          gitee-repo: doocs/advanced-java
          # 要部署的分支，默认是 master，若是其他分支，则需要指定（指定的分支必须存在）
          branch: main
```

按上面的注释填好对应的内容，在 GitHub 项目的 `Settings -> Secrets` 路径下配置好 `GITEE_RSA_PRIVATE_KEY` 以及 `GITEE_PASSWORD` 两个密钥。其中：

`GITEE_RSA_PRIVATE_KEY`: 存放你的 id_rsa 私钥(本地 `cat ~/.ssh/id_rsa`)。  
`GITEE_PASSWORD`: 存放你的 Gitee 帐号的密码。

配置完后，提交上面的文件到Github，如果一切配置正常，会成功触发 Gitee Pages Action ，我们会在 Gitee 公众号收到一条登录通知。这是 GitHub Action 程序帮我们登录到 Gitee 官网，并为我们点击了项目的部署按钮。

目前使用该方式实现Github->Gitee自动同步非常便捷，除了少数时候因为Gitee登录验证无法同步外，大多数时候表现都很稳定，感谢[gitee-pages-action](https://github.com/yanglbme) 的开发者 yanglbme 给我们提供的便捷。
