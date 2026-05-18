# Attention-CNN-LSTM for Network Intrusion Detection

## Paper Reference

| Field | Details |
|-------|---------|
| **Title** | Deep learning for network security: an Attention-CNN-LSTM model for accurate intrusion detection |
| **Author** | Abdullah Mujawib Alashjaee |
| **Affiliation** | Department of Computer Science, Northern Border University, Arar, Saudi Arabia |
| **Journal** | Scientific Reports, Vol. 15, Article 21856 |
| **Year** | 2025 |
| **DOI** | https://doi.org/10.1038/s41598-025-07706-y |

## Dataset

**Bot-IoT Dataset (UNSW 2018)**

| Property | Value |
|----------|-------|
| Total records | ~4 million network traffic flows |
| Files | 74 CSV files (~16 GB total) |
| Features | 34 network features |
| Source | University of New South Wales (UNSW) |
| URL | https://research.unsw.edu.au/projects/bot-iot-dataset |

**Feature categories:** packet statistics, timing metrics, protocol info, flow identifiers, MAC addresses, traffic flags

**Classes:** Normal, Reconnaissance, Service Scan, DoS, TCP-based attacks, and subcategories

## Paper Summary

This paper proposes a hybrid deep learning model that combines three architectural components for multi-class network intrusion classification:

**Architecture:**
1. **CNN (Convolutional Neural Network)** — Extracts local spatial patterns and feature correlations from network traffic feature vectors
2. **LSTM (Long Short-Term Memory)** — Models temporal dependencies across sequential traffic flows
3. **Attention Mechanism** — Assigns importance weights to different features and time steps, improving both accuracy and interpretability

**Pipeline:**
1. Raw network traffic flows are pre-processed and normalized
2. Feature sequences are fed into the CNN layers for spatial feature extraction
3. LSTM layers capture temporal patterns in the extracted features
4. Attention layer focuses on the most relevant features for classification
5. Output layer classifies traffic as normal or a specific attack type

**Results (from paper):**
- Accuracy: 94.8% – 97.5% depending on dataset split
- Strong F1-score and Matthews Correlation Coefficient (MCC) improvements over baselines
- Evaluated on both NSL-KDD and Bot-IoT datasets

## Implementation

| File | Description |
|------|-------------|
| `01_setup_and_download.ipynb` | Environment setup, dataset download instructions, EDA |
| `Deep learning for network security.pdf` | Original paper |

**Status:** Environment setup and exploratory data analysis complete. Model implementation in progress.
