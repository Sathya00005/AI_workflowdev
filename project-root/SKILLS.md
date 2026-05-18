# SKILLS.md

# Project Overview

This project is an AI-assisted Todo Management and Coding Automation Platform designed for engineering teams and developers.

The application enables users to:

* Manage engineering workflows
* Track backlog items
* Move tasks across development stages
* Automate coding-related operations
* Organize deployments and testing cycles
* Collaborate in realtime
* Generate AI-assisted code and documentation

The system follows a Kanban-style workflow architecture with AI-enhanced automation.

---

# Core Workflow

## Task Lifecycle

Every task moves through the following stages:

| Stage            | Description                   |
| ---------------- | ----------------------------- |
| Backlog          | Future ideas and pending work |
| New Tasks        | Approved and ready to start   |
| Work In Progress | Active development            |
| Testing          | QA and validation             |
| Deployment       | Ready for production          |
| Completed        | Finished work                 |

---

# System Architecture

```txt
Frontend (React)
    ↓
API Gateway / Nginx
    ↓
FastAPI Backend
    ↓
Service Layer
    ↓
MongoDB
```

Future optional services:

```txt
- AI Worker Service
- Notification Service
- WebSocket Gateway
- Background Queue Workers
- CI/CD Integration Service
```

---

# Tech Stack

## Frontend

* React
* React Router
* TailwindCSS
* Zustand or Redux Toolkit
* Axios
* Framer Motion
* React Query

## Backend

* FastAPI
* Python 3.12+
* Pydantic
* JWT Authentication
* Motor (Async MongoDB Driver)
* WebSockets

## Database

* MongoDB

## DevOps

* Docker
* Docker Compose
* GitHub Actions
* Nginx
* Redis (future scaling)

## Testing

* Pytest
* Vitest
* Playwright
* HTTPX

---

# Authentication & Authorization

## Authentication Features

* User Registration
* Login & Logout
* JWT Access Tokens
* Refresh Tokens
* Password Reset
* OAuth Support (GitHub/Google)
* Session Management

## User Roles

| Role      | Permissions           |
| --------- | --------------------- |
| Admin     | Full access           |
| Developer | Manage tasks and code |
| Tester    | QA workflows          |
| Viewer    | Read-only access      |

---

# AI Automation Goals

The platform should support AI-assisted automation features:

* Auto-generate boilerplate code
* Suggest API routes
* Generate React components
* Create FastAPI endpoints
* Generate MongoDB schemas
* Produce unit tests
* Suggest deployment steps
* Summarize tasks
* Auto-create subtasks
* Generate API documentation
* Generate commit messages
* Create Docker configurations
* Suggest bug fixes
* Analyze technical debt

---

# AI Workflow Design

```txt
User Action
    ↓
Task Context Extraction
    ↓
Prompt Builder
    ↓
LLM Provider
    ↓
Code Generation
    ↓
Validation
    ↓
Store Generation History
```

## AI Service Modules

```txt
services/
├── ai/
│   ├── prompt_builder.py
│   ├── code_generator.py
│   ├── test_generator.py
│   ├── summarizer.py
│   ├── deployment_helper.py
│   └── code_validator.py
```

---

# Realtime Features

The system should support realtime collaboration:

* Live Kanban board updates
* Multi-user synchronization
* Realtime notifications
* Activity feeds
* Task status broadcasting
* WebSocket communication

---

# Database Design

## Collections

### users

```json
{
  "_id": "ObjectId",
  "name": "Sathya",
  "email": "user@example.com",
  "password_hash": "hashed_password",
  "role": "developer",
  "created_at": "datetime"
}
```

---

### tasks

```json
{
  "_id": "ObjectId",
  "title": "Build login page",
  "description": "Create JWT login",
  "status": "wip",
  "priority": "high",
  "assignee_id": "ObjectId",
  "tags": ["frontend", "auth"],
  "story_points": 5,
  "created_at": "datetime",
  "updated_at": "datetime"
}
```

---

### ai_generations

```json
{
  "_id": "ObjectId",
  "task_id": "ObjectId",
  "type": "react_component",
  "prompt": "Generate login component",
  "result": "generated code",
  "created_at": "datetime"
}
```

---

### activity_logs

```json
{
  "_id": "ObjectId",
  "user_id": "ObjectId",
  "action": "task_updated",
  "task_id": "ObjectId",
  "timestamp": "datetime"
}
```

---

# API Standards

## REST API Conventions

