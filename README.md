# Financial News Sentiment vs NIFTY50 Analysis

## Project Overview

This project investigates whether financial news sentiment, combined with NIFTY50 market features, can help predict the next-day direction of the NIFTY50 index.

The project combines financial news data with NIFTY50 market data, performs sentiment-based feature engineering, and evaluates multiple machine learning models for next-day market direction prediction.

---

## Objectives

- Analyze financial news sentiment.
- Combine sentiment information with NIFTY50 market data.
- Engineer features such as sentiment moving averages, sentiment volatility, market movement lags, volume change, and high-low spread.
- Predict the next-day direction of the NIFTY50.
- Compare multiple machine learning models.
- Evaluate whether model predictions can translate into better market performance.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- XGBoost
- Google Colab
- GitHub

---

## Methodology

The project follows these major steps:

1. Load and clean financial news and NIFTY50 datasets.
2. Process financial news and calculate sentiment scores.
3. Aggregate news sentiment by date.
4. Engineer rolling sentiment features and market-based features.
5. Create a next-day market direction target.
6. Split the data chronologically into training and testing periods.
7. Train and evaluate:
   - Logistic Regression
   - Random Forest
   - XGBoost
8. Perform time-series cross-validation for Random Forest tuning.
9. Analyze Random Forest feature importance.
10. Backtest the Random Forest prediction strategy against a buy-and-hold strategy.

---

## Models Evaluated

| Model | Test Accuracy |
|---|---:|
| Majority Baseline | 44% |
| Logistic Regression | 44% |
| Random Forest | 48% |
| XGBoost | 40% |
| Tuned Random Forest | 44% |

Random Forest achieved the highest initial test accuracy of 48%, although the improvement over the majority baseline was limited.

---

## Key Findings

- Random Forest performed best among the initial models with 48% test accuracy.
- Logistic Regression performed at the same level as the majority-class baseline.
- XGBoost achieved 40% test accuracy.
- Hyperparameter tuning did not improve Random Forest performance on the held-out test set.
- `volume_change` and `high_low_spread` were among the most important features.
- Rolling sentiment features, particularly `sentiment_ma7`, showed meaningful feature importance.
- The raw daily `sentiment_score` had lower feature importance than several engineered features.

---

## Backtesting Results

The Random Forest predictions were used in a simple next-day trading strategy.

| Strategy | Return |
|---|---:|
| Random Forest Strategy | -2.14% |
| Market Buy & Hold | -1.05% |

The model-based strategy underperformed the buy-and-hold market strategy during the tested period.

---

## Conclusion

The results suggest that the available financial news sentiment and market features provided only limited predictive information for next-day NIFTY50 direction in this dataset.

Although Random Forest achieved the highest initial accuracy among the evaluated models, its performance remained close to the majority baseline, and the corresponding trading strategy did not outperform the market.

The analysis demonstrates the challenges involved in predicting short-term financial market movements using sentiment and historical market features.

---

## Project Files

- `financial_news_nifty50_analysis.ipynb` — Complete analysis and machine learning workflow.
- `final_project_dataset.csv` — Final processed dataset used for modelling.
- `data/` — Source datasets.
- `plots/` — Project visualizations.
- `requirements.txt` — Python dependencies.
