# Assignment 2

## Reading 

- Read Sections 14.5, 14.6 from the main book
- Watch videos 5,6, and 16 from the _Audio Signal Processing for ML_ tutorial 

## Implementation 

- Write  python program to perform the following tasks: 
  - Record or use given speech audio samples
  - Compute the frequency spectrum of the speech signals using the Fast Fourier Transform (FFT)
  - Plot the frequency spectrum as well as the original waveform along with the sinusoidal components
  - Identify and discuss dominant frequencies and fundamental frequency (F0) for different spoken words or phonemes
  - Generate spectrograms by applying Short-Time Fourier Transform (STFT) on speech signals
  - Plot the spectrogram along with the spoken words (each word is written under each block in spectrogram)
  - Plot and interpret spectrograms and discuss formant patterns and phoneme distinctions
  - Explore different window sizes and overlaps and analyze their effect on time-frequency resolution

- Comparative Analysis of Male and Female Speech Using Mel Spectrograms and Mel Filter Banks: Let's assume that you are provided with two audio files: one recording of a male speaker and one recording of a female speaker speaking the exact same short sentence "the quick brown fox jumps over the lazy dog".
  - Records this sentence twice, once by a male and once by a female.
  - Load both audio files and preprocess them as needed.
  - Compute the Mel spectrograms of both audio signals.
  - Extract and visualize the Mel filter banks used in the spectrogram computation.
  - Compare the Mel spectrograms of the male and female speakers by analyzing differences in spectral energy distribution, fundamental frequency (F0) regions, and formant patterns.
  - Discuss the acoustic differences evident in the Mel spectrograms.
  - Reflect on how such spectral differences are relevant to speech recognition and speaker identification systems.