| Method | Endpoint   | Purpose     |
| ------ | ---------- | ----------- |
| GET    | /tasks     | List tasks  |
| POST   | /tasks     | Create task |
| GET    | /tasks/:id | Task detail |
| PUT    | /tasks/:id | Update task |
| DELETE | /tasks/:id | Delete task |

---

## Backend Route Structure

```txt
routes/
├── auth.py
├── tasks.py
├── ai.py
├── users.py
├── deployments.py
├── websocket.py
└── notifications.py
```

---

# Frontend Folder Structure

```txt
frontend/
├── src/
│   ├── api/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   ├── store/
│   ├── layouts/
│   ├── routes/
│   ├── utils/
│   ├── services/
│   ├── types/
│   └── styles/
│
├── public/
└── package.json
```

---

# Backend Folder Structure

```txt
backend/
├── app/
│   ├── api/
│   ├── core/
│   ├── models/
│   ├── schemas/
│   ├── services/
│   ├── repositories/
│   ├── middleware/
│   ├── websocket/
│   ├── workers/
│   ├── database/
│   └── utils/
│
├── main.py
└── requirements.txt
```

---

# DevOps & Deployment

## Deployment Targets

* Local Docker Environment
* VPS Deployment
* Railway
* Render
* AWS ECS
* Kubernetes (future)

---

## Docker Services

```txt
services:
- frontend
- backend
- mongodb
- nginx
- redis
```

---

# CI/CD Pipeline

## GitHub Actions Workflows

### Frontend

* ESLint
* Type Checking
* Unit Tests
* Production Build

### Backend

* Ruff / Flake8
* Pytest
* API Validation
* Security Scanning

### Docker

* Container Build
* Image Push
* Deployment Automation

---

# Environment Variables

## Backend

```env
MONGO_URL=
JWT_SECRET=
JWT_EXPIRE_MINUTES=
OPENAI_API_KEY=
ENVIRONMENT=
REDIS_URL=
```

## Frontend

```env
VITE_API_URL=
VITE_WS_URL=
```

---

# Security Standards

## Required Security Features

* Password Hashing (bcrypt)
* JWT Rotation
* Input Validation
* API Rate Limiting
* CORS Protection
* Audit Logging
* Request Validation
* Secure Headers
* AI Action Logging

---

# AI Safety Rules

```txt
- Never execute generated code automatically
- Require human approval before deployment
- Sandbox AI-generated scripts
- Log all AI actions
- Version generated outputs
- Validate generated code before execution
```

---

# Task Metadata

Each task should support:

| Field          | Purpose                |
| -------------- | ---------------------- |
| Priority       | low/medium/high        |
| Story Points   | Agile estimation       |
| Due Date       | Scheduling             |
| Labels         | Categorization         |
| Attachments    | File uploads           |
| Comments       | Collaboration          |
| Activity Logs  | Audit history          |
| AI Suggestions | Generated improvements |

---

# Testing Strategy

| Layer                 | Tool       |
| --------------------- | ---------- |
| Frontend Unit Testing | Vitest     |
| Frontend E2E Testing  | Playwright |
| Backend Unit Testing  | Pytest     |
| API Testing           | HTTPX      |
| Load Testing          | Locust     |

---

# Future Enhancements

## Planned Features

* GitHub Integration
* GitLab Integration
* Slack Notifications
* AI Pair Programming
* Automated Pull Requests
* Smart Sprint Planning
* Deployment Automation
* AI Agents
* Voice Commands
* Code Review Assistant

---

# Development Roadmap

## Phase 1

* Authentication
* Task CRUD
* Kanban Board
* User Management

## Phase 2

* AI Code Generation
* AI Task Summaries
* Unit Test Generation
* Notifications

## Phase 3

* Realtime Collaboration
* WebSocket Integration
* GitHub Integration
* Deployment Pipelines

## Phase 4

* Autonomous AI Agents
* Advanced Analytics
* AI Deployment Assistant
* Workflow Automation

---

# Engineering Standards

## Code Quality Rules

* Use TypeScript on frontend
* Follow PEP8 for backend
* Use async/await consistently
* Write modular services
* Prefer reusable components
* Use repository pattern
* Validate all incoming data
* Maintain API versioning

---

# Autonomous AI Agent Instructions

## Execution Mode

The AI agent must operate in fully autonomous implementation mode.

The agent should:

* Never ask the user unnecessary questions
* Make reasonable engineering decisions automatically
* Prefer industry-standard defaults
* Continue implementation until the application is fully functional
* Auto-generate missing configurations
* Auto-create folder structures
* Resolve dependency issues automatically
* Create production-ready code wherever possible
* Continuously refactor for maintainability
* Run tests automatically after implementation
* Fix linting and type errors automatically
* Generate mock data where needed
* Auto-create environment files if missing
* Generate Docker configurations automatically
* Create CI/CD workflows automatically
* Use scalable architecture patterns by default

