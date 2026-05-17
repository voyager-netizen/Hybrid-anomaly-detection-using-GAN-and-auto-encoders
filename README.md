# Hybrid Anomaly Detection using GANs and Autoencoders

A deep learning–based anomaly detection framework that combines **Autoencoders** and **Generative Adversarial Networks (GANs)** to detect anomalous patterns in highly imbalanced datasets.

This project demonstrates the approach using the **Credit Card Fraud Detection Dataset**, where fraudulent transactions represent only a tiny fraction of the overall data. The framework is designed to model normal behavior effectively and identify deviations with improved robustness compared to standalone anomaly detection methods.

---

# Overview

Traditional anomaly detection techniques often struggle with highly imbalanced datasets because anomalous samples are rare and difficult to model directly.

This project introduces a **hybrid architecture** that leverages:

- **Autoencoders** for reconstruction-based anomaly detection
- **GANs** for distribution-based anomaly detection

By combining both approaches, the model captures:

- Individual sample reconstruction deviations
- Global distribution inconsistencies

The resulting system produces a more stable and reliable anomaly score for detecting suspicious data points.

---

# Motivation

Conventional deep learning approaches for anomaly detection typically rely on either:

## Autoencoders

- Learn compressed representations of normal data
- Detect anomalies using reconstruction error
- Limitation: may fail to capture broader distribution shifts

## GANs

- Learn the distribution of normal data
- Detect anomalies through discriminator behavior
- Limitation: training instability and weak sample-level reconstruction insight

This project combines both methods to exploit their complementary strengths.

---

# Architecture

## 1. Autoencoder

The autoencoder is trained exclusively on normal samples.

### Purpose

- Learn latent representations of normal behavior
- Reconstruct normal data with minimal loss

### Observation

Anomalous samples typically produce:

- Higher reconstruction error
- Poor latent representation quality

---

## 2. Generative Adversarial Network (GAN)

The GAN consists of:

- **Generator** → attempts to generate realistic normal samples
- **Discriminator** → distinguishes real data from generated data

### Purpose

- Learn the distribution of normal transactions
- Identify abnormal samples through discriminator confidence

---

## 3. Hybrid Anomaly Scoring

The final anomaly score combines:

- Reconstruction error from the autoencoder
- Distribution discrepancy from the GAN discriminator

### Formula

```text
Anomaly Score =
Reconstruction Error
+ (1 − |Discriminator(real) − Discriminator(fake)|)
```

This hybrid scoring mechanism improves robustness by capturing both:

- Sample-level deviations
- Distribution-level abnormalities

---

# Dataset

## Credit Card Fraud Detection Dataset

The project uses the publicly available credit card fraud dataset containing anonymized transaction features.

### Dataset Characteristics

- Highly imbalanced dataset
- Fraudulent transactions ≈ 0.17%
- Numerical features only
- Preprocessed using `MinMaxScaler`

### Training Strategy

The model is trained only on **normal (non-fraudulent)** samples, which is a standard approach in unsupervised anomaly detection.

---

# Features

- Hybrid anomaly detection framework
- Autoencoder + GAN integration
- Handles highly imbalanced datasets
- PyTorch-based implementation
- Reconstruction and discriminator-based scoring
- Easily adaptable to other anomaly detection domains

---

# Potential Applications

This framework can be extended to several real-world anomaly detection problems, including:

- Financial fraud detection
- Network intrusion detection
- System failure prediction
- IoT anomaly monitoring
- Industrial fault detection
- Real-time risk analysis

---

# Tech Stack

- Python
- PyTorch
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Google Colab

---

# Project Structure

```text
Hybrid-anomaly-detection-using-GAN-and-auto-encoders/
│
├── notebooks/                 # Training and experimentation notebooks
├── models/                    # Saved model weights
├── dataset/                   # Dataset files
├── results/                   # Evaluation plots and outputs
├── utils/                     # Helper functions and preprocessing
├── README.md
└── requirements.txt
```

---

# Installation

Clone the repository:

```bash
git clone https://github.com/aditya-m-mishra/Hybrid-anomaly-detection-using-GAN-and-auto-encoders.git
```

Navigate to the project directory:

```bash
cd Hybrid-anomaly-detection-using-GAN-and-auto-encoders
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# Usage

Run the training notebook or script to:

- Preprocess the dataset
- Train the autoencoder
- Train the GAN
- Compute hybrid anomaly scores
- Evaluate anomaly detection performance

---

# Results

The hybrid approach improves anomaly detection by combining:

- Reconstruction-based learning
- Distribution-based adversarial learning

This leads to:

- Better detection sensitivity
- Improved robustness on imbalanced datasets
- More stable anomaly scoring compared to standalone models

---

# Research Paper

This project is based on our IEEE published research paper:

## **A Hybrid Deep Learning Approach for Detecting Anomalies in Real-Time Data Streams**

Published in:

**2025 6th International Conference for Emerging Technology (INCET)**

🔗 IEEE Xplore:  
https://ieeexplore.ieee.org/document/11140026

---

# Citation

If you use this work in your research or projects, please cite the paper.

```bibtex
@inproceedings{hybrid_anomaly_detection_2025,
  title={A Hybrid Deep Learning Approach for Detecting Anomalies in Real-Time Data Streams},
  booktitle={2025 6th International Conference for Emerging Technology (INCET)},
  year={2025}
}
```

---

# Future Improvements

- Real-time streaming anomaly detection
- Transformer-based anomaly modeling
- Explainable AI for anomaly interpretation
- Adaptive thresholding methods
- Deployment using Flask/FastAPI

---

# Author

**Aditya Mishra**

GitHub:  
https://github.com/aditya-m-mishra
