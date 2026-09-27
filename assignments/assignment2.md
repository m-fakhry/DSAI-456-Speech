# Assignment 2

Due next week. Graded. 

Reading: J&M 3rd ed., Ch. 16.1–16.2.

Use your own recording from Assignment 1 (the sentence you recorded and computed WER on).

1. Write a python program that loads your recording and plots, aligned on the same time axis: the waveform, short-time (RMS) intensity, and an F0 contour. Mark which regions are voiced and which are unvoiced.

2. Pick 2–3 vowels from your sentence. For each, measure F1 and F2 (using librosa).

3. Generate a spectrogram of your full sentence and hand-annotate it: mark formant bands, consonant bursts, and silence.

4. Downsample your recording to 8 kHz and then 4 kHz, and separately requantize it to 8-bit and then 4-bit. Re-run each degraded version through the same ASR system you used in Assignment 1, and recompute WER for each.

5. Make two graphs. One shows WER at each sampling rate (16k, 8k, 4k). The other shows WER at each bit depth (16-bit, 8-bit, 4-bit). Listen to each degraded recording yourself. Find the point where you first notice it sounds worse. Look at your WER graph. Find the point where WER jumps up a lot, not just a little. Compare the two points. Ask: does the recording start sounding bad at the same place where the ASR system starts failing? Or does one happen before the other?
