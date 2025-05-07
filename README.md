# 📝 Task List App with Flask, PostgreSQL, and Redis

This project is a multi-service Task List web application built with **Flask**, **PostgreSQL**, and **Redis**, containerized using **Docker Compose**, and deployed via a **CI/CD pipeline using GitHub Actions**. It includes advanced Docker practices like multi-stage builds, environment management, persistent volumes, and secure deployment.

---

## 🚀 Features

- ✅ Create and view tasks via a web UI
- 🐘 PostgreSQL for persistent storage
- 🔄 Redis for caching
- 🐳 Dockerized multi-service architecture
- 🔐 Environment-specific configuration (`.env.dev`, `.env.prod`)
- 📦 Multi-stage builds for optimized images
- 🚢 CI/CD pipeline with GitHub Actions + Docker Hub
- 📊 Optional: Advanced logging & monitoring with ELK / Prometheus

---

## 🗂 Project Structure

```bash
task-list-app/
├── web/                  # Flask app
│   ├── app.py
│   ├── requirements.txt
│   ├── Dockerfile
│   └── templates/
│       └── index.html
├── db/                   # PostgreSQL
│   ├── Dockerfile
│   └── init.sql
├── cache/                # Redis
│   └── Dockerfile
├── docker-compose.yml
├── .env.dev              # Development env vars
├── .env.prod             # Production env vars
├── .github/workflows/
│   └── ci.yml            # GitHub Actions pipeline
└── README.md

🛠️ Getting Started
✅ Prerequisites
Docker 20.10+

Docker Compose 1.27+

(For CI/CD) GitHub account and Docker Hub account

🚀 Run in Development
docker compose --env-file .env.dev up --build

App will be available at:
➡️ http://localhost:5000

🚀 Run in Production
docker compose --env-file .env.prod up --build -d

⚙️ Environment Configuration
Use .env.dev and .env.prod to manage per-environment variables:

# .env.dev
REDIS_HOST=cache
REDIS_PORT=6379
DB_HOST=db
DB_NAME=tasksdb
DB_USER=postgres
DB_PASSWORD=postgres

Then in docker-compose.yml, these are injected via:

environment:
  REDIS_HOST: ${REDIS_HOST}
  ...

📦 Docker Setup
Each service has its own Dockerfile

The Flask app uses a multi-stage build for optimized image size

PostgreSQL data is persisted via a Docker volume (db_data)

Services communicate over a default Docker bridge network

🛡️ Security & Best Practices
Multi-stage builds for smaller images

No root usage in containers (where applicable)

.env files are excluded from git

Secrets like DOCKER_USERNAME are stored securely in GitHub

🔄 CI/CD Pipeline (GitHub Actions)
A full pipeline is included in .github/workflows/ci.yml:

💡 Steps:
Checkout Code

Log in to Docker Hub

Build & Tag Images

Push to Docker Hub

(Optional) Deploy via SSH or similar

🧪 Set Secrets in GitHub
Go to your repo → Settings → Secrets → Actions → Add:

DOCKER_USERNAME

DOCKER_PASSWORD

📊 Logging & Monitoring (Bonus)
To enable advanced logging/monitoring:

Option A: ELK Stack
Logstash collects logs from services

Elasticsearch stores them

Kibana visualizes

Option B: Prometheus + Grafana
Prometheus scrapes metrics

Grafana dashboards visualize service health

Instructions for this setup can be added if required.

🧪 Testing
TBD: Add Python unit tests in /web/tests and extend the CI pipeline to run them via:

- name: Run tests
  run: pytest

🌐 Deployment Preview
Live: http://localhost:5000

Or deploy via Docker Hub:

docker pull <your-dockerhub-username>/task-list-app:latest