# 90-Day Onboarding Plan: QA Manager

## Overview

This plan covers the first 90 days for a QA Manager joining any organization — whether inheriting an existing QA team, building the function from scratch, or stepping into a role where QA has been performed informally by developers and manual testers. It is structured in three phases — **Orient**, **Build**, and **Scale** — each roughly one month.

The QA Manager's primary leverage is not personal test execution — it is the system you design, the people you develop, and the visibility you create. Everything in this plan is oriented toward those three outcomes.

> **How to use this plan:** This is a living document. Review and adjust it at each phase boundary. Items marked with `[Lead]` represent decisions or communications that typically require formal sign-off or stakeholder alignment — do not act on these unilaterally.

---

## Guiding Principles

- **Listen before you change anything.** The first two weeks are for understanding, not restructuring. Changes made too early — before you have context and trust — backfire.
- **Build trust with your direct reports first.** They have institutional knowledge you do not have yet. Make their jobs easier before you ask them to do things differently.
- **Make quality visible.** Leadership often cannot see QA's contribution. Your job includes creating that visibility through metrics, reports, and clear communication.
- **Governance over gatekeeping.** Quality is a team responsibility — your role is to design the system, not be the bottleneck.
- **People before process.** Processes that do not fit the people fail. Understand your team before designing workflows.
- **Communicate progress.** Regular, transparent updates to your manager and stakeholders build credibility faster than any single deliverable.

---

## Phase 1 — Orient & Discover (Weeks 1–4)

**Goal:** Build deep context about the organization, your team, the product, and the current state of quality. Produce a clear strategy before changing any process.

---

### Day 1–2: First Steps

The first two days are about access, relationships, and first impressions — not process changes.

- [ ] Complete HR and IT onboarding: accounts, credentials, VPN, and any required policy training.
- [ ] Request access upfront: defect tracker, project management tool, CI/CD system, test documentation, any existing reporting dashboards, and shared documentation (Confluence, Notion, etc.).
- [ ] Schedule individual 1:1s with every direct report in the first week — these are listening sessions, not performance conversations.
- [ ] Ask your manager: _"What does success look like for this role at 30, 60, and 90 days?"_
- [ ] Identify all key ceremonies and add them to your calendar: standups, sprint planning, retrospectives, release reviews, and any existing QA-specific meetings.
- [ ] Find out where product requirements, architecture decisions, and compliance documentation live.

---

## Week 1: Orientation & Discovery

**Goal:** Understand the people, product, and current quality landscape before forming any opinions about what needs to change.

### People & Culture

- [ ] Complete administrative and HR onboarding (access, tools, policies, benefits).
- [ ] Hold individual 1:1s with every direct report — listen for pain points, current workload, morale, career goals, what is going well, and what they wish was different.
- [ ] Meet individually with key stakeholders: Engineering Manager, Product Manager, and any other QA-adjacent leads (UX, DevOps, Security).
- [ ] Understand team rituals and cadences: sprint length, release frequency, retrospective health, and decision-making norms.
- [ ] `[Lead]` Clarify your scope of authority with your manager: what quality decisions are yours to make vs. collaborative vs. escalated? Where does your budget authority begin and end?
- [ ] `[Lead]` Understand leadership's definition of quality success — what are their top concerns? What keeps them up at night? What metrics do they already track (even informally)?

### Product & Domain

- [ ] Review available product documentation: feature specs, user stories, architecture diagrams, and design specs.
- [ ] Understand the product's core user journeys, target users, and most business-critical workflows.
- [ ] Review the product roadmap — understand what is built, what is in progress, and what is planned in the next quarter.
- [ ] Identify the highest-risk areas of the product from a business perspective (what would be catastrophic to break?).

### Process & Quality Landscape

- [ ] Assess the current state of QA: how does the team currently test? Manual only? Some automation? Who does the testing — dedicated QA, developers, or both?
- [ ] Review any existing test plans, test cases, or test documentation.
- [ ] Understand how defects are logged, triaged, prioritised, and resolved. Is there an SLA? Is it followed?
- [ ] Review the CI/CD pipeline: is any automated testing integrated? What runs on pull requests vs. merges vs. releases?
- [ ] Understand how releases are currently approved — is there a formal sign-off process or an informal thumbs-up?
- [ ] Review recent production incidents or escaped defects — identify patterns and root causes.

### Tools & Process Landscape

- [ ] Inventory the tools currently in use: defect tracker, test case management (if any), project management, documentation, dashboards, and reporting.
- [ ] Understand test environment availability: staging, pre-production, ephemeral PR environments. Are they stable? Who controls them?
- [ ] Identify any tool gaps or pain points your team has raised.
- [ ] Understand how the team communicates about quality: async channels, synchronous meetings, written reports.

