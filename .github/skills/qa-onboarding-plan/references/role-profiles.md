# Role Profiles

This reference defines how to adapt the 90-day onboarding plan for each supported role. Load this file in Step 2 of the skill procedure.

---

## QA Automation Developer / Engineer

**Core emphasis:** Framework setup, test scripting, CI/CD integration, testability collaboration with developers.

**Phase 1 adaptations:**

- Landscape section: "Existing QA Landscape" — assess current automation state, scripts, CI hooks
- Environment Setup: local dev env, ability to run the application, access to test environments

**Phase 2 adaptations:**

- Week 3 title: "Framework Setup & AI-Assisted Development"
- Key subsections: Framework Setup (POC → Foundation), AI-Assisted Test Development, First Test Scripts
- Week 4 title: "Team Integration & Coverage Expansion"
- Key subsections: Collaboration with dev team, Definition of Done, exploratory testing, API/DB test coverage

**Phase 3 adaptations:**

- Stabilize: flaky test audit, full regression triage, test suite reliability
- Scale: visual regression, performance hooks, AI-assisted maintenance

**AI-driven testing:** Full section in Week 2 strategy and Week 3 implementation. Include: LLM-assisted test case generation, Copilot for scripting, edge case identification, prompt library, ROI tracking.

**[Lead] tags:** Not applicable. All items are IC-level.

**Metrics to include:** Automation coverage, smoke pass rate, regression pass rate, defect detection rate, escaped defects, flaky test rate, CI test stage duration, MTTF, AI-assisted coverage gain.

**Seniority modifiers:**

- **Junior:** Extend environment setup to 2 weeks; pair with a developer for the first framework POC; scope Phase 1 deliverable to a current-state assessment only (no full strategy); defer CI/CD integration ownership to a senior/lead.
- **Mid:** Standard plan as described above — owns framework setup and scripting, contributes to strategy, operates independently within sprint.
- **Senior:** Drives framework architecture decisions from Week 2; expected to propose automation strategy, advocate for tooling choices, and mentor other contributors from Phase 1.

---

## QA Automation Lead

**Core emphasis:** Strategy ownership, tooling decisions, team enablement, standards, stakeholder communication.

**Phase 1 adaptations:**

- Landscape section: "Existing QA Landscape" — assess team structure, current practices, and gaps
- Add: Clarify scope of authority (what decisions are yours vs. collaborative vs. escalated)

**Phase 2 adaptations:**

- Week 3 title: "Framework Architecture & Standards"
- Key subsections: Framework design decisions, contribution guidelines, CI/CD standards, team walkthrough
- Week 4 title: "Team Enablement & Stakeholder Integration"
- Key subsections: Mob testing session, Definition of Done review, release readiness process, stakeholder reporting

**Phase 3 adaptations:**

- Stabilize: audit framework quality, enforce standards across team
- Scale: QA roadmap presentation to leadership, hiring or capacity plan

**AI-driven testing:** Full section. Emphasis on evaluating AI tooling across the team, building shared prompt libraries, advocating for AI tooling access, measuring team-level ROI.

**[Lead] tags:** Apply to: scope of authority, strategy sign-off, team onboarding on framework, stakeholder presentations, hiring plan, QA roadmap.

**Metrics to include:** All Developer metrics plus team contribution rate (% of tests written by developers), mean time to onboard new contributors to the framework.

**Seniority modifiers:**

- **Junior:** Not typical for this role; if encountered, treat as QA Automation Developer with lead mentorship from a senior engineer; defer tooling decisions and standards ownership.
- **Mid:** Owns strategy within their team scope; drives framework standards for the immediate team; presents to EM and PM but not to wider leadership.
- **Senior:** Expected to influence cross-team tooling decisions, present QA roadmap to leadership independently, and own hiring justification from Phase 2.

---

## SDET (Software Development Engineer in Test)

**Core emphasis:** Testability at the code level, unit/integration depth, test utilities, embedded in dev teams.

**Phase 1 adaptations:**

- Landscape section: "Engineering & Testability Landscape" — assess code coverage, unit test quality, CI pipeline depth, testability of existing code
- Environment Setup: full local dev setup including ability to build, run, and debug the application

**Phase 2 adaptations:**

- Week 3 title: "Test Utilities, Harnesses & AI-Assisted Development"
- Key subsections: Test utility library setup, API contract testing, schema validation, test harness design
- Week 4 title: "Developer Integration & Coverage Depth"
- Key subsections: Pairing with developers, code review contributions, shifting quality left, unit/integration coverage expansion

**Phase 3 adaptations:**

- Stabilize: measure code coverage trends, identify untestable code and propose refactors
- Scale: establish team-level testing standards, contribute to architecture decisions

**AI-driven testing:** Full section. Additional emphasis on: AI-assisted code generation for test utilities and harnesses, LLM-assisted review of unit test quality.

