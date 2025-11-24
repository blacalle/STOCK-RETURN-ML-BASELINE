# Stock Return & Volatility Explorer + ML Baseline

This project is a first end-to-end financial data science pipeline inspired by AI-driven investment analytics platforms (e.g., BridgeWise-like workflows).

## Goal
Build a simple but complete ML baseline to predict whether the next-day stock return is positive (1) or negative (0), using historical OHLCV data and basic technical indicators.

> This is an educational project focused on learning financial data handling, feature engineering, and time-series ML validation — not on producing a tradable strategy.

---

## Dataset
Daily OHLCV prices downloaded from Yahoo Finance via `yfinance`.

- Asset example: `ASML.AS` (Euronext)
- Period: 2018-01-01 to 2025-01-01
- Features include price-based indicators and rolling statistics.

---

## Pipeline Overview
1. **Data loading**
   - Download OHLCV data with `yfinance`
2. **EDA**
   - Price evolution
   - Daily returns distribution
   - Rolling annualized volatility (20d)
3. **Cleaning**
   - Sort by date, remove duplicates
   - Drop NaNs created by rolling windows
4. **Feature engineering**
   - SMA / EMA
   - RSI (14)
   - MACD + signal
   - Bollinger Bands width
   - Returns over multiple horizons (1d, 5d, 10d)
   - Volume change
5. **Target**
   - `target = 1` if next-day return > 0 else `0`
6. **Model**
   - Random Forest Classifier (baseline)
   - **TimeSeriesSplit** cross-validation (no shuffling)
7. **Evaluation**
   - Accuracy across folds
   - Hold-out test on last 20%
   - Feature importance interpretation

---

## Results (baseline)
Typical accuracy is slightly above random (≈0.52–0.56), which is expected in liquid markets.

Key takeaways:
- Technical indicators provide weak predictive signals.
- Performance is unstable across regimes → next steps should focus on richer features.

---

## How to run
```bash
pip install -r requirements.txt


#ñeee