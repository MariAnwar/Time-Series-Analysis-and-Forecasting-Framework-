# 📡 Time Series Analysis and Forecasting Framework

> End-to-end internet traffic forecasting framework built on the **Province of Trentino Grid dataset** (Italy) — featuring a full preprocessing pipeline, SARIMA, SARIMAX, GARCH, LSTM, and TACTiS2 models, and an interactive Streamlit dashboard.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-UI-red?logo=streamlit)
![SARIMA](https://img.shields.io/badge/Model-SARIMA-blue)
![LSTM](https://img.shields.io/badge/Model-LSTM-blueviolet)

---

##  Overview

This framework provides a complete pipeline for analyzing and forecasting large-scale internet traffic data from the **Province of Trentino telecommunications in Italy**. The dataset is organized into geographic grid cells (squares), and the pipeline covers everything from raw data acquisition and preprocessing to training five different forecasting models and comparing them interactively via a web dashboard.

Key highlights:
-  Processes internet traffic data across **geographic grid cells** of the Trentino network
-  Full preprocessing pipeline including time zone handling, resampling, and smoothing
-  Implements and compares **SARIMA, SARIMAX, GARCH, LSTM, and TACTiS2** forecasting models
-  Achieves **10.82% MAPE** (one-shot) and **16.36% MAPE** (rolling window) with SARIMA
-  Interactive Streamlit dashboard to select a model, run forecasts, and compare results

---

##  Features

| Feature | Description |
|---|---|
|  Dataset Acquisition | Automated notebook to download the Trentino internet traffic dataset |
|  Grid Cell Separation | Splits raw data into individual geographic grid cells for per-cell analysis |
|  Preprocessing Pipeline | Time zone normalization, resampling, and noise reduction via smoothing |
|  Model Selection | ACF/PACF-based analysis to identify optimal SARIMA parameters |
|  5 Forecasting Models | SARIMA, SARIMAX, GARCH, LSTM, and TACTiS2 — each with dedicated implementation |
|  Interactive Web UI | Streamlit dashboard to select a grid cell and model, run forecasts, and explore results |

---

##  Project Structure
```
Time-Series-Analysis-and-Forecasting-Framework/
├── Downloading_Dataset.ipynb                # Download and inspect the raw Trentino dataset
├── Separating_the_Data_into_squares.ipynb   # Split data by geographic grid cell and store them in CSV format for each square
├── Data_Handler.py                          # Preprocessing pipeline (timezone, resampling, smoothing)
├── Model_selection.py                       # Main interface for selecting and running different forecasting models
├── SARIMAModel.py                           # SARIMA training, one-shot & rolling window forecasting
├── SARIMAXModel.py                          # SARIMAX model implementation
├── GARCHModel.py                            # GARCH model implementation
├── lstm_data_handler.py                     # Data preparation and utilities for LSTM models
├── LSTMModel.py                             # LSTM model implementation
├── TACTiS2Model.py                          # TACTiS2 model implementation
├── webpage.py                               # Streamlit interactive forecasting dashboard
├── DFs/                                     # Processed per-cell dataframes

```

---

##  Data Flow
```
Raw Trentino Dataset
    ↓
Downloading_Dataset.ipynb  →  downloads and inspects the raw traffic data
    ↓
Separating_the_Data_into_squares.ipynb  →  splits data into individual geographic grid cells
    ↓
Data_Handler.py  →  time zone handling, resampling, smoothing, outputs clean DFs/
    ↓
Model_selection.py  →  selecting and running the preferred model by the user
    ↓
[Selected Model].py  →  generate forecasts using the chosen model
    ↓
webpage.py  →  user selects grid cell and model → displays forecast results interactively
```

---

##  Getting Started

### Prerequisites

- Python 3.10+
- Jupyter Notebook (for the data preparation notebooks)

### Installation

1. **Clone the repository**
```bash
   git clone https://github.com/MariAnwar/Time-Series-Analysis-and-Forecasting-Framework-.git
   cd Time-Series-Analysis-and-Forecasting-Framework-
```

2. **Create a virtual environment**
```bash
   python -m venv venv
   source venv/bin/activate        # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
   pip install -r requirements.txt
```

### Usage

**Step 1 — Download the dataset**

Open and run `Downloading_Dataset.ipynb` to fetch the raw Trentino internet traffic data.

**Step 2 — Separate into grid cells**

Run `Separating_the_Data_into_squares.ipynb` to split the data by geographic grid cell. Processed files are saved to `DFs/`.

**Step 3 — Preprocess**

`Data_Handler.py` is invoked automatically by downstream scripts, but can also be run standalone to inspect the preprocessing steps (time zone normalization, resampling, smoothing).


**Step 4 — Launch the dashboard**
```bash
streamlit run webpage.py
```

Opens the interactive dashboard at `http://localhost:8501` where you can upload a grid cell, choose a forecasting model, and run predictions.

---

##  Results

SARIMA performance on the Trentino internet traffic dataset:

| Forecasting Strategy | MAPE |
|---|---|
| One-Shot Prediction | **10.82%** |
| Rolling Window Forecasting | **16.36%** |

---

##  How It Works

### Preprocessing
Raw internet traffic data from the Trentino grid is first separated by geographic cell. Each cell's time series then goes through time zone normalization to UTC+1 (Italy), resampling to a uniform frequency, and smoothing to reduce noise before model fitting.


### Forecasting Strategies (SARIMA)
- **One-shot:** The model is trained once on the full training set and forecasts the entire test horizon in a single pass — achieving **10.82% MAPE**.
- **Rolling window:** The model is retrained at each step as new observations become available — achieving **16.36% MAPE**.

### Model Comparison
The dashboard allows exploration of all five models — SARIMA, SARIMAX, GARCH, LSTM, and TACTiS2 — on any selected grid cell, making it easy to compare their forecasting behavior visually.

---

##  Tech Stack

- **[Streamlit](https://streamlit.io/)** — Interactive forecasting dashboard
- **[statsmodels](https://www.statsmodels.org/)** — SARIMA and SARIMAX model implementation
- **[arch](https://arch.readthedocs.io/)** — GARCH model implementation
- **[TensorFlow / Keras](https://www.tensorflow.org/)** — LSTM model
- **[TACTiS2](https://github.com/ServiceNow/TACTiS)** — Transformer-based probabilistic forecasting
- **[pandas](https://pandas.pydata.org/)** — Data wrangling and resampling
- **[matplotlib](https://matplotlib.org/)** — ACF/PACF plots and result visualization
- **[scikit-learn](https://scikit-learn.org/)** — Evaluation metrics

---

##  Contributers


| Contributor | Contribution |
|---|---|
| **Mari Anwar** | Data preparation pipeline, SARIMA model |
| **Salma Ahmed** | SARIMAX model |
| **Rafik Sameh** | GARCH model |
| **Etedal Abughanem** | LSTM model |
| **Nour Fouad** | TACTiS2 model |

---