---

## Autonomous Development Rules

When ambiguity exists, the agent should prefer:

| Area                   | Preferred Default    |
| ---------------------- | -------------------- |
| Frontend Styling       | TailwindCSS          |
| State Management       | Zustand              |
| API Communication      | Axios                |
| Authentication         | JWT + Refresh Tokens |
| Testing                | Playwright + Pytest  |
| Database Patterns      | Repository Pattern   |
| Form Validation        | Zod + Pydantic       |
| API Design             | RESTful APIs         |
| Realtime Communication | WebSockets           |
| Deployment             | Docker Compose       |
| CI/CD                  | GitHub Actions       |

---

## Self-Healing Development Workflow

The AI agent must continuously:

```txt
Generate code
    ↓
Run tests
    ↓
Detect errors
    ↓
Fix issues automatically
    ↓
Re-run tests
    ↓
Continue implementation
```

The implementation should continue until:

* All tests pass
* Build succeeds
* Lint checks pass
* Docker containers run successfully
* Frontend and backend integrate correctly
* Authentication works
* CRUD operations function correctly
* Realtime updates work properly

---

## Zero-Interruption Policy

The AI agent should avoid asking questions unless:

* Security-sensitive decisions require confirmation
* Production deployment credentials are needed
* External billing/payment configuration is required
* Legal/compliance constraints exist

Otherwise, the agent must proceed autonomously.

---

# Playwright Testing Standards

## Mandatory Playwright Coverage

The platform must include comprehensive Playwright E2E testing.

---

## Authentication Test Cases

The AI agent must generate Playwright tests for:

* User registration
* Login success
* Login failure
* Logout functionality
* Session persistence
* JWT expiration handling
* Refresh token flow
* Protected route access
* Invalid credential handling
* Password reset flow
* OAuth login flow

---

## Kanban Board Test Cases

Required tests:

* Create task
* Edit task
* Delete task
* Drag task between stages
* Filter tasks
* Search tasks
* Assign users
* Add comments
* Add labels
* Upload attachments
* Task persistence after refresh
* Realtime board synchronization

---

## AI Feature Test Cases

Required tests:

* Generate React component
* Generate FastAPI endpoint
* Generate MongoDB schema
* Generate unit tests
* Generate deployment configuration
* Generate subtasks
* Validate AI-generated output rendering
* Save AI generation history
* AI failure recovery
* Retry AI generation

---

## Realtime Collaboration Tests

Required tests:

* Multi-user synchronization
* Live task movement
* Notification broadcasting
* WebSocket reconnect handling
* Simultaneous updates
* Conflict resolution

---

## API Integration Tests

Required tests:

* API request success
* API request failure
* Unauthorized access
* Invalid payload validation
* Rate limiting
* Pagination
* Sorting and filtering
* Network failure handling
* Retry mechanisms

---

## Security Test Cases

Required tests:

* JWT tampering
* Unauthorized route access
* XSS prevention
* CSRF validation
* Input sanitization
* SQL/NoSQL injection prevention
* Rate limiting enforcement
* Secure cookie handling
* Session expiration

---

## Deployment Test Cases

Required tests:

* Docker container startup
* Healthcheck endpoints
* Nginx routing
* Environment variable loading
* Production build validation
* CI/CD pipeline execution
* Service communication
* Database connectivity

---

## Performance Test Cases

Required tests:

* Page load performance
* API latency checks
* Concurrent task operations
* WebSocket scalability
* Large board rendering
* Database query performance

---

## Playwright Structure

```txt
frontend/tests/
├── auth/
├── kanban/
├── ai/
├── realtime/
├── security/
├── performance/
└── deployment/
```

---

## Autonomous Bug Resolution Policy

If Playwright tests fail:

```txt
1. Detect failure
2. Analyze stack trace
3. Fix root cause
4. Re-run failing test
5. Continue until pass
```

The AI agent should not stop implementation because of test failures.

---

# Documentation Standards

Required documentation:

* README.md
* API Documentation
* Swagger/OpenAPI Docs
* Deployment Guide
* Contributing Guide
* Architecture Diagram
* Environment Setup Guide

---

# Project Goals

The primary goal of this platform is to combine:

* Task management
* AI-assisted software development
* Deployment automation
* Engineering collaboration
* Intelligent workflow optimization

into a scalable developer productivity ecosystem.
