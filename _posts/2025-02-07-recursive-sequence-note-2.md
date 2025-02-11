---
layout: post
title: 数列递推·笔记 2
#subtitle: 数列笔记 2
header-img: img/in-post/2020-10-07/header.jpg
header-style: text
catalog: true
tags:
  - sequence
  - maths
---


## 生成函数法

### 生成函数的定义

设$(a_n)$是一个数列, 一般来说, 它的生成函数是

$$G(a_n;x)=\sum_{n=0}^\infin a_nx^n.$$

生成函数（又叫母函数, 英文：Generating function）是一种形式幂级数, 其每一项的系数可以提供关于这个数列的信息。我们常常使用生成函数来解决诸如求通项公式和求和之类的问题.

### 生成函数的线性性

生成函数具有线性性, 即

$$G(\lambda a_n+\mu b_n;x)=\lambda G(a_n;x)+\mu G(b_n;x).$$

证：

$$\begin{align*}
G(\lambda a_n+\mu b_n;x)&=\sum_{n=0}^\infin(\lambda a_n+\mu b_n)x^n\\&=\lambda\sum_{n=0}^\infin a_nx^n+\mu\sum_{n=0}^\infin b_nx^n\\&=\lambda G(a_n;x)+\mu G(b_n;x).
\end{align*}$$

### 求生成函数的方法

以一个简单的数列为例, $a_{n+1}=2a_n+2$, 其中$a_1=1.$

为了求出$G(a_n;x)=\displaystyle\sum_{n=0}^\infin a_nx^n$, 我们将递推式两边同时乘$x^n$, 得

$$\dfrac1xa_{n+1}x^{n+1}=2a_nx^n+2x^n.$$

将$n$从$0$取到$\infin$并求和, 得

$$\dfrac1x\sum_{n=1}^\infin a_nx^n=2\sum_{n=0}^\infin a_nx^n+2\sum_{n=0}^\infin x^n.$$

并且

$$\sum_{n=1}^\infin a_nx^n=\sum_{n=0}^\infin a_nx^n-a_0=G(a_n;x)-a_0.$$

因此接下来要计算$\displaystyle\sum_{n=0}^\infin x^n.$

设

$$S=\sum_{n=0}^\infin x^n.$$

则

$$xS=\sum_{n=1}^\infin x^n=S-1$$

得

$$(1-x)S=1$$

即

$$S=\dfrac1{1-x}$$

得

$$\dfrac1x\left(G(a_n;x)-a_0\right)=2G(a_n;x)+\dfrac2{1-x}.$$

得

$$\begin{align*}
G(a_n;x)&=\dfrac{(2-a_0)x+a_0}{(1-x)(1-2x)}\\
&=\dfrac{-2}{1-x}+\dfrac{a_0+2}{1-2x}.
\end{align*}$$

另外, 根据递推公式$a_{n+1}=2a_n+2$以及$a_1=1$, 将$n$取为$0$, 得

$$1=a_1=2a_0+2.$$

得

$$a_0=-\dfrac12.$$

因此

$$\begin{align}
G(a_n;x)=\dfrac{-2}{1-x}+\dfrac{\dfrac32}{1-2x}.
\end{align}$$

### 利用生成函数求数列通项

以前例中的生成函数$(1)$为例, 根据线性性, 可以先求解第一项, 即需要将$\dfrac{-2}{1-x}$写成$\displaystyle\sum_{n=0}^\infin b_nx^n$的形式.

利用先前得到的

$$\sum_{n=0}^\infin x^n=\dfrac1{1-x},$$

得

$$\dfrac{-2}{1-x}=\sum_{n=0}^\infin (-2)x^n.$$

因此$(1)$式中的第一项对应的数列为$b_n=-2.$

同理, 对于第二项可以得到

$$\dfrac32\cdot\dfrac{1}{1-2x}=\dfrac32\sum_{n=0}^\infin(2x)^n=\sum_{n=0}^\infin\dfrac32\cdot2^nx^n.$$

于是第二项对应的数列为$\dfrac32\cdot2^n$也求出来了. 

因此, 所求的数列为

$$a_n=3\cdot2^{n-1}-2.$$


<hr>


下面以著名的$\mathrm{Fibonacci}$数列为例, $F_{n+2}=F_{n+1}+F_n$, 其中$F_1=F_2=1.$

先利用递推公式取$n=0$得$1=1+F_0.$ 于是$F_0=0.$

由$F_{n+2}=F_{n+1}+F_n$得

$$x^{-2}F_{n+2}x^{n+2}=x^{-1}F_{n+1}x^{n+1}+F_nx^n.$$

即得

$$x^{-2}(G(x)-F_0-F_1x)=x^{-1}(G(x)-F_0)+G(x).$$

解得

$$G(x)=\dfrac{x}{1-x-x^2}.$$

现在看起来并不好分解, 我们先分解分母, 即

$$\Delta=(-1)^2-4\times(-1)\times1=5, $$

$$x_{1, 2}=-\dfrac{1\pm\sqrt5}{2}.$$

即

$$1-x-x^2=-\left(x+\dfrac{1+\sqrt5}{2}\right)\left(x+\dfrac{1-\sqrt5}{2}\right).$$

设

$$\begin{align*}
G(x)&=\dfrac{-x}{x^2+x-1}=\dfrac{A}{x+\dfrac{1+\sqrt5}{2}}+\dfrac{B}{x+\dfrac{1-\sqrt5}{2}}\\
&=\dfrac{(A+B)x+\dfrac{1-\sqrt5}{2}A+\dfrac{1+\sqrt5}{2}B}{x^2+x-1}
.
\end{align*}$$

对比系数知

$$A+B=-1, \dfrac{1-\sqrt5}{2}A+\dfrac{1+\sqrt5}{2}B=0.$$

解得

$$A=-\dfrac1{\sqrt5}\dfrac{1+\sqrt5}{2}, B=\dfrac1{\sqrt5}\dfrac{1-\sqrt5}{2}.$$

即

$$\begin{align*}
G(x)&=\dfrac{\dfrac1{\sqrt5}\dfrac{1-\sqrt5}{2}}{x+\dfrac{1-\sqrt5}{2}}-\dfrac{\dfrac1{\sqrt5}\dfrac{1+\sqrt5}{2}}{x+\dfrac{1+\sqrt5}{2}}\\
&=\dfrac1{\sqrt5}\left(\dfrac{1}{1-\dfrac{1+\sqrt5}{2}x}-\dfrac{1}{1-\dfrac{1-\sqrt5}{2}x}\right)\\
&=\dfrac1{\sqrt5}\left(\sum_{n=0}^\infin\left(\dfrac{1+\sqrt5}{2}x\right)^n-\sum_{n=0}^\infin\left(\dfrac{1-\sqrt5}{2}x\right)^n\right)\\
&=\sum_{n=0}^\infin\dfrac1{\sqrt5}\left(\left(\dfrac{1+\sqrt5}{2}\right)^n-\left(\dfrac{1-\sqrt5}{2}\right)^n\right)x^n.
\end{align*}$$

因此

$$F_n=\dfrac1{\sqrt5}\left(\left(\dfrac{1+\sqrt5}{2}\right)^n-\left(\dfrac{1-\sqrt5}{2}\right)^n\right).$$








