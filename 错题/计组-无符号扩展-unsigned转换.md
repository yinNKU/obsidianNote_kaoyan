---
type: 错题
domain: 计算机组成原理
topic: 无符号数扩展
source: 2012统考真题/27
wrong_count: 1
difficulty:
last_review:
mastery: 未掌握
knowledge: [无符号整数, 零扩展, 类型转换]
tags: [无符号扩展, unsigned, 零扩展]
---

# unsigned short 转 unsigned int

## 题目
> 假定编译器规定 int 型和 short 型长度分别为32位和16位，执行下列C语言语句：
>
> ```c
> unsigned short x = 65530;
> unsigned int y = x;
> ```
>
> 得到 y 的机器数为（）。
>
> A. 0000 7FFAH　B. 0000 FFFAH　C. FFFF 7FFAH　D. FFFF FFFAH

## 正确答案
> 16位无符号整数最大值 65535 = FFFFH。
>
> x = 65530 = FFFFH − 5 = FFFAH。
>
> 无符号数扩展：高位补 0（零扩展）。
>
> 故 y = 0000 FFFAH。
>
> C、D 高位补了1（符号扩展），排除。
>
> 故选 **B**。

## 错因
- 混淆了无符号扩展（零扩展）与有符号扩展（符号扩展）。

## 我的理解
> **零扩展 vs 符号扩展**：无符号数扩展高位一律补0；补码（有符号数）扩展高位复制符号位。本质原因：无符号数没有符号位概念，数值本身不依赖高位解释。

## 关联错题
- [[计组-符号扩展-16位扩32位]]
