# FastAPI Production Template

[![CI](https://github.com/kauadev77/fastapi-production-template/actions/workflows/ci.yml/badge.svg)](https://github.com/kauadev77/fastapi-production-template/actions/workflows/ci.yml)
![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.115-009688?logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-ready-4169E1?logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-ready-2496ED?logo=docker&logoColor=white)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A clean, production-minded FastAPI starter showing how I structure a small backend service with API versioning, environment-based configuration, health checks, tests, Docker and CI.

## What this demonstrates

- FastAPI application factory
- Versioned API routes
- Pydantic settings
- Health and readiness endpoints
- Service-layer separation
- PostgreSQL-ready configuration
- Docker and Docker Compose
- Automated tests with pytest
- GitHub Actions CI
- Environment configuration with .env

## Architecture

```mermaid
flowchart TD
    Client[Client] --> API[FastAPI]
    API --> V1[/v1 routes/]
    V1 --> Service[Service layer]
    API --> Config[Environment settings]
    Config --> DB[(PostgreSQL-ready config)]
    Tests[pytest] --> API
    CI[GitHub Actions] --> Tests
```

## Project structure

```text
.
├── app/
│   ├── api/
│   │   └── v1/
│   │       └── routes.py
│   ├── core/
│   │   └── config.py
│   ├── services/
│   │   └── echo.py
│   ├── main.py
│   └── schemas.py
├── tests/
│   └── test_api.py
├── .github/workflows/ci.yml
├── .env.example
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
└── README.md
```

## Local development

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```

Interactive docs: `http://localhost:8000/docs`

## Endpoints

### Health

```http
GET /v1/health
```

### Readiness

```http
GET /v1/ready
```

### Echo example

```http
POST /v1/echo
Content-Type: application/json

{
  "message": "hello world"
}
```

## Tests

```bash
pytest
```

## Docker

```bash
docker compose up --build
```

## Environment

Copy the example file:

```bash
cp .env.example .env
```

On Windows PowerShell:

```powershell
Copy-Item .env.example .env
```

Settings use the `APP_` prefix, for example:

```env
APP_ENVIRONMENT=development
APP_DATABASE_URL=postgresql://portfolio:portfolio@localhost:5432/portfolio
```

## Portfolio safety

This project was created from scratch to demonstrate backend engineering practices. It does not expose proprietary production code or private infrastructure.

## License

MIT
