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
lecture: 8
---

<!-- <style>
  h1 { color: #2c7be5; }
  .center { text-align: center; }
  img { max-width: 85%; border-radius: 6px; }
</style> -->

# Speech Recognition <br> (DSAI 456)
## Lecture 8

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

# Lecture 5 Recap 

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
layout: top-title
---

:: title ::

# The Backward Algorithm of HMM

:: content ::

- The backward algorithm helps evaluate the probability of the ending partial observation sequence, given state $i$ at time $t$.

<v-click>

- Define:

$$
\beta_t(i) = P(o_{t+1}, o_{t+2}, \ldots, o_T \mid q_t = i, \lambda)
$$

which is the probability of observing the partial sequence from $t+1$ to $T$ given state $i$ at time $t$.

</v-click>

---

<v-click>

- Initialization at $t = T$ (end time):

$$
\beta_T(i) = 1, \quad \forall i = 1, 2, \ldots, N
$$

since after the last observation, the probability of the empty future observation sequence is 1.

</v-click>

<v-click>

- Recursion for $t = T-1, T-2, \ldots, 1$:

$$
\beta_t(i) = \sum_{j=1}^N a_{ij} b_j(o_{t+1}) \beta_{t+1}(j)
$$

where $a_{ij}$ is the state transition probability from state $i$ to $j$, and $b_j(o_{t+1})$ is the emission probability of observing $o_{t+1}$ in state $j$.

</v-click>

<v-click>

- Termination step:

$$
P(O \mid \lambda) = \sum_{i=1}^N \pi_i b_i(o_1) \beta_1(i)
$$

which sums over initial states weighted by initial probabilities $\pi_i$, emission probabilities, and the backward probabilities.

</v-click>

---

<v-click>

- The backward algorithm runs in time $O(N^2 T)$ and complements the forward algorithm for smoothing tasks and parameter estimation.

</v-click>

---
layout: top-title
---

:: title ::

# Baum-Welch Algorithm - Training the HMM

:: content ::

- The Baum-Welch algorithm solves the learning problem of finding unknown model parameters $\lambda = (A, B, \pi)$ given observed data $O$.

<v-click>

- It is a special case of the Expectation-Maximization (EM) algorithm that uses the forward-backward procedure to estimate expected sufficient statistics.

- Define the forward variables $\alpha_t(i)$ and backward variables $\beta_t(i)$ for each time $t$ and state $i$ (see previous slides).

</v-click>

---

<v-click>

- Compute the $\gamma$ variables:

$$
\gamma_t(i) = P(q_t = i \mid O, \lambda) = \frac{\alpha_t(i) \beta_t(i)}{\sum_{j=1}^N \alpha_t(j) \beta_t(j)}
$$

which represent the posterior probability of being in state $i$ at time $t$.

</v-click>

<v-click>

- Compute the $\xi$ variables, joint posterior of being in state $i$ at $t$ and state $j$ at $t+1$:

$$
\xi_t(i,j) = P(q_t = i, q_{t+1} = j \mid O, \lambda) = \frac{\alpha_t(i) a_{ij} b_j(o_{t+1}) \beta_{t+1}(j)}{\sum_{i=1}^N \sum_{j=1}^N \alpha_t(i) a_{ij} b_j(o_{t+1}) \beta_{t+1}(j)}
$$

</v-click>

---

<v-click>

- Update parameters using the expected counts:

$$
\begin{aligned}
\pi_i^{new} &= \gamma_1(i) \\
a_{ij}^{new} &= \frac{\sum_{t=1}^{T-1} \xi_t(i,j)}{\sum_{t=1}^{T-1} \gamma_t(i)} \\
b_j^{new}(k) &= \frac{\sum_{t=1}^{T} \textbf{1}_{\{o_t = v_k\}} \gamma_t(j)}{\sum_{t=1}^{T} \gamma_t(j)}
\end{aligned}
$$

where $v_k$ is the observation symbol $k$.

</v-click>

<v-click>

- Repeat these E and M steps iteratively until convergence to locally maximize $P(O \mid \lambda)$.

- The Baum-Welch algorithm efficiently trains HMM parameters from data, enabling practical applications like speech recognition.

</v-click>


---
layout: center
class: text-center
---

# Learn More

[Course Homepage](https://github.com/m-fakhry/DSAI-456-SR)
