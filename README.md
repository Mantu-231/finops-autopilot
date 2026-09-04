FinOps Autopilot

Agentic Financial Reconciliation & Exception Resolution Platform

FinOps Autopilot is an intelligent financial operations platform designed to automate payment reconciliation, detect settlement exceptions, identify anomalous transactions using machine learning, and assist with exception resolution.

Features
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
Tech Stack
Frontend
React
Vite
Axios
Backend
Python
FastAPI
Uvicorn
Database
PostgreSQL
SQLAlchemy
Psycopg2
Machine Learning
Scikit-learn
System Architecture
React Dashboard
      │
      ▼
FastAPI Backend
      │
      ├───────────────┬────────────────┐
      ▼               ▼                ▼
Reconciliation   ML Detection   Resolution Agent
      │               │                │
      └───────────────┼────────────────┘
                      ▼
                 PostgreSQL
                    finops

Core Components
Payment Reconciliation

Compares payment records with settlement records and determines whether transactions are successfully reconciled.

The reconciliation service identifies:

Successful matches
Missing settlements
Settlement mismatches
Amount differences
Exception Detection

Financial exceptions are automatically created when a payment cannot be successfully reconciled.

Supported exception types include:

MISSING_SETTLEMENT
SETTLEMENT_MISMATCH
Severity Classification

Detected exceptions are classified according to severity:

CRITICAL
HIGH
MEDIUM
Bulk Reconciliation

The platform supports reconciliation of all available payment records through a single API operation.

POST /reconcile-all

ML Anomaly Detection

The ML service uses Scikit-learn to identify unusual payment activity.

Each payment receives:

Anomaly Score
Prediction


Prediction values:

-1 → Anomaly
 1 → Normal

Resolution Agent

The Resolution Agent processes detected financial exceptions and updates their operational status.

OPEN exceptions can be processed directly from the React dashboard.

Demo Data

The current development environment contains:

Metric	Value
Payments	20
Settlements	1
Exceptions	20
Missing Settlements	19
Settlement Mismatch	PAY_000001
ML Anomaly Detection	Enabled
Resolution Agent	Enabled
Example Exception
Payment ID:       PAY_000001
Expected Amount:  3710.34 EUR
Received Amount:  3690.34 EUR
Difference:       20.00 EUR
Exception Type:   SETTLEMENT_MISMATCH
Severity:         HIGH

Project Structure
finops-autopilot/
│
├── backend/
│   │
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
│   │
│   ├── src/
│   │   ├── App.jsx
│   │   ├── App.css
│   │   └── main.jsx
│   │
│   ├── package.json
│   └── vite.config.js
│
└── README.md

Database Design
Customers

Stores customer information associated with payment transactions.

Merchants

Stores merchant information associated with financial transactions.

Payments

Stores payment transaction information including:

payment_id
customer_id
merchant_id
amount
currency
status
processor
created_at

Settlements

Stores settlement information used for payment reconciliation.

Exceptions

Stores detected reconciliation exceptions including:

exception_id
payment_id
exception_type
severity
expected_amount
actual_amount
difference
status
created_at

API Endpoints
Health Check
GET
/health


Checks backend and database connectivity.

Example response:

{
  "status": "healthy",
  "database": "connected"
}

Dashboard API
Dashboard Summary
GET
/dashboard/summary


Returns:

Total payments
Settlement count
Total exceptions
Open exceptions
Critical exceptions
High exceptions
Medium exceptions
Exceptions in review
Exceptions
GET
/dashboard/exceptions


Returns all detected financial exceptions.

Payment API
Payments
GET
/payments


Returns processed payment records used by the Payment Operations dashboard.

Reconciliation API
Reconcile Payment
POST
/reconcile/{payment_id}


Reconciles an individual payment against its settlement.

Reconcile All Payments
POST
/reconcile-all


Runs reconciliation across all available payments.

Machine Learning API
Detect Anomalies
GET
/ml/anomalies


Runs ML-based anomaly detection against payment data.

Example prediction:

PAY_000001 → Anomaly
PAY_000002 → Normal

Resolution Agent API
Resolve Exception
POST
/exceptions/{exception_id}/resolve


Processes a financial exception through the Resolution Agent.

Example:

POST /exceptions/EXC_PAY_000020/resolve


The dashboard automatically refreshes after resolution.

End-to-End Workflow
Payment Data
     │
     ▼
Reconciliation
     │
     ├── Match
     │     │
     │     ▼
     │  Successful
     │
     └── Mismatch / Missing
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

React Dashboard

The React dashboard provides an operational interface for monitoring financial reconciliation.

Dashboard Features
System health status
Total payment monitoring
Settlement monitoring
Exception monitoring
Open exception count
Exception severity overview
Payment Operations table
ML anomaly detection
Bulk reconciliation
Exception resolution
Dashboard refresh

The dashboard communicates with the FastAPI backend using Axios.

Backend Setup
Clone Repository
git clone https://github.com/Mantu-231/finops-autopilot.git


Move into the project:

cd finops-autopilot

Create Virtual Environment

Navigate to the backend:

cd backend


Create virtual environment:

python -m venv venv


Activate on Windows:

venv\Scripts\activate

Install Backend Dependencies
pip install -r requirements.txt

Configure PostgreSQL

Create a PostgreSQL database named:

finops


Configure the database connection in the backend database configuration.

Make sure PostgreSQL is running before starting the application.

Run Backend

From the backend directory:

uvicorn app.main:app --reload


Backend URL:

http://127.0.0.1:8000

API Documentation

FastAPI Swagger UI:

http://127.0.0.1:8000/docs


OpenAPI specification:

http://127.0.0.1:8000/openapi.json


Health check:

http://127.0.0.1:8000/health

Frontend Setup

Open a second terminal.

Navigate to the frontend:

cd frontend


Install dependencies:

npm install


Start the Vite development server:

npm run dev


Frontend URL:

http://localhost:5173

Running the Complete Application
Terminal 1 — Backend
cd backend
venv\Scripts\activate
uvicorn app.main:app --reload

Terminal 2 — Frontend
cd frontend
npm run dev


Open the dashboard:

http://localhost:5173

Project Status
MVP Complete
PostgreSQL database
SQLAlchemy models
Synthetic financial data
Payment reconciliation
Settlement matching
Exception detection
Bulk reconciliation
ML anomaly detection
Resolution Agent
FastAPI APIs
React dashboard
Exception management
Payment Operations dashboard
Automated dashboard refresh
CORS integration
Future Improvements
Authentication and role-based access
Advanced exception prioritization
Automated settlement ingestion
Processor-level analytics
Historical reconciliation reports
Advanced anomaly detection models
Email and notification integration
Docker deployment
Cloud deployment
Production monitoring and logging
Purpose

FinOps Autopilot is designed as an internal financial operations platform for teams that need to monitor payment transactions, reconcile settlements, identify financial exceptions, detect anomalous activity, and streamline exception handling.

The platform combines automated reconciliation, machine learning, and agent-assisted workflows to reduce manual financial operations and provide real-time operational visibility.

Author

Mantu Kumar

FinOps Autopilot
Agentic Financial Reconciliation & Exception Resolution Platform
