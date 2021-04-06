---
layout: post
title: "Normal Variance-Mean Mixture: Introductions"
use_math: true
lang: en
tags: notes
desc: In this note, I will summarize the derivatives of main results of Barndrff-Nielson (1982), and do some extensions. The configuration of this note would be very doctrine and elusive, however, this is the only way that I find clear. 
---

<br>

In this note, I will summarize some basic conclusions of normal variance-mean mixture. The configuration of this note would be very doctrine and elusive, however, this is the only way that I find clear. Please check the references below if you want further studies. 

<br>

#### 1. Basics

***Citation:*** 

Barndorff-Nielsen, O. E., Kent, J., and Sørensen, M. (1982). Normal variance-mean mixtures
and z distributions. International Statistical Review/Revue Internationale de Statistique,
pages 145–159. doi: [10.2307/1402598](https://doi.org/10.2307/1402598).

<br>

**Def. [Normal mean-variance mixture].** Suppose $x$ is a random vector which, for a given $u\ge0$, follows an $r$-dimensional normal distribution with $x\sim\mathcal{N}(\mu+u\beta, u\Delta)$, where $\Delta$ is symmetric, positive-definite $r\times r$-matrix with determinant one, and $\mu$ and $\beta$ are vectors of dimension $r$. Suppose moreover that $u$ follows a probability distribution $F$ on $[0, +\infty)$. We say the distribution of $x$ is a *normal variance-mean mixture* with position $\mu$, drift $\beta$, structure matrix $\Delta$ and mixing distribution $F$. 

**Exp. [The meaning of $u$].** Here $u$ can be considered as a *random time*. 

**Cor. [The p.d.f. of $x$].** Now we derive the pdf of $x$. Suppose $g$ is the pdf of $x$, and $f(,)$ is the pdf of normal distribution given mean and variance, then it is obvious that 
$$
\begin{aligned}
g(x) = \int f(\mu+u\beta, u\Delta) F(du)
\end{aligned}
$$

Click [here](https://encyclopedia.thefreedictionary.com/Multivariate+normal+distribution) for the form of pdf of multivariate normal distribution $f$. Plug the form of $f$ into the above equation, and remember $\det(\Delta) = 1$, we get 

$$
\begin{aligned}
g(x) &= \int (2\pi)^{-r/2}\det(u\Delta)^{-1/2} \cdot e^{-\frac{1}{2}(x-\mu-u\beta)'(u\Delta)^{-1}(x-\mu-u\beta)}F(du)\\
     &= \int (2\pi u)^{-r/2} \cdot e^{-\frac{1}{2}(x-\mu)'(u\Delta)^{-1}(x-\mu)-\frac{1}{2}(u\beta)'(u\Delta)^{-1}(u\beta) + \frac{1}{2}(x-\mu)'(u\Delta)^{-1}(u\beta)+\frac{1}{2}(u\beta)'(u\Delta)^{-1}(x-\mu)}F(du)\\
     &= \int (2\pi u)^{-r/2} \cdot e^{-\frac{1}{2}(x-\mu)'(u\Delta)^{-1}(x-\mu)-\frac{1}{2}u\beta'\Delta^{-1}\beta+\frac{1}{2}(x-\mu)'\Delta^{-1}\beta+\frac{1}{2}\beta'\Delta^{-1}(x-\mu)}F(du)\\
     &= e^{(x-\mu)'\Delta^{-1}\beta} \cdot \int (2\pi u)^{-r/2} \cdot e^{-\frac{1}{2}(x-\mu)'(u\Delta)^{-1}(x-\mu)-\frac{1}{2}u\beta'\Delta^{-1}\beta} F(du)
\end{aligned}
$$

Notice that $(x-\mu)'\Delta^{-1}\beta$ is a scaler, and its transition is equal to itself. 

**Cor. [The characteristic function of $x$].**  We want to get the characteristic function of $x$ based on its distribution given by above. Click [here](https://encyclopedia.thefreedictionary.com/Characteristic+function+(probability+theory)) for more introductions to the characteristic function in probability theorem. This [note](http://www2.math.ethz.ch/finance/summerschool/partD.pdf) provides the general idea of coping with this kind of problems. Suppose $\theta$ is a $r-$dimensional column vector, we have 

$$
\begin{aligned}
\hat{g}(\theta) &= E(e^{i\theta'x}) = E(E(e^{i\theta'x}|u)) = E_u\left\{ \int e^{i\theta'x} f_N(x|u) dx \right\} \\
                &= E_u\left\{ \int (2\pi)^{-r/2}|u\Delta|^{-1/2} \cdot e^{i\theta'x} \cdot e^{-\frac{1}{2}(x-\mu-u\beta)'(u\Delta)^{-1}(x-\mu-u\beta)} dx \right\} \\
                &= E_u\left\{ e^{i\theta'\mu} \cdot \int (2\pi)^{-r/2}|u\Delta|^{-1/2} \cdot e^{i\theta'(x-\mu)} \cdot e^{-\frac{1}{2}(x-\mu-u\beta)'(u\Delta)^{-1}(x-\mu-u\beta)} d(x-\mu) \right\} \\
                &= e^{i\theta'\mu} \cdot E_u\left\{ \int (2\pi)^{-r/2}|u\Delta|^{-1/2} \cdot e^{i\theta'z-\frac{1}{2}(z-u\beta)'(u\Delta)^{-1}(z-u\beta)} dz \right\} \\
                &= e^{i\theta'\mu} \cdot E_u\left\{ \int (2\pi)^{-r/2}|u\Delta|^{-1/2} \cdot e^{-\frac{1}{2}(z-u\beta-iu\Delta\theta)'(u\Delta)^{-1}(z-u\beta-iu\Delta\theta)} dz \cdot e^{(i\beta'\theta-\frac{1}{2}\theta'\Delta'\theta)u} \right\} \\
                &= e^{i\theta'\mu} \cdot E_u\left(e^{i\theta'\beta u-\frac{1}{2}\theta'\Delta'\theta u}\right) \\
                &= e^{i\theta'\mu} \cdot \phi\left(i\theta'\beta-\frac{1}{2}\theta'\Delta'\theta\right)
\end{aligned}
$$

where $\phi$ is the moment generating function of $F$. 

**Cor. [First and second central moments].** Since we have the property of characteristic function, that 


$$
(-i)^k\phi^{(k)}_X(0) = (-i)^k \cdot \frac{d^k}{d\theta^k}E\left(e^{i\theta x}\right) = (-i)^k \cdot E\left([ix]^ke^0\right) = E(x^k)
$$


we have 

$$
\begin{aligned}
E(x) &= -i \cdot \left[ e^{i\theta'\mu} \cdot i\mu \cdot \phi\left(i\theta'\beta-\frac{1}{2}\theta'\Delta'\theta\right)+e^{i\theta'\mu}\phi'\left(i\theta'\beta-\frac{1}{2}\theta'\Delta'\theta\right)(i\beta-\Delta\theta) \right] \\
&= -i \cdot \left[ i\mu+Eu\cdot i\beta \right] = \mu + Eu\cdot\beta
\end{aligned}
$$

and 


$$
\begin{aligned}
E(XX') &= \mu\mu'+\mu\beta'Eu+\mu\beta'Eu+Vu\beta\beta'+Eu\Delta\\
&=(-i)^2 \cdot \bigg[ (i\mu)^2e^{i\theta'\mu}\phi(i\theta'\beta-\frac{1}{2}\theta'\Delta'\theta)+i\mu e^{i\theta'\mu}\phi'(i\theta'\beta-\frac{1}{2}\theta'\Delta'\theta)(i\beta-\Delta\theta)\\
&\quad + i\mu e^{i\theta'\mu}\phi'(i\theta'\beta-\frac{1}{2}\theta'\Delta'\theta)(i\beta-\Delta\theta)\\
&\quad + e^{i\theta'\mu}\phi''(i\theta'\beta-\frac{1}{2}\theta'\Delta'\theta) (i\beta-\Delta\theta)(i\beta-\Delta\theta)'\\
&\quad + e^{i\theta'\mu}\phi''(i\theta'\beta-\frac{1}{2}\theta'\Delta'\theta) (i\beta-\Delta\theta)(i\beta-\Delta\theta)'
\end{aligned}
$$


Thus, the variance of $x$ is 


$$
V(X) = E(XX')-E(X)E(X)' = \left[Eu^2-EuEu'\right]\beta\beta' + Eu\Delta = Vu\beta\beta' + Eu\Delta
$$

Higher order moments can also be derived. Here we do not derive the general form. In the following sections we can derive the moments for each distributions with Lapalce transform. 

<br>

#### 2. Normal Inverse Gaussian Distribution

***Citation:*** 

Folks, J. L. and Chhikara, R. S. (1978). The inverse gaussian distribution and its statistical
applicationa review. Journal of the Royal Statistical Society: Series B (Methodological),
40(3):263–275. doi: [10.1111/j.2517-6161.1978.tb01039.x](https://doi.org/10.1111/j.2517-6161.1978.tb01039.x).

<br>

When the random vector has only one element, meaning that $X$ is a scaller, and the mixing distribution is inverse Gaussian, 


$$
\begin{aligned}
f_{IG}(x | \gamma, \sigma, a) &=\frac{a}{\sigma\sqrt{2\pi x^3}}\exp\left(-\frac{(\gamma x-a)^2}{2x\sigma^2}\right), \quad x>0,\\
&=0, \quad \text{otherwise},
\end{aligned}
$$

we say $X$ is normal inverse Gaussian distribution ([Folks, J. L. and Chhikara, R. S. 1978](https://doi.org/10.1111/j.2517-6161.1978.tb01039.x)). The above form can be re-parameterized with 


$$
\xi = a/\gamma \quad \text{and} \quad \lambda=a^2/\sigma^2
$$


which gives 


$$
\begin{aligned}
f_{IG}(x | \xi, \lambda) &= \sqrt{\frac{\lambda}{2\pi x^3}}\exp\left\{-\frac{\lambda(x-\xi)^2}{2\xi^2x}\right\}, \quad x>0,\\
&= 0, \quad \text{otherwise}.
\end{aligned}
$$


The density of normal variance-mean mixture can be expressed by 


$$
\begin{aligned}
f_Y&(y|\mu,\theta,\sigma,\xi,\lambda)\\ 
&= \int^\infty_0\frac{1}{\sqrt{2\pi\sigma^2 x}}\exp\left\{-\frac{(y-\mu-\theta x)^2}{2\sigma^2 x}\right\}\sqrt{\frac{\lambda}{2\pi x^2}}\exp\left\{-\frac{\lambda(x-\xi)^2}{2\xi^2x}\right\}dx\\
&= \int^\infty_0\frac{\sqrt{\lambda}}{2\sigma\pi x^2}\exp\left\{-\frac{1}{2}\cdot\frac{\xi^2(y-\mu-\theta x)^2 + \sigma^2\lambda(x-\xi)^2}{\sigma^2\xi^2x}\right\}dx\\
&=\frac{\sqrt{\lambda}}{2\sigma\pi}\exp\left\{\frac{y\theta}{\sigma^2}-\frac{\mu\theta}{\sigma^2}+\frac{\lambda}{\xi}\right\}\int^\infty_0\frac{1}{x^2}\exp\left\{-\frac{1}{2}\left[\left(\frac{\theta^2}{\sigma^2}+\frac{\lambda}{\xi^2}\right)x+\left(\frac{(y-\mu)^2}{\sigma^2}+\lambda\right)\frac{1}{x}\right]\right\}dx\\ 
&=\frac{\sqrt{\lambda}}{2\sigma\pi}\exp\left\{\frac{y\theta}{\sigma^2}-\frac{\mu\theta}{\sigma^2}+\frac{\lambda}{\xi}\right\}\int^\infty_0\exp\left\{-\frac{1}{2}\left[\left(\frac{\theta^2}{\sigma^2}+\frac{\lambda}{\xi^2}\right)\frac{1}{t}+\left(\frac{(y-\mu)^2}{\sigma^2}+\lambda\right)t\right]\right\}dt
\end{aligned}
$$


Let 


$$
u = \sqrt{\frac{(y-\mu)^2/\sigma^2+\lambda}{\theta^2/\sigma^2+\lambda/\xi^2}}\cdot t
$$


we finally get the density function 


$$
\begin{aligned}
f_Y&(y | \mu,\theta,\sigma,\xi,\lambda)\\
=\ &\frac{1}{2\pi}\exp\left\{\frac{y\theta}{\sigma^2}-\frac{\mu\theta}{\sigma^2}+\frac{\lambda}{\xi}\right\}\frac{\alpha}{\sqrt{(y-\mu)^2+\lambda\sigma^2}}\cdot K_1\left(\frac{\alpha}{\sqrt{\lambda\sigma^2}}\sqrt{(y-\mu)^2+\lambda\sigma^2}\right) 
\end{aligned}
$$


where $K_p(.)$ is modified Bessel function of the second kind with index $p$. 

<br>

#### 3. Generalized Hyperbolic Distribution.

***Citations:*** 

Barndorff-Nielsen, O. E. and Halgreen, C. (1977). Infinite divisibility of the hyperbolic and
generalized inverse gaussian distribution. Zeitschrift Für Wahrscheinlichkeitstheorie Und
Verwandte Gebiete, 38(4):309–311. doi: [10.1007/BF00533162](https://doi.org/10.1007/BF00533162).<br>

Barndorff-Nielsen, O. E. (1977). Exponentially decreasing distributions for the logarithm of
particle size. Proceedings of the Royal Society of London. A. Mathematical and Physical
Sciences, 353(1674):401–419. doi: [10.1098/rspa.1977.0041](https://doi.org/10.1098/rspa.1977.0041).

<br>

When the mixture distribution is generalized hyperbolic distribution ([Barndorff-Nielsen, O. E. and Halgreen, C. ,1977](https://doi.org/10.1007/BF00533162))


$$
f_{GIG}(x | a, b, p) = \frac{(a/b)^{p/2} x^{p-1}}{2K_p(\sqrt{ab})}\exp\left(-\frac{ax^2+b}{2x}\right) 
$$


Then the normal variance-mean mixture is generalized hyperbolic distribution. The density of GH distribution is also derived from the mixture 


$$
\begin{aligned}
f_Y&(y|\mu, \theta, \sigma, a, b, p)\\ 
=\ &\int_{0}^{\infty} \frac{(a/b)^{p/2}x^{p-1}}{2K_p(\sqrt{ab})}\exp\left\{-\frac{ax^2+b}{2x}\right\}\frac{1}{\sqrt{2\pi\sigma^2 x}}\exp\left\{-\frac{(y-\mu-\theta x)^2}{2\sigma^2 x}\right\} dx\\
=\ &\frac{1}{\sigma\sqrt{2\pi}}\frac{(a/b)^{p/2}}{K_p(\sqrt{ab})}\exp\left\{\frac{\theta(y-\mu)}{\sigma^2}\right\}\int^\infty_0 \frac{x^{p-\frac{3}{2}}}{2}\exp\left\{-\frac{(a\sigma^2+\theta^2)x^2+b\sigma^2+(y-\mu)^2}{2\sigma^2x}\right\}dx
\end{aligned}
$$


Let 


$$
u = \sqrt{\frac{a + \theta^2/\sigma^2}{b + (y-\mu)^2/\sigma^2}} \cdot x \equiv \frac{\alpha\cdot x}{\sqrt{b+(y-\mu)^2/\sigma^2}}
$$


Then we have 


$$
\begin{aligned}
f_Y&(y|\mu, \theta, \sigma, a, b, p)\\ 
=\ &\frac{(a/b)^{p/2}}{\sigma\sqrt{2\pi} K_p(\sqrt{ab})}\exp\left\{\frac{\theta(y-\mu)}{\sigma^2}\right\}
\left[\frac{\sqrt{b + (y-\mu)^2/\sigma^2}}{\alpha}\right]^{p-\frac{1}{2}}
K_{p-\frac{1}{2}}\left(\alpha\sqrt{b+(y-\mu)^2/\sigma^2}\right) 
\end{aligned}
$$


where $K_p(.)$ is modified Bessel function of the second kind with index $p$. 

<br>

#### Relative notes

[Normal variance-mean mixture: Estimation.](https://zhuanglinsheng.github.io/2019/09/15/NVMM-Estimation.html) 