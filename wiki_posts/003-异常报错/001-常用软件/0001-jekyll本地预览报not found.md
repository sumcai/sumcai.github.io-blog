# Jekyll新增文章本地预览时报 not found

## <i class="fa fa-question-circle"></i> 问题描述
使用jekyll博客，本地新增了一篇文章，`jekyll server`启动本地服务预览时，文章列表里能显示，点击进去时报错not found，但_site文件夹下存在对应文件。

![](assets/003/001/0001-1609954618696.png)

## <i class="fa fa-bullseye"></i> 查找原因
编码格式的问题，导致server无法正确找到对应的文章

## <i class="fa fa-check-circle"></i> 解决方法
找到Ruby安装目录下的`D:/Ruby27-x64/lib/ruby/2.7.0/webrick/httpservlet/filehandler.rb`，按如下图示修改内容

此处修改`path = req.path_info.dup.force_encoding("UTF-8")`
![](assets/003/001/0001-1609954825526.png)

此处新增`base.force_encoding("UTF-8")`
![](assets/003/001/0001-1609954861374.png)

修改保存后重新执行`jekyll server`，能正常跳转。