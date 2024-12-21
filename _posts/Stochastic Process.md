---
layout:     post
title:      Stochatic Process
subtitle:   Notes
date:       2024-12-21
author:     ManifoldCaffe
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - Math
    - Stochastic Process
---

# §1 Intro
## §§1.2 Kolmogorov thm. and separability
### 1. Kolmogorov Theorem
**Proposition**: Suppose $(\mathscr{S}, \mathscr{F})$ is a Polish space with a compatible probability measure family $\{P_s|s \in \bigcup_{i=1}^\infty T^i\}$, then there is a probability $P$ on $(\mathscr{S}^T, \mathscr{F}^T)$ s.t. coincides with $P_s$ on finite rec
tangle parabolic set on $\mathscr{S}^T$.
### 2. Separability
**Definition**: *Separability of stochastic process*: $\forall$open interval $I$, $\forall$ closed set $F$, $\xi_t(\omega) \in F$, $\forall t \in S \cap I$ 
$\implies \xi_t(\omega) \in F$, $\forall t \in T \cap I$ a.e
If $\xi$ is separable, then $\sup_{t\in (a, b)}\xi_t$ , $\inf_{t \in (a,b)}\xi_t$ a.e. $\mathscr{B}^T$-measurable. ($\{\omega | \sup_{t \in (a,b)} \xi_t \leq a\} = \left\{\omega | \xi_t \leq a, \forall t \in (a,b) \right\}$, when $\omega \in N^c, \{\omega|\xi\leq A, \forall t\in(a,b)\}=\{\omega|\xi\leq A, \forall t \in (a,b) \cap S\} = \sup_{t \in S}\xi_t = \bigcap_{i\in S} \{\omega|\xi_i \leq A\} \in \mathscr{B}^T$
### 3. Shift Operator
**Definition**: (*Shift operator*) Let $(\Omega, \mathscr{F})=(\mathscr{S}^T,\Sigma^T)$ , $T$ is closed under addition. Define $\theta^t:\mathscr{S}^T \rightarrow \mathscr{S}^T$ s.t. $(\theta^t\omega)_s = \omega_{s+t}$. Then $\theta^t$ is $\Sigma^T - \Sigma^T$ measurable. From $\theta^t$ we get a set operator $\theta^{-t}$: $\theta^{-t}\{\omega|(\omega_{t_1}, \dots, \omega_{t_n})\in B\} = \{\omega|(\omega_{t_1+t}, \dots, \omega_{t_n+t}) \in B\}$, $\forall B \in \Sigma^n$. And a function operator $\theta^t$: $\theta^tf(\omega_{t_1}, \dots, \omega_{t_n}, \dots) = f(\omega_{t_1 + t}, \dots, \omega_{t_n + t}, \dots)$. If $\mathrm{P}\circ \theta^t = \mathrm{P}$, then $f = g \implies \theta^t f \implies \theta^t g$.
## §§1.3 Independent Increment Process and Martingale
### 1. Independent Increment Process
**Definition**: *Independent increment process*: $\forall t_0<t_1<\dots<t_n \in T$, $\xi_{t_0}, \xi_{t_1} - \xi_{t_2}, \dots, \xi_{t_n}-\xi_{t_{n-1}}$are independent
**Properties**: 
+ Suppose $\mathbb{E}(\xi_t) = 0 (\forall t \in T)$, $\mathscr{F} = \sigma(\xi_u; u \leq s \in T)$. Then $\forall s < t \in T$, $\mathbb{E}(\xi_t|\mathscr{F}_s) = \xi_s$.
+ $\forall s < t$ and $\mathscr{B}_\mathbf{R}$-measurable function $f$. $\mathbb{E}(f(\xi_t)|\mathscr{F}_s) = \mathbb{E}(f(\xi_t)|\xi_s)$. (Markov property)
	*Proof: 
	**lemma**: Let $(\Omega, \mathcal{F}, \mathbf{P})$ be a probability space, $\mathcal{G}$ is a sub-$\sigma$-field of $\mathcal{F}$, $(S, \mathcal{S})$ and $(E, \mathcal{E})$ are measurable spaces, $X$ is a $S$-valued r.v. , $Y$ is a $E$-valued r.v. . Suppose $Y$ is independent of $\mathcal{G}$. Let $g$ be a $\mathcal{S} \times \mathcal{E}$-measurable function on $(S, E)$ s.t. $\mathbb{E}[|g(X, Y)|] < \infty$, then $\mathbb{E}[g(X, Y)|\mathcal{G}] = \mathbb{E}[g(x, Y)]|_{x = X}$.
	It's sufficient to show that $\mathbb{E}(f(\xi_t)|\mathscr{F}_s)$ is $\sigma(\xi_s)$-measurable which follows from the lemma noticing that $\mathbb{E}(f(\xi_t)|\mathscr{F}_s) = \mathbb{E}(f(\xi_t - \xi_s + \xi_s)|\mathscr{F}_s)$.*
### 2. Martingale
*Martingale*: $\{\xi_t, \mathscr{F}_t; t \in T\}$ is a martingale, if $\forall s \leq t \in T$, $\mathbb{E}[|\xi_t|] < +\infty$, $\mathbb{E}(\xi_t)|\mathscr{F}_s) = \xi_s$. Especially, when $\mathscr{F}_s = \sigma(\xi_u; u \leq s)$, we call $\xi = \{\xi_t\}$ is a martingale for short.
**Proposition**: $\xi$ is a martingale, then $$\mathbb{E}(\xi_t|\mathscr{F}_s) = \xi_s, \forall s \leq t \iff \mathbb{E}(\xi_{t_{n + 1}} | \xi_{t_0}, \dots, \xi_{t_n}) = \xi_{t_n}, \forall t_1 < t_2 < \dots < t_n \in T.$$
	*Proof:
	$\Leftarrow$: $\mathbb{E}(\xi_t|\mathscr{F}_s) = \mathbb{E}({\mathbb{E}(\xi_t|\xi_{t_0}, \xi_{t_1}, \dots, \xi_{s})|\mathscr{F}_s}) = \mathbb{E}(\xi_s | \mathscr{F}_s) = \xi_s$.
	$\Rightarrow$: It's sufficient to show that $\mathbb{E}(\xi_{t_{n+1}} \chi_B) = \mathbb{E}(\xi_{t_{n}} \chi_B), \forall B \in \sigma(\xi_{t_0}, \dots, \xi_{t_n}) \subset \mathscr{F}_s$ , which follows from the left side directly.*

