+++
title = "高中数学柯西不等式的应用"
date = 2021-04-15T16:34:15.809Z
description = "四个模型：平方与一次转换、一次与分式转换、平方和为定值、和为定值"
draft = false
tags = [ "高中数学" ]
categories = [ "高中数学" ]
+++

## 柯西不等式

> **柯西不等式**是由大数学家奥古斯丁·路易·柯西（Augustin Louis Cauchy）在研究数学分析中的“流数”问题时得到的。但从历史的角度讲，该不等式应称作 Cauchy-Buniakowsky-Schwarz 不等式（柯西-布尼亚科夫斯基-施瓦茨不等式），因为后两位数学家彼此独立地把该不等式在积分学中推而广之，才将这一不等式应用到近乎完善的地步。

### 二维形式

$$
\left(a^2+b^2\right)\left(c^2+d^2\right) \geq(a c+b d)^2
$$

等号成立当且仅当 $a d=b c$ （即 $\frac{a}{c}=\frac{b}{d}$ 或 $c=d=0$）时。

#### 证明

##### 向量法

设 $\vec{m}=(a,b), \vec{n}=(c,d)$，两向量夹角为 $\theta$。

则 $|\vec{m}||\vec{n}|\cos \theta = \vec{m}\cdot\vec{n}$

所以 $|\vec{m}|^2|\vec{n}|^2\cos^2 \theta = (\vec{m}\cdot\vec{n})^2$

又因为 $0 \le \cos^2\theta \le 1$

所以 $|\vec{m}|^2|\vec{n}|^2 \ge (\vec{m}\cdot\vec{n})^2$

即 $\left(a^2+b^2\right)\left(c^2+d^2\right) \geq(a c+b d)^2$

##### 构造法

$$
\begin{aligned}
&\left(a^2+b^2\right)\left(c^2+d^2\right) \\
= & a^2c^2 + b^2d^2 + a^2d^2+b^2c^2 \\
= & (ac+bd)^2+(ad-bc)^2 \\
\geq & (a c+b d)^2 \quad (a, b, c, d \in \mathbb{R})
\end{aligned}
$$

等号当且仅当 $ad-bc=0$ 即 $ad=bc$。

### 一般形式

$$
\left(\sum_{i=1}^{n} a_{i}{ }^2\right) \left(\sum_{i=1}^{n} b_{i}{ }^2\right) \geq\left(\sum_{i=1}^{n} a_{i} b_{i}\right)^2
$$

等号成立当且仅当 $\frac{a_1}{b_1}=\frac{a_2}{b_2}=\cdots=\frac{a_{n}}{b_{n}}$ 或 $a_{i}, b_{i}$（$i=1,2,3, \cdots, n$）中有至少一方全为零。

#### 证明

不等式可以表示成

$(x_1^2+x_2^2+\cdots +x_{n}^2)(y_1^2+y_2^2+\cdots +y_{n}^2)\geq (x_1y_1+x_2y_2+\cdots +x_{n}y_{n})^2$

当 $x_i$（$i=1,2,3, \cdots, n$）或 $y_i$（$i=1,2,3, \cdots, n$）全部为零时，上式显然取到等号。下面考虑 $x_i, y_i$（$i=1,2,3, \cdots, n$）均不为零的情况。

考虑一个关于 $t$ 的一个一元二次方程 $(x_1t+y_1)^2+\cdots +(x_{n}t+y_{n})^2=0$ 

很明显的，此方程无实数解或有重根，故其判别式 $\Delta \leq 0$

注意到 $(x_1 t + y_1)^2 + \cdots + (x_n t + y_n)^2 \geq 0$

所以 $(x_1^2 +x_2^2 + \cdots + x_n^2) t^2 + 2 (x_1 y_1 + x_2 y_2 + \cdots + x_n y_n) t + (y_1^2 +y_2^2 + \cdots + y_n^2) \geq 0$

则 $\Delta = 4 (x_1 y_1 + x_2 y_2 + \cdots + x_n y_n)^2 - 4 (x_1^2 +x_2^2 + \cdots + x_n^2) (y_1^2 +y_2^2 + \cdots + y_n^2) \leq 0$

即 $(x_1^2 +x_2^2 + \cdots + x_n^2)(y_1^2 +y_2^2 + \cdots + y_n^2) \ge (x_1 y_1 + x_2 y_2 + \cdots + x_n y_n)^2$

而等号成立于判别式 $\Delta=0$ 时

也就是此时方程有重根，故 $\frac {x_1}{y_1} = \frac {x_2}{y_2} = \cdots = \frac {x_n}{y_n}$

## 应用

### 平方与一次转换

**例** 已知正数 $a,b$ 满足 $a+2b=3$，求 $4a^2+5b^2$ 的最小值。

**解** 运用柯西不等式 $\left[\left(2a\right)^2+\left(\sqrt5 b\right)^2\right]\left[\left(\frac{1}{2}\right)^2+\left(\frac{2}{\sqrt{5}}\right)^2\right] \ge \left(a+2b\right)^2$

