+++
title = "二项分布方差的详细证明"
date = 2020-04-16T11:08:00
lastmod = 2020-04-16T11:12:00
description = "包你看懂"
draft = false
tags = [ "高中数学", "方差" ]
categories = [ "高中数学" ]
+++

## 前置技能

从组合数公式可以直接推出： $k\mathrm{C}_n^k = n\mathrm{C}_{n-1}^{k-1}$

同样地，你可以得到 $(k-1)\mathrm{C}_{n-1}^{k-1} = (n-1)\mathrm{C}_{n-2}^{k-2}$ ~~（禁止套娃）~~

你还要熟悉二项式定理：

$$
(p+q)^n = \sum_{k=0}^n \mathrm{C}_n^k p^k q^{n-k}
$$

你还要知道二项分布的概率和期望公式：

若 $X\sim B(n,p)$，则 $P(x = k) = \mathrm{C}_n^k \ p^k \ (1-p)^{n- k}$，$E(X) = np$

## 回归正题

第一步当然是定义式啦

$$
\begin{aligned}
D(X) &=\sum_{k=0}^{n}\left[k-E(X)\right]^{2} \cdot p_{k} \\
&=\sum_{k=0}^{n}(k-n p)^{2} \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k} \\
\end{aligned}
$$

看到 $(k-np)^2$ 是不是就很想把它拆开？

$$
\begin{aligned}
D(X) &=\sum_{k=0}^{n}(k^2-2knp+n^2p^2) \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k} \\
& =\color{Red}{\sum_{k=0}^{n} k^{2} \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k}} \\
&\quad -2np \color{Blue}{\sum_{k=0}^{n} k \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k}} \\
&\quad +n^2 p^2 \color{Green}{\sum_{k=0}^{n} \mathrm{C}_{n}^{k} p^{k} q^{n-k}}
\end{aligned}
$$

> 这式子也太长了吧 (＃°Д°)

首先你肯定会把魔爪伸向 $\color{Green}{\sum_{k=0}^{n} \mathrm{C}_{n}^{k} p^{k} q^{n-k}}$ —— 他就是个二项式定理嘛！

$$
\color{Green}{\sum_{k=0}^{n} \mathrm{C}_{n}^{k} p^{k} q^{n-k}} = (p+q)^n=1
$$

然后，你看到 $\color{Blue}{\sum_{k=0}^{n} k \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k}}$ 里面的 $\color{Blue}{k \cdot \mathrm{C}_{n}^{k}}$ 的时候，是不是有把 $\color{Blue}{k\cdot \mathrm{C}_n^k}$ 换成 $n\cdot\mathrm{C}_{n-1}^{k-1}$ 的冲动？

$$
\begin{aligned}
&\color{Blue}{\sum_{k=0}^{n} k \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k}} \\
=& \sum_{k=1}^{n} k \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k} \quad \text{（第一项是 0, 丢掉）}\\
=& \sum_{k=1}^{n} n \cdot \mathrm{C}_{n-1}^{k-1} p^{k} q^{n-k} \\
=& np \cdot \sum_{k=1}^{n} \mathrm{C}_{n-1}^{k-1} p^{k-1} q^{n-k} \\
=& np \cdot (p+q)^{n-1} \\
=& np
\end{aligned}
$$

现在只剩 $\color{Red}{\sum_{k=0}^{n} k^{2} \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k}}$ 了，首先你肯定会故技重施:

$$
\begin{aligned}
&\color{Red}{\sum_{k=0}^{n} k^{2} \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k}} \\
=& \sum_{k=1}^{n} k \cdot k \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k} \\
=& \sum_{k=1}^{n} kp \cdot n \cdot \mathrm{C}_{n-1}^{k-1} p^{k-1} q^{n-k} \\
=& np\sum_{k=1}^{n} k \cdot \mathrm{C}_{n-1}^{k-1} p^{k-1} q^{n-k}
\end{aligned}
$$

但是 $\mathrm{C}_{n-1}^{k-1} p^{k-1} q^{n-k}$ 前面还有个 $k$ 啊，不能用啊 (ノ｀Д)ノ

**所以，怎么把这个** $k$ **搞掉呢？？？**（我认为这是最难的一步，读者可以停下来思考思考）

你肯定想用 $(k-1) \mathrm{C}_{n-1}^{k-1} = (n-1) \mathrm{C}_{n-2}^{k-2}$，但人家是 $k\mathrm{C}_{n-1}^{k-1}$ 不是 $(k-1) \mathrm{C}_{n-1}^{k-1}$ 啊

那就……把 $k$ 拆成 $(k-1+1)$ 吧！~~（我真是太机智了）~~

$$
\begin{aligned}
& \color{Red}{np\sum_{k=1}^{n} k \cdot \mathrm{C}_{n-1}^{k-1} p^{k-1} q^{n-k}} \\
=& np\sum_{k=1}^{n} (k-1+1) \cdot \mathrm{C}_{n-1}^{k-1} p^{k-1} q^{n-k} \\
=& np\sum_{k=1}^{n} \left[(k-1) \mathrm{C}_{n-1}^{k-1} p^{k-1} q^{n-k} + \mathrm{C}_{n-1}^{k-1} p^{k-1} q^{n-k}\right] \\
=& np \left[\sum_{k=2}^{n} (k-1) \mathrm{C}_{n-1}^{k-1} p^{k-1} q^{n-k} + \sum_{k=1}^n \mathrm{C}_{n-1}^{k-1} p^{k-1} q^{n-k}\right] \\
=& np \left[\sum_{k=2}^{n} (n-1)p \cdot \mathrm{C}_{n-2}^{k-2} p^{k-2} q^{n-k} + (p+q)^{n-1}\right] \\
=& np \left[(n-1)p \cdot \sum_{k=2}^{n} \mathrm{C}_{n-2}^{k-2} p^{k-2} q^{n-k} + 1\right] \\
=& np \left[(n-1)p \cdot (p+q)^{n-2} + 1\right] \\
=& np \left[(n-1)p + 1\right] \\
=& np(np-p+1)
\end{aligned}
$$

终于！三个部分都推完了！！

$$
\begin{aligned}
&D(X) \\
=&\color{Red}{\sum_{k=0}^{n} k^{2} \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k}} \\
& -2np \color{Blue}{\sum_{k=0}^{n} k \cdot \mathrm{C}_{n}^{k} p^{k} q^{n-k}} \\
& +n^2 p^2 \color{Green}{\sum_{k=0}^{n} \mathrm{C}_{n}^{k} p^{k} q^{n-k}} \\
=& np(np-p+1) -2np\cdot np +n^2p^2 \\
=& np(1-p)
\end{aligned}
$$

证毕（￣︶￣）↗