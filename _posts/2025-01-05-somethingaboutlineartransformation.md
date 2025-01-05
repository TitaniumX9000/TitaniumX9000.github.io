---
layout: post
title:  "对向量基变换的一致理解"
date:   2025-01-05 12:46 +0800
categories: math
background: "/assets/images/europa-clipper-phone-backgrounds-03.png"
---

基变换和坐标变换一直是学线代以来个人觉得最反直觉的一部分, 为什么一个是右乘过渡矩阵, 一个是左乘过渡矩阵? 想了一晚上, 感觉理解的关键在于: **一个向量本身是不变的, 并不随采用的基的和相应的坐标的变化而变化**, 换言之, 是向量决定了坐标, 而不是坐标决定了向量, 坐标仅仅是对向量在基下的描述.

---
### 记号说明

本文考虑将向量分为两类, 并采用不同的记法:用粗体表示带有"方向"和"长度"含义的, 既是"形式上的"又是"实质上的"向量--**几何向量**; 而对于仅仅表示一个由标量构成的数组的, 仅仅是"形式上的"向量--**向量坐标**, 这里用字母加箭头表示.  
本文中所有形式上的向量均为**列**向量.

本文围绕
- 向量 $\boldsymbol{x}$ 
- $m$ 维线性空间 $V$, 以及该空间中的一组基 $\boldsymbol{A}=\begin{bmatrix}\boldsymbol{\alpha_1} & \boldsymbol{\alpha_2}&\boldsymbol{...} &\boldsymbol{\alpha_m}\end{bmatrix}$
- $n$ 维线性空间 $W$, 以及该空间中的一组基 $\boldsymbol{B}=\begin{bmatrix}\boldsymbol{\beta_1} & \boldsymbol{\beta_2}&\boldsymbol{...} &\boldsymbol{\beta_n}\end{bmatrix}$
- 线性映射 $T\in L(V, W)$ 及其对应的 $m\times n$ 实矩阵 $\boldsymbol{M}$  
- 基变换的过渡矩阵 $\boldsymbol{M^\prime}$

展开讨论.  

并将(用 $\boldsymbol{A}$ 表示出 $\boldsymbol{x}$)这一过程中使用的坐标记作 $\vec{a}=\begin{pmatrix}a_1&a_2&...&a_m\end{pmatrix}$, (用 $\boldsymbol{B}$ 表示出 $\boldsymbol{x}$)这一过程中使用的坐标记作 $\vec{b}=\begin{pmatrix}b_1&b_2&...&b_n\end{pmatrix}$

---
## 1. 用基和坐标定义向量

我们如何表示向量 $\boldsymbol{x}$? 一般都是用一个标量数组 $\vec{a}$. 但是这个标量数组只有在采用空间 $V$ 内的 基 $\boldsymbol{A}$ 的情形下才是与 $\boldsymbol{x}$ 对应的. 换言之, 一般地,  $\boldsymbol{x} \neq \vec{a}$, $\vec{a}$ 并不总是表示 $\boldsymbol{x}$.  
然而我们不难发现: 
$$\boldsymbol{x} = \boldsymbol{A}\vec{a}$$  
这表明: 单独指出坐标并不能完全定义一个向量; 完全定义向量还必须指明这个坐标使用的基. 因为 $\vec{a}$ 只能表示一个伸缩和组合的操作, 必须有一组基作为这个操作的作用对象.  
(也许你会感到奇怪: 为何平时我们并不区分本文中黑体的向量和箭头表达的向量? 其实是因为在不指明基的时候, 我们仍然默认使用了一类基--$\boldsymbol{I}$ , 即自然基, 也就是单位矩阵. 这样才有 $\boldsymbol{x} = \boldsymbol{I}\vec{a}=\boldsymbol{a}$, 只不过 $\vec{a}$ 和 $\boldsymbol{a}$ 被写成括号包围的一组数字的时候, 形式上恰好是完全一样的.)

可以形象地理解为: 相同的信息(**向量**)就是在特定的语境(**线性空间**)下对特定的语言(**基**)进行的特定组合(**坐标**).

---
## 2. 广义的基变换和坐标变换

