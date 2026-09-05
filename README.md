# Regime-Aware Hybrid GARCH-LSTM Ensemble for Nasdaq-100 Volatility Forecasting

## **Overview**

This repository contains the code and results for a master's thesis investigating volatility forecasting for the Nasdaq-100 index.

The study compares traditional econometric models, deep learning, and hybrid approaches, including GARCH-family models, LSTM, a hybrid GARCH-LSTM model, and a GMM-based regime-aware ensemble.

## **Research Question**

The study investigates whether integrating traditional econometric models with deep learning and regime-aware approaches can improve the out-of-sample forecasting of Nasdaq-100 realized volatility.

Specifically, it examines whether:

1. The developed models improve upon benchmark forecasting methods.
2. LSTM outperforms GARCH-family models.
3. Incorporating GARCH forecasts improves standalone LSTM performance.
4. A GMM-based regime-aware ensemble improves upon the hybrid LSTM model.

## **Methodology**

The forecasting framework consists of the following stages:
---
```text
               ┌──────────────────────────────┐
               │     Nasdaq-100 OHLC Data     │
               └──────────────┬───────────────┘
                              │
                              ▼
               ┌──────────────────────────────┐
               │  Yang-Zhang Realized Vol.    │
               └──────────────┬───────────────┘
                              │
          ┌───────────────────┼───────────────────┐
          ▼                   ▼                   ▼
    ┌───────────┐     ┌───────────────┐   ┌───────────────┐
    │Benchmarks │     │ GARCH-family  │   │Standalone LSTM│
    └─────┬─────┘     └───────┬───────┘   └───────┬───────┘
          │                   │                   │
          │                   └─────────┬─────────┘
          │                             ▼
          │                     ┌───────────────┐
          │                     │  Hybrid LSTM  │
          │                     └───────┬───────┘
          │                             │
          │     ┌───────────────────────┤
          │     │ GMM Regime Detection  │
          │     └───────────┬───────────┘
          │                 ▼
          │     ┌───────────────────────┐
          │     │ Regime-Aware Ensemble │
          │     └───────────┬───────────┘
          │                 │
          └─────────┬───────┘
                    ▼
      ┌───────────────────────────┐
      │     Model Evaluation      │
      │  QLIKE • MAE • RMSE • DM  │
      └───────────────────────────┘

Benchmark models include the Historical Average, Simple Moving Average (SMA), and Simple Exponential Smoothing (SES). GARCH-family models include GARCH, EGARCH, and GJR-GARCH, estimated under Normal, Student's t, and skewed Student's t innovation distributions.

The hybrid LSTM uses forecasts from multiple GARCH-family models as additional input features. The regime-aware ensemble combines the best-performing GARCH model with the standalone LSTM using GMM-derived regime probabilities, used to determine their relative contribution under different market conditions.

## **Key Findings**

The empirical results show that:

* SES achieved the best overall forecasting performance among the models considered.
* Standalone LSTM outperformed the GARCH-family models in out-of-sample forecasting.
* The hybrid LSTM improved upon the standalone LSTM by incorporating GARCH forecasts as additional inputs.
* TThe regime-aware ensemble did not outperform the hybrid LSTM, indicating that the GMM-based combination did not provide additional forecasting gains.

## **Repository Structure**
---
```text
├── data/        # Data and data preparation 
├── notebooks/   # Analysis and forecasting workflows 
├── src/         # Reusable Python modules 
├── results/     # Model results and statistical tests 
├── figures/     # Generated visualizations 
├── thesis/      # Final thesis 
├── requirements.txt 
└── README.md
```text

## **Thesis**

**A Regime-Aware Hybrid GARCH-LSTM Ensemble Framework for Forecasting Nasdaq-100 Realized Volatility**

**Author:** Tran Hoang Mai · 2026
