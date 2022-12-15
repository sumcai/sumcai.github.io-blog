---
title: Markdown语法
author: sumcai
article: false
tags: 
  - markdown
date: 2021-01-12 15:23:40
categories: 
  - 工具使用
permalink: /other/markdown/
---


# Markdown 快速开始

## 一、快捷键

```html
加粗 Ctrl + B
斜体 Ctrl + I
引用 Ctrl + Q
插入链接 Ctrl + L
插入代码 Ctrl + K
插入图片 Ctrl + G
提升标题 Ctrl + H
有序列表 Ctrl + O
无序列表 Ctrl + U
横线 Ctrl + R
撤销 Ctrl + Z
重做 Ctrl + Y
```

## 二、基本语法

### （一）斜体、粗体、删除线：

 ![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/10610eae1854cf61e844f57aa4197ace.jpg) 

### （二）分级标题，两种写法：

 ![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/16c797244c82bd0159082331129d0916.jpg) 

写法2：

 ![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/c6b8e22a7d1d5cd19d7be51c0e5eec8c.jpg) 

### （三）链接

#### （1）插入本地图片链接

 **语法规则，有两种写法：** 

 ![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/3156ace953fdbac6c52c0f999351d0f2.jpg) 

示例图如下：

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/ab4ea2b0710c6b9364a716b06012b977.jpg) 

#### （2）插入互联网上图片

**语法规则：**

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/cc7dbde921b3b3275491e0b9c19b2949.jpg)

示例如下：

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/22c5e4abf6108cede721de4dea972e0a.jpg)

#### （3）自动连接

**Markdown 支持以比较简短的自动链接形式来处理网址和电子邮件信箱，只要是用<>包起来， Markdown 就会自动把它转成链接。也可以直接写，也是可以显示成链接形式的**

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/5c043698e3fb70f2c0f98cd0ec4461c9.jpg)

### （四）分割线

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/39a4d6410f49cfcb762fc2ea7ff4de79.jpg)

### （五）代码块

对于程序员来说这个功能是必不可少的，插入程序代码的方式有两种，一种是利用缩进(tab), 另一种是利用英文“`”符号（一般在ESC键下方，和~同一个键）包裹代码。

#### （1）代码块：缩进 4 个空格或是 1 个制表符。效果如下：

```cpp
#include <stdio.h>
int main(void)
{
    printf("Hello world\n");
}
```

#### （2）行内式：如果在一个行内需要引用代码，只要用反引号`引起来就好(Esc健）

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/f00fad8de9c74494940bd5da5c2e229a.jpg)

#### （3）多行代码块与语法高亮：在需要高亮的代码块的前一行及后一行使用三个单反引号“`”包裹，就可以了。

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/efe6c7f2b7b44330da7540b5ecd26adb.jpg)

#### （4）代码块里面包含html代码

在代码区块里面， & 、 < 和 > 会自动转成 HTML 实体，这样的方式让你非常容易使用 Markdown 插入范例用的 HTML 原始码，只需要复制贴上，剩下的 Markdown 都会帮你处理。

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/626619bb6e74921315eec8a1f8991e1f.jpg)

### （六）引用

在被引用的文本前加上>符号，以及一个空格就可以了，如果只输入了一个>符号会产生一个空白的引用。

#### （1）基本使用

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/ead50e75bc16b6673aed3c3356085757.jpg)

#### （2）引用的嵌套使用

![img](assets/6098829-ff02994c913f4864.jpg)

#### （3）引用其它要素

引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等。

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/a89c306414c879644cd15004c91a951c.jpg)

### （七）列表

#### （1）无序列表

使用 *，+，- 表示无序列表。
 **注意：符号后面一定要有一个空格，起到缩进的作用。**

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/933161454fb38b5fad8c4b2cfaab5db0.jpg)

#### （2）有序列表

使用数字和一个英文句点表示有序列表。
 **注意：英文句点后面一定要有一个空格，起到缩进的作用。**

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/ec897eecc956afcdc9326c8f070eda57.jpg)

#### （3）无序列表和有序列表同时使用

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/9b09c9d4c4323e768d6b838fd53448ee.jpg)

#### （4）列表和其它要素混合使用

**注意事项：列表中包含多行代码块，需要另起一行，否则不生效。**

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/a93bc1bf5b54fe7df98f36965a011796.jpg)

#### （5）注意事项

在使用列表时，只要是数字后面加上英文的点，就会无意间产生列表，比如2017.12.30 这时候想表达的是日期，有些软件把它被误认为是列表。解决方式：在每个点前面加上\就可以了。如下图所示：

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/cbf8e4b383f8ea5c134a3b2eeb779f6f.jpg)

