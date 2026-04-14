下面给你一份 **数学常用 LaTeX 符号对照表**，可以直接在 **Obsidian** 的 `$...$` 或 `$$...$$` 中使用。内容主要覆盖 **高等数学 + 线性代数** 最常用符号，适合做笔记速查。

---

# 一、基本运算符号

|LaTeX|显示|含义|
|---|---|---|
|`+`|$+$|加|
|`-`|$-$|减|
|`\times`|$\times$|乘|
|`\cdot`|$\cdot$|点乘|
|`\div`|$\div$|除|
|`\pm`|$\pm$|正负|
|`\mp`|$\mp$|负正|

例：

```latex
$a \times b = c$
```

---

# 二、不等号与比较符号

|LaTeX|显示|
|---|---|
|`<`|$<$|
|`>`|$>$|
|`\le`|$\le$|
|`\ge`|$\ge$|
|`\neq`|$\neq$|
|`\approx`|$\approx$|
|`\equiv`|$\equiv$|

例：

```latex
$a \le b$
```

---

# 三、推导与逻辑符号

|LaTeX|显示|含义|
|---|---|---|
|`\rightarrow`|$\rightarrow$|推出|
|`\Rightarrow`|$\Rightarrow$|蕴含|
|`\Leftarrow`|$\Leftarrow$|反向蕴含|
|`\Leftrightarrow`|$\Leftrightarrow$|等价|
|`\iff`|$\iff$|当且仅当|
|`\therefore`|$\therefore$|因此|
|`\because`|$\because$|因为|

例：

```latex
$a>b \Rightarrow a^2>b^2$
```

---

# 四、集合符号

|LaTeX|显示|
|---|---|
|`\in`|$\in$|
|`\notin`|$\notin$|
|`\subset`|$\subset$|
|`\subseteq`|$\subseteq$|
|`\cup`|$\cup$|
|`\cap`|$\cap$|
|`\emptyset`|$\emptyset$|

例：

```latex
$x \in A$
```

---

# 五、常用数学运算

|LaTeX|显示|
|---|---|
|`\frac{a}{b}`|$\frac{a}{b}$|
|`a^2`|$a^2$|
|`a_i`|$a_i$|
|`\sqrt{x}`|$\sqrt{x}$|
|`\sqrt[n]{x}`|$\sqrt[n]{x}$|

例：

```latex
$\frac{a+b}{2}$
```

---

# 六、极限与求和

| LaTeX             | 显示                |
| ----------------- | ----------------- |
| `\lim_{x\to0}`    | $\lim_{x\to0}$    |
| `\sum_{i=1}^{n}`  | $\sum_{i=1}^{n}$  |
| `\prod_{i=1}^{n}` | $\prod_{i=1}^{n}$ |
| `\int`            | $\int$            |
| `\iint`           | $\iint$           |
| \infty            | $\infty$          |
|                   |                   |

例：

```latex
\lim_{x\to0}\frac{\sin x}{x}
```

---

# 七、希腊字母


| 名称      | 小写  | LaTeX      | 大写  | LaTeX      |     |
| ------- | --- | ---------- | --- | ---------- | --- |
| Alpha   | α   | `\alpha`   | Α   | `A`        |     |
| Beta    | β   | `\beta`    | Β   | `B`        |     |
| Gamma   | γ   | `\gamma`   | Γ   | `\Gamma`   |     |
| Delta   | δ   | `\delta`   | Δ   | `\Delta`   |     |
| Epsilon | ε   | `\epsilon` | Ε   | `E`        |     |
| Zeta    | ζ   | `\zeta`    | Ζ   | `Z`        |     |
| Eta     | η   | `\eta`     | Η   | `H`        |     |
| Theta   | θ   | `\theta`   | Θ   | `\Theta`   |     |
| Iota    | ι   | `\iota`    | Ι   | `I`        |     |
| Kappa   | κ   | `\kappa`   | Κ   | `K`        |     |
| Lambda  | λ   | `\lambda`  | Λ   | `\Lambda`  |     |
| Mu      | μ   | `\mu`      | Μ   | `M`        |     |
| Nu      | ν   | `\nu`      | Ν   | `N`        |     |
| Xi      | ξ   | `\xi`      | Ξ   | `\Xi`      |     |
| Omicron | ο   | `o`        | Ο   | `O`        |     |
| Pi      | π   | `\pi`      | Π   | `\Pi`      |     |
| Rho     | ρ   | `\rho`     | Ρ   | `P`        |     |
| Sigma   | σ   | `\sigma`   | Σ   | `\Sigma`   |     |
| Tau     | τ   | `\tau`     | Τ   | `T`        |     |
| Upsilon | υ   | `\upsilon` | Υ   | `\Upsilon` |     |
| Phi     | φ   | `\phi`     | Φ   | `\Phi`     |     |
| Chi     | χ   | `\chi`     | Χ   | `X`        |     |
| Psi     | ψ   | `\psi`     | Ψ   | `\Psi`     |     |
|         |     |            |     |            |     |
|         |     |            |     |            |     |
|Omega|ω|`\omega`|Ω|`\Omega`|
---

# 八、矩阵与行列式（线性代数）

### 矩阵

```latex
\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
```

显示：

$$  
\begin{pmatrix}  
a & b \  
c & d  
\end{pmatrix}  
$$

---

### 行列式

```latex
\begin{vmatrix}
a & b \\
c & d
\end{vmatrix}
```

显示：

$$  
\begin{vmatrix}  
a & b \  
c & d  
\end{vmatrix}  
$$

---

# 九、向量与线性代数符号

| LaTeX                 | 显示                   |
| --------------------- | -------------------- |
| `\vec{a}`             | $\vec{a}$            |
| `\mathbf{v}`          | $\mathbf{v}$         |
| `\langle x,y \rangle` | $\langle x,y\rangle$ |
| `\parallel`           | $\parallel$          |
| `\perp`               | $\perp$              |
| `\bar{A}`             | $\bar{A}$            |
| `\overline{A}`        | $\overline{A}$       |

---

# 十、数学证明常用符号

|LaTeX|显示|
|---|---|
|`\forall`|$\forall$|
|`\exists`|$\exists$|
|`\neg`|$\neg$|
|`\land`|$\land$|
|`\lor`|$\lor$|

例：

```latex
\forall x \in A
```

---

✅ **写 Obsidian 数学公式时最常用的 10 个符号**

基本每天都会用到：

```
\frac
\sum
\lim
\sqrt
\le
\ge
\neq
\Rightarrow
\iff
\lambda
```

---

💡 如果你愿意，我可以 **帮你整理一份专门给 Obsidian 用的 LaTeX 速查 Markdown 模板**（复制到笔记里直接查），并且包含：

- 线性代数专用公式
    
- 行列式展开
 \begin{vmatrix}
A & B \\
0 & C
\end{vmatrix}
- 矩阵模板
 \begin{pmatrix}
A & B \\
0 & C
\end{pmatrix}
 \begin{bmatrix}
A & B \\
0 & C
\end{bmatrix}
    
- 常用推导格式
    

写数学笔记会非常顺手。