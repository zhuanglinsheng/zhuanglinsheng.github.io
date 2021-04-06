---
layout: post
title: "Normal Variance-Mean Mixture: Estimation"
use_math: true
lang: en
tags: notes
desc: I guess this paper, Belomestny and Panov (2018), is valuable since it provides with an overview of the estimation of distributions directly from the sample, which should be encountered in Machine Learning quite often. The Mellin transform technique is especially inspiring.
---

<br>

In this note I will summarize [Belomestny and Panov (2018)](https://arxiv.org/pdf/1705.07578.pdf). This paper provides a **non-parametric** way to estimate $\mu$ and $G$ of **normal variance-mean mixture** of the form: 


$$
p(x;\mu,G):=\int_{R_+}\phi_{\mathcal{N}(\mu s, s)}(x)G(ds)=\int_{R_+}\frac{1}{\sqrt{2\pi s}}\exp\left(-\frac{(x-\mu s)^2}{2s}\right)G(ds) \tag{1}
$$

or


$$
X\overset{d}{=}\mu s+\sqrt{s}\eta,\ \ \ \eta\sim N(0, 1) \tag{2}
$$


where $s$ is the normal variance distributed in $G$ and $\mu s$ is the normal mean. 

<br>

***Citation:*** 

Denis Belomestny and Vladimir Panov. (2018) Semiparametric estimation in the normal variance-mean mixture model, arXiv preprint:  [1705.07578v1](https://arxiv.org/pdf/1705.07578.pdf). 

<br>

#### 1. Estimate $\mu$ 

The equation (1) can be represented in 


$$
\begin{aligned}
p(x;\mu,G)&=\int_{R_+}\frac{1}{\sqrt{2\pi s}}\exp\left(-\frac{x^2-2x\mu s+\mu^2s^2}{2s}\right)G(ds)\\
&=\int_{R_+}\frac{1}{\sqrt{2\pi s}}\exp\left(-\frac{x^2}{2s}-\frac{\mu^2s}{2}+x\mu\right)G(ds)\\
&=e^{x\mu}\int_{R_+}\frac{1}{\sqrt{2\pi s}}\exp\left(-\frac{x^2}{2s}-\frac{\mu^2s}{2}\right)G(ds)\\
&=e^{x\mu}I_{\mu,G}(-x^2/2)
\end{aligned} \tag{4}
$$


where 


$$
I_{\mu,G}(u):=\int_{R_+}\frac{1}{\sqrt{2\pi s}}\exp\left(\frac{u}{s}-\frac{\mu^2}{2}s\right)G(ds)
$$

<br>

**Def. [An Estimation as Comparison].** The equation (4) implies that 

$$
p(-x;\mu,G)=e^{-x\mu}I_{\mu,G}(-x^2/2) \tag{5}
$$



thus, dividing (4) and (5), we get 


$$
\begin{aligned}
&\frac{e^{x\mu}}{e^{-x\mu}}=\frac{p(x;\mu,G)}{p(-x;\mu,G)}\\
\Rightarrow\ &\mu=\frac{1}{2x}\log\left(\frac{p(x;\mu,G)}{p(-x;\mu,G)}\right)\\
\Rightarrow\ &\mu=\int_{R_+}\frac{1}{2x}\log\left(\frac{p(x;\mu,G)}{p(-x;\mu,G)}\right)p(x;\mu,G)dx
\end{aligned}\tag{6,7}
$$

The last equation holds because taking expectation with respect to a scaler gets the number itself. (7) looks similar to the entropy of $p(\cdot;\mu,G)$, which is $H(p)=-\int_{R_+}\log\left(p(x;\mu,G)\right)p(x;\mu,G)dx$.  The methods of estimating differential entropy is listed in Extensions at the end of the notes.<br>

<br>

**Def. [Function $w$ and $W$].** Let $w(x)$ be a Lipschitz continuous function on $\mathbb{R}$ with <br>

(1) $w(x)\le 0$ for $x\ge 0$,  <br>

(2) $w(-x)=-w(x)$, <br>

(3) $\sup(w)\subset [-A,A]$ for some $A>0$. <br>

Set $W(\rho):=E(e^{-\rho X}w(X))$, where $\rho\in R$ and $X$ is distributed in $G$. <br>

**Assertion.** Then, $W(\rho)$ is monotone and $W(\mu)=0$. <br>

***Proof.*** Plug into (4) and we have that 

$$
W(\rho)=E(e^{-\rho X}w(X))=\int_R e^{-\rho x}w(x)\cdot e^{x\mu}I_{\mu,G}(-x^2/2)dx
$$


thus we know $W(\rho)$ is monotone simply by differentiating with respect to $\rho$. Also, 


$$
W(\mu)=\int_R w(x) I_{\mu,G}(-x^2/2)dx
$$


Since $x(.)$ is odd function and $I_{\mu,G}$ is even function, the integral equals to 0.<br>

<br>

**Def. [Estimation of $\mu$].** Without loss of generality we assume $\mu\in[0, M/2)$ for some $M>0$. Set 

$$
\mu_n:=\inf\{\rho>0: W_n(\rho)=0\} \land M \tag{8}
$$


with 


$$
W_n(\rho):=\frac{1}{n}\sum^{n}_{i=1}e^{-\rho X_i}w(X_i).
$$

where $x_i$ are drawn form $X\sim G$. <br>

**Assertion.** We have that $\lim_{\rho\to-\infty}W_n(\rho)\le 0$ and $\lim_{\rho\to\infty}W_n(\rho)\ge0$, and 


$$
W'_n(\rho)=\frac{1}{n}\sum^{n}_{i=1}(-X_i)e^{-\rho X_i}w(X_i)\ge 0
$$


for all $\rho\in\mathbb{R}$, the function $W_n(\rho)$ is thus monotone and $\mu_n$ is unique. <br>

***Proof.*** We first simply show $\lim_{\rho\to-\infty}W_n(\rho)\le 0$. When $x_i>0$, it is easy to see that $e^{-\rho x_i}\to\infty$, and $w(x_i)<0$, and their product is negative. When $x_i<0$, since $w(.)$ is bounded and $e^{-\rho x_i}\to0$, their product goes to $0$. Thus, we know the limit of $e^{-\rho x_i}w(x_i)$ is non-positive. When $x_i=0$, by the property of odd function we know $w(x_i)=0$. We can similar show that $\lim_{\rho\to\infty}W_n(\rho)\ge0$. <br>

Based on the property 2 of $w(.)$, we can easily verify $W'_n(\rho)\ge0$, and thus $W_n(\rho)$ is increasing. Thus, for any given $n$, there is a unique $\rho$ such that $W_n(\rho)=0$. <br>

<br>

**Theorem 2.1. [Convergence Speed].** Let $p\ge2$ and $M\ge0$ with 

$$
\Lambda(M, p):= ||(1+e^{-MX})Xw(X)||_p<\infty
$$


Then 


$$
||\mu_n-\mu||\le \frac{KM^{1-1/p}}{n^{1/2}}\left[\frac{1}{W'(\mu)}+\frac{1}{W(M/2)}\right]
$$


with a constant $K$ depending on $p$ and $\Lambda(M, p)$ only. <br>

***Proof.*** See appendix 7.1 of the paper. 

<br>

#### 2. Estimate $G$ 

In this section, we want to estimate the density function $g$ of $G$, from observations $x_1, x_2, ...$ of random variable $X\sim p(x;\mu,G)$, supposing $\mu$ is known. Based on the [introduction](https://zhuanglinsheng.github.io/paper_notes/2019/09/14/Normal-Variance-Mean-Mixture-Properties.html) note, we know the characteristic function of $X=\mu s+\sqrt{s}\eta $ is 


$$
\begin{aligned}
\phi_X(u)&=E(e^{iuX})=E(E(e^{iu(\mu s+\sqrt{s}\eta)}|s)) = E(e^{iu\mu s-su^2/2})\\
&=E(e^{s(iu\mu-u^2/2)})=E(e^{s\psi(u)})=L_s(\psi(u))
\end{aligned} \tag{9}
$$


where  $\psi(u)=u^2/2-iu\mu$, and $L_s(x):=E(e^{-s x})=\int_Re^{-sx}g(s)ds$ is the Laplace transform of r. v. $s\sim G$. See [wiki](https://encyclopedia.thefreedictionary.com/Characteristic+function+(probability+theory)) for the form of characteristic function of normal distribution. <br>

<br>

**Mellin Transformation of $L_s$.** More about Mellin transform and its inverse can be found in the extension part at the end of the note. Let 

$$
\mathcal{M}[L_s](z):=\int_{R_+} L_s(u)u^{z-1}du.
$$

**Mellin transform of $g$.** We have the collection between $\mathcal{M}[L_s]$ and $\mathcal{M}[g]$, 

$$
\begin{aligned}
M[L_s](z) &= \int_{R_+}u^{z-1}L_s(u)du=\int_{R_+}u^{z-1}\left( \int_{R_+}e^{-su}g(s)ds\right)du\\
&= \int_{R_+}g(s)\left(\int_{R_+}e^{-su}u^{z-1}du\right)ds\\
&= \int_{R_+}g(s)\left(\int_{R_+}e^{-(su)}(su)^{z-1}s^{-z+1}s^{-1}d(su)\right)ds\\
&= \int_{R_+}g(s)\left(\int_{R_+}e^{-v}v^{z-1}dv\right)s^{-z}ds\\
&= \Gamma(z) \cdot \int_{R_+}g(s)s^{-z}ds = \Gamma(z) \cdot \mathcal{M}[g](1-z)
\end{aligned}
$$



Thus we can estimate $\mathcal{M}[g]$ by 
$$
\mathcal{M}[g](z):=\frac{\mathcal{M}[L_s](1-z)}{\Gamma(1-z)}\tag{11}
$$


and finally, we apply the inverse Mellin transform to estimate $g$ of r. v. $s$. 


$$
\begin{aligned}
g(x)&=\frac{1}{2\pi}\int_R\mathcal{M}[g](\gamma+iv)\cdot x^{-\gamma-iv}dv\\
    &=\frac{1}{2\pi}\int_R\frac{\mathcal{M}[L_s](1-\gamma-iv)}{\Gamma(1-\gamma-iv)} \cdot x^{-\gamma-iv} dv
\end{aligned}
$$

<br>

**Statistics: Estimate $\mathcal{M}[L_{s}]$.** Now we want to estimate the Mellin transform.  First, by (9) and Cauchy's integral theorem, we know 

$$
\begin{aligned}
\mathcal{M}[L_s](z)&=\int_{R_+}L_s(u)u^{z-1}du=\int_l L_s(w)w^{z-1}dw\\
&=\int_{R_+}L_s(\psi(u))[\psi(u)]^{z-1}\psi'(u)du=\int_{R_+}\phi_X(u)[\psi(u)]^{z-1}\psi'(u)du
\end{aligned}\tag{A}
$$


where $l$ is the curve on the complex plain, defined as the image of $\psi(u)$, that is, $l$ is the set of points $w\in\mathbb{C}$ satisfying $\mathrm{Im}(w)=-\mu\sqrt{2\mathrm{Re}(w)}$. So that the Melin transform can be estimated from the data via 

$$
\begin{aligned}
\hat{\mathcal{M}}[L_s](z):=\int^{U_n}_0\phi_n(u)[\psi(u)]^{z-1}\psi'(u)du, \quad \mu\mathrm{Im}(z)<0,\\
\hat{\mathcal{M}}[L_s](z):=\int^{U_n}_0\overline{\phi_n(u)}\left[\overline{\psi(u)}\right]^{z-1}\overline{\psi'(u)}du, \quad \mu\mathrm{Im}(z)>0
\end{aligned}\tag{10}
$$


where 


$$
\phi_n(u)=\frac{1}{n}\sum^{n}_{k=1}e^{iuX_k}
$$

and $U_n$ is sequence of positive numbers tending to infinity as $n\to\infty$. <br>

<br>

<br>

<br>

#### Relative notes

[An inroduction to Normal variance-mean mixture](https://zhuanglinsheng.github.io/2019/09/14/NVMM-Properties.html) 

<br>

#### Further reading 

Estimation of $H(p)$:<br>

[1] [J. Beirlant, E. J. Dudewicz, L. Gyorfi and E. C. van der Meulen (2001)](http://jimbeck.caltech.edu/summerlectures/references/Entropy%20estimation.pdf).<br>

[2] [Laurent, B (1997)](https://projecteuclid.org/download/pdf_1/euclid.bj/1177526728).<br>

[3] [W.  Yeung (2010)](http://www.inc.cuhk.edu.hk/InformationTheory/files/Abridged/Ch_10.pdf).<br>

An Introduction to Mellin Transform:<br>

[1] [D. Zagier (notes)](http://people.mpim-bonn.mpg.de/zagier/files/tex/MellinTransform/fulltext.pdf).<br>

[2] [wikipedia: Mellin Transform](https://encyclopedia.thefreedictionary.com/Mellin+transform).<br>

[3] [wikipedia: Mellin Tranform Theory](https://encyclopedia.thefreedictionary.com/Mellin+inversion+theorem).<br>

About EM Algorithm:<br>

[1] [A. P. Dempster; N. M. Laird; D. B. Rubin (1977)](http://web.mit.edu/6.435/www/Dempster77.pdf).<br>

[2] [ C. F. Jeff Wu (1983)](http://web1.sph.emory.edu/users/hwu30/teaching/statcomp/papers/EM_converge.pdf).<br>

[3] [Angela Loregian, Lorenzo Mercuri, Edit Rroji (2011)](https://www.sciencedirect.com/science/article/pii/S0167715211003257).<br>

[4] [Fundamental Theorem of Gauss Quadrature (notes)](http://pluto.mscc.huji.ac.il/~mszucker/BINARY/gaussian_quadrature.pdf).<br>

[5] [Orthogonal Polynomials](http://mathworld.wolfram.com/OrthogonalPolynomials.html).<br>

[6] [Numpy Packages: polynomials.hermite](https://docs.scipy.org/doc/numpy/reference/routines.polynomials.hermite_e.html).<br>

[7] [Rostislav S. Protassov (2004)](https://link.springer.com/content/pdf/10.1023%2FB%3ASTCO.0000009419.12588.da.pdf).<br>

[8] [Wikipedia: Variance Gamma Distribution](https://encyclopedia.thefreedictionary.com/Variance-gamma+distribution).<br>

[9] [Wikipedia: General Hyperbolic Distribution](https://encyclopedia.thefreedictionary.com/generalised+hyperbolic+distribution).<br>

[10] [Wikipedia:  Generalized Inverse Gaussian Distribution](https://encyclopedia.thefreedictionary.com/Generalized+inverse+Gaussian+distribution).<br>

[11] [Denis Belomestny and Vladimir Panov. (2018)](https://arxiv.org/pdf/1705.07578.pdf)<br>

[12] [My notes about the above paper.](https://zhuanglinsheng.github.io/paper_notes/2019/09/17/Normal-Variance-Mean-Mixture-Statistics-1.html)<br>

[13] [R. G. Campos,  F. Mejia (2007): Quadrature formulas for the Laplace and Mellin transforms.](https://arxiv.org/pdf/0704.2842.pdf)<br>

[14] [Paul E. Saylor,  Dennis C. Smolarski (2000): Why Gaussian quadrature in the complex plane?](https://web.stanford.edu/class/cme335/spr11/saylorcomplex.pdf).<br>