### （八）表格

表格的基本写法很简单，就跟表格的形状很相似：

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/394f06d41891084beff4a125f2b4c948.jpg)



**表格对齐方式：我们可以指定表格单元格的对齐方式，冒号在左边表示左对齐，右边表示有对齐，两边都有表示居中。**

如下图所示：

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/17962a450a314a4870a2065e0d37d7a3.jpg)

------

## 三、常用技巧

### （一）换行

```xml
方法1: 连续两个以上空格+回车
方法2：使用html语言换行标签：<br>
```

### （二）缩进字符

```bash
不断行的空白格 &nbsp; 或 &#160;
半角的空格 &ensp; 或 &#8194;
全角的空格 &emsp; 或 &#8195;
```

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/ed8cb68a0a295c5e8092f5b5664ca121.jpg)

### （三）如何打出一些特殊符号

- （1）对于 Markdown 中的语法符号，前面加反斜线`\`即可显示符号本身。

示例如下：

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/83c18e906e222568de5fb08657e257b0.jpg)

- （2）其他特殊字符，示例如下：

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/ed582bf554fb7b217e1f99b054ce8a8c.jpg)

### （四）链接注脚

#### （1）参考式链接。

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/a11189d01cda3116765f609e00188ebe.jpg)

#### （2）注脚

![img](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/7293b58406e50a09b90f90390589402e.jpg)


## 四、数学公式

### （一）行内与独行

1. 行内公式：将公式插入到本行内，符号：`$公式内容$`，如：$xyz$
2. 独行公式：将公式插入到新的一行内，并且居中，符号：`$$公式内容$$`，如：$$ xyz $$

### （二）上标、下标与组合

1. 上标符号，符号：`^`，如：$x^4$
2. 下标符号，符号：`_`，如：$x_1$
3. 组合符号，符号：`{}`，如：${16}_{8}O{2+}_{2}$

### （三）汉字、字体与格式

1. 汉字形式，符号：`\mbox{}`，如：$V_{\mbox{初始}}$
2. 字体控制，符号：`\displaystyle`，如：$\displaystyle \frac{x+y}{y+z}$
3. 下划线符号，符号：`\underline`，如：$\underline{x+y}$
4. 标签，符号`\tag{数字}`，如：$\tag{11}$
5. 上大括号，符号：`\overbrace{算式}`，如：$\overbrace{a+b+c+d}^{2.0}$
6. 下大括号，符号：`\underbrace{算式}`，如：$a+\underbrace{b+c}_{1.0}+d$
7. 上位符号，符号：`\stacrel{上位符号}{基位符号}`，如：$\vec{x}\stackrel{\mathrm{def}}{=}{x_1,\dots,x_n}$

### （四）占位符

1. 两个quad空格，符号：`\qquad`，如：$x \qquad y$
2. quad空格，符号：`\quad`，如：$x \quad y$
3. 大空格，符号`\`，如：$x \  y$
4. 中空格，符号`\:`，如：$x : y$
5. 小空格，符号`\,`，如：$x , y$
6. 没有空格，符号``，如：$xy$
7. 紧贴，符号`\!`，如：$x ! y$

### （五）定界符与组合

1. 括号，符号：`（）\big(\big) \Big(\Big) \bigg(\bigg) \Bigg(\Bigg)`，如：$（）\big(\big) \Big(\Big) \bigg(\bigg) \Bigg(\Bigg)$
2. 中括号，符号：`[]`，如：$[x+y]$
3. 大括号，符号：`\{ \}`，如：${x+y}$
4. 自适应括号，符号：`\left \right`，如：$\left(x\right)$，$\left(x{yz}\right)$
5. 组合公式，符号：`{上位公式 \choose 下位公式}`，如：${n+1 \choose k}={n \choose k}+{n \choose k-1}$
6. 组合公式，符号：`{上位公式 \atop 下位公式}`，如：$\sum_{k_0,k_1,\ldots>0 \atop k_0+k_1+\cdots=n}A_{k_0}A_{k_1}\cdots$

### （六）四则运算

1. 加法运算，符号：`+`，如：$x+y=z$
2. 减法运算，符号：`-`，如：$x-y=z$
3. 加减运算，符号：`\pm`，如：$x \pm y=z$
4. 减甲运算，符号：`\mp`，如：$x \mp y=z$
5. 乘法运算，符号：`\times`，如：$x \times y=z$
6. 点乘运算，符号：`\cdot`，如：$x \cdot y=z$
7. 星乘运算，符号：`\ast`，如：$x \ast y=z$
8. 除法运算，符号：`\div`，如：$x \div y=z$
9. 斜法运算，符号：`/`，如：$x/y=z$
10. 分式表示，符号：`\frac{分子}{分母}`，如：$\frac{x+y}{y+z}$
11. 分式表示，符号：`{分子} \voer {分母}`，如：${x+y} \over {y+z}$
12. 绝对值表示，符号：`||`，如：$|x+y|$

### （七）高级运算

1. 平均数运算，符号：`\overline{算式}`，如：$\overline{xyz}$
2. 开二次方运算，符号：`\sqrt`，如：$\sqrt x$
3. 开方运算，符号：`\sqrt[开方数]{被开方数}`，如：$\sqrt[3]{x+y}$
4. 对数运算，符号：`\log`，如：$\log(x)$
5. 极限运算，符号：`\lim`，如：$\lim^{x \to \infty}_{y \to 0}{\frac{x}{y}}$
6. 极限运算，符号：`\displaystyle \lim`，如：$\displaystyle \lim^{x \to \infty}_{y \to 0}{\frac{x}{y}}$
7. 求和运算，符号：`\sum`，如：$\sum^{x \to \infty}_{y \to 0}{\frac{x}{y}}$
8. 求和运算，符号：`\displaystyle \sum`，如：$\displaystyle \sum^{x \to \infty}_{y \to 0}{\frac{x}{y}}$
9. 积分运算，符号：`\int`，如：$\int^{\infty}_{0}{xdx}$
10. 积分运算，符号：`\displaystyle \int`，如：$\displaystyle \int^{\infty}_{0}{xdx}$
11. 微分运算，符号：`\partial`，如：$\frac{\partial x}{\partial y}$
12. 矩阵表示，符号：`\begin{matrix} \end{matrix}`，如：
$
\left[
\begin{matrix}
 1      & 2      & \cdots & 4      \\
 7      & 6      &{\cdot^{\cdot^{\cdot}}} & 5      \\
 \vdots & \vdots & \ddots & \vdots \\
 8      & 9      & \cdots & 0      \\
\end{matrix}
\right]
$

### （八） 矩阵
使用 \begin{matrix}开头及\end{matrix}结尾，每行 \\结尾，每个元素 &分隔。
```markdown
$$
\begin{matrix}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1 \\
\end{matrix}
$$
```

- matrix
  
$$
\begin{matrix}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1 \\
\end{matrix}
$$

- pmatrix

$$
\begin{pmatrix}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1 \\
\end{pmatrix}
$$

- bmatrix

$$
\begin{bmatrix}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1 \\
\end{bmatrix}
$$

- Bmatrix

$$
\begin{Bmatrix}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1 \\
\end{Bmatrix}
$$

- vmatrix

$$
\begin{vmatrix}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1 \\
\end{vmatrix}
$$

- Vmatrix

$$
\begin{Vmatrix}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1 \\
\end{Vmatrix}
$$

###  （九）多值函数

使用 cases 块表达式，每行 \\结尾，每个元素 & 分隔
```markdown
$$
p(x) = 
\\begin{cases}
  p, & x = 1 \\
  1 - p, & x = 0
