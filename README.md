**Bank Transaction Fraud Detection Using Machine Learning**

This repository presents a complete machine‑learning framework for detecting fraudulent bank transactions using both unsupervised anomaly detection and supervised classification. The project analyzes real‑world financial behavior using the Kaggle Bank Transaction Dataset and demonstrates how ML can significantly improve fraud detection accuracy.

“Financial fraud represents a significant challenge for banking institutions, costing billions annually.”

**Executive Summary**

Global Fraud Losses: $30B annually

Dataset Size: 2,512 transactions

Model Accuracy: 97% (Random Forest)

This project combines Isolation Forest for anomaly detection and Random Forest for classification, achieving strong predictive performance while uncovering key fraud indicators.

**Problem Statement**

Traditional rule‑based fraud detection systems:

Fail to adapt to evolving fraud patterns

Generate excessive false positives

Require heavy manual intervention

Project Objectives
Identify key indicators of fraudulent transactions

Apply ML algorithms to detect anomalies

Improve detection accuracy through feature engineering

Reduce false positives while maximizing fraud capture

**Dataset Overview**

Source: Kaggle – Bank Transaction Dataset
Total Records: 2,512 transactions

Feature Categories
Transaction: Amount, Type, Timestamp

Channel: Device ID, IP Address, Browser

Customer: Age, Account Balance, Login Attempts

Data Quality:

No missing values

No duplicates

Clean and analysis‑ready

**Exploratory Data Analysis (EDA)**

Univariate Insights
Transaction amounts are right‑skewed

Account balances cluster into three customer segments

Transaction durations show a bimodal pattern

Categorical Insights
Credit transfers: 42%

Debit card: 28%

Wire transfers: 16%

Metropolitan areas show higher transaction frequency

Temporal Patterns
Peak activity: 10 AM – 4 PM

Highest volume: Fridays

Seasonal spikes: month‑end & holidays

**Feature Engineering**

Temporal Features
TransactionHour

TransactionDay

WeekdayVsWeekend

Behavioral Features
TimeSinceLastTransaction

TransactionFrequency

LoginToTransactionTime

Financial Features
AmountToBalanceRatio

TypicalAmountDeviation

AmountVsHistoricalAverage

After encoding and removing irrelevant identifiers, the final dataset contained 32 engineered features.

**Anomaly Detection — Isolation Forest**

Contamination: 5% (industry standard)

Anomalies Detected: 126 suspicious transactions

Key Observations
Anomalies cluster around low account balances + high transaction amounts

Strong indicator of fraudulent behavior

Effective for identifying novel fraud patterns

**Predictive Modeling — Random Forest**

Training Setup
Labels derived from Isolation Forest anomalies

80% training, 20% testing

Default hyperparameters initially

Model Performance
Metric	Score
Accuracy	97%
Precision (Fraud)	0.81
Recall (Fraud)	0.52
F1‑Score (Fraud)	0.63
Confusion Matrix Summary
True Negatives: 478

True Positives: 13

False Negatives: 12

False Positives: 3

The model is highly precise but misses some fraud cases — a common tradeoff in fraud detection.

**Model Improvement — Hyperparameter Tuning**
Using GridSearchCV (5‑fold cross‑validation):

Best Parameters:

n_estimators = 200

max_depth = 10

max_features = 'sqrt'

Outcome:

Same 97% accuracy

Improved robustness and lower variance

**Key Insights**
Strong Fraud Indicators
High transaction amount relative to low balance

Rapid consecutive transactions from different locations

Multiple failed login attempts before a successful transaction

Technical Recommendations
Deploy real‑time alerting for high‑risk patterns

Use hybrid unsupervised + supervised models

Automate retraining pipelines to adapt to new fraud tactics

Operational Integration
Connect model outputs to fraud management systems via APIs

Generate customer‑specific risk scores

Build dashboards for fraud analysts

**Conclusion & Future Work**

Achievements
Built a robust ML fraud detection pipeline

Combined anomaly detection + classification

Achieved 97% accuracy

Identified actionable fraud indicators

Limitations
Class imbalance affects recall

Static dataset doesn’t capture evolving fraud patterns

Some fraudulent transactions remain undetected

Future Enhancements
Apply advanced sampling (SMOTE, ADASYN)

Integrate streaming data for real‑time detection

Explore deep learning architectures

Add explainable AI for regulatory compliance
