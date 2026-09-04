FinOps Autopilot

Agentic Financial Reconciliation \& Exception Resolution Platform



FinOps Autopilot is an intelligent financial operations platform that automates payment reconciliation, detects settlement exceptions, identifies anomalous transactions using machine learning, and assists operations teams with exception resolution.



The platform combines FastAPI, React, PostgreSQL, SQLAlchemy, Scikit-learn, and an agent-based resolution workflow into a single financial operations dashboard.



🚀 Overview



Financial operations teams often need to reconcile large numbers of payment transactions against settlement records while identifying mismatches, missing settlements, and unusual transaction behavior.



FinOps Autopilot automates this workflow:



Payment Data → Reconciliation → Exception Detection → ML Anomaly Detection → Resolution Agent → Dashboard



The system provides a real-time operational dashboard where users can monitor payments, review exceptions, run reconciliation, execute anomaly detection, and process exceptions through the Resolution Agent.



🏗️ System Architecture

&#x20;                   ┌─────────────────────────┐

&#x20;                   │     React Dashboard      │

&#x20;                   │      Vite Frontend       │

&#x20;                   │     localhost:5173       │

&#x20;                   └────────────┬────────────┘

&#x20;                                │

&#x20;                                ▼

&#x20;                   ┌─────────────────────────┐

&#x20;                   │        FastAPI           │

&#x20;                   │       Backend API        │

&#x20;                   │     localhost:8000       │

&#x20;                   └────────────┬────────────┘

&#x20;                                │

&#x20;            ┌───────────────────┼───────────────────┐

&#x20;            │                   │                   │

&#x20;            ▼                   ▼                   ▼

&#x20;     ┌──────────────┐   ┌──────────────┐   ┌────────────────┐

&#x20;     │Reconciliation│   │ ML Detection │   │Resolution Agent│

&#x20;     │   Service    │   │  Scikit-learn│   │    Workflow    │

&#x20;     └──────┬───────┘   └──────┬───────┘   └───────┬────────┘

&#x20;            │                  │                   │

&#x20;            └──────────────────┼───────────────────┘

&#x20;                               ▼

&#x20;                   ┌─────────────────────────┐

&#x20;                   │       PostgreSQL        │

&#x20;                   │        finops DB        │

&#x20;                   └─────────────────────────┘



✨ Core Features

💳 Payment reconciliation

🔄 Settlement matching

⚠️ Missing settlement detection

💰 Settlement mismatch detection

📊 Exception severity classification

🔁 Bulk payment reconciliation

🤖 ML-based anomaly detection

🧠 Agent-assisted exception resolution

📈 Real-time operational dashboard

🔎 Exception management

💾 PostgreSQL persistence

💼 Payment Operations dashboard

🔄 Automated dashboard refresh

📊 Current Demo Data



The development environment currently contains:



20 payments

1 settlement

20 detected exceptions

Settlement mismatch for PAY\_000001

Missing settlements for the remaining payments

Multiple exceptions processed by the Resolution Agent

ML anomaly detection results



The demo dataset is synthetic and intended for demonstrating the complete financial reconciliation workflow.



🛠️ Technology Stack

Layer	Technology

Frontend	React + Vite

API	FastAPI

ORM	SQLAlchemy

Database	PostgreSQL

Database Driver	Psycopg2

HTTP Client	Axios

Machine Learning	Scikit-learn

Backend Runtime	Python

Frontend Runtime	Node.js

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



🔄 End-to-End Workflow

&#x20;                   Payment Data

&#x20;                        │

&#x20;                        ▼

&#x20;                 ┌──────────────┐

&#x20;                 │Reconciliation│

&#x20;                 └──────┬───────┘

&#x20;                        │

&#x20;             ┌──────────┴──────────┐

&#x20;             │                     │

&#x20;           Match             Mismatch/Missing

&#x20;             │                     │

&#x20;             ▼                     ▼

&#x20;        Successful          Exception Detection

&#x20;                                   │

&#x20;                                   ▼

&#x20;                          Severity Classification

&#x20;                                   │

&#x20;                                   ▼

&#x20;                          ML Anomaly Detection

&#x20;                                   │

&#x20;                                   ▼

&#x20;                           Resolution Agent

&#x20;                                   │

&#x20;                                   ▼

&#x20;                            Dashboard Update



⚙️ Backend Setup



Navigate to the backend:



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



Open a second terminal.



Navigate to the frontend:



cd frontend





Install dependencies if required:



npm install





Start the Vite development server:



npm run dev





