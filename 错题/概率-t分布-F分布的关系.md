---
type: 错题
domain: 概率论
topic: t分布与F分布
source: 学习册p107/例9
wrong_count: 1
difficulty:
last_review:
mastery: 未掌握
knowledge: [t分布, F分布, 典型模式]
tags: [t分布, F分布, 分位数]
---

# t分布与F分布的关系

## 题目
> 设随机变量 $X \sim t(n)$ , $Y \sim F(1, n)$ ，给定 $\alpha (0 < \alpha < 0.5)$ ，常数 c 满足 $P\{X > c\} = \alpha$ ，则 $P\{Y > c^{2}\} =$
>
> (A) $\alpha.$
> (B) $1 - \alpha$ .
> (C) $2\alpha$
> (D) $1 - 2\alpha$ .

## 正确答案
> $X \sim t(n)$，由 t 分布典型模式：$X = \frac{X_1}{\sqrt{Y_1/n}}$，其中 $X_1 \sim N(0,1), Y_1 \sim \chi^2(n)$，且独立。
>
> 因为 t 分布密度函数是偶函数，对 $\alpha \in (0, 0.5)$，$P\{X > c\} = \alpha$ 意味着 $P\{X < -c\} = P\{X > c\} = \alpha$。
>
> 又 $X^2 = \frac{X_1^2}{Y_1/n}$，$X_1^2 \sim \chi^2(1), Y_1 \sim \chi^2(n)$，故 $X^2 \sim F(1, n) \sim Y$。
>
> $$P\{Y > c^2\} = P\{X^2 > c^2\} = P\{X > c\} + P\{X < -c\} = 2\alpha.$$
>
> 答案选 **(C)**。

## 错因
-

## 我的理解
> 核心结论：$X \sim t(n)$ 时，$X^2 \sim F(1, n)$。t 分布的对称性使得双边尾概率为单边的两倍。

## 关联错题
- [[概率-统计量-两个正态样本的统计量分布]]
