---
layout: post
title: "Fixed Point Iteration"
use_math: true
lang: en
tags: blog
desc:
---

This note summarize the Section 5.1-5.2 of Bauschke and Combettes (2011). The key result is the weak convergence of Krasnosel'skii–Mann (KM) Iteration, which is an fixed point algorithm of non-expansive operator mapping from a convex and closed set into itself. This result relies on that (1) weak convergence implies fixed point and (2) Fejér Monotonicity implies weak convergence.

<!-- more -->

Reference

- Bauschke, H. H., & Combettes, P. L. (2011). *Convex analysis and monotone operator theory in Hilbert spaces* (Vol. 408). New York: Springer.

- [Section 5.1-5.2](https://link.springer.com/chapter/10.1007/978-1-4419-9467-7_5) of [Bauschke and Combettes (2011)](https://link.springer.com/book/10.1007/978-1-4419-9467-7).

<br>

## 1. Fejér Monotone Sequence

**Def. 5.1 (Fejér Monotonicity)** Let $C$ be a nonemoty subset of $\mathcal{H}$ and let $(x_n)$ be a sequence in $\mathcal{H}$. Then $(x_n)$ is Fejér monotone w.r.t. $C$ if


$$
\|x_{n+1}-x\| \le \|x_n-x\|
$$


for all $x\in C$ and $n\in N$.

**Example 5.2** A bounded increasing sequence $(x_n)$ is Fejér Monotone with respect to the set $(\sup x_n, +\infty)$.

**Definition (Quasi-nonexpansiveness)** For any $\emptyset\not=D\subset\mathcal{H}$, an operator $T:D\to D$ such that $\text{Fix}(T)\not=\emptyset$ is [quasi-nonexpansive](https://www.cambridge.org/core/services/aop-cambridge-core/content/view/S144678870001123X) if


$$
\|Tx-p\| \le \|x-p\|
$$


for all $x\in D$ and $p\in\text{Fix}(T)$.

**Note.** Non-expansiveness implies quasi-non-expansiveness:

$$
\|Tx - Tp\| \le \|x-p\|
\Rightarrow
\|Tx - p\| \le \|x - p\|
$$

for all $p\in\text{Fix}(T)$.

**Example 5.3** Let $\emptyset\not=D\subset\mathcal{H}$ and let $T:D\to D$ be a quasi-nonexpansive operator such that $\text{Fix}(D)\not=\emptyset$. Then $(x_n)$ generated by the fixed point iterations of $T$ is Fejér Monotone.

**Proposition 5.4 (Fejér monotonicity; General Set)** Let $\emptyset\not=C\subset\mathcal{H}$. Suppose $(x_n)\subset\mathcal{H}$ is Fejér monotone with respect to $C$. Then

i) $(x_n)$ is bounded by $B(x,\Vert x_0-x\Vert)$ for any $x\in C$

***Proof.*** By definition 5.1.

ii) For every $x\in C$ we have $(\Vert x_n-x \Vert)$ converges

***Proof.*** By definition 5.1.

iii) $(d_C(x_n))$ is decreasing and converges.

***Proof.*** By contradiction. If $d_C(x_{n+1}) > d_C(x_n)$ for some $n\in N$, then

$$
\|x_{n+1}-P_C(x_n)\| \ge \|x_{n+1}-P_C(x_{n+1})\| > \|x_n-P_C(x_n)\|
$$

iv) $\Vert x_{n+m}-x_n \Vert \le 2d_C(x_n)$ for all $m,n\in N$.

***Proof.*** $\Vert x_{n+m}-x_n \Vert \le \Vert x_{n+m}-x \Vert + \Vert x_n-x \Vert \le 2\Vert x_n-x \Vert$ for all $x\in C$.

<br>

## 2. Shadow of Fejér Monotone Sequence

**Proposition 5.7 (Shadow Sequence; Fejér monotonicity; Closed Convex Set)** Let $\emptyset\not=C\subset\mathcal{H}$ is convex and closed. Suppose $(x_n)\subset\mathcal{H}$ is Fejér monotone with respect to $C$. Then the shadow sequence $(P_C(x_n))$ converges strongly to a point $z\in C$.