**Remark**: All real-valued independent increment processes with constant mean are martingale but the opposite is not true. Because $\mathbb{E}(\xi_{t+s} | \mathscr{F}) = \mathbb{E}(\xi_{t+s} - \xi_s | \mathscr{F}_s) + \xi_s$, when $\xi$ is a process with independent increment and constant mean, the first term of the rhs equals $0$, but this doesn't necessarily mean $\xi_{t+s} - \xi_{s}$ is in independent with $\mathscr{F}_s$.
### 3. Properties of Process with Independent Increment and Stable Process
**Definition**: ==Stable Process==: $\exists a > 0$ s. t. $\forall c > 0, \xi_{ct} \overset{d}{=} c^{\frac{1}{a}} \xi_t$.
**Example**: Brown motion $\{B_t, t \in \mathbb{R}\}, B_{ct}, c^{\frac{1}{2}}B_t \sim N(0,ct)$, 
## §§1.4 Markov Process
**Definition**: ==Markov Process== Suppose $\xi$ is a stochastic process on $(\Omega, \mathscr{F}, \mathbb{P})$ and takes values on $(\mathscr{S}, \Sigma)$, ${\mathscr{F}_t; t \in T}$ is a family of $\sigma$-algebra s.t. $\forall s < t$, $\mathscr{F}_s \subset \mathscr{F}_t$, $\xi$ is adapted w.r.t. $\{\mathscr{F}_t\}$. We call $\xi$ is a Markov process when $\forall s < t \in T, B \in \Sigma$, $\mathbb{P}(\{\omega, \xi_t(\omega) \in B\} | \mathscr{F}_s) = \mathbb{P}(\{\omega, \xi_t(\omega) \in B\} | \xi_s)$. Especially, when $\mathscr{F}_t = \sigma(\xi_u; u \leq t) = \mathbb{P}(\{\omega | \xi_t(\omega) \in B\} | \xi_s)$, we call $\boldsymbol \xi$ is the Markov process on $(\Omega, \mathscr{F}, \mathbb{P})$.

