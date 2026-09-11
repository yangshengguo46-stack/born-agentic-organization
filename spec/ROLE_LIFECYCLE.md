# Role Lifecycle v0.1

```text
Draft
  ↓
Provisioning
  ↓
Active
  ├── Working
  ├── Blocked
  ├── NeedsCapability
  │      ↓
  │   CapabilityResolution
  │      ├── Build
  │      ├── Buy
  │      ├── Automate
  │      ├── Outsource
  │      └── HireHuman
  │              ↓
  │         HumanAssigned
  │              ↓
  │           Working
  │
  ├── HumanAssignmentEnded
  │      ↓
  │   Working / NeedsCapability
  │
  └── Suspended
         ↓
      Archived
```

A Human leaving does **not** terminate the Role.

A model replacement does **not** terminate the Role.

Role termination is an explicit organizational action.

---

## Related documents

- [README.md](../README.md) — project overview and core principles
- [architecture/DIAGRAMS.md](../architecture/DIAGRAMS.md) — the same lifecycle as a rendered state diagram
- [spec/ROLE_OBJECT.md](ROLE_OBJECT.md) — the `status` field this lifecycle describes
- [spec/CAPABILITY_MODEL.md](CAPABILITY_MODEL.md) — what triggers `NeedsCapability`
- [spec/ASSIGNMENT_OBJECT.md](ASSIGNMENT_OBJECT.md) — what `HumanAssignmentEnded` ends
- [spec/EVENT_MODEL.md](EVENT_MODEL.md) — lifecycle transitions as events
- [ROADMAP.md](../ROADMAP.md) — Phase 1 implements these states
