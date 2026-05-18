# DeepLog: Anomaly Detection and Diagnosis from System Logs through Deep Learning

## Paper Reference

| Field | Details |
|-------|---------|
| **Title** | DeepLog: Anomaly Detection and Diagnosis from System Logs through Deep Learning |
| **Authors** | Min Du, Feifei Li, Guineng Zheng, Vivek Srikumar |
| **Affiliation** | School of Computing, University of Utah |
| **Venue** | ACM CCS 2017 (Conference on Computer and Communications Security) |
| **DOI** | https://doi.org/10.1145/3133956.3134015 |

## Dataset

**HDFS (Hadoop Distributed File System) Logs**

| Property | Value |
|----------|-------|
| Total log lines | ~11.2 million |
| Total sessions (by block_id) | 575,061 |
| Normal sessions | 558,223 |
| Anomalous sessions | 16,838 (~2.9%) |
| Distinct log keys | 29 |
| Source | Amazon EC2 Hadoop cluster (200+ nodes) |

**Files:**
- `HDFS.log` — full raw log file
- `HDFS_2k.log` — 2,000-line sample for quick testing
- `anomaly_label.csv` — ground truth labels per block_id

## Paper Summary

DeepLog frames system log analysis as a sequence prediction problem, similar to language modeling in NLP. The key insight is that normal system execution follows predictable patterns in log event sequences, and deviations from those patterns indicate anomalies.

**Approach:**
1. **Log Parsing** — Raw log text is parsed into structured log keys (templates) using the Drain3 algorithm
2. **Session Construction** — Log entries are grouped into sessions by block_id
3. **Sequence Modeling** — A 2-layer LSTM is trained on normal sessions to predict the next log key given a sliding window of h=10 previous keys
4. **Anomaly Detection** — At inference time, if the actual next log key does not appear in the top-g (g=9) LSTM predictions, the session is flagged as anomalous

**Model Architecture:**
- Embedding layer (log key ID → dense vector)
- 2-layer LSTM (64 hidden units per layer)
- Fully connected output layer (multi-class next-key prediction)

**Key Properties:**
- Trained on normal data only — no anomaly labels required for training
- Supports online learning via incremental model updates
- Provides workflow-based diagnosis to explain detected anomalies
- Reported ~96% F1-score on HDFS in the original paper

## Implementation

| File | Description |
|------|-------------|
| `parser.ipynb` | Full pipeline: log parsing, data preparation, LSTM training, anomaly detection |
| `deeplog_hdfs.pt` | Saved PyTorch model weights |
