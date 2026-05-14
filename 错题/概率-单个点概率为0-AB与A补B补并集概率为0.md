---
type: 错题
domain: 概率论
topic: 单个点概率为0
source: 学习册p12/例5
wrong_count: 1
difficulty:
last_review:
mastery: 未掌握
knowledge: [概率的加法公式, 对立事件概率]
tags: [单个点概率, 对立事件]
---

# AB与A补B补并集概率为0

## 题目
> 已知随机事件 $A, B$ 满足条件 $P(AB \cup \overline{A} \overline{B}) = 0$ , 则有
>
> (A) $A, B$ 为对立事件.
> (B) $A,B$ 互斥,但不对立.
> (C) $P(A)=P(B).$
> (D) $P(A)=P(\overline{B})$ .

## 正确答案
> $P(AB \cup \overline{A}\overline{B}) = 0$，则 $P(AB) = 0$ 同时 $P(\overline{A}\overline{B}) = 0$。
>
> $$
> \begin{aligned}
> 0 = P(\overline{A}\overline{B}) &= 1 - P(A \cup B) \\
> &= 1 - P(A) - P(B) + P(AB) \\
> &= 1 - P(A) - P(B) = -P(A) + P(\overline{B}),
> \end{aligned}
> $$
>
> 故 $P(A)=P(\overline{B})$。答案选 **(D)**。
>
> **评注**：选项(A)和(B)肯定不对，因为题设只给出概率条件，得不出事件关系的结论。选项(C)可举反例：取 $A = \varnothing, B = \Omega$，则 $P(AB \cup \overline{A}\overline{B}) = 0$ 但 $P(A) \neq P(B)$。

## 错因
-

## 我的理解
> 概率为0的条件只能推出概率等式，不能推出事件关系（如互斥、对立）。排除法在此类题中很有效。

## 关联错题
- [[概率-单个点概率为0-条件概率为1的推理]]
