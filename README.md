FinOps Autopilot

Agentic Financial Reconciliation \& Exception Resolution Platform



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

&#x20;                   ┌──────────────────────┐

&#x20;                   │    React Dashboard   │

&#x20;                   │      Vite + Axios    │

&#x20;                   │    localhost:5173    │

&#x20;                   └───────────┬──────────┘

&#x20;                               │

&#x20;                               ▼

&#x20;                   ┌──────────────────────┐

&#x20;                   │       FastAPI        │

&#x20;                   │     Backend API      │

&#x20;                   │    localhost:8000    │

&#x20;                   └───────────┬──────────┘

&#x20;                               │

&#x20;               ┌───────────────┼───────────────┐

&#x20;               │               │               │

&#x20;               ▼               ▼               ▼

&#x20;      ┌────────────────┐ ┌──────────────┐ ┌──────────────────┐

&#x20;      │ Reconciliation │ │ ML Detection │ │ Resolution Agent │

&#x20;      │    Service     │ │ Scikit-learn │ │     Workflow     │

&#x20;      └───────┬────────┘ └──────┬───────┘ └────────┬─────────┘

&#x20;              │                 │                  │

&#x20;              └─────────────────┼──────────────────┘

&#x20;                                │

&#x20;                                ▼

&#x20;                   ┌──────────────────────┐

&#x20;                   │      PostgreSQL      │

&#x20;                   │       finops DB      │

&#x20;                   └──────────────────────┘



🔄 How It Works

Payment Data

&#x20;    │

&#x20;    ▼

Reconciliation

&#x20;    │

&#x20;    ├──────── Match ──────────────► Successful

&#x20;    │

&#x20;    └──────── Mismatch / Missing

&#x20;                   │

&#x20;                   ▼

&#x20;           Exception Detection

&#x20;                   │

&#x20;                   ▼

&#x20;           Severity Classification

&#x20;                   │

&#x20;                   ▼

&#x20;           ML Anomaly Detection

&#x20;                   │

&#x20;                   ▼

&#x20;            Resolution Agent

&#x20;                   │

&#x20;                   ▼

&#x20;            Dashboard Update



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

Settlement Mismatch	PAY\_000001

Missing Settlements	19

ML Anomaly Detection	Enabled

Resolution Agent	Enabled

Example Exception

Payment ID:      PAY\_000001

Expected Amount: 3710.34 EUR

Received Amount: 3690.34 EUR

Difference:      20.00 EUR

Exception Type:  SETTLEMENT\_MISMATCH

Severity:        HIGH



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

│   │   │   └── resolution\_agent.py

│   │   │

│   │   ├── api/

│   │   │   └── dashboard.py

│   │   │

│   │   ├── db/

│   │   │   ├── base.py

│   │   │   └── database.py

│   │   │

│   │   ├── ml/

│   │   │   └── anomaly\_detector.py

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

│   │   │   └── bulk\_reconciliation.py

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



venv\\Scripts\\activate





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





Start the frontend:



npm run dev





Frontend:



http://localhost:5173



🔌 API Endpoints

Health

GET /health





Checks database connectivity.



Dashboard Summary

GET /dashboard/summary





Returns payment, settlement, exception and status statistics.



Exceptions

GET /dashboard/exceptions





Returns detected financial exceptions.



Payments

GET /payments





Returns processed payment records used by the Payment Operations dashboard.



Reconcile Payment

POST /reconcile/{payment\_id}





Reconciles an individual payment against its settlement.



Reconcile All

POST /reconcile-all





Runs reconciliation across all payments.



ML Anomalies

GET /ml/anomalies





Runs anomaly detection against payment data.



Resolve Exception

POST /exceptions/{exception\_id}/resolve





Processes an exception through the Resolution Agent.



🤖 Automation Workflow

&#x20;                Payment Data

&#x20;                     │

&#x20;                     ▼

&#x20;             Payment Reconciliation

&#x20;                     │

&#x20;           ┌─────────┴─────────┐

&#x20;           │                   │

&#x20;         Match          Mismatch / Missing

&#x20;           │                   │

&#x20;           ▼                   ▼

&#x20;      Successful       Exception Detection

&#x20;                               │

&#x20;                               ▼

&#x20;                      Severity Classification

&#x20;                               │

&#x20;                               ▼

&#x20;                      ML Anomaly Detection

&#x20;                               │

&#x20;                               ▼

&#x20;                       Resolution Agent

&#x20;                               │

&#x20;                               ▼

&#x20;                      Dashboard Update



📈 Dashboard



The React dashboard provides:



Total payment count

Settlement count

Exception count

Open exception count

Critical exception count

High severity exception count

Medium severity exception count

In-review exception count

Exception management table

Payment Operations table

Reconciliation controls

ML anomaly detection control

Exception resolution actions

Automated dashboard refresh

🧪 Example ML Output

{

&#x20; "payment\_id": "PAY\_000019",

&#x20; "amount": 566.65,

&#x20; "settlement\_difference": 0,

&#x20; "has\_settlement": 0,

&#x20; "anomaly\_score": 0.434,

&#x20; "prediction": -1

}





Prediction values:



\-1 = Anomaly

&#x20;1 = Normal



📌 Project Status

MVP Complete

&#x20;PostgreSQL database

&#x20;SQLAlchemy models

&#x20;Synthetic financial data

&#x20;Payment reconciliation

&#x20;Settlement matching

&#x20;Exception detection

&#x20;Exception severity classification

&#x20;Bulk reconciliation

&#x20;ML anomaly detection

&#x20;Resolution Agent

&#x20;FastAPI APIs

&#x20;React dashboard

&#x20;Exception management

&#x20;Payment Operations dashboard

&#x20;Automated dashboard refresh

&#x20;PostgreSQL persistence

🎬 Demo



Start the backend first:



cd backend

venv\\Scripts\\activate

uvicorn app.main:app --reload





Then start the frontend in a second terminal:



cd frontend

npm run dev





Open:



http://localhost:5173





The dashboard displays the current reconciliation and exception state and allows OPEN exceptions to be processed through the Resolution Agent.



🎯 Purpose



FinOps Autopilot is designed as an internal financial operations platform for teams that need to:



Monitor payment transactions

Reconcile payment and settlement records

Identify missing settlements

Detect settlement mismatches

Detect anomalous financial activity

Prioritize financial exceptions

Automate exception handling

Monitor operations through a centralized dashboard

🔐 Development Note



This project currently uses synthetic financial data and is intended for demonstration, development, and portfolio purposes.



It is not intended for processing real production financial transactions without additional security, compliance, authentication, authorization, monitoring, and infrastructure controls.



📄 License



This project is intended for educational, demonstration, and portfolio use.

