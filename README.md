# 📈 AI-Driven Smart DCA Strategy for Thai S&P 500 Mutual Funds

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.0+-orange.svg)
![Finance](https://img.shields.io/badge/Domain-Quantitative_Finance-green.svg)

## 📌 Project Overview
This project proposes a dynamic asset allocation strategy (Smart DCA) designed to overcome the limitations of investing in Thai S&P 500 Feeder Funds. Thai mutual funds suffer from **Time Zone Lags** (15:30 cut-off time) and a **T+3 settlement period**, leaving investors vulnerable to overnight U.S. market crashes (Tail Risks).

By leveraging a **Hybrid Deep Learning Architecture (GARCH + LSTM)**, this system accurately forecasts next-day market volatility and dynamically reallocates capital between a risky asset (S&P 500) and a safe haven (Money Market Fund) to strictly control the Maximum Drawdown.

## 🧠 Methodology: The Hybrid Engine
The core predictive engine combines traditional econometrics with modern deep learning:
1. **GARCH(1,1) Sensor:** Extracts underlying volatility patterns and financial shocks.
2. **LSTM Network:** Processes historical multivariate sequences (S&P 500 Returns, VIX Index, EuroStoxx50 Returns, and GARCH Volatility) with a 21-day lookback period to capture non-linear market regimes.
3. **Volatility Targeting:** Dynamically adjusts the S&P 500 position size to maintain a target portfolio volatility of 15%.

## 📊 Key Findings (10-Year Backtest: 2016 - 2025)
The strategy was backtested accounting for **real-world frictions** (0.107% exit fees and a 3-day trading cooldown).

### 1. Overall Performance (2016-2025)
| Strategy | Total Return | Max Drawdown | Sharpe Ratio |
|----------|-------------|--------------|--------------|
| Naive DCA | 105.12% | -32.82% | 0.71 |
| **Hybrid AI** | **77.06%** | **-14.32%** | **0.78** |

### 2. Stress Testing: COVID-19 Crash (2020)
* **Naive DCA:** Suffered a catastrophic **-32.82%** drawdown.
* **Hybrid AI:** Successfully mitigated the crash, limiting the drawdown to **-13.59%** and achieving a superior Sharpe Ratio of **1.60**.

### 3. Out-of-Sample Forward Test (2023-2025)
Demonstrating robustness in modern bull markets with underlying uncertainties:
* **Hybrid AI** achieved a highly efficient **Sharpe Ratio of 1.86**, outperforming the standard DCA (1.77) while maintaining the drawdown shield (-14.32%).

## 🔬 Ablation Study
To validate the hybrid architecture, an LSTM-only baseline model (without GARCH feature) was tested. The LSTM-only model suffered a **-28.63%** drawdown during the COVID-19 crisis, proving that integrating GARCH is critical for effectively capturing sudden volatility spikes.

## 🛠️ Tech Stack
* **Data manipulation:** `pandas`, `numpy`
* **Machine Learning:** `tensorflow`, `keras`, `scikit-learn`
* **Econometrics:** `arch`
* **Data Visualization:** `matplotlib`, `seaborn`
* **Financial Data API:** `yfinance`

## 👨‍💻 How to Run
1. Clone this repository.
2. Install dependencies: `pip install -r requirements.txt`
3. Run the Jupyter Notebook `IS_Step_1to7.ipynb` sequentially.
