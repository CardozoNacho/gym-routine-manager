# Gym Routine Manager | FastAPI, React and PostgreSQL

[Español](README.es.md)

An individual academic project by Carlos Ignacio Cardozo Peragallo. A full-stack application to create, search, view, edit and delete routines with nested exercises.

## Implementation

FastAPI 0.115.6, SQLModel 0.0.22, Uvicorn 0.32.1, PostgreSQL, React 19, React Router 7 and Vite 7. The frontend uses Context API and Fetch. Validation covers names, days and numeric values. Exercises are managed inside routines; there is no independent exercise router.

## Local setup

Requires Python 3.10+, PostgreSQL and a Node version compatible with the lockfile: `^20.19.0 || >=22.12.0`.

```bash
git clone https://github.com/CardozoNacho/gym-routine-manager.git
cd gym-routine-manager
```

1. Create the `rutinas_gym_db` database and a `backend/.env` file containing `DATABASE_URL=postgresql://<user>:<password>@localhost:5432/rutinas_gym_db`.
2. In `backend`, create and activate a virtual environment, install dependencies with `pip install -r requirements.txt`, then run `uvicorn main:app --reload --port 8000`.
3. Create `frontend/.env` containing `VITE_API_URL=http://localhost:8000`, without a trailing slash.
4. In `frontend`, run `npm ci` followed by `npm run dev`.

Frontend: `http://localhost:5173`. Swagger UI: `http://localhost:8000/docs`. Tables are created at startup; the database must already exist.

## API

| Method | Path | Operation |
|---|---|---|
| GET | `/api/rutinas` | List routines |
| GET | `/api/rutinas/buscar?nombre=...` | Search by name |
| GET | `/api/rutinas/{id}` | Get details |
| POST | `/api/rutinas` | Create with exercises |
| PUT | `/api/rutinas/{id}` | Update; replace exercises when supplied |
| DELETE | `/api/rutinas/{id}` | Delete with exercises |

## Docker and current limitations

Dockerfiles and Compose with PostgreSQL 15 are included, but the frontend image uses Node 18, which is incompatible with Vite 7. Update the image and test the flow before treating `docker compose up --build` as a reproducible starting point.

The default URL in `frontend/src/config.js` ends in `/`, while the context appends `/api/...`. Without an explicit setting, requests may contain `//api/...`. The `.env` setting above avoids this locally.

`init-db.sql` contains comments only; it does not seed sample data. There is no authentication, pagination or automated test suite. Source code was reviewed statically; end-to-end execution and production readiness are not claimed.

[Backend guide — Spanish](backend/README.md) | [Frontend guide — Spanish](frontend/README.md)
