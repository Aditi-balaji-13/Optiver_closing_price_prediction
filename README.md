# Optiver’s Trading at the Close  
### By Aditi Balaji, Janhavi Sathe

## 📝 Introduction

In this project, we tackle the Kaggle competition [Optiver - Trading at the Close](https://www.kaggle.com/competitions/optiver-trading-at-the-close), which involves building a model to predict closing price movements for 200 Nasdaq-listed stocks using data from the order book and closing auction.

In addition to the competition dataset, we explore augmenting with social media sentiment and expert predictions to provide broader context for stock performance. This is experimental and not part of the main scope.

---

## ❓ Problem Statement

> “Stock exchanges are fast-paced, high-stakes environments... [see full statement on Kaggle](https://www.kaggle.com/competitions/optiver-trading-at-the-close).”

Each trading day on the Nasdaq concludes with the **Closing Cross auction**, determining the official prices of listed securities. Optiver, a global market maker, consolidates order book and auction book data to provide optimal pricing.  
The challenge is to predict the **closing price movement** using auction and order book data for 200 stocks.

---
$$ Project Structure
```text
├── COMP540_Aditi-Janhavi_Interim-Project-Report_20th-Nov.docx
├── COMP540_Aditi-Janhavi_Interim-Project-Report_25th-Oct.docx
├── COMP540_Aditi-Janhavi_Project-Proposal.docx
├── Leaderboard.png
├── fork-of-optiver-2023-basic-submission-demo.ipynb
├── notebook70273b6892.ipynb
└── whiteboard.docx
```
---

## 📂 Dataset

**Source**: [Kaggle Dataset](https://www.kaggle.com/competitions/optiver-trading-at-the-close/data)  
**Size**: ~5.2 million rows × 17 columns  
**Duration**: 481 trading days

### 🔑 Key Features:
- `stock_id`, `date_id`
- `imbalance_size`, `imbalance_buy_sell_flag`
- `reference_price`, `matched_size`, `near_price`, `far_price`
- `bid_price`, `ask_price`, `bid_size`, `ask_size`
- `wap` (weighted average price)
- `target`: 60-second future move of WAP relative to synthetic index

We also plan to integrate **social media sentiment** scores (range -1 to +1), collected using tools like [Information Tracer](https://informationtracer.com).

---

## 🧠 Model Selection

### Phase I: Basic Models
- **Baseline**: Predicting 0 for all samples
- **Last Value / Moving Average** (not used due to test data limitations)
- **Linear Regression**

### Phase II: Boosted Trees
- **XGBoost (XGB)**
- **LightGBM (LGBM)**

### Phase III: Neural Networks
- **Recurrent Neural Network (RNN)**
- **Long Short-Term Memory (LSTM)**

> Sentiment-enriched models will be experimented with using ensemble approaches.

---

## 🧪 Evaluation Procedure

Metric: **Mean Absolute Error (MAE)**  
Formula:
$$MAE = (1/n) * ∑ |yᵢ - xᵢ|$$

---

## 📈 Expected Results

- **Phase I**: Error ~10⁻¹ (e.g. 5.46%)
- **Phase II**: Boosted trees expected to marginally outperform baselines
- **Phase III**: Neural networks targeted to achieve error close to 3%

---

## 📚 Literature Review

- [Optiver’s Kaggle Tutorial Discussion](https://www.kaggle.com/competitions/optiver-trading-at-the-close/discussion/441590)
- [EDA Notebook by chiangken](https://www.kaggle.com/code/chiangken/introduction-and-explore-data-analysis)
- [ML Techniques for Stock Price](https://towardsdatascience.com/machine-learning-techniques-applied-to-stock-price-prediction-6c1994da8001)

### Social Media Prediction Literature:
- [IEEE: NASDAQ Trend Forecasting](https://ieeexplore.ieee.org/document/10108281)
- [Artificial Life & Robotics (2023)](https://doi.org/10.1007/s10015-023-00857-z)
- [CMC Journal on Big Data & Stocks](https://www.techscience.com/cmc/v67n2/41320/html)

---

## ⚙️ Technical Approach

- **Data**: [Kaggle Dataset](https://www.kaggle.com/competitions/optiver-trading-at-the-close/data)
- **Baseline Code**: [Google Drive](https://drive.google.com/file/d/1d0smsRQAZQGuFU6TKqZ5EbDoRhqRx94Z/view?usp=sharing)
- **XGBoost Model**: [Colab Notebook](https://colab.research.google.com/drive/1V7KK69pA0qfrjdMBntk3ZKAE02SIYz8N)
- **LightGBM**: [Notebook](https://www.kaggle.com/code/verracodeguacas/high-speed-predictions-no-gpu)
- **Linear Regression Reference**: [Discussion](https://www.kaggle.com/competitions/optiver-trading-at-the-close/discussion/442851)

We split our modeling into:
1. **Stage 1** – Basic and boosted models on i.i.d features
2. **Stage 2** – Data engineering + ensemble model + hyperparameter tuning

---

## 📊 Results Summary

| Model               | MAE (%)    |
|---------------------|------------|
| Predict 0           | 5.465      |
| Predict 1           | 5.5455     |
| Predict Mean        | 5.4648     |
| XGBoost             | 15.42      |

---

## 🔜 Future Work

- Implement and benchmark **LightGBM**, **Linear Regression**, **RNN**, and **LSTM**
- Incorporate social media features (if time allows)
- Explore ensemble-based enhancements and fine-tuning

---

## 🔗 Useful Links

- 💼 [Optiver Competition on Kaggle](https://www.kaggle.com/competitions/optiver-trading-at-the-close)
- 🧪 [Optiver Tutorial Notebook](https://www.kaggle.com/code/janhavihsathe/optiver-2023-basic-submission-demo/notebook)

---

## 📄 License

This work is licensed under the MIT License (if applicable).

---

