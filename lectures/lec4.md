---
theme: neversink
background: RL-bg.png
class: 'text-center'
transition: slide-left
title: Speech Recognition (DSAI 456)
author: Mohamed Ghalwash
year: Spring 2025-2026
venue: Zewail City
mdc: true
lecture: 4
slide:
  disableSlideNumbers: true
slide_info: false
---

# Speech Recognition <br> (Spring DSAI 456)
## Lecture 4

Mohamed Ghalwash
<Email v="mghalwash@zewailcity.edu.eg" />

---
layout: top-title
---

:: title :: 

# Lecture 3 Recap 

:: content :: 
  
- Single Univariate Gaussian Distribution

---
layout: top-title 
---

:: title :: 

# Motivation: Three Distributions

:: content :: 

![Three](./images/lec4_mixture_3_gaussians.png)

$$x \sim  \textcolor{green}{0.3 * \mathcal{N_1}(\mu_1,\sigma_1)} + \textcolor{red}{0.4 * \mathcal{N_2}(\mu_2,\sigma_2)} +  \textcolor{purple}{ 0.3 * \mathcal{N_2}(\mu_2,\sigma_2)} $$

---
layout: top-title 
class: text-center 
---

:: title :: 

# Motivation: Mixture of Multivariate Distributions

:: content :: 

![Multivariate](./images/lec4_gaussian_mixtures_2d.png){style="margin: auto;"}

---
layout: top-title
---

:: title :: 

# Univariate vs Multivariate 

:: content ::

## Each component is modeled as 

- Univariate 
  
$$
p(x) = \mathcal{N}(x\mid \mu, \sigma^{2}) \;=\; \frac{1}{\sqrt{2\pi\sigma^{2}}}\,\exp\!\left(-\frac{(x-\mu)^{2}}{2\sigma^{2}}\right)
$$

- Multivariate
$$
p(x) = \mathcal{N}(x\mid\mu,\Sigma)=\frac{1}{(2\pi)^{D/2}|\Sigma|^{1/2}}
\exp\!\left(-\frac{1}{2}(x-\mu)^\top\Sigma^{-1}(x-\mu)\right)$$


---
layout: intro
---

# Gaussian Mixture Model

A weighted sum of Gaussian components used to model complex continuous distributions

---
layout: top-title
---

:: title :: 

# What is a GMM?

:: content :: 

- Density
$$
p(x)=\sum_{k=1}^K \pi_k \,\mathcal{N}(x\mid\mu_k,\Sigma_k) \\ 
\text{such that } \sum_{k=1}^K \pi_k = 1,\quad \pi_k \ge 0
$$

- Parameters: 
  - weight $\pi_k$
  - mean $\mu_k$
  - covariance $\Sigma_k$

---
layout: top-title
---

:: title :: 

# GMM

:: content :: 

Emphasize the difference between 
- One univariate distribution for each class 
- One multivariate distribution for each class 
- Mixture of univariate distributions for each class 
- Mixture of multivariate distributions for each class 
- Each class might have a different number of mixtures 
- Choosing the number of mixtures for each class 


---
layout: center
class: text-center
---

# Learn More

[Course Homepage](https://github.com/m-fakhry/DSAI-456-SR)
