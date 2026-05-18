# Detecting Large-Scale System Problems by Mining Console Logs

## Paper Reference

| Field | Details |
|-------|---------|
| **Title** | Detecting Large-Scale System Problems by Mining Console Logs |
| **Authors** | Wei Xu, Ling Huang, Armando Fox, David Patterson, Michael I. Jordan |
| **Affiliation** | UC Berkeley EECS Department & Intel Labs Berkeley |
| **Venue** | ACM SOSP 2009 (Symposium on Operating Systems Principles) |
| **URL** | https://dl.acm.org/doi/10.1145/1629575.1629587 |

## Dataset

**Hadoop MapReduce Console Logs**

| Property | Value |
|----------|-------|
| Total log lines | ~24 million |
| Source | Production Hadoop cluster |
| Format | Unstructured console log text |

**Darkstar Online Game Server Logs** — used as secondary evaluation dataset in the paper

**Sample used in this implementation:** `HDFS_2k.log` (2,000 lines for demonstration)

## Paper Summary

This paper presents one of the earliest approaches to automated large-scale system problem detection using console log mining. It addresses the challenge that real-world system logs are unstructured, high-volume, and difficult to analyze manually.

**Approach:**
1. **Log Parsing** — Regex-based parsing extracts structured fields from raw log lines: timestamp, log level (INFO/WARN/ERROR), thread ID, component name, and message text
2. **Message Type Identification** — Numeric values, hex IDs, and IP addresses in messages are replaced with placeholders (`#`) to identify recurring message "types" (templates)
3. **Feature Extraction** — Log messages are grouped into sessions by application or attempt ID; each session is represented as a vector of message type counts
4. **Source Code Analysis** — The paper's key innovation: uses static analysis of application source code combined with information retrieval to automatically identify which log variables are informative, reducing feature engineering effort
5. **Anomaly Detection** — PCA (Principal Component Analysis) is applied to session feature vectors to detect deviations from normal behavior

**Key Properties:**
- Does not require labeled anomaly data for training
- Scales to tens of millions of log lines
- Automatically identifies the most informative log variables via source code analysis
- Serves as a classical ML baseline for log-based IDS before deep learning approaches

## Implementation

| File | Description |
|------|-------------|
| `log_mining.ipynb` | Log parsing, feature extraction, message type identification, anomaly visualization |
| `loghub/` | Collection of public system log datasets for benchmarking |
