# 📝 Task List App with Flask, PostgreSQL, and Redis

This project is a simple **Task List** web application built using **Flask** for the frontend/backend, **PostgreSQL** for persistent task storage, and **Redis** for caching. All services are containerized using **Docker Compose**.

---

## 🚀 Features

- ✅ Create and view tasks via a web UI
- 🐘 PostgreSQL database for persistent storage
- 🔄 Redis cache for faster access
- 🐳 Multi-service architecture using Docker Compose
- ⚙️ Environment configuration with `.env` support

---

## 📦 Project Structure

task-list-app/
├── web/ # Flask app
│ ├── app.py
│ ├── requirements.txt
│ ├── Dockerfile
│ └── templates/
│ └── index.html
├── db/ # PostgreSQL database
│ ├── Dockerfile
│ └── init.sql # Optional: DB init script
├── cache/ # Redis service
│ └── Dockerfile
├── docker-compose.yml
└── README.md

---

## 🛠 Getting Started

### Prerequisites

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

### Run the App

```bash
git clone https://github.com/your-username/task-list-app.git
cd task-list-app
docker compose up --build

Visit the app in your browser:
➡️ http://localhost:5000

Running application UI
<img width="959" alt="image" src="https://github.com/user-attachments/assets/d427a501-4b54-457f-a085-42a67fc41b8f" />

**### Bonus question**
Implement environment variable management in your Docker Compose file to handle different environments 
(development, production)

Run in development env
docker compose --env-file .env.dev up --build

Run in production env 
docker compose --env-file .env.prod up --build

📄 License
This project is licensed under the MIT License.

🤝 Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you’d like to change.

