# Event Model v0.1

Born-Agentic Organization should be event-driven.

Representative events:

```text
OrganizationCreated
OrganizationObjectiveChanged
RoleCreated
RoleActivated
RoleSuspended
TaskCreated
TaskCompleted
TaskFailed
ToolAttached
PolicyChanged
CapabilityGapDetected
CapabilityResolutionSelected
HiringRequested
CandidateAdded
CandidateScreened
InterviewCompleted
HiringApproved
AssignmentCreated
AssignmentEnded
HumanResigned
ModelChanged
```

Each event should include:

```yaml
event_id: EVT-00001
organization_id: ORG-00001
role_id: ROLE-00017
type: CapabilityGapDetected
occurred_at: 2026-09-11T00:00:00Z
actor:
  type: agent
  id: AGENT-00473
payload: {}
trace_id: TRACE-123
```

Events support:
- auditability;
- durable execution;
- replay;
- cross-Role coordination;
- memory construction;
- capability evaluation.

Every event must be attributable to an actor (agent or human) and scoped to a Role. This is the mechanism behind the governance rule that autonomous actions remain attributable.

---

## Related documents

- [README.md](../README.md) — project overview and terminology
- [architecture/OVERVIEW.md](../architecture/OVERVIEW.md) — Task & Event Service and the runtime loop
- [architecture/DIAGRAMS.md](../architecture/DIAGRAMS.md) — runtime loop diagram
- [spec/ROLE_OBJECT.md](ROLE_OBJECT.md) — Role state that events mutate
- [spec/ROLE_LIFECYCLE.md](ROLE_LIFECYCLE.md) — lifecycle transitions as events
- [spec/CAPABILITY_MODEL.md](CAPABILITY_MODEL.md) — capability events
- [GOVERNANCE.md](../GOVERNANCE.md) — audit trail requirements
