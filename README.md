# 🧑‍💻 Traceo - Centralized Logging & Audit Backend

> A **real-world backend system** that collects, processes, and queries logs and user activities across multiple services. Built to demonstrate **distributed backend engineering, event-driven architecture, and audit logging**.

This project is ideal for **entry-level developers who want to show production-grade backend skills**.

---

## 📌 Features

* **Centralized log ingestion** from multiple services
* **Asynchronous processing** using background workers
* **Structured storage** for logs and audit events
* **Event-driven architecture** (RabbitMQ/Kafka)
* **Query API** with filters, pagination, and audit trails
* **Immutable audit logs** for critical actions
* **Dockerized services** for easy deployment
* **Swagger documentation** for APIs

---

## 🎯 What It Does

1. Services generate logs (e.g., errors, actions, payments, role changes)
2. Logs are sent to a **central ingestion API**
3. Logs are **queued asynchronously** to workers
4. Workers process, enrich, and store logs in the database
5. Query API provides **searchable, filterable logs** for monitoring, debugging, or auditing
6. Audit logs are **immutable**, ensuring compliance and security

---

## 🧩 Folder Structure

```md

centralized-logging-backend/
├── api-gateway/              # NestJS API Gateway
│   ├── src/
│   ├── Dockerfile
│   └── README.md
├── ingestion-service/        # Node.js/Express Log Ingestion API
│   ├── src/
│   ├── Dockerfile
│   └── README.md
├── log-worker/               # Go Worker for processing logs
│   ├── main.go
│   ├── Dockerfile
│   └── README.md
├── query-service/            # NestJS Query API
│   ├── src/
│   ├── Dockerfile
│   └── README.md
├── message-broker/           # RabbitMQ/Kafka configs
│   └── docker-compose.yml
├── database/                 # PostgreSQL or MongoDB configs
│   └── docker-compose.yml
├── docker-compose.yml        # Orchestrates all services
├── README.md                 # This README
└── .env.example              # Example environment variables

```

---

## 🧱 Tech Stack

| Layer                     | Technology                                             |
| ------------------------- | ------------------------------------------------------ |
| Programming Languages     | Node.js, NestJS, Go                                    |
| Backend Frameworks        | Express.js, NestJS, Gin (for worker optional)          |
| Database                  | PostgreSQL (structured logs), Redis (optional caching) |
| Message Queue             | RabbitMQ or Kafka                                      |
| Background Processing     | Go Worker                                              |
| Authentication & Security | JWT, Role-based access control                         |
| API Documentation         | Swagger / OpenAPI                                      |
| Deployment                | Docker, Docker Compose                                 |

---

## 🛠️ Services Breakdown

### 1️⃣ API Gateway (NestJS)

* Entry point for clients
* Auth validation & routing
* Rate limiting
* Swagger docs

### 2️⃣ Log Ingestion API (Node.js/Express)

* Receives logs from multiple services
* Validates and normalizes logs
* Pushes logs to message queue

### 3️⃣ Log Processing Worker (Go)

* Consumes log events from queue
* Enriches logs (metadata, timestamps)
* Stores structured logs in DB
* Handles retries & failures

### 4️⃣ Query API (NestJS)

* Query and filter logs
* Access control for admins vs normal users
* Provides audit trails for critical actions

---

## 🔁 Workflow

```text
Service (Order / Inventory / Payment)
        │
        ▼
Log Ingestion API (Node.js/Express)
        │
        ▼
Message Queue (RabbitMQ / Kafka)
        │
        ▼
Log Processing Worker (Go)
        │
        ▼
Database (PostgreSQL)
        │
        ▼
Query API (NestJS)
        │
        ▼
Admins / Engineers / Auditors
```

---

## ⚡ Setup & Run (Local)

### Clone the repository

```bash
git clone https://github.com/syedrafinulhuq/Traceo.git
cd centralized-logging-backend
```

### Copy environment variables

```bash
cp .env.example .env
```

### Start all services using Docker Compose

```bash
docker-compose up --build
```

### Access services

* API Gateway Swagger: `http://localhost:3000/api/docs`
* Query API Swagger: `http://localhost:4000/api/docs`

---

## 📄 Example Log Payload

```json
{
  "service": "order-service",
  "level": "ERROR",
  "message": "Payment failed",
  "userId": "123",
  "timestamp": "2026-02-18T12:00:00Z",
  "metadata": {
    "orderId": "ORD-98765",
    "retryCount": 1
  }
}
```

---

## 📈 What This Project Has

* Event-driven backend design
* Microservices understanding
* Asynchronous processing & queues
* Immutable audit logging
* Multi-service orchestration with Docker
* Realistic, production-grade backend thinking

---

## 📎 Resume Line

> Developed a centralized logging and audit backend using **Node.js, NestJS, Go**, RabbitMQ/Kafka, and PostgreSQL, enabling structured logging, audit trails, and event-driven processing across multiple services.

---
# Traceo
