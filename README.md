# TSA Assignments — Time Series Modelling Notebooks

Jupyter notebooks for a Time Series Analysis (TSA) course at IIT Madras. Two assignments covering classical and deep-learning approaches to modelling real-world and simulated time series data.

## What's Inside

### Q1 — IBM Stock Price Modelling (`TSA_Assignment_modelling_Q1.ipynb`)

Models daily IBM stock prices (Jan 1980 – Oct 1992) using a full pipeline:

1. Exploratory analysis, stationarity testing (ADF), and differencing
2. ACF / PACF analysis → ARIMA(1,1,0) model fitting and residual diagnostics
3. SARIMAX with exogenous macro variables (unemployment rate, yield curve, CPI) fetched from FRED
4. GARCH(1,1) volatility modelling on SARIMAX residuals
5. Bidirectional LSTM with 10-year Treasury yield as an external feature, trained for one-year-ahead forecasting

### Q2 — Simulated Process Identification (`TSA_Assignment_modelling_Q2.ipynb`)

Identifies the generating process behind a simulated time series:

1. Stationarity check (ADF) — data is already stationary
2. ACF / PACF inspection
3. ARIMA grid search over p ∈ [1,5], q ∈ [1,5] (d = 0) — best model: ARIMA(1,0,1)
4. Residual diagnostics: Shapiro-Wilk, Anderson-Darling, Kolmogorov-Smirnov, Q-Q plot

## Dataset

| Notebook | Data file | Description |
|----------|-----------|-------------|
| Q1 | `dailyibm.dat` | 3 333 daily IBM stock closing prices |
| Q2 | `a3q3.dat` | 2 048 observations from a simulated random process |

Both `.dat` files are loaded from Google Drive inside the Colab notebooks. To run locally, update the `file_path` variables to point to your local copies.

## 🛠 Tech Stack

| | Tool | Purpose |
|---|---|---|
| 🐍 | Python 3 | Language |
| 📊 | pandas / NumPy | Data wrangling |
| 📈 | statsmodels | ARIMA, SARIMAX, ACF/PACF, ADF test |
| 🔥 | arch | GARCH volatility modelling |
| 🧠 | TensorFlow / Keras | Bidirectional LSTM |
| 📉 | plotly / matplotlib | Visualisation |
| 🏦 | pandas-datareader / fredapi | Macro-economic data from FRED |
| 🧪 | scipy | Distribution tests (Shapiro-Wilk, K-S, Anderson-Darling) |

## Getting Started

```bash
pip install pandas numpy statsmodels arch tensorflow plotly matplotlib scipy pandas-datareader fredapi
```

Open the notebooks in Google Colab or Jupyter and update the data file paths as needed.

## ⚠️ Known Issues

- Data files (`dailyibm.dat`, `a3q3.dat`) are not included in the repo — they must be sourced separately.
- File paths are hardcoded to Google Drive (`/content/drive/...`). Update them for local execution.
- The FRED API key in Q1 is embedded in the notebook. Replace it with your own key from [FRED](https://fred.stlouisfed.org/docs/api/api_key.html).

## License

Academic coursework — IIT Madras, CH23M514.
