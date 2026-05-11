# TallerMate

Aplicación Fullstack para la gestión de un taller mecánico, desarrollada con **Laravel** (backend/API RESTful) y **Angular** (frontend SPA). La aplicación está completamente dockerizada para facilitar el desarrollo local.

## Características principales

- **Backend Laravel**
  - API RESTful para todas las entidades: mecánicos, clientes, vehículos, reparaciones, piezas.
  - Autenticación y autorización con roles (admin/mecánico) usando Laravel Sanctum (API tokens).
  - Migraciones y seeders automáticos al iniciar el contenedor.
  - Seeder que crea un usuario administrador por defecto (`admin@example.com` / `password`).
  - Gestión de relaciones entre entidades.
  - CORS abierto para permitir acceso desde el frontend.

- **Frontend Angular**
  - SPA moderna y responsiva.
  - Login y registro de usuarios.
  - Panel de administración para gestionar mecánicos, clientes, vehículos, reparaciones y piezas.
  - Todas las llamadas a la API se hacen vía `/api` (proxy nginx), evitando problemas de CORS.

- **Docker & Desarrollo Local**
  - Contenedores para backend (Laravel+Apache), frontend (Angular+nginx), y base de datos (MariaDB).
  - phpMyAdmin disponible en `http://localhost:8080` para administración de la BD.
  - Configuración lista para iniciar con un comando.

## Despliegue en desarrollo local

1. Clona el repositorio.
2. Copia el archivo `.env.example` a `.env` en la carpeta `backend/`:
   ```sh
   cp backend/.env.example backend/.env
   ```
3. Ejecuta los contenedores:
   ```sh
   docker-compose up -d --build
   ```
4. Accede a la aplicación:
   - **Frontend**: http://localhost
   - **phpMyAdmin**: http://localhost:8080 (usuario: `root`, contraseña: `root`)
5. Inicia sesión con las credenciales por defecto:
   - **Usuario**: `admin@example.com`
   - **Contraseña**: `password`

## Estructura del proyecto

```
taller_app/
├── backend/         # Laravel API
│   ├── app/         # Modelos, controladores, etc.
│   ├── database/    # Migraciones y seeders
│   ├── public/      # DocumentRoot
│   ├── routes/      # Rutas API/web
│   ├── Dockerfile   # Docker backend
│   └── ...
├── frontend/        # Angular SPA
│   ├── src/         # Código fuente Angular
│   ├── Dockerfile   # Docker frontend
│   └── ...
├── docker-compose.yml
└── README.md
```

## Instalación y despliegue local (desarrollo)

1. Clona el repositorio y copia tu `.env` en `backend/`.
2. Ejecuta:
   ```sh
   docker-compose up -d --build
   ```
3. Accede al frontend en `http://localhost` (o el dominio configurado).

## Seguridad
- Backend y base de datos accesibles internamente dentro de la red Docker.
- phpMyAdmin disponible localmente para desarrollo.

---

¡Listo para usar y ampliar según las necesidades de tu taller!

