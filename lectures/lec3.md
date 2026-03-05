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
lecture: 3
slide:
  disableSlideNumbers: true
slide_info: false
---

# Speech Recognition <br> (Spring DSAI 456)
## Lecture 3

Mohamed Ghalwash
<Email v="mghalwash@zewailcity.edu.eg" />

---
layout: top-title
---

:: title :: 

# Lecture 3 Recap 

:: content :: 
  
- Mel Spectrum 
- Mel Filter Bank
- MFCC


---
layout: top-title 
---

:: title :: 

# Agenda 

:: content :: 

- Motivation and intuition
- Mathematical formulation
- EM algorithm (E-step / M-step)
- Using GMMs in speech recognition 
- Practical tips


---
layout: top-title 
---

:: title :: 

# Motivation: GPA Distribution 

:: content :: 

![Single](./images/lec4_single_gaussian.png){width=60% style="margin: auto;"}

$$GPA \sim \mathcal{N}(\mu,\sigma)$$

$$
p(GPA) = \mathcal{N}(GPA\mid \mu, \sigma^{2}) \;=\; \frac{1}{\sqrt{2\pi\sigma^{2}}}\,\exp\!\left(-\frac{(GPA-\mu)^{2}}{2\sigma^{2}}\right)
$$


---
layout: top-title 
---

:: title :: 

# Motivation: Two Distributions 

:: content :: 

![Two](./images/lec4_mixture_2_gaussians.png)

$$x \sim \textcolor{green}{\mathcal{N_1}(\mu_1,\sigma_1)} + \textcolor{red}{\mathcal{N_2}(\mu_2,\sigma_2)}$$


---
layout: top-title 
---

:: title :: 

# Motivation: Two Distributions 

:: content :: 

![Two](./images/lec4_mixture_2_gaussians_2.png)

$$x \sim \textcolor{green}{\mathcal{N_1}(\mu_1,\sigma_1)} + \textcolor{red}{\mathcal{N_2}(\mu_2,\sigma_2)}$$

<v-click>

<Admonition title="Should be weighted sum" color='teal-light' width="300px" v-drag="[660,450,310,60]">

$x \sim  \textcolor{green}{0.3 * \mathcal{N_1}(\mu_1,\sigma_1)} + \textcolor{red}{0.7 * \mathcal{N_2}(\mu_2,\sigma_2)}$

</Admonition>

</v-click> 



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
layout: center
class: text-center
---

# Learn More

[Course Homepage](https://github.com/m-fakhry/DSAI-456-SR)
