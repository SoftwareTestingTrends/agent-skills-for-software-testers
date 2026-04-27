# 90-Day Onboarding Plan: QA Manager

## Overview

This plan covers the first 90 days for a mid-level QA Manager joining a healthcare product organization. The team currently has 4 developers and 2 manual QA engineers, with fragmented testing practices and no unified QA process. The product is a healthcare platform subject to HIPAA compliance requirements, built on a NextJS / Python (FastAPI) / PostgreSQL stack with GitHub Actions for CI/CD.

The plan is structured in three phases — **Orient**, **Build**, and **Scale** — each roughly one month. The immediate priorities are understanding the people, assessing the quality gaps, and establishing the foundations of a structured QA function — all while ensuring HIPAA compliance obligations are embedded into every quality decision from day one.

> **How to use this plan:** This is a living document. Review and adjust it at each phase boundary. Items marked with `[Lead]` are particularly relevant for cross-team and leadership-facing responsibilities.

---

## Guiding Principles

- **Listen before you lead.** Invest the first two weeks in understanding — team dynamics, existing practices, and leadership expectations — before proposing structural changes.
- **HIPAA is not optional.** Every process, test data strategy, tooling decision, and workflow must account for HIPAA compliance from the start.
- **Build trust with the existing QA team first.** Two manual QA engineers are already on the team — understand their frustrations, capabilities, and aspirations before changing anything they own.
- **Make quality visible.** Establish metrics and reporting early so leadership can see QA's contribution clearly.
- **Governance over gatekeeping.** Quality belongs to the whole team; your role is to design the system, not be the sole quality check.
- **Communicate progress.** Regular, transparent updates to leadership and the team build credibility faster than any deliverable.

---

## Phase 1 — Orient & Discover (Weeks 1–4)

**Goal:** Build deep context about the organization, team, product, HIPAA obligations, and current QA state. Produce a clear strategy before changing any process.

---

### Day 1–2: First Steps

- [ ] Complete HR, IT, and compliance onboarding: accounts, credentials, VPN, required HIPAA training, BAA acknowledgements, and privacy policy review.
- [ ] Request access upfront: GitHub repository (read-only), GitHub Actions pipelines, defect tracking system, test documentation, and any existing quality reporting dashboards.
- [ ] Introduce yourself individually to both QA engineers — schedule dedicated 1:1s in the first week.
- [ ] Meet your manager and ask: _"What does success look like at 30, 60, and 90 days for this role?"_
- [ ] Identify the key ceremonies (sprint planning, standups, retrospectives, release reviews) and add them all to your calendar.
- [ ] Find out where product requirements, architecture decisions, and compliance documentation live.

---

## Week 1: Orientation & Discovery

**Goal:** Understand the people, product, compliance landscape, and current QA state.

### People & Culture

- [ ] Schedule 1:1s with all direct reports (both QA engineers) — listen for pain points, current workload, morale, career goals, and what they wish was different.
- [ ] Meet individually with key stakeholders: Engineering Manager, Product Manager, lead developer, and any compliance or security officer.
- [ ] Understand team rituals and cadences: sprint length, release frequency, code review norms, retrospective health.
- [ ] `[Lead]` Clarify your decision-making scope: what quality decisions are yours to make vs. collaborative vs. escalated to the Engineering Manager?
- [ ] `[Lead]` Understand leadership's definition of quality success — what keeps them up at night, what metrics they care about.

### Product & Domain

- [ ] Review available product documentation: feature specifications, user stories, architecture diagrams.
- [ ] Understand the product's core user journeys, primary user types, and most business-critical workflows.
- [ ] Review the product roadmap — understand what is built, what is in progress, and what is planned in the next quarter.
- [ ] Identify which features involve PHI (Protected Health Information) — these are highest risk and require the most rigorous test coverage.
- [ ] Understand the product's data flows: where PHI is collected, stored, transmitted, and accessed.

### Process & Quality Landscape

- [ ] Assess the current state of QA: How do the two QA engineers spend their time? What is tested, when, and how?
- [ ] Review any existing test plans, test cases, or manual test checklists.
- [ ] Understand how defects are logged, triaged, prioritized, and resolved — is there an SLA?
- [ ] Review the GitHub Actions CI/CD pipeline: is any automated testing integrated? What runs on pull requests vs. merges?
- [ ] Identify how releases are currently approved — is there a formal release checklist or sign-off process?
- [ ] Understand how HIPAA compliance testing (if any) is currently handled — audit logging, access controls, data masking.

### Tools & Process Landscape

- [ ] Inventory the tools currently in use: defect tracker, test case management (if any), project management, documentation, and reporting.
- [ ] Assess GitHub Actions pipelines for any existing test stages.
- [ ] Understand how test environments are managed — who controls staging? Is there a dedicated QA environment?
- [ ] Determine whether any PHI or real patient data is used in test environments (HIPAA violation risk — flag immediately if so).

