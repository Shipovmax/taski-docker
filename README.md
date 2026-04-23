# Taski

A minimal full-stack task manager — create, complete, and delete tasks.  
Django REST Framework backend + React frontend, wired together with Nginx and Docker Compose.

---

## Features

- **Task list** — view all tasks with title, description, and completion status
- **Create / edit / delete** — full CRUD via modal form in the React SPA
- **Toggle completion** — mark tasks done directly from the list
- **REST API** — standard ModelViewSet; `DELETE` returns the deleted object for frontend state sync
- **CORS** — `django-cors-headers` configured for local SPA development
- **Fully containerised** — one command brings up DB + backend + frontend + gateway

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Python, Django 5.1, Django REST Framework 3.15 |
| Frontend | React 18 |
| Database | PostgreSQL 13 |
| Gateway | Nginx |
| Infrastructure | Docker Compose |

---

## Quick Start

```bash
cp .env.example .env   # fill in DB credentials and SECRET_KEY
docker compose up --build
```

App available at `http://localhost:8000`.

---

## Environment Variables (`.env`)

```env
POSTGRES_DB=taski
POSTGRES_USER=taski
POSTGRES_PASSWORD=taski
DB_HOST=db
DB_PORT=5432
SECRET_KEY=your-django-secret-key
DEBUG=False
ALLOWED_HOSTS=localhost,127.0.0.1
```

---

## API

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/tasks/` | List all tasks |
| `POST` | `/api/tasks/` | Create a task |
| `PATCH` | `/api/tasks/{id}/` | Update a task |
| `DELETE` | `/api/tasks/{id}/` | Delete a task (returns deleted object) |

---

## Project Structure

```
taski/
├── backend/
│   ├── api/               # Task model, serializer, viewset
│   └── backend/           # Django settings, urls
├── frontend/
│   └── src/
│       ├── App.js
│       └── components/    # TabList, Task, TaskEditModal
├── gateway/               # Nginx Dockerfile + nginx.conf
└── docker-compose.yml
```

---

## Author

- GitHub: [Shipovmax](https://github.com/Shipovmax)
- Email: shipov.max@icloud.com
