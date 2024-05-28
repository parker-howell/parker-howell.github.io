---
title: 'Micro I Notes'
author: "Parker Howell"
date: 'Last Updated: 2024-05-28'
output:  
  html_document:
    keep_md: yes
    toc: true
    toc_float: true
    toc_collapsed: true
    number_sections: true
  # pdf_document:
  #       toc: true
  #       number_sections: true
---






# Preference

<!-- 1. consider $X \times X = $ -->

### Def "binary relation"
A binary relation $R$ on $X$ is a subset of $X \times X$.

The ordered pair $(x,y) \in R$ means $x$ is (weakly) preferred to $y$.

### Remark "binary relation notation"
We use $\succsim$ to denote $R$ but all these methods are the same thing:
$$(x,y)  \iff xRy \iff x \succsim y$$

<!-- ## Example -->
<!-- 1. $X$ = real line; $R$ is "=" -->
<!--   * Then $(2,2) \in$ =" but $(2,4) \notin$ "=" -->
<!-- 2. $X$ = real line; $R$ is "$\geq$" -->
<!--   * Then $(x,y) \in R \iff x \geq y$ -->

### Def "attributes of binary relations"
A binary relation $\succsim$ is

1. complete if for all $x,y\in X$ either $x \succsim y$ or $y \succsim x$
2. transitive if for all $x,y,z\in X, [x \succsim y, y \succsim z] \Rightarrow x \succsim y$
3. reflexive if for all $x \in X, x \succsim x$
4. symmetric if for all $x,y\in X, x \succsim y \iff y \succsim x$
5. irreflexive if for all $x \in X, x \not\succsim x$
6. asymmetric if for all $x,y\in X, x \succsim y \Rightarrow y \not\succsim x$
7. antisymmetric...


### Def "rational"
A binary relation $\succsim$ is *rational* if it is complete and transitive

# Choice

### Def "choice function"
A function $c: \mathcal{B} \rightarrow \mathcal{P}(X)$ is called a *choice function* if for all $A \in \mathcal{B}, c(A) \subseteq A$.

1. If $c$ is a choice function, then $c(A) \neq \emptyset, \forall A \in \mathcal{B}$ 
2. $|c(A)| \geq 1$


### Def "choice structure"
The pair $(\mathcal{B}, c)$ is called a *choice structure*.

### Def "WARP"
Weak Axiom of Revealed Preference. The following are equivalent for all $A, B \in \mathcal{B}$:

* $c(A) \cap B \neq \emptyset \Rightarrow c(B) \cap A  \subseteq c(A)$
* $[c(A) \cap B \neq \emptyset \text{ AND } c(B) \cap A \neq \emptyset] \Rightarrow [c(A) \cap B \subseteq c(B) \text{ AND } c(B) \cap A \subseteq c(A)]$
* $x, y \in A \cap B, x \in c(A), y \in c(B) \Rightarrow x \in c(B), y \in c(A)$
* Sen's $\alpha$ and $\beta$ both hold

### Def Sen's $\alpha$ and $\beta$
For all $A, B \in \mathcal{B}$:

1. Sen's $\alpha$: If $x \in B \subseteq A$ and $x \in c(A)$ then $x\in c(B)$
2. Sen's $\beta$: If $x,y \in c(B), B \subseteq A$ and $y \in c(A)$ then $x\in c(A)$

### Prop 1 "WARP $\iff \alpha$ and $\beta$"

### Term "single-valued"
We say $c$ is single-valued if $\forall A \in \mathcal{B}, |c(A)| = 1$


### Prop 2 "$\alpha$ and single-valued $\Rightarrow$ WARP"
If $(\mathcal{P}(X), c)$ satisfies $\alpha$ and $c$ is single-valued, then it satisfies WARP.


# Choice and Preference

### Def "$c_\succsim$"
For any binary relation $\succsim$ define
$$c_\succsim(A) = \{x \in A: x \succsim y, \forall y \in A\}, \forall A \in \mathcal{P}(X)$$