**[Lead] tags:** Not applicable. SDET is an IC role. Use influence-based framing for cross-team impact.

**Metrics to include:** Code coverage (unit + integration), contract test pass rate, defect detection rate (pre-production), testability debt items identified, AI-assisted coverage gain.

**Seniority modifiers:**

- **Junior:** Extend pairing with developers through Phase 2; narrow scope to one team; defer architecture decisions and cross-team influence to a senior engineer or lead; Phase 1 deliverable is a testability assessment, not a full strategy.
- **Mid:** Standard plan as described — owns testability within the team, contributes to code review and CI, operates with developer-level autonomy.
- **Senior:** Expected to drive testability strategy across multiple teams from Phase 1; propose architecture refactors to improve testability; influence engineering standards and contribute to ADRs.

---

## QA Manager

**Core emphasis:** People, process, metrics, hiring, cross-team governance, budget/tooling approvals.

**Phase 1 adaptations:**

- Landscape section: "Process & Quality Landscape" — assess team structure, current processes, reporting mechanisms, existing QA function maturity
- Replace "Environment Setup" with "Tools & Process Landscape" — project management, defect tracking, dashboards, reporting tools
- Add: Understand team members' strengths, growth areas, and morale. Understand leadership's definition of quality success.

**Phase 2 adaptations:**

- Week 3 title: "Process Design & Team Integration"
- Key subsections: Defect lifecycle process, release criteria definition, QA ceremony structure, team 1:1s
- Week 4 title: "Metrics, Reporting & Stakeholder Alignment"
- Key subsections: Dashboard setup, metrics baseline, executive reporting, cross-team governance model

**Phase 3 adaptations:**

- Stabilize: hiring plan execution or capacity review, process retrospective
- Scale: QA OKRs for next quarter, team growth plan, leadership roadmap presentation

**AI-driven testing:** Lightweight. Focus on: making the business case for AI tooling investment, evaluating AI tools for the team's use, tracking ROI. Do not include scripting-level AI detail.

**[Lead] tags:** Apply broadly — hiring, budget, governance, escalation paths, OKRs, cross-team relationships.

**Sections to skip:** Test environment strategy (delegate to technical team), framework setup, scripting sections, Test Plan Components Reference.

**Replace with:** "QA Governance Reference" — release criteria, defect SLA, escalation policy, reporting cadence, Definition of Done ownership.

**Metrics to include:** Escaped defects, team velocity (test coverage per sprint), hiring pipeline progress, defect SLA adherence, regression pass rate at release, employee satisfaction/retention.

**Seniority modifiers:**

- **Junior:** Not typical for this role; if encountered, treat as a QA Lead with a manager mentor; scope ownership to process design only — defer hiring, budget, and cross-team governance to their manager.
- **Mid:** Standard plan as described — owns QA processes, team health, metrics, and stakeholder reporting; hiring justification requires EM sponsorship.
- **Senior:** Expected to independently drive QA strategy, own hiring decisions, present OKRs to leadership, and proactively shape engineering culture around quality from Phase 1.

---

## Test Architect

**Core emphasis:** Framework and tooling architecture decisions across teams, standards and governance, no direct reports.

**Phase 1 adaptations:**

- Landscape section: "Architecture & Standards Landscape" — assess existing frameworks, duplication across teams, tooling fragmentation, CI/CD patterns
- Focus on: understanding ALL teams' testing approaches, not just one team

**Phase 2 adaptations:**

- Week 3 title: "Framework Architecture & Cross-Team Standards"
- Key subsections: Shared utility design, common CI templates, framework governance model, ADR (Architecture Decision Record) for tooling choices
- Week 4 title: "Standards Rollout & Team Enablement"
- Key subsections: Documentation and standards publication, team walkthroughs, feedback collection, adoption plan

**Phase 3 adaptations:**

- Stabilize: measure standards adoption across teams, identify deviations and root causes
- Scale: automation platform roadmap, influence on engineering architecture decisions

**AI-driven testing:** Full section with architectural lens — evaluate AI tooling at the platform level, define standards for AI usage in testing across teams, assess build-vs-buy for AI-native test platforms.

**[Lead] tags:** Apply to: ADRs, standards governance, cross-team decisions, platform roadmap, leadership presentations.

**Metrics to include:** Standards adoption rate across teams, framework duplication reduction, CI test stage duration trends across teams, AI tooling adoption rate.

**Seniority modifiers:**

- **Junior:** Not typical for this role; if encountered, embed with one team initially; defer cross-team ADRs and standards governance to Phase 2; provide explicit mentorship framing.
- **Mid:** Standard plan as described — owns architecture decisions for assigned scope, produces ADRs, drives standards rollout across teams.
- **Senior:** Expected to independently shape the organization's testing platform vision; present roadmap to CTO-level leadership; drive build-vs-buy decisions for AI-native test infrastructure from Phase 1.

