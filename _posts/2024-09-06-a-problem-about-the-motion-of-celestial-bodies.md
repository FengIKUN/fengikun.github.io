---
layout: post
title: 一个关于天体运动的问题
#subtitle: 一个关于天体运动的问题
header-img: img/in-post/2020-10-07/header.jpg
header-style: text
catalog: true
tags:
  - the motion of celestial bodies
  - physics
---

### **Problem**  
木星是太阳系中质量最大的行星。假设地球和木星都在绕太阳的圆形轨道上运行，且它们的轨道共面。将太阳、地球和木星视为点质量，忽略太阳系中其他天体的引力影响，并假设在某些时刻地球与木星之间的引力可以忽略不计。设太阳和木星的质量分别为 $m_s$ 和 $m_j$，引力常数为 $\mathrm{G}$。地球和木星绕太阳的轨道半径分别为 $r_e$ 和 $r_j$。在某一时刻，设地球与太阳的连线与木星与太阳的连线之间的夹角为 $\theta$。如果在这一刻太阳的质量突然变为零，求：  

1. 地球相对于木星的速度大小 $v_{ej}$。  
2. 使地球不被木星的引力捕获所需的最小速度 $v_0$。  

---

### **Solution**  
由牛顿第二定律和万有引力定律可得, 

$$
\frac{\mathrm{G}m_s m_e}{r_e^2} = m_e \frac{v_e^2}{r_e}.
$$

整理得, 

$$
v_e = \sqrt{\frac{\mathrm{G}m_s}{r_e}}.
$$

同理可得, 

$$
v_j = \sqrt{\frac{\mathrm{G}m_s}{r_j}}.
$$

根据几何关系，地球相对于木星的速度为, 

$$
\begin{align*}
    v_{ej} &= \sqrt{v_e^2+v_j^2-2v_e v_j \cos\theta} \\
    &= \sqrt{\bigg(\frac{1}{r_e}+\frac{1}{r_j}-\frac{2\cos\theta}{\sqrt{r_e r_j}}\bigg)\mathrm{G}m_s}.
\end{align*}
$$

要防止地球被木星的引力捕获，必须满足, 

$$
\frac{1}{2}m_e v_0^2 - \frac{\mathrm{G}m_j m_e}{r_{ej}} = 0.
$$

解得, 

$$
v_0 = \sqrt{\frac{2\mathrm{G}m_j}{\sqrt{r_e^2 + r_j^2 - 2r_e r_j \cos\theta}}}.
$$
