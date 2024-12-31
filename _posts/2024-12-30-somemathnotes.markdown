---
layout: post
title:  "一些高数结论"
date:   2024-12-31 11:05:08 +0800
categories: review
background: "/assets/images/SnowyMountain.jpg"
---

在这里写一点鸡肋的微积分学结论--._食之无味, 弃之可惜_. 权当期末复习开胃菜和LaTex语法练习吧.

---  
## 三角函数和双曲函数

__三角恒等式__

令 $t=\tan{\frac{x}{2}}$ ,则有:

- $\sin x = \frac{2t}{1+t^2}$
- $\cos x=\frac{1-t^2}{1+t^2}$
- $\mathrm{d}x=\frac{2}{1+t^2}\mathrm{d}t$

记不住? 用更好记的正切半角公式"上差下和单正弦"得到两个方程 $\tan{\frac{x}{2}}=\frac{\sin x}{1+\cos x}=\frac{1-\cos x}{\sin x}$, 这样就很容易解出来了.

__反三角函数的关系__

- $\arcsin x =-\arcsin (-x)= \frac{\pi}{2}-\arccos x =\arccos \sqrt{1-x^2}$ (最后一个等号仅当 $x \geq 0$ 时成立, 可以通过换元 $x$ 为 $\cos t$ 证明)
- $\arccos x=\pi - \arccos(-x) =\frac{\pi}{2}-\arcsin x=\arcsin\sqrt{1-x^2}$ (最后一个等号仅当 $x \geq 0$ 时成立)
- $\arctan x = -\arctan (-x)=\frac{\pi}{2}-\text{arccot }x = \text{arccot }\frac{1}{x}$
- $\text{arccot }x= \pi - \arctan (-x) = \arctan\frac{1}{x}$

__三角和反三角函数的复合函数的化简__

化简这类式子的关键, 是考虑某一边长为1的直角三角形, 并设某内角为复合函数中的内函数, 进而凑出某函数与其反函数直接复合的形式(形如 $\tan\arctan x$, 可化简单为$x$ )列出方程求解.

__双曲函数及其关系__

与三角函数与单位圆相关有异曲同工之妙地, 双曲函数与单位等轴双曲线$x^2-y^2=1$息息相关. 与三角函数 $\cos \theta$ 和 $\sin \theta$ 类似地, $\cosh 2\theta$ 和 $\sinh 2\theta$ 分别对应了单位双曲线原点弦的横纵坐标, 考虑到双曲线在极坐标自变量 $\theta\in[\frac{\pi}{4}, \frac{3\pi}{4}]\cup[\frac{5\pi}{4}, \frac{7\pi}{4}]$ 时没有定义, $2\theta$ 对应某点极坐标自变量的两倍也是很自然的.

$\sinh x = \frac{\mathrm{e}^x-\mathrm{e}^{-x}}{2}$, $\cosh=\frac{\mathrm{e}^x+\mathrm{e}^{-x}}{2}$, 其他双曲函数的生成方式与三角函数完全相同.

- $\cosh^2 x -\sinh^2 x= 1$  

本来觉得这玩意和三角函数容易搞混淆, 结果发现有个神奇的规则可以直接让三角恒等式变成双曲恒等式:  
> _Osborn's rule_: 先将三角恒等式中的 $\sin$ 和 $\cos$ 分别换成 $\sinh$ 和 $\cosh$, 如果转换结果某项中有$n$个 $\sinh^2$ 因子, 再将该项乘 $(-1)^n$, 最终结果即为双曲恒等式.

不过在涉及倍角的情况下应用该规则易导致错误, 因为设及倍角的三角恒等式往往含有含 $\sin^2$ 因子的项.

__反双曲函数__

- $\sinh^{-1} x=\ln{(x+\sqrt{x^2+1})}$
- $\cosh^{-1} x=\ln{(x+\sqrt{x^2-1})} \left(x\in[1,\infty)\right)$

## 积分
__基本初等函数__
- $\int a^x \mathrm{d}x=\frac{a^x}{\ln a}+C$
- $\int \ln x \mathrm{d}x=x\ln x - x +C$
- $\int \csc^2 x\mathrm{d}x=-\cot x +C$
- $\int \sec\tan x \mathrm{d} x = \sec x+C$
- $\int \csc \cot x\mathrm{d}x = -\csc x+C$
- $\int \sec x\mathrm{d}x = \ln\left\vert\sec x+\tan x\right\vert+C=\frac{1}{2}\ln \frac{1+\sin x}{1-\sin x}+C$ _(这里个人更喜欢后者, 无需取绝对值且更容易得到)_
- $\int \csc x\mathrm{d}x=\frac{1}{2}\ln \frac{1-\cos x}{1+\cos x}+C=\ln \left\vert \csc x - \cot x \right\vert +C=\ln \left\vert\tan\frac{x}{2}\right\vert+C$

__有关$\mathrm{e}^x$__

- $\int \frac{\mathrm{d}x}{1+\mathrm{e}^x} = x-\ln(1+\mathrm{e}^x)+C$ (分子分母同时乘$\mathrm{e}^x$, 然后凑微分)
- $\int\mathrm{e}^x\sin x=\frac{\mathrm{e}^x}{2}(\sin x-\cos x)+C$
- $\int\mathrm{e}^x\cos x=\frac{\mathrm{e}^x}{2}(\sin x+\cos x)+C$

__有关 $x^2 \pm a^2$__

