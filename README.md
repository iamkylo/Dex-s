# Dex's

# Ethereum Transaction Monitoring & Fraud Detection

This project monitors **pending Ethereum transactions** in real-time, extracts relevant on-chain data, and runs it through a **Machine Learning (ML) API** to detect potential fraudulent activities.  

## 📌 Features
- Fetch **pending transactions** directly from the Ethereum mempool
- Extract and log transaction details such as:
  - `wallet_address` *(string)*
  - `timestamp` *(string)*
  - `token_pair` *(string)*
  - `amount` *(number)*
  - `total_value_locked_usd` *(number)*
  - `liquidity_change` *(number)*
  - `price_usd` *(number)*
  - `price_change` *(number)*
  - `gasPrice` *(number)*
  - `gasUsed` *(number)*
  - `value` *(number)*
  - `from_address` *(string)*
  - `to_address` *(string)*
- Send transaction data to a **hosted ML model API** for fraud prediction
- Display ML prediction and fraud probability in real-time

## 🛠 Tech Stack
- **Node.js** — Ethereum mempool listener
- **Ethers.js / Web3.js** — Blockchain interaction
- **Axios / Fetch** — API calls to ML service
- **Python (FastAPI)** — Machine Learning model hosting
- **Ethereum Node Provider** — Infura / Alchemy / Local Geth node

## 🚀 Installation
1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/eth-fraud-monitor.git
   cd eth-fraud-monitor
Install dependencies

npm install


Set up environment variables in .env

INFURA_API_KEY=your_infura_key
ML_API_URL=https://your-ml-api.com/predict_fraud


Run the mempool listener

node index.js

📊 API Response Example

Request Payload:

{
  "wallet_address": "0x1..........",
  "timestamp": "2025-08-14 10:24:00",
  "token_pair": "ETH/USDT",
  "amount": 1000.0,
  "total_value_locked_usd": 500000.0,
  "liquidity_change": 100.0,
  "price_usd": 2000.0,
  "price_change": 2.0,
  "gasPrice": 50,
  "gasUsed": 21000,
  "value": 1.5,
  "from_address": "0xabc...",
  "to_address": "0xdef..."
}


ML API Response:

{
  "is_fraud_pred": true,
  "xgb_fraud_prob": 0.85,
  "fraud_type_pred": "sandwich_attack"
}

📌 Notes

Ensure your Ethereum node provider supports pending transaction subscription

The ML API must be deployed before running the listener

You can use FastAPI + XGBoost/LightGBM for the ML backend
