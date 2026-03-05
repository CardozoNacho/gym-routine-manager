# Gym Routine Manager – Full Stack Web Application

**Autor:** Cardozo Peragallo Carlos Ignacio

Full-stack application built with FastAPI, React and PostgreSQL for managing workout routines and exercises. 
Includes REST API, modern frontend and Docker-based deployment.

## 🏗️ Arquitectura del Proyecto

El proyecto está organizado en tres componentes principales:

```
FinalProgIV/
├── backend/          # API RESTful con FastAPI
├── frontend/         # Aplicación web con React + Vite
├── docker-compose.yml  # Orquestación de servicios
└── init-db.sql       # Script de inicialización de BD
```

### Componentes

- **Backend**: API REST desarrollada con FastAPI y PostgreSQL para gestionar rutinas y ejercicios
- **Frontend**: Interfaz user desarrollada con React y Vite para consumir la API
- **Database**: PostgreSQL para almacenar datos de rutinas y ejercicios

## 🚀 Inicio Rápido

### Con Docker (Recomendado)

La forma más sencilla de ejecutar el proyecto completo:

```bash
# Clonar el repositorio
git clone https://github.com/CardozoNacho/FinalProgIV.git
cd FinalProgIV

# Ejecutar con Docker Compose
docker-compose up -d
```

Luego accede a la aplicación:
- **Frontend**: http://localhost:5173
- **Backend API Docs**: http://localhost:8000/docs
- **Database**: PostgreSQL en localhost:5432

### Instalación Local

**Requisitos:**
- Python 3.10+
- Node.js 16+
- PostgreSQL 12+

**Backend:**

```bash
cd backend
python -m venv venv
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

**Frontend:**

```bash
cd frontend
npm install
npm run dev
```

## 📚 Documentación

Cada componente del proyecto tiene su propia documentación detallada:

- **[Backend - Documentación Completa](backend/README.md)**
  - Instalación y configuración de la API
  - Endpoints disponibles
  - Modelos de datos y esquemas
  - Instrucciones de desarrollo

- **[Frontend - Documentación Completa](frontend/README.md)**
  - Instalación y configuración de la aplicación
  - Estructura de componentes
  - Guía de desarrollo
  - Scripts disponibles

## 🛠️ Tecnologías Utilizadas

### Backend
- **FastAPI** 0.115+ - Framework web rápido y moderno
- **SQLModel** 0.0.22+ - ORM con type hints
- **PostgreSQL** - Base de datos relacional
- **Uvicorn** 0.32.1 - Servidor ASGI

### Frontend
- **React** 18 - Librería para UI
- **Vite** - Build tool rápido
- **React Router DOM** - Navegación entre vistas
- **Fetch API** - Comunicación con el backend
- **CSS Puro** - Estilos personalizados

### DevOps
- **Docker** - Containerización
- **Docker Compose** - Orquestación de servicios

## 📁 Estructura del Proyecto

```
FinalProgIV/
├── backend/
│   ├── main.py              # Punto de entrada de la API
│   ├── database.py          # Configuración de base de datos
│   ├── requirements.txt     # Dependencias Python
│   ├── Dockerfile           # Imagen Docker del backend
│   ├── models/              # Modelos de datos (SQLModel)
│   ├── routers/             # Endpoints de la API
│   ├── schemas/             # Esquemas Pydantic
│   └── README.md            # Documentación del backend
│
├── frontend/
│   ├── src/
│   │   ├── App.jsx          # Componente principal
│   │   ├── config.js        # Configuración (URL del backend)
│   │   ├── components/      # Componentes reutilizables
│   │   ├── contexts/        # Gestión de estado global
│   │   ├── pages/           # Páginas principales
│   │   └── assets/          # Recursos estáticos
│   ├── package.json         # Dependencias Node
│   ├── Dockerfile           # Imagen Docker del frontend
│   ├── vite.config.js       # Configuración de Vite
│   └── README.md            # Documentación del frontend
│
├── docker-compose.yml       # Orquestación de servicios
├── init-db.sql              # Script de inicialización BD
└── README.md                # Este archivo
```

## 🔧 Configuración de Ambiente

### Variables de Entorno

**Backend** (crear archivo `.env` en `backend/`):
```
DATABASE_URL=postgresql://usuario:contraseña@localhost:5432/gym_routines_db
```

**Frontend** (crear archivo `.env` en `frontend/`):
```
VITE_API_URL=http://localhost:8000
```

Con Docker Compose, estas variables se configuran automáticamente en `docker-compose.yml`.

## 📝 Funcionalidades Principales

- ✅ Crear nuevas rutinas de entrenamiento
- ✅ Ver lista de rutinas disponibles
- ✅ Ver detalles de cada rutina (ejercicios, series, repeticiones)
- ✅ Modificar rutinas existentes
- ✅ Eliminar rutinas
- ✅ Gestión de ejercicios dentro de rutinas
- ✅ Interfaz responsiva y moderna

## 🐳 Comandos Docker Útiles

```bash
# Levantar los servicios en background
docker-compose up -d

# Ver logs de los servicios
docker-compose logs -f

# Detener todos los servicios
docker-compose down

# Reconstruir las imágenes
docker-compose up -d --build

# Entrar a la terminal de un servicio específico
docker-compose exec backend bash
docker-compose exec frontend sh
```

## 📊 Endpoints Principales (Backend)

```
GET  /api/rutinas          - Listar todas las rutinas
POST /api/rutinas          - Crear una nueva rutina
GET  /api/rutinas/{id}     - Obtener detalles de una rutina
PUT  /api/rutinas/{id}     - Actualizar una rutina
DELETE /api/rutinas/{id}   - Eliminar una rutina
```

Para documentación interactiva completa, accede a: **http://localhost:8000/docs**

## ❓ Troubleshooting

**El frontend no puede conectar con el backend:**
- Verifica que el backend esté corriendo en `http://localhost:8000`
- Verifica la variable `VITE_API_URL` en el archivo `.env` del frontend
- Con Docker Compose, asegúrate que `depends_on` esté configurado correctamente

**Errores de base de datos:**
- Verifica que PostgreSQL esté corriendo
- Verifica la cadena de conexión en la variable `DATABASE_URL`
- Con Docker Compose, espera a que el contenedor `db` se inicie completamente

**Puerto en uso:**
- Cambia los puertos en `docker-compose.yml` o en la configuración local si los puertos (5173, 8000, 5432) están siendo usados

## 📞 Contacto

Para más información sobre componentes específicos, consulta la documentación individual:
- [Backend README](backend/README.md)
- [Frontend README](frontend/README.md)

---

**Última actualización:** febrero 2026
