# Assignment 7

## Implementation 

**HMM for Word Recognition**

- Objectives:
    The objective of this assignment is to implement the Viterbi algorithms to build HMM for word recognition. We need to gain skills on how to implement a dynamic programming algorithm. 

- Dataset:
    The [TIMIT Acoustic-Phonetic Continuous Speech Corpus](https://catalog.ldc.upenn.edu/LDC93S1) contains recordings of phonetically rich sentences spoken by 630 speakers across 8 major American English dialects. It provides detailed manual phoneme-level alignments with precise start and end times for training HMMs to model phoneme sequences accurately. It also  includes predefined training, development, and test sets for reproducible experiments and model comparisons.

- Experiment Setup:
  You need to prepare the dataset with the following considerations
  - The observable sequence consists of acoustic feature vectors extracted from audio files where each file contains a single spoken word. The audio waveform is segmented such that the start and end times of each phoneme are marked and used
  - The hidden state corresponds to a phoneme. You need to keep in mind that multiple phonemes can map to a single character, and conversely, a single phoneme can correspond to multiple characters
  - The HMM models the probabilistic relationship between the hidden phoneme states and the observed acoustic features
  - During training, audio is aligned with phoneme transcriptions, and the model learns the parameters to decode phonemes or words from audio features

- Task:
  - Download the dataset 
  - Extract features like MFCCs or Mel filter bank features from the raw audio
  - Call the HMM train function using [hmmlearn](https://hmmlearn.readthedocs.io/en/latest/) library
  - Inspect the model, by looking at the transition matrix, emission matrix, and initial states
  - Implement **your own** version of the Viterbi algorithm (do not use the hmmlearn library for this function)
  - Apply your own Viterbi implementation to compute the most likely hidden sequence of phonemes that generated a given word (audio)

