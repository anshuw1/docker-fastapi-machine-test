# 🧪 FastAPI Machine Test – Dockerized User API

A lightweight FastAPI project created as a machine test for handling user data using file-based storage. This application is packaged using Docker and orchestrated via Docker Compose for simple deployment and scalability.

---

## 📌 Project Overview

This API allows users to be added through a JSON payload. It doesn’t use any external database – user data is saved in a local file (`users.json`) under the `app/data/` directory.

This project demonstrates:

- Python 3.12 with FastAPI
- Docker & Docker Compose for containerization
- Basic CRUD simulation with JSON file storage
- Auto-generated OpenAPI documentation

---

## 🛠 Tech Stack

| Tool           | Purpose                                  |
|----------------|------------------------------------------|
| **FastAPI**    | Web framework for building APIs          |
| **Uvicorn**    | ASGI server to serve FastAPI app         |
| **Docker**     | Containerization                         |
| **Docker Compose** | Service orchestration               |
| **Python 3.12** | Base runtime environment                |

---

## Run the Application

```bash
docker compose up --build
```
---
## Once running, visit the API documentation:
- Swagger UI: http://localhost:8000/docs
---
## Project Structure

```
docker-fastapi-userapi/
├── app/
│   ├── main.py            # FastAPI app entry point
│   ├── services.py        # Logic to handle file operations
│   └── data/              # Contains users.json
│       └── users.json     # Auto-created when user data is posted
├── Dockerfile             # Docker image instructions
├── docker-compose.yml     # Docker Compose file
├── requirements.txt       # Python dependencies
└── README.md              # Project documentation
```

---

## User Payload

```json
{
  "data": [
     {
        "first_name": "Anshu"
        "last_name": "Waghmare"
        "age": 23
     }
  ] 
}
```

---

## Dockerfile

```yaml
FROM python:3.12-slim

WORKDIR /app

COPY . /app

RUN pip install --no-cache-dir -r /app/requirements.txt

USER root

EXPOSE 8000

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
```

---

## Docker Compose File

```yaml
version: '3.8'

services:
  fastapi-app:
    build: .
    container_name: fastapi-app
    ports:
      - "8000:8000"
    volumes:
      - .:/app
      - ./app/data:/app/app/data
    restart: always
```



## Author

- **AnshuWaghmare**
- [GitHub Profile](https://github.com/anshuw1)
---
