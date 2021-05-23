+++
title = "简单线性回归的相关公式与推导"
date = 2021-05-23T07:17:39.423Z
description = "最小二乘法估计参数、相关系数、相关指数"
draft = false
tags = [ "高中数学", "回归分析" ]
categories = [ "高中数学" ]
+++

> 参考 https://zhuanlan.zhihu.com/p/66261557

本文内容包括：

1. 简单线性回归中拟合直线的两个参数 $\hat{\beta_0},\hat{\beta_1}$ 的推导（最小二乘法）
2. 简单线性回归中对 $R^2$ 意义的一点个人理解
3. 推导 $R^2=r^2$

## 简单线性回归中拟合直线的两个参数 $\hat{\beta_0},\hat{\beta_1}$ 的推导

现在我们有一组数据点，比如说 $x$ 代表体重，$y$ 代表腹围，那么 $y$ 和 $x$ 之间的关系可以用下面的式子表示

$$
y=\beta_0+\beta_1x+u
$$

实际上我们不可能知道 $\beta_0$，$\beta_1$ 和 $u$，但是我们可以使用手上有限的数据推测出下面的线性方程

$$
\hat{y}=\hat{\beta_0}+\hat{\beta_1}x \tag{1}
$$

于是真实值 $y$ 和使用拟合直线预测出来的 $\hat{y}$ 之间就会有偏差，用 $\hat{u}=y-\hat{y}$ 表示这个偏差。

其实简单线性回归说白了就是根据手上的数据点想办法优化拟合直线的两个参数，让预测值 $\hat{y}$ 和真实值 $y$ 之间的偏差尽可能的小。也就是让 $\hat{u}$ 的总和尽可能的小。问题是如果直接把 $\hat{u}$ 相加，有些 $\hat{u}$ 可能为正，有些 $\hat{u}$ 可能为负，而且举一个极端的例子，令 $y=\bar{y}$ 作为拟合直线，这个时候的拟合水平相当于是最差的（在所有经过 $(\bar{x},\bar{y})$ 的直线中），但是根据平均值的性质，一组数据各项减去平均值差的和等于 0. 为了避免这个尴尬的局面，仿照方差的定义，我们把各个 $\hat{u}$ 都作一个平方，然后把平方求和：

$$
\sum{u^2}=\sum{(y-\hat{y})^2}=\sum{\left[y-\left(\hat{\beta_0}+\hat{\beta_1}x\right)\right]^2} \tag{2}
$$

所以接下来需要做的就是求 $(2)$ 式的极值。这个式子是一个二次方程，只有一个极小值，位于导数等于 $0$ 的地方。于是 $(2)$ 求最小值的问题可以通过对 $\hat{\beta_0}$ 和 $\hat{\beta_1}$ 分别求一阶导数，令一阶导数为 $0$ 就可以求出符合要求的两个参数了。

先看 $\hat{\beta_0}$

符合极值要求的方程如下：

$$
\frac{\partial \sum{u^2}}{\partial \hat{\beta_0}}=\sum{2\left(y-\hat{\beta_0}-\hat{\beta_1}x\right)(-1)}=0
$$

将 $2$ 和 $-1$ 两个常数消掉，于是方程左边等于：

$$
\begin{aligned}
& \sum{\left(y-\hat{\beta_0}-\hat{\beta_1}x\right)} \\
=& \sum{y}-\sum{\hat{\beta_0}}-\sum{\hat{\beta_1}x} \\
=& \sum{y}-n\hat{\beta_0}-\hat{\beta_1}\sum{x} \\
\end{aligned}
$$


由于 $\sum{y}=n\bar{y}$，$\sum{x}=n\bar{x}$，上面的方程可化为

$$
n\bar{y}-n\hat{\beta_0}-n\hat{\beta_1}\bar{x}=0
$$

所以 $\bar{y}-\hat{\beta_0}-\hat{\beta_1}\bar{x}=0$

即

$$
\bar{y}=\hat{\beta_0}+\hat{\beta_1}\bar{x} \tag{3}
$$

