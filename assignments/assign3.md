# Assignment 3

## Reading 

- Read Chapter 2 from the supplementary book 
- Read Sections 11.1, 11.2, 11.3 from the "Mathematics For Machine Learning, by Deisenroth, Faisal, Ong, 2019" book, it has a very nice explanation about GMM.

## Implementation 

**GMM for Speaker Identification**

- Objectives:
  The objective of this assignment is to implement the EM algorithm to build GMMs for speaker recognition. We need to gain skills on how to implement an iterative algorithm. 

- Dataset:
The VCTK Corpus is a multi-speaker English speech dataset designed for building speaker recognition systems. It consists of recordings from 110 speakers with various English accents. Each speaker reads approximately 400 sentences selected from different sources. Samples per speaker are single sentences which makes it suitable for a classification task where a GMM can be trained per speaker from their many utterances.

- Task
  - Download the dataset from Kaggle 
  - Extract features like MFCCs or Mel filter bank features from the raw audio
  - Implement (not use the gaussian mixture model in sklearn or any other library) the EM algorithm as in slide 22 in lecture 4. 
  - Train a GMM model for each speaker (class) using EM algorithm on their feature distributions 
  - Evaluate test samples by computing the likelihood of each sample under each GMM and assign to the speaker with highest likelihood