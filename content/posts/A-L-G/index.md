+++
title = "关于对数平均不等式"
date = 2021-06-04T13:23:42.026Z
description = "对数平均不等式的证明以及应用"
draft = false
tags = [ "高中数学", "回归分析" ]
categories = [ "高中数学" ]
+++

**对数平均不等式**，也称算数-对数-几何平均值不等式、A-L-G 不等式（**A**rithmetic mean-**L**ogarithmic mean-**G**eometric mean inequality），是指对任意不相等的正实数 $a,b$，它们满足

$$
\frac{a+b}{2} > \frac{b-a}{\ln b-\ln a} > \sqrt{ab}
$$

其中 $\dfrac{b-a}{\ln b-\ln a}$ 被称为**对数平均值**。

## 证明

### 用柯西积分不等式证明

> 参考：[怎么理解对数均值不等式？ - Warlock的回答 - 知乎](https://www.zhihu.com/question/339199415/answer/1192504001)

根据柯西积分不等式（[证明]({{< ref "#柯西积分不等式的证明" >}})）

$$
\left[\int_a^b f(x)g(x)\ \mathrm{d}x\right]^2\le \int_a^b f^2(x)\ \mathrm{d}x\int_a^b g^2(x)\ \mathrm{d}x
$$

令 $f^2(x)= x$，$g^2(x)= \frac{1}{x}$，则有 $\left| f(x)g(x) \right| = 1$

代入柯西积分不等式得（$f(x)$ 与 $g(x)$ 线性无关，故等号不可取）

$$
\left( b-a \right)^2 < \frac{1}{2}\left( b^2-a^2 \right)\left( \ln b-\ln a \right)
$$

$b-a$ 与 $\ln b-\ln a$ 同正负，故 $(b-a)(\ln b -\ln a)>0$，不等式两边同时除以 $(b-a)(\ln b -\ln a)$ 得

$$
\frac{b-a}{\ln b-\ln a} < \frac{a+b}{2}
$$

令 $f(x) = \frac{1}{x}$，$g(x)=1$，则有 $\left| f(x)g(x) \right| = \frac{1}{x}$

代入柯西积分不等式得（$f(x)$ 与 $g(x)$ 线性无关，故等号不可取）

$$
\left( \ln b-\ln a \right)^2 < \left( \frac{1}{a} - \frac{1}{b}\right)\left( b-a \right)
$$

其中

$$
\left( \frac{1}{a} - \frac{1}{b}\right)\left( b-a \right) = \frac{(b-a)^2}{ab}
$$

所以

$$
ab < \frac{(b-a)^2}{(\ln b-\ln a)^2}
$$

即

$$
\sqrt{ab} < \frac{b-a}{\ln b-\ln a}
$$

### 高中知识证明

思路：由于 $a,b$ 是两个独立的变量，如果能够构造两个变量的比值（或差值）实现变量归一，那么就能利用导数证明此不等式。

不妨设 $b>a$，则

$$
\frac{a+b}{2} > \frac{b-a}{\ln b-\ln a} \\[8pt]
\Leftrightarrow (a+b)(\ln b-\ln a)>2(b-a) \\[8pt]
\Leftrightarrow \left(\frac{b}{a}+1\right) \ln \frac{b}{a}>2\left(\frac{b}{a}-1\right)
$$

设函数 $f(x)=(1+x) \ln x-2(x-1)\ (x>1)$，则

$$
f'(x)=\ln x+\frac{x+1}{x}-2=\frac{x \ln x-x+1}{x}
$$

令 $g(x)=x \ln x-x+1(x>1)$, 则 $g'(x)=\ln x>0$，所以 $g(x)$ 在 $(1,+\infty)$ 单调递增，$g(x)>g(1)=0$

所以 $f'(x)>0$，$f(x)$ 在 $(1,+\infty)$ 单调递增，$f(x)>f(1)=0$，故原不等式成立。

$$
\frac{b-a}{\ln b-\ln a} > \sqrt{ab} \\[8pt]
\Leftrightarrow \sqrt{\frac{b}{a}} - \sqrt{\frac{a}{b}} > \ln \frac{b}{a}
$$

设 $f(x)=x-\frac{1}{x}-\ln x^2 = x-\frac{1}{x}-2\ln x\ (x>1)$，则

$$
f'\left(x\right)= 1+\frac{1}{x^2}+\frac{2}{x}=\frac{(x+1)^2}{x} > 0
$$

所以 $f(x)$ 在 $(1,+\infty)$ 单调递增，$f(x)>f(1)=0$，故原不等式得证。

### 几何意义

![](A-L-G_1.svg)

图中曲线为 $y=\frac{1}{x}$，因为曲边梯形面积 $>$ 梯形面积 $=$ 矩形面积，所以

$$
\int_a^b \frac{1}{x}\ \mathrm{d}x > \frac{2}{a+b}(b-a)
$$

$$
\ln b-\ln a > \frac{2}{a+b}(b-a)
$$

$$
\frac{a+b}{2} > \frac{b-a}{\ln b-\ln a}
$$

![](A-L-G_2.svg)

图中曲线为 $y=\frac{1}{x}$，因为曲边梯形面积 $<$ 两个梯形面积之和，所以

$$
\ln b-\ln a < \frac{1}{2}\left(\frac{1}{a}+\frac{1}{\sqrt{ab}}\right)\left(\sqrt{ab}-a\right) + \frac{1}{2}\left(\frac{1}{\sqrt{ab}}+\frac{1}{b}\right)(b-\sqrt{ab}) \\[8pt]
=\frac{(\sqrt{ab}+a)(\sqrt{ab}-a)}{2 a\sqrt{ab}}+\frac{(b+\sqrt{ab})(b-\sqrt{ab})}{2 b \sqrt{a b}} \\[8pt]
=\frac{ab-a^2}{2 a\sqrt{ab}}+\frac{b^2-ab}{2 b \sqrt{a b}}=\frac{b-a}{2\sqrt{ab}}+\frac{b-a}{2\sqrt{a b}} =\frac{b-a}{\sqrt{a b}}
$$

所以

$$
\sqrt{a b}<\frac{b-a}{\ln b-\ln a}
$$

## 应用

To be continued...

## 柯西积分不等式的证明

由 $\left[f(x)+tg(x)\right]^2\ge 0$ 得

$$
\int_a^b \left[f(x)+tg(x)\right]^2 \mathrm{d}x \ge 0
$$

$$
\int_a^b f^2(x)\ \mathrm{d}x + 2t\int_a^b f(x)g(x)\ \mathrm{d}x + t^2\int_a^b g^2(x)\ \mathrm{d}x \ge 0
$$

将上式视为关于 $t$ 的不等式，则

$$
\Delta = 4\left[\int_a^b f(x)g(x)\ \mathrm{d}x\right]^2 - 4\int_a^b f^2(x)\ \mathrm{d}x\int_a^b g^2(x)\ \mathrm{d}x\le 0
$$

所以

$$
\left[\int_a^b f(x)g(x)\ \mathrm{d}x\right]^2\le \int_a^b f^2(x)\ \mathrm{d}x\int_a^b g^2(x)\ \mathrm{d}x
$$

上式称为**柯西积分不等式**。等号成立的充分必要条件是 $f(x)$ 和 $g(x)$ 线性相关，即 $f(x)$ 和 $g(x)$ 中有一个恒为零或存在常数 $t$ 使得 $f(x)=tg(x)$ 恒成立。（证明见[柯西施瓦兹不等式的积分形式等号成立的条件是什么呢？如何证明呢？ - 刘醉白的回答 - 知乎](https://www.zhihu.com/question/431329683/answer/1587501678)）