也就是说，根据极值的要求， 拟合直线必须经过 $(\bar{x},\bar{y})$ 这个点。

接下来看关于 $\hat{\beta_1}$ 的方程

$$
\frac{\partial \sum{u^2}}{\partial \hat{\beta_1}}=\sum{2\left(y-\hat{\beta_0}-\hat{\beta_1}x\right)(-x)}=0
$$

同样是消掉常数，把 $x$ 乘进各项：

$$
\sum{xy}-\sum{\hat{\beta_0}x}-\sum{\hat{\beta_1}x^2}=0
$$

将 $(3)$ 代入上式，方程左边等于

$$
\begin{aligned}
& \sum{xy}-\sum{\left(\bar{y}-\hat{\beta_1}\bar{x}\right)x}-\sum{\hat{\beta_1}x^2} \\
=& \sum{xy}-\sum{\left(\bar{y}x-\hat{\beta_1}\bar{x}x\right)}-\sum{\hat{\beta_1}x^2} \\
\end{aligned}
$$


将常数 $\bar{y},\bar{x},\hat{\beta_1}$ 提取出来：

$$
=\sum{xy}-\bar{y}\sum{x}+\hat{\beta_1}\bar{x}\sum{x}-\hat{\beta_1}\sum{x^2}
$$

同样，由于 $\sum{y}=n\bar{y}, \sum{x}=n\bar{x}$，上式

$$
=\sum{xy}-\bar{y}\cdot n\bar{x}+\hat{\beta_1}\bar{x}\cdot n\bar{x}-\hat{\beta_1}\sum{x^2}
$$

整理一下上面的式子，于是方程转化成下面的形式

$$
\left(\sum{xy}-n\bar{x}\bar{y}\right)-\hat{\beta_1}\left(\sum{x^2}-n\bar{x}^2\right)=0
$$

也就是说

$$
\hat{\beta_1}=\frac{\displaystyle\sum{xy}-n\bar{y}\bar{x}}{\displaystyle\sum{x^2}-n\bar{x}^2}
$$

在进一步转化以前，我们先看一下 $x$ 和 $y$ 的协方差 $\operatorname{Cov}(x,y)$（实际上是样本协方差 $\hat{\operatorname{Cov}(x,y)}$, 这里为了省事就不打 hat 了）是什么：

$$
\operatorname{Cov}(X,Y)=E\left[(X-E[X])(Y-E[Y])\right]
$$

不大严谨地说，对一组样本量为 $n$ 的数据的 $x$ 值（我们假定样本里面每一个数据出现的概率是均等的），$E(X)=\frac{1}{n}\sum x=\bar{x}$ , 于是

$$
\operatorname{Cov}(x,y)=\frac{1}{n}\sum{(x-\bar{x})(y-\bar{y})}
$$

做一下转换可以有

$$
\operatorname{Cov}(x,y)=\frac{1}{n}\sum{(xy-\bar{x}y-\bar{y}x+\bar{x}\bar{y})}
$$

其中

$$
\begin{aligned}
& \sum{(xy-\bar{x}y-\bar{y}x+\bar{x}\bar{y})} \\
=& \sum{xy}-\bar{x}\sum{y}-\bar{y}\sum{x}+\bar{y}\bar{x}\sum{1} \\
=& \sum{xy}-\bar{x}\cdot n\bar{y}-\bar{y}\cdot n\bar{x}+\bar{x}\bar{y}\cdot n \\
=& \sum{xy}-n\bar{x}\bar{y} \\
\end{aligned}
$$

所以 $\hat{\beta_1}$ 的分子实际上就是 $n\operatorname{Cov}(x,y)$.

接下来看一下分母部分，这个就更眼熟了，我们看一下方差的公式：

$$
\operatorname{Var}(X)=E\left[(X-E(X))^2\right]=\frac{1}{n}\sum({x-\bar{x}})^2
$$

其中

$$
\begin{aligned}
 & \sum({x-\bar{x}})^2 \\
