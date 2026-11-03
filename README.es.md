# Gym Routine Manager | FastAPI, React y PostgreSQL

[English](README.md)

Proyecto académico individual de Carlos Ignacio Cardozo Peragallo. Aplicación Full Stack para crear, buscar, consultar, editar y eliminar rutinas con ejercicios anidados.

## Implementación

FastAPI 0.115.6, SQLModel 0.0.22, Uvicorn 0.32.1, PostgreSQL, React 19, React Router 7 y Vite 7. El frontend usa Context API y Fetch. Hay validaciones de nombres, días y valores numéricos. Los ejercicios se administran dentro de las rutinas; no existe un router independiente de ejercicios.

## Inicio local

Requiere Python 3.10+, PostgreSQL y Node compatible con el lockfile: `^20.19.0 || >=22.12.0`.

```bash
git clone https://github.com/CardozoNacho/gym-routine-manager.git
cd gym-routine-manager
```

1. Crear la base `rutinas_gym_db` y `backend/.env` con `DATABASE_URL=postgresql://<usuario>:<clave>@localhost:5432/rutinas_gym_db`.
2. Desde `backend`, crear/activar un entorno virtual, instalar `pip install -r requirements.txt` y ejecutar `uvicorn main:app --reload --port 8000`.
3. Crear `frontend/.env` con `VITE_API_URL=http://localhost:8000`, sin barra final.
4. Desde `frontend`, ejecutar `npm ci` y `npm run dev`.

Frontend: `http://localhost:5173`. Swagger UI: `http://localhost:8000/docs`. Las tablas se crean al iniciar; la base debe existir.

## API

| Método | Ruta | Operación |
|---|---|---|
| GET | `/api/rutinas` | Listar |
| GET | `/api/rutinas/buscar?nombre=...` | Buscar por nombre |
| GET | `/api/rutinas/{id}` | Detalle |
| POST | `/api/rutinas` | Crear con ejercicios |
| PUT | `/api/rutinas/{id}` | Actualizar; reemplazar ejercicios si se envían |
| DELETE | `/api/rutinas/{id}` | Eliminar con ejercicios |

## Docker y límites pendientes

Se incluyen Dockerfiles y Compose con PostgreSQL 15, pero el frontend usa Node 18, incompatible con Vite 7. Actualizar esa imagen y probar el flujo antes de presentar `docker compose up --build` como inicio reproducible.

La URL predeterminada en `frontend/src/config.js` termina en `/` y el contexto concatena `/api/...`: sin configuración explícita puede generar `//api/...`. El `.env` anterior evita ese caso local.

`init-db.sql` solo contiene comentarios; no carga datos de ejemplo. No hay autenticación, paginación ni suite automatizada de pruebas. La revisión fue estática; no se afirma ejecución integral ni preparación para producción.

[Backend](backend/README.md) | [Frontend](frontend/README.md)
