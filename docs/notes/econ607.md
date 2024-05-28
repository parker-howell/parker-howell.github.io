---
title: 'Econ 607 Notes'
author: 'Parker Howell'
date: 'Last Updated: 2024-05-28'
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, encoding = encoding, output_dir = "../../website/parker-howell.github.io/docs/notes")})
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






# Simple Endowment Economy


### Def "Primitives Simple Endowment Economy"
* Last for $T+1$ periods, $T$ is odd
* One good, perishable (i.e., no storage)
* Two types of consumers: $A, B$, of which there are $N^A$ and $N^B$
* Endowments: $A: \{1,0,1, ..., 0\}, B: \{0, 1, 0, ..., 1\}$
* Utility: $\sum_{t=0}^\infty \beta^t u(c_t^j)$ (usually log utility)


### Def "real savings"
$$b_{t}^{j} = \frac{s_{t}^{j}}{p_{t}}$$


### Def "real rate of return (aka Fisher Equation)"
$$1+ r_t = (1+i_t)\frac{p_t}{p_{t+1}}$$
Can also write
$$1+ r_t = \frac{1+i_t}{1+\pi_t} \Rightarrow \underbrace{r_t \approx i_t - \pi_{t+1}}_{\substack{\text{by logs:} \\ \text{approx in discrete} \\ \text{exact in cont time}}}$$



### Def "SEE Budget constraints"
* period 0: $\underbrace{ p_0 y_0^j}_{\text{sell all}} \geq \underbrace{p_0 c_0^j}_{\text{buy some back}} + \underbrace{s_0^j}_{\text{save rest}}$
* period t: $p_t y_t^j + s_{t-1}(\underbrace{1 + i_{t-1}}_{\substack{\text{1+net = } \\ \text{gross nom}}}) \geq p_t c_t^j + s_t^j$
* period T: $p_T y_T^j + s_{T-1}(1 + i_{T-1}) \geq p_T c_T^j + \underbrace{s_T^j}_{\text{need no Ponzi}}$
* No Ponzi: $s_T^j \geq 0$
* rewrite period $t$ to convert from nominal: $y_t^j + \frac{s_{t-1}}{p_t}(1 + i_{t-1}) \geq c_t^j + \frac{s_t^j}{p_t}$
* rewrite period $t$ in terms of real savings: $y_t^j + \underbrace{\frac{s_{t-1}}{p_{t-1}}}_{b_{t-1}} \frac{p_{t-1}}{p_t} (1 + i_{t-1}) \geq c_t^j + \underbrace{\frac{s_t^j}{p_t}}_{b_t}$
* Final version of budget constraint:
$$y_t^j + b_{t-1}^j(1+r_{t-1}) \geq c_t^j + b_t^j$$
or, for period 0:
$$y_0^j \geq c_0^j + b_0^j$$


### Def "Competitive equilibrium"
A *competitive equilibrium* consists of

* prices $\{1+r_t\}_{t=0}^{T-1}$ and 
* sequences of allocations $\{ c_t^A, c_t^B, b_t^A, b_t^B  \}_{t=0}^{T}$ such that

1. Taking prices as given, the sequences of allocations maximize utility for $j = A,B$, and
2. All markets clear:

* goods market: $N^A c_t^A + N^B c_t^B = N^A y_t^A + N^B y_t^B$
* money/bond market: $N^A b_t^A + N^B b_t^B = 0$

### Def "standard Euler Equation"
$$c_{t+1} = \beta (1+r_t)c_t$$

> Remember: this EE corresponds to a single person

# Dynamic Programming

### Thm "Theorem of the Maximum"
If $u(x, s)$ is continuous then $v(s) = \max_x \{u(x,s)\}$ is continuous, and $h(s) = arg \max_x \{u(x,s)\}$ is upper hemicontinuous

**Additionally:** If $u(x, s)$ is strictly concave in $x$ for any $s$, then $h(s)$ is single-valued and continuous.

> Recall: upper hemicontinuity is what says convergent sequence converges in the set


### Def "Bellman"

The value of being in state $s_0$ is:
$$V(s_0)=\max_{\{c_t, s_{t+1} \}_{t=0}^\infty} \sum_{t=0}^\infty \beta^t u(c_t, s_t) \text{ s. to } \underbrace{s_{t+1} = g(c_t, s_t)}_{\text{transition eq}} \text{ and } s_0 \text{ given.}$$
where $c = $ choice variable(s), $s = $ state variable(s).

