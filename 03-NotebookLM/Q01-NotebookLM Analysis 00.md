### Lecture Section: Prototyping vs. Engineering — The Anatomy of "After the Vibe"

#### 1. Core Thesis: Working Code vs. Dependable Systems

- **The Demo Illusion**: Generating a working software prototype answers the baseline question: _"Does it work on the happy path?"_ However, production systems force organizations to answer: _"Can we depend on it under adversarial or degraded conditions?"_
- **The Functional Shift**: Software engineering begins where code generation ends. When moving past the prototype, the core activity shifts from writing code to proving correctness, refactoring architecture, hardening security, managing operational runtime, and establishing organizational accountability.

---

#### 2. Structural Failure Modes of Unvetted Vibe Code

- **Architectural Monoliths & Coupling**: Conversational prompting naturally solves immediate feature requirements without planning for long-term modularity. This produces single-file monolithic scripts, redundant helper utilities, and tight cross-module coupling that resist maintainability and enterprise scale.
- **Comprehension Debt**: Software that executes correctly but whose internal logic and design decisions are understood by no human engineer. This poses severe operational risks during incidents (such as a 2:00 AM production outage), forcing teams to reverse-engineer undocumented, conversationally generated code under time pressure.
- **Edge-Case Blindness & Incomplete Error Handling**: Prototypes optimize for user-flow demonstrations rather than operational resilience. Real-world failure points—such as duplicate transactions, upstream API timeouts, or unhandled null states—are frequently omitted unless explicitly extracted by deterministic test suites.
- **Security & Authorization Bypasses**: Vibe code frequently passes functional smoke tests while silently violating enterprise security policies, ignoring pre-existing role-based access controls (RBAC), leaving injection vulnerabilities exposed, or introducing unvetted third-party package dependencies.
- **The "Orphaned Application" Problem**: Citizen developers or internal teams build ad-hoc utilities that become embedded in company workflows. When the original creator leaves the organization, the company inherits unmanaged, ungoverned software with unknown data access and no assigned maintainer.

---

#### 3. Quantitative Failure Metrics & Governance Signals

|Metric / Indicator|Observed Value / Tracking Standard|Context & Attribution|
|:--|:--|:--|
|**Known Vulnerability Injection Rate**|**~45%** of AI-generated code samples introduced known vulnerabilities.|_Veracode (2026 report)_; directional vendor metric highlighting common security oversights in raw generation.|
|**AI-Attributed Common Vulnerabilities and Exposures (CVEs)**|Rose from **6 (Jan 2026)** to **35 (Mar 2026)**.|_Georgia Tech Tracking_; systematic measurement of publicly documented CVEs directly traced to AI coding tools.|
|**Named Human Accountability Rate**|Percentage of merged production code tied to a named, accountable human owner.|Key governance KPI used by security leadership; dropping rates indicate compounding, unmonitored debt.|
|**Defect Escape Rate & Review Latency**|Systematic operational metrics measuring bugs reaching production and the time required to review AI output.|Used to evaluate whether acceleration at generation is being negated by remediation bottlenecks.|
|**Formal Audit Adherence**|Audit-trail and environment separation compliance.|Standards mandated by **ISO 42001** (AI Management Systems) and **Cyber Essentials Plus**.|

---

#### 4. The Engineering Maturation Pipeline

```
[ Conversational Prompting / Vibe Code ]
                   │
                   ▼
  1. Gating & Triage (Risk Assessment) ────────► Disposable / Low-Risk: "Keep It Small"
                   │ (Production-Bound)
                   ▼
  2. Verification & Testing
     ├── Deterministic Test Suites (Unit, Integration, Property-Based)
     └── Security Audits (SAST, DAST, Dependency Triage)
                   │
                   ▼
  3. Architectural Refactoring
     ├── Decomposition into Domain-Driven Interfaces
     └── Establishing Prompt-to-PR Lineage
                   │
                   ▼
  4. Operational Deployment & Ownership
     ├── Managed Runtime & Infrastructure (e.g., Google Cloud Run, Heroku Postgres)
     ├── Named Human Accountability
     └── Closed-Loop Telemetry (Agent-Assisted Log/Metric Diagnostics)
```

1. **Risk Gating**: CTOs route projects into separate lanes—allowing fast iteration for low-risk, internal, disposable tools, while strictly gating systems handling regulated data or core infrastructure.
2. **Deterministic Hardening**: Teams surround generated code with unit, integration, and property-based tests to uncover latent logic flaws before merging. Security workflows deploy automated Static (SAST) and Dynamic (DAST) testing alongside dependency reviews.
3. **Domain Alignment & Lineage**: Senior engineers break monolithic outputs into clean domain boundaries. Prompt chains and provenance records are committed alongside Pull Requests to maintain architectural transparency.
4. **Managed Operations & Closed Loops**: Deployment shifts to managed containers and cloud platforms. Operational logging and telemetry provide closed-loop feedback, allowing diagnostic agents to assist engineers in patching runtime issues without removing human judgment.

---

#### 5. Long-Term Workforce Implications

- **The 2028 Maintenance Deficit**: Relying on AI generation while cutting junior developer recruitment threatens the future engineering pipeline. Without junior developers mastering foundational debugging, system architecture, and system maintenance today, organizations risk lacking the senior talent required to remediate and maintain accumulated technical debt in future years.

---

💡 We could also build a slide-by-slide presenter outline or draft an interactive demonstration script showing a simulated code refactoring from "vibe prototype" to production-hardened module.