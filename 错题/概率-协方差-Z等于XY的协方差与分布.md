---
type: 错题
domain: 概率论
topic: 协方差与分布
source: 学习册p78/例8
wrong_count: 1
difficulty:
last_review:
mastery: 未掌握
knowledge: [协方差, 泊松分布, 二维离散分布]
tags: [协方差, 泊松分布, Z=XY]
---

# 协方差与Z=XY的分布

## 题目
> 设随机变量 $X$ 与 $Y$ 相互独立, $X$ 的概率分布为 $P\{X=1\}=P\{X=-1\}=\frac{1}{2}$ , $Y$ 服从参数为 $\lambda$ 的泊松分布. 令 $Z=XY$.
>
> (1) 求 $\operatorname{Cov}(X,Z)$ .
> (2) 求 $Z$ 的概率分布.

## 正确答案
> **(1)**
> $$\operatorname{Cov}(X, Z) = \operatorname{Cov}(X, XY) = E(X^2Y) - E(X)E(XY).$$
>
> $$E(X^2Y) = E(X^2)E(Y) = \left[(-1)^2 \times \frac{1}{2} + 1^2 \times \frac{1}{2}\right] \lambda = \lambda.$$
>
> $E(X) = 0$，所以 $E(X)E(XY) = 0$。
>
> 故 $\operatorname{Cov}(X,Z) = \lambda$.
>
> **(2)** $X$ 取值为 $-1, 1$，$Y$ 取值为 $0, 1, 2, \dots$。$Z=XY$ 取值为 $0, \pm 1, \pm 2, \dots$。
>
> $$P\{Z=0\} = P\{Y=0\} = e^{-\lambda}.$$
>
> $$P\{Z=k\} = P\{X=1, Y=k\} = \frac{1}{2} \cdot \frac{\lambda^k}{k!} e^{-\lambda}, \quad k=1,2,\dots$$
>
> $$P\{Z=-k\} = P\{X=-1, Y=k\} = \frac{1}{2} \cdot \frac{\lambda^k}{k!} e^{-\lambda}, \quad k=1,2,\dots$$

## 错因
-

## 我的理解
> $E(X)=0$ 时 $\operatorname{Cov}(X,XY) = E(X^2Y)$ 大大简化计算。$Z=XY$ 的分布需考虑 $X$ 的正负号，正向和负向对称各占一半概率。

## 关联错题
-