\\end{cases}
$$
```

$$
p(x) = 
\begin{cases}
  p, & x = 1 \\
  1 - p, & x = 0
\end{cases}
$$

### （十）逻辑运算

1. 等于运算，符号：`=`，如：$x+y=z$
2. 大于运算，符号：`>`，如：$x+y>z$
3. 小于运算，符号：`<`，如：$x+y<z$
4. 大于等于运算，符号：`\geq`，如：$x+y \geq z$
5. 小于等于运算，符号：`\leq`，如：$x+y \leq z$
6. 不等于运算，符号：`\neq`，如：$x+y \neq z$
7. 不大于等于运算，符号：`\ngeq`，如：$x+y \ngeq z$
8. 不大于等于运算，符号：`\not\geq`，如：$x+y \not\geq z$
9. 不小于等于运算，符号：`\nleq`，如：$x+y \nleq z$
10. 不小于等于运算，符号：`\not\leq`，如：$x+y \not\leq z$
11. 约等于运算，符号：`\approx`，如：$x+y \approx z$
12. 恒定等于运算，符号：`\equiv`，如：$x+y \equiv z$

### （十一）集合运算

1. 属于运算，符号：`\in`，如：$x \in y$
2. 不属于运算，符号：`\notin`，如：$x \notin y$
3. 不属于运算，符号：`\not\in`，如：$x \not\in y$
4. 子集运算，符号：`\subset`，如：$x \subset y$
5. 子集运算，符号：`\supset`，如：$x \supset y$
6. 真子集运算，符号：`\subseteq`，如：$x \subseteq y$
7. 非真子集运算，符号：`\subsetneq`，如：$x \subsetneq y$
8. 真子集运算，符号：`\supseteq`，如：$x \supseteq y$
9. 非真子集运算，符号：`\supsetneq`，如：$x \supsetneq y$
10. 非子集运算，符号：`\not\subset`，如：$x \not\subset y$
11. 非子集运算，符号：`\not\supset`，如：$x \not\supset y$
12. 并集运算，符号：`\cup`，如：$x \cup y$
13. 交集运算，符号：`\cap`，如：$x \cap y$
14. 差集运算，符号：`\setminus`，如：$x \setminus y$
15. 同或运算，符号：`\bigodot`，如：$x \bigodot y$
16. 同与运算，符号：`\bigotimes`，如：$x \bigotimes y$
17. 实数集合，符号：`\mathbb{R}`，如：`\mathbb{R}` 
18. 自然数集合，符号：`\mathbb{Z}`，如：`\mathbb{Z}` 
19. 空集，符号：`\emptyset`，如：$\emptyset$

### （十二）数学符号

1. 无穷，符号：`\infty`，如：$\infty$
2. 虚数，符号：`\imath`，如：$\imath$
3. 虚数，符号：`\jmath`，如：$\jmath$
4. 数学符号，符号`\hat{a}`，如：$\hat{a}$
5. 数学符号，符号`\check{a}`，如：$\check{a}$
6. 数学符号，符号`\breve{a}`，如：$\breve{a}$
7. 数学符号，符号`\tilde{a}`，如：$\tilde{a}$
8. 数学符号，符号`\bar{a}`，如：$\bar{a}$
9. 矢量符号，符号`\vec{a}`，如：$\vec{a}$
10. 数学符号，符号`\acute{a}`，如：$\acute{a}$
11. 数学符号，符号`\grave{a}`，如：$\grave{a}$
12. 数学符号，符号`\mathring{a}`，如：$\mathring{a}$
13. 一阶导数符号，符号`\dot{a}`，如：$\dot{a}$
14. 二阶导数符号，符号`\ddot{a}`，如：$\ddot{a}$
15. 上箭头，符号：`\uparrow`，如：$\uparrow$
16. 上箭头，符号：`\Uparrow`，如：$\Uparrow$
17. 下箭头，符号：`\downarrow`，如：$\downarrow$
18. 下箭头，符号：`\Downarrow`，如：$\Downarrow$
19. 左箭头，符号：`\leftarrow`，如：$\leftarrow$
20. 左箭头，符号：`\Leftarrow`，如：$\Leftarrow$
21. 右箭头，符号：`\rightarrow`，如：$\rightarrow$
22. 右箭头，符号：`\Rightarrow`，如：$\Rightarrow$
23. 底端对齐的省略号，符号：`\ldots`，如：$1,2,\ldots,n$
24. 中线对齐的省略号，符号：`\cdots`，如：$x_1^2 + x_2^2 + \cdots + x_n^2$
25. 竖直对齐的省略号，符号：`\vdots`，如：$\vdots$
26. 斜对齐的省略号，符号：`\ddots`，如：$\ddots$

### （十三）希腊字母

| 字母 | 实现       | 字母 | 实现       |
| ---- | ---------- | ---- | ---------- |
| A    | `A`        | α    | `\alhpa`   |
| B    | `B`        | β    | `\beta`    |
| Γ    | `\Gamma`   | γ    | `\gamma`   |
| Δ    | `\Delta`   | δ    | `\delta`   |
| E    | `E`        | ϵ    | `\epsilon` |
| Z    | `Z`        | ζ    | `\zeta`    |
| H    | `H`        | η    | `\eta`     |
| Θ    | `\Theta`   | θ    | `\theta`   |
| I    | `I`        | ι    | `\iota`    |
| K    | `K`        | κ    | `\kappa`   |
| Λ    | `\Lambda`  | λ    | `\lambda`  |
| M    | `M`        | μ    | `\mu`      |
| N    | `N`        | ν    | `\nu`      |
| Ξ    | `\Xi`      | ξ    | `\xi`      |
| O    | `O`        | ο    | `\omicron` |
| Π    | `\Pi`      | π    | `\pi`      |
| P    | `P`        | ρ    | `\rho`     |
| Σ    | `\Sigma`   | σ    | `\sigma`   |
| T    | `T`        | τ    | `\tau`     |
| Υ    | `\Upsilon` | υ    | `\upsilon` |
| Φ    | `\Phi`     | ϕ    | `\phi`     |
| X    | `X`        | χ    | `\chi`     |
| Ψ    | `\Psi`     | ψ    | `\psi`     |
| Ω    | `\v`       | ω    | `\omega`   |