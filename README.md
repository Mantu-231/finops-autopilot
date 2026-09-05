# FinOps Autopilot

Agentic financial reconciliation and exception resolution platform. Automates payment ↔ settlement reconciliation, flags exceptions, scores anomalies with ML, and routes resolution through an agent workflow.

## Features

- Payment reconciliation & settlement matching
- Missing settlement / mismatch detection
- Exception severity classification (Critical / High / Medium)
- ML-based anomaly detection (scikit-learn)
- Agent-assisted exception resolution
- Real-time dashboard with auto-refresh

## Tech Stack

| Layer | Tech |
|---|---|
| Frontend | React + Vite + Axios |
| Backend | FastAPI (Python) |
| ORM / DB | SQLAlchemy + PostgreSQL |
| ML | scikit-learn |

## Architecture

```
React Dashboard (5173) → FastAPI (8000) → [Reconciliation | ML Detection | Resolution Agent] → PostgreSQL
```

## Getting Started

**Backend**
```bash
cd backend
venv\Scripts\activate
uvicorn app.main:app --reload
```
API: `http://127.0.0.1:8000` · Docs: `/docs` · Health: `/health`

**Frontend**
```bash
cd frontend
npm install
npm run dev
```
App: `http://localhost:5173`

## Key API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/dashboard/summary` | Payment/settlement/exception stats |
| GET | `/dashboard/exceptions` | List detected exceptions |
| GET | `/payments` | Payment records |
| POST | `/reconcile/{payment_id}` | Reconcile one payment |
| POST | `/reconcile-all` | Bulk reconcile |
| GET | `/ml/anomalies` | Run anomaly detection |
| POST | `/exceptions/{exception_id}/resolve` | Resolve via agent |

## Project Structure

```
finops-autopilot/
├── backend/app/
│   ├── agents/         # resolution_agent.py
│   ├── api/            # dashboard.py
│   ├── ml/             # anomaly_detector.py
│   ├── models/         # customer, merchant, payment, settlement, exception
│   ├── services/       # reconciliation, bulk_reconciliation
│   └── main.py
└── frontend/src/        # App.jsx, main.jsx
```

## Status

MVP complete — reconciliation, exception detection/classification, ML anomaly detection, resolution agent, and dashboard are all functional with PostgreSQL persistence.

> Uses synthetic data. Not production-ready without added security, auth, compliance, and monitoring.

## License

Educational / demonstration / portfolio use.
