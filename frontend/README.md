# Frontend de Gym Routine Manager

Proyecto académico individual con React 19, React Router 7, Vite 7, Context API y Fetch. Listado, búsqueda, detalle, creación, edición y eliminación de rutinas con ejercicios.

## Inicio local

El lockfile exige Node `^20.19.0 || >=22.12.0`. Desde `frontend`, crear `.env` con `VITE_API_URL=http://localhost:8000`, sin barra final, y ejecutar:

```bash
npm ci
npm run dev
```

Frontend: `http://localhost:5173`; backend esperado: `http://localhost:8000`. Reiniciar Vite si cambia `.env`.

`npm run build` genera el bundle; `npm run lint` ejecuta ESLint. No hay script de pruebas funcionales.

## Estructura y límites

`src/pages/`: pantallas; `src/components/`: tarjetas y navegación; `src/contexts/RutinasContext.jsx`: peticiones/estado; `src/config.js`: URL; `src/App.jsx`: rutas.

El Dockerfile usa Node 18 y debe actualizarse para Vite 7. La URL predeterminada termina en `/` y puede producir una doble barra; usar el `.env` anterior evita ese caso local. Conviene verificar los formularios ante errores de API: el contexto captura errores y algunas operaciones retornan `undefined`.

Ver [guía general](../README.md).
