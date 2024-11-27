# Modus AI ML Engineer Task
## Overview

This project implements an anomaly detection system for identifying fraudulent transactions among merchants using an **autoencoder neural network**. The system processes merchant transactions, engineers features, trains on normal data, and identifies anomalies based on reconstruction errors.

---

## Features

1. **Data Simulation**:
   - Generates a dataset with 1000 unique merchants.
   - Simulates 30 days of transactions for each merchant.
   - Ensures 20% of the transactions exhibit fraudulent behavior.

2. **Fraud Patterns**:
   - **Late Night Trading**: Transactions occur outside normal business hours.
   - **Sudden Activity Spike**: An unusually high volume of transactions.
   - **Customer Concentration**: Transactions clustered around a few customer IDs.

3. **Feature Engineering**:
   - Aggregates transaction data for each merchant.
   - Computes statistical features such as `total_txns`, `avg_amount`, `max_amount`, `min_amount`, and `night_txn_ratio`.

4. **Autoencoder Model**:
   - Detects anomalies by reconstructing input features and calculating reconstruction errors.
   - Trains on normal (non-fraudulent) data and identifies transactions with high reconstruction errors as fraudulent.

5. **Output**:
   - Anomalous transactions are flagged with their anomaly scores.
   - Metrics like **Accuracy**, **Precision**, **Recall**, and **F1 Score** are calculated.

6. **Data Persistence**:
   - Full dataset saved as `all_transactions.csv`.
   - Test results with predictions saved as `test_results.csv`.

---

## Files

| File Name              | Description                                                   |
|------------------------|---------------------------------------------------------------|
| `main.py`              | Python script containing the implementation of the fraud detection system. |
| `README.md`            | Documentation for the project.                               |


[This link](https://drive.google.com/drive/folders/1EFECZyVRZoyVRLuU28edbOqk8ADCfZRJ?usp=sharing) contains `all_transactions.csv` and `test_results.csv` .

---

## Setup and Requirements

### Prerequisites

- Python 3.8 or higher
- Required Python libraries:
  - `pandas`
  - `numpy`
  - `sklearn`
  - `keras`
  - `tensorflow`

### Installation

1. Clone the repository or download the script.
2. Install the required libraries using pip:

   ```bash
   pip install pandas numpy scikit-learn keras tensorflow
   ```

3. Run the script:

   ```bash
   python main.py
   ```

---

## Usage

1. **Data Simulation**:
   - The script generates synthetic merchant transaction data and injects fraudulent patterns.
   - Modify parameters like `merchant_count` or fraud patterns in the script if needed.

2. **Training and Detection**:
   - The autoencoder model is trained on normal transaction data.
   - Anomaly scores are computed for the test dataset, and fraud predictions are made.

3. **Results**:
   - Fraudulent transactions are flagged in `test_results.csv`.
   - Metrics for model performance are displayed in the console.

---

## Outputs

1. **Full Transaction Dataset** (`all_transactions.csv`):
   - Contains all transactions, including normal and fraudulent ones.
   - Key columns:
     - `merchant_id`
     - `amount`
     - `velocity_flag`
     - `time_flag`
     - `fraud`

2. **Test Results** (`test_results.csv`):
   - Contains anomaly scores and predictions for the test dataset.
   - Key columns:
     - `merchant_id`
     - `anomaly_score`
     - `predicted_fraud`
     - `fraud` (true label)

---


## Customization

1. **Merchant Count**:
   - Change the number of merchants by modifying the `merchant_count` variable in the script.

2. **Fraud Injection**:
   - Adjust the proportion of fraud by changing the probability in the fraud injection block (`random.random() < 0.2`).

3. **Model Hyperparameters**:
   - Modify the autoencoder architecture or training parameters (e.g., epochs, batch size).

---


### Dataset Samples

#### `all_transactions.csv`
| transaction_id | merchant_id | amount  | velocity_flag | time_flag | fraud |
|----------------|-------------|---------|---------------|-----------|-------|
| TXN1234567890  | M12345678   | 150.75  | False         | False     | 0     |
| TXN0987654321  | M87654321   | 7500.00 | True          | True      | 1     |

#### `test_results.csv`
| merchant_id | anomaly_score | predicted_fraud | fraud |
|-------------|---------------|-----------------|-------|
| M12345678   | 0.0025        | 0               | 0     |
| M87654321   | 0.0728        | 1               | 1     |

