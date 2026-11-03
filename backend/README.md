# Backend de Gym Routine Manager

Proyecto académico individual. FastAPI 0.115.6, SQLModel 0.0.22, Uvicorn 0.32.1 y PostgreSQL. Dependencias en `requirements.txt`.

Requiere Python 3.10+ y una base PostgreSQL existente. Desde `backend`, crear/activar un entorno virtual e instalar `pip install -r requirements.txt`. Crear `.env` con `DATABASE_URL=postgresql://<usuario>:<clave>@localhost:5432/rutinas_gym_db`.

Ejecutar `uvicorn main:app --reload --port 8000`; documentación en `http://localhost:8000/docs`.

## Rutas reales

- `GET /api/rutinas`: listar con ejercicios.
- `GET /api/rutinas/buscar?nombre=...`: búsqueda parcial sin distinguir mayúsculas.
- `GET /api/rutinas/{id}`: detalle o 404.
- `POST /api/rutinas`: crear con ejercicios; 201.
- `PUT /api/rutinas/{id}`: actualizar; reemplaza ejercicios si se envían.
- `DELETE /api/rutinas/{id}`: eliminar rutina y ejercicios; 204.

Los ejercicios se gestionan como parte de una rutina. No hay endpoints independientes, autenticación ni paginación. Los esquemas validan días, longitudes y números; el router comprueba nombres duplicados.

Ver [inicio general y limitaciones](../README.md). No se incluye suite automatizada de pruebas.
