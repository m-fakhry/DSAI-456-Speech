---
theme: neversink
background: RL-bg.png
class: 'text-center'
transition: slide-left
title: Speech Recognition (DSAI 456)
author: Mohamed Ghalwash
year: Spring 2025-2026
venue: Zewail City
mdc: true
lecture: 1
slide:
  disableSlideNumbers: true
slide_info: false
---

# Speech Recognition <br> (Spring DSAI 456)
# Lecture 1 

Mohamed Ghalwash
<Email v="mghalwash@zewailcity.edu.eg" />

---
transition: fade-out
layout: top-title
---

:: title :: 

# Speech Sounds and Phonetic Transcription

:: content :: 

- Represent the pronunciation as a string of phones (speech sounds) which has special alphabets (IPS international phonetics alphabets)

- Mapping between letters of english (orthography) and phones (sound-orthography mapping)
  
  _e.g: 'c' can be mapped to phone 'k' or phone 's'_

![sound-orthography dictionary](./images/ips.png){width=320}


---
transition: fade-out
layout: side-title
titlewidth: is-2
---

:: title :: 

# Speech Sounds and Phonetic Transcription

:: content :: 

- Time-aligned transcription: mapping between waveform and phones (TIMIT corpus)

![alt text](./images/timit.png)

- Articulatory phonetics
  
	- consonant vs vowel 

![alt text](./images/articulation.png)



---
transition: fade-out
layout: side-title
titlewidth: is-2
---

:: title :: 

# Speech Sounds and Phonetic Transcription

:: content :: 

- Syllable:  a vowel-like sound together with some of the surrounding consonants that are most closely associated with it

  - `dog` has one syllable (d aa g), `catnip` has two (k ae t) and (n ih p)

  - The vowel at the core of a syllable is called the **nucleus**
  
  - Initial consonants are called the **onset** (as in strike (s t r ay k))

  - The **coda** is the optional consonant or sequence of consonants following the nucleus

  - The rime, or rhyme, is the nucleus plus coda

![alt text](./images/syllable.png){width=500}


---
layout: top-title-two-cols
---

:: title :: 

# Signal Representation

:: left :: 

- Signal is a waveform 

- Air passes through the glottis -> air pressure -> sound waves

- Waveform can be represented as a combination of `sin` or `cos` functions, e.g. $y = A\; sin(2 \pi f t)$

  - $A$ is the **amplitude**: the maximum value on the Y-axis
  - $f$ is the **frequency**: number of cycles per second
  
<!-- ![alt text](./images/sin.png) -->


:: right :: 

- y-axis the amount of air pressure variation

- **Hertz**: number of cycles per second

- The **period** T of the wave is the time it takes for one cycle to complete, i.e. $T = 1/f$

<img src="./images/sin.png" alt="alt text" width="100%" height="auto">


---
layout: center
class: text-center
---

<img src="./images/wave.png" alt="sound">

A waveform of the vowel (iy). The y-axis shows the level of air pressure above and below normal atmospheric pressure.


---
layout: top-title
---

:: title :: 

# Analog to Digital

:: content :: 

	- Sampling (sampling rate is at least twice the frequency)
  
	- Digitization (stored as integers)

![alt text](./images/digital.png)
  
      - telephone speech is often sampled at 8 kHz and stored as 8-bit samples
      - microphone data is often sampled at 16 kHz and stored as 16-bit samples


---
layout: top-title
---

:: title :: 

# Analog to Digital

:: content :: 

  - _Human hearing is more sensitive at small intensities than large ones_ 
  
  - Compression (linear vs log compression algorithms like $\mu$-law)
	
  - The log represents small values with more faithfulness at the expense of more error on large values

  - `.wav` file 

![alt text](./images/wav.png)


---
layout: top-title-two-cols
columns: is-9
---

:: title :: 

# Pitch and Loudness

:: left :: 

- Pitch (Hz): pitch is our perception of the frequency of the sound wave, meaning how high or low a sound seems to be
  
  - High-pitched sounds, like a whistle, are caused by sound waves with a high frequency 
  - Low-pitched sounds, like a deep bass note, are caused by sound waves with a low frequency 
  - pitch is subjective and linked to how the sound is heard rather than the exact physical frequency
  
- Loudness (decibel dB) is a measure of intensity $I$ of sound ($I \alpha A^2$)

<!-- https://www.youtube.com/watch?v=eA19gFOH1JA -->

:: right ::

<img src="./images/sound-waves.png" width="85%"/>


---
layout: center
class: text-center
---

<img src="./images/animals.png" alt="sound">

Human can hear sound of frequencies between 20Hz and 20kHz. 

# Hearing ranges 


---
layout: top-title
---
:: title :: 

# Features

:: content :: 

- Intensity 

<v-clicks>

![alt text](./images/intensity_1.png)

![alt text](./images/intensity_2.png)

</v-clicks>


---
layout: top-title
---
:: title :: 

# Features

:: content :: 

