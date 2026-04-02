🚀 MarketFlow — Real-Time Crypto Analytics Platform

A fully containerized end-to-end data engineering project that streams, processes, stores, and visualizes real-time cryptocurrency data using modern data stack tools.

📌 Project Overview

MarketFlow is a real-time data pipeline that:

Streams live crypto price data
Processes it using distributed computing
Stores it in a data lake
Runs analytics & anomaly detection
Displays insights through an interactive dashboard

This project demonstrates production-level architecture using tools like Kafka, Spark, Airflow, and Docker.

🏗️ Architecture
        ┌────────────┐
        │  API Data  │
        └─────┬──────┘
              ↓
        ┌────────────┐
        │   Kafka    │  ← Streaming Layer
        └─────┬──────┘
              ↓
   ┌─────────────────────┐
   │ Spark Streaming     │
   │ (Kafka → MinIO)     │
   └─────────┬───────────┘
             ↓
        ┌────────────┐
        │   MinIO    │  ← Data Lake (S3)
        └─────┬──────┘
              ↓
   ┌─────────────────────┐
   │ Spark Analytics     │
   │ (Batch Processing)  │
   └─────────┬───────────┘
             ↓
        ┌────────────┐
        │ Postgres   │  ← Data Warehouse
        └─────┬──────┘
              ↓
   ┌─────────────────────┐
   │ Dashboard API       │
   └─────────┬───────────┘
             ↓
   ┌─────────────────────┐
   │ React Dashboard UI  │
   └─────────────────────┘
🧰 Tech Stack
⚙️ Backend & Data Engineering
Apache Kafka — Streaming
Apache Spark — Processing (Streaming + Batch)
Apache Airflow — Orchestration
PostgreSQL — Data Warehouse
MinIO — Data Lake (S3 compatible)
🌐 Frontend
React (Vite)
Tailwind CSS
Recharts
🐳 DevOps
Docker & Docker Compose
Nginx (Reverse Proxy)
📂 Project Structure
├── dags/                  # Airflow DAGs
├── spark-jobs/            # Spark Streaming & Analytics Jobs
├── dashboard/
│   ├── api/               # Backend API
│   └── ui/                # React Frontend
├── postgres/
│   └── init.sql           # DB initialization
├── docker-compose.yml     # Multi-service orchestration
⚡ Features

✔ Real-time crypto data streaming using Kafka
✔ Distributed data processing using Spark
✔ Data lake storage using MinIO (S3)
✔ Batch analytics with Spark
✔ Workflow orchestration with Airflow
✔ REST API for serving processed data
✔ Interactive dashboard with charts
✔ Fully Dockerized setup (one command deployment)

🚀 Getting Started
1️⃣ Clone the Repository
git clone https://github.com/your-username/marketflow.git
cd marketflow

2️⃣ Create .env File
Create a .env file in root:

POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=crypto

AIRFLOW_DB_USER=airflow
AIRFLOW_DB_PASSWORD=airflow
AIRFLOW_DB_NAME=airflow

AIRFLOW_ADMIN_USER=admin
AIRFLOW_ADMIN_PASSWORD=admin
AIRFLOW_ADMIN_EMAIL=admin@example.com

MINIO_ROOT_USER=minioadmin
MINIO_ROOT_PASSWORD=minioadmin

KAFKA_BROKER=kafka:9092
KAFKA_TOPIC=crypto-prices

3️⃣ Run the Project
docker-compose up --build

4️⃣ Access Services
Service	URL
Airflow UI	http://localhost:8080

Dashboard UI	http://localhost:3000

MinIO Console	http://localhost:9001

API	http://localhost:8000

🔄 Data Flow
1. Crypto data fetched via API
2. Produced to Kafka topic
3. Spark Streaming consumes Kafka
4. Data stored in MinIO (Parquet format)
5. Spark Analytics processes data
6. Results stored in PostgreSQL
7. Dashboard fetches via API

📊 Dashboard
The frontend provides:
📈 Real-time price trends
📉 Historical analysis
🚨 Anomaly detection alerts


🧪 Future Improvements
-Add authentication (JWT)
-Deploy on AWS/GCP
-Add CI/CD pipeline
-Improve anomaly detection with ML models
-Add more financial indicators

📜 License

This project is licensed under the MIT License.