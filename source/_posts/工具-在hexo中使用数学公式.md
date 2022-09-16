---
layout: post
title: 在 Hexo 中使用数学公式
date: 2021-07-06 21:00:18
categories: 工具
---
## 用法
<!-- more -->

```js
var md = window.markdownit();
md.use(window.markdownitLatex2img,
  {style: "filter: opacity(75%);transform:scale(0.75);text-align:center;"} //可选
);
md.render(input.value);
```
## 1 数学公式
### 1.1 内联公式
**开头的`$`必须在其右边紧跟一个非空格字符，而结尾的`$`必须在其左边紧接一个非空格字符，并且不能紧跟一个数字。**
- 勾股定理: $a^2+b^2=c^2$
- 等差数列求和公式: $S_{n}=n a_{1}+\frac{n(n-1)}{2} d, n \in N^{*}$
- 牛顿-莱布尼茨公式: $\int_{a}^{b} f(x) d x=F(b)-F(a)=\left.F(x)\right|_{a} ^{b}$
- 二项分布: $P_{n}(k)=C_{n}^{k} p^{k} q^{n-k} \quad k=0,1,2 \ldots \ldots, n$
### 1.2 块公式
正态分布$X \sim N(\mu,\sigma^2)$:
$$f(x) = \frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$

斐波那契数列$A_n=A_{n-1}+A_{n-2}$,前后两项的比值逐渐收敛到黄金分割比例
$$\lim_{n\to \infty}\frac{A_{n-1}}{A_n}=\frac{\sqrt{5}-1}{2}.$$

因式分解
$$\begin{split}(x−1)(x−3)&=x^2−4x+3 \\
&=x^2−4x+4−1 \\
&=(x−2)^2−1
\end{split}
$$

狄利克雷函数

$$
D(x)=
\begin{cases}
1,& x \in Q \\
0,& x \notin Q
\end{cases}
$$

高斯公式
$$
\iiint_{\Omega}\left(\frac{\partial P}{\partial x}+\frac{\partial Q}{\partial y}+\frac{\partial R}{\partial z}\right) d v=\iint_{\Sigma} P d y d z+Q d z d x+R d x d y
$$

范德蒙行列式
$$D_{n-1}=\left|\begin{array}{cccc}
1 & 1 & \dots & 1 \\
x_{2} & x_{3} & \dots & x_{n} \\
\vdots & \vdots & & \vdots \\
x_{2}^{n-2} & x_{3}^{n-2} & \dots & x_{n}^{n-2}
\end{array}\right|=\prod_{2 \leq j<i \leq n}\left(x_{i}-x_{j}\right)$$

线性方程组
$$\left\{\begin{aligned}
a_{11} x_{1}+a_{12} x_{2}+\cdots+a_{1 n} x_{n} &=b_{1} \\
a_{21} x_{1}+a_{22} x_{2}+\cdots+a_{2 n} x_{n} &=b_{2} \\
\cdots \cdots \cdots \\
a_{m 1} x_{1}+a_{m 2} x_{2}+\cdots+a_{m n} x_{n} &=b_{m}
\end{aligned}\right.$$

## 2 物理公式
- 牛顿第一定律: $\sum \vec{F}_{i}=\frac{\mathrm{d} \vec{v}}{\mathrm{d} t}=0$
- 牛顿第二定律: $\vec{F}=\frac{\mathrm{d} m}{\mathrm{d} t} \vec{v}+m \frac{\mathrm{d} \vec{v}}{\mathrm{d} t}=\frac{\mathrm{d} m}{\mathrm{d} t} \vec{v}+m \vec{a}=\frac{\mathrm{d} m}{\mathrm{d} t} \vec{v}+m \frac{\mathrm{d}^{2} \vec{r}}{\mathrm{d} t^{2}}$
- 牛顿第三定律: $\overrightarrow{F_{12}}=-\overrightarrow{F_{21}}$
- 质能守恒: $E=mc^2$

万有引力定律: $F=\frac{G M m}{r^{2}}$
$$G \frac{m M}{(r+h)^{2}}=m \frac{\nu^{2}}{(r+h)}$$
基尔霍夫定律
$$\left[\frac{\partial\left(\Delta_{r} H_{m}\right)}{\partial T}\right]_{p}=\sum_{B} v_{B} C_{p, m}(B)$$
热力学第二定律
$$d S \geq \frac{\delta Q}{T}$$
## 3 化学公式
离子反应与沉淀: $\ce{SO4^2- + Ba^2+ -> BaSO4 v}$

氮气氢气合成氨
$$
\ce{N2 + 3H2 <=>T[高温、加压][催化剂] 2NH3}
$$

化学平衡常数:$\mathrm{Zn}+2 \mathrm{HCl}(\mathrm{aq})=\mathrm{H}_{2}+\mathrm{ZnCl}_{2} \quad(\mathrm{aq})$
$$K^{\theta}=\frac{\left[p\left(\mathrm{H}_{2}\right) / p^{\theta}\right]\left[c\left(\mathrm{ZnCl}_{2}\right)\right]}{c^{2}(\mathrm{HC})}$$

## 4 语法参考

[MathJax basic tutorial and quick reference](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)
