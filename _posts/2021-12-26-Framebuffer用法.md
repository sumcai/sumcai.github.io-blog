---
title: Framebuffer用法
layout: post
categories: 
  - opengl技术
tags: 
  - opengl基础
  - framebuffe
permalink: /opengl/framebuffer/
date: 2021-12-26 20:14:37
---

# Framebuffer介绍

opengl中framebuffer称为帧缓冲，它是一个内存缓冲区，如果把渲染到屏幕的颜色缓冲，深度缓冲，模板缓冲都缓存到内存中，那么就叫帧缓冲。

## Framebuffer用法

framebuffer通常用在离屏渲染或者后处理上，主要涉及这几个函数：

-  `glGenFramebuffers` ：创建framebuffer
-  `glBindFramebuffer` ：绑定framebuffer
-  `glFramebufferTexture2D` ：将纹理附加到framebuffer到，实现绘制到纹理



## 示例代码

我们模拟一个后处理操作，将[Blend用法](http://iogl.cn/opengl/blend/)中的绘制结果画在屏幕中央，并且对结果的颜色取反向，让我们看看具体代码：

`05.FBTexture.fs`内容：

```glsl
#version 330 core
in vec2 TexCoord;
uniform sampler2D tex1;
out vec4 FragColor;
void main()
{
    FragColor = vec4(vec3(1.0 - texture(tex1, TexCoord)), 1.0);
}
```

实现代码：

```c++
void display( GLFWwindow* window )
{
    // 1.绑定framebuffer，这样可以绘制到附加的纹理fbTexture上
    glBindFramebuffer(GL_FRAMEBUFFER, framebuffer);
    glEnable(GL_DEPTH_TEST);
    glEnable(GL_BLEND);
    glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);
    glClearColor( 0, 0, 0.4, 0 );
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

    glUseProgram(boxProgramID);

    glm::mat4 projection = glm::perspective(glm::radians(45.0f), (float) 5 / (float)5, 0.1f, 100.0f);
    glm::mat4 view = glm::lookAt(glm::vec3(1,2,3), glm::vec3(0,0,0), glm::vec3(0,1,0));
    glm::mat4 model = glm::mat4(1.0f);
    glm::mat4 mvp = projection * view * model;

    // 2.画地面
    GLuint mvpId = glGetUniformLocation(boxProgramID, "MVP");
    glUniformMatrix4fv(mvpId, 1, GL_FALSE, &mvp[0][0]);
    glBindVertexArray(FloorVAO);
    glBindTexture(GL_TEXTURE_2D, floorTexture);
    glDrawArrays(GL_TRIANGLES, 0, 6);

    // 3.画立方体
    glBindVertexArray(VAO);
    glBindTexture(GL_TEXTURE_2D, texture);
    glDrawArrays(GL_TRIANGLES, 0, 36);

    // 4.画blend物体
    model = glm::mat4(1.0f);
    model = glm::translate(model, glm::vec3(0, 0, 1.01f));
    mvp = projection * view * model;
    glUniformMatrix4fv(mvpId, 1, GL_FALSE, &mvp[0][0]);
    glBindTexture(GL_TEXTURE_2D, blendTexture);
    glDrawArrays(GL_TRIANGLES, 0, 6);
    
    // 5.对fbTexture采样后处理将绘制到屏幕
    glDisable(GL_DEPTH_TEST);
    glDisable(GL_BLEND);
    glBindFramebuffer(GL_FRAMEBUFFER, 0);
    glClearColor(0.3f, 0.3f, 0.3f, 1.0f);
    glClear(GL_COLOR_BUFFER_BIT);
    glUseProgram(screenProgramID);
    glBindVertexArray(screenVAO);
    glBindTexture(GL_TEXTURE_2D, fbTexture);
    glDrawArrays(GL_TRIANGLES, 0, 6);
}

void prepare() {
    boxProgramID = LoadShaders( "data/shader/03.MVP.vs", "data/shader/03.MVP.fs" );

    const GLfloat g_vertex_buffer_data[] = {
            -0.5f, -0.5f, -0.5f,  0.0f, 0.0f,
            0.5f, -0.5f, -0.5f,  1.0f, 0.0f,
            0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
            0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
            -0.5f,  0.5f, -0.5f,  0.0f, 1.0f,
            -0.5f, -0.5f, -0.5f,  0.0f, 0.0f,

            -0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
            0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
            0.5f,  0.5f,  0.5f,  1.0f, 1.0f,
            0.5f,  0.5f,  0.5f,  1.0f, 1.0f,
            -0.5f,  0.5f,  0.5f,  0.0f, 1.0f,
            -0.5f, -0.5f,  0.5f,  0.0f, 0.0f,

            -0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
            -0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
            -0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
            -0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
            -0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
            -0.5f,  0.5f,  0.5f,  1.0f, 0.0f,

            0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
            0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
            0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
            0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
            0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
            0.5f,  0.5f,  0.5f,  1.0f, 0.0f,

            -0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
            0.5f, -0.5f, -0.5f,  1.0f, 1.0f,
            0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
            0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
            -0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
            -0.5f, -0.5f, -0.5f,  0.0f, 1.0f,

            -0.5f,  0.5f, -0.5f,  0.0f, 1.0f,
            0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
            0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
            0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
            -0.5f,  0.5f,  0.5f,  0.0f, 0.0f,
            -0.5f,  0.5f, -0.5f,  0.0f, 1.0f
    };

    float fllor_vertex_buffer_data[] = {
            5.0f, -0.5f,  5.0f,  1.0f, 0.0f,
            -5.0f, -0.5f,  5.0f,  0.0f, 0.0f,
            -5.0f, -0.5f, -5.0f,  0.0f, 1.0f,

            5.0f, -0.5f,  5.0f,  1.0f, 0.0f,
            -5.0f, -0.5f, -5.0f,  0.0f, 1.0f,
            5.0f, -0.5f, -5.0f,  1.0f, 1.0f
    };
    float blend_vertex_buffer_data[] = {
            0.0f,  0.5f,  0.0f,  0.0f,  0.0f,
            0.0f, -0.5f,  0.0f,  0.0f,  1.0f,
            1.0f, -0.5f,  0.0f,  1.0f,  1.0f,

            0.0f,  0.5f,  0.0f,  0.0f,  0.0f,
            1.0f, -0.5f,  0.0f,  1.0f,  1.0f,
            1.0f,  0.5f,  0.0f,  1.0f,  0.0f
    };

    // 1.VAO、VBO的数据
    glGenVertexArrays(1, &VAO);
    glBindVertexArray(VAO);
    GLuint VBO1;
    glGenBuffers(1, &VBO1);
    glBindBuffer(GL_ARRAY_BUFFER, VBO1);
    glBufferData(GL_ARRAY_BUFFER, sizeof(g_vertex_buffer_data), g_vertex_buffer_data, GL_STATIC_DRAW);
    glEnableVertexAttribArray(0);
    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 5 * sizeof(GLfloat), (void*)0);
    // 纹理坐标
    glEnableVertexAttribArray(1);
    glVertexAttribPointer(1, 2, GL_FLOAT, GL_FALSE, 5 * sizeof(GLfloat), (void*)(3 * sizeof(GLfloat)));

    // 2.地面贴图
    glGenVertexArrays(1, &FloorVAO);
    glBindVertexArray(FloorVAO);
    GLuint VBO2;
    glGenBuffers(1, &VBO2);
    glBindBuffer(GL_ARRAY_BUFFER, VBO2);
    glBufferData(GL_ARRAY_BUFFER, sizeof(fllor_vertex_buffer_data), fllor_vertex_buffer_data, GL_STATIC_DRAW);
    glEnableVertexAttribArray(0);
    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 5 * sizeof(GLfloat), (void*)0);
    // 纹理坐标
    glEnableVertexAttribArray(1);
    glVertexAttribPointer(1, 2, GL_FLOAT, GL_FALSE, 5 * sizeof(GLfloat), (void*)(3 * sizeof(GLfloat)));

    // 3.blend贴图
    glGenVertexArrays(1, &BlendVAO);
    glBindVertexArray(BlendVAO);
    GLuint VBO3;
    glGenBuffers(1, &VBO3);
    glBindBuffer(GL_ARRAY_BUFFER, VBO3);
    glBufferData(GL_ARRAY_BUFFER, sizeof(blend_vertex_buffer_data), blend_vertex_buffer_data, GL_STATIC_DRAW);
    glEnableVertexAttribArray(0);
    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 5 * sizeof(GLfloat), (void*)0);
    // 纹理坐标
    glEnableVertexAttribArray(1);
    glVertexAttribPointer(1, 2, GL_FLOAT, GL_FALSE, 5 * sizeof(GLfloat), (void*)(3 * sizeof(GLfloat)));

    // 纹理数据
    floorTexture = loadTexture("data/img/33.png");
    texture = loadTexture("data/img/11.jpg");
    blendTexture = loadTexture("data/img/chick.png");


    // 4.创建framebuffer以及附加的纹理
    glGenFramebuffers(1, &framebuffer);
    glBindFramebuffer(GL_FRAMEBUFFER, framebuffer);
    glGenTextures(1, &fbTexture);
    glBindTexture(GL_TEXTURE_2D, fbTexture);
    glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, 512, 512, 0, GL_RGB, GL_UNSIGNED_BYTE, NULL);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
    glFramebufferTexture2D(GL_FRAMEBUFFER, GL_COLOR_ATTACHMENT0, GL_TEXTURE_2D, fbTexture, 0);

    // 5.绘制到屏幕的shader和顶点数据
    screenProgramID = LoadShaders( "data/shader/02.Texture.vs", "data/shader/05.FBTexture.fs" );

    const GLfloat g_screen_vertex_buffer_data[] = {
            -0.5f,  0.5f,  0.0f,  0.0f,  1.0f,
            -0.5f, -0.5f,  0.0f,  0.0f,  0.0f,
            0.5f, -0.5f,  0.0f,   1.0f,  0.0f,

            -0.5f,  0.5f,  0.0f,  0.0f,  1.0f,
            0.5f, -0.5f,  0.0f,  1.0f,  0.0f,
            0.5f,  0.5f,  0.0f,  1.0f,  1.0f
    };

    // VAO、VBO的数据
    GLuint screenVBO;
    glGenVertexArrays(1, &screenVAO);
    glBindVertexArray(screenVAO);
    glGenBuffers(1, &screenVBO);
    glBindBuffer(GL_ARRAY_BUFFER, screenVBO);
    glBufferData(GL_ARRAY_BUFFER, sizeof(g_screen_vertex_buffer_data), g_screen_vertex_buffer_data, GL_STATIC_DRAW);
    glEnableVertexAttribArray(0);
    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 5 * sizeof(GLfloat), (void*)0);
    glEnableVertexAttribArray(1);
    glVertexAttribPointer(1, 2, GL_FLOAT, GL_FALSE, 5 * sizeof(GLfloat), (void*)(3 * sizeof(GLfloat)));
}
```

最终显示结果：

![1640529248087](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/e2fabf1d21d3bcb698475c4adc3fd233.png)