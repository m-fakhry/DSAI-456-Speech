3. **EM by hand.** Write `em(x, mu, sigma, c, n_iter)` for a mixture of two 1-D Gaussians: the E-step computes the shares $r_{tm}$, and the M-step updates $\mu_m$, $\sigma_m$ and $c_m$.
   - Run it on the Activity 6 cards (1, 2, 3, 4, 5, 6, 12, 13, 14, 15), starting from $\mu = (1, 4)$, $\sigma = (2, 2)$ and $c = (0.5, 0.5)$. Plot the log-likelihood after every iteration: it must never go down.
   - Compare your final $\mu$, $\sigma$ and $c$ with `sklearn.mixture.GaussianMixture(n_components=2, means_init=[[1], [4]])`.
   - Replace the shares by 0 or 1 (each card goes to the nearer centre) and update only the centres. Check that you reproduce the rounds of the human k-means: centres (1.5, 9), then (3, 12), then (3.5, 13.5).

4. **GMMs on your own vowels.** Record yourself saying a long /aː/ and a long /iː/ (about 3 s each, 16 kHz). Compute 13 MFCCs per frame as in Assignment 3 (25 ms window, 10 ms hop) and drop the silent frames as in Assignment 4. Keep the last 20% of each vowel's frames for testing.
   - For each vowel, fit `GaussianMixture` with $M = 1, 2, 4, 8$ components, once with `covariance_type="diag"` and once with `"full"`. Plot the average log-likelihood of the test frames against $M$ for both.
   - Classify each test frame by which vowel's GMM gives it the higher score. Report the accuracy for diagonal and for full covariance.
   - Repeat with 40 log-mel energies instead of MFCCs ($M = 1$ and $2$ only). Does the gap between diagonal and full covariance grow? Connect your answer to the correlation figure from the lecture.
   - Plot $c_1$ against $c_2$ for both vowels, with the contours of the 2-component diagonal model.

5. **Forced alignment** (demonstrated at the start of the lab). Run Montreal Forced Aligner on a recording of *salaam* (your own voice, or a classmate's with their consent) and open the TextGrid in Praat.
   - Where does /l/ start? Compare it with the class's Slido guesses from Lecture 4 (Activity 1).
   - How long are /a/ and /aː/, in ms, and what is the ratio?
   - If MFA's Arabic model is not available in your version, align an English sentence instead (`english_mfa`) and compare a short and a long vowel.

6. **Explore.** Open `lectures/public/trellis.html` (Trellis Lab) from the course repository in your browser. In the Sum vs Max tab, find your own pair of words that the forward score and the Viterbi score rank differently; do not use "Show me one". Report the observations and both words' settings, and explain in two sentences why the two scores disagree.
