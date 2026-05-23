![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=flat&logo=powerbi&logoColor=black)
![Prophet](https://img.shields.io/badge/Facebook-Prophet-0866FF?style=flat&logo=meta&logoColor=white)
![NSE](https://img.shields.io/badge/NSE-RELIANCE.NS-009B77?style=flat)

A data-driven analysis of Reliance Industries using Python for data processing and Power BI for interactive visualization and insights.

# 📈 Reliance Industries — Stock Market Analysis & Price Forecasting



![image alt](https://github.com/kishan45yadav/Reliance-Stock-Performance-Analytics-Dashboard/blob/main/Screenshot%20(47).png?raw=true)
![image alt](https://github.com/kishan45yadav/Reliance-Stock-Performance-Analytics-Dashboard/blob/main/Screenshot%20(65).png?raw=true)

> An end-to-end data analytics project covering historical stock analysis, technical indicator computation, and 30-day price forecasting for **Reliance Industries Limited (NSE: RELIANCE.NS)** — India's largest publicly listed conglomerate.

---

## 📌 Project Highlights

| Metric | Value |
|---|---|
| 📅 Data Period | Jan 2023 – Jan 2025 (2 Years) |
| 📊 Trading Days Analysed | 500+ |
| 💰 Avg Closing Price | ~INR 2,631 |
| 📈 Max Single-Day Gain | +4.8% |
| 📉 Max Single-Day Loss | -3.9% |
| 🔮 Forecast Horizon | 30 Days |
| 📦 Price Appreciation (24M) | ~12.4% |

---

## 🗂️ Repository Structure

```
Reliance-Stock-Analysis/
│
├── Reliance.ipynb                        # Main Jupyter Notebook (full pipeline)
├── Reliance_Stock_Analysis_Report.docx   # Detailed project report
├── reliance_final.csv                    # Processed OHLCV data with indicators
├── reliance_forecast.csv                 # Prophet model forecast output
└── README.md
```

---

## 🎯 Objectives

- **Data Acquisition** — Download historical OHLCV data via the `yfinance` API
- **Exploratory Data Analysis (EDA)** — Validate data quality, compute descriptive statistics
- **Technical Indicators** — Calculate 20-Day & 50-Day Moving Averages and Daily Return %
- **Time Series Forecasting** — Build a 30-day price forecast using Facebook Prophet
- **Business Intelligence** — Export clean datasets for interactive Power BI dashboards

---

## 🛠️ Tools & Technologies

### Python Libraries

| Library | Purpose |
|---|---|
| `yfinance` | Historical stock data download from Yahoo Finance |
| `pandas` | Data manipulation & feature engineering |
| `numpy` | Numerical computations |
| `matplotlib` | Static chart plotting |
| `seaborn` | Statistical visualisation & heatmaps |
| `Prophet` (Meta) | Time series forecasting — 30-day prediction |

### BI & Reporting
- **Microsoft Power BI Desktop** — Interactive dashboard with slicers, KPI cards, and forecast visualisation
- **Jupyter Notebook** — Complete reproducible analysis pipeline

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install yfinance pandas numpy matplotlib seaborn prophet
```

### Run the Notebook

```bash
git clone https://github.com/your-username/reliance-stock-analysis.git
cd reliance-stock-analysis
jupyter notebook Reliance.ipynb
```

---

## 📊 Analysis Pipeline

### 1. Data Acquisition
```python
import yfinance as yf
df = yf.download('RELIANCE.NS', start='2023-01-01', end='2025-01-01')
df.reset_index(inplace=True)
```

### 2. Technical Indicators
```python
df['MA_20'] = df['Close'].rolling(window=20).mean()   # Short-term trend
df['MA_50'] = df['Close'].rolling(window=50).mean()   # Medium-term trend
df['Daily_Return'] = df['Close'].pct_change() * 100
```

### 3. 30-Day Forecast with Prophet
```python
from prophet import Prophet

prophet_df = df[['Date', 'Close']].rename(columns={'Date': 'ds', 'Close': 'y'})
model = Prophet(daily_seasonality=True)
model.fit(prophet_df)

future = model.make_future_dataframe(periods=30)
forecast = model.predict(future)
```

---

## 🔮 Forecast Results (30-Day Projection)

| Forecast Day | Lower Bound | Predicted (yhat) | Upper Bound |
|---|---|---|---|
| Day +5  | INR 2,641 | INR 2,680 | INR 2,719 |
| Day +10 | INR 2,665 | INR 2,710 | INR 2,755 |
| Day +15 | INR 2,686 | INR 2,734 | INR 2,782 |
| Day +20 | INR 2,704 | INR 2,758 | INR 2,812 |
| Day +30 | INR 2,738 | INR 2,801 | INR 2,864 |

> The model projects a **gradual upward continuation** with confidence intervals widening as the forecast horizon extends — statistically expected behaviour.

---

## 📈 Key Findings

- The **20-Day MA trended above the 50-Day MA** for most of 2023, signalling sustained bullish sentiment
- A **consolidation phase** was observed mid-2024 where the two moving averages converged
- **Average daily return of +0.043%** indicates a positive bias throughout the analysis period
- **Return volatility** (std dev ~1.1%) reflects moderate, investable risk

---

## 📋 Power BI Dashboard Components

| Component | Description |
|---|---|
| KPI Cards | Current price, average return, max gain/loss |
| Price Trend Chart | Close price with MA_20 & MA_50 overlays |
| Volume Analysis | Monthly trading volume grouped by year |
| Daily Returns | Area chart with zero-baseline reference |
| Forecast View | Ribbon chart with yhat confidence bands |
| Monthly Heatmap | Average close prices by month and year |

---

## 🔭 Future Scope

- [ ] Integrate **sentiment analysis** from financial news for enhanced forecast accuracy
- [ ] Add advanced indicators: **RSI, MACD, Bollinger Bands**
- [ ] Extend forecasting to **90-day and 180-day** horizons
- [ ] Build a **live Power BI dashboard** with real-time API refresh
- [ ] Benchmark Prophet against **LSTM and XGBoost** models

---

## 📚 References

- [Yahoo Finance API](https://finance.yahoo.com) — Historical stock data source
- [Facebook Prophet Documentation](https://facebook.github.io/prophet/)
- [yfinance Python Library](https://pypi.org/project/yfinance/)
- NSE India — [RELIANCE.NS](https://www.nseindia.com)

---

## 📄 License

This project is developed for academic purposes under the Data Analytics curriculum (2024–2025).

---

<p align="center">
  Made with ❤️ using Python, Prophet & Power BI
</p>
