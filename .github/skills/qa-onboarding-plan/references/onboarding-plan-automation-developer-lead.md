# 90-Day Onboarding Plan: Software QA Automation Developer / Lead

## Overview

This plan covers the first 90 days for a Software QA Automation Developer or Lead joining any organization — whether or not a QA function already exists. It is structured in three phases — **Orient**, **Build**, and **Scale** — each roughly one month. Timelines are guidelines, not hard deadlines; adjust based on team size, product maturity, and existing QA infrastructure.

**AI-driven testing is a core investment throughout this plan.** Modern automation roles increasingly rely on LLMs and AI tooling to accelerate test design, improve coverage, and reduce maintenance overhead. This plan treats AI-assisted testing not as a future nice-to-have, but as a capability to build from the start and deepen over 90 days.

> **How to use this plan:** This is a living document. Review and adjust it at each phase boundary. Items marked with `[Lead]` are particularly relevant if you are in a lead or senior capacity.

---

## Guiding Principles

- **Listen before you act.** Invest the first two weeks in understanding — people, product, and process — before proposing solutions.
- **Deliver early wins.** Identify small, visible contributions in the first month to build credibility.
- **Shift quality left.** Integrate testing into the development workflow; quality is not a gate at the end of a sprint.
- **Invest in AI-driven testing.** Treat LLMs and AI tooling as first-class members of your QA workflow — for test design, generation, code writing, and maintenance.
- **Document as you go.** Knowledge captured early prevents blind spots later.
- **Communicate progress.** Regular, transparent updates build trust with stakeholders and teammates.
- **Advocate for quality culture.** QA is a shared team responsibility, not a single person's job.

---

## Phase 1 — Orient & Discover (Weeks 1–4)

**Goal:** Build deep context about the organization, product, team, and existing QA landscape. Produce a tested strategy before writing a single production test.

---

### Day 1–2: First Steps

The first two days are about logistics and first impressions — not automation. Prioritize access and relationships.

- [ ] Complete HR and IT onboarding: accounts, credentials, VPN, required software.
- [ ] Request access upfront: version control, CI/CD system, project management tool, test environments, staging credentials, and shared documentation (Confluence, Notion, etc.).
- [ ] Introduce yourself to every team member — even a short virtual coffee matters.
- [ ] Ask your manager: _"What does success look like at 30, 60, and 90 days?"_
- [ ] Find out where requirements, designs, and technical documentation live.
- [ ] Identify key ceremonies and add them to your calendar.

---

## Week 1: Orientation & Discovery

**Goal:** Understand the organization, product, team dynamics, and existing QA landscape.

### People & Culture

- [ ] Complete administrative and HR onboarding (access, accounts, tools, policies).
- [ ] Meet individually with key stakeholders: Engineering Manager, Product Owner/Manager, UX Designer(s), and representative developers.
- [ ] Understand team rituals: stand-ups, sprint planning, retrospectives, code review processes.
- [ ] Identify who to go to for decisions, blockers, and technical questions.
- [ ] `[Lead]` Clarify your scope of authority: what decisions are yours vs. collaborative vs. escalated.

### Product & Domain

- [ ] Review available product documentation: PRDs, user stories, architecture diagrams, design specs.
- [ ] Understand the product's target users, core use cases, and key user journeys.
- [ ] Review the product roadmap — understand what is built, what is in progress, and what is planned.
- [ ] Identify the most business-critical features and highest-risk areas of the product.

### Existing QA Landscape

- [ ] Assess the current state of testing: What exists? Manual only? Some automation? No QA function?
- [ ] Identify any existing test cases, test plans, or automation scripts.
- [ ] Understand how defects are currently tracked and reported.
- [ ] Review the CI/CD pipeline and understand where (if anywhere) testing is integrated.

### Environment Setup

- [ ] Set up your local development and testing environment end-to-end (including being able to run the application locally).
- [ ] Understand the available test environments: local, staging, pre-production, ephemeral (PR-based). Document what exists and what is missing.
- [ ] Familiarize yourself with the technology stack in enough depth to write and debug tests.

**Phase 1 Early Deliverable (End of Week 1–2):** A written QA current-state assessment — what exists, key gaps, initial observations, and open questions — shared with your manager.

---

## Week 2: Assessment & Strategy

**Goal:** Define the testing strategy, select tooling, and produce a test plan draft.

### Risk & Coverage Analysis

- [ ] Map application features against business risk (impact × likelihood of failure).
- [ ] Identify types of testing needed: UI/E2E, API, integration, unit, performance, accessibility, visual regression, security.
- [ ] Identify data handling requirements: test data sources, sensitive/secure data (`.env`, secrets management), API mocking needs, fixtures (JSON/CSV).
- [ ] Assess database testing needs: schema changes, data migrations, data integrity checks.