**Phase 1 Early Deliverable (End of Week 1–2):** A written QA current-state assessment — current practices, team observations, HIPAA compliance gaps, tooling inventory, and open questions — shared with your manager.

---

## Week 2: Assessment & Strategy

**Goal:** Translate observations into a structured strategy. Define the target state for QA within this organization.

### Risk & Coverage Analysis

- [ ] Map the highest-risk areas of the product: PHI handling, authentication/authorization, audit logging, data exports, integrations with external health systems.
- [ ] Identify untested or undertested areas based on defect history, team feedback, and your own review.
- [ ] Review recent production incidents or escaped defects — identify root cause patterns.
- [ ] Assess HIPAA-specific test gaps: role-based access control testing, audit trail validation, data encryption verification, and breach notification scenarios.

### QA Process Design

- [ ] Draft a target QA process model: where in the SDLC does QA participate? What are the entry and exit criteria for each stage?
- [ ] Define a preliminary defect lifecycle: severity/priority definitions, SLA by severity, escalation path for HIPAA-related defects.
- [ ] Draft a release readiness checklist tailored to the product — including mandatory HIPAA sign-off items.
- [ ] Design a test data strategy: how to create, manage, and de-identify or synthesize test data that avoids using real PHI.

### Tooling Evaluation & Selection

- [ ] Evaluate whether a test case management tool is needed (e.g., TestRail, Zephyr, Notion-based tracking).
- [ ] Assess whether the 2 QA engineers have the tools they need to do their work effectively.
- [ ] Identify gaps in the GitHub Actions pipeline that a lightweight automation layer could address (e.g., smoke tests on deploy).
- [ ] `[Lead]` Research AI-powered QA tooling options — evaluate feasibility, compliance requirements (data residency, BAAs for SaaS tools), and ROI for the team context.

### Planning

- [ ] Draft a 90-day QA roadmap with milestones aligned to this plan.
- [ ] Identify quick wins: processes or tooling improvements deliverable within 30 days that build credibility.
- [ ] `[Lead]` Identify whether the QA team capacity (2 engineers) is sufficient for the product's risk profile and roadmap — flag if hiring is needed.

**Phase 1 Deliverable (Day 30):** A QA Strategy Document covering: current-state assessment, target QA process model, risk-prioritized coverage map, HIPAA compliance test gaps, tooling recommendations, test data strategy, and a 90-day roadmap. Reviewed with your manager and shared with the Engineering Manager.

---

## What Good Looks Like at 30 Days

- You have met individually with every team member and key stakeholder.
- You have a clear, documented picture of the current QA state and its gaps.
- HIPAA-related test gaps have been identified and flagged — no real PHI is being used in test environments.
- A QA strategy document is drafted and reviewed with your manager.
- The two QA engineers feel heard and understand that changes will be made with them, not to them.
- You have identified 2–3 quick wins to deliver in Phase 2.

---

## Phase 2 — Build & Integrate (Weeks 5–8)

**Goal:** Establish the core QA processes, governance structures, and baseline metrics. Integrate QA into the team's ways of working.

---

## Week 3: Process Design & Team Integration

### Defect Lifecycle & Release Criteria

- [ ] Publish the defect lifecycle process: severity/priority definitions, SLA targets per severity, triage cadence, escalation policy.
- [ ] Establish a HIPAA escalation path: any defect involving potential PHI exposure or audit log failure is P1 by definition.
- [ ] Define and publish formal release criteria — minimum regression pass rate, zero open P1/P2 defects, HIPAA sign-off checklist completed.
- [ ] `[Lead]` Get Engineering Manager and Product Manager alignment on release criteria before publishing team-wide.

### QA Ceremonies & Team Cadence

- [ ] Establish a recurring QA team sync (weekly) with the 2 QA engineers: workload review, blocker identification, process retrospective.
- [ ] Integrate QA into sprint ceremonies: ensure QA participates in sprint planning (to identify testability requirements early) and retrospectives.
- [ ] Establish a "Definition of Done" contribution from QA: what test coverage is required before a story can be marked complete.
- [ ] Begin 1:1 cadence with both QA engineers (bi-weekly minimum).

### Test Data Strategy Implementation

- [ ] Implement or document the approved test data strategy — synthetic data generation or de-identified data pipeline — to eliminate PHI risk in test environments.
- [ ] `[Lead]` Work with a developer to review whether the current staging environment contains any real PHI; remediate if so.
- [ ] Document the test data creation process so QA engineers can follow it independently.

### HIPAA Compliance Testing Integration

- [ ] Establish a HIPAA test checklist as a mandatory part of every release: audit log validation, role-based access control tests, data masking confirmation, session timeout behavior.
- [ ] Ensure both QA engineers understand which test scenarios are HIPAA-required and cannot be deferred.

