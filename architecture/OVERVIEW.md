# Reference Architecture v0.1

## Design Goal

Build an organizational runtime where **Role is the persistent system object** and Agents/Humans are attached resources.

## High-Level Architecture

```text
┌──────────────────────────────────────────────┐
│                 Organization                 │
│ Objectives · Policies · Global Memory        │
└──────────────────────┬───────────────────────┘
                       │
                ┌──────▼──────┐
                │ Boss Agent  │
                │ Orchestrator│
                └──────┬──────┘
                       │
       ┌───────────────┼────────────────┐
       │               │                │
┌──────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐
│ Sales Role  │ │Marketing Role│ │ People Role │
│ ROLE-001    │ │ ROLE-002     │ │ ROLE-003    │
└──────┬──────┘ └──────┬──────┘ └──────┬──────┘
       │               │                │
 ┌─────┼─────┐    ┌────┼────┐      ┌────┼────┐
 │     │     │    │    │    │      │    │    │
Agent Human Tools Agent ...        Agent Human Tools
```

## Logical Services

```text
Role Service
├── Role identity
├── objectives / KPI
├── policies / authority
└── assignments

Agent Runtime
├── planner
├── executor
├── evaluator
├── tool router
└── escalation

Memory Service
├── organization memory
├── role memory
├── entity memory
├── working memory
└── decision log

Task & Event Service
├── durable tasks
├── event stream
├── timers
└── retries

Capability Engine
├── required capability model
├── observed capability model
├── gap analysis
└── build / buy / automate / outsource / hire recommendation

People Service
├── hiring request
├── candidate profile
├── screening
├── interview
└── assignment

Identity & Authority
├── Human identity
├── Agent identity
├── Role identity
├── RBAC
├── ABAC
└── audit
```

## Runtime Loop

```text
Observe
  ↓
Update State
  ↓
Plan
  ↓
Check Authority
  ↓
Execute
  ↓
Evaluate
  ↓
Write Memory / Decision Log
  ↓
Continue / Retry / Escalate / Request Capability
```

## Event-Driven Model

Representative events:

```text
OrganizationCreated
ObjectiveCreated
RoleCreated
RoleActivated
TaskCreated
TaskCompleted
TaskFailed
CustomerReplied
CapabilityGapDetected
HiringRequested
CandidateAdded
InterviewCompleted
AssignmentCreated
AssignmentEnded
HumanResigned
PolicyChanged
```

## Suggested v0.1 Stack

```text
Frontend
- Next.js / React

Desktop shell (optional)
- Tauri

Backend
- Python / FastAPI

Database
- PostgreSQL

Vector search
- pgvector

Durable workflow
- Temporal

Event transport v0.1
- PostgreSQL Outbox

Later
- NATS / Kafka if scale requires it

Authorization
- RBAC + ABAC

Model Layer
- Model Router
  ├── OpenAI
  ├── Anthropic
  ├── Qwen
  └── other providers
```

Critical rule:

```text
Role != Model
Role != Agent instance
Role != Human
```

## MVP

```text
Create Organization
      ↓
Create BD Role
      ↓
Role Agent starts work
      ↓
Memory & State accumulate
      ↓
Capability Gap detected
      ↓
Hiring Request
      ↓
Candidate evaluation
      ↓
Human Assignment
      ↓
Agent-led onboarding
      ↓
Human + Agent continue Role
```

---

## Related documents

- [README.md](../README.md) — project overview and terminology
- [architecture/DIAGRAMS.md](DIAGRAMS.md) — Mermaid diagrams for each structure above
- [docs/CONCEPT.md](../docs/CONCEPT.md) — concept and abstractions
- [spec/ROLE_OBJECT.md](../spec/ROLE_OBJECT.md) — Role object specification
- [spec/ROLE_LIFECYCLE.md](../spec/ROLE_LIFECYCLE.md) — Role lifecycle
- [spec/CAPABILITY_MODEL.md](../spec/CAPABILITY_MODEL.md) — Capability Engine inputs
- [spec/ASSIGNMENT_OBJECT.md](../spec/ASSIGNMENT_OBJECT.md) — Assignment object
- [spec/EVENT_MODEL.md](../spec/EVENT_MODEL.md) — event model
- [ROADMAP.md](../ROADMAP.md) — phases that build these services