**Phase 1 Early Deliverable (End of Week 1–2):** A written QA current-state assessment — current practices, team observations, tooling inventory, known gaps, and open questions — shared with your manager. This is for alignment, not announcement.

---

## Week 2: Assessment & Strategy

**Goal:** Translate observations into a clear picture of the target state. Design the QA function you are building toward.

### Risk & Coverage Analysis

- [ ] Map the highest-risk areas of the product against current test coverage — where are the gaps?
- [ ] Review defect history: where do bugs originate? What types escape to production? What is the average time to detection?
- [ ] Identify the team's current coverage blind spots: are there user journeys with no test coverage? Features tested only manually? APIs with no contract testing?
- [ ] Identify any compliance or regulatory requirements that affect QA coverage (data privacy, audit logging, access control, industry-specific regulations).

### QA Process Design

- [ ] Draft a target QA process model: where in the SDLC should QA participate? What are the entry and exit criteria for each stage (story review, development, testing, release)?
- [ ] Define a preliminary defect lifecycle: severity and priority definitions, SLA targets by severity, triage cadence, escalation path.
- [ ] Draft a release readiness checklist: minimum regression pass rate, open defect thresholds, sign-off steps.
- [ ] Design or review the Definition of Done: what testing is required before a story can be marked complete?

### Tooling Evaluation

- [ ] Evaluate whether a test case management tool is needed or whether the existing solution is adequate.
- [ ] Identify any tool investments (new or improved) that would materially improve QA effectiveness.
- [ ] `[Lead]` Research AI-assisted QA tooling — assess feasibility, compliance requirements for SaaS tools, cost, and potential ROI. Build the business case before proposing any purchase.
- [ ] `[Lead]` Identify any tool contracts up for renewal and understand your approval authority for tooling spend.

### Planning

- [ ] Draft a 90-day QA roadmap with milestones aligned to this plan.
- [ ] Identify 2–3 quick wins deliverable within 30 days — small, visible improvements that build credibility with the team and leadership.
- [ ] `[Lead]` Assess whether the current team capacity is adequate for the product's risk profile and roadmap. If a gap exists, begin documenting the case for hiring.

**Phase 1 Deliverable (Day 30):** A QA Strategy Document covering: current-state assessment, target QA process model, risk-prioritised coverage gaps, tooling recommendations, and a 90-day roadmap. Reviewed with your manager and shared with the Engineering Manager.

---

## What Good Looks Like at 30 Days

At the 30-day mark, you should feel confident that:

- You have met individually with every direct report and key stakeholder and genuinely listened.
- You have a clear, documented picture of the current QA state and its most significant gaps.
- Your direct reports understand that changes will be made _with_ them, not _to_ them.
- A QA Strategy Document is drafted and your manager has reviewed it.
- You have identified 2–3 quick wins to deliver in Phase 2.
- You have not yet changed any core processes — that comes in Phase 2 with team input.

---

## Phase 2 — Build & Integrate (Weeks 5–8)

**Goal:** Establish core QA processes, governance structures, and baseline metrics. Integrate QA meaningfully into the team's ways of working.

---

## Week 3: Process Design & Team Integration

### Defect Lifecycle & Release Criteria

- [ ] Publish the defect lifecycle process: severity and priority definitions, SLA targets per severity, triage cadence, and escalation path.
- [ ] Define and publish formal release criteria — minimum regression pass rate, maximum open defect thresholds by severity, required sign-off steps.
- [ ] `[Lead]` Align release criteria with the Engineering Manager and Product Manager before publishing team-wide. These are agreements, not mandates.
- [ ] Establish a clear escalation path for quality-related disagreements (e.g., dev wants to ship, QA has open criticals) — document it and agree with the Engineering Manager.

### QA Ceremonies & Team Cadence

- [ ] Establish a recurring QA team sync with your direct reports: workload review, blocker identification, morale check, and process retrospective cadence.
- [ ] Integrate QA into sprint ceremonies: ensure QA participates in sprint planning (to identify testability requirements early) and retrospectives (to contribute a quality perspective).
- [ ] Embed QA into the Definition of Done: define what test coverage is required before a story can be marked complete, and ensure the team understands and follows it.
- [ ] Establish a regular 1:1 cadence with every direct report (bi-weekly minimum).

### Team Development

- [ ] Based on your Week 1 1:1 observations, identify each team member's strengths, growth areas, and immediate development needs.
- [ ] Identify any skills gaps across the team relative to the target QA function (e.g., automation skills, domain knowledge, exploratory testing depth).
- [ ] `[Lead]` If skills gaps are significant, explore options: training, mentoring, pair work with developers, or hiring.

**Week 3 Deliverable:** Defect lifecycle process published, release criteria agreed with Engineering Manager and PM, QA ceremonies established and calendar invitations sent.

