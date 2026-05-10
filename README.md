# 🚀 Java Microservices Portfolio — Sri Mega Kesavan

> **Java Backend Developer** | Spring Boot 3.x · Microservices · Kafka · Docker · PostgreSQL · AWS  
> 📍 UAE | 📧 srimegakesavan@gmail.com | 🔗 [LinkedIn](https://www.linkedin.com/in/srimegakesavan/)

---

## 🗺️ Architecture Overview

A production-grade microservice ecosystem built from scratch, replicating real enterprise backend architecture used in fintech, IoT, and e-commerce platforms.

```
                        ┌─────────────────────┐
                        │    API Gateway       │  ← Single entry point, routing, CORS
                        │  (Spring Cloud GW)   │
                        └────────┬────────────┘
                                 │
          ┌──────────────────────┼──────────────────────┐
          │                      │                       │
   ┌──────▼──────┐      ┌───────▼──────┐      ┌────────▼──────┐
   │ Auth Service│      │Product Catalog│      │ Order Service  │
   │  JWT + RBAC │      │  + Inventory  │      │  Saga Pattern  │
   └─────────────┘      └──────────────┘      └───────────────┘
          │                      │                       │
          └──────────────────────┼──────────────────────┘
                                 │
                    ┌────────────▼──────────────┐
                    │        Apache Kafka        │  ← Event streaming
                    └────────────┬──────────────┘
                                 │
          ┌──────────────────────┼──────────────────────┐
          │                      │                       │
   ┌──────▼──────┐      ┌───────▼──────┐      ┌────────▼──────┐
   │Notification │      │  Reporting   │      │  WebSocket     │
   │  Service    │      │  (Batch)     │      │  Real-Time     │
   └─────────────┘      └──────────────┘      └───────────────┘
                                 │
                    ┌────────────▼──────────────┐
                    │     IoT Dashboard + AI     │  ← MQTT + LLM
                    └───────────────────────────┘
```

---

## 📦 Microservices Index

| # | Service | Description | Key Tech | Repo |
|---|---------|-------------|----------|------|
| 1 | 🔐 **Auth Service** | JWT auth, BCrypt, RBAC, Spring Security | Java 17, Spring Security, JWT, PostgreSQL | [→ authservice](https://github.com/SriMegaKesavan/authservice) |
| 2 | 🛍️ **Product Catalog** | CRUD, pagination, search, Flyway migrations | Spring Boot, PostgreSQL, Flyway, JPA | [→ product-catalog](https://github.com/SriMegaKesavan/productcatalog) |
| 3 | 📋 **Task Manager** | REST API, streams-based filtering, DTO mapping | Spring Boot, Validation, Global Exception Handling | [→ taskmanager](https://github.com/SriMegaKesavan/taskmanager) |
| 4 | 🛒 **Order Service** | Saga pattern, distributed transactions, compensating actions | Spring Boot, @Transactional, REST clients | [→ orderservice](https://github.com/SriMegaKesavan/orderservice) |
| 5 | 📦 **Inventory Service** | Stock reserve/release/deduct, inter-service REST | Spring Boot, PostgreSQL, REST | [→ inventoryservice](https://github.com/SriMegaKesavan/inventoryservice) |
| 6 | 🗂️ **File Storage Service** | Multipart upload, profile-based storage, static serving | Spring Boot, Multipart, Spring Profiles | [→ fileservice](https://github.com/SriMegaKesavan/fileservice) |
| 7 | 🔔 **Notification Service** | Async email, @Scheduled, retry logic, SMTP | Spring Boot, @Async, JavaMailSender, Actuator | [→ notificationservice](https://github.com/SriMegaKesavan/notificationservice) |
| 8 | 🌐 **API Gateway** | Routing, CORS, auth forwarding, env-based config | Spring Cloud Gateway, Spring Profiles | [→ gateway](https://github.com/SriMegaKesavan/gateway) |
| 9 | 📊 **Reporting Service** | Spring Batch, CSV generation, scheduler, File Service upload | Spring Batch, @Scheduled, REST client | [→ reportingservice](https://github.com/SriMegaKesavan/reportingservice) |
| 10 | 💬 **WebSocket Service** | Real-time chat, live dashboards, private messaging | Spring WebSocket, STOMP, SockJS | [→ websocketservice](https://github.com/SriMegaKesavan/realtime) |
| 11 | ⚡ **Kafka Event Streaming** | Event-driven microservices, Redis pub/sub, durable streaming | Apache Kafka, Redis, Docker | [→ kafkaservice](https://github.com/SriMegaKesavan/kafkaservice) |
| 12 | 🌡️ **IoT Dashboard + AI** | MQTT telemetry, React UI, AI chatbot (local LLM) | Spring Boot, MQTT, React, Ollama/phi3, PostgreSQL | [→ IoT](https://github.com/SriMegaKesavan/IoT) · [→ iot-dashboard](https://github.com/SriMegaKesavan/iot-dashboard) |

---

## 🛠️ Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Backend** | Java 17, Spring Boot 3.x, Spring Security, Spring Data JPA, Spring Batch, Spring Cloud Gateway |
| **Messaging** | Apache Kafka, MQTT (Eclipse Mosquitto), Redis Pub/Sub |
| **Database** | PostgreSQL, Redis, H2 (testing) |
| **Security** | JWT, BCrypt, OAuth2, Role-Based Access Control |
| **DevOps** | Docker, Docker Compose, Jenkins, GitHub Actions |
| **Cloud** | AWS EC2, AWS RDS, AWS CloudWatch, AWS S3 |
| **AI / LLM** | Spring AI, Ollama (phi3), LLM API integration |
| **Frontend** | React 18, REST API integration, WebSocket (STOMP) |
| **Monitoring** | Spring Actuator, Custom Health Indicators |

---

## 🏗️ How to Run the Full Ecosystem

### Prerequisites
- Java 17+
- Docker & Docker Compose
- Maven 3.8+

### Start infrastructure
```bash
# PostgreSQL
docker run -d --name pg -e POSTGRES_PASSWORD=postgres -p 5432:5432 postgres:15

# Kafka + Zookeeper
docker-compose -f kafka-compose.yml up -d

# MQTT Broker
docker run -d --name mqtt-broker -p 1883:1883 eclipse-mosquitto

# Redis
docker run -d --name redis -p 6379:6379 redis:7
```

### Start services (in order)
```bash
# 1. Auth Service (port 8081)
# 2. Product Catalog (port 8082)
# 3. Inventory Service (port 8083)
# 4. Order Service (port 8084)
# 5. Notification Service (port 8085)
# 6. File Storage Service (port 8086)
# 7. Reporting Service (port 8087)
# 8. WebSocket Service (port 8088)
# 9. IoT Backend (port 8080)
# 10. API Gateway (port 8090) ← start last
```

---

## 🔑 Key Design Patterns Applied

| Pattern | Where Applied |
|---------|--------------|
| **Saga (Orchestration)** | Order Service — distributed transaction management |
| **Event-Driven Architecture** | Kafka Service — async inter-service communication |
| **API Gateway Pattern** | Gateway — single entry point, routing |
| **CQRS basics** | Reporting Service — read-optimised batch queries |
| **Circuit Breaker** | Feign clients — resilience with fallback |
| **Repository Pattern** | All services — clean data access layer |
| **DTO / Mapper Pattern** | All services — clean API contract separation |

---

## 🏢 Real-World Domain Coverage

- **Fintech / Payments** — Order lifecycle, distributed transactions, idempotency
- **IoT** — Device registration, telemetry ingestion, real-time monitoring, AI insights  
- **E-commerce** — Product catalog, inventory management, order management  
- **Enterprise** — File management, batch reporting, notification systems  
- **Security** — Auth, JWT, RBAC — foundation for all services

---

## 👨‍💻 About

**Sri Mega Kesavan** — Java Backend Developer based in UAE with 4.5 years at Infosys (Cisco account), building enterprise IoT and backend systems.

📧 srimegakesavan@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/srimegakesavan/)  
📍 Dubai, UAE
