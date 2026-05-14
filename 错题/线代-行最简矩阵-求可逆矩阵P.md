---
type: 错题
domain: 线性代数
topic: 行最简矩阵
source: 练习册p19/14
wrong_count: 1
difficulty:
last_review:
mastery: 未掌握
knowledge: [矩阵, 初等行变换]
tags: [行最简矩阵, 可逆矩阵, 初等变换]
---

# 行最简矩阵与可逆矩阵P

## 题目
> 已知 $A = \begin{bmatrix} 1 & -1 & -1 & 3 \\ 2 & -1 & -3 & 1 \\ 3 & 2 & -5 & 2 \end{bmatrix}$ ，化其为行最简矩阵 $F$，并求一个可逆矩阵 $P$，使 $PA = F$.

## 正确答案
> 对 $(A \mid E)$ 作初等行变换，得：
>
> 行最简矩阵 $F = \begin{bmatrix} 1 & 0 & 0 & 10 \\ 0 & 1 & 0 & 1 \\ 0 & 0 & 1 & 6 \end{bmatrix}$，
>
> $P = \frac{1}{3} \begin{bmatrix} 11 & -7 & 2 \\ 1 & -2 & 1 \\ 7 & -5 & 1 \end{bmatrix}$，有 $PA = F$.

## 错因
-

## 我的理解
> $(A \mid E)$ 经初等行变换 $\rightarrow (F \mid P)$，即左乘 $P$ 的效果等同于这些初等行变换的复合。关键在于增广矩阵同时记录变换过程。

## 关联错题
-
