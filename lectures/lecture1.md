---
theme: neversink
layout: cover
# color: navy
colorSchema: light
routerMode: hash
transition: slide-left
title: Speech (DSAI 456) # Why Speech Recognition
# neversink_string: DSAI 456, Lecture 1
author: Mohamed Ghalwash
year: Fall 2026-2027
venue: Zewail City
class: 'text-center'
mdc: true
lecture: 1- Speech System
slide:
  disableSlideNumbers: false
  slide_info: false
disableSlideNumbers: true
slide_info: false
---

# Speech Recognition <br> (DSAI 456)
## Lecture 1: What is Speech System?

**Prof. Mohamed Ghalwash**  
<Email v="mghalwash@zewailcity.edu.eg" />
_Zewail City University_  

:: note ::

Lecture 1, Monday 21 September 2026

---
layout: top-title
color: sky-light
align: lt
title: Today
---

:: title ::

# Agenda

:: content ::

**Objectives**: you should be able to say what a speech system takes in and what it emits, compute the error rate of one by hand, and explain why a leaderboard number does not tell you whether the system works for your users.

- Problem: What does the machine actually receive, and why is turning it into text hard?
- Measurement: What is WER, what does it hide, and when is it the wrong metric?
- Course: How is this course run, and what does the project ask of you?

---
layout: grid-cards
cols: 3
---

# Core Speech Processing Tasks

Key functional modalities in modern speech AI systems.

:: card-1 ::

<div class="flex items-center gap-2 mb-1 text-blue-500 font-bold text-sm">
  <span>ASR</span>
</div>

<p class="font-semibold text-slate-700 dark:text-slate-200 mb-2">
  Automatic Speech Recognition
</p>

<p class="text-slate-500 dark:text-slate-400 mb-4 flex-grow">
  Converts continuous acoustic audio signals into discrete text transcripts.
</p>

<div class="flex items-center justify-between p-2 rounded bg-blue-500/10 text-blue-600 dark:text-blue-400 font-mono text-xs font-semibold">
  <span>Audio</span>
  <span>→</span>
  <span>Text</span>
</div>

:: card-2 ::

<div class="flex items-center gap-2 mb-1 text-emerald-500 font-bold text-sm">
  <span>TTS</span>
</div>

<p class="font-semibold text-slate-700 dark:text-slate-200 mb-2">
  Text-to-Speech
</p>

<p class="text-slate-500 dark:text-slate-400 mb-4 flex-grow">
  Synthesizes human-like spoken audio waveforms directly from input text.
</p>

<div class="flex items-center justify-between p-2 rounded bg-emerald-500/10 text-emerald-600 dark:text-emerald-400 font-mono text-xs font-semibold">
  <span>Text</span>
  <span>→</span>
  <span>Audio</span>
</div>

:: card-3 ::

<div class="flex items-center gap-2 mb-1 text-purple-500 font-bold text-sm">
  <span>Speech LM</span>
</div>

<p class="font-semibold text-slate-700 dark:text-slate-200 mb-2">
  Speech Language Models
</p>

<p class="text-slate-500 dark:text-slate-400 mb-4 flex-grow">
  Generates speech directly from speech by preserving tone and emotion.
</p>

<div class="flex items-center justify-between p-2 rounded bg-purple-500/10 text-purple-600 dark:text-purple-400 font-mono text-xs font-semibold">
  <span>Audio</span>
  <span>→</span>
  <span>Audio</span>
</div>

---
layout: top-title
color: light
align: lt
title: What arrives
---

:: title ::

# What the Machine Actually Receives

:: content ::

<!-- Key Metric Callout Cards -->
<div class="grid grid-cols-3 gap-4 mb-6">
  
  <div class="p-4 rounded-xl bg-amber-500/10 border border-amber-500/20 flex flex-col justify-between">
    <div class="text-xs uppercase tracking-wider font-semibold text-amber-600 dark:text-amber-400">Raw Input Stream</div>
    <div class="text-2xl font-bold my-1 text-amber-700 dark:text-amber-300">16,000 <span class="text-xs font-normal">samples/sec</span></div>
    <div class="text-[10px] opacity-75">Continuous amplitude values (at 16 kHz)</div>
  </div>

  <div class="p-4 rounded-xl bg-blue-500/10 border border-blue-500/20 flex flex-col justify-between">
    <div class="text-xs uppercase tracking-wider font-semibold text-blue-600 dark:text-blue-400">Target Output</div>
    <div class="text-2xl font-bold my-1 text-blue-700 dark:text-blue-300">12–15 <span class="text-xs font-normal">chars/sec</span></div>
    <div class="text-[10px] opacity-75">Discrete text characters per second</div>
  </div>

  <div class="p-4 rounded-xl bg-purple-500/10 border border-purple-500/20 flex flex-col justify-between">
    <div class="text-xs uppercase tracking-wider font-semibold text-purple-600 dark:text-purple-400">Scale Disparity</div>
    <div class="text-2xl font-bold my-1 text-purple-700 dark:text-purple-300">~1,000 : 1</div>
    <div class="text-[10px] opacity-75">Ratio of acoustic data points to output text</div>
  </div>

</div>

