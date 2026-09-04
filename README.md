FinOps Autopilot
Agentic Financial Reconciliation & Exception Resolution Platform

FinOps Autopilot is an intelligent financial operations platform designed to automate payment reconciliation, detect settlement exceptions, identify anomalous transactions using machine learning, and assist with exception resolution.

🚀 Features
Payment reconciliation
Settlement matching
Missing settlement detection
Settlement mismatch detection
Exception severity classification
Bulk reconciliation
ML-based anomaly detection
Agent-assisted exception resolution
Real-time operational dashboard
Exception management
Payment Operations monitoring
PostgreSQL persistence
Automated dashboard refresh
🏗️ System Architecture
                    ┌──────────────────────┐
                    │    React Dashboard    │
                    │      Vite + Axios     │
                    │    localhost:5173     │
                    └───────────┬──────────┘
                                │
                                ▼
                    ┌──────────────────────┐
                    │       FastAPI        │
                    │      Backend API     │
                    │    localhost:8000    │
                    └───────────┬──────────┘
                                │
              ┌─────────────────┼─────────────────┐
              │                 │                 │
              ▼                 ▼                 ▼
      ┌──────────────┐  ┌──────────────┐  ┌────────────────┐
      │Reconciliation│  │ ML Detection │  │Resolution Agent│
      │   Service    │  │ Scikit-learn │  │    Workflow    │
      └──────┬───────┘  └──────┬───────┘  └───────┬────────┘
             │                 │                  │
             └─────────────────┼──────────────────┘
                               ▼
                    ┌──────────────────────┐
                    │      PostgreSQL      │
                    │       finops DB      │
                    └──────────────────────┘

🔄 How It Works
Payment Data
     │
     ▼
Reconciliation
     │
     ├──────── Match ──────────────► Successful
     │
     └──────── Mismatch/Missing
                    │
                    ▼
            Exception Detection
                    │
                    ▼
          Severity Classification
                    │
                    ▼
           ML Anomaly Detection
                    │
                    ▼
             Resolution Agent
                    │
                    ▼
             Dashboard Update

🧠 Core Components
Payment Reconciliation

Compares payment records against settlement records and identifies whether transactions are successfully reconciled.

Exception Detection

Detects financial exceptions including:

Missing settlements
Settlement mismatches
Amount differences
High-value discrepancies
Severity Classification

Exceptions are automatically classified into:

CRITICAL
HIGH
MEDIUM
ML Anomaly Detection

Uses Scikit-learn to identify unusual payment activity based on transaction and settlement-related features.

The ML service produces an anomaly score and prediction for each payment.

Prediction: -1 → Anomaly
Prediction:  1 → Normal

Resolution Agent

The Resolution Agent processes detected exceptions and updates their operational status.

Users can trigger exception resolution directly from the dashboard.

📊 Demo Data

The current development environment contains:

Metric	Value
Payments	20
Settlements	1
Exceptions	20
Settlement Mismatch	PAY_000001
Missing Settlements	19
ML Anomaly Detection	Enabled
Resolution Agent	Enabled
Example Exception
Payment ID:       PAY_000001
Expected Amount:  3710.34 EUR
Received Amount:  3690.34 EUR
Difference:       20.00 EUR
Exception Type:   SETTLEMENT_MISMATCH
Severity:         HIGH

🛠️ Technology Stack
Layer	Technology
Frontend	React
Build Tool	Vite
HTTP Client	Axios
Backend	FastAPI
Language	Python
ORM	SQLAlchemy
Database	PostgreSQL
Database Driver	Psycopg2
Machine Learning	Scikit-learn
Runtime	Python + Node.js
📁 Project Structure
finops-autopilot/
│
├── backend/
│   ├── app/
│   │   ├── agents/
│   │   │   └── resolution_agent.py
│   │   │
│   │   ├── api/
│   │   │   └── dashboard.py
│   │   │
│   │   ├── db/
│   │   │   ├── base.py
│   │   │   └── database.py
│   │   │
│   │   ├── ml/
│   │   │   └── anomaly_detector.py
│   │   │
│   │   ├── models/
│   │   │   ├── customer.py
│   │   │   ├── merchant.py
│   │   │   ├── payment.py
│   │   │   ├── settlement.py
│   │   │   └── exception.py
│   │   │
│   │   ├── services/
│   │   │   ├── reconciliation.py
│   │   │   └── bulk_reconciliation.py
│   │   │
│   │   └── main.py
│   │
│   ├── data/
│   └── requirements.txt
│
├── frontend/
│   ├── src/
│   │   ├── App.jsx
│   │   ├── App.css
│   │   └── main.jsx
│   │
│   ├── package.json
│   └── vite.config.js
│
└── README.md