### Test Environment Strategy

- [ ] Define where automated tests will run: local only, CI on PR, CI on merge, scheduled nightly, or all of the above.
- [ ] Determine whether a dedicated staging environment exists and whether it is stable enough for automation.
- [ ] Identify risks: shared environments, flaky test data, external service dependencies. Propose mitigations (e.g., API mocking, containerized environments, seed scripts).
- [ ] Document the test environment strategy — this is a common blocker if left undefined early.

### AI-Driven Testing Strategy

- [ ] Evaluate LLMs available for test design and automation (e.g., GitHub Copilot, ChatGPT, Claude) — assess how they can generate test cases from requirements, user stories, and API schemas.
- [ ] Evaluate AI-native testing tools where applicable (e.g., Octomind, Testim, Mabl) and assess fit with the technology stack.
- [ ] Identify where AI adds the most value in your specific context: test case generation, edge case identification, code writing, result analysis, or test maintenance.
- [ ] Identify where AI is not yet reliable enough to trust without review — and establish review checkpoints.
- [ ] Define how AI assistance will be integrated into the QA workflow as a standard practice.
- [ ] `[Lead]` Advocate for AI tooling access if not already available (e.g., GitHub Copilot licences, LLM API access). Make the business case with concrete examples.

### Test Strategy Draft

- [ ] Define the **test pyramid** approach appropriate for the product (unit / integration / E2E ratio).
- [ ] Define scope: what will and will not be automated, and why.
- [ ] Define the device/browser matrix for UI testing.
- [ ] Define smoke test suite scope (minimal set to verify core product health).
- [ ] Define regression test suite scope.
- [ ] `[Lead]` Draft a formal Test Strategy document and schedule a review with the team.

### Tooling Evaluation & Selection

- [ ] Evaluate automation framework options based on the tech stack (e.g., Playwright, Cypress, Selenium, Jest, Vitest, Puppeteer).
- [ ] Evaluate API testing tools (e.g., Supertest, Postman/Newman, REST Assured).
- [ ] Evaluate test reporting options (e.g., Allure, HTML reports, dashboard integrations).
- [ ] Evaluate CI/CD integration options (e.g., GitHub Actions, GitLab CI, Jenkins, CircleCI).
- [ ] Select tooling and document the rationale.

### Planning

- [ ] Prioritize the first batch of automated test cases — focus on smoke tests and the most critical user flows.
- [ ] Create a backlog of test scenarios tied to product features.
- [ ] `[Lead]` Estimate effort for framework setup and initial automation coverage.

**Phase 1 Deliverable (Day 30):** Test Strategy document — objective, scope, tool decisions, test types, environment strategy, AI tooling plan, device matrix, and reporting approach — reviewed and signed off by the team.

---

## What Good Looks Like at 30 Days

At the 30-day mark, you should feel confident that:

- You understand the product well enough to reason about risk and test coverage.
- You have built genuine working relationships with engineering, product, and design.
- The team understands your strategy and supports the direction.
- You know where the biggest quality gaps are and have a concrete plan to address them.
- You have not yet written much production automation code — and that is intentional. Strategy before scripts.

---

## Phase 2 — Build & Integrate (Weeks 5–8)

**Goal:** Establish the automation framework, deliver meaningful test coverage, and integrate testing into the team's daily workflow.

---

## Week 3: Framework Setup & AI-Assisted Development

### Framework Setup (POC → Foundation)

- [ ] Set up the chosen automation framework in the repository with a clean, scalable project structure.
- [ ] Configure test runner, reporters, and environment variable management.
- [ ] Implement a basic CI pipeline trigger (e.g., run tests on pull request and on merge to main).
- [ ] Set up test data management: fixtures, factories, or database seeding strategies.
- [ ] Configure API mocking/interception where needed (e.g., `msw`, Playwright network intercept).
- [ ] Set up reporting and integrate with team communication channels (e.g., Slack failure notifications, test result dashboards).

### AI-Assisted Test Development

- [ ] Use LLMs to generate an initial set of test cases from user stories, acceptance criteria, and API documentation — treat AI output as a draft, not final truth.
- [ ] Review and validate AI-generated test cases with the team before implementing them.
- [ ] Use GitHub Copilot (or equivalent) to accelerate writing test scripts; review all AI-generated code carefully for correctness, edge cases, and maintainability.
- [ ] Use LLMs to identify negative scenarios, edge cases, and boundary conditions that manual analysis is likely to miss.
- [ ] Begin building a prompt library: document which prompts produce reliable, high-quality test outputs for your specific product and tech stack.

### First Test Scripts