**Proposition**: $\boldsymbol{\xi}$ is a Markov process on $(\Omega, \mathscr{F}, \mathbb{P})$, iff $\forall n \geq 1$, $t_1 < t_2 <\dots < t_n < t_{n + 1} \in T$, $\mathbb{P}(\xi_{t_{n + 1}} \in B | \xi_{t_1}, \xi_{t_2}, \dots, \xi_{t_n}) = \mathbb{P}(\xi_{t_{n + 1}} \in B | \xi_{t_n})$.
	Proof: $\Rightarrow$: Trivial.
	$\Leftarrow$: We only need to show that $\forall A \in \mathscr F_s$, $\mathbb E(\mathbb P(\xi_t | \xi_s)\chi_A) = \mathbb E(\xi_t \chi_A)$. Let $\mathcal G = \{A | \mathbb E(\mathbb P(\xi_t | \xi_s)\chi_A) = \mathbb E(\xi_t \chi_A)\}$. We can see that $\forall t_1, \dots, s \in T$, $\sigma(\xi_{t_1}, \dots, \xi_s) \subset \mathcal G$, so the family of finite dimensional rectangle parabolic sets $\mathcal C \subset \mathcal G$. And it's easy to check that $\mathcal G$ is a $\lambda$-system, thus $\mathscr F_s = \sigma(\mathcal C) = \lambda(\mathcal C) \subset \lambda(\mathcal G) = \mathcal G$.
**Proposition**: The followings are equivalent.
1. $\xi$ is a Markov process
2. $\forall s < t \in T$ and bounded real-valued function $f \in (\mathscr{S}, \Sigma)$, $$\mathbb{E}(f(\xi_t) | \mathscr{F}_s) = \mathbb{E}(f(\xi_t) | \xi_s).$$
3. Let $\mathscr{F}^s = \sigma(\xi_u; u \geq s)$, $\forall$ bounded real-valued r.v $g \in \mathscr{F}^t$, $\mathbb E(g | \mathscr F_s) = \mathbb E (g | \xi_s)$.
4. $\forall$ bounded real-valued function $f \in \mathscr F_s$ and $g \in \mathscr F^s$, $\forall s \in T$, $\mathbb E(fg | \xi_s) = \mathbb E(f | \xi_s) \mathbb E(g | \xi_s)$.
	Proof: 2 $\implies$ 3: For measurable real-valued function $f_1, f_2$ and $t_2 > t_1 \geq s$, 
	$$
	\begin{align}
	\mathbb E(f_1(\xi_{t_1})f_2(\xi_{t_2}) | \mathscr F_s) &= \mathbb E(f_1(\xi_{t_1})\mathbb E(f_2(\xi_{t_2}) | \mathscr F_{t_1}) | \mathscr F_s)\\
	&=\mathbb E(f_1(\xi_{t_1})\mathbb E(f_2(\xi_{t_2}) | \xi_{t_1}) | \mathscr{F}_{s}))\\
	&=\mathbb E(f_1(\xi_{t_1})\mathbb E(f_2(\xi_{t_2}) | \mathscr \xi_{t_1}) | \xi_s))\\
	&= \mathbb E(f_1(\xi_{t_1}) \mathbb E(f_2(\xi_{t_2}) | \mathscr{F}_{t_1}) | \xi_s)\\
	&= \mathbb E(\mathbb E(f_1(\xi_{t_1})f_2(\xi_{t_2}) | \mathscr{F}_{t_1}) | \xi_{s})\\
	&= \mathbb E(f_1(\xi_{t_1}) f_2(\xi_{t_2}) | \xi_s)
	\end{align}
	$$
	By reduction, $\forall f_1, f_2, \dots, f_n \in \Sigma$ and $t_n > t_{n - 1} > \dots > t_1 \geq s$,
	$$
	\mathbb E(f_1(\xi_{t_1})f_2(\xi_{t_2})\cdots f_n(\xi_{t_n}) | \mathscr F_s)\\
	=\mathbb E(f_1(\xi_{t_1})f_2(\xi_{t_2})\cdots f_n(\xi_{t_n}) | \xi_s).
	$$
	Especially, $\forall A_1, \dots, A_n \in \Sigma$, 
	$$
	\mathbb E(\chi_{A_1}(\xi_{t_1})\cdots \chi_{A_n}(\xi_{t_n}) | \mathscr F_s) = \mathbb E(\chi_{A_1}(\xi_{t_1}) \cdots \chi_{A_n}(\xi_{t_n}) | \xi_s).
	$$
	Let 
	$$
	\begin{align}
	\mathscr S \triangleq& \{B | B = \{\omega ; \xi_{t_1} \in A_1, \cdots, \xi_{t_n} \in A_n\},\\
	&\text{ for some } t_n > t_{n-1} > \cdots > t_1 \geq s; A_1, \dots, A_n \in \Sigma, n \geq 1\}\\
	\mathscr H \triangleq& \{g \in \mathscr F^t | \mathbb E(g | \mathscr F_s) = \mathbb E (g | \xi_s) \}.
	\end{align}.
	$$
	Obviously, $\mathscr S$ is a $\pi$ system. And $\forall A \in \mathscr S$, $\chi_A \in \mathscr H$, $1 \in \mathscr H$ and $f_n \in \mathscr H, n \geq 1, 0 \leq f_n \uparrow f \implies f \in \mathscr H$. Hence by monotone class thm. of function. All $\sigma(\mathscr S)$ measurable function belong to $\mathscr H$.
