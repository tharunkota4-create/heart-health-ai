# Heart Health AI

AI-based heart disease risk estimation and personalized health support system —
a B.Tech CSE capstone project.

> **Medical disclaimer.** This is an educational decision-support tool. It does
> **not** diagnose disease, prescribe medication, or replace a qualified
> healthcare professional. In an emergency, call your local emergency number.

[![CI](https://github.com/<OWNER>/heart-health-ai/actions/workflows/ci.yml/badge.svg)](https://github.com/<OWNER>/heart-health-ai/actions/workflows/ci.yml)
![Python](https://img.shields.io/badge/python-3.11+-blue)
![Node](https://img.shields.io/badge/node-18+-green)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

## Features

- JWT authentication with role-based access control (patient / doctor / admin)
- Real machine-learning pipeline trained on the UCI Cleveland heart dataset
- Six classifiers compared by cross-validated ROC-AUC; best model serialized
- Per-prediction explainability (feature importance / coefficients)
- Personalized educational precautions
- Educational medication information (never prescriptive)
- Emergency-symptom detection with hard-stop guidance
- Assessment history, trend charts, and downloadable PDF reports
- Doctor dashboard with patient list and assessments
- Admin dashboard with system statistics and audit log

## Technology Stack

| Layer | Technology |
|-------|------------|
| Frontend | React 18 · TypeScript · Vite · Tailwind CSS · Recharts |
| Backend | Python 3.11 · FastAPI · Pydantic v2 · SQLAlchemy 2.0 |
| Database | SQLite (dev) · PostgreSQL (prod-ready) |
| ML | scikit-learn · XGBoost · pandas · NumPy · SHAP · joblib |
| Auth | PyJWT · passlib/bcrypt |
| Reporting | ReportLab |

## Quick Start

```bash
# 1. Clone
git clone https://github.com/<OWNER>/heart-health-ai.git
cd heart-health-ai

# 2. Backend
python -m venv backend/.venv
source backend/.venv/bin/activate          # Windows: backend\.venv\Scripts\activate
pip install -r backend/requirements.txt
cp backend/.env.example backend/.env
# edit backend/.env — set a strong JWT_SECRET

# 3. Train the model (once)
python ml/prepare_data.py
python ml/train.py

# 4. Run backend
cd backend && uvicorn app.main:app --reload --port 8000

# 5. Frontend (new terminal)
cd frontend
npm install
cp .env.example .env
npm run dev
