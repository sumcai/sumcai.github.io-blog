## 数学公式表示

![show](assets/001/001/0003-1609335853763.jpeg)

## 文字方式(wiki暂不支持)

### 行内与独行

行内公式：符号：`$xyz$`，如： $xyz$  
独行公式：符号：`$$xyz$$`，如：$$xyz$$

### 上标、下标与组合

上标符号，符号：`x^4`，如：$x^4$  
下标符号，符号：`x_1`，如：$x_1$  
组合符号，符号：`${16}_{8}O{2+}_{2}$`，如：${16}_{8}O{2+}_{2}$  

### 占位符

两个quad空格，符号：`$x \qquad y$`，如：$x \qquad y$  
quad空格，符号：`$x \quad y$`，如：$x \quad y$  
大空格，符号`$x \ y$`，如：$x \ y$  
中空格，符号`$x : y$`:，如：$x : y$  
小空格，符号`$x , y$`,，如：$x , y$  
没有空格，符号`$xy$`，如：$xy$  
紧贴，符号`$x ! y$`，如：$x ! y$  

### 定界符与组合

括号，符号：`()\big(\big) \Big(\Big) \bigg(\bigg) \Bigg(\Bigg)`，如：$()\big(\big) \Big(\Big) \bigg(\bigg) \Bigg(\Bigg)$  
中括号，符号：`$[x+y]$`，如：$[x+y]$  
大括号，符号：`${x+y}$`，如：${x+y}$  
自适应括号，符号：`$\left(x\right)$，$\left(x{yz}\right)$`，如：$\left(x\right)$，$\left(x{yz}\right)$  
组合公式，符号：`${n+1 \choose k}={n \choose k}+{n \choose k-1}$`，如：${n+1 \choose k}={n \choose k}+{n \choose k-1}$  
组合公式，符号：`$\sum_{k_0,k_1,\ldots>0 \atop k_0+k_1+\cdots=n}A_{k_0}A_{k_1}\cdots$`，如：$\sum_{k_0,k_1,\ldots>0 \atop k_0+k_1+\cdots=n}A_{k_0}A_{k_1}\cdots$  

### 四则运算  

加法运算，符号：`$x+y=z$`，如：$x+y=z$  
减法运算，符号：`$x-y=z$`，如：$x-y=z$  
加减运算，符号：`$x \pm y=z$`，如：$x \pm y=z$  
减甲运算，符号：`$x \mp y=z$`，如：$x \mp y=z$  
乘法运算，符号：`$x \times y=z$`，如：$x \times y=z$  
点乘运算，符号：`$x \cdot y=z$`，如：$x \cdot y=z$  
星乘运算，符号：`$x \ast y=z$`，如：$x \ast y=z$  
除法运算，符号：`$x \div y=z$`，如：$x \div y=z$  
斜法运算，符号：`$x/y=z$`，如：$x/y=z$  
分式表示，符号：`$\frac{x+y}{y+z}$`，如：$\frac{x+y}{y+z}$  
分式表示，符号：`${x+y} \over {y+z}$`，如：${x+y} \over {y+z}$  
绝对值表示，符号：`$|x+y|$`，如：$|x+y|$  

### 高级运算

平均数运算，符号：`$\overline{xyz}$`，如：$\overline{xyz}$  
开二次方运算，符号：`$\sqrt x$`，如：$\sqrt x$  
开方运算，符号：`$\sqrt[3]{x+y}$`，如：$\sqrt[3]{x+y}$  
对数运算，符号：`$\log(x)$`，如：$\log(x)$  
极限运算，符号：`$\lim^{x \to \infty}_{y \to 0}{\frac{x}{y}}$`，如：$\lim^{x \to \infty}_{y \to 0}{\frac{x}{y}}$  
极限运算，符号：`$\displaystyle \lim^{x \to \infty}_{y \to 0}{\frac{x}{y}}$`，如：$\displaystyle \lim^{x \to \infty}_{y \to 0}{\frac{x}{y}}$  

求和运算，符号：`$\sum^{x \to \infty}_{y \to 0}{\frac{x}{y}}$`，如：$\sum^{x \to \infty}_{y \to 0}{\frac{x}{y}}$  
求和运算，符号：`$\displaystyle \sum^{x \to \infty}_{y \to 0}{\frac{x}{y}}$`，如：$\displaystyle \sum^{x \to \infty}_{y \to 0}{\frac{x}{y}}$  