Frontend:



http://localhost:5173



🔌 API Endpoints

Health Check

GET /health





Checks backend and PostgreSQL connectivity.



Dashboard Summary

GET /dashboard/summary





Returns:



Total payments

Total settlements

Total exceptions

Open exceptions

Critical exceptions

High severity exceptions

Medium severity exceptions

Exceptions in review

Exceptions

GET /dashboard/exceptions





Returns detected financial exceptions and their current status.



Payments

GET /payments





Returns processed payment records used by the Payment Operations dashboard.



Reconcile Payment

POST /reconcile/{payment\_id}





Reconciles an individual payment against its settlement record.



Example:



POST /reconcile/PAY\_000001



Reconcile All Payments

POST /reconcile-all





Runs reconciliation across all available payments.



ML Anomaly Detection

GET /ml/anomalies





Runs machine-learning-based anomaly detection against payment data.



Resolve Exception

POST /exceptions/{exception\_id}/resolve





Processes an exception through the Resolution Agent.



Example:



POST /exceptions/EXC\_PAY\_000020/resolve



🖥️ Dashboard



The React dashboard provides:



System health status

Payment statistics

Settlement statistics

Exception statistics

Exception severity overview

ML anomaly detection controls

Bulk reconciliation controls

Exception management

Payment Operations monitoring

Resolution Agent controls

Automatic dashboard refresh



Example dashboard workflow:



Run Reconciliation

&#x20;       ↓

Exceptions detected

&#x20;       ↓

Run ML Anomaly Detection

&#x20;       ↓

Review exceptions

&#x20;       ↓

Resolve selected exception

&#x20;       ↓

Dashboard automatically updates



🤖 Machine Learning



The platform includes an anomaly detection component built with Scikit-learn.



The detector evaluates payment-related features such as:



Payment amount

Settlement difference

Settlement availability



The system produces:



Anomaly score

Prediction

Payment-level anomaly classification



A prediction of:



\-1





indicates an anomalous transaction according to the trained model.



🧠 Resolution Agent



The Resolution Agent processes detected exceptions and updates their operational status.



Supported exception scenarios include:



Missing settlements

Settlement mismatches

High-severity exceptions



The dashboard allows operators to trigger resolution directly from the Exception Management table.



🗄️ Database



The application uses PostgreSQL for persistent financial operations data.



Main entities include:



Customers

Merchants

Payments

Settlements

Exceptions





SQLAlchemy provides the ORM layer between the FastAPI backend and PostgreSQL.



🧪 Demo Scenario



The included synthetic dataset demonstrates a settlement mismatch:



Payment:

PAY\_000001



Expected:

3710.34 EUR



Received:

3690.34 EUR



Difference:

20.00 EUR



Exception:

SETTLEMENT\_MISMATCH



Severity:

HIGH





The system detects the mismatch, creates an exception, displays it in the dashboard, and allows the Resolution Agent to process it.



📈 Project Status

MVP Complete ✅

&#x20;PostgreSQL database

&#x20;SQLAlchemy models

&#x20;Synthetic financial data

&#x20;Payment reconciliation

&#x20;Settlement matching

&#x20;Exception detection

&#x20;Missing settlement detection

&#x20;Settlement mismatch detection

&#x20;Severity classification

&#x20;Bulk reconciliation

&#x20;ML anomaly detection

&#x20;Resolution Agent

&#x20;FastAPI APIs

&#x20;React dashboard

&#x20;Exception management

&#x20;Payment Operations dashboard

&#x20;Automated dashboard refresh

&#x20;GitHub repository

🎯 Purpose



FinOps Autopilot is designed as an internal financial operations platform for teams that need to:



Monitor payment transactions

Reconcile payments against settlements

Detect financial discrepancies

Identify missing settlement records

Detect anomalous payment activity

Prioritize exceptions by severity

Automate exception handling

Monitor financial operations through a centralized dashboard



The project demonstrates how traditional financial reconciliation workflows can be combined with automation, machine learning, APIs, and agent-based workflows.



🚀 Quick Start

Terminal 1 — Backend

cd backend

venv\\Scripts\\activate

uvicorn app.main:app --reload



Terminal 2 — Frontend

cd frontend

npm install

npm run dev



Open Dashboard

http://localhost:5173



Open API Documentation

http://127.0.0.1:8000/docs



📌 Project



FinOps Autopilot

Automated Financial Reconciliation \& Exception Resolution Platform



Built with Python · FastAPI · React · PostgreSQL · SQLAlchemy · Scikit-learn