- [ ] Implement smoke tests covering the most critical user flows.
- [ ] Implement initial regression tests for the highest-priority features from the risk analysis.
- [ ] Establish and enforce framework patterns: page object model (or equivalent), reusable helpers, test data separation.
- [ ] Conduct a code review of the initial scripts with a developer or peer — set the quality bar early.

**Week 3 Deliverable:** Working automation framework in the repository with smoke tests passing in CI.

---

## Week 4: Team Integration & Coverage Expansion

### Collaboration & Integration

- [ ] Walk the development team through the framework: structure, how to run tests locally, and how to contribute tests.
- [ ] Introduce testing into the definition of done for new features (if not already present).
- [ ] Begin a regular cadence of exploratory testing alongside automation — manual exploration consistently surfaces gaps that scripted tests miss.
- [ ] `[Lead]` Run a **mob testing session** — the entire team participates collectively in exploratory testing, generating diverse perspectives and surfacing defects quickly. (Reference: [Everyone's a Tester: Mob Testing](https://www.gojek.io/blog/everyones-a-tester-while-mob-testing))
- [ ] `[Lead]` Establish a lightweight process for developers to contribute tests as part of feature development.

### Expanding Coverage

- [ ] Extend API test coverage: validate request/response contracts, authentication, error handling, and edge cases.
- [ ] Add database testing where applicable: schema validation, data integrity checks, migration testing.
- [ ] Add visual regression testing if the product has a stable UI (e.g., Percy, Playwright screenshots).
- [ ] Begin tagging tests by priority tier (P1 = smoke, P2 = regression, P3 = edge case) to enable intelligent test selection in CI.

**Phase 2 Deliverable (Day 60):** Working automation framework in CI with smoke suite, initial regression tests, and API test coverage. The team can run and contribute to tests independently.

---

## What Good Looks Like at 60 Days

At the 60-day mark, you should feel confident that:

- The automation suite is live in CI and catching real issues before they reach production.
- The team is engaged with the testing process — it is not a black box owned by one person.
- You have a clear picture of coverage gaps and a prioritized backlog to address them.
- AI tooling is actively part of your workflow, saving measurable time on test design and script writing.
- Flaky tests have been identified and a remediation plan is in progress.

---

## Phase 3 — Stabilize & Scale (Weeks 9–12)

**Goal:** Mature the QA function, deepen AI integration, close coverage gaps, and establish the foundation for sustained quality at scale.

---

## Week 5–6 (within Phase 3): Stabilize & Deepen

### Regression & Reliability

- [ ] Execute full regression suites against the current build — triage and resolve failures systematically.
- [ ] Audit for flaky tests: identify root causes (timing, test data dependencies, environment instability) and fix them.
- [ ] Validate suite consistency: does the suite produce the same results in CI vs. local?
- [ ] Integrate database change testing (schema migrations, data integrity) into the release process.

### Advanced AI Integration

- [ ] Use LLMs to analyze test failure logs and surface patterns — are failures systemic or isolated?
- [ ] Experiment with AI-assisted test prioritization: use risk signals and code-change history to identify the most relevant tests for each build.
- [ ] Evaluate AI-assisted test maintenance: when the application changes, use LLMs to suggest which tests need updating and how.
- [ ] Share findings with the team — document which AI workflows are production-ready vs. still experimental.
- [ ] `[Lead]` Assess ROI of current AI tooling investment and evaluate whether deeper tooling (e.g., AI-native test platforms) is warranted.

---

## Week 7–8 (within Phase 3): Scale & Future Planning

### Feedback, Documentation & Knowledge Sharing

- [ ] Collect structured feedback from developers and the product team on the QA process.
- [ ] Finalize and publish all QA documentation: framework guide, test plan, contribution guidelines, naming conventions.
- [ ] Add QA onboarding documentation to the team knowledge base (Confluence, Notion, README).
- [ ] `[Lead]` Present a 90-day testing progress summary to leadership: coverage achieved, defects prevented, CI integration status, AI tooling ROI, and the roadmap ahead.

### Future Planning

- [ ] Identify remaining coverage gaps and reprioritize them for the next quarter.
- [ ] Propose the next wave of investment: performance testing, accessibility testing, security testing, contract testing, or chaos/resilience testing.
- [ ] Define a roadmap for deepening AI-driven testing: more sophisticated generation pipelines, autonomous test maintenance, AI-powered defect prediction.
- [ ] Establish a test suite maintenance cadence: who reviews and prunes the suite, and how often.
- [ ] `[Lead]` If QA capacity needs to grow, outline a plan for hiring, embedding QA engineers in squads, or upskilling developers as QA contributors.
- [ ] `[Lead]` Define team-level quality OKRs for the next quarter, tied to the success metrics below.

**Phase 3 Deliverable (Day 90):** 90-day retrospective and QA roadmap for the next quarter — shared with the team and leadership.

---

## What Good Looks Like at 90 Days

At the 90-day mark, you should feel confident that:

- Quality is a visible, measurable part of the team's definition of done.
- The automation suite is stable, trusted, and actively preventing regressions.
- AI-driven testing is saving real time and improving coverage quality — not just a proof of concept.
- Stakeholders see QA as a value-adding function, not a bottleneck.
- You have a clear, realistic roadmap for the next quarter and the team is aligned on it.
- You feel genuinely productive, and you have identified the areas where you still want to grow.

---

## Key Deliverables Summary

| Phase   | Milestone       | Deliverable                                                        |
| ------- | --------------- | ------------------------------------------------------------------ |
| Phase 1 | End of Week 1–2 | QA current-state assessment (written, shared with team)            |
| Phase 1 | Day 30          | Test Strategy document — reviewed and signed off                   |
| Phase 2 | Day 60          | Framework live in CI with smoke, API, and initial regression tests |
| Phase 3 | Day 90          | 90-day retrospective and QA roadmap for the next quarter           |

---

## Success Metrics

Use these metrics to track and communicate QA effectiveness. Targets are indicative — calibrate to your product's maturity and team context.

| Metric                         | Description                                                      | Indicative Target                                            |
| ------------------------------ | ---------------------------------------------------------------- | ------------------------------------------------------------ |
| **Automation Coverage**        | % of identified test scenarios automated                         | >60% by Day 60; >80% by Day 90                               |
| **Smoke Suite Pass Rate**      | % of smoke tests passing on each build                           | >98% — near-zero tolerance for broken smoke                  |
| **Regression Suite Pass Rate** | % of regression tests passing before each release                | >95%                                                         |
| **Defect Detection Rate**      | Number of defects found by QA before production                  | Trending upward month-over-month                             |
| **Escaped Defects**            | Defects found in production that should have been caught in QA   | Trending toward zero                                         |
| **Flaky Test Rate**            | % of tests producing inconsistent results                        | <5%; resolve any test with >10% flake rate immediately       |
| **CI Test Stage Duration**     | Time for the automated test stage to complete                    | Establish a baseline; optimize if smoke suite exceeds 10 min |
| **Mean Time to Fix (MTTF)**    | Average time from defect report to resolution                    | Track trend; set targets once baseline is established        |
| **AI-Assisted Coverage Gain**  | % of test cases initially drafted or improved with AI assistance | Track to quantify AI investment ROI                          |

---

---

## Ongoing Practices

These practices sustain quality beyond the first 90 days:

- **Participate in sprint ceremonies** — Stand-ups, planning, and retrospectives keep QA aligned with the development cadence.
- **Review requirements early** — Engage during story refinement to surface testability concerns and ambiguities before development begins.
- **Continuously evolve AI usage** — Regularly reassess which AI tools and prompting strategies produce reliable results; the tooling landscape changes rapidly.
- **Maintain the test suite** — Regularly review, refactor, and retire outdated tests. An unmaintained suite becomes a liability.
- **Track and share metrics** — Report QA metrics in sprint reviews or team dashboards to make testing impact visible to stakeholders.
- **Foster psychological safety around quality** — Teams surface defects earlier when they are not penalized for finding them.
- **Advocate for testability** — Provide feedback to developers on API design, application architecture, and feature design to make the product easier to test.
- **Stay current** — Follow advancements in test tooling, AI-assisted testing, and industry best practices.

---

## Test Plan Components Reference

When drafting your Test Plan (Phase 1, Week 2–3), ensure it covers the following:

- **Objective** — What the testing effort aims to achieve.
- **Scope** — What is in and out of scope.
- **Test Types** — Smoke, regression, exploratory, API, database, performance, accessibility, visual regression, security.
- **Device / Browser Matrix** — Browsers, OS versions, and devices to support.
- **Test Environment Strategy** — Where tests run, environment stability, test data management, and external dependency mocking.
- **Data Handling Strategy** — Environment variables (`.env`), fixtures (JSON/CSV), API mocking, secure data management.
- **AI Tooling Plan** — Which AI tools will be used, for what purposes, and how AI-generated outputs will be reviewed and validated.
- **Defect Management** — How defects are logged, triaged, prioritized, and tracked.
- **Reporting** — Test result dashboards, failure notifications (e.g., Slack), and release-gate criteria.
- **CI/CD Integration** — When tests run (on PR, on merge, on schedule) and what constitutes a build failure.
- **Entry / Exit Criteria** — Conditions under which testing begins and is considered complete for a release.
