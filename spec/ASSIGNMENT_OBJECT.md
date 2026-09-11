# Assignment Object Specification v0.1

An Assignment connects a Human to a Role without making the Human the identity of the Role.

```yaml
assignment_id: ASSIGN-02831
organization_id: ORG-00001
role_id: ROLE-00017
human_id: EMP-00891

type: primary
status: active

started_at: 2026-09-11T00:00:00Z
ended_at: null

authority_overrides:
  customer_calls: true
  pricing_approval: true
  contract_signing: false

observed_capabilities:
  negotiation: 88
  relationship: 91
  product_knowledge: 64
```

## Invariants

- Ending an Assignment does not delete the Role.
- Ending an Assignment does not delete Role Memory.
- One Human may have multiple Assignments.
- One Role may have multiple Human Assignments.
- `authority_overrides` may widen or narrow a Human's authority inside the Role, but may not exceed the Role's own authority.
- Assignment is the only supported way to connect a Human to a Role.

---

## Related documents

- [README.md](../README.md) — project overview and terminology
- [docs/CONCEPT.md](../docs/CONCEPT.md) — Human Assignment section
- [architecture/DIAGRAMS.md](../architecture/DIAGRAMS.md) — Human → Assignment → Role diagram
- [spec/ROLE_OBJECT.md](ROLE_OBJECT.md) — the Role this Assignment attaches to
- [spec/CAPABILITY_MODEL.md](CAPABILITY_MODEL.md) — where `observed_capabilities` feeds back
- [spec/EVENT_MODEL.md](EVENT_MODEL.md) — `AssignmentCreated` / `AssignmentEnded`
- [GOVERNANCE.md](../GOVERNANCE.md) — authority and privacy boundaries
