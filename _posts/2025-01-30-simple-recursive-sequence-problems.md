---
layout: post
title: 数列递推·笔记 1
#subtitle: 数列笔记 1
header-img: img/in-post/2020-10-07/header.jpg
header-style: text
catalog: true
tags:
  - sequence
  - maths
---


所有数列记号的花括号无法显示，请自行脑补（.
{:.warning}


## 基础方法

如果递推公式可化为$a_{n+1}-a_{n}=f(n)$的形式，我们可以用累加的方法，利用

$$
\begin{align*}
a_n&=(a_n-a_{n-1})+(a_{n-1}-a_{n-2})+...+(a_2-a_1)+a_1\\&=\sum_{k=1}^{n-1}f(k)+a_1
\end{align*}
$$

得到${a_n}$的通项公式.

类似地，如果递推公式可化为$\dfrac{a_{n+1}}{a_{n}}=f(n)$的形式，我们可以用累乘的方法，利用

$$
\begin{align*}
a_n&=\dfrac{a_{n}}{a_{n-1}}\dfrac{a_{n-1}}{a_{n-2}}...\dfrac{a_{2}}{a_{1}}\cdot a_1\\&=\left(\prod_{k=1}^{n-1}f(k)\right)a_1
\end{align*}
$$

也可得到$a_n$的通项公式.


注意如果利用$a_n=S_n-S_{n-1}$, 则必须要求$n\geq2$.
{:.info}


**例1** 已知数列${a_n}$满足$a_1=1$, 前$n$项和为$S_n$，且$\forall n\in\mathbb{N},\ S_n=n^2a_n$, 求此数列的通项公式.

**解**

对$n\geq2$, 

$$a_n=S_n-S_{n-1}=n^2a_n-(n-1)^2a_{n-1}.$$

移项得

$$(n+1)(n-1)a_n=(n-1)^2a_{n-1}, $$

$$\dfrac{a_n}{a_{n-1}}=\dfrac{n-1}{n+1}.$$

则

$$
\begin{align*}
a_n&=\dfrac{a_{n}}{a_{n-1}}\dfrac{a_{n-1}}{a_{n-2}}...\dfrac{a_{2}}{a_{1}}a_1\\
&=\dfrac{n-1}{n+1}\dfrac{n-2}{n}\dfrac{n-3}{n-1}...\dfrac{2}{4}\cdot\dfrac{1}{3}\cdot1\\
&=\dfrac{2}{n(n+1)}
\end{align*}$$

而当$n=1$时, 经检验也满足该通项公式.

因此该数列得通项公式为

$$a_n=\dfrac{2}{n(n+1)}.$$

**例2** 已知数列${a_n}$满足$a_1=1,\ a_{n-1}-a_n=\dfrac{a_n}{n^2-1}$, 求此数列的通项公式.

**解**

$$\dfrac{a_n}{a_{n-1}}=\dfrac1{\left(1+\dfrac{1}{n^2-1}\right)}=\dfrac{n^2-1}{n^2}.$$

这时，有两种方法.

如果直接累乘，

$$\begin{align*}
a_n&=\dfrac{(n+1)(n-1)}{n^2}\dfrac{n(n-2)}{(n-1)^2}\dfrac{(n-1)(n-3)}{(n-2)^2}...\dfrac{4\times2}{3^2}\dfrac{3\times1}{2^2}\cdot1\\
&=\dfrac{n+1}{2n}.
\end{align*}$$

中间从$(n-1)$到$3$的项被全部约去，而分母上$n$和$2$只被约去了一次，分子上$(n+1)$没有被约去.
{:.info}

我们也可以将原式化为

$$\dfrac{na_n}{(n-1)a_{n-1}}=\dfrac{n+1}{n}.$$

如果我们令$b_n=na_n$, 则

$$\dfrac{b_n}{b_{n-1}}=\dfrac{n+1}{n}.$$

得

$$\begin{align*}
na_n=b_n&=\dfrac{n+1}{n}\dfrac{n}{n-1}\dfrac{n-1}{n-2}...\dfrac{4}{3}\cdot\dfrac{3}{2}\\
&=\dfrac{n+1}{2}.
\end{align*}$$

所以

$$a_n=\dfrac{n+1}{2n}.$$

## 推广

### 一阶线性递推

$$a_{n+1}=pa_n+q.$$

假设数列${a_n+t}$为等比数列，则

$$a_{n+1}+t=p(a_n+t).$$

即

$$a_{n+1}=pa_n+(p-1)t.$$

对比系数可知

$$(p-1)t=q.$$

即

$$t=\dfrac{q}{p-1}.$$

所以数列${a_n+\dfrac{q}{p-1}}$为等比数列, 公比为$p$，有

$$a_n+\dfrac{q}{p-1}=\left(a_1+\dfrac{q}{p-1}\right)p^{n-1}.$$

就得到数列${a_n}$的通项公式为

$$a_n=\left(a_1+\dfrac{q}{p-1}\right)p^{n-1}-\dfrac{q}{p-1}.$$

### 变式的一阶线性递推

**变式 1**

$$a_{n+1}=pa_n^r.$$

两边取对数得

$$\ln a_{n+1}=r\ln a_n + \ln p.$$

令$b_n=\ln a_n$，则$b_{n+1}=rb_n+p$，由前面的结论可知

$$b_n=\left(b_1+\dfrac{p}{r-1}\right)r^{n-1}-\dfrac{p}{r-1}.$$

即

$$a_n=\exp\left(\left(\mathrm{e}^{a_1}+\dfrac{p}{r-1}\right)r^{n-1}-\dfrac{p}{r-1}\right).$$

**变式 2**

$${a_{n+1}}=\dfrac{a_n}{pa_n+q}.$$

两边取倒数得

$$\dfrac{1}{a_{n+1}}=q\cdot\dfrac{1}{a_n}+p.$$

可知

$$a_n=\dfrac1{\left(\dfrac1{a_1}+\dfrac{p}{q-1}\right)q^{n-1}-\dfrac{p}{q-1}}.$$

**变式 3**

$$a_{n+1}=pa_n+qn+r$$

假设数列${a_n+sn+t}$是等比数列，则

$$a_{n+1}+s(n+1)+t=p(a_n+sn+t).$$

则

$$a_{n+1}=pa_n+(p-1)sn+pt-s-t.$$

对比系数知

$$(p-1)s=q,\; (p-1)t-s=r.$$

得

$$s=\dfrac{q}{p-1},\; t=\dfrac{(p-1)r+q}{p-1}$$

可知数列${a_n+sn+t}$是等比数列，公比为$p$，

$$a_n+sn+t=(a_1+s+t)p^{n-1}.$$

即

$$a_n=\left(a_1+\dfrac{(p-1)r+2q}{p-1}\right)p^{n-1}-\dfrac{q}{p-1}n-\dfrac{(p-1)r+q}{p-1}.$$