---

## Week 4: Metrics, Reporting & Stakeholder Alignment

### Metrics Baseline

- [ ] Define the QA metrics that matter for your context: escaped defect rate, regression pass rate at release, defect SLA adherence, open critical/high defect count, test coverage trends, and team capacity utilisation.
- [ ] Establish baselines for each metric using historical data where available. Document the current state explicitly — this is the baseline all future improvement will be measured against.
- [ ] Set up a lightweight reporting dashboard or shared document. It does not need to be a complex tool — a well-maintained wiki page or spreadsheet is sufficient to start.

### Stakeholder Reporting

- [ ] `[Lead]` Establish a recurring QA status report cadence for leadership (bi-weekly or per sprint): key metrics, risks, upcoming release readiness, and any flags requiring leadership attention.
- [ ] Create a release readiness summary template — a consistent, one-page view of QA status that the team produces before every release.
- [ ] `[Lead]` Schedule a working session with the Engineering Manager to review QA metrics together and agree on improvement targets.

### Cross-Team Governance

- [ ] `[Lead]` Define QA's role in the code review and pull request process — should QA review certain changes? Define the criteria and communicate them to the team.
- [ ] `[Lead]` Identify any external reporting or audit requirements relevant to QA and ensure the team's processes generate the necessary evidence.
- [ ] Identify dependencies between QA and other teams (DevOps for environment stability, Security for penetration testing, Data for test data access) and establish working agreements.

### AI Tooling

- [ ] `[Lead]` If the AI tooling business case from Phase 1 is ready, present it to the Engineering Manager or relevant decision-maker. Include: potential time savings, coverage quality improvements, compliance requirements for any SaaS tools, and recommended next step (pilot vs. full rollout).

**Phase 2 Deliverable (Day 60):** QA processes operating consistently for at least 2 sprints; baseline metrics established and visible to leadership; release readiness reports being produced before each release; team 1:1 cadence in place.

---

## What Good Looks Like at 60 Days

At the 60-day mark, you should feel confident that:

- QA processes — defect lifecycle, release criteria, Definition of Done, QA ceremonies — are in place and followed consistently.
- Baseline quality metrics are tracked and visible to leadership.
- Both you and your direct reports have a clear understanding of each other's expectations.
- Release readiness reports are being produced before each release.
- Leadership has seen at least one quality metrics update from you.
- You have a working relationship of trust with the Engineering Manager and Product Manager.

---

## Phase 3 — Stabilize & Scale (Weeks 9–12)

**Goal:** Demonstrate measurable quality improvement, address structural gaps, and establish the QA function's strategic roadmap.

---

## Week 5–6: Stabilize & Deepen

- [ ] Conduct a process retrospective with your QA team: what is working, what is not, what should be adjusted?
- [ ] Review metrics against the baselines established in Phase 2 — identify trends, improvements, and areas of concern.
- [ ] Assess team capacity sustainability: are your direct reports carrying a sustainable workload? Are there coverage gaps caused by team size or skills constraints?
- [ ] `[Lead]` If capacity is insufficient, prepare a hiring justification with data: coverage gaps, escaped defect trends, roadmap growth projections, and proposed role. Present to your manager.
- [ ] Identify automation investment opportunities: are there high-frequency manual regression tests that would deliver strong ROI if automated? Work with the team to prioritise these.
- [ ] Deepen any compliance testing posture that was identified in Phase 1 — ensure coverage is documented, consistent, and defensible.

---

## Week 7–8: Scale & Future Planning

- [ ] `[Lead]` Draft the QA OKRs for the next quarter, aligned to the product roadmap's risk profile and the team's development goals.
- [ ] `[Lead]` Prepare a QA roadmap presentation for leadership: where QA is today vs. Day 1, what has improved and by how much, what the next 6 months look like, and what investment is needed.
- [ ] Define a career development plan skeleton for each direct report: growth areas, expanded ownership, and any training or mentoring investment.
- [ ] Document all QA processes, metrics, and governance in a shared, durable location so the function is not dependent on your personal presence to operate.
- [ ] Evaluate whether the AI tooling pilot (if approved in Phase 2) has produced measurable results — document findings and recommend next steps.
- [ ] Conduct a 90-day retrospective for yourself: what went well, what you would do differently, and what you still need to learn.

**Phase 3 Deliverable (Day 90):** QA function operating independently and consistently; quality metrics showing measurable trend improvement vs. Day 1 baseline; QA OKRs for next quarter agreed with leadership; hiring plan or capacity review completed; all processes documented; QA roadmap presented to leadership.

---

## What Good Looks Like at 90 Days

At the 90-day mark, you should feel confident that:

- The QA function has a clear identity, process, and voice within the engineering team.
- Quality metrics are tracked, trended, and moving in the right direction vs. the Day 1 baseline.
- Every direct report has clear role expectations, a development path, and is performing at or above that expectation.
- Leadership has consistent, reliable visibility into QA's contribution through regular reporting.
- A QA roadmap and OKRs for the next quarter are agreed and in flight.
- The QA function would continue to operate effectively if you were unavailable for two weeks.
- You feel genuinely productive, and you have identified the areas where you still want to grow as a manager.

---

## Key Deliverables Summary

| Phase   | Milestone       | Deliverable                                                                                 |
| ------- | --------------- | ------------------------------------------------------------------------------------------- |
| Phase 1 | End of Week 1–2 | QA current-state assessment (written, shared with manager)                                  |
| Phase 1 | Day 30          | QA Strategy Document — process model, risk map, tooling recommendations, 90-day roadmap     |
| Phase 2 | Week 3          | Defect lifecycle + release criteria published and agreed with EM and PM                     |
| Phase 2 | Week 3          | QA ceremonies and 1:1 cadence established                                                   |
| Phase 2 | Week 4          | Metrics baseline documented; release readiness report template in use                       |
| Phase 2 | Day 60          | Processes operating consistently for ≥ 2 sprints; leadership receiving QA status updates    |
| Phase 3 | Week 5–6        | Process retrospective completed; capacity review or hiring justification prepared           |
| Phase 3 | Week 7–8        | QA OKRs drafted; QA roadmap presented to leadership                                         |
| Phase 3 | Day 90          | All processes documented; career development plans in place; 90-day retrospective completed |

---

## Success Metrics

Use the Current Baseline column to anchor targets to the actual starting point. Populate it at Day 30.

| Metric                               | Current Baseline (Day 30) | Target at Day 60                              | Target at Day 90                      |
| ------------------------------------ | ------------------------- | --------------------------------------------- | ------------------------------------- |
| **Escaped defect rate**              | Measure and document      | Trending down vs. baseline                    | Measurably reduced vs. Day 1          |
| **Regression pass rate at release**  | Measure and document      | ≥ 85% or +10% vs. baseline (whichever higher) | ≥ 90% or +15% vs. baseline            |
| **Defect SLA adherence (P1/P2)**     | Process defined           | ≥ 80%                                         | ≥ 90%                                 |
| **Open P1 defects at release**       | Tracked                   | 0                                             | 0                                     |
| **Team morale (via 1:1 signal)**     | Assessed                  | Stable                                        | Stable or improving                   |
| **QA ceremony attendance**           | Baseline established      | ≥ 90% attendance                              | ≥ 90% attendance; team self-organises |
| **Release readiness report cadence** | Template created          | 100% of releases have a report                | 100% of releases have a report        |

> **Calibration note:** If QA maturity is **None (first QA hire)**, all Day 30 targets should read "Establish baseline". Do not set numerical targets until the baseline is confirmed. If maturity is **Established**, use existing historical data to set precise, evidence-backed targets rather than the indicative values above.

---

## Ongoing Practices

- **Weekly QA team sync** — workload review, blocker identification, morale check.
- **Bi-weekly 1:1s with each direct report** — career development, performance signals, and psychological safety check.
- **Per-sprint release readiness report** — consistent template, shared with EM and PM before every release.
- **Monthly metrics review with EM** — trends, targets, risks.
- **Quarterly process retrospective** — what is working, what needs adjusting.
- **Retrospective participation** — QA perspective in every sprint retrospective.
- **Definition of Done review** — QA exit criteria reviewed in every sprint planning session.
- **Stakeholder reporting cadence** — bi-weekly or per-sprint executive summary.

---

## QA Governance Reference

When drafting your QA governance model (Phase 1–2), ensure it covers the following:

| Governance Item                 | Definition                                                                                            |
| ------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Release criteria**            | Minimum regression pass rate, maximum open defect count by severity, required sign-off steps          |
| **Defect severity definitions** | P1 (Critical), P2 (High), P3 (Medium), P4 (Low) — with examples specific to your product              |
| **Defect SLA by severity**      | Acknowledgement and resolution time targets for each severity level                                   |
| **Escalation path**             | Who decides when an open P1 blocks a release; who has authority to override with documented rationale |
| **Definition of Done (QA)**     | What test coverage is required before a story is complete; who verifies it                            |
| **Release readiness sign-off**  | Who signs off on release readiness, what evidence is required, and how it is recorded                 |
| **Reporting cadence**           | Per-sprint release readiness report; bi-weekly executive summary; monthly metrics trend review        |
| **Ship/no-ship disagreement**   | QA Manager → Engineering Manager → documented final decision with rationale                           |
| **Test data policy**            | What data may and may not be used in non-production environments                                      |
| **Tooling approval**            | Budget thresholds and approval chain for new QA tooling                                               |