现在我们考虑一个问题: 如何将(用原始基 $\boldsymbol{A}$ 可以表示为坐标 $\vec{a}$ 的)向量 $\boldsymbol{x}$ 使用目标基 $\boldsymbol{B}$ 表示为坐标 $\vec{b}$.  
自然的想法是, 先将原始基 $\boldsymbol{A}$ 中的所有基向量 $\boldsymbol{a_i}(i=1, 2, ..., m)$ 全部用目标基 $\boldsymbol{B}$ 表示出来, 从而(用基 $\boldsymbol{A}$ 下的坐标 $\vec{a}$ 表示的) $\boldsymbol{x}$ 自然也就用基 $\boldsymbol{B}$ 下的坐标 $\vec{b}$ 表示出来了.  

设

$$
\begin{align}
\boldsymbol{a_i} &= \sum\limits_{j=1}^{n}b_{ij}\boldsymbol{\beta_j}\\
&= \begin{bmatrix}\boldsymbol{\beta_1} & \boldsymbol{\beta_2}&\boldsymbol{...} &\boldsymbol{\beta_n}\end{bmatrix}\begin{bmatrix}b_{i1}\\b_{i2}\\...\\b_{in}\end{bmatrix}\\
&= \boldsymbol{B}\begin{bmatrix}b_{i1}\\b_{i2}\\...\\b_{in}\end{bmatrix}=\boldsymbol{B}\vec{b_i}
\end{align}
$$

($\vec{b_i}$ 为 $\boldsymbol{\alpha_i}$ 在 $\boldsymbol{B}$ 下的坐标), 则

$$\begin{align}
\boldsymbol{A} &=
\begin{bmatrix}
\boldsymbol{\alpha_1} & \boldsymbol{\alpha_2}&\boldsymbol{...} &\boldsymbol{\alpha_m}
\end{bmatrix}\\
&=
\begin{bmatrix}
\sum\limits_{j=1}^{n}b_{1j}\boldsymbol{\beta_j}&\sum\limits_{j=1}^{n}b_{2j}\boldsymbol{\beta_j}&\boldsymbol{...}&\sum\limits_{j=1}^{n}b_{nj}\boldsymbol{\beta_j}
\end{bmatrix}\\
&=\boldsymbol{B}
\begin{bmatrix}
\vec{b_1}&\vec{b_2}&...&\vec{b_i}
\end{bmatrix}
\\
&=\boldsymbol{B}
\begin{bmatrix}
b_{11}&b_{21}&\boldsymbol{...}&b_{n1}\\
b_{12}&b_{22}&\boldsymbol{...}&b_{n2}\\
\boldsymbol{...}&\boldsymbol{...}&\boldsymbol{...}&\boldsymbol{...}\\
b_{1m}&b_{2m}&\boldsymbol{...}&b_{nm}
\end{bmatrix}=\boldsymbol{BM}
\end{align}
$$

这样我们就得到了基的变换.  
这里我们使用目标基 $\boldsymbol{B}$ 表达原始基 $\boldsymbol{A}$, 然而在狭义的基变换情形下, $V=W$, 原始基 $\boldsymbol{A}$ 就是是自然基 $\boldsymbol{I}$, 而目标基的基向量却往往是用原始基表达的(这意味着变换矩阵 $\boldsymbol{M}$ 可逆), 所以过渡矩阵被定义为满足 $\boldsymbol{B}=\boldsymbol{AM^\prime}$ 的 $\boldsymbol{M^\prime}$, 也就是说 $\boldsymbol{M^\prime}=\boldsymbol{M^{-1}}$.

在等式两侧同时右乘坐标 $\vec{a}$, 即可得到 $\boldsymbol{x}$ 在基 $\boldsymbol{A}$ 下的定义 $\boldsymbol{x}=\boldsymbol{A}\vec{a}=\boldsymbol{BM}\vec{a}$. 又因为我们已经在基 $\boldsymbol{B}$ 下定义 $\boldsymbol{x}=\boldsymbol{B}\vec{b}$, 故有定义
$$
\boldsymbol{x}=\boldsymbol{A}\vec{a}=\boldsymbol{BM}\vec{a}=\boldsymbol{B}\vec{b}
$$
观察等式, 其中 $\boldsymbol{x}=\boldsymbol{BM}\vec{a}$ 可以理解为
$$\begin{align}
\boldsymbol{向量}&=\boldsymbol{目标基\times(从原始基到目标基的变换\times向量在原始基上的坐标)}\\&=\boldsymbol{目标基\times 向量在目标基上的坐标}
\end{align}
$$
- 如果采用第一个等号的理解方式,  $\boldsymbol{A}\vec{a}$ 和 $\boldsymbol{B}\vec{b}$ 和 $\boldsymbol{BM}\vec{a}$ 形式上不统一, 考虑和前面相同的思路, 我们可以将其改写成
    $$
    \boldsymbol{x}=\boldsymbol{AI}\vec{a}=\boldsymbol{BM}\vec{a}=\boldsymbol{BI}\vec{b}
    $$  
    $\boldsymbol{E}$ 表明原始基和目标基相同 