**Remark**: $\xi_t$'s conditional expectation w.r.t. $\xi_s$'s given value $\mathbb E( \xi_t \in A | \xi_s = x)$ and the initial distribution $\mathbb P \circ \xi_0^{-1}$ determine the distribution of $\boldsymbol \xi$.
**Definition**: $p(s, x; t, A) \triangleq \mathbb E(\chi_{\{\xi_t \in A\}} | \xi_s = x)$, $p_0(A) \triangleq \mathbb P([\xi_0 \in A])$.
***
**Theorem**:

**Definition**: (family of transitive probability): 
1. For fixed $x, s, t$, $p(s, x; t, A)$ is a probability measure on $(\mathscr S, \Sigma)$;
2. For fixed $A, s, t$, $p(s, \cdot; t, A)$ is a $(\mathscr S, \Sigma)$- measurable function.
3. $\forall s \leq r \leq t$, we have Kolmogorov-Chapman equation:
$$
p(s, x; t, A) = \int p(s, x; r, \mathrm{d}y) p(r, y; t, A)
$$
**Proposition**: Let $(\mathscr S, \Sigma)$ is a complete divisible metric space generated measure space; $\{p(s, x; t, A); s < t \in T, x \in \mathscr S, A \in \Sigma \}$ is a transitive probability measure family, then we can construct a measure space $(\Omega, \mathscr F, \mathbb P)$ and a Markov process $\boldsymbol \xi$, s.t. 
$$
\mathbb P([\xi_t \in A]) = p(s, x; t, A).
$$
	**Proof**: We use Kolmogorov theorem to construct probability space. For this, let $\Omega = \mathscr S^T$, $\mathscr C$ is the family of finite dimension measurable sets on $\Omega$, $\mathscr F = \sigma(\mathscr C)$. For $\forall t_1 < t_2 < \dots < t_n \in T$ and $\forall \tilde A \in \Sigma^n$. Let
	$$
	F_{t_1, \dots, t_n}(\tilde A) = \int p_0(\mathrm{d} x_0) \int p(0, x_0; t_1, \mathrm d x_1) \cdots \int p(t_{n - 1}, x_{n - 1}; t_n, \mathrm d x_n) \chi_{\tilde A}.
	$$
