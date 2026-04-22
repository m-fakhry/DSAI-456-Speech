#  Speech Recognition (DSAI 456) - 2025-2026

Repository for the Speech Recognition undergraduate course (DSAI 456) for the 2025-2026 academic year at Zewail City University. 

---

### Logistics

Course | Speech Recognition - DSAI 456
---|----
Webpage| [https://github.com/m-fakhry/DSAI-456-Speech](https://github.com/m-fakhry/DSAI-456-Speech)
Structure | 2-hour lecture (Tue 10-12) and 3-hour lab (Sun 11-2, Thu 8-11)
TAs | Ahmed Aamer
Book | "_Speech and Language Processing_", Jurafsky and Martin, 3rd Edition, 2025
Supplementary Book| "_Automatics Speech Recognition, A Deep Learning Approach_", Yu and Deng, 2015 
Objectives | Provide students with foundational knowledge and practical skills in the theory and application of speech processing and recognition. It covers both traditional statistical approaches and modern deep learning techniques to design, implement, and evaluate speech recognition systems.
Prerequitstis | Deep Learning, PyTorch, Python
Tools/APIs |  [librosa](https://librosa.org/doc/latest/index.html), [pyAudioAnalysis](https://github.com/tyiannak/pyAudioAnalysis), [torchaudio](https://github.com/pytorch/audio), [openSmile](https://audeering.github.io/opensmile/), [senselab](https://github.com/sensein/senselab)
Tutorials | [Audio Signal Processing for ML, by Valerio Velardo](https://www.youtube.com/playlist?list=PL-wATfeyAMNqIee7cH3q1bh4QJFAaeNv0)
Lab Policy| Assignments and quizzes

---

### Lectures

Week| Date |Topic | Contents | Lecture | Assignment
---|---|---|---|---|---
1| 02-10 | | | | 
2| 02-17 | Foundations and Acoustic Features | What is speech recognition, phonetics and signals, frequency, amplitude, period, analog to digital, sampling and quantization, pitch, intensity, discrete and fast Fourier transform,  time and frequency domain, freq spectrum, spectrogram, Mel scale  | [Lecture 1](lectures/lec1.md) | [Assignment 1](assignments/assign1.md) 
3| 02-24 | Acoustic Features | Discrete and fast Fourier transform, time and frequency domain, freq spectrum, spectrogram, Mel scale, Mel filter bank, windowing, MFCC | [Lecture 2](lectures/lec2.md) | [Assignment 2](assignments/assign2.md) 
4| 03-03 | GMM | Definition of Gaussian, univariate distribution, one distribution for each class, GMM | [Lecture 3](lectures/lec3.md) | No assignment 
5| 03-10 | GMM | difference between univariate and multivariate, single and mixture of distribution, distribution for each class, number of mixtures for each class | [Lecture 4](lectures/lec4.md) | [Assignment 3](assignments/assign3.md) 
6| 03-17 | GMM + HMM | EM algorithm, problems of HMM, Evaluation problem| [Lecture 5](lectures/lec5.md) | [Assignment 4](assignments/assign4.md)
7| 03-24 | Eid | | | 
8| 03-31 | Midterm | | | 
9| 04-07 | Midterm review | reviewing the midterm exam |  | [Assignment 5](assignments/assign5.md)
10| 04-14 | HMM | Direct computation, the forward algorithm | [Lecture 6](lectures/lec6.md)  | [Assignment 6](assignments/assign6.md)
11| 04-21 | Quiz | lecture quiz + review the quiz | No lecture | No assignment  
12| 04-28 | Lab Quiz + Decoding | Decoding (Habiba Ayman?) | | 
13| 05-05 | CTC + Encodec + VALLE | | | 
14| 05-12 | Lab Final | | | 
15| 05-19 | Prepare for Final | | |  

Please note that the syllabus content is subject to change throughout the semester. Topics may be added or removed based on the instructor’s discretion, student progress, and available time. Your feedback and participation will inform these adjustments to ensure alignment with course goals and schedule constraints.

--- 

### Grading Policy 

Topic| Percentage | Notes
---|---|---
Lab Assignments | 15% | 
Lab Quizzes | 5% | 
Lecture Quizzes | 10% | 
Final Lab | 10% | 
Midterm | 20% | 
Final | 40% | 
