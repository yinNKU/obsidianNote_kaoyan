---
type: 错题
domain: 概率论
topic: 最大似然估计
source: 学习册p119/例4
wrong_count: 1
difficulty:
last_review:
mastery: 未掌握
knowledge: [最大似然估计, 均匀分布, 次序统计量]
tags: [MLE, 均匀分布, 顺序统计量]
---

# 均匀分布U[-θ,θ]的最大似然估计

## 题目
> 设总体 $X \sim U[-\theta, \theta]$ , $X_1, X_2, \cdots, X_n$ 是来自总体 X 的简单随机样本，试求参数 $\theta$ 的最大似然估计.

## 正确答案
> 似然函数为
> $$L(\theta) = \prod_{i=1}^{n} f(x_i) = \begin{cases} \frac{1}{(2\theta)^n}, & -\theta \leqslant x_1, x_2, \dots, x_n \leqslant \theta, \\ 0, & \text{其他}. \end{cases}$$
>
> $\theta$ 越小，$\frac{1}{(2\theta)^n}$ 越大，但 $\theta$ 必须满足
> $$\begin{cases} \theta \geqslant \max(x_1, \dots, x_n), \\ -\theta \leqslant \min(x_1, \dots, x_n) \end{cases} \quad \text{即} \quad \begin{cases} \theta \geqslant \max(x_1, \dots, x_n), \\ \theta \geqslant \max(-x_1, \dots, -x_n). \end{cases}$$
>
> 总之 $\theta \geqslant \max(|x_1|, |x_2|, \cdots, |x_n|)$，$\theta$ 又要尽量小。
>
> 故 $\hat{\theta} = \max(|X_1|, |X_2|, \cdots, |X_n|)$。

## 错因
-

## 我的理解
> 均匀分布的 MLE 不能用求导法，需用"边界约束 + 单调性"方法。$\theta$ 的取值范围由样本绝对值的最大值决定，似然函数关于 $\theta$ 递减，故取最小的可行值。

## 关联错题
-