### Def "$\succsim_c$"
For a choice structure $(\mathcal{P}(X), c)$ define a binary relation $\succsim_c$ such that
$$x \succsim_c y \iff x \in c(\{x,y\})$$


### Prop "satisfies WARP $\iff \succsim$ rational"
If $\succsim$ is a binary relation on a finite set $X$ then $(\mathcal{P}(X), c_\succsim)$ is a choice structure that satisfies WARP if and only if $\succsim$ is rational.

### Prop "WARP $\Rightarrow c=c_\succsim$"
If $(\mathcal{P}, c)$ is a choice structure that satisfies WARP then there exists a unique rational binary relation $\succsim$ such that $c=c_\succsim$ (i.e., for all $A \in \mathcal{P}, c(A) = c_\succsim (A)$).

<!-- ### Def "$\succsim^*$ from MWG" -->

# Utility

### Def "utility function"
A function $U: X \rightarrow \mathbb{R}$ represents $\succsim$ if and only if, for all $x, y \in X$
$$x \succsim y \iff U(x) \geq U(y).$$



### Prop "$U$ represents $\succsim \Rightarrow$ rational"
If $U: X \rightarrow \mathbb{R}$ represents $\succsim$, then $\succsim$ is rational.

> Note: this proposition does NOT require finiteness!


### Prop "$X$ finite + $\succsim$ rational $\Rightarrow \exists U$
If $X$ is finite and $\succsim$ is rational then there exists $U: X \rightarrow \mathbb{R}$ that represents $\succsim$.

### Prop "$V \iff \phi$ and $\phi$ strictly increasing"
Suppose $U: X \rightarrow \mathbb{R}$ represents $\succsim$. Then $V: X \rightarrow \mathbb{R}$ represents $\succsim$ if and only if there exists $\phi: U(X) \rightarrow V(X)$ such that $V = \phi \circ U$ and $\phi$ is strictly increasing.


# Expected Utility

### Def "lottery"
Suppose $X$ is a non-empty and finite set of prizes (consequences). Then a *lottery*, $p$ is a probability distribution over $X$:
$$p: X \rightarrow [0,1], \text{ such that } \sum_{x\in X} p(x) = 1.$$

We denote $\mathcal{L}$ as the set of all lotteries.

### Term "degenerate lottery"
If $p(x)=1$ for some $x \in X$ then we write $\delta_x$.

### Remark: $\mathcal{L}$ is the set of alternatives, and unlike $X$ is infinite!

### Def "vNM expected utility function/utility index"
$U: \mathcal{L} \rightarrow \mathbb{R}$ is an expected utility function if there exists $u: X \rightarrow \mathbb{R}$ such that $U(p) = \sum_{x \in X} u(x)p(x), \forall p \in \mathcal{L}$.

Called a "von Neumann–Morgenstern utility index" or a "Bernoulli index."

### Def "Mixture operation"
For all $p, q \in \mathcal{L}, \alpha \in [0,1]$:

* let $\alpha p + (1-\alpha)q$ denote a lottery $r\in \mathcal{L}$ such that for all $x\in X, r(x) = \alpha p(x) + (1-\alpha)q(x)$.


### Def "expected utility representation"
$\succsim$ on $\mathcal{L}$ has an expected utility representation if there exists $u: X \rightarrow \mathbb{R}$ such that for $p,q \in \mathcal{L}$
$$p \succsim q \iff U(p) = \sum_{x\in X} p(x)u(x) \geq U(q) = \sum_{x\in X} q(x)u(x)$$




### Def "linear function"
A function $U: \mathcal{L} \rightarrow \mathbb{R}$ is *linear* if for all $\alpha \in [0,1]$ and $p,q \in \mathcal{L}$:
$$U(\alpha p + (1-\alpha)q) = \alpha U(p) + (1-\alpha) U(q).$$

### Lemma "linear $\iff U$ is an expected utility function"
A function $U: \mathcal{L} \rightarrow \mathbb{R}$ is *linear* if and only if $U$ is an expected utility function.
 
### Def "vNM Axioms"
The von Neumann–Morgenstern axioms are:

