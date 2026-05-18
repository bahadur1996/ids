# Intrusion Detection System — Research Paper Implementations

This repository contains implementations of academic research papers on **Intrusion Detection Systems (IDS)**. Each subfolder reproduces a published paper's methodology using real-world datasets, covering both log-based and network-based anomaly detection.

## Implementations

| Subfolder | Paper | Method | Dataset | Status |
|-----------|-------|--------|---------|--------|
| [Log Mining](./Log%20Mining/) | Detecting Large-Scale System Problems by Mining Console Logs (SOSP 2009) | Log parsing + PCA | Hadoop logs | Complete |
| [DeepLog](./DeepLog/) | DeepLog: Anomaly Detection and Diagnosis from System Logs through Deep Learning (CCS 2017) | LSTM sequence prediction | HDFS logs | Complete |
| [Attention-CNN-LSTM](./attention-CNN-LSTM/) | Deep learning for network security: an Attention-CNN-LSTM model for accurate intrusion detection (Scientific Reports 2025) | CNN + LSTM + Attention | Bot-IoT (UNSW 2018) | In Progress |

## Environment

- Python 3.8+
- PyTorch 2.x with CUDA support
- Jupyter Notebooks
- pandas, numpy, scikit-learn, matplotlib, seaborn
