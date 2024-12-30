---
layout: post
title: Note on Advanced Probability Theory
subtitle: ---
date: 2024-12-30
header-img: img/post-bg-coffee.jpeg
author: ManifoldCaffe|流形咖啡
catalog: true
tags:
  - probability-theory
  - math
---

**Proposition**: $\lim_{x \rightarrow \infty} x\mathbb{P}(|X_1| \geq x) = 0 \Leftrightarrow \frac{1}{n} \sum_{i = 1}^n X_i - \mathbb{E} X_1 \chi_{[|X_1| \leq n]}$ 

**Kolmogorov ineq.** : Let $\{X_i\}$ be an i.i.d r.v. seq., $S_n = \sum_{i = 1}^n X_i$, then $\forall \epsilon > 0$, $\mathbb{P} (\sup_{1 <= k <= n} | S_k - \mathbb{E} S_k | \geq \epsilon) \leq \frac{1}{\epsilon} D(S_n)$.
Supremum inequality, $\{S_n - \mathbb{E} S_n\}$ is a martingale

**Theorem.**: Let $\{X_n\}$ be a iid r.v. and $\sum_n D X_n < +\infty$, then $\sum_n(S_n - \mathbb X_n)$ converges a.e. .

**Proof**: W. L. O. G. , suppose $\mathbb{E} X_n = 0, \forall n \geq 1$. Let $S_n = \sum_{i = 1}^n X_i, n \geq 1$. $S_n$ converges a.s. $\Leftrightarrow$ $S_n - S_m \overset{a.s.}{\rightarrow} 0$ as $n, m \rightarrow +\infty$ $\Leftrightarrow$ $\forall \epsilon > 0$, $\mathbb{P}(\bigcap_{l = 1}^\infty \bigcup_{m, n > l}[| S_n - S_m | \geq \epsilon]) = 0$ 
***

