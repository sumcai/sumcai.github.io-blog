---
title: VSCode开发换配置
date: 2021-11-20 20:28:19
permalink: /other/vscodecpp/
article: false
categories:
  - 工具使用
tags:
  - VSCode
---

## vscode+cmake配置C/C++环境

记录一下如何利用vscode和cmake配置C/C++环境，话不多说直接上手。

### 1.下载安装

下好vscode，cmake(记得配置环境变量)，在vscode扩展中下载**cmake**和**cmake-tools**两个插件

### 2.新建工程

新建文件夹CmakeDemo，用vscode打开，编写一个main.cpp和CMakeLists.txt，其中CMakeList如下

```cmake
cmake_minimum_required(VERSION 2.8)

project(vscode_cmake_project)

# 这行要添加，否则gdb调试会出问题
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")

add_executable(hello main.cpp)
```

### 3.配置CMake

ctrl+shift+P，选择 **CMake：配置**，由于这个时候还没有选择工具包，也就是编译器，会自动跳出目前可选的所有编译器的路径，我选的是我之前安装的mingw，里面包含GCC 8.1。点击之后的结果如下
![在这里插入图片描述](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/e1a78e2578a331e901b2845ac5182a25.png)

这个过程自动生成了build文件夹，并在build文件夹内自动生成了makefile，下一步就是make了

### 4.生成目标

然后看vscode最下面栏
![在这里插入图片描述](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/d1ceeffd56aa1850fc0a99417afad18f.png)
点击那个齿轮，就在build文件夹中生成了exe了，进入终端执行可以看到输出结果
![在这里插入图片描述](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/54053ed16125b912fa66c8febb5c69a3.png)

### 5.调试配置

最后一个就是调试了，点击运行 -> 添加配置 -> gdb -> 默认配置
自动弹出一个 launch.json，这个文件一般就是用来配置调试的。改两个地方就可以，就是打了注释的两个地方

```json
{
    // 使用 IntelliSense 了解相关属性。
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) 启动",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/build/hello.exe",//改为可执行程序的路径
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "miDebuggerPath": "C:/mingw64/bin/gdb.exe",//改为gdb的路径
            "setupCommands": [
                {
                    "description": "为 gdb 启用整齐打印",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}
```



打上断点，按f5就可以进行调试了
![在这里插入图片描述](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/39f6038d4e745cdad0311c36190afd2f.png)

------



### 6.另一种方法(task方式)

以上是通过插件进行生成makefile，并make的方法，下面再介绍一种配置task的方式来实现makefile的生成，以及make

1、点击终端->配置任务，随便选哪个，反正只要能弹出tasks.json就行，往tasks.json中填入以下内容

```json
{
    "version": "2.0.0",
    "options": {
        "cwd": "${workspaceRoot}/build" //所有的task均在build中进行
    },
    "tasks": [
        {
            "label": "cmake", // 先 cmake
            "type": "shell",
            "command": "cmake",
            "args": [
                "-G",
                "Unix Makefiles", // win系统需要加这个
                "-DCMAKE_BUILD_TYPE=Debug",// 以debug版本编译
                ".."
            ]
        },

        {
            "label": "make",// 再 make
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "type": "shell",
            "command": "make",
            "args": []
        },

        {
            "label": "run",// 最后可以运行
            "type": "shell",
            "command": "./hello.exe",
        }
    ]
}
```



很明显，tasks中含有三个任务，并且都在build中运行，因此这种方式需要事先建立build文件夹

2、进入了build文件夹后，点击终端->运行任务，然后我们就可以看到我们自定义的三个任务的名字，cmake，make，run，这些名字都可以自己取，记住各自的含义就行，按照顺序来可以成功输出。
![在这里插入图片描述](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/c2737755461878ffd3f7b2b90f6619e5.png)

3、同样，为了能够调试我们也要配置launch.json文件

```json
{
    // 使用 IntelliSense 了解相关属性。
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) 启动",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/build/hello.exe",//改为可执行程序的路径
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "miDebuggerPath": "C:/mingw64/bin/gdb.exe",//改为gdb的路径
            "setupCommands": [
                {
                    "description": "为 gdb 启用整齐打印",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "make" //调试前的运行的任务，也可以换成run
        }
    ]
}
```



与第一种方法略有不同的是最后一行，添加了一个preLaunchTask，顾名思义就是launch.json运行之前运行的task，设置为run或者make都行，只要保证调试的时候存在可执行程序就行。

最后，打上断点，f5调试即可。



## 总结
第一种方式可以很方便的进行cmake和make，不过当你需要往cmake后面需要添加一些参数的话，第二种方法会更好一点，根据需要选择即可。本来对vscode配置一头雾水，折腾了几天下来，也有了不少的进步，加油！