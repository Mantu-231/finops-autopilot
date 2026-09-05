# FinOps Autopilot
## Agentic Financial Reconciliation & Exception Resolution Platform

FinOps Autopilot is an intelligent financial operations platform designed to automate payment reconciliation, detect settlement exceptions, identify anomalous transactions using machine learning, and assist with exception resolution.

============================================================
FEATURES
============================================================

- Payment reconciliation
- Settlement matching
- Missing settlement detection
- Settlement mismatch detection
- Exception severity classification
- Bulk reconciliation
- ML-based anomaly detection
- Agent-assisted exception resolution
- Real-time operational dashboard
- Exception management
- Payment Operations monitoring
- PostgreSQL persistence
- Automated dashboard refresh


============================================================
SYSTEM ARCHITECTURE
============================================================

                    +--------------------------+
                    |     React Dashboard       |
                    |      Vite + Axios         |
                    |     localhost:5173        |
                    +------------+-------------+
                                 |
                                 | HTTP / REST API
                                 v
                    +--------------------------+
                    |         FastAPI           |
                    |       Backend API         |
                    |     localhost:8000        |
                    +------------+-------------+
                                 |
              +------------------+------------------+
              |                  |                  |
              v                  v                  v
     +----------------+  +----------------+  +-------------------+
     | Reconciliation |  | ML Detection   |  | Resolution Agent  |
     |    Service     |  | Scikit-learn  |  |     Workflow      |
     +-------+--------+  +-------+--------+  +---------+---------+
             |                   |                     |
             |                   |                     |
             +-------------------+---------------------+
                                 |
                                 v
                    +--------------------------+
                    |       PostgreSQL         |
                    |         finops DB        |
                    +--------------------------+


============================================================
HOW IT WORKS
============================================================

                    +----------------+
                    |  Payment Data  |
                    +-------+--------+
                            |
                            v
                +------------------------+
                | Payment Reconciliation |
                +-----------+------------+
                            |
                  +---------+---------+
                  |                   |
                  v                   v
             +---------+      +-------------------+
             |  Match  |      | Mismatch / Missing|
             +----+----+      +---------+---------+
                  |                     |
                  v                     v
          +-------------+      +---------------------+
          | Successful  |      | Exception Detection|
          +-------------+      +----------+----------+
                                         |
                                         v
                              +----------------------+
                              | Severity             |
                              | Classification       |
                              +----------+-----------+
                                         |
                                         v
                              +----------------------+
                              | ML Anomaly Detection |
                              +----------+-----------+
                                         |
                                         v
                              +----------------------+
                              |   Resolution Agent   |
                              +----------+-----------+
                                         |
                                         v
                              +----------------------+
                              |  Dashboard Update    |
                              +----------------------+


============================================================
CORE COMPONENTS
============================================================

PAYMENT RECONCILIATION

Compares payment records against settlement records and identifies
whether transactions are successfully reconciled.


EXCEPTION DETECTION

Detects financial exceptions including:

- Missing settlements
- Settlement mismatches
- Amount differences
- High-value discrepancies


SEVERITY CLASSIFICATION

Exceptions are automatically classified into:

- CRITICAL
- HIGH
- MEDIUM


ML ANOMALY DETECTION

Uses Scikit-learn to identify unusual payment activity based on
transaction and settlement-related features.

The ML service produces an anomaly score and prediction for each payment.

Prediction:
-1 = Anomaly
 1 = Normal


RESOLUTION AGENT

The Resolution Agent processes detected exceptions and updates
their operational status.

Users can trigger exception resolution directly from the dashboard.


============================================================
DEMO DATA
============================================================

Metric                     Value
------------------------------------------------------------
Payments                   20
Settlements                1
Exceptions                 20
Settlement Mismatch        PAY_000001
Missing Settlements        19
ML Anomaly Detection       Enabled
Resolution Agent           Enabled


Example Exception

Field                      Value
------------------------------------------------------------
Payment ID                 PAY_000001
Expected Amount            3710.34 EUR
Received Amount            3690.34 EUR
Difference                 20.00 EUR
Exception Type             SETTLEMENT_MISMATCH
Severity                   HIGH


============================================================
TECHNOLOGY STACK
============================================================

Layer                      Technology
------------------------------------------------------------
Frontend                   React
Build Tool                 Vite
HTTP Client                Axios
Backend                    FastAPI
Language                   Python
ORM                        SQLAlchemy
Database                   PostgreSQL
Database Driver            Psycopg2
Machine Learning           Scikit-learn
Runtime                    Python + Node.js


============================================================
PROJECT STRUCTURE
============================================================

finops-autopilot/
|
+-- backend/
|   |
|   +-- app/
|   |   |
|   |   +-- agents/
|   |   |   +-- resolution_agent.py
|   |   |
|   |   +-- api/
|   |   |   +-- dashboard.py
|   |   |
|   |   +-- db/
|   |   |   +-- base.py
|   |   |   +-- database.py
|   |   |
|   |   +-- ml/
|   |   |   +-- anomaly_detector.py
|   |   |
|   |   +-- models/
|   |   |   +-- customer.py
|   |   |   +-- merchant.py
|   |   |   +-- payment.py
|   |   |   +-- settlement.py
|   |   |   +-- exception.py
|   |   |
|   |   +-- services/
|   |   |   +-- reconciliation.py
|   |   |   +-- bulk_reconciliation.py
|   |   |
|   |   +-- main.py
|   |
|   +-- data/
|   +-- requirements.txt
|
+-- frontend/
|   |
|   +-- src/
|   |   +-- App.jsx
|   |   +-- App.css
|   |   +-- main.jsx
|   |
|   +-- package.json
|   +-- vite.config.js
|
+-- README.md