**Week 3 Deliverable:** Defect lifecycle process published, release criteria agreed with Engineering Manager and PM, QA ceremonies established, and HIPAA test checklist in use.

---

## Week 4: Metrics, Reporting & Stakeholder Alignment

### Metrics Baseline

- [ ] Define the QA metrics that matter for this context: escaped defect rate, regression pass rate at release, defect SLA adherence, open critical/high defect count, and HIPAA test completion rate per release.
- [ ] Establish baselines for each metric using historical data where available.
- [ ] Set up a lightweight reporting dashboard or shared document — this does not need to be a complex tool; a well-structured GitHub wiki page or Notion doc is sufficient.

### Stakeholder Reporting

- [ ] `[Lead]` Establish a recurring QA status report cadence for leadership (bi-weekly or per sprint): key metrics, risks, upcoming release readiness, and any HIPAA-related flags.
- [ ] Create a release readiness summary template — a consistent, one-page view of QA status before each release.
- [ ] `[Lead]` Schedule a working session with the Engineering Manager to review QA metrics together and agree on targets.

### Cross-Team Governance

- [ ] `[Lead]` Define QA's role in the pull request process — should QA review certain PRs? Define the criteria.
- [ ] `[Lead]` Establish an escalation path for quality-related disagreements (e.g., dev wants to ship, QA has open criticals) — document and agree with the Engineering Manager.
- [ ] Identify and document any external compliance reporting requirements relevant to QA (e.g., audit logs reviewed quarterly, penetration testing schedule).

### AI Tooling Business Case

- [ ] `[Lead]` Compile a short business case for AI-assisted QA tooling for the team: potential time savings, coverage gains, HIPAA compliance requirements for any SaaS tools (BAA required), and recommended next step.
- [ ] Socialize with the Engineering Manager before any tool purchase decision.

**Phase 2 Deliverable (Day 60):** QA processes operating consistently for at least 2 sprints, baseline metrics established and shared with leadership, release criteria in active use, HIPAA compliance checklist embedded in every release, and AI tooling recommendation documented.

---

## What Good Looks Like at 60 Days

- QA processes (defect lifecycle, release criteria, Definition of Done, QA ceremonies) are in place and followed consistently.
- Baseline quality metrics are visible to leadership — escaped defect rate, regression pass rate, HIPAA checklist completion.
- No real PHI is present in any test environment.
- Both QA engineers are operating with clear expectations, and morale is stable or improving.
- Release readiness reports are being produced before each release.
- You have a relationship of trust with the Engineering Manager and Product Manager.

---

## Phase 3 — Stabilize & Scale (Weeks 9–12)

**Goal:** Demonstrate measurable quality improvement, address capacity or structural gaps, and establish QA's strategic roadmap.

---

## Week 5–6: Stabilize & Deepen

- [ ] Conduct a process retrospective with the QA team: what is working, what is not, what should be adjusted?
- [ ] Review metrics against baselines set in Phase 2 — identify trends and areas needing improvement.
- [ ] Assess whether the QA team's capacity is sustainable: are the 2 QA engineers overloaded? Are there coverage gaps due to team size?
- [ ] `[Lead]` If capacity is insufficient, prepare a hiring justification with data: coverage gaps, escaped defect trends, roadmap growth. Present to the Engineering Manager.
- [ ] Deepen the HIPAA compliance testing posture: review whether current checks cover all required controls (access control, audit logging, integrity, transmission security).
- [ ] Identify any automation opportunities the QA engineers could realistically own with support — e.g., smoke test scripts in GitHub Actions for the most critical user journeys.

---

## Week 7–8: Scale & Future Planning

- [ ] `[Lead]` Draft the QA OKRs for the next quarter: align to product roadmap risks, HIPAA obligations, and team growth.
- [ ] `[Lead]` Prepare a QA roadmap presentation for leadership: where QA is today, where it will be in 6 months, what investment is needed (tooling, headcount, training).
- [ ] Define a career development plan skeleton for each QA engineer — what skills to grow, what ownership to expand.
- [ ] `[Lead]` Assess whether any external audit readiness work is needed (HIPAA security risk assessment contributions, penetration test coordination, BAA inventory review).
- [ ] Evaluate whether the AI tooling business case from Phase 2 has received approval — if so, begin a controlled pilot.
- [ ] Document all QA processes, metrics, and governance in a shared, durable location (GitHub wiki or equivalent) so the function is not dependent on you personally.

**Phase 3 Deliverable (Day 90):** QA function operating independently and consistently; quality metrics showing measurable trend improvement vs. Day 1 baseline; QA OKRs for next quarter agreed with leadership; hiring plan or capacity review completed; QA roadmap presented to leadership; all processes documented.

---

## What Good Looks Like at 90 Days