=& \sum\left(x^2-2\bar{x}x+\bar{x}^2\right) \\
=& \sum{x^2}-2\bar{x}\sum{x}+\bar{x}^2\sum{1} \\
=& \sum{x^2}-2n\bar{x}^2+n\bar{x}^2 \\
=& \sum{x^2}-n\bar{x}^2 \\
\end{aligned}
$$

所以 $\hat{\beta_1}$ 的分母实际上就是 $n\operatorname{Var}(X)$. 综上，

$$
\hat{\beta_1}=\frac{n\operatorname{Cov}(x,y)}{n\operatorname{Var}(x)}=\frac{\operatorname{Cov}(x,y)}{\operatorname{Var}(x)} \tag{4}
$$

## 对于 $R^2$ 意义的一些个人理解

比如说现在我给你一组人（样本量为 $n$）的腹围数据（也就是上面提到的 $y$），除此以外什么都没有了。那现在你想要给出一个拟合直线，让所有的 $y$ 值到这个拟合直线的距离 $\hat{u}=y-\hat{y}$ 的平方的和尽可能的小。鉴于我们没有其他的参数（比如说体重 $x$）, 因此 $\hat{y}$ 只能设置成一个常数。于是现在我们最好的选择就是使用样本均值，毕竟根据平均值的性质： $\sum{(y-\hat{y})^2}$ 在 $\hat{y}=\bar{y}$ 的时候是最小的，而这个平方和我们记为 $\mathrm{TSS}$（Total Sum of Squares 总离差平方和/总平方和）

$$
\mathrm{TSS}=\sum{(y-\bar{y})^2}
$$

现在比如说，我们的数据集里增加了体重这一个参数（$x$），于是我们可以考虑根据 $x$ 对 $y$ 进行一个预测了，所以 $\hat{y}$ 不必再设置为一个常数，而是可以按照下面的式子去计算：

$$
\hat{y}=\hat{\beta_0}+\hat{\beta_1}x
$$

那么根据新的 $\hat{y}$ 推算出来的 $\hat{u}$ 平方的和我们记为 $\mathrm{RSS}$【Residual Sum of Squares 残差平方和，又名 Sum of Squared Residuals (SSR)、Sum of Squared Estimate of Errors (SSE)】

$$
\mathrm{RSS}=\sum{(y-\hat{y})^2}=\sum{\left[y-\left(\hat{\beta_0}+\hat{\beta_1}x\right)\right]^2}
$$

那么现在的 $\mathrm{TSS}$ 代表的是什么呢？也就是完全没有任何其他信息的时候，单纯从腹围这个变量自身出发可以得到的最低的误差平方和。而 $\mathrm{RSS}$ 又代表什么呢？它代表的是加入了 $x$ 这个变量以后，在已经做了最优化的设置（比如使用最小二乘法）之后，还会残留的误差的平方和。

于是有：

$$
R^2=\frac{\mathrm{TSS}-\mathrm{RSS}}{\mathrm{TSS}}
$$

这个 $R^2$ 的分子代表的是加入了 $x$ 这个变量以后，可以消除多少的误差（原有的全部误差平方和-剩下的误差平方和），分母就是原有的全部误差平方和。所以 $R^2$ 方代表的是加入 $x$ 变量以后，可以消除掉的误差平方和的一个比例。所以当 $R^2$ 接近 $0$ 的时候，就说明新加入的这个变量基本没什么用，而接近 $1$ 的时候，就说明这个新加入的变量大幅度的减少了预测的误差。

## $R^2$ 为什么等于相关系数 $r$ 的平方？

$r$ 也就是皮尔森相关系数，$r$ 的计算公式如下：

$$
r = \frac{\operatorname{Cov}(x,y)}{\sqrt{\operatorname{Var}(X)\operatorname{Var}(Y)}}
$$

$R^2$ 的公式：

$$
\begin{aligned}
R^2 &= \frac{\mathrm{TSS}-\mathrm{RSS}}{\mathrm{TSS}} \\
&= \frac{\sum{(y-\bar{y})^2}-\sum{(y-\hat{y})^2}}{\sum{(y-\bar{y})^2}} \\
\end{aligned} \tag{3.1}
$$