积分运算，符号：`$\int^{\infty}_{0}{xdx}$`，如：$\int^{\infty}_{0}{xdx}$  
积分运算，符号：`$\displaystyle \int^{\infty}_{0}{xdx}$`，如：$\displaystyle \int^{\infty}_{0}{xdx}$  

微分运算，符号：`$\frac{\partial x}{\partial y}$`，如：$\frac{\partial x}{\partial y}$  

### 矩阵
使用 \begin{matrix}开头及\end{matrix}结尾，每行 \\结尾，每个元素 &分隔。
<pre>
$
\\begin{matrix}
  1 & 0 & 0 \\\\
  0 & 1 & 0 \\\\
  0 & 0 & 1 \\\\
\\end{matrix}
$
</pre>

- matrix
  
$$
\begin{matrix}
  1 & 0 & 0 \\\\
  0 & 1 & 0 \\\\
  0 & 0 & 1 \\\\
\end{matrix}
$$

- pmatrix

$$
\begin{pmatrix}
  1 & 0 & 0 \\\\
  0 & 1 & 0 \\\\
  0 & 0 & 1 \\\\
\end{pmatrix}
$$

- bmatrix

$$
\begin{bmatrix}
  1 & 0 & 0 \\\\
  0 & 1 & 0 \\\\
  0 & 0 & 1 \\\\
\end{bmatrix}
$$

- Bmatrix

$$
\begin{Bmatrix}
  1 & 0 & 0 \\\\
  0 & 1 & 0 \\\\
  0 & 0 & 1 \\\\
\end{Bmatrix}
$$

- vmatrix

$$
\begin{vmatrix}
  1 & 0 & 0 \\\\
  0 & 1 & 0 \\\\
  0 & 0 & 1 \\\\
\end{vmatrix}
$$

- Vmatrix

$$
\begin{Vmatrix}
  1 & 0 & 0 \\\\
  0 & 1 & 0 \\\\
  0 & 0 & 1 \\\\
\end{Vmatrix}
$$

### 多值函数

使用 cases 块表达式，每行 \\结尾，每个元素 & 分隔
<pre>
$
p(x) = 
\\begin{cases}
  p, & x = 1 \\\\
  1 - p, & x = 0
\\end{cases}
$
</pre>

$$
p(x) = 
\begin{cases}
  p, & x = 1 \\
  1 - p, & x = 0
\end{cases}
$$

### 逻辑运算
等于运算，符号：`$x+y=z$`，如：$x+y=z$  
大于运算，符号：`$x+y>z$`，如：$x+y>z$  
小于运算，符号：`$x+y<z$`，如：$x+y<z$  
大于等于运算，符号：`$x+y \geq z$`，如：$x+y \geq z$  
小于等于运算，符号：`$x+y \leq z$`，如：$x+y \leq z$  
不等于运算，符号：`$x+y \neq z$`，如：$x+y \neq z$  
不大于等于运算，符号：`$x+y \ngeq z$`，如：$x+y \ngeq z$  
不大于等于运算，符号：`$x+y \not\geq z$`，如：$x+y \not\geq z$  
不小于等于运算，符号：`$x+y \nleq z$`，如：$x+y \nleq z$  
不小于等于运算，符号：`$x+y \not\leq z$`，如：$x+y \not\leq z$  
约等于运算，符号：`$x+y \approx z$`，如：$x+y \approx z$  
恒定等于运算，符号：`$x+y \equiv z$`，如：$x+y \equiv z$

### 集合运算

