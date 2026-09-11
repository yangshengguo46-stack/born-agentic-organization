# Architecture Diagrams

All diagrams are Mermaid and render directly on GitHub. Each diagram is followed by a text description, so the structure is readable without rendering and extractable by machines.

Related: [architecture/OVERVIEW.md](OVERVIEW.md) · [spec/ROLE_OBJECT.md](../spec/ROLE_OBJECT.md) · [README.md](../README.md)

---

## 1. Organization → Boss Agent → Roles

```mermaid
flowchart TD
    O[Organization] --> B[Boss / Organization Agent]
    O --> OM[Organization Memory]
    O --> OP[Objectives and Policies]

    B --> R1[Sales Role]
    B --> R2[Marketing Role]
    B --> R3[People Role]

    R1 --> A1[Resident Role Agent]
    R1 --> H1[Human Assignment]
    R1 --> T1[Tools]
    R1 --> M1[Role Memory]

    R2 --> A2[Resident Role Agent]
    R3 --> PA[People Agent]
```

**What this shows.** The Organization is the top-level container holding objectives, policies and global memory. The Boss / Organization Agent is an orchestrator, not a super-agent that performs all work: it decomposes objectives, creates Roles and coordinates across them. Every Role is a first-class node with its own resident Role Agent, Human Assignments, tools and memory. The People Role is an ordinary Role that hosts the People Agent — hiring capability is itself organized as a Role.

---

## 2. Role → Agent / Human / Tools / Memory

```mermaid
flowchart TD
    R[Role<br/>persistent organizational unit]

    R --> RA[Resident Role Agent]
    R --> HA[Human Assignment]
    R --> T[Tools and Resources]
    R --> MEM[Role Memory and State]
    R --> DH[Decision History]
    R --> POL[Authority and Policies]

    RA --> MD1[Model A]
    RA --> MD2[Model B]
    HA --> HU1[Human A]
    HA --> HU2[Human B]

    MD1 -.->|replaceable| R
    MD2 -.->|replaceable| R
    HU1 -.->|replaceable| R
    HU2 -.->|replaceable| R
```

**What this shows.** The Role sits at the center and owns its own memory, state, decision history, authority and policies. Everything that *executes* is attached: the resident Role Agent (which itself binds to one or more Models), Human Assignments, and tools. The dashed edges mark the core invariant — Models, Agent instances and Humans are all replaceable, and replacing any of them does not terminate the Role or erase its memory.

---

## 3. Capability Gap → Resolution Paths

```mermaid
flowchart TD
    REQ[Required Capabilities] --> GAP
    AG[Available Agent Capabilities] --> GAP
    HU[Available Human Capabilities] --> GAP
    TV[Available Tool and Vendor Capabilities] --> GAP

    GAP{{Capability Gap}}

    GAP --> B[Build<br/>improve prompt, policy, workflow]
    GAP --> BU[Buy<br/>attach tool or service]
    GAP --> AU[Automate]
    GAP --> DE[Delegate<br/>another Agent or Role]
    GAP --> OU[Outsource<br/>vendor or freelancer]
    GAP --> EX[Assign Existing Human]
    GAP --> HI[Hire New Human]
```

**What this shows.** A Capability Gap is computed, not assumed — required capabilities minus what Agents, Humans, tools and vendors can currently supply. A gap does not lead directly to hiring. It is routed through the cheapest and most reliable resolution paths first; hiring a Human is the last branch, taken only when the others are insufficient or uneconomic. This is what makes Capability Allocation different from headcount planning.

---

## 4. Machine-Initiated Hiring

```mermaid
flowchart LR
    R[Role Agent] --> G[Capability Gap detected]
    G --> D{Resolution}
    D -->|Build| B[Improve Agent]
    D -->|Buy| T[Attach Tool or Service]
    D -->|Delegate| A[Other Agent or Role]
    D -->|Outsource| V[Vendor]
    D -->|Hire| H[Hiring Request]
    H --> P[People Agent]
    P --> C[Candidates]
    C --> I[Role-specific Interview<br/>Role Agent participates]
    I --> X[Human Approval]
    X --> AS[Human Assignment]
    AS --> R
```

**What this shows.** The inversion at the center of the model: hiring can be *initiated by the Role*, not only by a human manager. The Role Agent detects a persistent gap, attempts non-human resolutions first, and only then emits a Hiring Request expressed in capabilities rather than a job title. The People Agent sources candidates; the Role Agent participates in assessment because it owns the real work context. A Human approves the decision, and the Human is then attached back to the same Role through an Assignment — closing the loop.

---

## 5. Human → Assignment → Role

```mermaid
flowchart LR
    H1[Human A] --> A1[ASSIGN-02831<br/>primary]
    H2[Human B] --> A2[ASSIGN-02832<br/>fractional]
    A1 --> R[ROLE-00017<br/>North America BD]
    A2 --> R
    R --> RA[Resident Role Agent]
    RA --> R
    A1 -.->|ended, role persists| R
```

**What this shows.** A Human never *is* the Role — a Human is connected to a Role through an Assignment object. This supports one Role with multiple Humans, one Human across multiple Roles, temporary and fractional assignments, and running a Role with no Human at all. The dashed edge is the key invariant: ending an Assignment (resignation, rotation, contract end) leaves the Role, its memory and its resident Role Agent intact.

See [spec/ASSIGNMENT_OBJECT.md](../spec/ASSIGNMENT_OBJECT.md).

---

## 6. Role Lifecycle

```mermaid
stateDiagram-v2
    [*] --> Draft
    Draft --> Provisioning
    Provisioning --> Active
    Active --> Working
    Working --> Blocked
    Blocked --> Working
    Working --> NeedsCapability: Capability Gap detected
    NeedsCapability --> Working: build / buy / automate / outsource
    NeedsCapability --> HiringRequested: human required
    HiringRequested --> HumanAssigned: hiring approved
    HumanAssigned --> Working
    Working --> NeedsCapability: Human Assignment ended
    Working --> Suspended
    Suspended --> Archived
    Archived --> [*]
```

**What this shows.** A Role is created (Draft → Provisioning → Active) and then operates in Working state. A detected Capability Gap moves it to NeedsCapability, which either resolves back to Working through non-human means, or escalates to HiringRequested. A Human leaving returns the Role to Working or NeedsCapability — never to termination. Termination is an explicit organizational action (Suspended → Archived), not a side effect of a Human leaving or a Model being swapped.

See [spec/ROLE_LIFECYCLE.md](../spec/ROLE_LIFECYCLE.md).

---

## 7. Runtime Loop

```mermaid
flowchart TD
    E[Observe Event] --> S[Update State]
    S --> P[Plan]
    P --> A{Authority Check}
    A -->|Allowed| X[Execute]
    A -->|Approval needed| H[Human Approval]
    H --> X
    X --> V[Evaluate]
    V --> M[Write Memory / Decision Log]
    M --> C{Next}
    C -->|Continue| P
    C -->|Retry| X
    C -->|Escalate| H
    C -->|Capability Gap| G[Capability Engine]
    G --> P
```

**What this shows.** The operating cycle of a Role: observe an event, update state, plan, check authority *before* acting, execute, evaluate the outcome, and write both memory and a decision record. Authority is checked in the loop rather than assumed from model capability — that is how Role authority stays separable from what a Model happens to be able to do. Outcomes route back to planning, retry, human escalation, or into the Capability Engine when a gap is the real blocker.

See [architecture/OVERVIEW.md](OVERVIEW.md) and [spec/EVENT_MODEL.md](../spec/EVENT_MODEL.md).