***Proof.*** For any $m, n\in N$ we have

$$
\begin{aligned}
&\|P_C(x_m)-P_C(x_{n+m})\|^2\\
= &\|P_C(x_n)-x_{n+m}\|^2 + \|x_{n+m}-P_C(x_{n+m})\|^2 + 2\langle P_C(x_n)-x_{n+m}, x_{n+m}-P_C(x_{n+m}) \rangle\\
\le &\|P_C(x_n)-x_n\|^2 + d_C(x_{n+m})^2\\
&+ 2\langle P_C(x_n)-P_C(x_{n+m}), x_{n+m}-P_C(x_{n+m}) \rangle\\
&+ 2\langle P_C(x_{n+m})-x_{n+m}, x_{n+m}-P_C(x_{n+m}) \rangle\\
\le &d_C(x_n)^2 - d_C(x_{n+m})^2
\end{aligned}
$$

The first inequality is because $\Vert P_C(x_n)-x_{n+m}\Vert \le \Vert P_C(x_n)-x_n\Vert$ (Fejér monotonicity). The second inequality is because $\langle P_C(x_n)-P_C(x_{n+m}), x_{n+m}-P_C(x_{n+m}) \rangle \le 0$ (metric projection). By 5.4 (iii) we have $(d_C(x_n))$ decreasing and converge, $(P_C(x_n))$ is a Cauchy sequence.

**Proposition 5.9 (Shadow Sequence; Fejér monotonicity; Closed Affine Subspace)** Let $C\subset\mathcal{H}$ is a closed affine subspace. Suppose $(x_n)\subset\mathcal{H}$ is Fejér monotone with respect to $C$. Then $P_C(x_n) = P_C(x_0)$ for all $n\in N$.

***Proof.*** For any $n\in N$ and $\alpha \in R$ define $y_\alpha = \alpha P_C(x_0) + (1-\alpha) P_C(x_n) \in C$. Then for all $\alpha \in R$ and $n\in N$ we have

$$
\langle y_\alpha - P_C(x_n), x_n - P_C(x_n) \rangle \le 0
\Rightarrow
\alpha \langle P_C(x_0) - P_C(x_n), x_n - P_C(x_n) \rangle \le 0
$$

which implies that $y_\alpha - P_C(x_n) \perp x_n - P_C(x_n)$. We have

$$
\begin{aligned}
\alpha^2 \|P_C(x_n) - P_C(x_0)\|^2
&= \|P_C(x_n) - y_\alpha\|^2\\
&\le \|x_n-P_C(x_n)\|^2 + \|P_C(x_n)- y_\alpha\|^2\\
&= \|x_n - y_\alpha\|^2\\
&\le \|x_0 - y_\alpha\|^2\\
&= \|x_0  - P_C(x_0)\|^2 + \|P_C(x_0) - y_\alpha\|^2\\
&= d_C(x_0)^2 + (1-\alpha)^2\|P_C(x_n)-P_C(x_0)\|^2
\end{aligned}
$$

which implies that $(2\alpha - 1) \Vert P_C(x_n) - P_C(x_0)\Vert^2 \le d_C(x_0)^2$. Letting $\alpha \to +\infty$ and we have $P_C(x_n) = P_C(x_0)$.

<br>

## 3. Convergence of Fejér Monotone Sequence

**Proposition 5.10 (Convergence; Fejér monotonicity; Nonempty Interior; Raik)** Let $C\subset\mathcal{H}$ such that $\text{int}(C)\not=\emptyset$. Suppose $(x_n)\subset\mathcal{H}$ is Fejér monotone with respect to $C$. Then $(x_n)$ converges strongly and $\sum_n\Vert x_{n+1}-x_n \Vert < +\infty$.

***Proof.*** Pick $x\in \text{int}(C)$ and $\rho > 0$ such that $B(x,\rho) \subset C$. Define a sequence $(z_n)\subset B(x,\rho)$ by

$$
z_n = \begin{cases}
x, &x_{n+1} = x_n\\
x - \rho\frac{x_{n+1}-x_n}{\|x_{n+1}-x_n\|},&\text{otherwise}
\end{cases}
$$