$V(\cdot)$ satisfies the "principle of optimality" (I'm going to pick everything I possibly can to try to maximize given that I am now in $s_0$).


Bellman:
$$V(s_0)=\max_{c} \{ u(c,s) + \beta V(s') \}$$



### Def "Contraction Mapping"
Define the mapping $T: X \rightarrow X$ where
$$T(f(s)) \equiv \max_c \{ u(c,s) + \beta f(g(c,s))  \}.$$

$T$ is a *contraction mapping* with modulus $\lambda\in (0,1)$ if $\forall x, y\in X$:
$$d(T(x), T(y)) \leq d(x, y).$$
For us, $x, y$ are functions and the metric norm we use is the supnorm: $d(x, y) = \sup_{s\in S} |x(s) - y(s)|$.


### Thm "Contraction Mapping Thm"

If $X$ is *complete* metric space and $T: X \rightarrow X$ is a contraction (with $\lambda$), then

1. $T$ has a *unique* fixed point: $x^* = T(x^*)$
2. for all $x_0 \in X$: $d(T^n(x_0), x^*) \leq \lambda^n d(x_0, x^*)$ for all $n = 0, 1, 2...$ where $T^n(x_0) = T(T^{n-1}(x_0))$


> Complete: "Cauchy sequences converge to a point in the space"


### Thm "Blackwell's Sufficient Conditions for a Contraction"
Let $X(s)$ be the set of bounded functions on $S \subseteq \mathbb{R}^m$.

Let $T: X(s) \rightarrow X(s)$ satisfy

1. monotonicity: $x, y \in X: x \geq y \Rightarrow T(x) \geq T(y)$
2. discounting: Let $k \in X(s)$ be a constant function. Then $x\in X(s) \Rightarrow T(x+k) \leq T(x) + \beta k$, for some $\beta \in (0,1)$.

Then, $T$ is a contraction.

> Caution: this monotonicity is different from the monotonicity of the value function

### "What should you know about math of dynamic programming?"

1. Our functional equation exists and has a unique solution.
2. $V$ is strictly concave if $u(c, s)$ is strictly concave and $g$... MISSING SOMETHING HERE
3. $V$ is approached by iterations: $v_{j+1}(s) = \max_c \{ u(c,s) + \beta v_j(g(c, s)) \}$
4. In the interior of $s$, $V$ is often differentiable.

![]("src/dynprog_fp")


### "Value Function Properties"
1. Continuity
2. Monotonicity (not the same as the monotonicity of Blackwell's)
    a. this is: "is the value function itself monotone"
    b. remember: we don't need strict increasing (think about the reservation wage in search model--flat is fine)
3. Differentiability (usually assume concavity to prove differentiability)


### "To have a unique solution to the Bellman"
1. Generate a $T$-mapping from our value function
    a. literally just replace $V$ with $Tf$: go from $v(x, z) = \sup_{x' \in \Gamma(x, z)} \{F(x, x', z) +  \beta E[v(x', z')]\}$ to $Tf(x, z) = \sup_{x' \in \Gamma(x, z)} \{F(x, x', z) +  \beta E[Tf(x', z')]\}$
2. Check that the value function is bounded
3. Assume the value function is continuous and weakly increasing
4. Check monotonicity and discounting
5. If both hold, invoke Blackwells to show that $T$ is a contraction mapping
6. If $T$ is a contraction mapping then it will converge (under the supnorm) to a unique fixed point $v$ by the Contraction Mapping Theorem.

<!-- ### "Benveniste-Sheinkman (Pancake Thm)" -->

# Consumption

### Def "PIH"
Think of income as $y_t = y_t^{Permanent} + y_t^{Transitory}$. 

PIH says consumption is a function of $y_t^{Permanent}$ only.

Think of $y_t^{Permanent}$ as "annuity value" of lifetime income.

> MPC if you are old should be relatively high: you only have a few more years to live so an increase in income should be spent right away

> MPC if you are young should be relatively low: you have to spread an increase in income over the rest of your life

> As soon as income is promised, lifetime consumption should increase proportionally over each period.

### Model "Random Walk Hypothesis (Hall 1978)"
We have stochastic Euler:
$$u'(c_t) = \beta(1+r)E_t[u'(c_{t+1})].$$
Hall looks at the Euler equation and realizes: $E_t[u'(c_{t+1})]$ is NOT actual marginal utility of next period, it's really $u'(c_{t+1}) +  \varepsilon_{t+1}$, and the error is actually forecast error!

And, if expectations are rational, then $E_t[\varepsilon_{t+1}] = 0$!

So, $Cov_t(u'(c_t), \varepsilon_{t+1})=0$! In fact, $Cov_t(x_t, \varepsilon_{t+1})=0$ for any date-$t$ information, $x_t$. Plug this into the Euler equation to see that
$$u'(c_{t+1}) = \frac{1}{\beta (1+r)} u'(c_t) + \varepsilon_{t+1}.$$

In other words, the marginal utility of consumption is following a random walk with drift! (Where drift=$\frac{1}{\beta(1+r)}$).

> this may suggest that consumption inequality is growing without bound.


### Def "PIH Lit"
* Hall
    * Questions the EE
* Johnson, Parker, and Suleilis 
    * Use $300 checks randomly distributed to debunk. 
* Shea
    * Uses union contracts stipulating when raises would occur
* Campbell + Mankiw 1989
    * Use IVs + null. Finds $\hat{\lambda} \approx 0.5$ meaning that half of all income goes to hand-to-mouth consumers. I.e., if PIH is true, it applies to half the population only.
* Hansen + Singleton 1982
    * Structural estimation, $\sigma \in [.67, .97]$
* Hall 1988
    * Using Hansen + Singleton spec. Assume $c_t \sim Lognormal$, regress consumption growth on interest rates and get $\hat{\sigma} \in [0, .2]$.

### Paper "Hansen + Singleton 1982"
Have $i = 1, ..., N$ assets. Still a 1-good model, just have lots of assets now.

Budget constraint:
$$c_t + \sum_{i=1}^N p_{i,t} a_{i,t} + s_t = y_t + s_{t-1}(1+r_{t-1}) + \sum_{i=1}^N a_{i, t-1} (p_{i,t} + d_{i,t})$$


* $a_i =$ number of units of asset $i$
* $d_i =$ dividend of asset i, received in the morning
* $p_i =$ price of asset i

Euler Equation:
$$p_{i, t} u'(c_t) = \beta E_t[(p_{i, t+1} + d_{i, t+1}) u'(c_{t+1})], \forall i.$$
Define ex-post real rate of return $R_{i, t+1} \equiv \frac{p_{i,t+1} + d_{i,t+1}}{p_{i,t}}$. Rewrite EE as
$$\beta E_t \bigg[\frac{u'(c_{t+1})}{u'(c_t)} R_{i, t+1}\bigg] = 1.$$
Define the ex-post difference between the forecast and actual:
$$\varepsilon_{i, t+1}(\theta) = \beta E_t \bigg[\frac{u'(c_{t+1})}{u'(c_t)} R_{i, t+1}\bigg] - 1$$
where $\theta$ is a set of parameters we will estimate using structural estimation. Impose functional form $u(c) = \frac{c^{1-1/\sigma}}{1-1/\sigma}$ to get:
$$\varepsilon_{i, t+1}(\theta) = \beta \bigg(\frac{c_{t+1}}{c_t}\bigg)^{-1/\sigma}R_{i, t+1} - 1.$$
We have data on $R$ and $c$, so $\theta = [\beta, \sigma]$.

Then we'll iterate through different values of $\beta, \sigma$ to get $E_t[\varepsilon_{i, t+1}(\theta)]$ to be close to 0.

Imposing rational expectations means that
$$E_t[\varepsilon_{i, t+1}(\theta) z_t] = 0, \forall i \forall z, \text{ where z is any var. dated t or earlier}.$$

They use GMM to get estimates: $\beta \in [.942, .998], \sigma \in [.67, .97]$.

### Def "Variations on PIH"

1. Precautionary Savings
2. Borrowing Constraints
3. "Irrational" Intertemporal Choice

## 1. Precautionary Savings


### Model "Precautionary Savings"

Assume $1+r = \frac{1}{\beta}$. Start with Euler Equation:

$$u'(c_t) = E_t[u'(c_{t+1})]$$

2nd order Taylor Approximate to get:

$${ u'(c_t)} \approx E_t[u'(c_t) + u''(c_t)(c_{t+1} - c_t) + \frac{u'''(c_t)}{2!}(c_{t+1} - c_t)^2]$$
Note: you can pull anything dated $t$ or earlier out of expectation. Cancel, rearrange, divide by $c_t$ to get
$$E\bigg[\frac{c_{t+1} - c_t}{c_t}\bigg] \approx \bigg(-\frac{1}{2}\bigg)\bigg(\frac{u'''(c_t)}{u''(c_t)}c_t\bigg)\bigg(E_t\bigg[\bigg(\frac{c_{t+1} - c_t}{c_t}\bigg) ^2\bigg]\bigg)$$
So Hall's insight is true for all first-order approximations if all you care about is slope (i.e., elasticity), but this says that under uncertainty.... SOMETHING??????? WHAT HAPPENS?????

> Kimball (1980) calls $-\frac{1}{2}(\frac{u'''(c_t)}{u''(c_t)}c_t)$ the coefficient of relative prudence.

## 2. Borrowing Constraints

### Def "primitives of Stochastic Exchange Economy"
* endowments
* no storage
* mass 1 of consumers
* $y_t(i) \sim \varphi[y^{min}, y^{max}]$ (this is a pdf or pmf that characterizes endowments. Importantly: endowments not correlated across individuals)

**Claim:**

$$Y_t = \int_0^1 y_t(i) di = \bar{y}$$

### Def "stationary stochastic equilibrium"
A *stationary stochastic equilibrium* consists of 

* a (single) interest rate $(1+r)$,
* a policy function $h(y,A)$, and 
* a distribution $g(A)$, 

such that

1. $h(\cdot)$ is optimal given $1+r$,
2. All markets clear:
    1. bond market $\int_{-\infty}^\infty \int_{y^{min}}^{y^{max}} h(y,A) \varphi(y)g(A) dy dA = 0$ (i.e., agg savings  0)
    2. goods market - clears by Walras' law
3. $g(A)$ is implied by $h(\cdot)$.


> individuals may move around, but the distribution itself is stationary


## 3. "Irrational" Intertemporal Choice

### Model "Irrational Intertemporal Choice"
Let individual agents change preferences--essentially playing games against their past and future selves, finding Nash equilibria.


#### Laibson (1997) "Commitment devices"
IRL people use commitment devices (e.g., tax withholding, destroying credit cards). This is indicative of self-control problems. But, the representative consumer doesn't use these commitment devices. In fact, the representative consumer has credit card debt. Something about converting savings to illiquid assets.

* Standard discounting: $u = u(c_0) + \beta u(c_1) + \beta^2 u(c_2) + \cdot \cdot \cdot$
* Quasi-hyperbolic discounting: $u = u(c_0) +  \delta \{\beta u(c_1) + \beta^2 u(c_2) + \cdot \cdot \cdot\}$

> Ainsle (1992) says $\delta = 2/3$ (very high!)

**Compare $t+k$ vs $t+k+1$:**

**At time $t$:**
$$MRS = \frac{\delta \beta^{t+k} u(c_{t+k})}{\delta \beta^{t+k+1} u(c_{t+k+1})} = \frac{u'(c_{t+k})}{\beta u(c_{t+k+1})}$$
**At time $t+k$:** 
$$MRS = \frac{\beta^{t+k} u(c_{t+k})}{\delta \beta^{t+k+1} u(c_{t+k+1})} = \frac{u'(c_{t+k})}{\delta\beta u(c_{t+k+1})}$$



#### Caplin + Leahy (2004, JPE) "Valuation of Past Consumption"
The only way to go through life without constantly regretting decisions is to 'upgrade' past experiences. E.g., "we're not forgoing income during PhD in hopes of getting a reward later; we're just still celebrating the candy bar we ate as a child."

![]("src/LeahyDiscounting.png")

If we really are different people at different stages of life, the conclusion is: young guy is screwing over old guy--we should save more at time $t$.


# Labor Supply and Search

Two ways of modeling: Supply or Search.

## Supply

<!-- Sargent + Ljungvist 6.1-6.3 -->

### Def "Labor Supply Setup"

Neoclassical (price-taking, utility maximizing, single time period framework) Labor Supply: $\max \{u(c) - \nu(N)\}$

e.g., 
$$\max_{c,N} \bigg\{\frac{c^{1-\frac{1}{\sigma}}}{1-\frac{1}{\sigma}} - \phi \frac{N^{1+ \frac{1}{\eta}}}{1+ \frac{1}{\eta}} \bigg\} \text{ s. to } pc = wN+A$$

where $N$ = number hours worked, $A$ = other assets, $\eta > 0$ is Frisch Labor Supply Elasticity.

FOC:

$$v'(N) = \frac{w}{p} u'(c) \Rightarrow \text{ using parametric form: } \phi N^{1/\eta} = \frac{w}{p} c^{-1/\sigma}$$
Taking logs:
$$\ln N = \eta \ln \frac{w}{p} - \frac{\eta}{\sigma} \ln c - \eta \ln \phi$$
This lends itself to a common regression. Applied economists often "tack on" an additional error term to account for structural things, omitted variables, or measurement bias.

This implies that leisure is a normal good. We see an income effect on labor supply.


## Search

LOTS HERE FINISH!!!!


# Asset Pricing

## CAPM

Recall Hansen and Singleton:

FINISH

Maximization problem lets us derive the price given below.

<!-- $$\max E_t $$ -->

### Def "stochastic discount factor"

$$m_{t, t+j} = m_{t+j} \equiv \beta^j \frac{u'(c_{t+1})}{u'(c_t)}$$

### Def "price of asset $i$"

$$p_{i,t} = E_t \bigg[\sum_{j=1}^\infty m_{t,t+j} x_{i,t+j} \bigg] = E_t \bigg[\sum_{j=1}^\infty \beta^j \frac{u'(c_{t+1})}{u'(c_t)} x_{i,t+j}\bigg]$$

### Def "R (payoff of asset)"
$$R_{i,t+1} \equiv \frac{p_{i,t+1} + x_{i, t+1}}{p_{i,t}}$$

### Def "CAPM"

* $Cov(m, R) = 0 \Rightarrow$ risk-adjsted return = safe return
* $Cov(m, R) < 0 \Rightarrow$ when $R$ high, $m$ low (on average)
    * MU(c) is low, which means consumption is high (economy booming). So, asset pays when economy good, and asset sucks when economy sucks.
    * $E_t[R] > 1+r_t$ <-- this is risk!
* $Cov(m, R) > 0 \Rightarrow$ when $R$ high, $m$ high (on average)
    * economy sucks, but asset comes thru. willing to sacrifice rate to reduce risk


> "US steelworkers should buy stock in foreign steel"


> If you have an asset paying off when MU(c) is high, this is an asset that reduces your risk. So, you are willing to sacrifice your return to acquire the risk-reducing asset.

> "If I tell you this asset will come through in your darkest hour you will want that asset. So demand will rise $\Rightarrow$ price will rise."


### Puzzle 1 "Log approximation suggests $r \approx 11%$"
do reading!


### Puzzle 2 "Equity Premium Puzzle"

Mehra & Prescott (1985) show that equity (risky) return over last 100 years is approx 8% compared to 1% for bonds. 

We would need an implausibly high level of risk aversion to make this 7% difference plausible. 

Potential (incomplete) solution: Myopic Loss Aversion

### Model Lucas Asset Pricing (Trees)

* Endowment economy. 
* "Trees" - identical and correlated entities (think firms) 
* Trees bear a dividend, $x_t$ each period. 
    * $x_t \sim F(x | x_{t-1})$ (Markov Process)
* No trade
* No storage
* In equilibrium $c_t = x_t$ (this is true for every agent)

FOC:
$$E_t \bigg[ \beta \frac{u'(c_{t+1})}{u'(c_t)} \frac{p_{t+1} + x_t{+1}}{p_t}   \bigg] = 1$$


### Def "Stochastic Competitive Equilibrium"
A *Stochastic Competitive Equilibrium* is 

* a pricing function $p_t = \varphi(x_t)$ and 
* an allocation rule $sc(x_t)$ such that

1. goods market clears: $c(x_t) = x_t$ and
2. Euler equation holds: $E_t \bigg[ \beta \frac{u'(x_{t+1})}{u'(x_t)} \frac{\varphi'(x_{t+1}) + x_{t+1}}{\varphi'(x_t)}   \bigg] = 1$

> In this economy, shocks affect the aggregate economy--very different from previous equilibria in which a shock affected an  individual. Shocks to the aggregate economy will cause price changes.


# Investment


### Facts about US Investment
* Investment makes up 15-20% of GDP
* $\Delta$ Inventories comprises 0.1% of GDP, but unsold inventories account for 1/3 of variation in GDP
* $\delta$ for equipment $\approx$ 7-15% per year
* $\delta$ for structures $\approx$ 1-3% per year

### Def "User Cost of Capital"
$$\underbrace{p}_{=1} MPK = p_t^k (r + \delta  - \frac{\Delta p_{t+1}^k}{p_t^k}(1-\delta))$$
or in continuous time:
$$r_K(t) = p_K(t)\bigg[r(t) + \delta - \frac{\dot{p}_K(t)}{p_K(t)}\bigg]$$

> works well for long-term rentals/purchases, but no so well for short-term.


### Jorgenson's Model
Firm input demand: 
$$\max \sum_{t=0}^\infty (\frac{1}{1+r})^t\bigg(\underbrace{p}_{=1} F(K_t, N_t) - w_t N_t - p^k_t I_t  \bigg) \text{ s. to } K_{t+1} = K_t(1-\delta) + I_t$$
Solving gives:
$$F_{K, t+1} = p_{t+1}^K (r + \delta  - \frac{\Delta p_{t+1}^k}{p_t^k}(1-\delta))$$
which is the user cost of capital we defined previously.

In continuous time, $1-\delta \rightarrow 1$. We solve through one of:

**Hamiltonian:**
$$finish$$
or **Dynamic Programming:**
$$finish$$
to get:
$$p_t^k = \frac{1}{1+r} \sum_{j=0}^\infty (\frac{1-\delta}{1+r}^j) F_{k,t+j+1}.$$

> Summers: "this isn't really even investment demand... it's just capital demand."


## Q-theory

> "Investment analog to the PIH"


### Def "Tobin's Q"
$$Q^{Tobin} = \frac{\text{Value of firm}}{\text{Replacement Cost of Capital}} = \frac{V}{K} \equiv \text{average } Q$$



### Def "Hayashi Form"
Common parametrization for adjustment costs:
$$C(I, K) = K \phi(\frac{I}{K}), \phi \text{ convex. E.g., } C(I, K) = K \underbrace{\gamma(\frac{I}{K} - \delta)^2}_{\phi}.$$

### Model "Hayashi, Abel, Summers (i.e., Jorgenson's with adjustment costs)"

$$V(0)= \int_0^\infty e^{-rt} [F(K(t)) - \underbrace{p^K}_{=1} I(t) - C(I(t), K(t))]dt \text{ s. to } \dot{K}(t) = I(t) - \delta K(t)$$
$$\mathcal{H}^{\text{current value}} = F(K) - I - C(I, K) + q(I - \delta K)$$



Note that $q=$ Marginal value of additional capital = "marginal $q$." We want an expression for $q$ 

Assume Hayashi form and take FOCs:
$$\frac{\partial \mathcal{H}}{\partial I} = 0 \iff  -1 - \frac{\partial}{\partial I} (K \phi(\frac{I}{K})) + q = 0 \iff \phi'(\frac{I}{K}) = q - 1$$
$$\frac{\partial \mathcal{H}}{\partial K} = H_K = rq - \dot{q} \iff F_K - C_K - \delta q = rq - \dot{q} \iff FINISH$$
In the end we get:
$$q(t) = \int_t^\infty e^{-(r+\delta)(s - t)} [F_K(s) - \Gamma(s)]ds$$


### Thm "Hayashi's Thm"
If $F(K, N)$ and $C(I, K)$ are both homogeneous of degree 1 (aka $H^1$ or CRS in all inputs) then $Q = q$.

Other assumptions Hayashi makes implicitly:

* No financing constraints
* Competitive
* Single type of capital


**Intuition:** value of the firm is linearly proportional to capital: $V(t) = const(t) K(t)$.

Given $K(t)$, $K(t+s), I(t+s), N(t+s)$ are optimal if $K(t)$ doubles:

* $K^{new}(t+s) = 2 K(t+s)$
* $I^{new}(t+s) = 2 I(t+s)$
* $N^{new}(t+s) = 2 N(t+s)$

> If I double $K$ I double the value of the firm


## Intertermporal Elasticity of Investment Demand
"Lumpy" investment/inertia

Same model as before, but we've shifted back to discrete:

$$\underbrace{q_t}_{\text{Shadow Val}} = \frac{MPK_{t+1}}{1+r} + \underbrace{\frac{1-\delta}{1+r}q_{t+1}}_{\text{continuation val}}$$

$$\underbrace{p_t^k = q_t}_{\text{no adj costs now!}} = \frac{1}{1+r} \sum_{j=0}^\infty (\frac{1-\delta}{1+r})^j MPK_{t+j+1}$$

> if I know of some improvement in future MPK I should invest more today!


### Claim
If the subsidy is temporary and $\delta$ (and $r$) are small then $q_{j,t} \approx \bar{q}_j$. (i.e., $\frac{\Delta q_{j,t}}{\bar{q}_j} \approx 0$).


### Model Investment with Kinked Adjustment Costs

* purchase capital at $p^k$ (generally normalized to 1)
* sell capital at $\alpha p^k, \alpha < 1$.
* Payoff: $\Pi(K, \varepsilon), \varepsilon \sim iid, \Pi_K > 0, \Pi_{KK} < 0, \Pi_{K, \varepsilon} > 0$
* Cost of buying capital: 
$$\phi(K' - K) = \begin{cases} K' - K \text{ if } K' \geq K \\ \alpha(K' - K) \text{ if } K' \leq K \end{cases}$$

<!-- * high $\varepsilon$ -->



### Model Investment Adjustment with Fixed Costs

* Pay fixed cost, $F > 0$ any time $K' \neq K$.
* 


# Real Business Cycle (RBC) Models

### Regularities

* General equilibrium
* Representative agent
* No market failures
* No money
* Productivity shocks

**Household problem**
$$\max E_t \bigg[\sum_j \beta^j (\frac{c_{t+j}^{1-1/\sigma}}{1-1/\sigma} - \phi \frac{\eta_{t+j}^{1 + 1/\eta}}{1 +  1/\eta})\bigg]$$
s. to

1. $k_{t+1} = (1-\delta)k_t + I_t$ (capital accumulation)
2. $b_t + c_t + I_t = w_t n_t + R_t k_t + b_{t-1}(1+ r_{t-1})$ (budget constraint)

Notes:

* $\sigma$: IES
* $\eta$: Frisch elasticity of labor supply
* HH's hold capital (this makes things easier, but could have firms hold and HHs own firms instead)
* $b_t = 0$ in equilibrium --WHY??

FOCs:

1. Labor supply: $w_t c_t ^{-1/\sigma} = \phi n_t ^ {1/\eta}$
2. Euler equations: $c_t^{-1/\sigma} = \beta E_t\bigg[c_{t+1}^{-1/\sigma} (\underbrace{R_{t+1} + 1-\delta}_{=1+r_t}) \bigg]$

**Firm's problem**
$$\max Y_t - w_t - R_t K_t \text{ s. to } Y_t = Z_t K_t^\alpha N_t^{1-\alpha}$$



### RBC 8 unknowns and equations

Unknowns: $Z, K, I, Y, C, N, R, w$

1. Labor Supply (derive from HH FOCs for $n$ and $c$)
$$w_t c_t^{-1/\sigma} = \phi n_t^{1/\eta}$$
2. Euler equation(s) (derive from HH FOCs for $I$ and $K$ or $b$ and $c$)
$$c_t^{-1/\sigma} = \beta E_t[c_{t+1}^{-1/\sigma} (R_{t+1} + 1-\delta)]$$

3. Labor demand (derive from Firm's FOC for $N$)
$$w_t = (1-\alpha)Z_t K_t^\alpha N_t^{-\alpha}$$


4. Capital demand (derive from Firm's FOC for $K$)
$$R_t = \alpha Z_t K_t^{\alpha - 1} N_t^{1-\alpha}$$


5. Production Function
$$Y_t = Z_t K_t^\alpha N_t^{1-\alpha}$$

6. Market Clearing/Resource Constraint
$$Y_t = C_t + I_t$$

7. Capital Accumulation Equation
$$K_{t-1} = K_t(1-\delta) + I_t$$
8. Productivity
$$Z_t \sim F(Z_t | Z_{t-1}), Z_t = (1-\rho)\bar{Z} + \rho Z_{t-1} + \varepsilon_t$$

9. Intermediate from FOC $\partial I_t$
$$q_t = C_t^{-\frac{1}{\sigma}}$$

10. Intermediate from FOC $\partial K_{t+1}$
$$q_t = \beta E_t [C_{t_1}^{-\frac{1}{\sigma}} R_{t+1} + (1-\delta)q_{t+1}]$$

### Def "Recursive Competitive Equilibrium"
A *Recursive Competitive Equilibrium* is 

* a set of pricing functions $R(K, Z), w(K,Z)$;
* a set of individual policy functions $k'(k, K, Z), n(k, K,Z), c(k,K,Z)$, and
* aggregate allocation functions $K'(K, Z), n(K,Z), c(K,Z)$ 

such that

1. Taking $R(\cdot), w(\cdot)$, and $K(\cdot)$ as given, $n(\cdot), k(\cdot), c(\cdot)$ are optimal,
2. Firms max profits:
    a. $R(K,Z) = \alpha Z K^{\alpha-1} N(K,Z)^{1-\alpha}$,
    b. $w(K,Z) = (1- \alpha) Z K^{\alpha} N(K,Z)^{-\alpha}$
3. Markets clear:
    a. $Z K^\alpha N(K, Z)^{1-\alpha} = C(K, Z) + K'(K, Z) - K(1-\delta)$
4. $n(\cdot), k(\cdot), c(\cdot)$ imply $R(\cdot), w(\cdot), K(\cdot)$
    a. i.e., $k'(K, K, Z) = K'(K, Z)$, etc.
    b. Sargent calls this "big $K$-little $k$ trick"


> Here we are accomodating for 2 types of uncertainty: (1) for consumers, and (2) prices--$w_t$ and $R_t$ are moving around!

<!-- Recall: we started with a stationary stocahastic equilibrium: instead of a sequence of allocations it was a set of policy functions. As soon as we allowed for uncertainty, we had to change  -->

**Dynamic Programming Solution**

1. Solve for "nonstochastic" steady state, $\bar{k}, \bar{C},\bar{I},\bar{Y}, ...$
2. Linearize system and solve

### Claim
finish

### RBC Limiting Solution
* $\rho\rightarrow 0$ (short-lived shocks)
* $\delta\rightarrow 1$ (long-lived capital)
* $\beta\rightarrow 1$ (HHs more patient)

this causes:

$q_t \approx \bar{q} \iff \tilde{q}_t \approx 0$ and $K_t \approx \bar{K} \iff \tilde{K}_t \approx 0$

$\tilde{q}_t, \tilde{K}_t \approx 0 \Rightarrow \tilde{C}_t \approx 0$ (via FOC)

FINISH


# Money Demand


### Theory of Money Demand
* Kiyotaki + Wright
    * Matching model - A, B, C produce and consume one good each but never have a coincidence of wants. Suppose $a$ and $b$ are a pain to carry around, but $c$ not so much. Then $c$ becomes money.
* Townsend's turnpike
* Banerjee and Maskin
    * Asymmetric info: some goods are counterfeit. A good that is easy to identify as noncounterfeit emerges as medium of exchange.
    
> Walrasian models do not allow *fiat* money.

Alternative to these pure theory models:

**Assume money has a "convenience yield"**

### Money Demand Modeling

$$U = E\bigg[\sum_{t=0}^T \beta^t \bigg\{ u(c_t) + \Lambda\bigg(\frac{M_t}{P_t}\bigg)  \bigg\}\bigg]$$

* $\Lambda(\cdot) > 0, \Lambda''(\cdot) < 0$
* Could have a point where $\Lambda'(\cdot) = 0$ but not necessary

*Nominal* Budget Constraint
$$P_t C_t + S_t + M_t = P_t Y_t + S_{t-1}(1+i_{t-1} + M_{t-1})$$
FOCs wrt $C, S, M$ give

**(Hall's) Euler Equation**
$$u'(c_t) = \beta (1+i_t) E\bigg[\frac{p_t}{p_{t+1}}  u'(c_{t+1})\bigg]$$

**Money Demand Equation**
$$\Lambda'\bigg(\frac{M_t}{P_t}\bigg) = u'(C_t)\frac{i_t}{1+i_t}$$

### Friedman Rule
Set monetary policy so $i_t = 0$:
$$\Lambda'\bigg(\frac{M_t}{P_t}\bigg) = u'(C_t)\frac{i_t}{1+i_t} = 0$$

> $M$ changes nominal variables only up to this point, so no real effect except Friedman's rule.

> Very stupid in practice because of zero lower limit. One way to get Friedman allocation is to pay an "interest on reserves" so government isn't punishing banks holding resources.

### Nominal Rigidity - Mankiw, Akerlof, Yellen (1985) Menu Costs

* Firm with payoff $\Pi(p)$
* optimal price solves $\Pi'(p^*) = 0$
* suppose current price $p \neq p^*$ but the firm has to pay a menu cost, $z>0$ to change the price
* assume firm can affect prices (this assumption is ubiquitous in this literature)

Loss from not adjusting:
$$L(p) = \Pi(p) - \Pi(p^*)$$
Notice:
$$\Pi(p) \approx \Pi(p^*) + \Pi'(p^*)(p-p^*) + \frac{1}{2} \underbrace{\Pi''(p^*)}_{\text{curvature}}(p-p^*)^2$$
So,
$$L(p) \approx \frac{1}{2} \Pi''(p^*)(p-p^*)^2.$$
So, the firm suffers only a second-order loss to not adjusting (remember--severity of this loss will depend on curvature of $\Pi(\cdot)$).

BUT, aggregate up to Welfare and you get first-order price rigidities from second-order menu costs!

# Misc


### Law of Iterated Expectations (LIE)
$$E[E[Y|X]] = E[Y]$$

### Covariance
$$cov(X, Y) = E[(X - \mu_x)(Y - \mu_Y)] = E[XY] - E[X]E[Y]$$

### Growth rates
$$g_{X,t} \equiv  \frac{X_{t} - X_{t-1}}{X_{t-1}} \approx \ln X_t - \ln X_{t-1} = \ln \frac{X_t}{X_{t-1}} = \ln(1+g_{X,t})$$

> gross $\approx$ 1 + net; Gross: $\frac{c_{t+1}}{c_t}$; Net: $g_{c, t+1}


### Log linearization
1. take logs
2. First order Taylor approximation about the steady state
3. Simplify so everything is either in terms of percentage deviations from steady state, or is a steady state variable.

$\tilde{x} \equiv \frac{1}{x^{ss}}(x - x^{ss})$


### Current vs Present Value Lagrangian
Example: want to max:
$$\sum_{t=0}^\infty \beta^t u(c_t) \text{ s. to } k_t^{\alpha} \geq c_t + k_{t+1}$$
**Present-value Lagrangian:**
$$\mathcal{L} = \sum_{t=0}^\infty \beta^t u(c_t) + \sum_{t=0}^\infty \lambda_t(k_t^{\alpha} - c_t + k_{t+1})$$

> $\lambda_t$ reflects the marginal increase in lifetime utility that would result from an incremental reduction in the constraint in period $t$. 


**Current-value Lagrangian:**
$$\mathcal{L} = \sum_{t=0}^\infty \beta^t [u(c_t) + \lambda_t(k_t^{\alpha} - c_t + k_{t+1})]$$

> $\lambda_t$ reflects the marginal increase in period-$t$ utility that would result from an incremental reduction in the constraint in period $t$. 



### Current vs Present Value Hamiltonian
Example: Continuous-time version of the discrete-time problem considered above: 
$$\max \int_{t=0}^\infty e^{-\rho t} u(c(t)) \text{ s. to } \dot{k}(t) \geq k(t)^\alpha - c(t)$$
**Present-value Hamiltonian:**
$$\mathcal{H} = e^{-\rho t} u(c(t)) + \lambda(t)[k(t)^\alpha - c(t)]$$
FONCs:

1. for control variables: $\mathcal{H}_c = 0 \Rightarrow e^{-\rho t} u'(c(t)) - \lambda(t) = 0$
2. for state variables: $\mathcal{H}_k = -\dot{\lambda}(t) \Rightarrow \lambda(t) \alpha k(t)^{\alpha - 1} = -\dot{\lambda}(t)$
3. $\dot{k}(t) = k(t)^\alpha - c(t)$


**Current-value Hamiltonian:**
$$\mathcal{H} = u(c(t)) + \lambda(t)[k(t)^\alpha - c(t)]$$
FONCs:

1. for control variables: $\mathcal{H}_c = 0 \Rightarrow u'(c(t)) - \lambda(t) = 0$
2. for state variables: $\mathcal{H}_k = \rho \lambda(t) -\dot{\lambda}(t) \Rightarrow \lambda(t) \alpha k(t)^{\alpha - 1} = \rho \lambda(t) -\dot{\lambda}(t)$
3. $\dot{k}(t) = k(t)^\alpha - c(t)$