- $\int \frac{\mathrm{d}x}{a^2+x^2}=\frac{1}{a}\arctan \frac{x}{a}+C$
- $\int\frac{\mathrm{d}x}{\sqrt{a^2-x^2}}=\arcsin \frac{x}{a}+C$
- $\int \frac{\mathrm{d}x}{\sqrt{x^2 \pm a^2}} = \mathrm{ln}\left\vert x+\sqrt{x^2 \pm a^2}\right\vert +C$
- $\int \frac{x^2}{a^2+x^2}\mathrm{d}x=x-a\arctan\frac{x}{a}+C$
- $\int \frac{\mathrm{d}x}{(1+x^2)^2}=\frac{1}{2}\left(\arctan x+\frac{x}{x^2+1}\right)+ C$ (换元 $x$ 为 $\tan t$, 然后凑微分, 利用二倍角公式, 最后利用直角三角形化简三角和反三角函数的复合函数)
- $\int\frac{x^2}{(1+x^2)^2} \mathrm{d}x=\int\frac{(x^2-1)+1}{(x^2+1)^2}\mathrm{d}x=\frac{1}{2}\left(\arctan x-\frac{x}{x^2+1}\right)+ C$

__二项微分(形如 $x^m(a+bx^n)^p\mathrm{d}x$)__

> *Chebyshev theorem*: 对形如  
> 
> $$\int x^m(a+bx^n)^{p}\mathrm{d}x$$  
> 
> 的积分, 仅当 $p$ 或 $\frac{m+1}{n}$ 或 $p+\frac{m+1}{n}$ 为整数时可积.

具体而言, 
- 当 $p \in \mathbb{Z}$ 时, 换元 $x$ 为 $t^\lambda$, 其中 $\lambda$ 为分数 $m$ 和分数 $n$ 的分母的最小公倍数, 从而原式 $=\lambda\int t^{\lambda (m+1)-1}\left(a+bt^{\lambda n}\right)^{p}\mathrm{d}t$, 该函数为有理函数, 可积.  
  例如 $\int \frac{x^\frac{2}{3}}{\left(2+3x^\frac{1}{2}\right)^2}\mathrm{d}x=\int x^\frac{2}{3}\left(2+3x^{\frac{1}{2}}\right)^{-2}\mathrm{d}x=6\int t^9\left(2+3t^3\right)^{-2}\mathrm{d}t$... ~~_(绷不住了, 随便乱编的一个例子, 发现这玩意的结果及其丑陋)_~~
- 当 $\frac{m+1}{n}\in\mathbb{Z}$ 时, 将 $a+bx^n$ 换为 $t^\lambda$ (其中 $\lambda$ 为分数 $p$ 的分母), 从而原式 $=\frac{\lambda}{nb}\int t^{\lambda p+\lambda-1}\left(\frac{t^\lambda-a}{b}\right)^{\frac{m+1}{n}-1}\mathrm{d}t$, 该函数为有理函数, 可积.  
  例如 $\int x\left(1+x^\frac{2}{3}\right)^{-\frac{1}{2}}\mathrm{d}t=3\int \left(t^2-1\right)^{2}\mathrm{d}t=\frac{3}{5}x^5-2t^3+3t+C$  
- 当 $(\frac{m+1}{n}+p)\in \mathbb{Z}$ 时, 将 $\left(ax^{-n}+b\right)$ 换元为 $t^\lambda$ (其中 $\lambda$ 为分数 $p$ 的分母), 从而原式 $=-\frac{\lambda}{na}\int t^{\lambda p+\lambda-1}\left(\frac{t^\lambda-b}{a}\right)^{-\left(\frac{m+1}{n}+p\right)-1}\mathrm{d}t$, 该函数为有理函数, 可积.
## 微分

__Maclaurin's Series和等价无穷小__

- $\sin x=\sum\limits_{i=1}^\infty \frac{(-1)^{i-1}}{(2i-1)!}x^{2i-1}=x-\frac{x^3}{6}+o(x^3)$
- $\cos x=\sum\limits_{i=0}^\infty \frac{(-1)^i}{(2i)!}x^{2i}=1-\frac{x^2}{2}+o(x^2)$
- $\frac{1}{1-x}=\sum\limits_{i=0}^{\infty}x^i=1+x^2+x^3+o(x^3)$
- $\frac{1}{1+x}=\sum\limits_{i=0}^{\infty}(-1)^ix^i=1-x^2+x^3-o(x^3)$
- $\ln(1+x)=\sum\limits_{i=1}^\infty\frac{(-1)^{(i-1)}}{i}x^{i}=x-\frac{x^2}{2}+\frac{x^3}{3}-o(x^3)$
- $\sinh^{-1} x=\ln{\left(x+\sqrt{x^2+1}\right)}\sim \sinh x \sim x$
- $\log_a (1+x)\sim\frac{x}{\ln a}$
- $a^x-1\sim x\ln a$
- $\tan x-\sin x\sim \frac{1}{2}x^3$
- $\tan x - x\sim x-\arctan x\sim\frac{1}{3}x^3$
- $x-\sin x \sim \arcsin x-x\sim \frac{1}{6}x^3$

__对数求导法__

- $f^\prime(x)=f(x)(\ln f(x))^\prime$ 或 $\frac{\mathrm{d}f(x)}{\mathrm{d}x}=f(x)\frac{\mathrm{d}}{\mathrm{d}x}(\ln f(x))$




<br><br>
<div style="text-align: right;"><img src="{{ "/assets/images/winterbadge250x250.png" | relative_url }}" alt="winter" width="30" height="30"> <img src="{{ "/assets/images/favicon.svg" | relative_url }}" alt="Favicon" width="30" height="30"></div>