Then $\Vert x_{n+1}-z_n \Vert^2 \le \Vert x_n-z_n \Vert^2$ for all $(x_n)$ that is Fejér monotone with respect to $C$ and for all $n\in N$. We have

$$
\begin{aligned}
(\|x_{n+1}-x\| + \rho)^2 &\le (\|x_n-x\| - \rho)^2\\
\Rightarrow\quad
\|x_{n+1}-x\|^2 + 2\rho \|x_{n+1}-x\| &\le \|x_n - x\|^2 - 2\rho\|x_n - x\|\\
\Rightarrow\quad\quad\quad\quad\quad\quad\quad\quad
\|x_{n+1} - x\|^2 &\le \|x_n - x\|^2 - 2\rho (\|x_n - x\| + \|x_{n+1} - x\|)\\
\Rightarrow\quad\quad\quad\quad\quad\quad\quad\quad
\|x_{n+1} - x\|^2 &\le \|x_n - x\|^2 - 2\rho \|x_{n+1} - x_n\|
\end{aligned}
$$

Thus

$$
\sum_{n\in N}\|x_{n+1}-x_n\| \le \left(\frac{1}{2\rho}+1\right)\cdot\|x_0-x\|^2
$$

and $(x_n)$ is therefore a Cauchy sequence.

**Proposition 5.11 (Convergence; Fejér monotonicity; Closed Convex Set)** Let $\emptyset\not=C\subset\mathcal{H}$ is convex and closed. Suppose $(x_n)\subset\mathcal{H}$ is Fejér monotone with respect to $C$. Then the following are equivalent

i) $(x_n)$ converges strongly to a point in $C$.

ii) $(x_n)$ possesses a strong sequential cluster point in $C$.

iii) $\underline{\lim}d_C(x_n) = 0$.

***Proof.***

i) $\Rightarrow$ ii): Statement ii) is equivalent to say that $(x_n)$ has a sub-sequence that converges to a point in $C$.

ii) $\Rightarrow$ iii): Suppose $x_{k_n}\to x\in C$ then $d_C(x_{k_n}) \le \Vert x_{k_n} - x \Vert \to 0$.

iii) $\Rightarrow$ i): By 5.4 (iii) we know $(d_C(x_n))$ is decreasing and convergent, then $\underline{\lim} d_C(x_n) = 0$ implies that $d_C(x_n)\to 0$. By proposition 5.7 we have $(P_C(x_n))$ converges strongly to some point in $C$, say $P_C(x_n) \to x\in C$, then

$$
\|x_n - x\| \le \|x_n - P_C(x_n)\| + \|P_C(x_n)-x\| \to 0
$$

**Proposition 5.12 (Linear Convergence; Fejér monotonicity; Closed Convex Set)** Let $\emptyset\not=C\subset\mathcal{H}$ is convex and closed. Suppose $(x_n)\subset\mathcal{H}$ is Fejér monotone with respect to $C$ and there exists some $\kappa\in[0,1)$ such that for all $n\in N$ we have

$$
d_C(x_{n+1}) \le \kappa \cdot d_C(x_n)
\tag{5.7}
$$

Then $(x_n)$ converges linearly to a point $x\in C$; more precisely, for all $n\in N$ we have

$$
\|x_n-x\| \le 2 \kappa^n d_C(x_0)
\tag{5.8}
$$

***Proof.*** Condition (5.7) implies $\underline{\lim}d_C(x_n) = 0$ which, by Proposition 5.11, implies that $(x_n)$ converges strongly to a point in $C$, say $x_n\to x\in C$. Proposition 5.4 (iv) says for all $m,n\in N$ we have

$$
\|x_{n} - x_{n+m}\| \le 2d_C(x_n)
$$

Let $m\to +\infty$ and we have $\Vert x_n - x \Vert \le 2d_C(x_n) \le 2\kappa^1 d_C(x_{n-1}) \le ... \le 2 \kappa^n d_C(x_0)$.

<br>

## 4. Weak Convergence

