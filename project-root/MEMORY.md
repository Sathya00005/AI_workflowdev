## 1. Project Context & Purpose
* **System Name:** AI-Assisted Todo Management and Coding Automation Platform
* **Target Audience:** Engineering teams, developers, and QA personnel.
* **Core Goal:** Combine task management (Kanban workflow), AI-driven development automation, and deployment pipelines into a single, scalable ecosystem.

---

## 2. Architecture & Tech Stack

### High-Level Topology
```
Frontend (React)  ──>  API Gateway / Nginx  ──>  FastAPI Backend  ──>  Service Layer  ──>  MongoDB
```

### Stack Components
* **Frontend:** React, React Router, TailwindCSS, Zustand (or Redux Toolkit), Axios, Framer Motion, React Query.
* **Backend:** FastAPI (Python 3.12+), Pydantic, Motor (Async MongoDB), WebSockets.
* **Database:** MongoDB (Collections: `users`, `tasks`, `ai_generations`, `activity_logs`).
* **DevOps & Deployment:** Docker, Docker Compose, GitHub Actions, Nginx, Redis (future scaling).
* **Testing Suite:** Vitest, Playwright (E2E), Pytest, HTTPX, Locust.

---

## 3. Core System Logic & Workflows

### Task Lifecycle Stages
`Backlog` ──> `New Tasks` ──> `Work In Progress` ──> `Testing` ──> `Deployment` ──> `Completed`

### AI Service Subsystem (`services/ai/`)
1.  **Trigger:** User action extracts task metadata and code context.
2.  **Processing:** `prompt_builder.py` compiles the LLM prompt.
3.  **Generation:** `code_generator.py` or domain-specific modules run.
4.  **Guardrails:** `code_validator.py` evaluates outputs before storage.
5.  **Retention:** Writes transaction to `ai_generations` database collection.

### Core Safety Rules
* **No Auto-Execution:** Generated code must never be run or deployed automatically.
* **Human-in-the-loop:** Explicit developer approval is required before merging or deploying AI suggestions.
* **Isolation:** Sandbox all generated scripts; maintain strict version control logs.

---

## 4. Current Phase & Implementation Focus
The development plan is divided into four distinct phases:

* **Phase 1 (Active Focus):** Core Authentication (JWT/Refresh/OAuth), Task CRUD operations, Kanban Board mechanics, and User Management structures.
* **Phase 2:** AI Code/Test/Summary Generation services and notification integrations.
* **Phase 3:** Realtime WebSockets, GitHub sync, and initial deployment pipelines.
* **Phase 4:** Autonomous agents, advanced metrics, and end-to-end workflow automation.

---

## 5. Autonomous Implementation Instructions
The agent operates under a **Zero-Interruption, Fully Autonomous Mode** governed by a self-healing engineering loop:

```
Generate Code  ──>  Run Tests  ──>  Detect Errors  ──>  Fix Issues  ──>  Re-run Tests
```

### Defaults & Conventions
* **Frontend:** TypeScript, TailwindCSS, Zustand state, Axios.
* **Backend:** Async/Await syntax, PEP8 compliance, Pydantic validations, Repository Pattern.
* **Testing:** Strict mandatory Playwright E2E coverage across 7 key vectors (Auth, Kanban, AI features, Realtime, API, Security, Deployment).

### Escalation Thresholds
The agent must proceed autonomously using industry-standard defaults on all design ambiguity. It is authorized to halt or request human interaction *only* if it encounters:
1.  Security-sensitive permission definitions requiring explicit validation.
2.  Production deployment credentials or environment secrets.
3.  External billing, payment gateway, or third-party license configurations.
4.  Legal and compliance constraints.