---
type: 错题
domain: 概率论
topic: 方差计算
source: 学习册p73/例6
wrong_count: 1
difficulty:
last_review:
mastery: 未掌握
knowledge: [方差, 拉普拉斯分布, 伽马积分]
tags: [方差, 拉普拉斯分布, 偶函数积分]
---

# 拉普拉斯分布的D(X²)计算

## 题目
> 已知随机变量 $X$ 的概率密度为 $f(x) = \frac{1}{2}\mathrm{e}^{-|x|}, -\infty < x < +\infty$ ，则 $D(X^2) =$
>
> (A) 20. (B) 22. (C) 24. (D) 28.

## 正确答案
> $D(X^2) = E(X^4) - [E(X^2)]^2$
>
> $$
> E(X^2) = \int_{-\infty}^{+\infty} x^2 \cdot \frac{1}{2} e^{-|x|} \mathrm{d}x = \int_0^{+\infty} x^2 e^{-x} \mathrm{d}x = 2! = 2,
> $$
>
> $$
> E(X^4) = \int_{-\infty}^{+\infty} x^4 \cdot \frac{1}{2} e^{-|x|} \mathrm{d}x = \int_0^{+\infty} x^4 e^{-x} \mathrm{d}x = 4! = 24,
> $$
>
> $$D(X^2) = 24 - 2^2 = 20.$$
>
> 答案选 **(A)**。

## 错因
-

## 我的理解
> 核心公式：$\int_0^{+\infty} x^n e^{-x} \mathrm{d}x = n!$。偶函数从 $-\infty$ 到 $+\infty$ 的积分可化为 2 倍从 $0$ 到 $+\infty$ 的积分，$e^{-|x|}$ 去绝对值后即为 $e^{-x}$。

## 关联错题
-
