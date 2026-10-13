# A Behavior Consistency Framework for AI-Based Suspicious Transaction Detection in Banking Systems


An AI-powered web application that detects potentially fraudulent financial transactions using machine learning. SuspicioScan uses XGBoost, transaction feature engineering, and a real-time simulation dashboard to identify suspicious activity and support fraud monitoring.

## Features

- **Machine Learning Fraud Detection:** Uses an XGBoost model to classify transactions as normal or suspicious.
- **SMOTE-Based Training:** Addresses class imbalance by generating synthetic minority-class examples in the training data.
- **Receiver Familiarity Score (RFS):** Incorporates receiver transaction history as a feature.
- **Balance Change Score (BCS):** Incorporates transaction amount and balance-related signals to help identify suspicious behavior.
- **Real-Time Transaction Simulation:** Processes simulated transactions through a monitoring dashboard.
- **Fraud Alerts:** Displays transactions identified as potentially suspicious.
- **Performance Evaluation:** Compares model performance across three experimental stages.
- **Interactive Web Dashboard:** Provides transaction monitoring, statistics, and model predictions.

## Technologies Used

- Python
- Flask
- XGBoost
- Pandas
- NumPy
- Scikit-learn
- Imbalanced-learn (SMOTE)
- HTML, CSS, JavaScript
- PaySim dataset

## Dataset

This project uses the PaySim synthetic mobile money transaction dataset.

The dataset contains transaction details such as transaction type, amount, sender balance, recipient balance, and fraud labels.

**Note:** PaySim contains simulated financial transactions. SuspicioScan is a demonstration project and is not connected to a real banking system.

## Model Development

The project evaluates three stages:

1. **Stage 1 — Baseline Model:** XGBoost trained without SMOTE.
2. **Stage 2 — Baseline + SMOTE:** XGBoost trained using SMOTE to address class imbalance.
3. **Stage 3 — Proposed Model:** SMOTE-based training with additional Receiver Familiarity Score (RFS) and Balance Change Score (BCS) features.

All stages are evaluated on the same held-out test dataset for a fair comparison.

## Model Performance

The following results were obtained on a test dataset of 1,272,524 transactions, including 1,643 fraudulent transactions.

| Metric | Stage 1: Baseline | Stage 2: SMOTE | Stage 3: Proposed |
|---|---:|---:|---:|
| Accuracy | 99.96% | 99.88% | 99.90% |
| Precision | 89.29% | 52.89% | 55.70% |
| Fraud Recall | 78.64% | 98.72% | 98.11% |
| F1-Score | 83.62% | 68.87% | 71.06% |
| False Positives | 155 | 1,445 | 1,282 |

### Results Summary

- SMOTE increased fraud recall from 78.64% to 98.72%.
- The proposed Stage 3 model reduced false positives from 1,445 to 1,282 compared with Stage 2.
- Stage 3 improved precision from 52.89% to 55.70%.
- Stage 3 improved F1-score from 68.87% to 71.06%.
- Stage 3 maintained high fraud recall at 98.11%.

These results show the trade-off between catching fraudulent transactions and reducing false alarms.

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/Sanjaykumarsk19/AI_Project.git
cd YOUR-REPOSITORY
```

Replace `YOUR-USERNAME` and `YOUR-REPOSITORY` with your actual GitHub details.

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
```

Activate it:

**Windows**
```bash
venv\Scripts\activate
```

**Linux / macOS**
```bash
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

Ensure that `requirements.txt` includes the dependencies required by your project.

## Run the Application

Start the Flask application:

```bash
python app.py
```

Open the local address displayed in your terminal, commonly:

```text
http://127.0.0.1:5000
```

Use the dashboard to start transaction simulation, monitor transactions, review fraud alerts, and inspect model predictions.

## Project Structure

```text
SuspicioScan/
├── app.py
├── model/
│   └── xgb_fraud_model.json
├── data/
│   └── paysim.csv
├── templates/
│   └── index.html
├── static/
│   └── style.css
├── requirements.txt
└── README.md
```

*The structure above is illustrative. Adjust it to match the actual files and folders in your repository.*

## Evaluation Metrics

- **Accuracy:** Percentage of all transactions classified correctly.
- **Precision:** Percentage of transactions flagged as fraudulent that are actually fraudulent.
- **Recall:** Percentage of actual fraudulent transactions correctly detected.
- **F1-Score:** Harmonic mean of precision and recall.
- **False Positives:** Legitimate transactions incorrectly flagged as suspicious.

## Limitations

- PaySim is a synthetic dataset and may not represent all real-world banking behavior.
- Model performance on simulated data does not guarantee the same performance in a live banking environment.
- Fraud predictions are indicators for further review, not definitive proof of criminal activity.
- The current application demonstrates transaction monitoring and is not integrated with real bank payment systems.

## Future Enhancements

- Integrate additional transaction behavior features.
- Improve false-positive reduction while maintaining high fraud recall.
- Add downloadable fraud investigation reports.
- Explore explainable AI methods to clarify why transactions are flagged.
- Evaluate the model on additional datasets.

## Disclaimer

SuspicioScan is an academic final-year project developed for educational and demonstration purposes. It uses simulated transaction data and is not intended for direct use in production banking systems.

## Author

**Final-Year Project — AI-Based Suspicious Transaction Detection**

Developed using Python, Flask, XGBoost, and the PaySim dataset.

