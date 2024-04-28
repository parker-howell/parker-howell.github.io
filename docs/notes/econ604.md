---
title: 'Econ 604 Notes'
author: 'Parker Howell'
date: 'Last Updated: 2024-04-23'
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, encoding = encoding, output_dir = "../../website/parker-howell.github.io/docs/notes")})
output:  
  html_document:
    keep_md: yes
    toc: true
    toc_float: true
    toc_collapsed: true
    number_sections: true
  # pdf_document: default
---

<!-- header-includes: -->
<!--   - \usepackage{mathrsfs} -->




# Noncooperative Bargaining

### Model "Divide a dollar"
* Two players simultaneously submit demands $d_i \in [0,1]$
* Continuum of Nash equilibria--this will lead us to look at SPE instead.

### Model "Ultimatum Game"
* "sequential" but only one round (P1 makes TIOLI offer to P2 who accepts or rejects)
* **Prop:** has a **unique** SPE in which P1 offers (1,0) and P2 accepts any offer.
* multiple NE in the subgame following the offer, but P1 only has a BR if P2 accepts (1,0). 


### Model "Finite Alternating-Offer Bargaining"
Regularities:

1. Immediate agreement, efficient outcome
2. Proposer's offer makes responder indifferent
3. Unique SPE
4. Division of surplus depends:
    1. $x_1^*(T, \delta) = \sum_{t=1}^T (-\delta)^{t-1}= \frac{1-(-\delta)^T}{1+\delta}$
    2. $\delta \rightarrow 1 \Rightarrow$ last mover takes all
    3. $T\rightarrow\infty \Rightarrow X^* \rightarrow \frac{1}{1+\delta}$
    4. $T\rightarrow\infty$ then $\delta \rightarrow 1\Rightarrow$ equal sharing


> Every game in this class has a unique subgame perfect equilibrium, and in it there is immediate agreement in the first round.

> The proposer in round T offers to take everything, and the responder accepts every offer

### Thm "infinite alternating-offer bargaining game outcome"
The infinite horizon alternating-offer bargaining game with discount factor $\delta < 1$ has a unique subgame perfect equilibrium, in which Player 1 offers the payoff vector $(\frac{1}{1+\delta}, \frac{\delta}{1+\delta})$ in the first round and Player 2 accepts.

# Repeated Games

## Finitely Repeated Games

<!-- Examples: -->

<!-- * Prisoner's dilemma twice -->
<!-- * Augmented prisoner's dilemma twice -->

### Model "Repeated Games"

