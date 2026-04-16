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
lecture: 7
slide:
  disableSlideNumbers: true
slide_info: false
---

# Speech Recognition <br> (Spring DSAI 456)
## Lecture 7

Mohamed Ghalwash
<Email v="mghalwash@zewailcity.edu.eg" />

---
layout: fact
---

# Recording is NOT allowed 

---
layout: top-title-two-cols
align: l-lt-cm
columns: is-6
---

:: title :: 

# Lecture 6 Recap 

:: left :: 

- HMM : sequence of observed and hidden states
- HMM model $\lambda = (A, B, \pi)$
- Problems
  - **Evaluation**: $p(O ∣ \lambda)$
    - Direct Computation $O(TN^T)$
    - Forward Algorithm $O(TN^2)$
  - **Decoder**: $p(Q | O, \lambda)$
  - **Learning**: $\argmax_{\lambda} p(O|\lambda)$

:: right :: 

![](./images/lec5_hmm.png)

---
layout: cover 
--- 

# The Decoding Problem $p(Q | O, \lambda)$
#### Find the most likely sequence of hidden states that produced a given sequence of observations

---
layout: top-title
---

:: title ::

# The HMM Decoding Problem

:: content ::

Given an observation sequence $O = (o_1, o_2, \ldots, o_T)$ and model $\lambda$, find the most likely state sequence $Q = (q_1, q_2, \ldots, q_T)$

<br/>
<v-click>

Define the highest probability of a state sequence ending in state $i$ at time $t$ generating observations $o_1, \ldots, o_t$ as:

$$
\delta_t(i) = \max_{q_1, \ldots, q_{t-1}} P(q_1, q_2, \ldots, q_{t-1}, q_t = i, o_1, o_2, \ldots, o_t \mid \lambda)
$$

</v-click>

<v-click>

==In this case, our objective is to compute $\delta_T(i)$==

</v-click>

<v-click>You got it right! 👍  use Induction</v-click>



---
layout: top-title
---

:: title :: 

# Viterbi Algorithm

:: content :: 

<v-click>

- Initialization:  the highest probability along a single path, at time 1, which accounts for the first observation $o_1$ and ends in state $i$ 

$$\delta_1(i) = \pi_i b_i(o_1), \quad 1 \leq i \leq N $$
<!-- - and keep track of the back pointers: -->

<!-- $$
\begin{align*}
\delta_1(i) &= \pi_i b_i(o_1), \quad 1 \leq i \leq N \\
\psi_1(i) &= 0
\end{align*}
$$ -->

</v-click>

<v-click>

- Assume $\delta_t(i)$ is given, calculate $\delta_{t+1}(j)$
</v-click>

<v-click>

- Induction (for $t=2, \ldots, T$):

$$
\delta_{t+1}(j) = \max_{1 \leq i \leq N} \; \bigl[ \delta_{t}(i) a_{ij} \bigr] b_j(o_t), \quad 1 \leq j \leq N 
$$


<!-- $$
\begin{align*}
\delta_t(j) &= \max_{1 \leq i \leq N} \bigl[ \delta_{t-1}(i) a_{ij} \bigr] b_j(o_t), \quad 1 \leq j \leq N \\ 
\psi_t(j) &= \arg\max_{1 \leq i \leq N} \bigl[ \delta_{t-1}(i) a_{ij} \bigr]
\end{align*}
$$ -->

</v-click>

<v-click>

- Termination:
$$
P^* = \max_{1 \leq i \leq N} \delta_T(i)
$$

<!-- $$
\begin{align*}
P^* &= \max_{1 \leq i \leq N} \delta_T(i) \\
q_T^* &= \arg\max_{1 \leq i \leq N} \delta_T(i)
\end{align*}
$$ -->

</v-click>

<v-click>
<div style="text-align: center;">

[Where is the state sequence? 😢]{.decoration-4.underline.decoration-pink-500.bg-red-200}
</div>
</v-click>

<!-- Backtrack from $q_T^*$ to $q_1^*$ using $\psi_t(i)$ to get the most probable state sequence. -->

---
layout: fact
---

### We need to keep track of selected states along the path 

---
layout: top-title
---

:: title :: 

# Viterbi Algorithm

:: content :: 

<v-click>

- Initialization 
$$
\begin{align*}
\delta_1(i) &= \pi_i b_i(o_1), \quad 1 \leq i \leq N \\
\psi_1(i) &= 0
\end{align*}
$$
</v-click>

<v-click>

- Induction
$$
\begin{align*}
\delta_t(j) &= \max_{1 \leq i \leq N} \bigl[ \delta_{t-1}(i) a_{ij} \bigr] b_j(o_t), \quad 1 \leq j \leq N \\ 
\psi_t(j) &= \arg\max_{1 \leq i \leq N} \bigl[ \delta_{t-1}(i) a_{ij} \bigr]
\end{align*}
$$
</v-click>

<v-click>

- Termination
$$
\begin{align*}
P^* &= \max_{1 \leq i \leq N} \delta_T(i) \\
q_T^* &= \arg\max_{1 \leq i \leq N} \delta_T(i)
\end{align*}
$$
</v-click>

<v-click>

==Backtrack from $q_T^*$ to $q_1^*$ using $\psi_t(i)$ to get the most probable state sequence==
</v-click>

--- 
layout: fact
---

### The Viterbi algorithm efficiently solves the decoding problem with complexity $O(N^2 T)$


---
layout: center
class: text-center
---

# Learn More

[Course Homepage](https://github.com/m-fakhry/DSAI-456-SR)
