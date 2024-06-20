---
title: 'Misc'
author: 'Parker Howell'
date: 'Last Updated: 2024-06-11'
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



# Misc

### "Which way standard form"
$X \leq Y \Rightarrow OBJECTIVE + \lambda(Y - X)$


### "Utility Functions"
* Log
    * Doesn't have any relationship with the interest rate
* CRRA
    * $u(c) = \frac{c^{1-\sigma}}{1-\sigma}$
    * Note: $\lim_{\theta \rightarrow 1} \frac{c^{1-\theta} - 1}{1-\theta} = \ln c$
* CARA?

### "Intertemporal elasticity of substitution"
$\frac{1}{\theta} = IES$. 

* High $\theta \Rightarrow$ really want to smooth consumption. Won't be very reactive to rate changes.
* Low $\theta \Rightarrow$ don't care about smooth consumption. So, very reactive to changes in $r$.

### "Production Functions"
* Cobb-Douglas: $Y_t = K_t^\alpha L_t^{1-\alpha}$
* Linear: $Y = AK_t + BL_t$
    * CRS, but NOT neoclassical (because Marginal products are positive, but not falling!)
    * Production-side equilibrium:
        * $R_t = A; w_t = B$



### "Caution: log-differentiating works only in continuous time!" 
In discrete time you need to use the definition of growth rates...

### "Marginal Utility"
If $MU(c)$ is high then $c$ is low! This makes sense if you plot it out with MU(c) on the y-axis and $c$ on the x-axis and note that MU is falling in $c$.