* A1. (Rationality): $\succsim$ is complete and transitive.
* A2. (Independence): For all $p,q,r \in \mathcal{L}, \alpha \in (0,1)$ we have $[p \succ q] \Rightarrow [\alpha p + (1-\alpha)r \succ \alpha q + (1-\alpha)r]$.
* A3. (Continuity): For all $p, q, r \in \mathcal{L}$, if $p \succ q \succ r$ then there exists $\alpha, \beta \in (0,1)$ such that $\alpha p + (1- \alpha) r \succ q$ and $q \succ \beta p + (1-\beta) r$.
* We don't use A2\* in this class, but some literature uses it:
  * A2\*. (Independence, strengthened): $[p \succsim q] \iff [\alpha p + (1-\alpha) r \succsim \alpha q + (1-\alpha)r]$

### Lemma "applying vNM Axioms"
Suppose $\succsim$ satisfies A1, A2, and A3 of vNM axioms.

(i) $\forall \alpha \in (0,1), p,q \in \mathcal{L}$:
    (a) $p \succ q \Rightarrow p \succ \alpha p + (1 - \alpha) q \succ q$
    (b) $p \sim q \Rightarrow p \sim \alpha p + (1 - \alpha) q \sim q$
(ii) $p \succ q, 1 \geq \alpha > \beta \geq 0 \Rightarrow \alpha p + (1-\alpha)q \succ \beta p + (1-\beta)q$
(iii) $p \sim q, \alpha \in (0,1) \Rightarrow \alpha p + (1-\alpha)r \sim \alpha q + (1-\alpha)r$
(iv) $p \succsim q, r \succsim s, \alpha \in (0,1) \Rightarrow \alpha p + (1-\alpha)r \succsim \alpha q + (1-\alpha)s$


### Thm "A1-A3 $\iff$ EU representation"
Suppose $X$ is finite and $\succsim$ is a binary relation on $\mathcal{L}$. Then
$$[\succsim \text{ satisfies A1, A2, and A3 }] \iff \succsim \text{ has an Expected Utility representation.}$$

### Thm "$V$ linear representation $\iff V(p) = aU(p)+b$"
Suppose $U$ is a linear representation of $\succsim$, and $V: \mathcal{L}\rightarrow \mathbb{R}$ is a linear function. Then 
$$[V \text{ is a linear representation of } \succsim] \iff [\exists a>0, b\in\mathbb{R} \text{ such that } V(p)=aU(p) + b, \forall p \in \mathcal{L}]$$

#### Term "affine"
Basically a line, but the intercept doesn't have to be zero. "A function composed of a linear function and a constant and its graph is a straight line."

### Def "simple lottery"
$p: X \rightarrow \mathbb{R}$ is a *simple lottery* if

1. $\{x\in X: p(x)>0\}$ is finite
2. $\displaystyle \sum_{\{x\in X: p(x)>0\}} p(x) = 1$

### Def "simple improvement"
For all (simple) lotteries $p,q \in \mathcal{L}$, $p$ is a simple improvement of $q$ if there exists $\lambda \in (0,1), m, m' \in X, m>m';, r \in \mathcal{L}$ such that
$$p = \lambda \delta_m + (1-\lambda)r \text{ and } q = \lambda \delta_m' + (1-\lambda)r.$$

### Def "FOSD"
For $p, q \in \mathcal{L}$, $p$ first-order stochastically dominates (FOSD) $q$ if

1. $p \neq q$, and
2. $F_p(x) \leq F_q(x), \forall x \in X$

> caution: CDF of $p$ SMALLER than CDF of $q$ means $p$ dominates $q$, not the other way around

### Fact "$p$ FOSD $q \iff p$ is a complex improvement of $q$"


### Thm "EU representation means $p$ FOSD $q \Rightarrow p \succ q$ and $u$ strictly increasing"
Suppose $\succsim$ has an expected utility representation. Then the following are equivalent:

1. $p$ FOSD $q \Rightarrow p \succ q$
2. $p$ is a simple improvement of $q \Rightarrow p \succ q$
3. Every EU representation of $\succsim$ has a strictly increasing utility index ($U(p) = \sum_{x \in supp(p)} \underline{u(x)}p(x)$)