============================================================
BACKEND SETUP
============================================================

Open a terminal and navigate to the backend:

cd backend

Activate the virtual environment:

venv\Scripts\activate

Start the FastAPI server:

uvicorn app.main:app --reload


Backend:
http://127.0.0.1:8000

API Documentation:
http://127.0.0.1:8000/docs

Health Check:
http://127.0.0.1:8000/health


============================================================
FRONTEND SETUP
============================================================

Open a second terminal:

cd frontend

Install dependencies:

npm install

Start the frontend:

npm run dev


Frontend:
http://localhost:5173


============================================================
API ENDPOINTS
============================================================

HEALTH

GET /health

Checks database connectivity.


DASHBOARD SUMMARY

GET /dashboard/summary

Returns payment, settlement, exception and status statistics.


EXCEPTIONS

GET /dashboard/exceptions

Returns detected financial exceptions.


PAYMENTS

GET /payments

Returns processed payment records used by the Payment Operations dashboard.


RECONCILE PAYMENT

POST /reconcile/{payment_id}

Reconciles an individual payment against its settlement.


RECONCILE ALL

POST /reconcile-all

Runs reconciliation across all payments.


ML ANOMALIES

GET /ml/anomalies

Runs anomaly detection against payment data.


RESOLVE EXCEPTION

POST /exceptions/{exception_id}/resolve

Processes an exception through the Resolution Agent.


============================================================
AUTOMATION WORKFLOW
============================================================

                    +----------------+
                    |  Payment Data  |
                    +-------+--------+
                            |
                            v
                +------------------------+
                | Payment Reconciliation |
                +-----------+------------+
                            |
              +-------------+-------------+
              |                           |
              v                           v
        +-----------+             +-------------------+
        |   Match   |             | Mismatch / Missing|
        +-----+-----+             +---------+---------+
              |                             |
              v                             v
        +-----------+             +---------------------+
        | Successful|             | Exception Detection|
        +-----------+             +----------+----------+
                                             |
                                             v
                                  +----------------------+
                                  | Severity             |
                                  | Classification       |
                                  +----------+-----------+
                                             |
                                             v
                                  +----------------------+
                                  | ML Anomaly Detection |
                                  +----------+-----------+
                                             |
                                             v
                                  +----------------------+
                                  |   Resolution Agent   |
                                  +----------+-----------+
                                             |
                                             v
                                  +----------------------+
                                  |  Dashboard Update    |
                                  +----------------------+


============================================================
DASHBOARD
============================================================

The React dashboard provides:

- Total payment count
- Settlement count
- Exception count
- Open exception count
- Critical exception count
- High severity exception count
- Medium severity exception count
- In-review exception count
- Exception management table
- Payment Operations table
- Reconciliation controls
- ML anomaly detection control
- Exception resolution actions
- Automated dashboard refresh


============================================================
EXAMPLE ML OUTPUT
============================================================

{
  "payment_id": "PAY_000019",
  "amount": 566.65,
  "settlement_difference": 0,
  "has_settlement": 0,
  "anomaly_score": 0.434,
  "prediction": -1
}


Prediction Values

Prediction                  Meaning
------------------------------------------------------------
-1                           Anomaly
 1                           Normal


============================================================
PROJECT STATUS
============================================================

MVP COMPLETE

[✓] PostgreSQL database
[✓] SQLAlchemy models
[✓] Synthetic financial data
[✓] Payment reconciliation
[✓] Settlement matching
[✓] Exception detection
[✓] Exception severity classification
[✓] Bulk reconciliation
[✓] ML anomaly detection
[✓] Resolution Agent
[✓] FastAPI APIs
[✓] React dashboard
[✓] Exception management
[✓] Payment Operations dashboard
[✓] Automated dashboard refresh
[✓] PostgreSQL persistence


============================================================
DEMO
============================================================

Start the backend first:

cd backend
venv\Scripts\activate
uvicorn app.main:app --reload


Then start the frontend in a second terminal:

cd frontend
npm run dev


Open:

http://localhost:5173


The dashboard displays the current reconciliation and exception
state and allows OPEN exceptions to be processed through the
Resolution Agent.


============================================================
PURPOSE
============================================================

FinOps Autopilot is designed as an internal financial operations
platform for teams that need to:

- Monitor payment transactions
- Reconcile payment and settlement records
- Identify missing settlements
- Detect settlement mismatches
- Detect anomalous financial activity
- Prioritize financial exceptions
- Automate exception handling
- Monitor operations through a centralized dashboard


============================================================
DEVELOPMENT NOTE
============================================================

This project currently uses synthetic financial data and is intended
for demonstration, development, and portfolio purposes.

It is not intended for processing real production financial transactions
without additional security, compliance, authentication, authorization,
monitoring, and infrastructure controls.


============================================================
LICENSE
============================================================

This project is intended for educational, demonstration, and portfolio use.
