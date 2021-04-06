---
layout: post
title: "Optimal Public Debt Level"
use_math: true
lang: en
tags: notes, model
desc: This blog article tries to build a general equilibrium model and study the deviation of this idea-type with classical standard analysis of the optimal public debt policy, which originated from Barro (1974) and has developed into a rich branch in public economics.
---

<br>

The optimal public debt level analysis originated from Barro (1974), and has developed into a rich branch in public economics. Also, beginning with Barro (1990), public investment has also been widely studied. These literatures includes and not limited to Barro (1979), Barro (1995), Flodén (2001), Battaglini and Coate (2008), Chatterjeea and Turnovsky (2012), Chatterjeea et. al. (2017), Peterman and Sager (2018), etc. In this article, we will build a general equilibrium model that considers public investment. We Consider representative households, firms and public investment, and the market is always clear which determines the equilibrium wage and interest rate. Based on this model we study the optimal level of public debt. 

<br>

#### A. Settings 

Denote 


$$
x_t  = (w_t,r_t,\tau^K_t,\tau^L_t) \quad \text{and} \quad 
x(t) = \left\{x_u: 0 \le u \le t\right\}
$$


to represent the parameters and parameters-path of this economy system, where $w_t$ is labor wage rate and $r_t$ is capital gain rate, $\tau^L_t$ is labor tax rate and $\tau^K_t$ is capital gain tax rate. 

Denote $\epsilon_t$ as the exogenous technique shock which follows diffusion process, 


$$
\epsilon_t = \mu t + se
$$


where $e$ is standard normal distributed random variable. The drift term $\mu$ captures average technique progress while the variance $s$ captures exogenous volatility. 

<br>

*1. Households* 

For a representative household, they maximize their lifetime utility subject to the budget constraint. 


$$
\begin{aligned}
V(A_t; x(t)) = \max_{C_t,L^s_t}\quad &E\int^\infty_t e^{-\rho (u-t)}U(C_u, L^s_u)du\\
s.t.\quad &\dot{A}_t = (1-\tau^L_t)w_tL^s + (1-\tau^K_t)r_tA_t - C_t
\end{aligned}
$$


where $A_t$ is the asset holding at period $t$, $C_t$ is consumption, $L^{s}_{t}$ is the labor supply, and we assume the one-period utility function $U$ is regularly smooth. Note that, the value function $V(A_t;x(t))$ is not stationary over time, since the parameters $x(t)$ are time-variant. 

**Assumption 1. [Inada Condition on $U$]** We assume that $U_C\ge0$, $U_{L^s}\le0$, $\lim_{C\to0}U_C=\infty$, $\lim_{L\to0}U_{L^s}=0$, $\lim_{C\to\infty}U_C=0$, $\lim_{L^s\to\infty}U_{L^s}=-\infty$, and $U_{CC}<0$, $U_{LL}<0$, $U_{CL}=U_{LC}=0$. 

**Lemma 1.** Under Assumption $1$, the optimal consumption $C_{t}$, optimal labor supply $L^s_{t}$ and optimal asset accumulation path $(A_{t})$ are determined by 


$$
\begin{aligned}
U_C(C_t,L_t^s) &= \lambda_t\\
-U_L(C_t,L_t^s) &= \lambda_t\cdot(1-\tau^L_t)w_t\\
\lambda_t &= \lambda_0 \cdot \exp\left[\rho t-\int^t_0(1-\tau^K_u)r_udu\right]\\
\dot{A}_t &= (1-\tau^L_t)w_t \cdot L^s(x(t)) + (1-\tau^K_t)r_t \cdot A_t - C(x(t))
\end{aligned}
$$


***Proof.*** By Pontryagin's maximization principle we denote $\lambda_t \equiv V_A(A_t;x(t))$. Here $\lambda_t$ is future-value Hamiltonian multiplier and $H(C_t,L^s_t,\lambda_t,x(t)) \equiv U(C_t,L^s_t)+\lambda_t \dot{A}_t$ is future-value Hamiltonian. Assumption $1$ ensures the inner point solution and the *optimal* $\lambda_t$ satisfies 


$$
\begin{aligned}&\ -\dot{\lambda_t} + \rho\lambda_t = H_A = \lambda_t\cdot(1-\tau^K_t)r_t\\\Longrightarrow&\ \ V_A(A_t;x(t)) = \lambda_t = D \cdot \exp\left[\rho t -\int^t_0(1-\tau^K_t)r_udu \right]
\end{aligned}
$$


and $D=\lambda_0>0$ if we plug in $t=0$. We then solve the rule of optimal consumption and labor supply by FOC, 


