# Assignment 4

Due next week. Graded.

Reading: Rabiner (1989), Sections II and III.A (the elements of an HMM, the three problems, the forward procedure); J&M 3rd ed., Appendix A.1–A.3.

Use the *salaam* model from Lecture 4: two states /s/ → /a/, start in /s/ ($\pi = (1, 0)$), stay in /s/ with probability 0.5, never leave /a/, and emissions /s/: $P(h) = 0.8$, $P(v) = 0.2$; /a/: $P(h) = 0.2$, $P(v) = 0.8$.

1. **Forward algorithm.** Write `forward(pi, A, B, x)` in NumPy, in the **log domain** (use `scipy.special.logsumexp`), that returns the whole trellis of $\log \alpha_t(j)$. Run it on $X = (h, v, h, v)$ and check that you get the trellis from the lecture, with $\alpha_4(a) = 0.0704$.

2. **Check it two ways.**
   - Brute force: list every state sequence of length $T$, compute $P(X, Q \mid \lambda)$ for each one, and add up those that end in /a/. It must equal $\alpha_T(a)$.
   - Library: build the same model with `hmmlearn.hmm.CategoricalHMM` and call `score`. You will get $\log 0.0736$, not $\log 0.0704$. Explain the difference in one sentence.

3. **Timing.** For random sequences of length $T = 4, 8, 12, \dots$, time the brute force and your forward algorithm. Stop the brute force when one run takes more than a minute. Plot both times against $T$ (log scale on the time axis) and explain the shape of each curve.

4. **Underflow.** Run the forward algorithm on $X = (h, v)$ repeated 1000 times ($T = 2000$), once in the probability domain and once in the log domain. Show what each version returns and why.

5. **Recognize your own voice.** Record yourself saying "sa" (سا) and "as" (آس), once each, at 16 kHz.
   - Frame each recording as in Assignment 3 (25 ms window, 10 ms hop). Drop the silent frames (more than 35 dB below the loudest frame).
   - Turn each frame into a symbol: **h** if the energy above 4 kHz is larger than the energy below 1 kHz, **v** otherwise. Plot the symbols under the spectrogram and check that they make sense.
   - Build a second model for "as": the same two phones in the opposite order (start in /a/, then /s/).
   - Score each recording with both models. Which model wins for each recording, and by how much ($\log P$ difference)?

6. **Duration.** The coin (stay with probability 0.5) expects each phone to last about 2 frames. Count how many frames each phone really lasts in your recordings. Set the stay probability to $1 - 1/d$, where $d$ is that average length, and repeat Task 5. How does the margin between the two models change, and why?

Submit one notebook. Report the hardware you used and the wall-clock time for Task 3.