⚙️ Backend Setup

Open a terminal and navigate to the backend:

cd backend


Activate the virtual environment:

venv\Scripts\activate


Start the FastAPI server:

uvicorn app.main:app --reload


Backend:

http://127.0.0.1:8000


API documentation:

http://127.0.0.1:8000/docs


Health check:

http://127.0.0.1:8000/health

💻 Frontend Setup

Open a second terminal:

cd frontend


Install dependencies:

npm install


Start the development server:

npm run dev


Frontend:

http://localhost:5173

🔌 API Endpoints
Health Check
GET /health


Checks backend and PostgreSQL connectivity.

Dashboard Summary
GET /dashboard/summary


Returns payment, settlement, exception, severity, and status statistics.

Exceptions
GET /dashboard/exceptions


Returns all detected financial exceptions.

Payments
GET /payments


Returns processed payment records for the Payment Operations dashboard.

Reconcile Payment
POST /reconcile/{payment_id}


Reconciles an individual payment against its settlement.

Example:

POST /reconcile/PAY_000001

Reconcile All
POST /reconcile-all


Runs reconciliation across all payments.

ML Anomalies
GET /ml/anomalies


Runs ML-based anomaly detection against payment data.

Resolve Exception
POST /exceptions/{exception_id}/resolve


Processes an exception through the Resolution Agent.

Example:

POST /exceptions/EXC_PAY_000020/resolve

🖥️ Dashboard

The React dashboard provides an operational interface for monitoring the financial reconciliation workflow.

Dashboard capabilities
System health monitoring
Payment statistics
Settlement statistics
Exception statistics
Severity overview
Payment Operations table
Bulk reconciliation
ML anomaly detection
Exception management
Resolution Agent actions
Automatic dashboard refresh
🔐 Database

FinOps Autopilot uses PostgreSQL for persistent financial operations data.

Main database entities
Customers
Merchants
Payments
Settlements
Exceptions


SQLAlchemy is used as the ORM layer between the FastAPI application and PostgreSQL.

🧪 End-to-End Demo

Start the backend:

cd backend
venv\Scripts\activate
uvicorn app.main:app --reload


Start the frontend in another terminal:

cd frontend
npm install
npm run dev


Open the dashboard:

http://localhost:5173


From the dashboard, users can:

Run Reconciliation
        ↓
Detect Exceptions
        ↓
Run ML Anomaly Detection
        ↓
Review Exceptions
        ↓
Resolve Exceptions
        ↓
Dashboard Refresh

📈 Project Status
MVP Complete ✅
 PostgreSQL database
 SQLAlchemy models
 Synthetic financial data
 Payment reconciliation
 Settlement matching
 Missing settlement detection
 Settlement mismatch detection
 Exception severity classification
 Bulk reconciliation
 ML anomaly detection
 Resolution Agent
 FastAPI backend
 REST APIs
 React dashboard
 Exception management
 Payment Operations dashboard
 Automated dashboard refresh
 GitHub repository
🎯 Purpose

FinOps Autopilot is designed as an internal financial operations platform for teams that need to monitor payment transactions, reconcile settlements, identify financial discrepancies, detect anomalous activity, and streamline exception handling.

The project demonstrates how financial operations, automation, machine learning, APIs, and agent-based workflows can be combined into a unified operational platform.

🚀 Quick Start
Terminal 1 — Backend
cd backend
venv\Scripts\activate
uvicorn app.main:app --reload

Terminal 2 — Frontend
cd frontend
npm install
npm run dev

Dashboard
http://localhost:5173

API Documentation
http://127.0.0.1:8000/docs

👨‍💻 Project

FinOps Autopilot

Agentic Financial Reconciliation & Exception Resolution Platform

Built with:

Python · FastAPI · React · Vite · PostgreSQL · SQLAlchemy · Scikit-learn · Axios