$$
\begin{aligned}
0 &= -V_A(A_t; x(t)) + U_C(C_t,L^s_t)\\
0 &= V_A(A_t; x(t))(1-\tau^L)w_t + U_L(C_t,L^s_t)
\end{aligned}
$$


Combining Hamiltonian and FOC together, and remember to use *future-value* Hamiltonian multiplier in intra-temporal analysis, we have the solution in the Lemma, which altogether determines the optimal asset accumulation path $A_t$. 

***Remark.*** In the solution of the Lemma, by Assumption $1$, functions $C(x(t))$ and $L^s(x(t))$ are well-defined for all $t$. This is because of the *implicit function theorem of equations*. The Jacobian of the solution is 


$$
J = \begin{vmatrix}
U_{CC} & U_{CL}\\
-U_{LC} & -U_{LL}
\end{vmatrix} = -U_{CC}U_{LL} < 0
$$


Thus implicit functions $C(x(t))$ and $L^s(x(t))$ exists. 

<br>

*2. Private Firms* 

For the private firms, we assume the product is $e^{\epsilon_t}\cdot f(K_t,L_t)$, where $K_t$ is capital demand, $L_t$ is labor demand, and the production function $f$ is regularly smooth. Also, $\epsilon_t$ is a diffusion process by settings. Given goods demand $Y_t$, private firms minimize their expenditure 


$$
\begin{aligned}
\min_{K_t,L_t}\quad &w_tL_t + r_tK_t \\
s.t.\quad &e^{\epsilon_t} \cdot f(K_t,L_t)\ge Y_t
\end{aligned}
$$


**Assumption 2. [Inada Condition on $f$]** We assume that $f_K\ge0$, $f_L\ge0$, $\lim_{K\to0}f_K=\infty$, $\lim_{L\to0}f_{L}=\infty$, $\lim_{K\to\infty}f_K=0$, $\lim_{L\to\infty}f_L=0$, and $f_{KK}<0$, $f_{LL}<0$, $f_{KL}=f_{LK}>0$. 

Under Assumption $2$, we have inner point solution. Suppose $\eta_t$ is the Lagrangian multiplier, the cost minimization problem above gives 


$$
\begin{aligned}
r_t & = \eta_t \cdot e^{\epsilon_t} \cdot f_K(K_t,L_t) \\
w_t & = \eta_t \cdot e^{\epsilon_t} \cdot f_L(K_t,L_t) \\
Y_t &= e^{\epsilon_t} \cdot f(K_t,L_t)
\end{aligned}
$$


which determines the optimal capital demand $K(r_t,w_t, Y_t, \epsilon_t)$ and labor demand $L(r_t,w_t,Y_t,\epsilon_t)$. 

<br>

*3. Government* 

For public economy, i.e. SOE, we assume they also follow the production function $f$, however their productions are not affected by the exogenous shock. Public economy is driven by public debt $B_t$. We denote the productions of public firms 


$$
Y'_t = f(B_t,L'_t) 
$$


Public firms do not seek to maximize their profit. They merely follow the government plan on debt $B_t$ and labor demand $L'_t$, and then arrange their production plan. 

Government maximize the social welfare function, which is replaced by representative utility function, in two steps. First, select the optimal derived labor demand $L'_t$ subjecting to two constraints: (1) asset accumulation function, (2)  government budget constraint and (3) No-Ponzi constraint. Suppose household consumption $C$ and household labor supply $L^s$ take the optimal, then 


$$
\begin{aligned} 
Q_0 = \max\quad & E\int^\infty_0 e^{-\rho t}U(C(x(t)), L^s(x(t)))du\\ 
s.t.\quad 
&\dot{B}_t = G_t + r_tB_t + w_tL'_t - Y'_t - \tau^K_t A_t r_t - \tau^L_t L^s(x(t)) w_t\\
&\dot{A}_t = (1-\tau^L_t)w_t \cdot L^s(x(t)) + (1-\tau^K_t)r_t \cdot A_t - C(x(t))\\
&\lim_{t\to\infty}e^{-r_tt}B_t = 0
\end{aligned}
$$


**Lemma 3.** Under Assumption $1$ and $2$, the optimal public labor demand $L'_{t}$ is determined by 