其中 

$$
\mathrm{TSS}=\sum{(y-\bar{y})^2}=n\operatorname{Var}(y)
$$

$$
\begin{aligned}
&\mathrm{RSS} \\
=&\sum{(y-\hat{y})^2} \\
=& \sum{\left[y-\left(\hat{\beta_0}+\hat{\beta_1}x\right)\right]^2} \\
=& \sum{\left[y-\left(\bar{y}-\hat{\beta_1}\bar{x}+\hat{\beta_1}x\right)\right]^2} \\
=& \sum{\left[(y-\bar{y})-\hat{\beta_1}(x-\bar{x})\right]^2} \\
=& \sum{\left[(y-\bar{y})^2+\hat{\beta_1}^2(x-\bar{x})^2-2\hat{\beta_1}(y-\bar{y})(x-\bar{x})\right]} \\
=& \sum{(y-\bar{y})^2}+\hat{\beta_1}^2\sum{(x-\bar{x})^2}-2\hat{\beta_1}\sum{(y-\bar{y})(x-\bar{x})} \\
=& n\operatorname{Var}(y)+\hat{\beta_1}^2n\operatorname{Var}(x)-2\hat{\beta_1}n\operatorname{Cov}(x,y) \\
=& n\operatorname{Var}(y)+\left(\frac{\operatorname{Cov}(x,y)}{\operatorname{Var}(x)}\right)^2n\operatorname{Var}(x)-2\frac{\operatorname{Cov}(x,y)}{\operatorname{Var}(x)}n\operatorname{Cov}(x,y) \\
=& n\operatorname{Var}(y)-n\frac{\operatorname{Cov}(x,y)^2}{\operatorname{Var}(x)} \\
\end{aligned}
$$


所以 $R^2$ 的分子为 $\mathrm{TSS}-\mathrm{RSS}=n\operatorname{Var}(y)-\left(n\operatorname{Var}(y) - n\dfrac{\operatorname{Cov}(x,y)^2}{\operatorname{Var}(x)}\right)=n\dfrac{\operatorname{Cov}(x,y)^2}{\operatorname{Var}(x)}$

分母为 $\mathrm{TSS} = n\operatorname{Var}(y)$

所以式 $(3.1)$ 可化为：

$$
R^2 = n\frac{\operatorname{Cov}(x,y)^2}{\operatorname{Var}(x)}\times \frac{1}{n\operatorname{Var}(y)}=\frac{\operatorname{Cov}(x,y)^2}{\operatorname{Var}(x)\operatorname{Var}(y)}
$$

又因为 $r = \dfrac{\operatorname{Cov}(x,y)}{\sqrt{\operatorname{Var}(X)\operatorname{Var}(Y)}}$

所以 $R^2=r^2$.

顺带一提，$\mathrm{ESS}$（Explained Sum of Squares 回归平方和/解释平方和）$= \sum{(\hat{y}-\bar{y})^2}$ ，而 $\hat{y}=\hat{\beta_0}+\hat{\beta_1}x=\bar{y}-\hat{\beta_1}\bar{x}+\hat{\beta_1}x$

所以 $\mathrm{ESS}=\sum{\left(\hat{\beta_1}(x-\bar{x})\right)^2}=\hat{\beta_1}^2\sum{(x-\bar{x})^2}=\left(\frac{\operatorname{Cov}(x,y)}{\operatorname{Var}(x)}\right)^2(n\operatorname{Var}(x))=n\frac{\operatorname{Cov}(x,y)^2}{\operatorname{Var}(x)}$

也就是 $R^2$ 的分子部分（$\mathrm{TSS-RSS}$）。即 $\mathrm{ESS=TSS-RSS}$

而且，其实 $R^2$ 等于 $r^2$ 的验证直接用 $R^2=\dfrac{\mathrm{ESS}}{\mathrm{TSS}}=\dfrac{\operatorname{Cov}(x,y)^2}{\operatorname{Var}(x)\operatorname{Var}(y)}$ 会来的更快呢。