**Theorem(Tulcea)**: 
1. $\forall \omega \in A \in \mathscr F_{n - 1}, Q(n, \omega, A) = 1$;
2. compactness,  $$A_n(\omega) \triangleq \bigcap_{A \in \mathscr F_n, \omega \in A} A.$$for any sequence $\omega^{(n)} \in \Omega(n \geq 1)$, $\forall N \geq 1, \bigcap_{n = 1}^N A_n(\omega^{(n)}) \neq \varnothing \implies \bigcap_{n = 1}^\infty A_n(\omega^{(n)}) \neq \varnothing$. 
$\mathscr F_n \subset \mathscr F$, $\mathscr F_n \uparrow \mathscr F ( n \geq 0)$, $\{Q_0(\cdot)\}$, $\{Q_n(\omega; \cdot)\}$ satisfy that $Q(0, \cdot)$ is a measure on $(\Omega, \mathscr F_0)$, $Q_n(\omega; \cdot)$ is a probability measure on $(\Omega, \mathscr F_n)$ for given $\omega$ and for given $A \in \mathscr F_n$, $Q_n( \cdot; A)$ is $\mathscr F_{n - 1}$-measurable. 1. and 2. hold. Then $\exists!$ probability measure $\mathbb P$ on $(\Omega, \mathscr F)$ s.t.
1. $\mathbb P |_{\mathscr{F}_0} = Q_0(\cdot)$ (i.e. $\forall A \in \mathscr F_0, \mathbb P(A) = Q_0(A)$);
2. $$
\begin{align}
\mathbb E(\chi_A | \mathscr F_{n - 1}) = Q_n(\omega; A)(\forall A \in \mathscr F_n) \\
\iff \int_{A \cap B} \mathrm d \mathbb P = \int_B Q_n(\omega; A) \mathbb P(\mathrm d \omega) (\forall A \in \mathscr F_n, B \in \mathscr F_{n - 1}) \\
\implies \mathbb P(A) = \int Q_n(\omega; A) \mathbb P(\mathrm d \omega) (\forall A \in \mathscr F_n)
\end{align}
$$
## §§1.5 Gauss System
**Definition**(Gauss system): We a stochastic process $\boldsymbol \xi$ on $(\Omega, \mathscr F, \mathbb P)$ is a Gauss system if for $\forall t_1, t_2, \cdots, t_n \in T, (\xi_{t_1}, \cdots, \xi_{t_n})$'s joint distribution is Gaussian, i.e.
$$
\mathbb E \exp^{\imath \sum_{k = 1}^{n} \lambda_k \xi_{t_k}} = \exp^{\imath \sum_{k = 1}^n \lambda_k \mathbb E(\xi_{t_k}) - \frac{1}{2}\sum_{i,j}\lambda_i \mathrm{Cov}(\xi_{t_i},\xi_{t_j})\lambda_j}
$$
**Proposition**: $\boldsymbol \xi$ is a Gauss system iff any finite r.v.'s linear combination is a $1$-dimension Gaussian distribution, i.e. $\forall t_1, t_2, \cdots, t_n \in T(n \geq 1)$, $\alpha_k$ is real number$(1 \leq k \leq n)$, r.v. $\sum_{k = 1}^n \alpha_k \xi_{t_k} \sim N$.
**Proposition**: For $\forall n$
**Proposition**: Let $\boldsymbol \xi = \{\xi_t; t \in T\}$ is a Gauss system, then:
1. $\boldsymbol \xi$ is independent iff $\forall s \neq t(s, t \in T), \sigma(s, t) \triangleq \mathbb E(\xi_t - \mathbb E \xi_t)(\xi_s - \mathbb \xi_s) = 0$.
2. $\xi_{t_0}$ is independent with $\{\xi_t; t \in T, t \neq t_0\}$ iff $\sigma(t_0, t) = 0 (\forall t \in T, t \neq t_0)$.
**Proposition**: Let $\boldsymbol \xi$ is a Gauss system, and let $\xi_{t_n} \in \boldsymbol \xi$, then $\xi_{t_n} \overset{\mathbb P}{\to} \xi_0 (n \to \infty)$. Then $\mathbb \xi_{t_n} \overset{L^2}{\to} \xi_0  (n \to \infty)$. And $\xi_0$ is Gaussian.
	**Proof**: $\forall \epsilon > 0$, $\mathbb P( | \xi_{t_j} - \xi_{t_k} | > \epsilon) \to 0 (k, j \to \infty)$. And  $LHS =$.
## §§2.2 Stopping Time and Stopping Theorem of Martingale
