## Fraud Detection System

This project is designed to detect fraudulent transactions using Apache Kafka for data streaming, MongoDB for storage, and an email alert system for notifying about fraudulent transactions.

### 📌 Project Components

1. **Producer (**``**)**

   - Generates synthetic transaction data using the `Faker` library.
   - Streams data to a Kafka topic (`txndata`).

2. **Consumer & Fraud Detection (**``**)**

   - Consumes transactions from the Kafka topic.
   - Applies fraud detection logic (e.g., transactions above a threshold are flagged).
   - Stores fraud transactions in MongoDB under the `fraud_alerts` collection.

3. **Alert System (**``**)**

   - Monitors the `fraud_alerts` collection in MongoDB.
   - Sends email notifications when a fraudulent transaction is detected.

### ⚙️ Tech Stack

- **Apache Kafka** (for real-time data streaming)
- **MongoDB** (for data storage)
- **Python Libraries:**
  - `confluent_kafka` (for Kafka Producer/Consumer)
  - `faker` (for synthetic data generation)
  - `pymongo` (for MongoDB interaction)
  - `smtplib` (for sending email alerts)

### 🚀 Setup Instructions

1. **Install Dependencies**

   ```sh
   pip install confluent_kafka pymongo faker
   ```

2. **Start Kafka Producer**

   - Run `producer_for_fraud_data.ipynb` to stream transactions to Kafka.

3. **Start Fraud Detection Consumer**

   - Run `fraud data processing and storing into mongo.ipynb` to analyze transactions.

4. **Start Alert System**

   - Run `send_alert.ipynb` to monitor fraud transactions and send email alerts.

### 🔍 Fraud Detection Logic

A transaction is flagged as fraudulent if:

```python
fraud_score = transaction['amount'] / 5000
return fraud_score > 0.8
```

Any transaction where the amount exceeds 80% of ₹5000 is considered fraudulent.

### 📧 Email Alerts

- Fraudulent transactions trigger an email alert with details such as transaction ID, user ID, amount, merchant, and location.

