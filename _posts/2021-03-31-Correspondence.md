---
layout: post
title: "Perturbation of Correspondence"
use_math: true
lang: en
tags: notes, convex-optimization
desc: Briefly speaking, a set map (correspondence) can be perturbed around metric regular points. Metric regularity is equivalent to openness, while openness has a simple equivalent representation when the correspondence is closed and convex. 
---

<br>

Reference

[NUS MA6253 Conic Programming](https://nusmods.com/modules/MA6253/conic-programming) Lecture Notes of [Sun Defeng](https://scholar.google.com.sg/citations?user=QdIzNxgAAAAJ&hl=en). 

<br>

Briefly speaking, a set map (correspondence) can be perturbed around metric regular points. Metric regularity is equivalent to openness, while openness has a simple equivalent representation when the correspondence is closed and convex. 

<br>

### 1. Closeness and Convexity

**Lemma 1. ([Robinson, 1976](https://pubsonline.informs.org/doi/10.1287/moor.1.2.130))** Suppose $\mathcal{X}$ and $Y$ are normed linear space. Let $\mathcal{C}\subset\mathcal{X}\times\mathcal{Y}$ be closed and convex. Let $P_\mathcal{X}$ and $P_\mathcal{Y}$ are projections onto $\mathcal{X}$, $\mathcal{Y}$ respectively. Suppose $P_\mathcal{X}(\mathcal{C})$ is bounded, then 

- If $X$ is complete we have $\text{int}(cl(P_\mathcal{Y}(\mathcal{C}))) = \text{int}(P_{\mathcal{Y}}(\mathcal{C}))$. 
- If $X$ is reflexive then $P_\mathcal{Y}(X)$ is closed. 

***Proof.*** 

(1) It's trivial that $\text{int}(P_\mathcal{Y}(\mathcal{C})) \subset \text{int}(cl(P_\mathcal{Y}(\mathcal{C})))$, now we try to show the opposite. Suppose $P_\mathcal{X}(\mathcal{C})\subset\gamma B_\mathcal{X}$; let $y'\in \text{int}(cl(P_{\mathcal{Y}}(\mathcal{C})))$. Thus, for some $\epsilon>0$ we have $y'+\epsilon B_\mathcal{Y}\subset cl(P_\mathcal{Y}(\mathcal{C}))$. We shall show there exists a $x'\in\mathcal{X}$ with $(x',y')\in\mathcal{C}$ $\Leftrightarrow$ $y'\in P_\mathcal{Y}(\mathcal{C})$. 

[There are some simple missing logics: Since $y'\in \text{int}(cl(P))$ $\Leftrightarrow$ $y'+\epsilon B_\mathcal{Y} \subset cl(P)$ for some $\epsilon>0$, for all $y \in y'+\epsilon/2 B_\mathcal{Y}$ we have $y \in \text{int}(cl(P))$, because $y+\epsilon/4 B_\mathcal{Y}\subset y'+\epsilon B_\mathcal{Y}$. Thus, if we can show $y'\in P$ then we actually have showed that $y\in P$, which implies that $y'\in \text{int}(P)$.] 

Choose $(x_0, y_0)\in\mathcal{C}$ so that $y_0 = y'+r_0$ where $\Vert r_0\Vert \le \frac{\epsilon}{2}$. (That is because $y'\in cl(P_\mathcal{Y}(\mathcal{C}))$ and thus there exists a sequence in $P_\mathcal{Y}(\mathcal{C})$ converging to $y'$, so we can choose such a point $(x_0,y_0)$ from $\mathcal{C}$). Define $x_{-1} = x_0$ and note that $\Vert x_0\Vert \le \gamma$. For $k=0$ we have 


$$
(x_k,y_k)\in\mathcal{C},\quad y_k = y' + \frac{r_k}{2^k}, \quad 
\|r_k\| \le \frac{\epsilon}{2}, \quad \|x_k-x_{k-1}\| \le \frac{\gamma}{2^{k-1}}
\tag{1}
$$



If we can show by induction that such a sequence $(x_k, y_k)$ exists, then for any $k$ and any $n\ge1$ we have 


$$
\|x_{k+n}-x_k\| \le \sum^{n-1}_{i=0}\|x_{k+i+1}-x_{k+i}\| \le \sum^{n-1}_{i=0}2^{-(k+i)}\gamma < 2^{-(k-1)}\gamma
$$



so that $(x_k)$ is Cauchy sequence. By completeness of $X$ we know $x_k\to x'$ for some $x'$. Also, $y_k\to y'$ by the construction (1). Since $\mathcal{C}$ is closed we have $(x',y')\in\mathcal{C}$. 

Now suppose that (1) holds for some $n\ge0$. Then $\Vert(2-2^{-n})r_n\Vert \le (2-2^{-n})(\frac{\epsilon}{2})<\epsilon$ implies that 


$$
y' - (2-2^{-n})r_n \in y'+\epsilon B_\mathcal{Y} \subset cl(P_\mathcal{Y}(\mathcal{C}))
$$


So we can find $(u,v)\in\mathcal{C}$ with 


$$
v = y'-(2-2^{-n})r_n + r_{n+1},\quad\|r_{n+1}\|\le\frac{\epsilon}{2}
$$



We also have $\Vert u \Vert \le \gamma$. Define 


$$
(x_{n+1},y_{n+1}) = (1-2^{-(n+1)})(x_n,y_n) + 2^{-(n+1)}(u,v)
$$



The pair $(x_{n+1},y_{n+1})$ belongs to $\mathcal{C}$ by convexity; we have 


$$
\|x_{n+1}-x_n\| \le 2^{-(n+1)}\|u-x_n\| \le \frac{\gamma+\gamma}{2^{n+1}} = \frac{\gamma}{2^n}
$$



and 


$$
\begin{aligned}
y_{n+1} 
= (1-2^{-(n+1)})[y'+2^{-n}r_n] + 2^{-(n+1)}[y'-(2-2^{-n})r_n+r_{n+1}]
= y' + 2^{-(n+1)}r_{n+1}
\end{aligned}
$$



So (1) holds for $k=n+1$ and hence, by induction, for all $k$. 

(2) Omitted. 

**Def. (Closeness)** A correspondence $\Psi : \mathcal{X}\rightrightarrows \mathcal{Y}$ is closed at $x$ if for all $x_k\to x$, $y_k\in\Psi(x_k)$ and $y_k\to y$, we have $y\in\Phi(x)$. 

**Def. (Convexity)** A correspondence $\Psi:\mathcal{X}\rightrightarrows\mathcal{Y}$ is convex if for any $x_1, x_2\in\mathcal{X}$ and $t\in[0,1]$, we have 


$$
t\Psi(x_1) + (1-t)\Phi(x_2) \subset \Psi(tx_1+(1-t)x_2)
$$



**Proposition 2. ([Robinson, 1976](https://pubsonline.informs.org/doi/10.1287/moor.1.2.130))** Suppose $\mathcal{X}$ and $\mathcal{Y}$ are Banach spaces and the correspondence $\Psi:\mathcal{X}\rightrightarrows\mathcal{Y}$ is closed and convex. If $y\in \text{int}(\text{range}(\Psi))$ then for any $x\in\Psi^{-1}(y)$ we have $y\in \text{int}(\Psi(x+rB_{\mathcal{X}}))$ for all $r\in[0,1]$. 

***Proof.*** 

By translating the origin we can simply consider $x= 0$ and $y = 0$, and $0\in \Psi(0)$ by assumption. We want to first show that $0 \in \text{int}(\Psi(B_\mathcal{X}))$ (the case when $r=1$). Consider $Z = cl(\Psi(\frac{1}{2}B_\mathcal{X}))$ which is nonempty, closed and convex. 

Firstly, we want to show that $\Psi(\frac{1}{2}B_\mathcal{X})$ is absorbing. Since $0\in \text{int}(\text{range}(\Psi))$, for all $y\in\mathcal{Y}$ there is some $\alpha>0$ such that $\alpha y\in \text{range}(\Psi)$. Hence, $\alpha y\in\Psi(x)$ for some $x$. Thus, 


$$
t\alpha y = t\alpha y + (1-t)0 \in t\Psi(x) + (1-t)\Psi(0)\subset \Psi(tx)
$$



Thus, $t\alpha y\in\Psi(\frac{1}{2}B_\mathcal{X})$ for some sufficiently small $t>0$ (because $tx\in B_\mathcal{X}$ when $t$ is small). Thus, $\Psi(\frac{1}{2}B_\mathcal{X})$ is absorbing (for any $x\in\mathcal{X}$ there exists $t>0$ such that $tx\in \Psi(\frac{1}{2}B_\mathcal{X})$). Furthermore, $Z$ is absorbing. 

Secondly, Since $\mathcal{Y}$ is a [barreled space](https://en.wikipedia.org/wiki/Barrelled_space), we have $0\in \text{int}(Z)$. Thus, there exists a $\eta>0$ such that $0\in\eta B_\mathcal{Y} \subset \text{int}(cl(\Psi(\frac{1}{2}B_\mathcal{X})))$. Consider $\mathcal{C} = gph(\Psi) \cap (cl(\frac{1}{2}B_\mathcal{X})\times\mathcal{Y})$ and clearly $\Psi(cl(\frac{1}{2}B_\mathcal{X})) = P_\mathcal{Y}(\mathcal{C})$. Moreover, $\mathcal{C}$ is closed, convex and $P_\mathcal{X}(\mathcal{C}) = cl(\frac{1}{2}B_\mathcal{X})$ is bounded. By Lemma 1 we have 


$$
\eta B_\mathcal{Y} \subset \text{int}(cl(\Psi(\frac{1}{2}B_\mathcal{X}))) \subset \text{int}(cl(\Psi(cl(\frac{1}{2}B_\mathcal{X})))) = \text{int}(\Psi(cl(\frac{1}{2}B_\mathcal{X}))) \subset \text{int}(\Psi(B_\mathcal{X}))
$$



which completes the proof when $r=1$. 

Finally, since $0\in \text{int}(\Psi(B_\mathcal{X}))$, for any $r\in(0,1)$ we have 


$$
r\eta B_\mathcal{Y} \subset r\Psi(B_\mathcal{X}) + (1-r)0 \subset \Psi(rB_\mathcal{X}+(1-r)0) = \Psi(rB_\mathcal{X})
$$



Thus, $0\in \text{int}(\Psi(rB_\mathcal{X}))$ for all $r\in[0,1]$. 

<br>

### 2. Openness at rate $\gamma$ 

**Def. (Openness)** A correspondence $\Psi:\mathcal{X}\rightrightarrows\mathcal{Y}$ is open at $(x^0,y^0)\in gph(\Psi)$ at a linear rate $\gamma>0$, if there exists $t_0>0$ and a neighborhood $\mathcal{N}$ of $(x^0,y^0)$ such that for all $(x,y)\in gph(\Psi)\cap\mathcal{N}$ and for all $t\in[0,t_0]$ we have 


$$
y+\gamma t \cdot B_\mathcal{Y}\subset\Psi(x+t \cdot B_\mathcal{X})
$$



**Proposition 3.** Suppose $\Psi:\mathcal{X}\rightrightarrows \mathcal{Y}$ is closed and convex, then $\Psi$ is open at $(x_0,y_0)$ if and only if $y_0\in \text{int}(\text{range}(\Psi))$. 

***Proof.*** 

"$\Rightarrow$" Suppose $\Psi$ is open at $(x_0, y_0)$. Then by the definition there exists $t_0>0$ and $\gamma>0$ such that 


$$
y_0+\gamma t_0 B_\mathcal{Y} \subset \Psi(x_0+t_0 B_\mathcal{X}) \subset \text{range}(\Psi)
$$



which implies that $y_0\in \text{int}(\text{range}(\Psi))$. 

"$\Leftarrow$" Suppose $(x_0,y_0)\in gph(\Psi)$ and $y_0\in \text{int}(\text{range}(\Psi))$. We want to show that $\Psi$ is open at $(x_0,y_0)$. By Proposition 2 we have $y_0\in \text{int}(\Psi(x_0+B_{\mathcal{X}}))$. Thus, there exists $\gamma>0$ such that 


$$
y_0+2\gamma \cdot B_\mathcal{Y} \subset \Psi(x_0 + B_\mathcal{X})
$$



Let $\mathcal{N} = (x_0 + B_\mathcal{X})\times(y_0 + \gamma B_\mathcal{Y})$. For all $(x,y)\in gph(\Psi) \cap \mathcal{N}$ and $t\in[0,1]$ we have 


$$
\begin{aligned}
y + \gamma\cdot t B_\mathcal{Y} 
&= (1-t)y + t(y - \gamma B_\mathcal{Y})\\
&\subset (1-t)y + t (y_0 + 2\gamma B_\mathcal{Y})\\
&\subset (1-t)\Psi(x) + t\Psi(x_0 + B_\mathcal{X})\\
&\subset \Psi((1-t)x+t(x_0+B_\mathcal{X}))\\
&= \Psi(x + t(x_0 - x + B_\mathcal{X})) \\
&\subset \Psi(x+2t B_\mathcal{X})
\end{aligned}
$$



Thus, we can pick $t_0 = 2$. END. 

<br>

### 3. Metric Regularity at rate $\gamma$ 

**Def. (Metric Regularity)** A correspondence $\Psi:\mathcal{X}\rightrightarrows\mathcal{Y}$ is metric regular at $(x_0,y_0)\in gph(\Psi)$ at a rate $c>0$ if there exists a neighborhood $\mathcal{N}$ of $(x_0,y_0)$ such that  for all $(x,y)\in \mathcal{N}$ we have 


$$
D_\mathcal{X}(x,\Psi^{-1}(y)) \le c\cdot D_\mathcal{Y}(y,\Psi(x))
\tag{2}
$$



where $D_\mathcal{X}(.,.)$ and $D_{\mathcal{Y}}(.,.)$ are the minimum distance between point and set on $\mathcal{X}$ and $\mathcal{Y}$ respectively. 

**Note.** $\mathcal{N}$ is NOT necessarily included by $gph(\Psi)$. If $(x,y)\in gph(\Psi)$ then we have $D_\mathcal{X}(x,\Psi^{-1}(y)) =0$ and $ D_\mathcal{Y}(y,\Psi(x)) = 0$. 

**Proposition 4.** A correspondence $\Psi:\mathcal{X}\rightrightarrows\mathcal{Y}$ is metric regular at $(x_0,y_0)\in gph(\Psi)$ at a rate $c>0$ if and only if $\Psi$ is open at $(x_0,y_0)$ at the rate $\gamma = 1/c$. 

***Proof.*** 

"$\Rightarrow$". Suppose $\Psi$ is metric regular at $(x_0,y_0)$ at rate $c>0$, then there exists a neighborhood $\mathcal{N}$ of $(x_0,y_0)$ such that $D_\mathcal{X}(x,\Psi^{-1}(y))\le c\cdot D_\mathcal{Y}(y,\Psi(x))$ for all $(x,y)\in\mathcal{N}$. For all $(x,y)\in gph(\Psi)\cap\mathcal{N}$ and for all $z \in\mathcal{Y}$ and $t>0$ such that $(x,z)\in \mathcal{N}$ and $\Vert z-y\Vert \le t/c$ we have 

$$
D_\mathcal{X}(x,\Psi^{-1}(z)) \le c \cdot D_\mathcal{Y}(z,\Psi(x)) \le c \cdot \|z-y\| \le t
$$

Thus, there exists $w\in \Psi^{-1}(z)$ with $\Vert x-w\Vert \le t$. Thus we have $z\in \Psi(x+tB_\mathcal{X})$. 

"$\Leftarrow$". Suppose $\Psi$ is open at $(x_0,y_0)$ at rate $1/c$, then there exists $t_0>0$ and $\mathcal{N}$ around $(x_0,y_0)$ such that for all $t\in [0,t_0]$ and $(x,y)\in gph(\Psi)\cap \mathcal{N}$ we have 

$$
y + t/c \cdot B_\mathcal{Y} \subset \Psi(x + tB_\mathcal{X})
$$

Select $t_0$ small enough so that $B_{2t_0/c}(x_0,y_0) \subset \mathcal{N}$. 

Since $(x,y)$ can be picked as $(x_0,y_0)$, we have for all $(x,y)\in B_r(x_0,y_0)$ with $2r/c + r\le t_0/c$ there exists $u\in x + tB_\mathcal{X}$ such that $y\in\Psi(u)$ and $t = c\cdot \Vert y-y_0\Vert < r$. Then, 

$$
D_\mathcal{X}(x,\Psi^{-1}(z)) \le \|x-u\| \le \|x-x_0\| + \|u-x_0\| \le r + t
$$

If $r + t \le c \cdot D_\mathcal{Y}(y,\Psi(x))$ then we are done. 

Otherwise, we have $D_\mathcal{Y}(y,\Psi(x)) < (r+t)/c$. Then for all $0 < \alpha < (r+t)/c - D_\mathcal{Y}(y,\Psi(x))$ we can pick  $y_\alpha \in \Psi(x)$ such that 

$$
\|y - y_\alpha\| \le D_\mathcal{Y}(y,\Psi(x)) + \alpha \le (r+t)/c < 2r/c < t_0 / c
$$

Then $y_\alpha \in B_{t_0/c}(y_0)$ since $\Vert x-x_0\Vert \le r < t_0/c$ and 

$$
\|y_\alpha - y_0\| \le \|y - y_\alpha\| + \|y - y_0\| \le (r+t)/c + r \le 2r/c + r \le t_0 / c
$$

Finally we have $(x,y_\alpha) \in gph(\Psi) \cap \mathcal{N}$. By the openness of $\Psi$ at $(x,y_\alpha)$ there exists $u_\alpha \in x + t_\alpha B_\mathcal{X}$ such that $y\in\Psi(u_\alpha)$ and $t_\alpha = c\cdot \Vert y-y_\alpha\Vert$. Then 

$$
D_\mathcal{X}(x,\Psi^{-1}(y)) \le \|x-x_\alpha\| \le t_\alpha = c\cdot \|y-y_\alpha\| \le c\cdot D_\mathcal{Y}(y,\Psi(x)) + c\alpha
$$

Pushing $\alpha\to 0$ and we have the conclusion. END. 

<br>

### 4. Perturbation of the Set Maps $\Psi_G$ 

**Def.** Given a continuous function $G:\mathcal{X}\to\mathcal{Y}$ and a cone $\mathcal{K}\subset\mathcal{Y}$, define the set map $\Psi_G$ by 


$$
\Psi_G(x) = G(x) - \mathcal{K}
$$


**Proposition 5.** Given continuous function $G:\mathcal{X}\to\mathcal{Y}$ and $H:\mathcal{X}\to\mathcal{Y}$ and a solid cone $\mathcal{K}\subset\mathcal{Y}$. Suppose that

(1) $\Psi_G$ is metric regular at $(x_0, y_0)$ at a rate $c>0$,

(2) $A(x)=G(x)-H(x)$ is Lipschitz in a neighborhood of $x_0$ with modulus $\kappa<1/c$,

Then $\Psi_H$ is metric regular at $(x_0,y_0-A(x_0))$ at rate $c/(1-c\kappa)$. 

***Proof.*** 

Let $\eta_x>0$ and $\eta_y>0$ be the radius of the neighborhood of $(x_0, y_0)$ such that (2) holds for all $(x, y)$ with 


$$
\|x-x_0\| < \eta_x,
\quad
\|y-y_0\| < \eta_y
$$


For any $\epsilon>0$, there exists $\tilde{\eta}_x>0, \tilde{\eta}_y>0$ that are sufficiently small so that 


$$
\begin{aligned}
\tilde{\eta}_x + c(1+\epsilon) \cdot \left[\sup_{x\in x_0 + \tilde{\eta}_xB_\mathcal{X}}\|G(x)-G(x_0)\| + \tilde{\eta}_y + \kappa\tilde{\eta}_x\right] &<\eta_x\\
\tilde{\eta}_y+\kappa\tilde{\eta}_x+\kappa c(1+\epsilon)\cdot \left[\sup_{x\in x_0 + \tilde{\eta}_xB_\mathcal{X}}\|G(x)-G(x_0)\| + \tilde{\eta}_y + \kappa\tilde{\eta}_x\right] &< \eta_y\\
\frac{c(1+\epsilon)}{1-(1+\epsilon)c\kappa} \cdot \left[\sup_{x\in x_0 + \tilde{\eta}_xB_\mathcal{X}}\|G(x)-G(x_0)\| + \tilde{\eta}_y + \kappa\tilde{\eta}_x\right] &<\eta_x\\
\tilde{\eta}_y+\kappa\tilde{\eta}_x+\frac{c\kappa(1+\epsilon)}{1-(1+\epsilon)c\kappa} \cdot \left[\sup_{x\in x_0 + \tilde{\eta}_xB_\mathcal{X}}\|G(x)-G(x_0)\| + \tilde{\eta}_y + \kappa\tilde{\eta}_x\right] &<\eta_y
\end{aligned}
\tag{3}
$$


We arbitrarily pick $(x,y)$ such that 


$$
\|x-x_0\| < \tilde{\eta}_x,
\quad
\|y-(y_0-A(x_0))\| < \tilde{\eta}_y
$$


Note that 


$$
\|x - x_0\| < \tilde{\eta}_x < \eta_x
\tag{4}
$$

$$
\|y+A(x_1)-y_0\| \le \|y-(y_0-A(x_0))\| + \|A(x_1)-A(x_0)\| < \tilde{\eta}_y + \kappa\tilde{\eta}_x<\eta_y
\tag{5}
$$



and


$$
\begin{aligned}
D_\mathcal{Y}(y,\Psi_H(x)) 
&= D_\mathcal{Y}(G(x)-y-A(x),\mathcal{K})\\
&\le\|G(x)-G(x_0)\| + \|y-y_0\| + \|A(x)\|
\end{aligned}
\tag{6}
$$


Letting $x_1 = x$, we want to construct a sequence $(x_k)$ that satisfies the properties:

(A) $x_{k+1}\in\Psi_G^{-1}(y+A(x_k))$ $\Leftrightarrow$ $y+A(x_k)\in\Psi_G(x_{k+1})$, 

(B) $\Vert x_{k+1}-x_k\Vert \le (1+\epsilon) \cdot D_\mathcal{X}(x_k,\Psi_G^{-1}(y+A(x_k)))$, 

(C) $x_k\in B(x_0,\eta_x)$ and $y + A(x_k)\in B(y_0,\eta_y)$. 

If we can show the existence of such a sequence then (B), (C) and (A) implies that 


$$
\begin{aligned}
\|x_{k+1}-x_k\| 
&\le (1+\epsilon) \cdot D_\mathcal{X}(x_k,\Psi_G^{-1}(y+A(x_k)))\\
&\le (1+\epsilon)c\cdot D_\mathcal{Y}(y+A(x_k),\Psi_G(x_k))\\
&=   (1+\epsilon)c\cdot \|(y+A(x_k))-(y+A(x_{k-1}))\|
 \le (1+\epsilon)c \kappa \cdot \|x_k-x_{k-1}\|
\end{aligned}
$$


Thus, for all $x_k$ in the sequence $(x_k)$ we have 


$$
\begin{aligned}
\|x_k-x_1\| 
&\le \frac{1}{1 - (1+\epsilon)c\kappa} \cdot \|x_2-x_1\|\\
&\le \frac{1}{1 - (1+\epsilon)c\kappa} \cdot (1+\epsilon)c \cdot D_\mathcal{Y}(y+A(x_1), \Psi_G(x_1))\\
&= \frac{(1+\epsilon)c}{1 - (1+\epsilon)c\kappa} \cdot D_\mathcal{Y}(y,\Psi_G(x_1)-A(x_1))\\
&= \frac{(1+\epsilon)c}{1 - (1+\epsilon)c\kappa} \cdot D_\mathcal{Y}(y,\Psi_H(x_1))
\end{aligned}
$$


Remember $x_1 = x$, letting $\epsilon\to0$ and we have 


$$
\|x_k-x\| \le c/(1-c\kappa)\cdot D_\mathcal{Y}(y,\Psi_H(x))
$$


By (C) there exists a subsequence of $(x_k)$ that converges to $x^\star$. Since $\Psi_G$ is closed, Condition (A) implies that 


$$
y+A(x^*)\in\Psi_G(x^*) \Rightarrow y\in\Psi_H(x^*) \Rightarrow x^*\in\Psi_H^{-1}(y)
$$


Thus, 


$$
D_\mathcal{X}(x, \Psi_H^{-1}(y)) \le c/(1-c\kappa) \cdot D_\mathcal{Y}(y,\Psi_H(x))
$$


And the proposition is proved. 

Now we want to construct the sequence satisfying conditions (A)-(C). By definition, we can always pick a point $x_2\in\Psi_G^{-1}(y+A(x_1))$ such that 


$$
\|x_2 - x_1\| \le (1+\epsilon) \cdot D_\mathcal{Y}(x_1,\Psi_G^{-1}(y+A(x_1)))
$$



Then by metric regularity of $\Psi_G$ at $(x_0, y_0)$ we have 


$$
\begin{aligned}
\|x_2 - x_1\| 
&\le (1+\epsilon)\cdot c \cdot D_\mathcal{Y}(y+A(x_1),\Psi_G(x_1))\\
&=   (1+\epsilon)\cdot c \cdot D_\mathcal{Y}(y,G(x)-A(x)-\mathcal{K}) 
 = c(1+\epsilon) \cdot D_\mathcal{Y}(y, \Psi_H(x))
\end{aligned}
$$



Then by equation (3) and (6) we have 


$$
\|x_2-x_0\| \le c(1+\epsilon) \cdot D_\mathcal{Y}(y, \Psi_H(x)) + \tilde{\eta}_x < \eta_x
$$


and by (3) we have 


$$
\begin{aligned}
\|y+A(x_2)-y_0\|
&\le \|y+A(x_2)-y-A(x_1)\|+\|y+A(x_1)-y_0\|\\
&\le \kappa\cdot c(1+\epsilon)\cdot D_\mathcal{Y}(y,\Psi_H(x)) + \tilde{\eta}_y+\kappa\tilde{\eta}_x < \eta_y
\end{aligned}
$$



Now suppose we have had $(x_1, ..., x_k)$, $k \ge 2$ that satisfy these conditions. By definition we can always pick $x_{k+1}\in\Psi_G^{-1}(y+A(x_k))$ such that 


$$
\begin{aligned}
\|x_{k+1}-x_k\| 
&\le (1+\epsilon) \cdot D_\mathcal{X}(x_k,\Psi_G^{-1}(y+A(x_k)))\\
&\le c(1+\epsilon)\cdot D_\mathcal{Y}(y+A(x_k),\Psi_G(x_k))
 \le (1+\epsilon)c\kappa\cdot\|x_k-x_{k-1}\|
\end{aligned}
$$



Thus, by equation (3) we have 


$$
\|x_{k+1}-x_0\| \le \frac{(1+\epsilon)c}{1-(1+\epsilon)c\kappa} \cdot D_\mathcal{Y}(y,\Psi_H(x_1)) < \eta_x
$$


and 


$$
\|y+A(x_k)-y_0\| \le \frac{(1+\epsilon)c\kappa}{1-(1+\epsilon)c\kappa}\cdot D_\mathcal{Y}(y,\Psi_H(x))+\tilde{\eta}_y + \kappa\tilde{\eta}_x < \eta_y
$$


Finally, by induction the sequence $(x_k)$ exists. 

<br>