$$
\begin{aligned}
w_t = f_L(B_t,L')
\end{aligned}
$$


***Proof.*** Define 


$$
H_{t} = U(C_{t},L^{s}_{t}) + \gamma_{t} \dot{B}_{t} + \eta_{t} \dot{A}_{t}
$$


where $\gamma$ is the future-value Hamilton multiplier with respect to state variable $B$ while $\eta$ is for state variable $A$. By first order condition with respect to ${L'}_{t}$ we have 


$$
\begin{aligned}
0 &= \gamma_t \cdot (w_t-f_L(B_t,L'_t))
\end{aligned}
$$


which gives the first result. 

***Remark.*** The nature of optimization problem above is quite complex that we cannot resort to traditional variation method or control theories. 

<br>

*4. Equilibrium* 

**Definition 1. [General Equilibrium]** We assume Assumptions $1$-$2$ holds. Given $A_0$ and given $B_0=0$, the optimal parameters-path $x(t)$ is determined by following labor and asset markets clear conditions, 


$$
\begin{aligned}
L^s(x(t)) =\ &L(x(t),G_t,\epsilon_t) + L'(w_t,B_t) \\
A_t =\ &K(x(t),G_t,\epsilon_t) + B_t
\end{aligned}
$$


where $\gamma_0$ is undetermined, and *discounted* $C(x(t))$ and $L^s(x(t))$ are given by 


$$
\begin{aligned}
U_C(C_t,L^s_t) &= \lambda_0 \cdot e^{-\int^t_0 (1-\tau^K_u)r_udu}\\
U_L(C_t,L^s_t) &= -\lambda_0 \cdot e^{-\int^t_0 (1-\tau^K_u)r_udu}\cdot(1-\tau^L)w_t
\end{aligned}
$$


thus the incremental accumulated asset is given by 


$$
\dot{A}_t = (1-\tau^L_t)w_t \cdot L^s(x(t)) + (1-\tau^K_t)r_t \cdot A_t - C(x(t)) 
$$


and $L'(w_t,B_t)$ is given by 


$$
w_t = f_{L}(B_t,L') 
$$


and $K(x(t),G_t,\epsilon_t)$, $L(x(t),G_t,\epsilon_t)$ are given by 


$$
\begin{aligned}
\frac{r_t}{w_t} =\ &\frac{f_K(K,L)}{f_L(K,L)}\\
\dot{A}_t + C(x(t)) + G_t =\ &e^{\epsilon_t}\cdot f(K,L) + f(B_t,L'(w_t,B_t))
\end{aligned}
$$


Note that, public goods expenditure $G_{t}$ is taken as exogenous. Finally, the optimal bond path is given by 


$$
\begin{aligned}
\dot{B}_t =\ &G_t + r_tB_t + w_tL'(w_t,B_t) - f(B_t,L'(w_t,B_t)) - \\
             &\tau^K_t A_t r_t - \tau^L_t L^s(x(t)) w_t
\end{aligned}
$$


***Remark.*** We have 6 equilibrium conditions above in all together. In the first conclusion, we impose labor market and capital market clear conditions and social welfare optimization conditions. The four equations determine the optimal parameters. In conclusion five, we impose goods market clear conditions. 

<br>

*5. Optimal Tax Rate* 

We take the market clear conditions into the social welfare maximization problem. Then we have 


$$
\begin{aligned}
Q_0 = \max\quad & E\int^\infty_0 e^{-\rho t}U(C_t, L^s_t)du\\ 
s.t.\quad 
&\dot{B}_t = G_t + r_tB_t + w_tL'_t - Y'_t - \tau^K_t A_t r_t - \tau^L_t L^s_t w_t\\
&\dot{A}_t = (1-\tau^L_t)w_t \cdot L^s_t + (1-\tau^K_t)r_t \cdot A_t - C_t\\
&L^s_t =  L_t + L'_t\\
&A_t = K_t + B_t \\
&\dot{A}_t = e^{\epsilon}\cdot f(K_t,L_t) + Y'_t -C_t - G_t\\
&\lim_{t\to\infty}e^{-r_tt}B_t = 0 \\
\end{aligned}
$$


which can be transformed into 


$$
\begin{aligned}
Q_0 = \max\quad & E\int^\infty_0 e^{-\rho t}U(C_t, L_t + L'_t)du\\ 
s.t.\quad 
&\dot{B}_t = G_t + r_tB_t + w_tL'_t - Y'_t - \tau^K_tA_t r_t - \tau^L_t(L_t + L'_t)w_t\\
&\dot{A}_t = (1-\tau^L_t)w_t \cdot (L_t + L'_t) + (1-\tau^K_t)r_t \cdot A_t - C_t\\
&0 = e^{\epsilon}\cdot f(A_t - B_t,L_t) + Y'_t - G_t - (1-\tau^L_t)w_t \cdot (L_t + L'_t) - (1-\tau^K_t)r_t \cdot A_t\\
&\lim_{t\to\infty}e^{-r_tt}B_t = 0 \\
\end{aligned}
$$


**Lemma 4.** Under Assumption $1$ and $2$, in equilibrium the optimal capital gain tax rate $\tau^K_t$ and $\tau^L_t$ satisfies 


$$
\frac{e^{\epsilon_t}f_K(K, L) - r_t}{e^{\epsilon_t}f_L(K, L) - w_t} = \frac{\tau^K_t r_t}{\tau^L_t w_t}
$$


***Proof.*** Set the Hamiltonian to be 


$$
H = \gamma_t \dot{B}_t + \eta_t \dot{A}_t + \psi_t g_t
$$


where $0=g_t$ is the third constrain of the above optimization problem. Then we have the following conditions 


$$
\begin{aligned}
&H_{C} = 0 = U_C - \eta_t\\
&H_{L} = 0 = U_L + \gamma_t(-\tau^L_t w_t)+\eta_t(1-\tau^L_t)w_t + \psi_t\left[e^{\epsilon_t}f_L(A_t-B_t),L_t)-(1-\tau^L_t)w_t\right]
\end{aligned}
$$


Compared with the household optimization condition in Lemma 1, we have 


$$
\begin{aligned}
\eta_t &= \lambda_t\\
\tau^L_t\gamma_t w_t &= \psi_t\left[e^{\epsilon_t}f_L(A_t-B_t,L_t)-(1-\tau^L_t)w_t\right]
\end{aligned}
$$


By Pontryagin's maximization principle we have 


$$
-\dot{\eta}_t + \rho\eta_t = H_A = \gamma_t(-\tau^K_t r_t)+\eta_t(1-\tau^K_t)r_t + \psi_t\left[e^{\epsilon_t}f_K(A_t-B_t,L_t)-(1-\tau^K_t)r_t\right]
$$


Finally, we have 


$$
\tau^L_t\gamma_tw_t = \psi_t(e^{\epsilon_t}f_L(A_t-B_t,L_t)-(1-\tau^L_t)w_t)\\
\tau^K_t\gamma_tr_t = \psi_t(e^{\epsilon_t}f_K(A_t-B_t,L_t)-(1-\tau^K_t)r_t)
$$


which gives the result. 

**Proposition 1. [Optimal Tax Rate]** In equilibrium, given Assumption $1$-$2$ hold, we must have 


$$
\tau^K_t = \tau^L_t
$$


***Proof.*** Lemma $4$ combined with  equilibrium five gives this result. 

<br>

#### B. An Example 

We first give some numerical assumptions to the global parameters. These parameters include 

- Time discretization interval $h$. We need to discretize the continuous time. 
- Time horizon $T$. We use a large $T$ to replace infinity. 
- Utility discount rate $\rho$. 
- Initial asset endowment $A_0$. 

We assume the utility function is 


$$
U(C, L^s) = log(C) - \frac{1}{2}(L^s)^2
\quad\Longrightarrow\quad
\begin{aligned}
U_C(C, L^s) &= 1/C\\
U_L(C, L^s) &= -L^s
\end{aligned}
$$


It is easy to verify this utility function satisfies Assumption $1$, thus, it ensures the inner point of optimal $C$ and $L^s$. By equilibrium condition 2, the *discounted* optimal consumption and labor supply are determined by 


$$
\begin{aligned}
U_C(C_t,L^s_t) &= \lambda_0 \cdot e^{-\int^t_0 (1-\tau^K_u)r_udu}\\
U_L(C_t,L^s_t) &= -\lambda_0 \cdot e^{-\int^t_0 (1-\tau^K_u)r_udu}\cdot(1-\tau^L_t)w_t
\end{aligned} 
$$

$$
\Longrightarrow 
\begin{aligned}
C(x(t))   &= \lambda_0^{-1} \cdot e^{\int^t_0 (1-\tau^K_u)r_udu}\\
L^s(x(t)) &= \lambda_0 \cdot e^{- \int^t_0 (1-\tau^K_u)r_udu}\cdot(1-\tau^L_t)w_t
\end{aligned}
$$


Without loss of generality, we assume the undetermined parameter $\lambda_0 = 1$. Actually, $\lambda_0$ is only related to the initial endowment state. Thus, according to  equilibrium condition 3 we can represent the incremental asset $\dot{A}_t$ as a function of $A_t$ and $x(t)$. Also, we assume the production function is Cobb-Douglas function 


$$
f(K,L) = K^\alpha \cdot L^{1-\alpha}
\quad\Longrightarrow\quad
\begin{aligned}
f_K(K, L) &= \alpha K^{\alpha - 1} \cdot L^{1-\alpha}\\
f_L(K, L) &= (1-\alpha) K^\alpha \cdot L^{-\alpha}
\end{aligned}
$$


The equilibrium condition 4 gives the optimal government labor demand 


$$
L' = \left(\frac{1-\alpha}{w}\right)^{1/\alpha} \cdot B
$$


By equilibrium condition 5, we implement *goods market clear condition* and get 


$$
\begin{aligned}
\frac{r_t}{w_t} =\ &\frac{f_K(K,L)}{f_L(K,L)}\\
C(x(t)) + G_t + \dot{A}_t =\ &e^{\epsilon_t}\cdot f(K,L) + f(B_t,L')
\end{aligned}
$$

$$
\Longrightarrow\quad
\begin{aligned}
0 &= r_t f_L(K, L) - w_t f_K(K, L)\\
0 &= e^{\epsilon_t}\cdot f(K,L) + f(B_t,L') - C(x(t)) - G_t - \dot{A}_t
\end{aligned}
$$


Thus we can get the analytic solution of $K$ and $L$, 


$$
\begin{aligned}
K(x(t),G_t,\epsilon_t) &= e^{-\epsilon_t}\cdot\frac{C_t + G_t + \dot{A}_t - f(B_t,L'_t)}{\left(\frac{r_t}{w_t}\frac{1-\alpha}{\alpha}\right)^{1-\alpha}}\\
L(x(t),G_t,\epsilon_t) &= \frac{r_t}{w_t}\frac{1-\alpha}{\alpha}K(x(t),G_t,\epsilon_t)
\end{aligned}
$$


Then, by equilibrium condition 1 we can determine the equilibrium $r_t$ and $w_t$, given $x(t-h)$, $A_t$, $B_t$ $G_t$ and $\epsilon_t$. 


$$
\begin{aligned}
0 &= h^{2}(x(t),A_t,B_t,G_t,\epsilon_t) = L^s(x(t)) - L(x(t),G_t,\epsilon_t) - L'(w_t,B_t) \\
0 &= h^{1}(x(t),A_t,B_t,G_t,\epsilon_t) = A_t - K(x(t),G_t,\epsilon_t) - B_t
\end{aligned}
$$


And finally, according to equilibrium condition 3 and 6 we need to update the value of state variables, from $A_{t}$ and $B_{t}$ into $A_{t+h}$ into $B_{t+h}$. 

<br>

<br>

### Reference

Barro, Robert J (1974). Are Government Bonds Net Wealth? Journal of Political Economy. 82(6): 1095-1117. Retrived from: http://www.jstor.org/stable/1830663

Barro, Robert J (1979). On the determination of the public debt. Journal of Political Economy. 87(5): 940-971.doi: [10.1086/260807](https://doi.org/10.1086/260807) 

Barro, Robert J (1999). Notes On Optimal Debt Management. Journal of Applied Economics, v2(2,Nov), 282-290. Retrived from: https://www.nber.org/papers/w5327 

Battaglini, Marco & Coate, Stephen (2008). A Dynamic Theory of Public Spending, Taxation, and Debt, American Economic Review, vol. 98(1). 201-36. doi: [10.1257/aer.98.1.201](https://doi.org/10.1257/aer.98.1.201) 

Chatterjee, Santanu & Turnovsky, Stephen J. (2012). Infrastructure and inequality. European Economic Review. 56(8). 1730-1745. doi: [10.1016/j.euroecorev.2012.08.003](https://doi.org/10.1016/j.euroecorev.2012.08.003) 

Chatterjee, Santanu & Gibson, John & Rioja, Felix (2017). Optimal public debt redux. Journal of Economic Dynamics and Control. 83. 162-174. doi: [10.1016/j.jedc.2017.08.005](https://doi.org/10.1016/j.jedc.2017.08.005) 

Flodén, Martin (2001). The effectiveness of government debt and transfers as insurance. Journal of Monetary Economics. 48(1). 81-108. doi: [10.1016/S0304-3932(01)00064-2](https://doi.org/10.1016/S0304-3932(01)00064-2) 

Peterman, William B. & Sager, Erick (2018). Optimal Public Debt with Life Cycle Motives. Finance and Economics Discussion Series 2018-028. Washington: Board of Governors of the Federal Reserve System, doi: [10.17016/FEDS.2018.028.](https://doi.org/10.17016/FEDS.2018.028) 