属于运算，符号：`$x \in y$`，如：$x \in y$  
不属于运算，符号：`$x \notin y$`，如：$x \notin y$  
不属于运算，符号：`$x \not\in y$`，如：$x \not\in y$  
子集运算，符号：`$x \subset y$`，如：$x \subset y$  
子集运算，符号：`$x \supset y$`，如：$x \supset y$  
真子集运算，符号：`$x \subseteq y$`，如：$x \subseteq y$  
非真子集运算，符号：`$x \subsetneq y$`，如：$x \subsetneq y$  
真子集运算，符号：`$x \supseteq y$`，如：$x \supseteq y$  
非真子集运算，符号：`$x \supsetneq y$`，如：$x \supsetneq y$  
非子集运算，符号：`$x \not\subset y$`，如：$x \not\subset y$  
非子集运算，符号：`$x \not\supset y$`，如：$x \not\supset y$  
并集运算，符号：`$x \cup y$`，如：$x \cup y$  
交集运算，符号：`$x \cap y$`，如：$x \cap y$  
差集运算，符号：`$x \setminus y$`，如：$x \setminus y$  
同或运算，符号：`$x \bigodot y$`，如：$x \bigodot y$  
同与运算，符号：`$x \bigotimes y$`，如：$x \bigotimes y$  
空集，符号：`$\emptyset$`，如：$\emptyset$  

### 数学符号
无穷，符号：`$\infty$`，如：$\infty$  
虚数，符号：`$\imath$`，如：$\imath$  
虚数，符号：`$\jmath$`，如：$\jmath$  
数学符号，符号: `$\hat{a}$`，如：$\hat{a}$  
数学符号，符号: `\check{a}`，如：$\check{a}$  
数学符号，符号: `\breve{a}`，如：$\breve{a}$  
数学符号，符号: `\tilde{a}`，如：$\tilde{a}$  
数学符号，符号: `\bar{a}`，如：$\bar{a}$  
矢量符号，符号: `\vec{a}`，如：$\vec{a}$  
数学符号，符号: `\acute{a}`，如：$\acute{a}$  
数学符号，符号: `\grave{a}`，如：$\grave{a}$  
数学符号，符号: `\mathring{a}`，如：$\mathring{a}$  
一阶导数符号，符号: `\dot{a}`，如：$\dot{a}$  
二阶导数符号，符号: `\ddot{a}`，如：$\ddot{a}$  
上箭头，符号：`\uparrow`，如：$\uparrow$  
上箭头，符号：`\Uparrow`，如：$\Uparrow$  
下箭头，符号：`\downarrow`，如：$\downarrow$  
下箭头，符号：`\Downarrow`，如：$\Downarrow$  
左箭头，符号：`\leftarrow`，如：$\leftarrow$  
左箭头，符号：`\Leftarrow`，如：$\Leftarrow$  
右箭头，符号：`\rightarrow`，如：$\rightarrow$  
右箭头，符号：`\Rightarrow`，如：$\Rightarrow$  
底端对齐的省略号，符号：`$1,2,\ldots,n$`，如：$1,2,\ldots,n$  
中线对齐的省略号，符号：`$x_1^2 + x_2^2 + \cdots + x_n^2$`，如：$x_1^2 + x_2^2 + \cdots + x_n^2$  
竖直对齐的省略号，符号：`$\vdots$`，如：$\vdots$  
斜对齐的省略号，符号：`$\ddots$`，如：$\ddots$  

### 希腊字母

| 字母 | 实现       | 字母 | 实现       |
|----|----------|----|----------|
| A  | A        | α  | \alhpa   |
| B  | B        | β  | \beta    |
| Γ  | \Gamma   | γ  | \gamma   |
| Δ  | \Delta   | δ  | \delta   |
| E  | E        | ϵ  | \epsilon |
| Z  | Z        | ζ  | \zeta    |
| H  | H        | η  | \eta     |
| Θ  | \Theta   | θ  | \theta   |
| I  | I        | ι  | \iota    |
| K  | K        | κ  | \kappa   |
| Λ  | \Lambda  | λ  | \lambda  |
| M  | M        | μ  | \mu      |
| N  | N        | ν  | \nu      |
| Ξ  | \Xi      | ξ  | \xi      |
| O  | O        | ο  | \omicron |
| Π  | \Pi      | π  | \pi      |
| P  | P        | ρ  | \rho     |
| Σ  | \Sigma   | σ  | \sigma   |
| T  | T        | τ  | \tau     |
| Υ  | \Upsilon | υ  | \upsilon |
| Φ  | \Phi     | ϕ  | \phi     |
| X  | X        | χ  | \chi     |
| Ψ  | \Psi     | ψ  | \psi     |
| Ω  | \v       | ω  | \omega   |


