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
lecture: 8
slide:
  disableSlideNumbers: true
slide_info: false
---

# Speech Recognition <br> (Spring DSAI 456)
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

# Lecture 7 Recap 

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