- RMS (root-mean-square) of amplitude ($\sqrt{\frac{1}{n}\sum_{t=1}^{n}a_t^2}$): the average amplitude over some time range, to give us some idea of how great the average displacement of air pressure is 

- F0 (fundamental frequency): the lowest frequency of a periodic waveform
    
- Pitch track: is a time-based representation that shows how the pitch (perceived frequency) of a sound changes over time

- Frame-by-frame, short overlapping time frames


<!-- https://www.youtube.com/watch?v=eA19gFOH1JA -->


---
layout: top-title
---
:: title ::

# Interpretation of Phones from a Waveform

:: content :: 

<img src="./images/vowels-consonants.png" alt="alt text" width="90%" height="auto">

<v-click>

  - Vowels are pretty easy to spot. They are voiced, tend to be long, and are relatively loud
  - Each of the six vowels have regular amplitude peaks indicating voicing
  - Each major peak corresponding to an opening of the vocal folds

  - A stop consonant consists of a closure followed by a release. Can be seen as a period of silence followed by a slight burst of amplitude
  - Fricative consonant: when a narrow channel for airflow causes noisy, turbulent air

</v-click>

---
layout: section
titlewidth: is-3
---

# What is 
  
- ### Frequency Spectrum

- ### Frequency Bands
  
- ### Frequency Spectrogram

- ### Mel Spectrum 


---
layout: side-title
titlewidth: is-3
class: text-center
---
:: title :: 

# Frequency Spectrum 

:: content ::

<img src="./images/lec2-freq-sinewaves.png" />

<v-click>
<div class="text-red-500 text-xl flex items-center gap-2">
  <i class="i-mdi-emoticon-angry-outline"></i>
  <span>It does not look like a sine waveform</span>
</div>
</v-click>


---
layout: side-title
titlewidth: is-3
---
:: title :: 

# Frequency Spectrum 

:: content ::

<img src="./images/lec2-freq-sinewaves2.png" />

 Maybe a combination of sine waveforms <span class="text-blue-500"> _with different frequencies and amplitude_</span>


---
layout: side-title
titlewidth: is-3
---
:: title :: 

# Frequency Spectrum 

:: content ::

<img src="./images/lec2-freq-sinewaves3.png" />

<div class="flex items-center gap-2 text-yellow-400 text-4xl">
  <i class="i-ic-baseline-lightbulb-circle"></i>
  <span>Aha! I got it</span>
</div>


---
layout: side-title
titlewidth: is-3
---
:: title :: 

# Frequency Spectrum 

:: content ::

<img src="./images/lec2-freq-sinewaves4.png" />

Done using <span class="text-blue-500"> Discrete Fourier Transform </span>


---
layout: four-cell
---

:: top-left ::

<img src="./images/lec2-freq-sinewaves.png" />

:: bottom-left ::

<img src="./images/lec2-freq-sinewaves3.png" />

:: top-right ::

<img src="./images/lec2-freq-sinewaves2.png"  />

:: bottom-right ::

<img src="./images/lec2-freq-sinewaves4.png" />

---
layout: side-title
titlewidth: is-3
---

:: title :: 

# Frequency Bands

:: content :: 

- Phones have characteristic spectral _signatures (Spectral peaks)_

- Inner ear computes the spectrum of the incoming waveform

- Spectrogram for three vowels
  
![](./images/lec2-freq-sinewaves6.png)

<!-- dark is more important because amplitude for white region is almost zero -->
<!-- which frequency range the dark area is -->

- Each dark bar is called a **formant** which is a frequency band that is particularly amplified by the vocal tract



---
layout: center
titlewidth: is-3
---

![](./images/lec2-vowel-spectrum.png){margin:auto;width:50%}

---
layout: image-right
image: ./images/lec2_ear.png
---


# Issues with Hz

- Human hearing is less sensitive at higher frequencies
- The difference at low frequencies 50 Hz to 550 Hz is a massive change in perceived pitch
- However, the difference at high frequencies 13kHz to 15kHz is not a significant change in perceived pitch

- Information in low frequencies (like formants) is crucial for distinguishing vowels or nasals
- Modeling this human perceptual property improves speech recognition performance in the same way

---
layout: top-title-two-cols
columns: is-6
align: l-lt-cm
---

:: title :: 

# Mel to the Rescue 

:: left :: 

- Designed to match human perception of pitch: how humans _perceive_ sound at different frequencies
- Equal intervals in mels represent equal perceived distances between pitches to a human listener
- The scale is anchored at 1000 Hz being equal to 1000 mels
- Below approximately 500 Hz, the mel and Hz scales are roughly equivalent

  $mel(f) = 2595 \log(1+\frac{f}{700})$

:: right :: 

![alt text](./images/lec2-mel-hz.png)

---
layout: center
class: text-center
---

# Learn More

[Slidev](https://sli.dev) · [Course Homepage](https://github.com/m-fakhry/DSAI-456-SR)