<!-- Waveform visual & Core Insight split -->
<div class="grid grid-cols-12 gap-6 items-center">
  
  <div class="col-span-5 bg-slate-100 dark:bg-slate-800/60 p-4 rounded-xl border border-slate-200 dark:border-slate-700 text-center">
    <div class="text-xs font-mono text-slate-500 mb-2 flex items-center justify-center gap-2">
      <i class="carbon:wave-directional inline-block text-amber-500" />
      <span>Continuous Acoustic Waveform</span>
    </div>
    <img src="./images/lec1_sample.png" alt="Audio Waveform Visualization" class="w-full h-24 object-contain rounded my-2" />
    <div class="text-[11px] text-slate-400 italic">No boundaries between words or phonemes</div>
  </div>

  <div class="col-span-7 space-y-3 text-sm">
    <div class="p-3 rounded-lg bg-red-500/10 border-l-4 border-red-500 text-slate-700 dark:text-slate-200">
      <strong class="text-red-500">The Core Challenge:</strong> Nothing in the physical wave signal indicates where one word ends and the next begins.
    </div>
    <p class="text-xs leading-relaxed opacity-80">
      You cannot look at a waveform and see the word. Speech sound is stretched out over time and mixed together with background noise, room echoes, and the speaker's voice.
    </p>
  </div>

</div>

---
layout: top-title
# color: amber-light
align: lt
title: Why it is hard
---

:: title ::

# Four Sources of Difficulty

:: content ::

<v-clicks>

- **The same word is never the same signal.** Speaker, accent, speaking rate, emotion, microphone, room, background noise. All of it multiplies into the waveform and none of it is the message.

- **There are no boundaries to find.** Words run into each other. A native listener hears gaps that do not exist in the signal, because the listener already knows the language.

- **The input and output run at different rates.** The model has to decide which stretch of audio produced which character, and nobody hands it that alignment.

- **Ambiguity is only resolved by context.** Identical acoustics, different text, and only the surrounding words decide. A perfect acoustic model still needs a language model.

</v-clicks>

---
layout: top-title-two-cols
color: light
columns: is-6
align: l-lt-lt
title: Classification vs transduction
---

:: title ::

# Why Not Just Classify?

:: left ::

## Classification

- One input, one label from a fixed set. Ten thousand X-rays, fourteen diagnoses.

- The output space is known before training. You can count the classes.

- The question is <mark>which one is this?</mark>

- Success means matching the label.

:: right ::

## Sequence transduction

- One input of arbitrary length, one output sequence of a different and unknown length.

- The output space is every string the language admits. You cannot enumerate it.

- The question is <mark>what sequence explains this signal?</mark>

- Success means a transcript close to what was said, and "close" needs defining.

---
layout: top-title
color: navy-light
align: lt
title: WER
---

:: title ::

# Word Error Rate

:: content ::

Align the hypothesis to the reference with edit distance, count the three kinds of mistake, divide by the length of the **reference**.

$$\text{WER} = \frac{S + D + I}{N}$$

| | |
|---|---|
| Reference | the committee **approved** the **new** budget **today** |
| Hypothesis | the committee **improved** the budget **to date** |
| | 2 substitution, 1 deletion, 1 insertion |

$$\text{WER} = 4/7 = 57\%$$


<AdmonitionType type='important'>
WER has no upper bound. If you ever report a WER above 1.0, that is not a bug.
</AdmonitionType>

---
layout: top-title
color: light
align: lt
title: What WER hides
---

:: title ::

# What the Number Does Not Tell You

:: content ::

<v-clicks>

- **Every error costs the same.** Swapping a dose of 15 mg for 50 mg and dropping the word "the" are both one substitution. Your application does not agree.

- **The normalization decides the score.** Case, punctuation, numbers as digits or words, and in Arabic the hamza forms, the alef variants, the taa marbuta and the diacritics. Two labs can report different WERs on the same predictions by using different normalizers.

- **CER is often the fairer metric.** For morphologically rich languages, one wrong affix destroys a whole word under WER. Character error rate degrades more gracefully and is standard for Arabic work.

- **The average hides the tail.** A 7% WER over a corpus can be 3% for the men reading news and 30% for one dialect speaker. Your project must report per-speaker and per-condition breakdowns.

</v-clicks>

---
layout: top-title
color: light
align: lt
title: Summary
---

:: title ::

# What To Take Away

:: content ::

- Speech recognition maps a long, continuous, hugely variable signal to a short discrete sequence, with no alignment given and no boundaries marked. 

- WER is edit distance normalized by reference length. It has no ceiling, it weights every error equally, and it changes when your text normalizer changes.

- A leaderboard number describes a corpus, not a language and not your users. Ask what was spoken, by whom, and what the model had already seen.

Next week: the acoustics. Formants, sampling, quantization, framing, F0 and intensity.

---
layout: top-title
color: sky-light
align: lt
title: Before next week
---

:: title ::

# Before We Meet Again

:: content ::

1. **Browse the [Open ASR Leaderboard](https://huggingface.co/spaces/hf-audio/open_asr_leaderboard).** Pick the top system and write down, in one sentence each, which corpus its headline number comes from and which population that corpus represents.

2. **Record 30 seconds of yourself** on your phone, in Arabic, speaking the way you speak to a friend rather than to a microphone. Run it through any free ASR system. Compute the WER by hand.

3. **Bring one failure.** One error the system made that a human listener would not have made, and one sentence on why you think it happened.

<AdmonitionType type='tip'>
Start thinking about teams now. The proposal is due in week 4, and the teams that go looking for a real problem early are the ones that end up with something worth demoing.
</AdmonitionType>

---
layout: section
# color: navy
title: Questions
class: text-center
---

# Learn More

[Course Homepage](https://github.com/m-fakhry/DSAI-456-Speech)