即 $(4a^2+5b^2)(\frac{1}{4}+\frac{4}{5})\ge 3^2=9$

所以 $4a^2+5b^2\ge \frac{60}{7}$，最小值为 $\frac{60}{7}$

**例** 已知正数 $a,b$ 满足 $a^2+2b^2=4$，求 $a+3b$ 的最大值。

**解** 运用柯西不等式 $\left[a^2+\left(\sqrt2 b\right)^2\right]\left[1^2+\left(\frac{3}{\sqrt{2}}\right)^2\right] \ge \left(a+3b\right)^2$

即 $4\times(1+\frac{9}{2})\ge (a+3b)^2$

所以 $a+3b \le \sqrt{22}$，最大值为 $\sqrt{22}$

### 一次与分式转换

**例** 已知正数 $a,b$ 满足 $a+2b=3$，求 $\frac{4}{a}+\frac{5}{b}$ 的最小值。

**解** 运用柯西不等式 $\left[\left(\sqrt{a}\right)^2+\left(\sqrt{2b}\right)^2\right]\left[\left(\frac{2}{\sqrt{a}}\right)^2+\left(\frac{\sqrt{5}}{\sqrt{b}}\right)^2\right] \ge \left(2+\sqrt{10}\right)^2$

即 $3\left(\frac{4}{a}+\frac{5}{b}\right)\ge 14+4\sqrt{10}$

所以 $\frac{4}{a}+\frac{5}{b} \ge \frac{14+4\sqrt{10}}{3}$，最小值为 $\frac{14+4\sqrt{10}}{3}$

**例** 已知正数 $a,b$ 满足 $\frac{1}{a}+\frac{2}{b}=3$，求 $3a+b$ 的最小值。

**解** 运用柯西不等式 $\left[\left(\sqrt{3a}\right)^2+\left(\sqrt{b}\right)^2\right]\left[\left(\frac{1}{\sqrt{a}}\right)^2+\left(\frac{\sqrt{2}}{\sqrt{b}}\right)^2\right] \ge \left(\sqrt{3}+\sqrt{2}\right)^2$

即 $\left(3a+b\right)\times 3 \ge 5+2\sqrt{6}$

所以 $3a+b \ge \frac{5+2\sqrt{6}}{3}$，最小值为 $\frac{5+2\sqrt{6}}{3}$

### 平方和为定值

**例** （2017 年全国Ⅰ卷）10．已知 $F$ 为抛物线 $C:y^2=4x$ 的焦点，过作两条互相垂直的直线 $l_1$，$l_2$，直线 $l_1$ 与 $C$ 交于 $A$、$B$ 两点，直线 $l_2$ 与 $C$ 交于 $D$、$E$ 两点，则 $|AB|+|DE|$ 的最小值为（　　）
A.16　　B.14　　C. 12　　D.10

**解** $p=2$，设直线 $AB$ 的倾斜角为 $\alpha$，则直线 $DE$ 的倾斜角为 $\alpha+\frac{\pi}{2}$

使用结论：$|AB|=\frac{2p}{\sin^2\alpha}=\frac{4}{\sin^2\alpha}$，同理 $|DE|=\frac{4}{\sin^2(\alpha+\frac{\pi}{2})}=\frac{4}{\cos^2\alpha}$

> 结论推导见 [圆锥曲线与极坐标]({{< ref "conic-section-and-polar-coordinate-system/index.md" >}} "圆锥曲线与极坐标")

所以 $|AB|+|DE|=\frac{4}{\sin^2\alpha}+\frac{4}{\cos^2\alpha}=\left(\frac{4}{\sin^2\alpha}+\frac{4}{\cos^2\alpha}\right)\times 1=\left(\frac{4}{\sin^2\alpha}+\frac{4}{\cos^2\alpha}\right)\left(\sin^2\alpha+\cos^2\alpha\right)\geq(\frac{2}{\sin \alpha}\sin \alpha +\frac{2}{\cos\alpha}\cos \alpha)^2=(2+2)^2=16$ （柯西不等式）

### 和为定值

**例** 函数 $y=\frac{1}{\cos x}+\frac{9}{2-\cos x}\ (0<x<\frac{\pi}{2})$ 在何处取得最小值？最小值是？

**解** 令 $t=\cos x\ (0<t<1)$，则 $y=\frac{1}{t}+\frac{9}{2-t}$

运用柯西不等式 $\left(\frac{1}{t}+\frac{9}{2-t}\right)(t+2-t)\ge (1+3)^2$

即 $y\times 2\ge 16$，$y\ge 8$，当且仅当 $\frac{2-t}{t}=\frac{9t}{2-t}$，即 $t=\frac{1}{2}$，$x=\frac{\pi}{3}$ 时取等号。

所以函数在 $x=\frac{\pi}{3}$ 处取得最小值 $8$
