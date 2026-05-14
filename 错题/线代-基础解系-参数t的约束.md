---
type: 错题
domain: 线性代数
topic: 基础解系
source: 练习册p44/14
wrong_count: 1
difficulty:
last_review:
mastery: 未掌握
knowledge: [基础解系, 线性无关, 矩阵]
tags: [基础解系, 参数约束, 矩阵表示]
---

# 基础解系的参数约束

## 题目
> 已知 $\alpha_{1}, \alpha_{2}, \alpha_{3}, \alpha_{4}$ 是 $Ax = 0$ 的一个基础解系，若 $\beta_{1} = \alpha_{1} + t\alpha_{2}, \beta_{2} = \alpha_{2} + t\alpha_{3}, \beta_{3} = \alpha_{3} + t\alpha_{4}, \beta_{4} = \alpha_{4} + t\alpha_{1}$，讨论实数 $t$ 满足什么关系时，$\beta_{1}, \beta_{2}, \beta_{3}, \beta_{4}$ 也是 $Ax = 0$ 的一个基础解系。

## 正确答案
> $\beta_i$ 显然是 $Ax=0$ 的解。又有：
>
> $(\beta_1,\beta_2,\beta_3,\beta_4) = (\alpha_1,\alpha_2,\alpha_3,\alpha_4)\begin{bmatrix}1&0&0&t\\t&1&0&0\\0&t&1&0\\0&0&t&1\end{bmatrix}$，
>
> 行列式 $= 1 - t^4$。所以 $t \neq \pm 1$ 时 $\beta_i$ 线性无关，构成基础解系。

## 错因
-

## 我的理解
> 看似是向量组问题，其实应该看成矩阵变换。用过渡矩阵表示新向量组，行列式不为零则线性无关。

## 关联错题
-