**Definition (Weak Convergence in Hilbert Space)** A sequence $(x_n)\subset\mathcal{H}$ is said to converge weakly to a point $x\in \mathcal{H}$ if

$$
\langle x_n, y \rangle \to \langle x, y \rangle,
\quad
\forall y\in \mathcal{H}.
$$

The notation $x_n \rightharpoonup x$ is sometimes used to denote this kind of convergence. Referred from [Wikipedia](https://en.wikipedia.org/wiki/Weak_convergence_(Hilbert_space)).

**Corollary 4.18 (Fixed Point; Weak Convergence; Asymptotic regularity)** Let $\emptyset\not=D\subset\mathcal{H}$ that is closed and convex and let $T:D\to \mathcal{H}$ be a non-expansive operator. If there exists $(x_n)\subset D$ and $x\in \mathcal{H}$ such that $x_n\rightharpoonup x$ and $x_n-T(x_n)\to 0$, then $x\in\text{Fix}(T)$.

**Theorem 5.5 (Weak Convergence; Fejér Monotonicity)** Let $\emptyset\not=C\subset\mathcal{H}$ and $(x_n)\subset\mathcal{H}$ is Fejér monotone with respect to $C$. Suppose every weak sequential cluster point of $(x_n)$ belongs to $C$. Then $x_n\rightharpoonup x$.

**Proposition 5.13 (Weak Convergence; Asymptotic regularity; Non-expansiveness)** Let $\emptyset\not=D\subset\mathcal{H}$ that is closed and convex and let $T:D\to D$ be a non-expansive operator with $\text{Fix}(T)\not=\emptyset$. Let $x_0 \in D$. Set

$$
x_{n+1} = T(x_n)
\tag{5.9}
$$

and suppose that $x_{n}-T(x_n) \to 0$. Then

i) $(x_n)$ converges weakly to a point in $\text{Fix}(T)$.

ii) Suppose that $D = -D$ and that $T$ is odd: $T(-x) = -T(x)$ for all $x\in D$. Then $(x_n)$ converges strongly to a point in $\text{Fix}(T)$.

***Proof.*** By Example 5.3 we have $(x_n)$ is Fejér monotone with respect to $\text{Fix}(T)$.

i) Let $x$ to be a weak cluster point such that $x_{k_n} \rightharpoonup x$. Since $x_{k_n}-T(x_{k_n})\to 0$ we have $x\in \text{Fix}(T)$ by Corollary 4.18. Then by Theorem 5.5 we have $x_n\rightharpoonup \tilde{x} \in \text{Fix}(T)$.

ii) Since $D = -D$ and $D$ is convex we must have $0 = 0.5x + 0.5(-x)\in D$ for all $x\in D$. Since $T$ is odd we must have $T(0) = T(-0) = -T(0) \Rightarrow T(0) = 0$. Thus, $0\in\text{Fix}(T)$. Thus, by Fejér monotonicity we have $\Vert x_{n+1} \Vert \le \Vert x_n \Vert$. Thus, $(\Vert x_n \Vert)$ is decreasing and converges to some point $\ell \ge 0$. For any $m,n\in N$ we have

$$
\|x_{n+m+1} + x_{n+1}\| = \|T(x_{n+m})-T(-x_n)\| \le \|x_{n+m}+x_n\|
\tag{5.10}
$$

Thus, $(\Vert x_{n+m}+x_n \Vert)_{n\in N}$ is decreasing for all given $m\in N$. Also we have the identity

$$
\|x_{n+m}+x_n\|^2 = 2(\|x_{n+m}\|^2+\|x_m\|^2) - \|x_{n+m}-x_n\|^2
\tag{5.11}
$$

Since $T(x_n)-x_n\to 0$ we have $\lim_{n}\Vert x_{n+m}-x_n \Vert=0$. Thus, $\Vert x_{n+m}+x_n \Vert^2 \downarrow 2(\ell^2+\Vert x_m \Vert^2)$ as $n\to+\infty$ for any given $m\in N$. Thus, $\Vert x_{n+m}-x_n \Vert^2\to 4\ell^2-4\ell^2 = 0$ as $m,n\to+\infty$. Thus, $(x_n)$ is a Cauchy sequence and $x_n\to x\in\mathcal{H}$. Since $x\leftarrow x_{n+1}=T(x_n)\to T(x)$ we have $x\in\text{Fix}(T)$.

