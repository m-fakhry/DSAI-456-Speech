---
theme: neversink
background: RL-bg.png
class: text-center
transition: slide-left
title: Speech Recognition (DSAI 456)
author: Mohamed Ghalwash
year: 2025-2026
venue: Zewail City
mdc: true
lecture: 9
---

<!-- <style>
  h1 { color: #2c7be5; }
  .center { text-align: center; }
  img { max-width: 85%; border-radius: 6px; }
</style> -->

# Speech Recognition <br> (DSAI 456)
## Lecture 9

Mohamed Ghalwash
<Email v="mghalwash@zewailcity.edu.eg" />

---
layout: fact
---

# Recording is NOT allowed 

---
layout: top-title-two-cols
cols: is-6
---

:: title :: 

# Recap

:: left :: 

# HMM 
It requires the audio to be split into segments (characters, words, etc.) and then HMM would map each of these segments into their corresponding hidden state (phone, written words, etc.)

$$ \delta_t(j) = \max_{1 \leq i \leq N} \bigl[ \delta_{t-1}(i) a_{ij} \bigr] b_j(o_t) $$ 

![](./images/lec6_induction.png){width=50%}

:: right :: 

# CTC 

It is an alignment free but it will compute over all **possible alignments** to compute the likelihood of the output sequence

$$ \alpha_{s,t} = (\alpha_{s-1,t-1} + \alpha_{s,t-1}) . p_t(z_s | X) $$ 
$$ \alpha_t(s) = (\alpha_{t-1}(s-1) + \alpha_{t-1}(s)) . p_t(z_s | X) $$ 

![](./images/ctc_1.png)

