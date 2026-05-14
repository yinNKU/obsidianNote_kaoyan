---
type: 错题
domain: 线性代数
topic: 矩阵相似
source: 练习册p58/26
wrong_count: 1
difficulty:
last_review:
mastery: 未掌握
knowledge: [矩阵相似, 特征值, 行列式]
tags: [矩阵相似, 特征值, 行列式]
---

# 利用相似求矩阵和行列式

## 题目
> 已知三阶矩阵 $A$ 与三维向量 $x$，使得向量组 $x, Ax, A^{2}x$ 线性无关，且满足 $A^{3}x = 3Ax - 2A^{2}x$。
>
> (1) 记 $P = [x, Ax, A^{2}x]$，求三阶矩阵 $B$，使 $A = PBP^{-1}$；
> (2) 计算行列式 $|A + E|$。

## 正确答案
> (1) $AP = [Ax, A^{2}x, A^{3}x] = [Ax, A^{2}x, 3Ax-2A^{2}x] = P\begin{bmatrix}0&0&0\\1&0&3\\0&1&-2\end{bmatrix}$，故 $B = \begin{bmatrix}0&0&0\\1&0&3\\0&1&-2\end{bmatrix}$。
>
> (2) $A \sim B$，故 $|A+E| = |B+E| = \begin{vmatrix}1&0&0\\1&1&3\\0&1&-1\end{vmatrix} = -4$。

## 错因
-

## 我的理解
> 构造 $P$ 使得 $AP = PB$ 是相似关系的直接应用。不需要显式求出 $A$，利用相似不变性直接求 $|A+E|$。

## 关联错题
-
