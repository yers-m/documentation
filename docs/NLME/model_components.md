# Model components

## Structural model
* describes the central tendency in the data
    + "e.g. the central tendency of the cortisol concentration-time profiles after administration of hydrocortisone"
* to develop the simplest model, which still describes the data accurately [[2004_Ette]](https://doi.org/10.1345/aph.1d374)

$$y_{ij}=f(𝜙_{i},  x_{ij})$$ 
> $i$ - certain individual;<br>
> $j$ - certain timepoint;<br>
> $f$ - a nonlinear function;<br>
> $𝜙$ - vector of model parameters ($CL$, $V_c$);<br>
> $x$ - study design variables (covariates, dose and sampling times).

---

## Pharmacostatistical model
* several hierarchical levels of pharmacostatistical models

### InterIndividual Variability <kbd>**IIV**</kbd>
* difference between individuals
* allows for the individual parameter estimate to differ from the population estimate
* $𝜂_i$
    + discrepancy between the population estimate and individual model parameter
    + Empirical bayes estimates, or EBE
    + independent of each other 
    + normally distributed around 0 
    + variance of $ω^2$
    + the same within an individual unless IOV is applied
    + can be added as:
        - additive
        - proportional
        - <u>exponential</u>
            - the most common as parameters are usually log-normally distributed and non-negative values

$$𝜙_{i}=g(𝜃,  z_{i}) + 𝜂_i$$

$$𝜙_{i}=g(𝜃,  z_{i}) \cdot (1+ 𝜂_i)$$

$$𝜙_{i}=g(𝜃,  z_{i}) \cdot e^{𝜂_i}$$

> $i$ - certain individual;<br>
> $𝜙$ - vector of model parameters ($CL$, $V_c$);<br>
> $θ$ - population parameter estimates;<br>
> $z_{i}$ - covariates.

### InterOccasion Variability - <kbd>**IOV**</kbd>
* variability between different occasions
* depends on study design (different doses/days/study periods...)
* does not describe the reason for the variability between occasions
* should only be used if the model parameters change randomly between occasions
* $k_i$ [[1993_Karlsson]](https://doi.org/10.1007/bf01113502)
    + normally distributed around 0 
    + variance of $π^2$

$$𝜙_{i}=g(𝜃,  z_{i}) \cdot e^{𝜂_i+k_i}$$

### Residual Unexplained Variability <kbd>**RUV**</kbd>
* unexplained variability resulting
    + e.g. measurement error, model misspecification and errors in dosing
*discrepancy between the observed and individually predicted
* $ε_{ij}$
    + normally distributed around 0 
    + variance of $σ^2$
    + can be added as
        + additive
            + If estimating parameters using log-transformed data an additive model is commonly applied, since it approximates an exponential or a proportional RUV model on a linear scale
        + proportional
        + combined

$$y_{ij}=f(𝜙_{i},  x_{ij}) + ε_{add,ij}$$

$$y_{ij}=f(𝜙_{i},  x_{ij}) \cdot (1+ ε_{prop,ij})$$

$$y_{ij}=f(𝜙_{i},  x_{ij}) \cdot (1+ ε_{prop,ij}) + {add,ij}$$

---

## Covariate modeling
* whether any dose adjustments are needed in specific populations
* potentially reducing some unexplained IIV [[2012_Mould]](https://doi.org/10.1038%2Fpsp.2012.4)
    + body size related covariates
    + creatinine clearance for drugs with renal elimination
    + time-varying covariates [[2004_Wahlby]](https://doi.org/10.1111%2Fj.1365-2125.2004.02170.x)

$$𝜙_{i}=𝜃 + 𝜃_{cov} \cdot (z_{i}-z_{median})$$
> $θ$ - population parameter;<br>
> $θ_{cov}$ - covariate effect;<br>
> $z_{i}$ - individual covariate value;<br>
> $z_{median}$ - median value of the covariate.

---

