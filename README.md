<div align="center">

# Neural Signal Classification System

[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)]()

**EEG-based brain state classification using machine learning — Rest, Movement, and Visual stimulus detection from neural signals.**

</div>

---

## Why This Matters

Brain-computer interfaces (BCIs) are reshaping how humans interact with machines. From restoring motor function in paralysis patients to hands-free device control, the ability to decode neural intent in real time is foundational to next-generation assistive technology and neuroscience research.

This project demonstrates the core ML pipeline behind such systems: signal generation, preprocessing, classification, and evaluation — built entirely in Python with production-ready modularity.

---

## Features

- **Synthetic EEG Generation** — Produces biologically-grounded signals across three frequency bands (delta/theta, alpha/beta, gamma) to simulate distinct cognitive states
- **Automated Preprocessing** — Applies standard scaling and an 80/20 train-test split with reproducible random seeds
- **Random Forest Classifier** — 100-estimator ensemble trained on 64-channel feature vectors across 1,000 samples
- **Signal Visualization** — Per-class waveform plots that expose frequency-domain differences between brain states
- **Model Persistence** — Exports a serialized `.pkl` model for downstream inference or deployment
- **Modular Architecture** — Each pipeline stage is an isolated function, making substitution of real EEG datasets or deep learning models straightforward

---

## Architecture

```
Raw EEG Signal (64 channels, 1s window)
             |
             v
    +------------------+
    |  Signal Generator |   <-- synthetic or real dataset
    +------------------+
             |
             v
    +------------------+
    |   Preprocessor   |   StandardScaler + train/test split
    +------------------+
             |
             v
    +------------------+
    | Random Forest     |   n_estimators=100, random_state=42
    | Classifier        |
    +------------------+
             |
       +-----+-----+
       |           |
       v           v
  Evaluation    Saved Model
  (accuracy,    (.pkl export)
  F1, recall)
```

---

## Installation

```bash
# Clone the repository
git clone https://github.com/LakshmiSravyaVedantham/EEG.git
cd EEG

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# Install dependencies
pip install numpy pandas scikit-learn matplotlib seaborn scipy joblib
```

---

## Usage

```bash
python EEG/main.py
```

This single command will:

1. Generate 1,000 synthetic EEG samples across 64 time-domain features
2. Plot representative waveforms for each brain state
3. Train and evaluate a Random Forest classifier
4. Print accuracy and a full per-class classification report
5. Save the trained model to `neural_signal_classifier.pkl`

---

## Results

| Brain State | Frequency Band | Example Accuracy |
|-------------|---------------|-----------------|
| Rest        | Delta / Theta (5 Hz)  | ~XX%  |
| Movement    | Alpha / Beta (10 Hz)  | ~XX%  |
| Visual      | Gamma (30 Hz)         | ~XX%  |

> Run `python EEG/main.py` to populate this table with your results. Overall accuracy typically exceeds 90% on the synthetic dataset.

---

## Extending the Project

| Direction | Description |
|-----------|-------------|
| Real datasets | Swap synthetic data for PhysioNet, EEGBCI, or OpenBCI recordings |
| Deep learning | Replace Random Forest with an LSTM or EEGNet for temporal modeling |
| Real-time inference | Stream data via Python sockets to simulate a live BCI pipeline |
| Interactive dashboard | Wrap the pipeline in a Flask or Streamlit web app |

---

## Tech Stack

[![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)](https://numpy.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square)](https://matplotlib.org/)
[![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat-square&logo=scipy&logoColor=white)](https://scipy.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)

---

## Contributing

Contributions are welcome. To get started:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a pull request

Please follow PEP 8 style conventions and include tests for any new functionality.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

<div align="center">
Built by <a href="https://github.com/LakshmiSravyaVedantham">Lakshmi Sravya Vedantham</a>
</div>
