
# Chatbot Legal Assistant (RAG) — Indian Contract Law (React + FastAPI)

**RAG stack**: React (Vite) + FastAPI + FAISS + LangChain  
**Docs**: http://localhost:8000/docs

## Quick Start

### 0) Add PDFs
Place your PDFs in `server/data/` (e.g., `IndianContractAct1872.pdf`).

### 1) Backend (FastAPI)
```bash
cd server
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env
# OPTIONAL: set OPENAI_API_KEY in .env

python -m app.rag.ingest    # build FAISS index from PDFs
uvicorn app.main:app --reload --port 8000
```

### 2) Frontend (React)
```bash
cd web
cp .env.example .env        # ensure VITE_API_BASE=http://localhost:8000
npm install
npm run dev
```

## API
- `POST /ingest/rebuild` — rebuild FAISS index from PDFs in `server/data/`
- `POST /ask` — `{ "question": "...", "k": 5 }` → `{ answer, citations[] }`
- `GET /health`

> Educational demo, not legal advice.
