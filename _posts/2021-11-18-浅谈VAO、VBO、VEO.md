---
title: 浅谈VAO、VBO、VEO
layout: post
date: 2021-11-18 07:35:01
permalink: /opengl/vertex/
categories:
  - opengl技术
tags:
  - opengl基础
---

## 概念说明

在opengl中，VAO,VBO,VEO都是存储顶点数据的缓冲对象，解释如下：

- 顶点数组对象：Vertex Array Object，VAO
- 顶点缓冲对象：Vertex Buffer Object，VBO
- 索引缓冲对象：Element Buffer Object，EBO或Index Buffer Object，IBO



这三个缓冲对象的关系图：

![1635954045960](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/3c91e78070193e053a8588f8f91c6939.png)

### 顶点数组对象(VAO)

顶点数组对象(Vertex Array Object, VAO)可以像顶点缓冲对象那样被绑定，任何随后的顶点属性调用都会储存在这个VAO中。这样的好处就是，当配置顶点属性指针时，你只需要将那些调用执行一次，之后再绘制物体的时候只需要绑定相应的VAO就行了。这使在不同顶点数据和属性配置之间切换变得非常简单，只需要绑定不同的VAO就行了。



### 顶点缓冲对象(VBO)

我们通过顶点缓冲对象(Vertex Buffer Objects, VBO)管理内存，它会在GPU内存(通常被称为显存)中储存大批顶点。使用这些缓冲对象的好处是我们可以一次性的发送一大批数据到显卡上，而不是每个顶点发送一次。 



### 索引缓冲对象(EBO)

和顶点缓冲对象一样，EBO也是一个缓冲，它专门储存索引，OpenGL调用这些顶点的索引来决定该绘制哪个顶点。 



## 三者关系

**可以理解为VBO就是显存中的一个存储区域，可以保持大量的顶点属性信息**。并且可以开辟很多个VBO，每个VBO在OpenGL中有它的唯一标识ID，这个ID对应着具体的VBO的显存地址，通过这个ID可以对特定的VBO内的数据进行存取操作。 

**VAO是一个保存了所有顶点数据属性的状态结合，它存储了顶点数据的格式以及顶点数据所需的VBO对象的引用**。VAO本身并没有存储顶点的相关属性数据，这些信息是存储在VBO中的，VAO相当于是对很多个VBO的引用，把一些VBO组合在一起作为一个对象统一管理。

**EBO中存储的内容就是顶点位置的索引indices，EBO跟VBO类似，也是在显存中的一块内存缓冲器**，只不过EBO保存的是顶点的索引。 

## 示例代码

```c++
const GLfloat g_vertex_buffer_data[] = {
    -1.0f, -1.0f, 0.0f,     // 左下角
    1.0f, -1.0f, 0.0f,      // 右下角
    0.0f, 0.0f, 0.0f,       // 中间点
    -1.0f, 1.0f, 0.0f,      // 左上角
    1.0f, 1.0f, 0.0f        // 右上角
};

unsigned int indices1[] = {0, 1, 2};
unsigned int indices2[] = {2, 3, 4};

// VAO1、VBO1、EBO1的数据
GLuint VAO1;
GLuint VBO1;
GLuint EBO1;
glGenVertexArrays(1, &VAO1);
glBindVertexArray(VAO1);

glGenBuffers(1, &VBO1);
glBindBuffer(GL_ARRAY_BUFFER, VBO1);
glBufferData(GL_ARRAY_BUFFER, sizeof(g_vertex_buffer_data), g_vertex_buffer_data, GL_STATIC_DRAW);

glGenBuffers(1, &EBO1);
glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, EBO1);
glBufferData(GL_ELEMENT_ARRAY_BUFFER, sizeof(indices1), indices1, GL_STATIC_DRAW);

glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 0, (void*)0);
glEnableVertexAttribArray(0);


// VAO2、VBO2、EBO2的数据
GLuint VAO2;
GLuint VBO2;
GLuint EBO2;
glGenVertexArrays(1, &VAO2);
glBindVertexArray(VAO2);

glGenBuffers(1, &VBO2);
glBindBuffer(GL_ARRAY_BUFFER, VBO2);
glBufferData(GL_ARRAY_BUFFER, sizeof(g_vertex_buffer_data), g_vertex_buffer_data, GL_STATIC_DRAW);

glGenBuffers(1, &EBO2);
glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, EBO2);
glBufferData(GL_ELEMENT_ARRAY_BUFFER, sizeof(indices2), indices2, GL_STATIC_DRAW);

glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 0, (void*)0);
glEnableVertexAttribArray(0);

glClearColor( 0, 0, 0.4, 0 );
glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );

// 绑定VAO1
glBindVertexArray(1);
glDrawElements(GL_TRIANGLES, 3, GL_UNSIGNED_INT, 0);

// 绑定VAO2
glBindVertexArray(2);
glDrawElements(GL_TRIANGLES, 3, GL_UNSIGNED_INT, 0);
```

上面的示例代码，首先设置好VAO1、VAO2的缓冲数据，VAO中分别绑定对应的VBO、EBO，后面在绘制前直接绑定对应的VAO即可。

## 简单的绘制方式

如果给了一组顶点信息，可使用下面的两种方式绘制，两种方式是等效的：

```c++
const GLfloat points[] = {
    -1.0f, -1.0f, 0.0f,     // 左下角
    1.0f, -1.0f, 0.0f,      // 右下角
    0.0f, 0.0f, 0.0f,       // 中间点
};
// 方式一
glEnableVertexAttribArray(0);
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 0, points);
glDrawArrays(GL_TRIANGLES, 0, 3);
glDisableVertexAttribArray(0);

// 方式二
glEnableClientState(GL_VERTEX_ARRAY);
glVertexPointer(3, GL_FLOAT, 0, points);
glDrawArrays(GL_TRIANGLES, 0, 3);
glDisableClientState(GL_VERTEX_ARRAY);
```

