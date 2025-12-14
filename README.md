# 🚨 Sentinel — Incident Management System with AI Ops Assistant

Sentinel is a cloud-native, event-driven incident management system that ingests alerts, tracks incidents, and provides **AI-assisted operational insights** to help engineers respond faster and more effectively.

Inspired by real-world systems like PagerDuty and Opsgenie, Sentinel focuses on **correct system design and responsible AI usage**, not automation hype.

---

## 🎯 What Sentinel Does

- Ingests alerts from applications and monitoring systems
- Creates and manages incident lifecycles
- Streams alert and incident events using Kafka
- Uses an AI Ops Assistant to:
  - summarize incidents
  - identify recurring failure patterns
  - suggest remediation steps
- Displays incidents, alerts, and insights in a web dashboard

---

## 🧠 System Architecture

```

Frontend (React)
↓
API Gateway (Node.js)
↓
Microservices

- alert-service
- incident-service
- notification-service
  ↓
  Kafka (event bus)
  ↓
  AI Ops Assistant (LangGraph)
  ↓
  Dashboard / Slack

```

---

## 🛠️ Tech Stack

### Frontend

- React + TypeScript
- Vite
- Tailwind CSS

### Backend

- Node.js + TypeScript
- Express.js
- Zod (request validation)

### Event Streaming

- Apache Kafka
- KafkaJS

### AI

- LangChain.js
- LangGraph.js
- OpenAI API
- Vector DB (Pinecone / Weaviate)

### Databases

- MongoDB — alerts and incidents
- PostgreSQL — metadata and audit logs
- Redis — caching and rate limiting

### Infrastructure & DevOps

- Docker
- Kubernetes
- Terraform
- GitHub Actions (CI)
- Prometheus + Grafana (monitoring)

---

## 📁 Project Structure

```

sentinel/
│
├── apps/
│ ├── api-gateway/
│ ├── alert-service/
│ ├── incident-service/
│ ├── notification-service/
│ ├── ai-ops-agent/
│ └── web/
│
├── packages/
│ ├── shared-types/
│ └── kafka-lib/
│
├── k8s/
│ ├── services/
│ ├── kafka/
│ └── monitoring/
│
├── terraform/
│ ├── modules/
│ └── environments/
│
├── docker-compose.yml
├── pnpm-workspace.yaml
└── README.md

```

---

## 🔄 How It Works

### 1. Alert Ingestion

- Applications or monitoring tools send alerts to the API Gateway
- Alerts are validated and persisted

### 2. Event Streaming

- Alert and incident events are published to Kafka
- Services consume events asynchronously

### 3. Incident Management

- Incidents are created or updated based on alert patterns
- Incident lifecycle is tracked (open, acknowledged, resolved)

### 4. AI Ops Assistant

- Consumes incident events
- Retrieves similar past incidents using vector search
- Generates:
  - incident summary
  - probable root cause
  - recommended next actions

### 5. Visualization & Notification

- Updates shown in the web dashboard
- Optional Slack notifications for on-call engineers

---

## 🧠 AI Ops Assistant Design

```

Incident Event
↓
Context & Metadata Analysis
↓
Similar Incident Retrieval (RAG)
↓
Summary & Recommendation Generation

```

**The AI assistant is advisory only** — it does not execute fixes or modify infrastructure.

---

## 📈 Scaling & Reliability

- Kafka enables fan-out and replay of alert and incident events
- Kubernetes HPA scales alert and incident services
- Retry logic and dead-letter topics for failed events
- Idempotent incident creation to prevent duplicates

---

## 🔐 Security & Production Practices

- Input validation on all APIs
- Rate limiting at the API Gateway
- Secrets managed via environment variables / Kubernetes Secrets
- Audit logs for all incident state changes

---

## 🚀 Local Development

```bash
pnpm install
docker-compose up -d
pnpm dev
```

---

## 📌 What This Project Demonstrates

- Event-driven microservice architecture
- Correct, justified use of Kafka
- Production-grade backend engineering
- Kubernetes-based deployment and scaling
- Responsible, assistive use of AI agents in operations

---

## 🧭 Future Improvements

- Alert deduplication rules
- Role-based access control
- On-call scheduling
- Advanced incident correlation
