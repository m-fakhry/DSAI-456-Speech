# Speech Recognition (DSAI 456) - 2026-2027

Repository for the Speech Recognition undergraduate course (DSAI 456) for the 2026-2027 academic year at Zewail City University.

This year the course
- transitions the focus from traditional statistical ASR systems to modern neural speech architectures.
- adds a class project.

---

### Previous Offerings

- [Spring 2025-2026](https://github.com/m-fakhry/DSAI-456-Speech/tree/spring2526)
- [Fall 2025-2026](https://github.com/m-fakhry/DSAI-456-Speech/tree/fall2526)

---

### Logistics

Course | Speech Recognition - DSAI 456
---|----
Webpage| [https://github.com/m-fakhry/DSAI-456-Speech](https://github.com/m-fakhry/DSAI-456-Speech)
Instructor | Prof. Mohamed Ghalwash (mghalwash@zewailcity.edu.eg)
Structure | 2-hour lecture (Mon 8-10) and 2-hour lab (Mon 10-12, Tue 12-2, Tue 4-6)
TAs | Eng. Ahmed Aamer
Communication | Moodle or Email or office hours. **no phone, no whatsapp**
Lab Policy| Assignments, quizzes, and project milestones
Book | "_Speech and Language Processing_", Jurafsky and Martin, 3rd Edition, 2025
Supplementary | [HuggingFace Audio Course](https://huggingface.co/learn/audio-course)
Objective | Provide students with the theory and practical skills to build, adapt, and evaluate modern speech systems (recognition and synthesis), and to read the current literature critically
Prerequisites | Deep Learning
Tools/APIs | [librosa](https://librosa.org/doc/latest/index.html), [HuggingFace Transformers](https://github.com/huggingface/transformers) + [PEFT](https://github.com/huggingface/peft). Optional: [openSmile](https://audeering.github.io/opensmile/), [torchaudio](https://github.com/pytorch/audio), [NeMo](https://github.com/NVIDIA/NeMo) or [ESPnet](https://github.com/espnet/espnet)

---

### Course Learning Outcomes

CLO \# | Outcome | Statement
---|---|---
1 | Analyze Speech Signals | Explain the mathematical foundations of digital audio, including sampling, quantization, and the transformation of signals from the time domain to the frequency domain
2 | Extract Acoustic Features | Implement and evaluate feature extraction pipelines, specifically log-mel spectrograms and Mel-Frequency Cepstral Coefficients (MFCCs), for speech processing tasks
3 | Model Temporal Sequences | Apply dynamic programming over sequences, specifically the Forward and Viterbi algorithms, to align audio with text, using GMM-HMM systems as the classical case
4 | Develop and Adapt Neural ASR Systems | Design and implement modern End-to-End speech recognition architectures, including Connectionist Temporal Classification (CTC), transducer, and Encoder-Decoder frameworks, and fine-tune pretrained models for new languages and domains under realistic label budgets
5 | Build Generative Speech Systems | Explain neural audio codecs and token-based synthesis, and implement speech generation systems
6 | Evaluate & Appraise Research | Evaluate speech systems empirically against baselines, including accuracy-latency trade-offs, and critically appraise contemporary research in speech and audio AI, including its limitations and ethical implications

---

### Lectures

Papers in the Paper column are required reading. Individual papers are not graded, but the midterm and the final each include one question asking you to appraise an assigned paper - to take a position, predict a result, or propose the experiment that would settle a disagreement between two of them. Summaries will not earn marks.

Please note that the syllabus content is subject to change throughout the semester. Topics may be added or removed based on the instructor's discretion, student progress, and available time. Your feedback and participation will inform these adjustments to ensure alignment with course goals and schedule constraints.

Week| Date |Topic | Contents | Paper | CLO | Lecture | Assignment
---|---|---|---|---|---|---|---
1 | 09-21 | Intro | General introduction to the course. WER/CER metrics. |  Browse [Open ASR Leaderboard](https://huggingface.co/spaces/hf-audio/open_asr_leaderboard) as a benchmark | 6 | [Lecture 1](lectures/lecture1.md) | [Assignment 1](assignments/assignment1.md)
2 | 09-28 | Foundations | Formants, quantization, framing, F0 and intensity, spectrogram, sampling and Nyquist.  | Ch. 16.1-16.2 | 1 | | 
3 | 10-05 | Spectral Front End | DFT/FFT, windowing and spectral leakage, time-frequency resolution, STFT and spectrogram, mel filterbank, log-mel. MFCC | Ch. | 1, 2 | | 
4 | 10-12 | Alignment & Decoding | The alignment problem, HMM, forward algorithm, Viterbi, GMM as a density model.| [Rabiner (1989), _A Tutorial on Hidden Markov Models_](https://ieeexplore.ieee.org/document/18626) | 3 | | **Project proposal**
5 | 10-19 | CTC | Blank symbol, collapse function, summing over alignments, forward-backward, prefix beam search, shallow LM fusion | [Graves et al. (2006), _Connectionist Temporal Classification_](https://www.cs.toronto.edu/~graves/icml_2006.pdf) | 3, 4 | | 
6 | 10-26 | Encoders & Transducers | CNN, BiLSTM, Transformer. RNN-T (encoder + prediction + joint network), Conformer/FastConformer, subsampling, chunked attention and causality | [Graves (2012), _Sequence Transduction with RNNs_](https://arxiv.org/abs/1211.3711); [Gulati et al. (2020), _Conformer_](https://arxiv.org/abs/2005.08100) | 4 | | 
7 | 11-02 | Self-Supervised Learning | Why labels are the bottleneck, wav2vec 2.0 (masking, quantized targets, contrastive loss), HuBERT (offline clustering, masked prediction), WavLM, low-resource fine-tuning | [Baevski et al. (2020), _wav2vec 2.0_](https://arxiv.org/abs/2006.11477); [Hsu et al. (2021), _HuBERT_](https://arxiv.org/abs/2106.07447) | 4 | | **Data + evaluation protocol + pretrained baseline**
8 | 11-09 | **Midterm** | | | 1, 2, 3, 4 | |
9 | 11-16 | Weak Supervision at Scale | Attention encoder-decoder, cross-attention, Whisper's multitask token format, hallucination and repetition, long-form chunking, the scale-vs-curation debate | [Radford et al. (2023), _Whisper_](https://arxiv.org/abs/2212.04356); [Puvvada et al. (2024), _Less is more_](https://arxiv.org/abs/2406.19674) | 4, 6 | | 
10 | 11-23 | Neural Audio Codecs | VQ-VAE, straight-through estimator, codebook collapse, residual vector quantization, EnCodec, semantic vs acoustic tokens | [Défossez et al. (2022), _EnCodec_](https://arxiv.org/abs/2210.13438) | 5 | | **Working system + training curves**
11 | 11-30 | TTS as Language Modelling | VALL-E's two-stage AR + NAR recipe, zero-shot voice cloning from a 3-second prompt, instability and duration control, flow-matching alternatives, vocoders, MOS and speaker similarity | [Wang et al. (2023), _VALL-E_](https://arxiv.org/abs/2301.02111) | 5, 6 | | 
12 | 12-07 | Speech LLMs | Speech encoder + projector + LLM, what is frozen and what is trained, prompt-conditioned ASR, spoken QA and audio understanding, why a large LLM does not automatically lower WER | [Tang et al. (2023), _SALMONN_](https://arxiv.org/abs/2310.13289); [Qwen3-Omni](https://github.com/QwenLM/Qwen3-Omni) | 5, 6 | | 
13 | 12-14 | **Project Demos** | Team presentations and evaluation | - | 4, 5, 6 | | **Final report due (all teams)**
14 | 12-21 | **Project Demos** | Team presentations and evaluation | - | 4, 5, 6 | | 
15 | 12-28 | **Project Demos** | Team presentations and evaluation | - | 4, 5, 6 | | 
16 | | **Final** | | | all | |


---


### Class Project

- Teams of 3-4 propose a novel speech application and build a working system around it.
<!-- Full specification in [project/README.md](project/README.md). -->

- **Arabic data is highly preferred.** Modern and dialectal Arabic, code-switched Arabic-English, and Egyptian speech in particular are underserved by current models, and a project that improves on a pretrained baseline there is doing something that has not already been done a hundred times in English. Arabic is not a hard requirement, but a non-Arabic project has to carry its weight through a stronger idea.

- **The idea matters as much as the implementation.** A project is novel if it targets a task, a user group, a dialect, or a setting that existing systems handle badly, or if it combines components in a way the literature has not. It is not novel if it fine-tunes a standard model on a standard benchmark and reports the expected number. You do not need a research contribution - you need a reason the thing you built should exist.

<!-- - Some project ideas: dialectal and code-switched ASR, dysarthric and atypical speech, Qur'anic recitation and tajweed feedback, classroom and lecture transcription, call-centre analytics, pronunciation training for language learners, voice interfaces for low-literacy users, dialect-preserving TTS, speech-driven accessibility tools. -->

- Every project must have: a defined task and evaluation metric, a held-out test set the team did not tune on, a pretrained baseline, a system that improves on that baseline, honest failure analysis, and a working demo.

- The final report must open with a positioning section: what already exists for this task, where it falls short for your case, and what you did differently. Cite real systems and papers, not a general description of the field. How you weight research depth against engineering polish is up to the team and should be stated in the proposal.

- Teams are encouraged, but not required, to find a mentor or a real user, who is someone has the problem and will tell you whether your output is any good. A linguist, a teacher, a clinician, a call-centre supervisor. Their feedback is worth more than another epoch of training.

- Milestones

    Week | Deliverable
    ---|---
    4 | Proposal: the idea, why it is needed, dataset plan, evaluation metric
    7 | Data (with consent documentation where applicable), evaluation protocol, pretrained baseline results
    10 | Working system with training curves and error analysis
    13 | Final report, due for all teams regardless of demo slot; demos run weeks 13-15

---

### Grading Policy

Topic| Percentage | Notes
---|---|---
Lab Assignments | 20% | Graded in lab with your TA
Lab Quizzes | 10% | Weeks 6 and 12
Class Project | 20% | Distributed across the four milestones
Midterm | 10% | Covers weeks 1-7, including questions on the assigned papers
Final | 40% | Includes question on the assigned papers

---

### Course Instructions

Principle: deadlines are firm.

**Submissions**

- All assignments must be uploaded to the Moodle system before the deadline, even if the assignment has already been graded in the lab.
- Assignment grades depend on discussing your work with your TA. There are no extensions on these discussions: if you miss the discussion for an assignment, you lose its grade.
- Any assignment involving model training must report the hardware used and the wall-clock training time. "It did not converge" is a result; report it with evidence.

**Excuses and make-up tasks**

- Medical excuses must be submitted within one week of the excused task (assignment, quiz, or midterm). Excuses submitted after that window will not be considered.
- Make-up tasks cover the material taught up to the date of the make-up, not the material of the original task.

**Grade petitions**

- Once coursework grades (assignment, quiz, etc.) are posted, you have one week to raise an issue. If you believe there is an error in your grade, email me and CC your TA with:

  1. A clear and detailed explanation of exactly why you are petitioning the grade.
  2. Any relevant and approved documentation supporting your request, if the petition concerns a missed assignment, quiz, or exam.

- No grade adjustments will be considered after this deadline, and petitions that do not follow the format above will not be reviewed.

---

### Policies

**Use of AI tools.** You may use AI assistants for debugging, visualization, and boilerplate. You may not use them to produce your implementations, your error analysis, or your written analysis. Running a pretrained speech model is the subject of this course and is always allowed; having a model write your analysis of it is not. Disclose any AI assistance in your submission.

**Voice data, consent, and cloning.** Any recording of another person requires their informed consent, including consent for how the recording will be stored and who will hear it. Do not synthesize any identifiable person's voice without their written permission, and never for content they did not agree to say. Project datasets involving human subjects need a consent statement at the week 7 milestone. This is a course requirement, not a formality: it is the same standard the field is currently failing to meet.

**Academic integrity.** Standard Zewail City policy applies. Project code must be your team's own; pretrained models, third-party datasets, and libraries are permitted and must be cited with their licence.

---

### Resources

- [HuggingFace Audio Course](https://huggingface.co/learn/audio-course)
- [Jurafsky & Martin, 3rd Edition (free draft)](https://web.stanford.edu/~jurafsky/slp3/)
- [Audio Signal Processing for ML, by Valerio Velardo](https://www.youtube.com/playlist?list=PL-wATfeyAMNqIee7cH3q1bh4QJFAaeNv0)
- [torchaudio tutorials](https://docs.pytorch.org/audio/stable/index.html)
- [Open ASR Leaderboard](https://huggingface.co/spaces/hf-audio/open_asr_leaderboard)