# BUtique

BUtique is a full-stack marketplace and social app built with a Next.js frontend and a Python FastAPI backend (GraphQL).

Key pieces:
- Frontend: Next.js app in the repo root (`app/`) — UI, pages, and client GraphQL code.
- Backend: FastAPI-based GraphQL server in `backend/` — data, resolvers, and services.

The backend uses a Python virtual environment (`venv`) — instructions below show how to create and use it.

Prerequisites
- Node.js (LTS)
- Python 3.9+ (3.12 recommended)
- Git

Quick setup (macOS / Linux)
1. Clone the repo and enter it:

```bash
git clone https://github.com/MinsungKim0315/BUtique.git
cd BUtique
```

2. Create and activate a Python virtual environment for the backend

```bash
# from repo root
python3 -m venv .venv
source .venv/bin/activate
```

On macOS zsh/fish or Linux: `source .venv/bin/activate`.
On Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

3. Install backend dependencies (inside the activated venv)

```bash
cd backend
pip install -r requirements.txt
```

4. Install frontend dependencies (in a separate shell / outside venv)

```bash
cd ..
npm install
```

Environment variables
Create a `.env.local` file in the repo root with required keys (example):

```
NEXT_PUBLIC_SUPABASE_URL=...
NEXT_PUBLIC_SUPABASE_ANON_KEY=...
SUPABASE_SERVICE_ROLE_KEY=...
NEXT_PUBLIC_GRAPHQL_ENDPOINT=...
BACKEND_GRAPHQL_URL=...
APP_PASS=...
```

Running the services
- Start the backend (ensure venv is activated and you are in the `backend/` folder):

```bash
uvicorn app.main:app --reload --port 4000
```

GraphQL endpoint: http://localhost:4000/graphql

- Start the frontend (from repo root, can run outside the venv):

```bash
npm run dev
```

Open the frontend at http://localhost:3000

Running tests
- Backend tests (inside activated venv, from repo root):

```bash
cd backend
pytest
```

Notes
- Keep one terminal with the backend venv activated; run the frontend/npm commands in another terminal.
- If you need to recreate the venv: `rm -rf .venv && python3 -m venv .venv && source .venv/bin/activate && pip install -r backend/requirements.txt`

