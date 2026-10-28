# Assignment 5

Due next week. Not graded.

Reading: Rabiner (1989), the solution to Problem 2 (the Viterbi algorithm) and the section on continuous observation densities (mixtures of Gaussians); J&M 3rd ed., Appendix A.4.

Use the *salaam* model from Lectures 4 and 5: two states /s/ → /a/, start in /s/ ($\pi = (1, 0)$), stay in /s/ with probability 0.5, never leave /a/, and emissions /s/: $P(h) = 0.8$, $P(v) = 0.2$; /a/: $P(h) = 0.2$, $P(v) = 0.8$. The word must end in /a/.

1. **Viterbi.** Write `viterbi(pi, A, B, x)` in NumPy, in the **log domain**, that returns the trellis of $\log \delta_t(j)$, the backpointers $\psi_t(j)$ and the best path that ends in /a/. Run it on $X = (h, v, h, v)$ and check that you get $\delta_4(a) = 0.0512$ and the path s | a a a from the lecture. Transitions with probability 0 become $-\infty$ in the log domain: make sure your code handles them without warnings.

2. **Check it two ways.**
   - Brute force: list every state sequence that ends in /a/ and keep the one with the largest $P(X, Q \mid \lambda)$. Its probability must equal $\delta_T(a)$ and its sequence must equal your backtrace. Then plant bug B from Activity 3 (read $\psi$ one column too early) in a copy of your backtrace. Does the brute-force check catch it?
   - Library: build the same model with `hmmlearn.hmm.CategoricalHMM` and call `decode(..., algorithm="viterbi")`. On $X = (h, v, h, v)$ it agrees with you. Now run both on $X = (h, h, h, h)$. What does hmmlearn return, and why is it not an alignment of the word? Explain the difference in one sentence.

Submit one notebook. Report the hardware you used and the wall-clock time for Task 4.
