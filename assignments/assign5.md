# Assignment 5

## Paper

**HMM using Direct Computation**

- Objectives:
  - Understand the hidden state vs. observation relationship.
  - Manually compute the probability of a sequence via path summation.


- Scenario:
    You are given a simplified Hidden Markov Model (HMM) representing a specific phoneme. The model has two hidden states and a discrete vocabulary of two observation symbols
    - States: $S_1$ (Acoustic Transition), $S_2$ (Steady State)
    - Observations: $O = \{A, B\}$
    - Initial State Probabilities ($\pi$):
      - $\pi(S_1) = 0.8$
      - $\pi(S_2) = 0.2$
    - Transition Probability Matrix ($A$):
  
        | From \ To | $S_1$ | $S_2$ |
        | :--- | :--- | :--- |
        | $S_1$ | $0.6$ | $0.4$ |
        | $S_2$ | $0.3$ | $0.7$ |

    - Emission Probabilities ($B$):

        | State | $P(A \mid S_i)$ | $P(B \mid S_i)$ |
        | :--- | :--- | :--- |
        | $S_1$ | $0.7$ | $0.3$ |
        | $S_2$ | $0.4$ | $0.6$ |

- Task: You need to calculate the total probability of observing the sequence **$O = \{A, B, A\}$** using direct path summation.
  - For a sequence of length $T=3$ and a model with $N=2$ states, how many possible state sequences (paths) exist? List them all using state indices (e.g., $1-1-1, 1-1-2, \ldots$).
  - Calculate the joint probability of the observation $O$ and the following two specific paths. Show your full calculation (all multiplications) for $Q = \{S_1, S_1, S_1\}$
  - The total probability $P(O \mid \lambda)$ is the sum of the probabilities of all possible paths. If the sum of the probabilities of the remaining 6 paths is calculated to be **$0.0542$**, what is the final total probability of the observation sequence?  _(Use your results from Question 2 to complete the sum)_
  - A typical speech signal might be processed into $T=100$ frames. 
    - Calculate how many total paths would exist if $T=100$ and $N=2$. (Leave your answer in exponential form).
