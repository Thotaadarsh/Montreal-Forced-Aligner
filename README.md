# 🎙️ Montreal Forced Aligner (MFA) - Forced Alignment Project

## 📌 Overview

This project demonstrates the use of the **Montreal Forced Aligner (MFA)** to perform forced alignment between speech recordings and their corresponding transcripts.

The goal is to generate **TextGrid files** containing precise **word-level** and **phoneme-level** alignments for audio samples from the **ISLE corpus** and **F2BJRLP dataset**.

---

## 🎯 Objective

To align speech and text data using the **Montreal Forced Aligner (MFA)** and generate corresponding **TextGrid** files for accurate phonetic and word-level time alignment.

---

## 🤔 What is Forced Alignment?

Forced alignment is the process of automatically matching spoken audio with its written transcript and determining the exact timing of each word and phoneme in the recording.

### Example

🎤 **Audio:**

```text
Good Morning
```

📝 **Transcript:**

```text
GOOD MORNING
```

The aligner analyzes the audio and produces a TextGrid file containing word and phoneme boundaries.

### Sample Alignment

| Phoneme | Time Interval |
|----------|---------------|
| G | 0.00 – 0.15 |
| UH | 0.15 – 0.35 |
| D | 0.35 – 0.55 |
| M | 0.55 – 0.65 |
| AO | 0.65 – 0.85 |
| R | 0.85 – 1.00 |
| N | 1.00 – 1.10 |
| IH NG | 1.10 – 1.20 |

---

## 🖥️ Environment

### Operating System

- 🪟 Windows 11
- 🐧 WSL Ubuntu 22.04

### Software & Tools

- 🐍 Python 3.10
- 📦 Conda
- 🎙️ Montreal Forced Aligner (MFA)
- 📊 Praat
- 🔧 dos2unix

---

## 📂 Project Structure

```text
mfa_project/
│
├── corpus/
│   ├── F2BJRLP1.wav
│   ├── F2BJRLP1.txt
│   ├── F2BJRLP2.wav
│   ├── F2BJRLP2.txt
│   ├── F2BJRLP3.wav
│   ├── F2BJRLP3.txt
│   ├── ISLE_SESS0131_BLOCKD02_01_sprt1.wav
│   ├── ISLE_SESS0131_BLOCKD02_01_sprt1.txt
│   ├── ISLE_SESS0131_BLOCKD02_02_sprt1.wav
│   ├── ISLE_SESS0131_BLOCKD02_02_sprt1.txt
│   ├── ISLE_SESS0131_BLOCKD02_03_sprt1.wav
│   └── ISLE_SESS0131_BLOCKD02_03_sprt1.txt
│
├── output/
│   ├── F2BJRLP1.TextGrid
│   ├── F2BJRLP2.TextGrid
│   ├── F2BJRLP3.TextGrid
│   ├── ISLE_SESS0131_BLOCKD02_01_sprt1.TextGrid
│   ├── ISLE_SESS0131_BLOCKD02_02_sprt1.TextGrid
│   └── ISLE_SESS0131_BLOCKD02_03_sprt1.TextGrid
│
├── custom.dict
├── praat_view/
└── wordlist.txt
```

---

## 🚀 Installation

### 1️⃣ Create Conda Environment

```bash
conda create -n mfa_env python=3.10 -y
conda activate mfa_env
```

### 2️⃣ Install MFA

```bash
pip install montreal-forced-aligner
```

### 3️⃣ Install Praat and Utilities

```bash
sudo apt-get update
sudo apt-get install -y praat dos2unix
```

---

## 📁 Dataset Preparation

Create project folders:

```bash
mkdir -p ~/mfa_project/{corpus,output}
```

Copy all `.wav` and `.txt` files into the `corpus` directory.

Verify files:

```bash
ls ~/mfa_project/corpus
```

Convert Windows line endings to Unix format:

```bash
dos2unix ~/mfa_project/corpus/*.txt
```

---

## 📥 Download MFA Models

### Dictionary Model

```bash
mfa model download dictionary english_us_arpa
```

### Acoustic Model

```bash
mfa model download acoustic english_us_arpa
```

---

## ✅ Validate Corpus

### Using Default Dictionary

```bash
mfa validate ~/mfa_project/corpus english_us_arpa
```

### Using Custom Dictionary

```bash
mfa validate ~/mfa_project/corpus ~/mfa_project/custom.dict
```

---

## 🎯 Run Forced Alignment

### Using MFA Default Dictionary

```bash
mfa align \
~/mfa_project/corpus \
english_us_arpa \
english_us_arpa \
~/mfa_project/output \
--overwrite \
--num_jobs 4
```

### Using Custom Dictionary

```bash
mfa align \
~/mfa_project/corpus \
~/mfa_project/custom.dict \
english_us_arpa \
~/mfa_project/output \
--overwrite \
--num_jobs 4
```

---

## 📊 Generated Outputs

The alignment process generates the following TextGrid files:

```text
F2BJRLP1.TextGrid
F2BJRLP2.TextGrid
F2BJRLP3.TextGrid
ISLE_SESS0131_BLOCKD02_01_sprt1.TextGrid
ISLE_SESS0131_BLOCKD02_02_sprt1.TextGrid
ISLE_SESS0131_BLOCKD02_03_sprt1.TextGrid
```

These files contain:

✅ Word boundaries

✅ Phoneme boundaries

✅ Start and end timestamps

✅ Speech segmentation information

---

## 🔍 Visualization with Praat

Launch Praat:

```bash
praat &
```

Open:

- 🎵 Audio File (.wav)
- 📄 TextGrid File

Click:

```text
View & Edit
```

Praat will display:

- 📈 Waveform
- 📉 Spectrogram
- 🔤 Word Alignment
- 🔡 Phoneme Alignment

---

## 📈 Results

Successfully generated TextGrid alignments for:

- ✅ F2BJRLP1
- ✅ F2BJRLP2
- ✅ F2BJRLP3
- ✅ ISLE_SESS0131_BLOCKD02_01_sprt1
- ✅ ISLE_SESS0131_BLOCKD02_02_sprt1
- ✅ ISLE_SESS0131_BLOCKD02_03_sprt1

The alignments were verified in **Praat** and accurately identified word and phoneme boundaries from the supplied speech recordings. :contentReference[oaicite:0]{index=0}

---

## 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| 🎙️ Montreal Forced Aligner | Forced Alignment |
| 📊 Praat | Visualization |
| 🐍 Python 3.10 | Development |
| 📦 Conda | Environment Management |
| 🐧 Ubuntu 22.04 (WSL) | Execution Platform |
| 🪟 Windows 11 | Host Operating System |

---

## 🌟 Features

✨ Automatic speech-to-text alignment

✨ Word-level segmentation

✨ Phoneme-level segmentation

✨ TextGrid generation

✨ Compatible with Praat visualization

✨ Supports custom pronunciation dictionaries

✨ Supports batch processing of multiple audio files

---

## 📚 Applications

- 🗣️ Speech Recognition Research
- 🎤 Phonetics Analysis
- 📖 Language Learning Systems
- 🤖 NLP and Speech Processing
- 🔬 Linguistic Research
- 🎧 Audio Annotation

---

## 👨‍💻 Author

### Thota Adarsh

📧 Email: adarshthota61@gmail.com

🔗 GitHub: https://github.com/Thotaadarsh

---

## ⭐ Repository

If you found this project useful, consider giving it a ⭐ on GitHub!

---

## 📜 License

This project was developed as part of an academic assignment to explore speech processing and forced alignment using the Montreal Forced Aligner (MFA). 📚