### Def "Betweenness Axiom"
$$\forall p,q \in \mathcal{L}, \lambda \in (0,1):$$
$$p \sim q \Rightarrow \lambda p + (1-\lambda)q \sim p$$

### Def "Allais paradox"
Individuals prefer certainty over a risky outcome even if this defies the expected utility axiom


## Risk Attitudes

### Lemma
Suppose $\succsim$ has an expected utility representation with a strictly increasing and continuous index $u$. Then $\forall p \in \mathcal{L}, \exists$ unique $CE(p)\in X$ such that $p \sim \delta_{CE(p)}$. In this case, $CE(p)$ is the *certainty equivalent* of $p$.
$$CE(p) = u^{-1}(U(p)) = u^{-1}(\sum_{x\in supp(p)}u(x)p(x))\in X \iff u(CE(p))=U(p)$$


### Def "risk attitudes"
Let $\bar{p} = \sum_{x \in supp(p)} p(x)x$ be the expected value of $p$. Then $p$ is riskier than $\delta_{\bar{p}}$. For all $p \in \mathcal{L}$, $\succsim$ is

1. *risk averse* if $\delta_{\bar{p}} \succsim p$
2. *risk neutral* if $\delta_{\bar{p}} \sim p$
3. *risk seeking* if $p \succsim \delta_{\bar{p}}$


### Def "simple Mean-Preserving Spread (MPS)"
Say $\hat{p} = \lambda p + (1-\lambda)r$ is a simple mean-preserving spread of $\hat{q} = \lambda \delta_{\bar{p}} + (1-\lambda)r$. $\hat{p}$ is riskier than $\hat{q}$.

### Thm "risk-averse $\iff u$ concave $\iff$ MPS"
$\succsim$ has an EU representation such that its utility index, $u$, is strictly increasing and continuous. Then the following are equivalent:

1. $\succsim$ is risk-averse / <span style='color: red;'>-seeking</span> / <span style='color: green;'>-neutral</span>
2. $[p$ is a simple MPS of $q] \Rightarrow q \succsim p$
3. $u$ is concave / <span style='color: red;'>convex</span> / <span style='color: green;'>affine</span>

### Def "more risk averse"
$\succsim_1$ is more risk averse than $\succsim_2$ if for all $m\in X, p \in \mathcal{L}$ we have
$$\delta_m \succsim_2 p \Rightarrow \delta_m \succsim_1 p.$$


