<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
</head>
<body>

<header>
    <h1 align="center">🎭 Multimodal Emotion Classification from Social Media Videos</h1>
    <p align="center"><b>Multimodal Machine Learning for Emotion Understanding</b></p>
    <p align="center">
        Late Fusion–based Emotion Classification using Visual, Audio, and Text Features
    </p>
    <p align="center">
        <img src="https://img.shields.io/badge/Python-3.x-blue?style=flat-square&logo=python"/>
        <img src="https://img.shields.io/badge/Framework-XGBoost%20%7C%20LightGBM-orange?style=flat-square"/>
        <img src="https://img.shields.io/badge/Task-Multimodal%20Learning-green?style=flat-square"/>
        <img src="https://img.shields.io/badge/Competition-SATRIA%20DATA%202025-red?style=flat-square"/>
    </p>
    
</header>

---

## 🧩 Project Summary

This repository documents a **multimodal emotion classification project** developed for the  
<strong>SATRIA DATA 2025 – Big Data Challenge</strong>, where our team achieved  
<strong>Top 20 out of ~300 teams</strong> in the preliminary round.

The project aims to automatically classify emotions from **social media videos** by integrating
information from **visual, audio, and text modalities**.  
I served as <strong>Team Leader & Machine Learning Engineer</strong>, focusing on
<strong>multimodal fusion design, modeling, and evaluation</strong>.

---

## 🏗 Technical Methodology

The system follows a standard machine learning pipeline, from feature preparation
to multimodal integration and evaluation.

### 📊 Modalities Used
| Modality | Description | Role |
|--------|------------|------|
| Visual | Frame-level statistics (brightness, motion, colorfulness, edge density, optical flow, temporal dynamics) | Emotion cues |
| Audio | Engineered acoustic features (MFCC, chroma, mel-spectrogram, formant statistics) | Prosody & tone |
| Text | BERT embeddings from speech transcripts | Linguistic signals |

Each modality was processed independently, aligned on a shared <code>id</code>, and reduced to a
selected set of the most informative features per modality.

### 🔗 Feature Fusion Strategy
The final architecture uses a **Late Fusion (stacking)** approach:
- A separate base model is trained **per modality** (visual, audio, text).
- Out-of-fold cross-validated class probabilities from each base model are used as
  **meta-features**, avoiding data leakage into the final fusion stage.
- A **meta-model** is trained on the concatenated probabilities to produce the final prediction.

An **Early Fusion baseline** (concatenating all raw features into a single matrix before training one
model) was also implemented and benchmarked against three algorithms (XGBoost, LightGBM, Random Forest)
to validate that the late fusion design meaningfully improves over simple feature concatenation.

---

## 👤 My Contributions

As <strong>Team Leader & Machine Learning Engineer</strong>, my responsibilities included:

### 🔹 Multimodal System Design
- Designed the **end-to-end multimodal learning pipeline**
- Defined the **feature alignment and fusion strategy**

### 🔹 Modeling & Optimization
- Implemented and experimented with **early fusion architectures**
- Trained and tuned models using **classical ML and gradient boosting**
- Optimized performance for **class-imbalanced emotion categories**

### 🔹 Evaluation & Coordination
- Led model evaluation using the official **Macro-averaged F1-Score**
- Coordinated team workflow and ensured compliance with competition rules

> Feature extraction for individual modalities was handled collaboratively, while my focus was on
> **cross-modal integration and performance optimization**.

---

## 🧠 Modeling & Evaluation

### Model Configuration
- **Base models (per modality):** XGBoost classifiers trained independently on visual, audio, and text features
- **Meta-model (fusion stage):** XGBoost, trained on out-of-fold probability outputs of the three base models
- **Early Fusion baseline comparison:** XGBoost, LightGBM, and Random Forest, each tuned and benchmarked on the concatenated feature set
- **Task:** Multiclass emotion classification
- **Number of Classes:** 8  
  (Proud, Trust, Joy, Surprise, Neutral, Sadness, Fear, Anger)

### Training Strategy
- Stratified train–validation split, performed **before** any resampling to keep validation representative of the natural class distribution
- Class imbalance handling using **ADASYN** (Adaptive Synthetic Sampling)
- Hyperparameter tuning with **RandomizedSearchCV**, optimized directly for macro F1-score
- **Out-of-fold (OOF) stacking** via Stratified K-Fold cross-validation to generate leakage-free meta-features for the fusion model

### Evaluation Metric
- **Macro-averaged F1-Score**  
  (Official competition metric ensuring balanced evaluation across all classes)

---

## 📂 Repository Structure

<pre>
.
├── data/
│   ├── raw/
│   │   └── data_train_sample.csv
│   │
│   └── preprocessed/
│       ├── visual/
│       │   └── visual_features_sample.csv
│       ├── audio/
│       │   └── audio_features_sample.csv
│       └── text/
│           └── text_features_sample.csv
│
├── model/
│   └── best_model.h5
│
├── notebooks/
│   └── exploratory_and_modeling.ipynb
│
├── README.md
</pre>

<p><b>Note:</b> This public repository contains <b>sample data only</b>.
Full datasets and raw media files used during the competition are not included
due to size and redistribution constraints.</p>

---

## 📜 Academic & Portfolio Disclaimer

This project was developed as part of a national data science competition.
The repository is intended for <b>portfolio and demonstration purposes</b>,
focusing on methodological clarity rather than leaderboard replication.

---

## 📬 Contact

<strong>Natalio Michael Tumuahi</strong><br>
Team Leader & Machine Learning Engineer<br><br>

📧 Email: nataliotumuahi@gmail.com<br>
🔗 GitHub: https://github.com/natalio123<br>
🔗 LinkedIn: (add your LinkedIn URL)

</body>
</html>
