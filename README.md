# 🧠 Multimodal Focus Analytics Pipeline

[![arXiv](https://img.shields.io/badge/arXiv-23XX.XXXXX-b31b1b.svg)](https://arxiv.org/abs/23XX.XXXXX)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Powered by MediaPipe](https://img.shields.io/badge/Powered%20by-MediaPipe-green)](https://developers.google.com/mediapipe)
[![STT by Whisper](https://img.shields.io/badge/STT-OpenAI%20Whisper-orange)](https://github.com/openai/whisper)

> [cite_start]**A multimodal system for detecting focus drop intervals in lecture videos and recovering missed content via automated summarization.** [cite: 1, 4]

---

## 📖 Abstract

[cite_start]Students frequently lose critical information during recorded lectures due to fluctuating attention levels[cite: 3]. [cite_start]This repository contains the implementation of **"A Multimodal Pipeline for Detecting Focus Drop Intervals and Recovering Missed Lecture Content"**[cite: 1].

[cite_start]Unlike traditional review tools that require manual searching[cite: 12], this system uses a **multimodal approach (Video + Audio)** to:
1.  [cite_start]**Detect** physiological signs of drowsiness and distraction (eye aspect ratio, head pitch, pupil behavior)[cite: 5, 41, 44].
2.  [cite_start]**Align** these drops with timestamped speech-to-text transcripts[cite: 5, 19].
3.  [cite_start]**Generate** a comprehensive PDF report summarizing exactly *what* was missed during the attention lapse[cite: 6, 20].

---

## 🏗 System Architecture

[cite_start]The pipeline operates on a modular architecture processing visual and acoustic streams independently before fusion[cite: 16, 21].

```mermaid
graph LR
    A[Input Video] --> B{Stream Separation}
    B -->|Video| C[Visual Processing]
    B -->|Audio| D[Audio Processing]
    C --> E[Data Integration & Logic]
    D --> E
    E --> F[Output Generation]
    
    subgraph Visual Processing
    C1[FaceMesh Landmarks] --> C2[Drowsiness Estimation]
    C2 --> C3[Dynamic Calibration]
    end
    
    subgraph Audio Processing
    D1[FFmpeg Extraction] --> D2[Whisper STT]
    D2 --> D3[Content Summarization]
    end
