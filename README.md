# Dementia-Detection
# 🧠 AI Tool for Early-Stage Dementia Detection

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-Active-brightgreen)
![Tech](https://img.shields.io/badge/AI-Powered-orange)
![Platform](https://img.shields.io/badge/platform-Web%20%7C%20Mobile-lightgrey)

---

## 📘 Overview
Early-stage dementia often goes *undiagnosed* because cognitive decline can be subtle.  
This project is a *low-cost, accessible AI screening tool* that analyzes *speech, behaviour, and cognitive tests* to flag early signs of dementia and suggest clinical referral.

---

## 🌟 Key Features
- Speech pattern analysis (pauses, hesitations, articulation)
- Cognitive tasks (memory, pattern recognition, reaction time)
- Risk score generation and visual dashboard
- Multi-language (vernacular) support
- Simple, accessible UI for older adults

---

## 🏗️ Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | React.js (JSX) / React Native, Tailwind CSS |
| Backend | Node.js + Express.js |
| AI Engine | Python (TensorFlow / PyTorch / scikit-learn) |
| Database | MongoDB / PostgreSQL |
| Deployment | Docker, AWS / Render / Vercel |
| Auth & Security | JWT, HTTPS |
| Visualization | Recharts / Chart.js |

---


AI-Dementia-Detection/
│
├── frontend/                
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── assets/
│   │   └── App.jsx
│   ├── package.json
│   └── vite.config.js
│
├── backend/                 
│   ├── routes/
│   ├── controllers/
│   ├── models/
│   ├── services/
│   ├── app.js
│   ├── package.json
│   └── .env.example
│
├── ai_model/               
│   ├── data/
│   ├── notebooks/
│   ├── models/
│   ├── preprocess.py
│   ├── train_model.py
│   └── inference.py
│
├── docs/                    
│   ├── problem_statement.pdf
│   ├── sequence_flow.png
│   ├── architecture_diagram.png
│   └── ppt/
│
├── .gitignore
├── README.md
└── LICENSE


yaml
Copy code

---

## ⚙️ Setup & Run (Development)

### Frontend (development)
```bash
cd frontend
npm install
npm run dev
package.json should contain appropriate scripts, e.g.

json
Copy code
"scripts": {
  "dev": "vite",
  "build": "vite build",
  "start": "vite preview"
}
Backend (development)
bash
Copy code
cd backend
npm install
npm run dev
npm start
Example package.json scripts:

json
Copy code
"scripts": {
  "dev": "nodemon src/server.js",
  "start": "node src/server.js"
}
AI Engine (Python)
bash
Copy code
cd ai_engine
# create & activate venv (Linux / macOS)
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Run inference (example)
python inference.py
🔐 Environment variables (.env.example)
ini
Copy code
# Backend
PORT=5000
MONGO_URI=mongodb+srv://<user>:<pass>@cluster.example.mongodb.net/dbname
JWT_SECRET=your_jwt_secret

# AI / Storage
MODEL_PATH=./ai_engine/models/best_model.pt
S3_BUCKET=your-s3-bucket
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
🌐 API (examples)
1) Upload speech sample
POST /api/test/speech
Content-Type: multipart/form-data
Fields: file (wav/m4a), language, userId

Response

json
Copy code
{
  "status": "ok",
  "analysisId": "abc123",
  "message": "Speech received"
}
2) Submit cognitive task result
POST /api/test/cognitive

json
Copy code
{
  "userId": "u123",
  "taskId": "memory-1",
  "responseTimeMs": 3200,
  "score": 6,
  "errors": 2
}
Response

json
Copy code
{
  "status": "ok",
  "message": "Task recorded"
}
3) Get risk report
GET /api/result/:userId
Response

json
Copy code
{
  "userId": "u123",
  "riskScore": 78,
  "riskLevel": "Moderate",
  "insights": [
    "Increased pause rate in speech",
    "Slower recall on memory tasks"
  ],
  "recommendation": "Refer to neurologist"
}
🐳 Docker (quick starter)
docker-compose.yml should orchestrate frontend, backend, and ai_engine (if containerized). Example:

yaml
Copy code
version: "3.8"
services:
  backend:
    build: ./backend
    ports: ["5000:5000"]
    env_file:
      - .env
  frontend:
    build: ./frontend
    ports: ["3000:3000"]
🤝 Contributing
Fork the repo

Create a feature branch: git checkout -b feat/your-feature

Commit & push

Open a PR with a clear description

Please include tests & update docs when adding features.