**Definition**: A measurable space is called separable, if every atom of it is singleton. Two measurable spaces are called isomorphic if there exists a bijection that is measurable both sides (which is called measurable a isomorphism). [](https://www.bananaspace.org/wiki/%E8%AE%B2%E4%B9%89:%E9%9B%86%E5%90%88%E8%AE%BA%E5%9F%BA%E7%A1%80_(OperatorP)/%E5%88%9D%E7%AD%89%E6%8F%8F%E8%BF%B0%E9%9B%86%E5%90%88%E8%AE%BA/%E6%A0%87%E5%87%86Borel%E7%A9%BA%E9%97%B4)

**Lemma**: Let $(E, \mathcal{E})$ be a divisible and separable measure space, then $(E, \mathcal{E})$ is isomorphic to $(\mathbb{R}, \mathcal{B}(\mathbb R))$'s some measurable subspace. Precisely, suppose $\{A_n; n \geq 1\}$ is the algebra generating $\mathcal E$ on $E$. Let $f(x) = \sum_{n = 1}^\infty 3^{-n}\chi_{A_n}(x)$, then $f$ is a isomorphism from $(E, \mathcal E)$ to $(f(E), \mathcal B(f(E)))$. Here, $\mathcal B(f(E)) = f(E) \cap \mathcal B(\mathbb R)$.
***

**Monotone class thm.'s**:

**Definition**: Let $\mathcal F$ be a $\sigma$ algebra on $\Omega$. We call $(\Omega, \mathcal F)$ a measurable space and element of $\mathcal F$ measurable set. If there is a countable sub family of $\mathcal C$ s.t. $\sigma(\mathcal C) = \mathcal F$, we call $\sigma$ algebra $\mathcal F$ is divisible. If $\mathcal F$ is divisible, we call $(\Omega, \mathcal F)$ is a divisible measurable space.

**Theorem1.2.3**: Let $\mathcal C$ be a family of sets.
(1) $m(\mathcal C) = \sigma(\mathcal C) \Leftrightarrow (A \in \mathcal C \implies A^c \in m(\mathcal C) \wedge A, B \in \mathcal C \implies A \cap B \in m(\mathcal C)$)
(2) $m(\mathcal C) = \sigma(\mathcal C) \Leftrightarrow (A \in \mathcal C \implies A^c \in m(\mathcal C) \bigwedge A,B \in \mathcal C \implies A \cup B \in m(\mathcal C))$.

**Theorem.**: If $\mathcal F$ is divisible, then $\exists$ field $\mathcal C$ which contains at most countable elements, and $\sigma(\mathcal C) = \mathcal F$.

**Proof**: Let $\overline{\mathcal C} \triangleq \mathcal{C} \cup \{\emptyset, \Omega\}$, $\mathcal G = \{ A | A = ( \bigcap_{i = 1}^n A_i) \cap (\bigcap_{i = 1}^m B_i) \text{ for some }n, m \in \mathbb N \text{ and } A_i, B_i \in \overline{\mathcal C}\}$. Then $\mathcal G$ is a semi-field. Thus $\mathcal G_{\Sigma f}$ is a field. And $\sigma(\mathcal G_{\Sigma f}) = \mathcal F$.

**Definition**: Let $(\Omega, \mathcal F)$ is a measurable space, for any $\omega \in \Omega$, let
$$
\mathcal F_\omega = \{B \in \mathcal F | \omega \in B\}, A(\omega) = \bigcap_{B \in \mathcal F_\omega} B.
$$
$A(\omega)$ is call a $\mathcal F$ atom containing $\omega$.

**Claim**:
1. Let $\omega, \omega' \in \Omega$, then either $A(\omega) = A(\omega')$ or $A(\omega) \cap A(\omega') = \varnothing$.
2. Let $\mathcal C$ be the algebra generating $\mathcal F$. Then $\forall \omega \in \Omega$, let $\mathcal C_\omega = \{B \in \mathcal C | \omega \in B\}, then
$$
A(\omega) = \bigcap_{B \in \mathcal C_\omega} B.
$$

**Proof of 2**:
For any given $\omega_0 \in \bigcap_{B \in \mathcal C_\omega} B$, let $\mathcal G \triangleq \{A | \omega \in A \implies \omega_0 \in A\}$. Then $\mathcal C \subset \mathcal G$. And $\mathcal G$ is a monotone class. Thus $\sigma(\mathcal C) \subset \mathcal G$, i.e. for any given $\omega_0 \in \bigcap_{B \in \mathcal C_\omega} B$, $C \in \mathcal F$ and $\omega \in C \implies \omega_0 \in C$. Hence $\omega_0 \in \bigcap_{B \in \mathcal F_\omega} B$. Hence $\bigcap_{B \in \mathcal C_\omega} B \subset \bigcap_{B \in \mathcal F_\omega} B$.

**Theorem**: Let $(\Omega, \mathcal F)$ be a measurable space, $f$ is a measurable function.
1. There exists a sequence of simple function $\{f_n, n \geq 1\}$, s.t. $\forall n \geq 1$, $|f_n| \leq |f|$, and $\lim_{n \rightarrow +\infty} f_n = f$.
2. If $f$ is nonnegative, then there exists a monotonely increasing sequence of nonnegative simple measurable functions $\{f_n\}$ s.t. $\lim_{n \rightarrow \infty} = f$.

**Proof**: Writing $f$ as $f^+ - f^-$, it's easy to see that 1. follows from 2.. $\forall n \geq 1$, let
$$
f_n = \sum_{k = 0}^{n2^n - 1} \frac{k}{2^n} \chi_{\{\frac{k}{2^n} \leq f < \frac{k + 1}{2 ^n}\}} + n \chi_{\{f \geq n\}}.
$$
Then $\{f_n\}$ is a sequence of nonnegative simple measurable functions s.t. $f_n \uparrow f$.

**Theorem**: Let $(\Omega, \mathcal F)$ be a measurable space, $\mathcal C$ is a algebra generating $\mathcal F$. Let $\mathcal H$ be a family of measurable function on $\Omega$. If:
1. $f, g \in \mathcal H, \alpha, \beta \geq 0 \implies \alpha f + \beta g \in \mathcal H$;
2. $f_n \in \mathcal H, n \geq 1, f_n \uparrow f$ or $f_n \downarrow f$ $\implies f \in \mathcal H$;
3. $\forall A \in \mathcal C, \chi_A \in \mathcal H$,
Then $\mathcal H$ containing all $\mathcal F$-measurable function on $\Omega$.

**Proof**:
Let $\mathcal T = \{A \in \mathcal F | \chi_A \in \mathcal H\}$, then by 3. we know that $\mathcal T \supset \mathcal C$, and by 2. we know that $\mathcal T$ is a monotone class. Thus by monotone class thm. $\mathcal F \subset \mathcal T$.
***

**Theorem**: Let $\mathcal C$ be a $\pi$-system on $\Omega$, $\mathcal H$ be a linear space consisting of some real-valued function on $\Omega$. If:
1. $1 \in \mathcal H$;
2. $f_n \in \mathcal H, n \geq 1, 0 \leq f_n \uparrow f$, and $f$ is measurable(correspondingly, real-valued or bounded) $\implies$ $f \in \mathcal H$;
3. $\forall A \in \mathcal C, \chi_A \in \mathcal H$.
Then $\mathcal H$ containing all $\sigma$-measurable (correspondingly, real-valued or bounded) funcions on $\Omega$.

**Proof**: Let $\mathcal F = \{A \subset \Omega | \chi_A \in \mathcal H\}$, then it's obvious that $\mathcal F$ is a $\lambda$-system and $\mathcal C \subset \mathcal F$. Then by monotone class thm. $\sigma(\mathcal C) \subset \mathcal F$. Suppose $f$ is $\sigma(\mathcal C)$-measurable real-valued function. Let
$$
g_n = \sum_{k = 0}^{n2^n - 1} \frac{k}{2^n} \chi_{\{\frac{k}{2^n} \leq f^+ < \frac{k + 1}{2^n}\}} + n \chi_{\{f^+ \geq n\}},
$$
Then $g_n \in \mathcal H$, $g_n \uparrow f^+$, then by 2., $f^+ \in \mathcal H$. By similar argument, $f^- \in \mathcal H$. So $f = f^+ - f^- \in \mathcal H$. Q.E.D.