---

## QA Analyst (Manual or Transitioning to Automation)

**Core emphasis:** Risk-based test design, exploratory testing, acceptance testing, defect quality, gradual automation ramp-up.

**Phase 1 adaptations:**

- Landscape section: "Existing Testing Landscape" — understand current manual testing practices, test management tools, defect tracking
- Environment Setup: access to test environments, test management tool, defect tracker

**Phase 2 adaptations:**

- Week 3 title: "Test Design, Exploratory Testing & Tooling"
- Key subsections: Risk-based test case design, exploratory testing charters, boundary/equivalence analysis, defect reporting standards
- If transitioning to automation: introduce basic scripting (low-code tools or recorded tests) as a ramp — do not jump to full framework setup
- Week 4 title: "Coverage Expansion & Collaboration"
- Key subsections: Acceptance testing alignment with product, regression test library, exploratory testing sessions with the team

**Phase 3 adaptations:**

- Stabilize: test library health, coverage gaps, defect escape root cause analysis
- Scale: automation ramp-up plan (if transitioning), contribution to test strategy, identify exploratory testing patterns to formalize

**AI-driven testing:** Introductory level only. Focus on: using LLMs to generate test cases from user stories, using AI to identify missing test scenarios. Do not include framework-level AI detail.

**[Lead] tags:** Not applicable for this role.

**Sections to adapt:**

- "Test Strategy Draft" → "Test Design Approach" — test case structure, coverage criteria, exploratory testing charters
- "CI/CD Integration" — omit or defer to Phase 3 if transitioning

**Metrics to include:** Test coverage (% of user stories with test cases), defect detection rate, escaped defects, defect report quality score, exploratory session findings per sprint.

**Seniority modifiers:**

- **Junior:** Extend orientation to 3 weeks; pair with a senior QA or developer; focus Phase 1 deliverable on a test case library for the top 3 user journeys rather than a full strategy; defer exploratory testing ownership.
- **Mid:** Standard plan as described — owns test design, defect quality, and coverage for assigned areas; collaborates on strategy.
- **Senior:** Expected to define the test design approach and coverage strategy for the team; mentor junior QA; lead exploratory testing sessions; propose automation ramp-up plan from Phase 2.

---

## Performance / Load Testing Engineer

**Core emphasis:** Non-functional testing strategy, tool setup, baseline definition, SLO/SLA identification, CI performance gates.

**Phase 1 adaptations:**

- Landscape section: "Performance & Non-Functional Landscape" — assess existing performance tests, SLOs/SLAs, known bottlenecks, infrastructure setup
- Environment Setup: access to staging/performance environment, monitoring tools (APM, logs, dashboards)

**Phase 2 adaptations:**

- Week 3 title: "Performance Tooling Setup & Baseline Definition"
- Key subsections: Tool selection (k6, Gatling, JMeter, Locust, or equivalent), test environment validation for load testing, baseline scenario design (smoke load, average load, stress, spike, soak)
- Week 4 title: "CI Integration & Stakeholder Alignment on SLOs"
- Key subsections: Define SLOs/SLAs with product and engineering, integrate performance gates into CI pipeline, set up result dashboards (Grafana, Datadog, etc.)

**Phase 3 adaptations:**

- Stabilize: run full performance suites against the current build, analyze bottlenecks, produce a baseline report
- Scale: expand scenario coverage, integrate into release process, produce performance regression benchmarks

**AI-driven testing:** Technical section. Focus on: AI-assisted load scenario generation from usage patterns, LLM-assisted analysis of performance test results to surface anomalies and root causes.

**[Lead] tags:** Apply to: SLO negotiation with stakeholders, tooling decisions, CI gate policy.

**Sections to adapt:**

- "Test Strategy Draft" → "Performance Testing Strategy" — test types (load, stress, soak, spike), tool decisions, environment requirements, SLO definitions
- "Test Plan Components Reference" → "Performance Test Plan Reference" — scenario design, environment validation, result thresholds, reporting format

**Metrics to include:** p50/p95/p99 response time baseline, throughput (requests/sec), error rate under load, CI performance gate pass rate, infrastructure resource utilization under peak load.

**Seniority modifiers:**

- **Junior:** Extend tool setup to 3 weeks; pair with a developer or SRE for environment validation; scope Phase 1 deliverable to a single baseline scenario (smoke load only); defer SLO negotiation to a senior engineer.
- **Mid:** Standard plan as described — owns tool setup, baseline definition, and CI integration; SLO negotiation is collaborative.
- **Senior:** Expected to drive SLO/SLA negotiation independently, own the full performance test strategy from Phase 1, and present performance risk findings to engineering leadership.
