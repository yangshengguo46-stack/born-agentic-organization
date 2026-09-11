# Concept

## Problem

Enterprise AI is usually deployed into legacy organizations.

```text
Existing organization
        ↓
New AI system
        ↓
Training
        ↓
Employee adoption
        ↓
Process change
        ↓
Value
```

The value chain depends on people voluntarily changing established behavior.

Born-Agentic Organization proposes a different starting point.

## Core Abstraction

The core abstraction is **Role**.

```text
Role
├── Identity
├── Mission
├── Objectives
├── KPIs
├── Capabilities
├── Authority
├── Policies
├── Memory
├── State
├── Decision History
├── Tools
├── Resident Agent
└── Human Assignments
```

The Role is not the same as an Agent. The Agent is an executor attached to the Role.

The model can change without deleting the Role. A Human can leave without deleting the Role.

## Role-first vs Human-first

### Human-first

```text
Hire person
   ↓
Create responsibility around person
   ↓
Train person
   ↓
Person accumulates knowledge
   ↓
Person leaves
   ↓
Organization loses part of the knowledge
```

### Role-first

```text
Create Role
   ↓
Attach Agent Runtime
   ↓
Role starts working
   ↓
Role accumulates memory/state
   ↓
Capability gap detected
   ↓
Human added when needed
   ↓
Human leaves
   ↓
Role continues
```

## Capability Gap

A Role should continually compare:

```text
Required Capabilities
-
Available Agent Capabilities
-
Available Human Capabilities
-
Available Tool / Vendor Capabilities
=
Capability Gap
```

For each gap, the organization chooses:

```text
Build
Buy
Automate
Delegate to another Agent
Outsource
Hire Human
```

Hiring becomes one capability acquisition mechanism among several.

## Machine-Initiated Hiring

A Role can produce a Hiring Request when:
1. the gap materially affects objectives;
2. the gap cannot be reliably closed with existing software or Agents;
3. acquiring a Human is economically justified;
4. the role has authority to request headcount or receives approval.

## People Agent

People Agent is not simply an "AI recruiter." It is an organizational capability service.

Responsibilities may include:
- converting Capability Gap into candidate profile
- sourcing candidates
- outreach
- screening
- scheduling
- maintaining candidate state
- supporting structured interviews
- assignment administration

The Role Agent can participate in functional assessment because it owns the actual work context.

## Human Assignment

Use an Assignment object:

```text
Human
  ↓
Assignment
  ↓
Role
```

This supports one Role → multiple Humans, one Human → multiple Roles, temporary assignments, fractional roles, role handoffs and no-Human operation.

## Active Organizational Memory

Memory should be separated into:
1. Organization Memory
2. Role Memory
3. Entity Memory
4. Working Memory
5. Decision Log

## What this is not

Born-Agentic Organization is not:
- a chatbot per employee
- a multi-agent demo
- an AI wrapper around HR software
- a fixed workflow automation tool
- a claim that Humans are unnecessary
- a claim that Agents should hold legal accountability

It is an attempt to define a **Role-first organizational runtime**.

---

## Related documents

- [README.md](../README.md) — project overview and terminology
- [docs/MANIFESTO.md](MANIFESTO.md) — the nine theses behind this concept
- [docs/WHITEPAPER.zh-CN.md](WHITEPAPER.zh-CN.md) — 中文白皮书草案
- [architecture/OVERVIEW.md](../architecture/OVERVIEW.md) — services and runtime loop
- [architecture/DIAGRAMS.md](../architecture/DIAGRAMS.md) — Capability Gap, Machine-Initiated Hiring and Assignment diagrams
- [spec/ROLE_OBJECT.md](../spec/ROLE_OBJECT.md) — Role object fields
- [spec/CAPABILITY_MODEL.md](../spec/CAPABILITY_MODEL.md) — gap scoring and resolution order
- [spec/ASSIGNMENT_OBJECT.md](../spec/ASSIGNMENT_OBJECT.md) — Assignment object
- [spec/EVENT_MODEL.md](../spec/EVENT_MODEL.md) — event model