- The QA function has a clear identity, process, and voice within the team.
- Escaped defect rate and regression pass rate are tracked, trended, and moving in the right direction.
- HIPAA compliance test coverage is documented, consistent, and defensible in an audit.
- Both QA engineers have clear roles, growth paths, and are operating more effectively than when you arrived.
- Leadership has visibility into QA's contribution through regular, consistent reporting.
- A QA roadmap and OKRs for the next quarter are agreed and in flight.
- The QA function would continue to operate effectively if you were unavailable for a week.

---

## Key Deliverables Summary

| Deliverable                                                         | Target Date   | Owner                |
| ------------------------------------------------------------------- | ------------- | -------------------- |
| QA Current-State Assessment                                         | End of Week 2 | QA Manager           |
| QA Strategy Document (process model, risk map, HIPAA gaps, roadmap) | Day 30        | QA Manager           |
| Defect lifecycle process published                                  | Week 3        | QA Manager           |
| Release criteria agreed and in use                                  | Week 3        | QA Manager + EM + PM |
| HIPAA compliance test checklist in use                              | Week 3        | QA Manager           |
| Test data strategy implemented (no PHI in test envs)                | Week 4        | QA Manager + Dev     |
| QA metrics baseline and dashboard                                   | Week 4        | QA Manager           |
| Stakeholder reporting cadence established                           | Week 4        | QA Manager           |
| AI tooling business case                                            | Week 4        | QA Manager           |
| Process retrospective completed                                     | Week 5        | QA Manager           |
| Hiring justification (if applicable)                                | Week 6        | QA Manager           |
| QA OKRs for next quarter                                            | Week 7        | QA Manager           |
| QA roadmap presentation to leadership                               | Week 8        | QA Manager           |
| QA process documentation (durable)                                  | Day 90        | QA Manager           |

---

## Success Metrics

| Metric                                 | Baseline Target (Day 30) | Target at Day 60           | Target at Day 90             |
| -------------------------------------- | ------------------------ | -------------------------- | ---------------------------- |
| Escaped defect rate                    | Measured and documented  | Trending down vs. baseline | Measurably reduced vs. Day 1 |
| Regression pass rate at release        | Measured                 | ≥ 85%                      | ≥ 90%                        |
| Defect SLA adherence (P1/P2)           | Process defined          | ≥ 80%                      | ≥ 90%                        |
| HIPAA checklist completion per release | Checklist created        | 100%                       | 100%                         |
| Real PHI in test environments          | Identified               | Eliminated                 | Zero                         |
| QA engineer morale                     | Assessed via 1:1         | Stable                     | Stable or improving          |
| Open P1 defects at release             | Tracked                  | 0                          | 0                            |

---

## Ongoing Practices

- **Bi-weekly QA team sync** — workload review, blocker identification, process health check.
- **Per-sprint release readiness report** — consistent template, shared with EM and PM.
- **Monthly metrics review with EM** — trends, targets, risks.
- **Quarterly HIPAA compliance review** — confirm checklist is current and coverage is adequate.
- **1:1s with each QA engineer** — bi-weekly minimum; track career development, morale, and growth.
- **Definition of Done contribution** — QA criteria reviewed in every sprint planning.
- **Retrospective participation** — QA perspective included in every sprint retrospective.

---

## QA Governance Reference

| Governance Item                              | Definition                                                                                                                                          |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Release criteria**                         | Regression suite pass rate ≥ 90%, zero open P1 defects, zero open P2 defects without explicit EM sign-off, HIPAA compliance checklist 100% complete |
| **Defect severity — P1 (Critical)**          | PHI exposure risk, data loss, authentication/authorization bypass, system unavailable in production                                                 |
| **Defect severity — P2 (High)**              | Core user journey broken, audit logging failure, data integrity issue, significant functional regression                                            |
| **Defect SLA — P1**                          | Acknowledged within 2 hours; fix or mitigation within 24 hours                                                                                      |
| **Defect SLA — P2**                          | Acknowledged within 1 business day; resolved within current sprint                                                                                  |
| **HIPAA escalation path**                    | Any defect with potential PHI exposure → immediate P1 → notify EM + compliance officer within 2 hours                                               |
| **Test data policy**                         | No real PHI permitted in any non-production environment; all test data must be synthetic or de-identified                                           |
| **Definition of Done (QA contribution)**     | Story-level acceptance criteria tested, edge cases identified, defects logged, regression impact assessed                                           |
| **QA sign-off on release**                   | QA Manager or delegated QA engineer confirms release checklist complete before deploy to production                                                 |
| **Reporting cadence**                        | Per-sprint release readiness report; bi-weekly executive summary; monthly metrics trend review                                                      |
| **Escalation for ship/no-ship disagreement** | QA Manager → Engineering Manager → final decision documented with rationale                                                                         |