#### Term "Absolute risk aversion"
Call $-\frac{u_1''}{u_2'}$ Arrow-Pratt's measure of absolute risk aversion (ARA).


### Thm "more risk averse $\iff$ concave composition"
$\succsim_1, \succsim_2$ have an EU representation with $u_1, u_2$ strictly increasing and smooth. Then the following are equivalent:

1. $\succsim_1$ is (always) more risk averse than $\succsim_2$.
2. there exists a concave and strictly increasing function $f: u_2(X) \rightarrow u_1(X)$ such that $u_1 = f \circ u_2 = f(u_2(x)), \forall x \in X$
3. $ARA_{u_1} \geq ARA_{u_2}$


#### Term "smooth"
Twice continuously differentiable


### Def "CARA"
$$ARA = -\frac{u''(x)}{u'(x)} = a (\text{const} \in \mathbb{R})$$
Constant Absolute Risk Aversion (CARA) means risk attitude does not depend on the initial wealth level. 

### Def "functional form for CARA"
$$u(x) = \begin{cases} \frac{1-e^{-ax}}{a} \text{ if } a \neq 0 \\ x \text{ if } a=0\end{cases}$$

* $a>0 \Rightarrow$ risk-averse
* $a=0 \Rightarrow$ risk-neutral
* $a<0 \Rightarrow$ risk-seeking

> Can compare the "a-level" of individuals to see who is more risk averse (e.g., $a_1 > a_2 \Rightarrow$ person 1 more risk-averse)


### Def "CRRA"
$$RRA = -x\frac{u''(x)}{u'(x)} = \text{const} = r$$

Constant Absolute?? CHECK Risk Aversion (CARA) means risk attitude does not depend on inflation.
$$u(x) = \begin{cases} \frac{x^{1-r}}{1-r} \text{ if } r \neq 1 \\ \ln x \text{ if } r=1\end{cases}$$


> person is risk-neutral when $u(x) = x$.


# Demand Theory

### Def "Well-behaved" preference

1. Monotone
$$[x_i \geq y_i, \forall i]\Rightarrow[x \succsim y]$$
2. Strongly Monotone 
$$[x_i \geq y_i, \forall i \text{ and } x\neq y]\Rightarrow[x \succ y]$$
3. MWG Monotone
$$[x_i > y_i, \forall i]\Rightarrow[x \succ y]$$
4. Locally non-satiated
$$\forall x \in X, \forall \varepsilon > 0, \exists y \in B_\varepsilon(x) \text{ such that } y \succ x$$
5. Continuity
$x^{(m)} \rightarrow x$ and $y^{(m)} \rightarrow y, \forall m \geq 1$ and $x^{(m)} \succsim y^{(m)} \Rightarrow x \succsim y$ 


> 2 $\Rightarrow$ 3 $\Rightarrow$ 4 (but 3 alone does not imply 4)


### Def "convex relation"
For all $x, y \in X$ and for all $\alpha \in (0,1)$:

* $\succsim$ is *convex* if 
$$x \succsim y \Rightarrow \alpha x + (1-\alpha)y \succsim y$$

* $\succsim$ is *strictly convex* if 
$$x \succsim y, x \neq y \Rightarrow \alpha x + (1-\alpha)y \succ y$$


![](src/strict convex relation.jpg)


### Claim "$\succsim$ is rational $\not\Rightarrow \succsim$ has a utility representation"

### Term "lexicographic preferences"
1. $\succsim$ is rational
2. $\succsim$ is not continuous
3. $\succsim$ does not have a utility representation

### Def "economic preference / well-behaved preference"
A binary relation $\succsim$ is an *economic preference* (well-behaved preference) if it is 
1. rational, 
2. continuous, 
3. monotone, and 
4. locally non-satiated.

### Thm "economic preference $\Rightarrow$ represented by continuous $U$"
$\succsim$ is an economic preference $\Rightarrow \succsim$ can be represented by a continuous utility function $U$.

### Remark $U$ is also monotone and MWG monotone, but not strong


# Demand

#### Term "price vector"
$P \in \mathbb{R}^n_{++}$. $p \in P: p = (p_1, ..., p_n), p_i > 0 \forall i$

#### Term "Budget constraint"
$$B(p, m) = \{\vec{x} \in X: p \cdot \vec{x} = \sum^n_{i=1} p_i \cdot x_i \leq m\}, \forall p \in P, m \geq 0.$$
$B(p, m)$ is compact, non-empty (and convex, but that isn't important for now.)

### Thm "economic preference $\Rightarrow$ solution exists"
If $\succsim$ is an economic preference then $\forall p, m\geq 0, \exists x^* \in B(p,m)$ such that

1. $x^* \succsim y, \forall y \in B(p,m)$ and
2. $p \cdot x^* = m$.

### Def "demand"
<!-- set of menus subject to constraint -->
$$D: \mathcal{B} \rightarrow \mathcal{P}(X) \text{ such that } D(B(p,m)) = \{x^*\in B(p,m): x^* \succsim y \forall y \in B(p,m)\}$$

Where $\mathcal{B} = \{B(p,m): p \in P, m\geq 0\} \subsetneq \mathcal{P}(X).$ We can verify that $(\mathcal{B}, D)$ is a choice structure.

### Def "demand function"
If $D(B(p,m))$ is always a singleton we can define:
$$x: P \times \mathbb{R}_+ \rightarrow X$$
such that $x(p,m)$ is the only element of $D(B(p,m))$. We call $x(\cdot)$ the demand function.

### Thm "strictly convex $\Rightarrow$ demand fn well-defined"
If $\succsim$ is a strictly convex economic preference then $x(\cdot)$ is a well-defined and continuous function.

### Def "indirect utility function"
$V: P\times \mathbb{R}_+ \rightarrow \mathbb{R}$ such that $V(p,m) = U(x(p,m))$.


### Def "neoclassical utility function"
$U: X \rightarrow \mathbb{R}$ is a *neoclassical utility function* if $U$

1. is continuous, and
2. represents a strictly convex economic preference.

### Thm "neoclassical $U \Rightarrow$ properties of $V$"
Suppose $U$ is neoclassical and $V$ is the associated indirect utility function. Then,

1. $V$ is continuous,
2. $V$ is strictly increasing in $m$,
3. $V$ is quasiconvex ($V(p,m) \geq V(p',m') \Rightarrow V(p,m) \geq V(\alpha p + (1-\alpha)p', \alpha m + (1-\alpha)m'$), and
4. $V$ is homogeneous of degree 0 ($V(p,m) = V(\lambda p, \lambda m)$)


## Hicksian Demand

### Thm "neoclassical $\Rightarrow$ unique minimization solution"
Suppose $U$ is neoclassical. Then for all $p\in P, u\in U(X), \exists$ unique $x^*\in X$ such that

1. $U(x^*) = u$ and
2. $\forall x \in X, x \neq x^*: U(x) \geq u \Rightarrow p\cdot x > p \cdot x^*$

### Def "Hicksian demand function
Let $x^h(p,u)$ denote $x^* \forall p \in P, u \in U(X)$. Then $x^h: P \times U(X) \rightarrow X$ is called the *Hicksian demand function*.


### Def "expenditure function"
Define the *expenditure function*, $e: P \times U(X) \rightarrow X$ such that $\forall p \in P, u \in U(X):$
$$e(p,u)= p \cdot x^h(p,u).$$

### Thm "duality theorem"
Suppose $U$ is neoclassical. Then

1. $e(p, V(p,m)) = m$
2. $V(p,e(p,u)) = u$
3. $x(p,e(p,u)) = x^h(p,u)$
4. $x^h(p, V(p,m)) = x(p,m)$.


Three important results:

### Thm "relating $e(\cdot)$ and $x^h(\cdot)$"
Suppose $U$ is neoclassical. Then

1. $e(\cdot)$ is continuous,
2. $e(\cdot)$ is strictly increasing in $u$ and non-decreasing in $p_i$,
3. $e(\cdot)$ is concave in $p$ for fixed $u \in U(X)$,
4. $e(\lambda p, u) = \lambda e(p,u), \forall \lambda>0$, and
5. $\frac{\partial}{\partial p_i} e(p,u) = x^h_i(p,u), \forall i = 1, ..., n.$


### Thm "relating $x(\cdot)$ and $V(\cdot)$ (Roy's identity)"
Suppose $U$ is neoclassical, $V(p,m)$ is differentiable at $(p,m)$ and $x(p,m)$, is in the interior of $X$. Then
$$x_i(p,m) = -\frac{\frac{\partial }{\partial p_i}V(p,m)}{\frac{\partial }{\partial m}V(p,m)}$$


### Lemma "Shephard's Lemma"
Use this to go from expenditure function ($e(\cdot)$) to Hicksian demand ($x^h$):

$$x^h_i(\mathbf{p},u) = \frac{\partial e(\mathbf{p}, u)}{\partial p_i}$$
This is the counterpart to Roy's identity, just on the Hickisan side (and simpler).


### Thm "relating $x(\cdot)$ and $x^h(\cdot)$ (Slutsky equation)"
Suppose $U$ is neoclassical, $x(\cdot)$ is continuously differentiable, and $x(p,m)$ is in the interior of $X$. Then
$$\frac{\partial x_i^h}{\partial p_k} (p, V(p,m)) = \underbrace{\frac{\partial x_i}{\partial p_k} (p, m)}_{\text{substitution effect}} + \underbrace{\frac{\partial x_i}{\partial m} (p, m) x_k(p,m)}_{\text{income effect}}, \forall i, k \in \{1, ... ,n\}$$
