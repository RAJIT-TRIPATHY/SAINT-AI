# 🧠 SAINT-AI — Semi-Autonomous Intelligence Network Technology

> **Enterprise AI Workflow Infrastructure** — Not a chatbot. A workflow-executing, document-producing, audit-traceable enterprise automation system.

[![Java](https://img.shields.io/badge/Java-17+-ED8B00?style=flat&logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?style=flat&logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Angular](https://img.shields.io/badge/Angular-17+-DD0031?style=flat&logo=angular&logoColor=white)](https://angular.io/)
[![n8n](https://img.shields.io/badge/n8n-Orchestrator-EA4B71?style=flat&logo=n8n&logoColor=white)](https://n8n.io/)
[![MySQL](https://img.shields.io/badge/MySQL-8.x-4479A1?style=flat&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-6.x-47A248?style=flat&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 📌 Table of Contents

1. [What is SAINT-AI?](#what-is-saint-ai)
2. [System Architecture](#system-architecture)
3. [Core Modules](#core-modules)
4. [Technology Stack](#technology-stack)
5. [Phase Execution Plan](#phase-execution-plan)
6. [SaaS Revenue Model](#saas-revenue-model)
7. [Getting Started](#getting-started)
8. [Environment Variables](#environment-variables)
9. [API Overview](#api-overview)
10. [Human-in-the-Loop Governance](#human-in-the-loop-governance)
11. [Roadmap to 2026](#roadmap-to-2026)
12. [Contributing](#contributing)
13. [License](#license)

---

## 🤖 What is SAINT-AI?

SAINT-AI is an **Enterprise AI Operating Layer** — a full-stack, multi-model AI orchestration system designed for real task execution, workflow automation, and document production at enterprise scale.

Think of it as:
> **Zapier + Notion + Enterprise AI + Industrial Control Layer**

### Key Differentiators

| Feature | SAINT-AI | Traditional Chatbots |
|---|---|---|
| Task Execution | ✅ Real workflow execution | ❌ Conversation only |
| Document Generation | ✅ Audit-traceable outputs | ❌ Not supported |
| Human Approval Loop | ✅ Built-in governance | ❌ Fully automated |
| Multi-Model AI | ✅ OpenAI, Gemini, Claude | ❌ Single model |
| Enterprise Auth | ✅ JWT + RBAC | ❌ Basic/none |
| Cost Tracking | ✅ Per-request monitoring | ❌ Not supported |

---

## 🏗 System Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   SAINT-AI      │    │   n8n            │    │   AI Providers  │
│   Dashboard     │◄──►│   Orchestrator   │◄──►│ OpenAI / Gemini │
│   (Angular)     │    │   (Workflows)    │    │ Claude / etc.   │
└─────────────────┘    └──────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│ 💳 Subscription │    │ 🗄️  Dual DB       │    │ ☁️  Multi-Cloud  │
│   Billing       │    │ MySQL + MongoDB  │    │ GCS/S3/OneDrive │
└─────────────────┘    └──────────────────┘    └─────────────────┘
         │
         ▼
┌─────────────────┐
│ 🛡️  Spring Boot  │
│   Backend (JWT) │
└─────────────────┘
```

### Three-Tier Architecture

**1️⃣ Data Layer**
- **MySQL** — Users, subscriptions, document metadata, payments, audit logs
- **MongoDB** — AI logs, workflow objects, large JSON payloads, prompt history
- **Object Storage (GCS / S3)** — Files, images, video assets
- **OneDrive** — Office 365 integration and team collaboration

**2️⃣ Execution Layer**
- **Spring Boot Backend** — Auth (JWT), role-based access control, billing logic, signed file URLs
- **n8n Orchestrator** — AI calls, document generation, workflow automation, Notion sync

**3️⃣ Intelligence Layer**
- Multi-model AI providers (text / image / video)
- Prompt sanitization & injection prevention
- Cost tracking per request
- Human approval gating for sensitive outputs

---

## 🧩 Core Modules

### 🔐 Auth & Identity
- JWT-based authentication
- Role-Based Access Control (RBAC): `ADMIN`, `PRO`, `FREE`, `ENTERPRISE`
- OAuth2 integration (planned)
- Session management and token refresh

### 🤖 AI Orchestration
- Multi-provider routing (OpenAI GPT-4, Google Gemini, Anthropic Claude)
- Prompt sanitization pipeline
- Fallback and retry logic per provider
- Token usage tracking and cost attribution

### 📄 Document Engine
- Template-based document generation (PDF, DOCX, XLSX)
- Audit trail per document (who generated, which model, timestamp)
- Signed download URLs via GCS/S3
- Version history in MongoDB

### 🔁 Workflow Automation (n8n)
- Visual workflow builder
- AI-triggered automation pipelines
- Webhook integrations
- Notion, Slack, Email connectors

### 💳 Billing & Subscription
- Plan management: Free / Pro / Enterprise
- Usage metering per AI request
- Stripe / payment gateway integration
- Invoice generation

### 👥 Human-in-the-Loop (HITL)
- Approval queue for sensitive AI outputs
- Engineer review workflow
- Override and correction logging
- Compliance audit trail

### ☁️ Multi-Cloud Storage
- Unified file access layer across GCS, S3, OneDrive
- Presigned URL generation
- Folder-level access control per user/subscription

---

## 🛠 Technology Stack

| Layer | Technology |
|---|---|
| **Frontend** | Angular 17+, TypeScript, TailwindCSS |
| **Backend** | Java 17+, Spring Boot 3.x |
| **Auth** | Spring Security, JWT, OAuth2 |
| **Workflow Engine** | n8n (self-hosted) |
| **Relational DB** | MySQL 8.x |
| **Document DB** | MongoDB 6.x |
| **Object Storage** | Google Cloud Storage, AWS S3 |
| **Office Integration** | Microsoft OneDrive API |
| **AI Providers** | OpenAI API, Google Gemini, Anthropic Claude |
| **Containerization** | Docker, Docker Compose |
| **CI/CD** | GitHub Actions (planned) |
| **Monitoring** | Spring Actuator, custom cost dashboard |

---

## 🚀 Phase Execution Plan

### Phase 1 — Foundation (Months 1–2)
**Goal:** Stable backend, auth, and database layer

- [ ] Spring Boot project scaffolding
- [ ] MySQL schema: users, subscriptions, documents, payments
- [ ] MongoDB setup: AI logs, workflow objects
- [ ] JWT authentication & RBAC implementation
- [ ] Basic REST API (CRUD for users, documents)
- [ ] Docker Compose for local development
- [ ] Unit tests for auth and data layers

**Milestone:** Authenticated API serving structured data from dual DBs

---

### Phase 2 — AI Integration (Months 2–3)
**Goal:** Multi-model AI execution with cost tracking

- [ ] OpenAI GPT-4 integration (text generation)
- [ ] Google Gemini integration
- [ ] Anthropic Claude integration
- [ ] Provider abstraction layer (factory pattern)
- [ ] Prompt sanitization middleware
- [ ] Per-request cost tracking and storage in MongoDB
- [ ] Image generation endpoint (DALL·E / Imagen)
- [ ] Video generation stub (placeholder for Phase 4)

**Milestone:** AI requests routed, logged, and costed per provider

---

### Phase 3 — Workflow Engine (Month 3–4)
**Goal:** n8n orchestration connected to SAINT-AI backend

- [ ] Self-hosted n8n deployment (Docker)
- [ ] Webhook triggers from Spring Boot to n8n
- [ ] Document generation workflow (n8n → AI → template → PDF/DOCX)
- [ ] Notion sync workflow
- [ ] Email notification workflow
- [ ] Error handling and retry logic in workflows
- [ ] Workflow execution logs stored in MongoDB

**Milestone:** End-to-end document generation via workflow

---

### Phase 4 — Frontend Dashboard (Month 4–5)
**Goal:** Angular dashboard for users and admins

- [ ] Angular project setup with TailwindCSS
- [ ] Login / Registration UI (JWT integration)
- [ ] User dashboard: AI call history, document list, usage stats
- [ ] Admin panel: user management, subscription overview
- [ ] Cost tracking dashboard (charts, per-model breakdown)
- [ ] Document viewer with signed URL download
- [ ] Human approval queue UI

**Milestone:** Fully functional user-facing dashboard

---

### Phase 5 — Billing & SaaS (Month 5–6)
**Goal:** Revenue-generating subscription system

- [ ] Stripe integration (or local equivalent)
- [ ] Plan enforcement: Free / Pro / Enterprise limits
- [ ] Usage metering tied to billing
- [ ] Invoice generation and download
- [ ] Webhook handling for payment events (success, failure, renewal)
- [ ] Upgrade/downgrade plan flow

**Milestone:** End-to-end billing cycle operational

---

### Phase 6 — Multi-Cloud Storage & Office Integration (Month 6)
**Goal:** Unified file management across cloud providers

- [ ] GCS integration (upload, download, presigned URLs)
- [ ] AWS S3 integration
- [ ] OneDrive API integration
- [ ] Unified storage abstraction layer
- [ ] Folder structure per user/subscription
- [ ] File type validation and virus scanning (optional)

**Milestone:** Files stored, retrieved, and shared across cloud providers

---

### Phase 7 — HITL Governance & Audit (Month 6–7)
**Goal:** Enterprise-grade compliance and human oversight

- [ ] Approval queue system (sensitive AI outputs held for review)
- [ ] Engineer review and override workflow
- [ ] Full audit log: who triggered, which model, what output, who approved
- [ ] Exportable audit reports (PDF)
- [ ] Role-based visibility of audit logs

**Milestone:** Compliance-ready audit trail for all AI outputs

---

### Phase 8 — Validation & Scale (Month 7–8)
**Goal:** Real-user testing and infrastructure optimization

- [ ] Deploy to cloud (GCP / AWS)
- [ ] Onboard 50–100 beta users
- [ ] Monitor cost per AI request at scale
- [ ] Performance profiling and DB query optimization
- [ ] Load testing (JMeter or k6)
- [ ] Security audit (OWASP checklist)
- [ ] Documentation: API docs (Swagger/OpenAPI), user guides

**Milestone:** Production-ready system with validated user feedback

---

## 💰 SaaS Revenue Model

| Tier | AI Calls | Storage | Features | Target |
|---|---|---|---|---|
| **Free** | 50/month | 500 MB | Basic workflows, text AI | Students, explorers |
| **Pro** | 2,000/month | 10 GB | Premium models, DOCX/PDF export, automation | Startups, SMEs |
| **Enterprise** | Unlimited | 100 GB+ | Image/video gen, team dashboards, SLA, white-label | Corporates, universities |

---

## ⚙️ Getting Started

### Prerequisites
- Java 17+
- Node.js 18+ (for Angular and n8n)
- Docker & Docker Compose
- MySQL 8.x
- MongoDB 6.x

### 1. Clone the Repository

```bash
git clone https://github.com/your-org/saint-ai.git
cd saint-ai
```

### 2. Start Infrastructure (Docker)

```bash
docker-compose up -d
# Starts: MySQL, MongoDB, n8n, Redis (optional)
```

### 3. Configure Backend

```bash
cd backend
cp .env.example .env
# Edit .env with your credentials (see Environment Variables below)
./mvnw spring-boot:run
```

### 4. Configure Frontend

```bash
cd frontend
npm install
ng serve
# Dashboard available at http://localhost:4200
```

### 5. Access n8n

```
http://localhost:5678
# Default credentials: admin / changeme
```

---

## 🔐 Environment Variables

```env
# Database
MYSQL_HOST=localhost
MYSQL_PORT=3306
MYSQL_DB=saint_ai
MYSQL_USER=root
MYSQL_PASSWORD=yourpassword

MONGO_URI=mongodb://localhost:27017/saint_ai_logs

# JWT
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRY_MS=86400000

# AI Providers
OPENAI_API_KEY=sk-...
GEMINI_API_KEY=AIza...
ANTHROPIC_API_KEY=sk-ant-...

# Cloud Storage
GCS_PROJECT_ID=your-gcp-project
GCS_BUCKET=saint-ai-files
AWS_ACCESS_KEY=...
AWS_SECRET_KEY=...
AWS_BUCKET=saint-ai-s3

# OneDrive
ONEDRIVE_CLIENT_ID=...
ONEDRIVE_CLIENT_SECRET=...

# Billing
STRIPE_SECRET_KEY=sk_live_...
STRIPE_WEBHOOK_SECRET=whsec_...

# n8n
N8N_WEBHOOK_URL=http://localhost:5678/webhook
```

---

## 📡 API Overview

### Auth
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login, receive JWT |
| POST | `/api/auth/refresh` | Refresh access token |

### AI Execution
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/ai/text` | Generate text (multi-provider) |
| POST | `/api/ai/image` | Generate image |
| GET | `/api/ai/logs` | Retrieve AI call history |
| GET | `/api/ai/costs` | Cost breakdown by model |

### Documents
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/documents/generate` | Trigger document generation |
| GET | `/api/documents` | List user documents |
| GET | `/api/documents/{id}/download` | Signed download URL |

### Workflows
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/workflows/trigger` | Trigger n8n workflow |
| GET | `/api/workflows/logs` | Workflow execution logs |

### Admin
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/admin/users` | List all users |
| GET | `/api/admin/metrics` | Platform usage metrics |
| GET | `/api/admin/audit` | Full audit trail |

Full API documentation available via Swagger UI at `/swagger-ui.html` when running locally.

---

## 👥 Human-in-the-Loop Governance

SAINT-AI implements a **Human Approval Gate** for sensitive AI outputs:

```
AI Output Generated
       │
       ▼
 Risk Assessment
  (automated)
       │
  ┌────▼────┐
  │ Low Risk│──► Auto-delivered to user
  └─────────┘
       │
  ┌────▼────┐
  │High Risk│──► Queued for Engineer Review
  └─────────┘
       │
  Engineer Reviews → Approve / Modify / Reject
       │
       ▼
  Output delivered + Audit log updated
```

This ensures compliance for regulated industries (healthcare, finance, government).

---

## 📈 Roadmap to 2026

| Quarter | Milestone |
|---|---|
| **Q1 2025** | Phases 1–3: Backend, AI integration, n8n workflows |
| **Q2 2025** | Phases 4–5: Dashboard, billing |
| **Q3 2025** | Phases 6–7: Multi-cloud, HITL governance |
| **Q4 2025** | Phase 8: Beta users (50–100), production deploy |
| **Q1 2026** | Enterprise licensing, white-label offering |
| **Q2 2026** | IoT/hardware integration, SAINT-AI Marketplace |

---

## 🎯 Strategic Positioning

SAINT-AI targets:

- 🎓 **Universities** — Research automation, document generation
- 🚀 **Startups** — AI-powered operations without AI team overhead
- 🏢 **SMEs** — Workflow automation and document processing
- 🔧 **IT Automation Teams** — Infrastructure + AI orchestration
- 🔬 **Research Departments** — Structured AI experimentation

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add: your feature description'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for code standards and review process.

---

## 📄 License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

---

## 🧠 Strategic Reminder

> Keep scope disciplined. Build the core document + workflow engine first.
> Validate with 50–100 real users. Measure cost per AI request.
> Optimize infrastructure before scaling.

**SAINT-AI is not built to impress. It is built to execute.**

---

*Built with ☕ Java, 🅰 Angular, and 🤖 Multi-Model AI*
*SAINT-AI Research Project — Enterprise AI Workflow Infrastructure*
