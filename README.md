Overview

This project implements a hybrid anomaly detection framework that combines the strengths of Autoencoders and Generative Adversarial Networks (GANs) to identify anomalous patterns in data.

The approach is designed for highly imbalanced datasets, where anomalies are rare and difficult to model using traditional supervised techniques. The system is demonstrated on the Credit Card Fraud Detection dataset, but the framework is generic and can be adapted to other anomaly detection problems such as network intrusion, system failures, or financial risk detection.

Motivation

Traditional anomaly detection methods often rely on:

Reconstruction error alone (Autoencoders), or

Distribution learning alone (GANs)

Each has limitations when used independently.

This project hybridizes both approaches:

Autoencoders capture normal behavior via reconstruction

GANs capture data distribution discrepancies

The combination leads to more robust and stable anomaly scores.

Architecture
1. Autoencoder

Trained only on normal samples

Learns a compact latent representation

Anomalies produce high reconstruction error

2. GAN

Generator learns to mimic normal data distribution

Discriminator distinguishes real vs generated samples

Discriminator confidence is used as an anomaly signal

3. Hybrid Anomaly Score

The final anomaly score is computed as:

Anomaly Score =
Reconstruction Error
+ (1 − |Discriminator(real) − Discriminator(fake)|)


This balances sample-level deviation and distribution-level deviation.

Dataset

Credit Card Fraud Detection Dataset

Contains anonymized transaction features

Highly imbalanced (fraud ≈ 0.17%)

Only numerical features used

Data scaled using MinMaxScaler

Note: The model is trained only on normal (non-fraud) samples, which is standard practice in anomaly detection.

Technologies Used

Python

PyTorch

NumPy

Pandas

Scikit-learn

Matplotlib

Google Colab

## 📄 Research Paper

This project is based on our IEEE published research:

**A Hybrid Deep Learning Approach for Detecting Anomalies in Real-Time Data Streams**  

Published in: 2025 6th International Conference for Emerging Technology (INCET)

🔗 IEEE Xplore Link: https://ieeexplore.ieee.org/document/11140026

If you use this code, please cite the paper.

