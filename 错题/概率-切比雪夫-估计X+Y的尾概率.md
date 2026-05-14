---
type: 错题
domain: 概率论
topic: 切比雪夫不等式
source: 学习册p88/例2
wrong_count: 1
difficulty:
last_review:
mastery: 未掌握
knowledge: [切比雪夫不等式, 期望, 方差, 相关系数]
tags: [切比雪夫不等式, 相关系数, 期望计算]
---

# 切比雪夫不等式估计X+Y

## 题目
> 设 $X$ 的概率密度函数为 $f(x), D(X) = 1$ , 而 $Y$ 的概率密度函数为 $f(-y)$ , 且 $X$ 与 $Y$ 的相关系数为 $-\frac{1}{4}$ , 用切比雪夫不等式估计 $P\{|X + Y| \geqslant 2\} \leqslant$ ____ .

## 正确答案
> $$E(X) = \int_{-\infty}^{+\infty} x f(x) \mathrm{d}x = \int_0^{+\infty} x[f(x) - f(-x)] \mathrm{d}x = 0.$$
>
> (由 $Y$ 密度为 $f(-y)$ 得 $E(Y) = -E(X) = 0$，故 $E(X+Y)=0$)
>
> $$D(X+Y) = D(X) + D(Y) + 2\operatorname{Cov}(X,Y)$$
>
> $D(Y) = D(X) = 1$，$\rho_{XY} = -\frac{1}{4}$，
> $$\operatorname{Cov}(X,Y) = \rho_{XY} \sqrt{D(X)D(Y)} = -\frac{1}{4}.$$
>
> $$D(X+Y) = 1 + 1 + 2 \times (-\frac{1}{4}) = \frac{3}{2}.$$
>
> 由切比雪夫不等式：
> $$P\{|X+Y| \geqslant 2\} = P\{|X+Y - 0| \geqslant 2\} \leqslant \frac{D(X+Y)}{2^2} = \frac{3/2}{4} = \frac{3}{8}.$$

## 错因
-

## 我的理解
> 关键两步：(1) 由 $f_Y(y)=f_X(-y)$ 推出 $E(Y)=-E(X)$；(2) 由相关系数反推协方差，再算 $D(X+Y)$。切比雪夫不等式 $P\{|X-\mu|\geqslant\varepsilon\} \leqslant D(X)/\varepsilon^2$。

## 关联错题
-
