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
lecture: 6
slide:
  disableSlideNumbers: true
slide_info: false
---

# Speech Recognition <br> (Spring DSAI 456)
## Lecture 6

Mohamed Ghalwash
<Email v="mghalwash@zewailcity.edu.eg" />

---
layout: fact
---

# Recording is NOT allowed 

---
layout: top-title-two-cols
align: l-lt-cm
---

:: title :: 

# Lecture 5 Recap 

:: left :: 

- HMM : sequence of observed and hidden states
- HMM model $\lambda = (A, B, \pi)$
- Problems
  - Evaluation: $p(O ∣ \lambda)$
  - Decoder: $p(Q | O, \lambda)$
  - Learning: $\argmax_{\lambda} p(O|\lambda)$

:: right :: 

![alt text](./images/lec5_hmm.png)

---
layout: top-title 
---

:: title :: 

# Agenda 

:: content :: 

- Evaluation
- Decoder
- Learning

---
layout: top-title 
---

:: title :: 

# Evaluation Problem of HMM - Direct Computation

:: content :: 

$$
P(O \mid \lambda) = \sum_{all \, Q} P(O \mid Q, \lambda)P(Q|\lambda)
$$


<v-click>

$P(O \mid Q, \lambda) = b_{1}(o_1) \; . \; b_{2}(o_2) \; . \; b_{3}(o_3) \ldots b_{T}(o_T)$

$P(Q \mid \lambda) = \pi_1 \; . \; a_{12} \; . \; a_{23} \; . \; a_{34} \ldots a_{(T-1)T}$

Then 
$P(O, Q \mid \lambda) = \pi_{1} b_{1}(o_1) \prod_{t=2}^T a_{(t-1) t} b_{t}(o_t)$

</v-click>
<!-- <hr>  -->

<v-click>
<div class="ns-c-tight">

- Initially we are at time 1, we are in state $q_1$ with probability $\pi_{1}$
- Generate the symbol $o_1$ with probability $b_{1}(o_1)$
- Make a transition from state $q_1$ to state $q_2$ with probability $a_{12}$
- Generate the symbol $o_2$ with probability $b_{2}(o_2)$
- Continue until the last state 
  
</div>

</v-click>
<!-- <hr>  -->

<v-click>

==There are $N^T$ possible state sequences, each requires $2T$ calculations → exponential complexity==
</v-click>


---
layout: center
color: blue
--- 

## Can we find a faster algorithm to compute the likelihood? 

---
layout: top-title 
---

:: title :: 

# Evaluation Problem of HMM - Forward Algorithm

:: content :: 

<v-clicks>

A very nice trick is using **induction** or recursion

- Define probability of partial observation $o_1, o_2, \ldots o_t$ and being in state $i$ at time $t$ given $\lambda$ as 
$$ \alpha_t(i) = P(o_1, o_2, \ldots, o_t, q_t = i \mid \lambda) $$

- At last time point $T$: 
$$\alpha_T(i) = P(o_1, o_2, \ldots, o_T, q_T = i \mid \lambda) = p(O, q_T = i \mid \lambda) $$

- What we need is: 
$$ p(O\mid \lambda) = \sum_{i} p(O, q_T = i \mid \lambda) = \sum_{i}\alpha_T(i)$$
</v-clicks> 

<v-click> 

<span style="color:red;"> How to compute $\alpha_t(i)$ ? </span> <span style="color:green;"> inductively </span>
</v-click>


---
layout: top-title 
---

:: title :: 

# Evaluation Problem of HMM - Forward Algorithm 

:: content ::

<v-clicks> 

- Initialization: initialize the forward probabilities as the joint probability of state $i$ and initial observation $o_1$

$$
\alpha_1(i) = P(o_1, q_1 = i \mid \lambda) 
$$

<v-click>

$$
\alpha_1(i) = \pi_i b_i(o_1), \quad 1 \leq i \leq N
$$

</v-click>

<v-click>

- Assume $\alpha_t(i)$ is given, calculate $\alpha_{t+1}(j)$
</v-click>

<v-click>

- Induction: how state $j$ be reached at time $t+1$ from $N$ possible states at time $t$. 
Summation over all possible states $i$ at time $t$, transition to state $j$ at $t+1$, multiplied by emission probability at $t+1$
</v-click>


<div class="grid grid-cols-[3fr_1fr] gap-1 items-center">
  <div>
$$
\alpha_{t+1}(j) = \left( \sum_{i=1}^N \alpha_t(i) a_{ij} \right) b_j(o_{t+1}),
\quad 1 \leq j \leq N, \; 1 \leq t \leq T-1
$$
  </div>
  <div>

![](./images/lec6_induction.png){style="width:50%;"}
  </div>
</div>

</v-clicks> 


---
layout: top-title 
---

:: title :: 

# Evaluation Problem of HMM - Forward Algorithm 

:: content ::

<v-clicks> 

- Termination: Sum of probabilities over all states at final time

$$
P(O \mid \lambda) = \sum_{i=1}^N \alpha_T(i)
$$

- Computing $\alpha_t(i)$ using above steps enables efficient likelihood evaluation with complexity $O(N^2 T)$

</v-clicks> 


---
layout: fact
---

## Now we improved the time complexity of the likelihood evaluation $p(O\mid \lambda)$ from $N^TT$ to $N^2T$ using Forward algorithm (induction trick)

---
layout: center
class: text-center
---

# Learn More

[Course Homepage](https://github.com/m-fakhry/DSAI-456-SR)
