# Capability Model v0.1

## Goal

Represent what a Role needs and what the organization can currently provide.

| Capability | Required | Resident Agent | Human | Other Resources | Gap |
|---|---:|---:|---:|---:|---:|
| Research | 90 | 95 | 20 | 10 | 0 |
| Lead Generation | 90 | 92 | 20 | 10 | 0 |
| Writing | 80 | 95 | 50 | 0 | 0 |
| Negotiation | 85 | 55 | 0 | 0 | 30 |
| Relationship | 80 | 25 | 0 | 0 | 55 |
| Offline Presence | 70 | 0 | 0 | 0 | 70 |

The first version does **not** need mathematically perfect scores. The important thing is to make the gap explicit and testable.

## Resolution Strategy

For a material gap, evaluate:

1. improve prompt / policy / workflow;
2. use a stronger model;
3. attach a tool;
4. delegate to another Role or specialist Agent;
5. buy external service;
6. outsource;
7. assign an existing Human;
8. hire a new Human.

## Hiring Trigger

A Hiring Request may be generated only when:
- the capability gap is persistent;
- it materially affects an objective;
- non-human alternatives are insufficient or uneconomic;
- budget / authority rules permit the request;
- required Human capabilities are explicit.

The request is expressed in capabilities, not in a job title. See [docs/CONCEPT.md](../docs/CONCEPT.md) for the Machine-Initiated Hiring section and [architecture/DIAGRAMS.md](../architecture/DIAGRAMS.md) for the resolution flow.

Scores in the table above are illustrative and are not a specified scale. v0.1 does not mandate a scoring range, a measurement method or a threshold for "persistent".

---

## Related documents

- [README.md](../README.md) — project overview and terminology
- [architecture/OVERVIEW.md](../architecture/OVERVIEW.md) — Capability Engine service
- [architecture/DIAGRAMS.md](../architecture/DIAGRAMS.md) — Capability Gap and resolution diagrams
- [spec/ROLE_OBJECT.md](ROLE_OBJECT.md) — the `capabilities_required` block
- [spec/ASSIGNMENT_OBJECT.md](ASSIGNMENT_OBJECT.md) — the `observed_capabilities` block
- [spec/EVENT_MODEL.md](EVENT_MODEL.md) — `CapabilityGapDetected` and `CapabilityResolutionSelected`
- [ROADMAP.md](../ROADMAP.md) — Phase 3 implements the Capability Engine
