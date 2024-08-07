# Model components
* Models
    * represented in the form of mathematical relationships 
    * to answer certain questions and aid particular purposes 
    * using a combination of models:
        * [structural model](#structural-model);
        * [pharmacostatistical model](#pharmacostatistical-model);
        * [covariate model](#covariate-model).

---

## Structural model
* mathematical form of algebraic/differential equations 
    * parameters, their relationships, or rate of change [[📖]](https://doi.org/10.1007/s40262-017-0575-8 "Melin, 2018") [[📖]](https://www.scribd.com/document/319808093/Shafer-Nonmem-2) [[📖]](https://doi.org/10.1038/psp.2012.4)
    * parameters are considered as “true” values for the population with possible variability [[📖]](https://www.scribd.com/document/319808093/Shafer-Nonmem-2)
* describes the central tendency in the data
    + "e.g. the central tendency of the cortisol concentration-time profiles after administration of hydrocortisone"
* to develop the simplest model, which still describes the data accurately [[📖]](https://doi.org/10.1345/aph.1d374)

$$y_{ij}=f(𝜙_{i},  x_{ij})$$ 
> $i$ - certain individual;<br>
> $j$ - certain timepoint;<br>
> $f$ - a nonlinear function;<br>
> $𝜙$ - vector of model parameters ($CL$, $V_c$);<br>
> $x$ - study design variables (covariates, dose and sampling times).

---

## Pharmacostatistical model
* describes the variability, which can be subdivided into IIV and RUV models [[📖]](https://doi.org/10.1007/bf01113502 "Karlsson, 1993") [[📖]](https://doi.org/10.1038/psp.2013.14 "Mould, 2013")
* several hierarchical levels of pharmacostatistical models

### <kbd>**IIV**</kbd>
* **InterIndividual Variability**
* difference between individuals
* allows for the individual parameter estimate to differ from the population estimate
* $𝜂_i$
    + discrepancy between the population estimate and individual model parameter
    + Empirical bayes estimates, or EBE
    + independent of each other 
    + normally or log-normally distributed around 0 [[📖]](https://www.scribd.com/document/319808093/Shafer-Nonmem-2 "Fisher, 2007") [[📖]](https://doi.org/10.1038/psp.2013.14 "Mould, 2013")
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

### <kbd>**IOV**</kbd>
* **InterOccasion Variability**
* variability between different occasions
* depends on study design (different doses/days/study periods...)
* does not describe the reason for the variability between occasions
* should only be used if the model parameters change randomly between occasions
* $k_i$ [[📖]](https://doi.org/10.1007/bf01113502 "Karlsson, 1993")

$$𝜙_{i}=g(𝜃,  z_{i}) \cdot e^{𝜂_i+k_i}$$

### <kbd>**RUV**</kbd>
* **Residual Unexplained Variability**
* to explain the difference between model-predicted values and observations in the form of distribution variance [[📖]](https://www.scribd.com/document/319808093/Shafer-Nonmem-2 "Fisher, 2007") [[📖]](https://doi.org/10.1038/psp.2013.14 "Mould, 2013")
* unexplained variability
    + e.g. resulted by measurement error, model misspecification and errors in dosing
* discrepancy between the observed and individually predicted
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

## Covariate model
* explain variability using observable factors between subjects [[📖]](https://doi.org/10.1038/psp.2013.14 "Mould, 2013")
    * e.g. age, disease progression, height, weight, or interacting agents/drugs 
* whether any dose adjustments are needed in specific populations
* potentially reducing some unexplained IIV [[📖]](https://doi.org/10.1038%2Fpsp.2012.4 "Mould, 2012")
    + body size related covariates
    + creatinine clearance for drugs with renal elimination
    + time-varying covariates [[📖]](https://doi.org/10.1111%2Fj.1365-2125.2004.02170.x "Wahlby, 2004")

$$𝜙_{i}=𝜃 + 𝜃_{cov} \cdot (z_{i}-z_{median})$$
> $θ$ - population parameter;<br>
> $θ_{cov}$ - covariate effect;<br>
> $z_{i}$ - individual covariate value;<br>
> $z_{median}$ - median value of the covariate.

## "Final model"
* needs to have a scientific basis and descriptive and predictive power to address given clinical questions [[📖]](https://doi.org/10.1038%2Fpsp.2012.4 "Mould, 2012")
* based on components, mechanisms, and assumptions, which should be 
    * credible;
    * reasonable; 
    * comparable with existing system components.

---
