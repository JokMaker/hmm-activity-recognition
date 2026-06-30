# Human Activity Recognition Using Hidden Markov Models

Individual project for MLT1 Formative 2 — African Leadership University.

## Overview

This project collects real motion sensor data (accelerometer and gyroscope) using the Sensor Logger app on Android, and builds a Hidden Markov Model from scratch to classify four human activities: still, standing, walking, and jumping. The model is trained using the Baum-Welch algorithm with a log-likelihood convergence check, and decoded using a from-scratch implementation of the Viterbi algorithm.

## Results

Evaluated on 16 unseen test recordings, the model achieved an overall accuracy of 72.6% after correcting for HMM state-label misalignment.

| Activity | Sensitivity | Specificity | Accuracy |
|---|---|---|---|
| Still | 0.000 | 0.988 | 0.743 |
| Standing | 1.000 | 0.643 | 0.735 |
| Walking | 0.933 | 1.000 | 0.982 |
| Jumping | 0.962 | 1.000 | 0.991 |

Walking and jumping were classified reliably, while still and standing showed significant confusion due to highly similar low-energy signal profiles. Full analysis is available in the report.

## Project Structure

```
hmm-activity-recognition/
├── data/
│   ├── train/          # 50 labelled training recordings (100 CSV files)
│   │   ├── still/
│   │   ├── standing/
│   │   ├── walking/
│   │   └── jumping/
│   └── test/            # 16 unseen test recordings (32 CSV files)
│       ├── still/
│       ├── standing/
│       ├── walking/
│       └── jumping/
├── notebooks/
│   └── hmm_activity_recognition.ipynb
├── report/
│   ├── report.pdf
│   └── figures/
└── README.md
```

## Methodology

1. **Data Collection** — 50 training recordings + 16 unseen test recordings at 100 Hz sampling rate
2. **Feature Extraction** — 23 time-domain and frequency-domain features per 1-second window (mean, variance, std, SMA, inter-axis correlation, dominant frequency, spectral energy)
3. **Model Training** — Gaussian HMM trained via Baum-Welch with convergence threshold of 1e-4
4. **Decoding** — Viterbi algorithm implemented from scratch in log-space
5. **Evaluation** — Sensitivity, specificity, accuracy, and confusion matrix on unseen test data

## Tools & Libraries

Python, NumPy, hmmlearn, scikit-learn, SciPy, pandas, matplotlib, seaborn, Sensor Logger (Android)

## Author

Jok John Maker Kur — African Leadership University