* Stage Game $\langle N, A, \pi \rangle$ (Normal form game) 
* Players $N = \{1, ..., N\}$
* Action profiles $A = A_1 \times \cdot \cdot \cdot A_n$
* Stage payoffs $\pi: A \rightarrow \mathbb{R}^n$ (uniformly bounded) (i.e., $\pi_i(a)$ is $i$'s payoff from action profile $a$)
* Periods $t = 1, ..., T$, where $T < \infty$
* Discount factor $\delta > 0 (\delta < 1 \text{ if } T = \infty)$

### "Histories and Strategies"
A strategy (in a repeated game) maps from the history of past play into an action for the current period.


* History $h^t \equiv (a^1, ..., a^{t-1})$, $h^1 \equiv \varnothing$
* Possible $t$-histories $\mathcal{H}^t \equiv A^{t-1}$
* Possible histories $\mathcal{H} \equiv \cup_{t=1}^T\mathcal{H}^t$
* A (pure) strategy is a function $s_i: \mathcal{H} \rightarrow A_i$
* a correlated (behavioral) mixed strategy is defined in terms of strategy profiles to allow for correlation. So $\sigma: \mathcal{H} \rightarrow \Delta A$.


> a behavioral mixed-strategy must specify not only what players play "sequentially", but also in all other possible histories of the game.

<!-- Write, $\alpha \in \Delta A$ for a (possibly correlated) mixed action profile. -->

<!-- $$\pi(\alpha) = \mathbb{E}[\pi(a)|\alpha]$$ -->


### Def "Utility"
$$\text{Total Utility} = \tilde{u}_i(\sigma) \equiv \sum_{t=1}^T \delta^{t-1} \sum_{h^t \in \mathcal{H}^t} \pi_i(\sigma(h^t))Pr(h^t|\sigma)$$

$$\text{Average Utility} = u_i(\sigma) \equiv \frac{1-\delta}{1-\delta^T}\sum_{t=1}^T \delta^{t-1} \sum_{h^t \in \mathcal{H}^t} \pi_i(\sigma(h^t))Pr(h^t|\sigma)$$

> For infinite horizon we multiply by $1-\delta$, which is just the limit as $T \rightarrow \infty$ of $\frac{1-\delta}{1-\delta^T}$.


## Infinitely Repeated Games

### Def "Non-contingent strategy profile"
$\sigma$ is a non-contingent strategy profile if 
$$\sigma(h^t) = \sigma(\hat{h}^{t}),  \forall h^t, \hat{h}^{t} \in \mathcal{H}^t, \forall t = 1, ..., T.$$

> $\sigma$ is non-contingent if it specifies that in each period players should play some period-specific mixed action profile regardless of the history.

### Prop 13.1 "Non-contingent equilibria"
Suppose $T<\infty$. If $\sigma$ is a non-contingent strategy profile such that $\sigma(h^t)$ is a stage game NE for all $t = 1, ..., T$ then $\sigma$ is a SPE.

> Any sequence of stage Nash profiles can be supported as the outcome of a SPE. (Watson)


### Prop 13.2 "Unique Stage Game Equilibrium"
Suppose $T<\infty$. If $\alpha^*$ is the unique NE in the stage game, then the unique SPE in the repeated game is a non-contingent strategy profile $\sigma^*$ such that, for all $h \in \mathcal{H}, \sigma^*(h) = \alpha^*$.

### Def "profitable one-shot deviation"
A *profitable one-shot deviation* from $\sigma$ is a strategy $\hat{\sigma}_i \neq \sigma_i$ for some player $i$ such that:

1. there exists a unique history $\hat{h}^{t} \in \mathcal{H}$ such that $\hat{\sigma}_{i} (h) = \sigma_i(h), \forall h \neq \hat{h}$ and
2. $\tilde{u}_i(\hat{\sigma}_i|_{\hat{h}},\sigma_{-i}|_{\hat{h}}) > \tilde{u}_i(\sigma_i|_{\hat{h}})$.

### Thm "one-shot deviation principle"
In a finitely or infinitely repeated game, a strategy profile is a SPE if and only if it has no profitable one-shot deviations.


### Model "Infinite Cournot Duopoly"
* Two firms simultaneously choose *quantities* in each period
* Demand curve (e.g., $P = 12 - Q$)
* Zero costs
* $\delta < 1$

Proposal: 

* on path: produce 1/2 monopoly quantity each
* off path: produce Cournot quantity (i.e., stage game NE)

Q. For what value of $\delta$ is this proposal a SPE?


### Model "Infinite Bertrand Duopoly"
* Two firms simultaneously choose *prices* in each period
* Unit mass of consumers demand 1 unit at any price $\leq 1$
* lowest price gets the market; ties split
* Zero costs
* $\delta < 1$

Proposal:

* on-path: set price = 1 (note: this means market is split)
* off-path: set price = 0

Q. For what value of $\delta$ is this proposal a SPE?


## The Folk Theorem

### Thm "Nash-Threat Folk Theorem"
If $v$ is feasible and Nash-individually rational, then there exists $\underline{\delta}<1$ such that, for all $\delta \in (\underline{\delta}, 1)$, $v$ is the average utility profile of an SPE given $\delta$.

### Def "feasible"
A payoff vector $v \in \mathbb{R}^n$ is *feasible* if $v$ is in the convex hull of $\{\pi(a): a \in A\}$

### Def "Nash-individually rational"
A payoff vector $v \in \mathbb{R}^n$ is *Nash-individually rational* if 
$$v_i > \underline{v}_i^{Nash} \equiv \min_{\alpha \in \Delta A \text{ is Nash}} \pi_i(\alpha), \forall i.$$

#### Result
Nash-individually rational in pure strategies $\subseteq$ Nash-individually rational in mixed strategies.


### Def "Minimax-individually rational"
A payoff vector $v \in \mathbb{R}^n$ is *individually rational* if 
$$v_i > \underline{v}_{~i}^{min} \equiv \min_{\alpha_{-i} \in \Delta A_{-i}} \max_{a_i \in A_i} \pi_i(a_i, \alpha_{-i} ), \forall i.$$

#### Remark
$\underline{v}_i^{min} \leq \underline{v}_i^{Nash},  \forall i$


### Thm "Minimax Folk Theorem"
If $v$ is in the interior of the set of feasible and individually rational payoffs, then there exists $\underline{\delta} < 1$ such that, for all $\delta \in (\underline{\delta}, 1)$, $v$ is the average utility profile of an SPE given $\delta$.


# Bayesian Nash Equilibrium

## Bayesian Games

### Def "Bayesian Game"
A Bayesian game is a tuple $\langle N, A, u, \Theta, \mu  \rangle$ where

* each player $i$ privately observes some signal $\theta_i \in \Theta$
* Nature draws a type vector $\theta = (\theta_1, ..., \theta_n) \in \Theta$ from a common prior measure $\mu$ on $\Theta$
* $u_i: A \times \Theta \rightarrow \mathbb{R}$

A strategy for player $i$ is a measurable function mapping from $\Theta_i$ to $\Delta A_i$. $S_i$ is the space of such functions.

### Def "Bayesian Normal Form"
$\langle N, S, \mathbb{E}[u] \rangle$ where $\mathbb{E}[u_i(s)] \equiv \mathbb{E}[u_i(s(\theta),\theta)]$ is player $i$'s expected payoff given strategy profile $s$ and the common prior $\mu$.


### Def "Bayesian Nash Equilibrium"
In a Bayesian game, $\langle N, A, u, \Theta, \mu  \rangle$, a *Bayesian Nash Equilibrium* is a strategy profile $s \in S = \times^n_{i=1} S_i$ such that for each $i$ and each $s_i' \in S_i$,
$$\mathbb{E}[u_i(s(\theta), \theta)] \geq \mathbb{E}[u_i(s_i'(\theta_i), s_{-i}(\theta_{-i}), \theta)].$$

### Observation
A BNE is a NE in the game $\langle N, S, \mathbb{E}[u]  \rangle$.


### Thm "Bayesian Nash Equilibrium if"
In a Bayesian game, $\langle N, A, u, \Theta, \mu  \rangle$, a strategy profile $s \in S = \times^n_{i=1} S_i$ is a *Bayesian Nash Equilibrium* if
$$\mathbb{E}[u_i(s(\theta), \theta | \theta_i)] \geq \mathbb{E}[u_i(a_i, s_{-i}(\theta_{-i}) | \theta_i)], \forall a_i \in A_i, \theta_i \in \Theta_i, i \in N.$$

#### Remark
This is also "only if" if $\Theta$ is finite and $\mu$ has full support.


## Applications

### Model "Cournot Duopoly with higher order beliefs"
* 2 firms simultaneously choose quantities facing a demand curve
* Firm 1 has zero costs
* Firm 2 is 
    * type $\theta_2 = L$ (i.e., has low costs) with probability $1-\alpha$
    * type $\theta_2 = H$ (i.e., has high costs) with probability $\alpha$
* Firm 1's belief about Firm 2's costs:
    * Type $\theta_1 = l$ (i.e., believes $\alpha_l = 1/4$) with probability $1- \beta$
    * Type $\theta_1 = h$ (i.e., believes $\alpha_h = 3/4$) with probability $\beta$


### Model "Lemons"
* Seller privately knows his good has quality $\theta \in [0,1]$
* Buyer believes $\theta \sim U[0,1]$
* Seller chooses price $p \in [0,1]$
* Buyer chooses set $E \subseteq [0,1]$ of prices she will accept

Analysis:

1. $E^* = \emptyset \Rightarrow$ continuum of no-trade equilibria
2. $E^* \neq \emptyset \Rightarrow E^*$ contains its maximum, $e^*$
3. Seller BR to $e^*$: $BR_s(e^*|\theta) = \begin{cases} e^* \text{ if } \theta < \frac{e^*}{q} \\  (e^*,1] \text{ if } \theta > \frac{e^*}{q} \end{cases}$.
4. $E^* \neq \emptyset \Rightarrow e^* = 0$
5. $E^* = \{0\} \Rightarrow$ continuum of almost-no-trade equilibria


#### Term: "Adverse selection"
Occurs when asymmetric information leads to undesirable outcomes in transactions.


## Auctions

### Primitives
* $n$ bidders (one prize)
* Bidder $i$'s type: $\theta_i \in \Theta_i$
* Each bidder simultaneously submits $b_i \in [0,\infty]$
* Payoff: $u_i(b, \theta) = x_i(b) v_i(\theta) - p_i(b)$
    * $x_i(b)$ is the probability $i$ gets the prize
    * $v_i(b)$ is $i$ valuation of the prize
    * $p_i(b)$ is the price $i$ pays

#### Model "Second-price *Private* Values"
* Private values: $\Theta_i = [0, \bar\theta]$ and $v_i(\theta) = \theta_i$
* **Thm:** It is a weakly dominant strategy for each player to bid $b_i(\theta_i) = \theta_i$, regardless of the distribution over $\Theta$.


#### Model "First-price *Private* Values"
* (Confirmed) Guess: symmetric strictly increasing bid strategy, $s: \Theta_i \rightarrow [0,\infty)$.

#### Model "Second-price *Common* Values"
* **Claim:** Everyone bidding their true expected values is not an equilibrium (suppose not: bid lower, now you (1) lose if you were close, or (2) profitable deviation??) 
* **Claim:** Symmetric equilibrium in which each player bids his expected value conditional on $\theta_i$ and $\max_{j\neq i}\theta_j = \theta_i$. (Winner's curse!)

# Perfect Bayesian Equilibrium

## Perfect Bayesian Equilibrium

> "PBE $\subseteq$ NE" -Selcuk

### Def "Assessment"
An *assessment* is a pair $(\beta, \mu)$, where

1. $\beta$ is an independent behavior strategy profile
2. $\mu$ is a belief system

#### Term "belief system"
For each information set, $I$, $\mu(\cdot | I)$ is a measure over nodes in $I$.

#### Term "feasible paths ($H$), aka complete histories"
Histories that reach terminal nodes are called *feasible paths* or sometimes *complete histories*. $H$ is the set of all feasible paths.

* $\phi_\beta(H)$ is the probability of a set of feasible paths, $H$.
* $\phi_\beta(H_x | H_I)$ is the conditional probability that node $x$ is reached given that information set $I$ is reached. ($H_x \subseteq H_I$)

### Def "Weak perfect Bayesian Equilibrium (wPBE)"
An assessment $(\beta, \mu)$ is a *weak perfect Bayesian equilibrium* (wPBE) if at each information set, $I$, the following are satisfied:

1. Bayesian updating:

If $\underbrace{\phi_\beta (H_I) > 0}_{\text{i.e., on eqm path}}$, then $\mu(x|I) = \phi_\beta (H_x | H_I)$ for each node $x \in I$

2. Sequential rationality:

$$\beta_i(\cdot | H_i) \in arg\max_{\beta_i} \int_{x\in I} \int_{h \in H_x} u_i(h) d \phi_{\hat{\beta}_i, \beta_{-i}}(h|H_x)d\mu(x|I).$$

## Applications

### Relevant Models:

Gift Game, Simple Signaling, Simple Reputation (aka centipede or grab game)


## Limitations of PBE

### Def "Perfect Bayesian Equilibrium" (informal)
$$PBE = wPBE \cap SPE$$

I.e., PBE requires wPBE in every subgame.

> PBE $\not \Rightarrow$ correct beliefs

> PBE $\not \Rightarrow$ strategic independence


### Def "Consistent Assessments"
In a countable game, an assessment $(\beta, \mu)$ is *consistent* if there exists a sequence of assessments $\{(\beta^k, \mu^k)\}$ such that

1. each behavior strategy $\beta^k$ assigns strictly positive probability to every action at every information set,
2. each $\mu^k$ is derived from $\phi_{\beta^k}$ according to Bayes' rule, and 
3. $(\beta^k, \mu^k)$ converges uniformly to $(\beta, \mu)$.


### Def "Sequential Equilibrium"
In a countable game, an assessment is a *sequential equilibrium* if it is sequentially rational and consistent.

> Aka "perfect extended-Bayesian equilbrium", right?????????? or are these separate concepts?

# Mechanism Design

### Quasilinear Environment
* $N = \{1, ..., n\}$ agents
* A space $\mathcal{X}$ of alternatives/outcomes
* A space $\Theta_i$ of private info (i.e., types) for each agent
    * Type space $\Theta = \Theta_i \times \cdot \cdot \cdot \times \Theta_n$
    * Common prior $\phi$ on $\Theta$
* Agent utility $u_i(\chi, \theta, \tau) = v_i(\chi, \theta) + \tau_i$
    * $v$ is how $i$ values the chosen outcome $\chi$ given $\theta$
    * $\tau \in \mathbb{R}^n$ is a vector of monetary transfers



### Regularities
We construct a mechanism $\langle M, x, t \rangle$ that defines a game for the agents in which:

* Agents simultaneously report messages: $m = (m_1, ..., m_n) \in M = M_1 \times \cdot \cdot \cdot \times M_n$
* Outcome function $x: M \rightarrow \mathcal{X}$ selects an alternative, $\chi$ from $\mathcal{X}$, given $m$.
* Each agent $i$ receives transfer $t_i(m)$.


### Mechanism Design Problem
A mechanism design problem is the problem of choosing $x$ and $t$, subject to some constraints, to maximize some objective function. 

In the **principal-agent interpretation**, the objective function is (typically) either

* social welfare $\sum_i v_i(x(m(\theta)), \theta)$ or
* revenue $-\sum_i t_i(m(\theta))$


In the **repeated games interpretation**, the objective function is typically

* a weighted sum of the players' utilities, $\sum_i \lambda_i(x(m(\theta)), \theta) + t_i(m(\theta))$ for some vector of weights $\lambda \in \mathbb{R}^n$.


**principal-agent interpretation**

utility transfer: money

**repeated games interpretation**

utility transfer: changes in continuation utility

### Constraints
1. Incentive compatibility IC (=equilibrium concept)
    * Interim IC (aka Bayesian IC)  (weakest)
        * requires that the messages constitute a BNE, where each agent sends a message that maximizes her expected utility conditioning on her own info.
    * Ex post IC (EPIC)
        * requires that the messages constitute and ex post equilibrium, where each agent's message must max her ex post utility for all possible realizations of the other agents' private info (where each other agent sends his eqm message).
    * Dominant strategy IC (DSIC) (strongest)
        * requires each agent's message is a (weakly) dominant strategy - that is, each agent's message must maximize her ex post utility for all possible messages they could send. 
2. Individual Rationality (IR)
    * Ex ante IR (opt in: *before* learn type; *before* receive messages)
    * Interim IR (opt in: *after* learn type; *before* receive messages)
    * Ex post IR (opt in: *after* learn type; *after* receive messages)
3. Budget Balance
    * Ex ante BB - requires that the principal pays the agents zero in expectation, though he may pay them a positive or negative amount for different realizations (balances to 0)
        * $E[\sum_i t_i] = 0$ - CHECK
    * (Ex post) No subsidy (no matter type vec, all transfers must sum to 0)
        * $\sum_i t_i \leq 0$
    * Ex post BB - principal cannot pay a nonzero amount for any realization of their private info (but agents may pay each other)
        * $\sum_i t_i = 0$

> In principal-agent interpretation: often interested in a principal with NO BB constraint

> In repeated-games interpretation: prefer no-subsidy constraint (this allows agents to burn money but not bring money from outside the game)


### Def "Interim/Bayesian IC" (aka BNE of the Mechanism)
The strategy profile, $m^*$ is a Bayesian Nash equilibrium of the mechanism $\langle M, x, t \rangle$ if
$$E[v_i(x(m^*(\theta)), \theta) + t_i(m^*(\theta)) | \theta_i] \geq E[v_i(x(m_i, m_{-1}^*(\theta_{-i})), \theta) + t_i(m_i, m_{-i}^*(\theta_{-i})) | \theta_i], \forall m_i \in M_i, \forall \theta_i \in \Theta_i, \forall i.$$

The mechanism $\langle M, x, t \rangle$ *implements* the outcome rule $\hat{x}: \Theta \rightarrow \chi$ *in Bayesian Nash equilibrium* if there is a Bayesian Nash equilibrium $m^*$ of $\langle M, x, t \rangle$ with $x(m^*(\theta)) = \hat{x}(\theta)$ for all $\theta$.

> Such a mechanism is interim incentive compatible (IIC) (aka Bayesian Incentive compatible) 

### Def "Ex post Incentive Compatible (EPIC)"
Strategy profile $m^*$ is an *ex post equilibrium* of $\langle M, x, t \rangle$ if
$$v_i(x(m^*(\theta)), \theta) + t_i(m^*(\theta)) \geq v_i(x(m_i, m_{-i}^*(\theta)), \theta) + t_i(m_i, m_{-i}^*(\theta)), \forall m_i \in M_i, \forall \theta \in \Theta, \forall i.$$
The mechanism $\langle M, x, t \rangle$ *implements* the outcome rule $\hat{x}: \Theta \rightarrow \mathcal{X}$ *in ex post equilibrium* if there is an ex post equilibrium $m^*$ of $\langle M, x, t \rangle$ with $x(m^*(\theta)) = \hat{x}(\theta)$ for all $\theta$.

Such a mechanism is **ex post incentive compatible (EPIC)**.

### Def "Dominant strategy incentive compatible (DSIC)"
Strategy profile $m^*$ is a dominant strategy equilibrium of $\langle M, x, t\rangle$ if
$$v_i(x(m_i^*(\theta_i), m_{-i}), \theta) + t_i(m^*_i(\theta_i), m_{-i}) \geq v_i(x(m)), \theta) + t_i(m)$$
for all $m \in M$ and all $\theta \in \Theta$, and all $i$.

The mechanism $\langle M, x, t \rangle$ implements the outcome rule $\hat{x}:\Theta \rightarrow \mathcal{X}$ in dominant strategy equilibrium if there is a dominant strategy equilibrium $m^*$ of $\langle M, x, t \rangle$ with $x(m^*(\theta)) = \hat{x}(\theta)$ for all $\theta$. 

Such a mechanism is dominant strategy incentive compatible (DSIC).

### Def "Private Values"
$$v_i(\chi, \theta) = v_i(\chi, \theta_i, \theta_{−i}'), ~~~ \forall \theta_{−i}', \forall \theta, \forall i$$


### Remark "DSIC vs EPIC"
* Private values  $\Rightarrow$ DSIC = EPIC
* Interdependent values $\Rightarrow$ DSIC too strong to do anything

### Remark "EPIC vs. BIC/IIC"
IIC:

* Relies on details of $\phi$
* Not robust to “higher order beliefs”
* Not robust to “information leakage”

EPIC:

* Does not depend on $\phi$ at all
* Robust to “higher order beliefs”
* Robust to “information leakage”
* Simpler to work with!


### Thm "The revelation principle"
If there exists a mechanism $\langle M, x, t \rangle$ that implements $\hat{x}$ in a (Bayesian, ex post, or dominant strategy) equilibrium $m^*$, then there exists a mechanism $\langle \Theta, \hat{x},\hat{t} \rangle$, where $\hat{t}(\hat{\theta}) = t(m^*(\hat{\theta}))$ for all $\hat{\theta}$, with an equilibrium $\hat{m}_i(\theta_i) = \theta_i$ for all $\theta_i$ and all $i$.

We say that $\langle \Theta, \hat{x}, \hat{t} \rangle$ truthfully implements $\hat{x}$.

For direct mechanisms we write $\langle x, t \rangle$.


### Thm "Groves Mechanism" (Aka VCG (Vickrey-Clarke-Groves) mechanisms.)
Assume private values. If $x^*(\theta)$ maximizes social welfare for each $\theta$, then $x^*$ is truthfully implemented in ex post equilibrium by any direct mechanism $\langle x^*, t \rangle$ satisfying
$$t_i(\theta) = \sum_{j \neq i} v_j(x^*(\theta), \theta_j) + h_i(\theta_{-i})$$
where $h_i: \Theta_{-i} \rightarrow \mathbb{R}$ is an arbitrary function, for all $\theta$ and all $i$.


> $h_i(\theta_{-i})$ CANNOT depend on $i$'s type!

**Example "Public Project"**

**Example "Externalities"**


> 2nd price auction is a Groves mechanism: people report truthfully, has efficient outcome.

### Result "Groves $\iff$ Efficient and EPIC"
In the private values setting, Groves Mechanism $\iff$ efficient outcome AND EPIC

Groves thm proves if, can use envelope thm to show only if.

## Envelope Thm


### Def "Equilibrium payoff function"
$U_i(\theta; x, t) = v_i(x(\theta), \theta) + t_i(\theta)$ is agent $i$'s utility in a truthful equilibrium of mechanism $\langle x, t \rangle$.

### Lemma "Milgrom and Segal"
If $v_i(\chi, (\cdot, \theta_{-i}))$ is differentiable in $\theta_i$ and $\frac{d}{d\theta_i} v_i(\chi, \theta)$ is uniformly bounded for all $\chi \in \mathcal{X}$ and all $\theta \in \Theta$, then in any EPIC mechanism $U_i((\cdot, \theta_{-i}))$ is continuous and piecewise differentiable in $\theta_i$.

### Thm "Envelope Thm"
If $v_i(\chi, (\cdot, \theta_{-i}))$ is differentiable in $\theta_i$ and $\frac{d}{d\theta_i} v_i(\chi, \theta)$ is uniformly bounded for all $\chi \in \mathcal{X}$ and all $\theta_{-i}$, then, for any direct mechanism $\langle x , t \rangle$ that truthfully implements $x$ isn ex post equilibrium, for all $\theta_{-i}$,

$$U_i(\theta; x, t) =  U_i(\underline{\theta}, \theta_{-i}; x, t) + \int_{\underline{\theta}}^{\theta_i} \big(\frac{\partial}{\partial s_i} v_i(x(\hat{\theta}_i, \theta_{-i}), s_i, \theta_{-i})\big)\bigg|_{\hat{\theta}_i = s_i} ds_i.$$

Example: A public project

Example: Allocating an object

## Linear Private Values

### Def "Linear Private values"
$$v_i(\theta, \chi) = \theta \hat{v}_i(\chi), \text{ where } \hat{v}_i: \mathcal{X} \rightarrow \mathbb{R}.$$

### Thm "Linear Private Values"
In the linear private values environment, a mechanism $\langle x, t\rangle$ implements $x$ in ex post equilibrium if and only if, for all $i$

1. $\hat{v}_i(x(\theta))$ is non-decreasing in $\theta_i$ for all $\theta_{-i}$, and 
2. $U_i(\theta; x, t) = U_i(\underline{\theta}_i \theta_{-i}; x, t) + \int_{\underline{\theta}_i}^{\theta_i} \hat{v}_i(x(s_i, \theta_{-i}))ds_i$ for all $\theta$.


## Bayesian Implementation

### Thm "D'Aspremont/Gerard-Varet (AGV) mechanisms"
In the private values environment, if $x(\theta)$ maximizes social welfare for all $\theta$ and types are distributed independently, then $x$ is truthfully implemented in Bayesian Nash equilibrium by any mechanism $\langle x, t \rangle$ satisfying
$$t_i(\hat{\theta}) = E \big[\sum_{j\neq i} v_j(x(\hat{\theta}), \hat{\theta}_j) | \hat{\theta}_i  \big] + h_i(\hat{\theta}_{-i}),$$
where $h_i: \Theta \rightarrow \mathbb{R}$ is an arbitrary function, for all $\hat{\theta}$ and all $i$.


### Def "interim equilibrium utility"
$$\overline{U}_i(\theta_i; x, t) \equiv E[U_i(\theta; x, t) | \theta_i]$$


### Thm "Bayesian envelope theorem"
Suppose that $E[v_i(\chi, \theta) | \theta_i]$ is differentiable in $\theta_i$ for all $\chi \in \mathcal{X}$. Then, for any direct mechanism $\langle x, t \rangle$ that truthfully implements $x$ in Bayesian Nash equilibrium, 
$$\overline{U_i}(\theta; x, t) =  \overline{U_i}(\underline{\theta}, \theta_{-i}; x, t) + \int_{\underline{\theta}}^{\theta_i} \frac{\partial}{\partial s_i} \mathbb{E} \big[ v_i(x(\hat{\theta}_i, \theta_{-i}), s_i, \theta_{-i}) \big]\bigg|_{\hat{\theta}_i = s_i} ds_i.$$

### Thm "Independent types + BNE $\Rightarrow$ EPBB"
Suppose that the players' types are distributed independently. Then, if $x$ is implementable in Bayesian Nash equilibrium, then $x$ is truthfully implementable in Bayesian Nash equilibrium with ; i.e., $\sum_i t_i(\theta) = 0$ for all $\theta$.


### Thm "Linear Private Values implements $x$ in BNE iff"
In the linear private values environment, a mechanism $\langle x, t \rangle$ truthfully implements $x$ in Bayesian Nash equilbrium if, and only if

1. $E[\hat{v}_i(x(\theta))|\theta_i]$ is non-decreasing in $\theta$, and
2. $\bar{U}_i(\theta_i; x, t) = \bar{U}_i(\underline{\theta_i}; x, t) +  \int_{\underline{\theta}}^{\theta_i} E[\hat{v}_i(x(s_i, \theta_{-i}))|s_i] ds_i$.

## Individual Rationality

### Thm "Myerson-Satterthwaite"
The efficient outcome function $x^*$ is not Bayesian implementable with ex post individual rationality and ex ante budget balance.

## Ex post implementation and Budget Balance

### Def "(N-1)-additive separability"
A function $\psi: \Theta \rightarrow \mathbb{R}$ is $(N-1)$-additively separable if there exist function $\alpha_i: \Theta_{-i} \rightarrow \mathbb{R}, i=1, ..., N$, such that $\psi(\theta) = \sum_i \alpha_i(\theta_{-i})$ for $\phi$-almost all $\theta$.

### Thm "EPIC and EPBB"
An outcome rule $x$ is ex post implementable with ex post budget balance only if $\sum_i t_i^*(\theta)$ is $(N-1)$-additively separable, where 
$$t_i^*(\theta) = \int_{\underline{\theta}}^{\theta_i} \frac{\partial}{\partial s_i}v_i(x(\hat{\theta}_i, \theta_{-i})), s_i, \theta_{-i}) ds_i - v_i(x(\theta), \theta).$$
For sufficiency, add appropriate monotonicity condition.

### Observation "Groves mechanisms are generally not budget balanced"
Recall $t_i(\theta) = \sum_{j\neq i} v_j(x^*(\theta), \theta_j) + h_(\theta_{-i})$. Observe $v_j(x^*(\theta), \theta_j)$ itself generally not $(N-1)$-additively separable.

> 2 players: usually (N-1)-additively separable!


# Principal-Agent Contracts

### Thm "Inverse Function Theorem"
If $f$ is continuously differentiable with nonzero derivative at $a$ then
$${\displaystyle {\bigl (}f^{-1}{\bigr )}'(b)={\frac {1}{f'(a)}}={\frac {1}{f'(f^{-1}(b))}}.}$$



<!-- # Algorithms to solve for each solution concept -->

<!-- ### PSNE -->
<!-- * Construct best-response correspondences -->
<!--     * take FOCs (and SOCs) to max if continuous -->
<!--     * split into cases -->

<!-- ### MSNE -->
<!-- 1. reduce to rationalizable/undominated strategies -->
<!-- 2. split into cases on support sizes for each player -->
<!-- 3. use indifference conditions -->


<!-- ### BNE -->
<!-- 1. Write in normal form -->


<!-- ### SPE -->
<!-- 1. draw out extensive form if possible -->
<!-- 2. check one-shot deviation principle if repeated -->
<!-- 3.  -->


<!-- ### wPBE -->
<!-- 1. is it a Beer-Quiche game? -->
<!-- 2. figure out indifference conditions before starting analysis -->
<!-- 3. iterate through: -->
<!--     1. determine sequentially rational response -->
<!--     2. ensure beliefs are consistent with Bayesian updating -->
<!--     3. check for deviations. -->


<!-- ### PBE -->

### Clarke Pivot Rule
FINISH