- 如果采用第二个等号的理解方式,  $\vec{a}$, $\boldsymbol{M}\vec{a}$, $\vec{b}$ 就是向量在目标基上的坐标. 这种方式与我们在前文中提及的对向量的定义是一致的  

综上所述, 基变换的目的是对一个向量进行不同方式的定义, 所以我们可以用定义向量的形式来统一基变换和其对应的坐标变换.

---
## 3. 基变换是一种特殊的线性映射

*(之所以不用"线性变换"这个词, 是因为"变换"给人一种原向量变成了新向量过后, 原向量就不存在了的感觉, 然而线性映射其实应该被理解为一种函数, 它在另一个线性空间(就像值域)内找了一个新的向量(因变量)与原空间(就像定义域)的向量(自变量)对应 所以用"映射"更为恰当. 特别地, 对于线性算子, 它也是将某个向量映射到了同一个空间内的另一个向量上, 也不是被"变换掉了".)*  

现在我们考虑一个与前面类似的问题: 如何将(在空间 $V$ 内用原始基 $\boldsymbol{A}$ 可以表示为坐标 $\vec{a}$ 的)向量 $\boldsymbol{x}$ 在映射 $T$ 下的像在空间 $W$ 内使用目标基 $\boldsymbol{B}$ 表示为坐标 $\vec{b}$.  
自然的想法是, 先将原始基 $\boldsymbol{A}$ 中的所有基向量 $\boldsymbol{a_i}(i=1, 2, ..., m)$ 在映射 $T$ 下的像全部用目标基 $\boldsymbol{B}$ 表示出来(即将这些基向量线性映射到 $W$ 内), 从而(用基 $\boldsymbol{A}$ 下的坐标 $\vec{a}$ 表示的) $\boldsymbol{x}$ 在映射 $T$ 下的像自然也就用基 $\boldsymbol{B}$ 下的坐标 $\vec{b}$ 表示出来了.  

仔细比对上面这一段话和基变换中的对应段落, 我们会发现基变换的过程中, 我们对**向量坐标**进行了一次线性映射(对应矩阵 $\boldsymbol{M}$, $\vec{b}=\boldsymbol{M}\vec{a}$), 将原**向量坐标**的线性空间映射到了另一个**向量坐标**的线性空间, 然后找到了后者的基, 使得原始基的**向量坐标**在线性映射下的像就是目标基的**向量坐标**, 而**几何向量**本身并不改变. 这样看来, 基变换对**向量坐标**满足加性和齐性, 是一种作用在**向量坐标**上的线性映射; 基变换的过渡矩阵 $\boldsymbol{(M^\prime)^{-1}}$ 的逆矩阵就是对**向量坐标**的线性映矩阵 $\boldsymbol{M}$ 是合理的.

---
最后感谢基于GPT-4o的ChatGPT帮我解释了为何基变换也是一种线性变换.  

Prompt: *我听说基变换也可以看作一种线性变换。但是对于一般的线性变换，因为基由原来的线性空间的基变成了新的向量空间的基，向量在该线性变换下的像的“方向”和“长度”往往会与原像不同。而基变换虽然新的基和原来的基不同，然而向量的“方向”和“长度”却并未改变，请问这应该如何解释呢？*  
GPT-4o: 
<img src="/assets/images/GPT-4o'sAnswer.png" alt="ChatGPT的回答" title="ChatGPT的回答" style="opacity:0.5;">

<br><br>
<div style="text-align: right;"><img src="{{ "/assets/images/winterbadge250x250.png" | relative_url }}" alt="winter" width="30" height="30"> <img src="{{ "/assets/images/favicon.svg" | relative_url }}" alt="Favicon" width="30" height="30"></div>