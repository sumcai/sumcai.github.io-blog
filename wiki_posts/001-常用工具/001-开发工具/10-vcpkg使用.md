## vcpkg使用教程

```shell
# 下载vcpkg项目
git clone https://github.com/Microsoft/vcpkg.git
cd vcpkg
 
# 本地编译
.\bootstrap-vcpkg.bat

# 安装指定的包，curl包分号后面的表示架构，可用的值为之前列出的那些。
vcpkg install curl:x64-windows

# 已安装的包更新
vcpkg upgrade

# 列出已经安装的包
vcpkg list

# 删除已安装的包
vcpkg remove curl:x64-windows

# 集成，为每一个用户设置
vcpkg integrate install

# 为当前项目配置，这里需要在该项目的目录下拥有一份vcpkg的拷贝
vcpkg integrate project

# 只下载，不安装
vcpkg install  openimageio:x64-windows --only-downloads
```



cmake里如果要find_package查找vcpkg安装的包，需要在cmake的project之前添加vcpkg的cmake文件(通过`vcpkg integrate install`查看路径)

```
set(CMAKE_TOOLCHAIN_FILE E:/code/Cascade/vcpkg/scripts/buildsystems/vcpkg.cmake)
```