<br>

## 5. Krasnosel'skii–Mann (KM) Iteration

**Corollary (Identity)** For any $x, y\in\mathcal{H}$ and $\alpha\in R$ it is easy to verify that

$$
\|\alpha x + (1-\alpha)y\|^2 + \alpha(1-\alpha)\|x-y\|^2 = \alpha\|x\|^2 + (1-\alpha)\|y\|^2
$$

**Proposition 5.14 (Weak Convergence; KM Algorithm)** Let $\emptyset\not=D\subset\mathcal{H}$ is convex and closed and let $T:D\to D$ be a non-expansive operator with $\text{Fix}(T)\not=\emptyset$. Let $(\lambda_n)\subset[0,1]$ with $\sum_n\lambda_n(1-\lambda_n) = +\infty$. Let $x_0\in D$. Set

$$
x_{n+1} = x_n + \lambda_n(T(x_n) - x_n)
\tag{5.12}
$$

Then the following holds:

i) $(x_n)$ is Fejér monotone w.r.t. $\text{Fix}(T)$.

ii) $(Tx_n - x_n)$ converges strongly to zero.

iii) $(x_n)$ converges weakly to a point in $\text{Fix}(T)$.

***Proof.*** Since $x_0\in D$ and $D$ is convex, (5.12) generates a well-defined sequence in $D$.

i) For any $y\in \text{Fix}(T)$ and $n\in N$ we have

$$
\begin{aligned}
\|x_{n+1}-y\|^2
&= \|(1-\lambda_n)(x_n-y) + \lambda_n(Tx_n-y)\|^2\\
&= (1-\lambda_n)\|x_n-y\|^2+\lambda_n\|Tx_n-Ty_n\|^2 - \lambda_n(1-\lambda_n)\|Tx_n-x_n\|^2\\
&\le \|x_n-y\|^2 - \lambda_n(1-\lambda_n)\|Tx_n-x_n\|^2
\end{aligned}
\tag{5.13}
$$

The inequality is by the non-expansiveness of $T$.

ii) From (5.13) we have $\lambda_n(1-\lambda_n)\Vert Tx_n-x_n \Vert^2 \le \Vert x_n-y \Vert^2 - \Vert x_{n+1}-y \Vert^2$. Then

$$
\sum_n \lambda_n(1-\lambda_n)\|Tx_n-x_n\|^2 \le \|x_0-y\|^2
$$

Since $\sum_n\lambda_n(1-\lambda_n) = +\infty$ we must have $\underline{\lim}\Vert Tx_n-x_n \Vert=0$. And

$$
\begin{aligned}
\|Tx_{n+1}-x_{n+1}\|
&= \|Tx_{n+1}-Tx_n+(1-\lambda_n)(Tx_n-x_n)\|\\
&\le \|x_{n+1}-x_n\| + (1-\lambda_n)\|Tx_n-x_n\|\\
&= \|Tx_n-x_n\|
\end{aligned}
\tag{5.14}
$$

Consequently $(Tx_n-x_n)\downarrow 0$.

iii) For any $x\in D$ such that $x_{k_n}\rightharpoonup x$ we have $x\in \text{Fix}(T)$ by Corollary 4.18. Moreover $(x_n)$ is Fejér monotone w.r.t. $\text{Fix}(T)$. Thus, by Proposition 5.5 we have $x_n\rightharpoonup x$.

<br>

## 6. $\alpha$-Averaged Operator

**Definition 4.23 ($\alpha$-Averaged Operator)** Let $\emptyset\not=D\subset\mathcal{H}$ and let $T:D\to\mathcal{H}$. Let $\alpha\in(0,1)$. Then $T$ is called $\alpha$-averaged if there exists a non-expansive operator $R:D\to\mathcal{H}$ such that $T = (1-\alpha)\text{Id}+\alpha R$.

