# Assignment 3

Due next week. Graded. 

Reading: J&M Ch. 15.5.2–15.6 (windowing, DFT, mel filter bank and log, MFCC); review Ch. 15.4.5 from last week.

In the lab you will build the pipeline from this lecture.

1. Frame and window a recording yourself (NumPy only): check the frame count against the formula.
2. Compute the DFT per frame and compare with `librosa.stft`. It returns bins × frames and pads by default (`center=False` and `n_fft=512`).
3. Mel filterbank: build the triangular filters and apply them then take the log.
4. MFCC: keep 13 coefficients and add Δ and ΔΔ.
5. Explore: vary the window length and the window type and describe what changes.
