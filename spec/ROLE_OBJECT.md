# Role Object Specification v0.1

```yaml
role_id: ROLE-00017
organization_id: ORG-00001

name: North America BD
status: active

mission: >
  Build and convert enterprise pipeline in North America.

objectives:
  - id: OBJ-1
    name: Qualified pipeline
    target: 500000
    unit: USD
    period: quarter

kpis:
  - name: qualified_leads
    target: 100
    period: month

capabilities_required:
  research: 90
  lead_generation: 90
  writing: 80
  negotiation: 85
  relationship: 80
  offline_presence: 70

authority:
  email_send: autonomous
  crm_update: autonomous
  discount_under_10_percent: autonomous
  discount_over_10_percent: human_approval
  contract_signing: forbidden

policies:
  - pricing_policy_v3
  - privacy_policy_v2

state:
  active_leads: 137
  negotiations: 9
  meetings_pending: 8

resident_agent:
  agent_id: AGENT-00473
  runtime_profile: sales_bd_v1

human_assignments:
  - assignment_id: ASSIGN-02831
    human_id: EMP-00891
    type: primary

tools:
  - crm
  - email
  - web_research

memory_namespace: role/ROLE-00017
created_at: 2026-09-11T00:00:00Z
```

## Invariants

1. Role persists when Human assignment ends.
2. Role persists when resident Agent/model changes.
3. Authority belongs to Role policy, not the model.
4. Memory belongs to Role/Organization scope.
5. Every high-impact action is auditable.

The `human_assignments` list contains Assignment references only. A Human is never stored as an attribute of the Role — see [ASSIGNMENT_OBJECT.md](ASSIGNMENT_OBJECT.md).

---

## Related documents

- [README.md](../README.md) — project overview and terminology
- [docs/CONCEPT.md](../docs/CONCEPT.md) — Role-first vs Human-first
- [architecture/OVERVIEW.md](../architecture/OVERVIEW.md) — Role Service
- [spec/ROLE_LIFECYCLE.md](ROLE_LIFECYCLE.md) — how a Role reaches `status: active`
- [spec/ASSIGNMENT_OBJECT.md](ASSIGNMENT_OBJECT.md) — the `human_assignments` entries
- [spec/CAPABILITY_MODEL.md](CAPABILITY_MODEL.md) — the `capabilities_required` block
- [spec/EVENT_MODEL.md](EVENT_MODEL.md) — events emitted by Role state changes
- [GOVERNANCE.md](../GOVERNANCE.md) — audit and authority boundaries