**Proposition 4.24 (Properties of $\alpha$-Averaged Operator - 1)** Let $\emptyset\not=D\subset\mathcal{H}$ and $T:D\to\mathcal{H}$. Let $\alpha\in(0,1)$. Then

i) If $T$ is $\alpha$-averaged then it is non-expansive.

ii) If $T$ is non-expansive it is NOT necessarily averaged.

iii) $T$ is firmly non-expansive iff it is $1/2$-averaged.

**Proposition 4.25 (Properties of $\alpha$-Averaged Operator - 2)** Let $\emptyset\not=D\subset\mathcal{H}$ and $T:D\to\mathcal{H}$. Let $\alpha\in(0,1)$. Then the following are equivalent

i) $T$ is $\alpha$-averaged.

ii) $R\equiv(1-1/\alpha)\text{Id}+(1/\alpha)T$ is non-expansive.

iii) $\Vert T(x)-T(y) \Vert^2 \le \Vert x-y \Vert^2 - \frac{1-\alpha}{\alpha} \Vert(\text{Id}-T)x-(\text{Id}-T)y \Vert^2$ for all $x, y\in D$.

iv) $\Vert T(x) - T(y)\Vert^2 + (1-2\alpha)\Vert x-y\Vert^2 \le 2(1-\alpha)\langle x-y,T(x) - T(y)\rangle$ for all $x,y\in D$.

**Proposition 5.15 (Weak Convergence; $\alpha$-Averaged Operator)** Let $\alpha\in[0,1]$ and $T:\mathcal{H}\to\mathcal{H}$ be an $\alpha$-averaged operator such that $\text{Fix}(T)\not=\emptyset$. Let $(\lambda_n)$ be a sequence in $[0,1/\alpha]$ with $\sum_n\lambda_n(1-\alpha\lambda_n)= +\infty$. Let $x_0\in\mathcal{H}$ and set

$$
x_{n+1} = x_n + \lambda_n[T(x_n)-x_n]
\tag{5.15}
$$

Then the following hold:

i) $(x_n)$ is Fejér monotone w.r.t. $\text{Fix}(T)$.

ii) $(Tx_n - x_n)$ converges strongly to zero.

iii) $(x_n)$ converges weakly to a point in $\text{Fix}(T)$.

***Proof.***

Set $R = (1-1/\alpha)\text{Id}+1/\alpha T$ for all $n\in N$. Then $\text{Fix}(R) = \text{Fix}(T)$ by definition and $R$ is non-expansive by Proposition 4.25. Then (5.15) is

$$
x_{n+1} = x_n +\alpha\lambda_n(Rx_n - x_n)
$$

Since $\alpha\lambda_n\in[0,1]$ and $\sum_n\alpha\lambda_n(1-\alpha\lambda_n) = +\infty$, the result follows Proposition 5.14.

**Corollary 5.16 (Special Case: $1/2$-averaged)** Let $T:\mathcal{H}\to\mathcal{H}$ be a firmly non-expansive operator with $\text{Fix}(T)\not=\emptyset$. Let $(\lambda_n)$ be a sequence in $[0,2]$ with $\sum_n\lambda_n(2-\lambda_n) = +\infty$ and let $x_0\in\mathcal{H}$. Set $x_{n+1} = x_n +\lambda_n(Tx_n-x_n)$. Then

i) $(x_n)$ is Fejér monotone w.r.t. $\text{Fix}(T)$.

ii) $(Tx_n - x_n)$ converges strongly to zero.

iii) $(x_n)$ converges weakly to a point in $\text{Fix}(T)$.

***Proof.*** When $\alpha = 1/2$ and apply Proposition 4.24 (iii) and Proposition 5.15.

**Example 5.17 (Special Case: $1/2$-averaged when $\lambda_n=1$)** Let $T:\mathcal{H}\to\mathcal{H}$ be a firmly non-expansive operator such that $\text{Fix}(T)\not=\emptyset$. Let $x_0\in\mathcal{H}$. Set $x_{n+1}=T(x_n)$. Then $(x_n)$ converges weakly to a point in $\text{Fix}(T)$.

<br>


