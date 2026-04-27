# 90-Day Onboarding Plan: Senior QA Automation Lead

## Overview

This plan covers the first 90 days for a Senior QA Automation Lead joining a high-traffic e-commerce platform operating under PCI compliance, with a microservices architecture and no existing QA function. You are the first QA hire in a 4-person engineering team. The plan is structured in three phases — **Orient**, **Build**, and **Scale** — each roughly one month.

**This is a greenfield QA function.** Your first priority is earning trust, establishing a strategy that the team believes in, and building infrastructure that scales beyond you. You are not here to gate releases — you are here to shift quality left, build confidence in the system, and make PCI compliance and high-traffic resilience visible and measurable.

**AI-driven testing is a core investment throughout this plan.** LLMs and AI tooling will be used from the start to accelerate coverage, identify risks, and reduce manual overhead in a lean team.

> Items marked `[Lead]` reflect your authority, influence, and stakeholder responsibilities as a Senior Lead.

---

## Guiding Principles

- **Listen before you build.** The first two weeks are about understanding — don't propose solutions before you understand constraints.
- **Earn trust through early wins.** Identify one high-visibility quality problem in Week 1 and solve it visibly.
- **PCI first.** Understand PCI DSS scope on Day 1. Every test strategy decision must account for cardholder data flows and compliance audit requirements.
- **Design for microservices.** Service-level and contract testing are not Phase 3 items — they must be part of your strategy from Day 30.
- **High-traffic = performance is a quality requirement.** Load and performance testing is a first-class citizen, not an afterthought.
- **Invest in AI-driven testing.** Treat AI tooling as a core productivity multiplier for a single-person QA function in a 4-person team.
- **Document as you go.** With no existing QA function, your documentation is the institutional memory.
- **Quality is the team's job.** Your role is to enable developers to own quality alongside you — not to own it alone.

---

## Phase 1 — Orient & Discover (Weeks 1–4)

**Goal:** Build deep context about the product, team, microservices architecture, and PCI scope. Produce a tested, signed-off QA strategy before writing a single production test.

---

### Day 1–2: First Steps

- [ ] Complete HR and IT onboarding: accounts, credentials, VPN, required security training.
- [ ] Request access upfront: GitHub repository access, GitHub Actions, staging environment credentials, PostgreSQL read-only access, API documentation, PCI-relevant system documentation (data flow diagrams, scoping documentation), Jira/project tracker, and team communication channels.
- [ ] Introduce yourself to each of the 4 developers — schedule a short 1:1 with each in Week 1.
- [ ] Ask your manager: _"What does success look like at 30, 60, and 90 days? What quality problem keeps you up at night?"_
- [ ] Locate the PCI DSS compliance documentation and identify who owns compliance responsibility.
- [ ] Find out where product requirements, API documentation, and architecture diagrams live.
- [ ] Add all team ceremonies to your calendar.

---

## Week 1: Orientation & Discovery

**Goal:** Understand the team, product, architecture, PCI scope, and current quality landscape from scratch.

### People & Culture

- [ ] Complete all administrative and security onboarding — pay particular attention to PCI-mandated security training and acceptable use policies.
- [ ] 1:1 with each of the 4 developers: understand their role, what they build, what quality problems frustrate them most, and what testing they currently do.
- [ ] 1:1 with the Engineering Manager / Product Owner: understand business priorities, the release cadence, upcoming features, and the compliance calendar.
- [ ] Understand team rituals: standups, sprint planning, retrospectives, code review processes. Identify where quality touchpoints currently exist (or don't).
- [ ] `[Lead]` Clarify your scope of authority: what tooling and process decisions are yours, what requires consensus, and what requires leadership sign-off (especially for PCI-relevant tooling).

### Product & Domain

- [ ] Review all available product documentation: user stories, acceptance criteria, architecture diagrams, API specs (FastAPI OpenAPI docs), and design specs.
- [ ] Map the core e-commerce user journeys: browse → search → product detail → add to cart → checkout → payment → order confirmation → order management.
- [ ] Understand the cardholder data flow: where does payment data enter the system, how is it handled, and what is in and out of PCI scope?
- [ ] Identify the highest-risk business flows (checkout, payment processing, order fulfilment) and the highest-traffic paths.
- [ ] Review the product roadmap for the next quarter — understand which upcoming features will require new test coverage.

### Existing QA Landscape

- [ ] Confirm there is no existing test suite, test plan, or QA process — document the baseline explicitly.
- [ ] Review the GitHub Actions configuration: understand what automated checks (linting, unit tests, type checks) already exist in CI.
- [ ] Identify any developer-written tests (pytest, Jest): assess coverage, quality, and patterns.
- [ ] Understand how defects are currently found and reported — is it all reactive (production bugs) or are any caught before release?
- [ ] Review recent production incidents or bug reports to understand where failures have occurred historically.

### Environment Setup

- [ ] Set up your local development environment: Node.js/Next.js frontend, Python/FastAPI backend, PostgreSQL database.
- [ ] Confirm you can run the application locally end-to-end.
- [ ] Map the available environments: local, staging, pre-production, production. Document what exists, who owns each, and what data it contains — particularly whether any environment contains real cardholder data (it should not).
- [ ] Understand the GitHub Actions pipeline structure: what triggers it, what it does, and where tests would be integrated.

**Phase 1 Early Deliverable (End of Week 1–2):** A written QA current-state assessment covering: existing test coverage, PCI scope summary, known quality gaps, high-risk user journeys, environment inventory, and open questions — shared with your manager.

---

## Week 2: Assessment & Strategy

**Goal:** Define the testing strategy with PCI compliance and microservices as first-class constraints. Select tooling and produce a draft Test Strategy.

### Risk & Coverage Analysis

- [ ] Map all product features against business risk (impact × likelihood of failure). Weight checkout, payment flows, and cardholder data handling at maximum risk.
- [ ] Define the testing scope by layer: UI/E2E (Next.js flows), API (FastAPI endpoints), service-level/contract (microservices), database (PostgreSQL schema and data integrity), performance (high-traffic scenarios), security (PCI-relevant).
- [ ] Identify PCI DSS test requirements: input validation, authentication, session management, TLS/HTTPS enforcement, sensitive data masking in logs and test outputs, audit logging.
- [ ] Assess test data requirements: define which test data is needed, confirm no real cardholder data will ever be used in tests, and identify how to generate synthetic card data for payment flow testing.
- [ ] Identify microservices dependencies: which services does each test flow cross, and where are the integration seams most fragile?

### Test Environment Strategy

- [ ] Define where automated tests will run: on PR (smoke only), on merge to main (full smoke + regression), and on a nightly schedule (extended regression + performance).
- [ ] Confirm the staging environment is isolated from production and contains no real cardholder data.
- [ ] Identify risks: shared staging environment, dependency on third-party payment processors (Stripe, Adyen, etc.), microservices availability. Propose mitigations: API mocking for payment providers, containerised environment for integration tests, test data seeding scripts.
- [ ] `[Lead]` Define environment promotion gates: what must pass before code promotes from staging to pre-production, and from pre-production to production.
- [ ] Document the test environment strategy — environment instability is the most common automation blocker on a greenfield project.

### AI-Driven Testing Strategy

- [ ] Evaluate LLMs for test design and automation support: GitHub Copilot for script writing, ChatGPT/Claude for test case generation from FastAPI OpenAPI specs and Next.js user stories.
- [ ] Identify where AI adds the most immediate value in a lean 4-person team: generating test cases from the OpenAPI spec, writing pytest fixtures, generating Playwright page objects from Next.js component structure.
- [ ] Evaluate AI-native testing tools for e-commerce context: Octomind, Testim, or Mabl for UI regression; assess their PCI-readiness (data handling, where test data is sent).
- [ ] Define AI guardrails for PCI context: AI tools must never have access to real cardholder data or production credentials. Document this as a hard constraint.
- [ ] `[Lead]` Make the business case for GitHub Copilot licences for the full team — a 4-person team with no QA budget has high leverage from shared AI tooling.
- [ ] Begin building a prompt library: document initial prompts for generating FastAPI test cases, Playwright flows for e-commerce journeys, and edge case identification for payment flows.

### Test Strategy Draft

- [ ] Define the test pyramid for this stack: heavy API/integration layer (FastAPI + microservices), lean E2E layer (critical e-commerce flows only), strong contract testing between services.
- [ ] Define automation scope: what will be automated (all critical paths, all API contracts, PCI-relevant flows), what will remain exploratory (UX edge cases, new feature acceptance).
- [ ] Define the browser matrix: modern Chrome and Firefox at minimum; mobile viewport for e-commerce (significant mobile traffic expected on a high-traffic platform).
- [ ] Define the smoke suite: the minimum set of tests that must pass before any deployment — checkout flow, payment processing, user authentication, order confirmation.
- [ ] `[Lead]` Draft the formal Test Strategy document and schedule a review session with the team and manager.

### Tooling Evaluation & Selection

- [ ] **UI/E2E:** Playwright — optimal for Next.js, strong network interception for mocking payment APIs, excellent CI/GitHub Actions integration.
- [ ] **API testing:** pytest + httpx for FastAPI; consider Schemathesis for property-based API testing against the OpenAPI spec.
- [ ] **Contract testing:** Pact — critical for microservices; ensures service interfaces remain compatible as services evolve independently.
- [ ] **Performance testing:** k6 — lightweight, GitHub Actions-native, excellent for defining and enforcing SLOs on high-traffic flows.
- [ ] **Reporting:** Allure for test results; integrate failure notifications into team Slack/communication channel.
- [ ] `[Lead]` Document tooling decisions with rationale — this becomes the record for future team members and compliance audits.

### Planning

- [ ] Prioritise the first batch of test automation: smoke suite for checkout and payment flows first.
- [ ] Create a test backlog in Jira/the project tracker — link test scenarios to user stories.
- [ ] `[Lead]` Estimate effort for framework setup and initial automation milestones — communicate timeline to the Engineering Manager.

**Phase 1 Deliverable (Day 30):** Test Strategy document — objective, scope, risk analysis, tool decisions, test types, PCI constraints, environment strategy, AI tooling plan, browser matrix, and reporting approach — reviewed and signed off by the team and manager.

---

## What Good Looks Like at 30 Days

At the 30-day mark, you should feel confident that:

- You understand the e-commerce product, the microservices architecture, and the PCI compliance scope in enough depth to reason about risk.
- You have built genuine working relationships with all 4 developers and have credibility as a quality partner, not a gatekeeper.
- The team has reviewed and signed off on the Test Strategy — quality direction is agreed, not imposed.
- You have identified the most critical payment and checkout flows and have a concrete automation plan for them.
- You understand where the PCI audit trail requirements intersect with automated testing.
- You have not yet written much production automation code — and that is intentional. Strategy and relationships come first.

---

## Phase 2 — Build & Integrate (Weeks 5–8)

**Goal:** Build the automation framework, deliver coverage across the highest-risk flows, integrate testing into CI/GitHub Actions, and embed quality into the team's daily workflow.

---

## Week 3: Framework Architecture & Standards

### Framework Setup

- [ ] Set up Playwright in the repository with a clean, scalable project structure: `tests/e2e/`, `tests/api/`, `tests/contracts/`, `fixtures/`, `helpers/`.
- [ ] Configure Playwright for Next.js: base URL, environment-aware configuration, auth state management (avoid re-authenticating on every test).
- [ ] Set up pytest for FastAPI API tests: fixtures for database seeding, test client setup, environment variable management.
- [ ] Configure Pact for contract testing: provider and consumer definitions for each microservice boundary.
- [ ] Set up test data management: synthetic card data generators, PostgreSQL seed scripts, fixture files for common test states.
- [ ] Configure the GitHub Actions workflow: smoke tests on every PR, full regression on merge to main, nightly scheduled run for extended coverage.
- [ ] Set up Allure reporting and integrate test result notifications into the team Slack channel.
- [ ] `[Lead]` Define and document contribution guidelines: folder structure, naming conventions, fixture patterns, and the code review expectation for tests.

### AI-Assisted Test Development

- [ ] Generate an initial test case set from the FastAPI OpenAPI spec using an LLM — treat the output as a draft requiring review, not a finished product.
- [ ] Use GitHub Copilot to accelerate writing Playwright page objects for the checkout and payment flows; review all AI-generated code for correctness and PCI-safe patterns (no hardcoded credentials, no real card data).
- [ ] Use LLMs to identify edge cases and negative scenarios for the payment flow: declined cards, network timeouts, duplicate submissions, session expiry during checkout.
- [ ] Expand the prompt library: document prompts for FastAPI test generation, Playwright e-commerce flows, and edge case generation for PCI-relevant scenarios.
- [ ] `[Lead]` Present the AI tooling workflow to the team — demonstrate how Copilot accelerates test writing and invite developers to adopt the same prompting patterns in their own tests.

### PCI-Compliant Test Implementation

- [ ] Implement smoke tests: checkout flow (guest and authenticated), payment processing (mocked payment provider), order confirmation, user authentication.
- [ ] Implement PCI-specific test cases: TLS enforcement, sensitive data not appearing in logs or responses, session invalidation on logout, input validation on payment fields.
- [ ] Establish test patterns that enforce PCI safety: no real card data in fixtures, synthetic card numbers only (Stripe test cards or equivalent), secrets from environment variables never hardcoded.
- [ ] Conduct a code review of the initial test suite with a developer — set the security and quality bar early.

**Week 3 Deliverable:** Working Playwright and pytest framework in the repository. Smoke tests passing in GitHub Actions CI. PCI test safety patterns documented and enforced.

---

## Week 4: Team Enablement & Stakeholder Integration

### Team Enablement

- [ ] Walk the 4 developers through the framework: how to run tests locally, how to add tests for a new feature, and how to interpret CI results.
- [ ] Integrate testing into the Definition of Done: new features require a test scenario documented and ideally automated before the story is marked complete.
- [ ] Set up a lightweight developer contribution process: a test template, a checklist in the PR template, and an offer to pair with developers writing their first tests.
- [ ] `[Lead]` Run a **mob testing session** on the checkout flow — the entire team explores the flow together, surfacing edge cases and defects collaboratively. Capture findings in the test backlog.
- [ ] Begin a regular exploratory testing cadence — one focused session per sprint targeting the highest-risk or newest features.

### Contract Testing & API Coverage

- [ ] Implement Pact contract tests for the highest-priority microservice boundaries — focus on services involved in the checkout and payment flows.
- [ ] Extend pytest API coverage: request/response schema validation, authentication and authorisation checks, error handling (400/401/403/500 responses), rate limiting behaviour under high traffic.
- [ ] Add database integrity tests: schema validation on migrations, data integrity checks for order and payment records, no orphaned records after failed transactions.

### Stakeholder Reporting

- [ ] `[Lead]` Establish a lightweight QA reporting cadence: a brief weekly summary to the Engineering Manager covering coverage progress, CI pass rates, defects found, and any PCI-relevant findings.
- [ ] `[Lead]` Define release readiness criteria: what must pass before each production release — smoke suite green, no open P1 defects, PCI-relevant tests passing, no known regressions.

**Phase 2 Deliverable (Day 60):** Working automation framework in GitHub Actions CI with: smoke suite, API and contract tests, PCI compliance test cases, and developer contribution guidelines in place. The team can run, read, and contribute to tests independently.

---

## What Good Looks Like at 60 Days

At the 60-day mark, you should feel confident that:

- The automation suite is live in CI and catching real issues before they reach production.
- The 4 developers understand the framework and are beginning to contribute tests as part of feature development.
- PCI-relevant test cases are implemented, documented, and integrated into CI.
- Contract tests are covering the highest-risk microservice boundaries.
- AI tooling is actively saving you time on test design and script generation.
- You have a clear picture of remaining coverage gaps and a prioritised backlog.

---

## Phase 3 — Stabilize & Scale (Weeks 9–12)

**Goal:** Mature the QA function, harden reliability, extend into performance testing, deepen AI integration, and establish the QA roadmap for the next quarter.

---

## Week 5–6: Stabilize & Deepen

### Regression & Reliability

- [ ] Execute full regression suites against the current build — triage and resolve all failures systematically.
- [ ] Audit for flaky tests: identify root causes (timing issues, shared test data, environment instability, payment mock latency) and fix them.
- [ ] Validate suite consistency: do tests produce the same results in CI as locally?
- [ ] Review contract test health across all microservice boundaries — identify any contracts that are stale or no longer enforced.
- [ ] `[Lead]` Conduct a framework quality audit: are contribution guidelines being followed? Are naming conventions consistent? Is test data management safe and PCI-compliant throughout?

### Performance Testing Foundations

- [ ] Set up k6 for performance testing against the staging environment.
- [ ] Define SLOs for critical e-commerce flows with the Engineering Manager and Product Owner: checkout response time, payment processing time, product search latency under load, and order submission throughput.
- [ ] Design baseline load scenarios: smoke load (1–5 concurrent users), average load (typical traffic profile), stress test (peak e-commerce traffic — e.g., promotional events), spike test (sudden traffic surge).
- [ ] Run baseline performance tests and document results — establish the benchmark before any optimization conversation.
- [ ] Integrate a lightweight performance gate into the GitHub Actions pipeline: fail CI if critical response times exceed agreed thresholds.

### Advanced AI Integration

- [ ] Use LLMs to analyze test failure logs from CI — surface patterns: are failures correlated with specific services, environments, or code changes?
- [ ] Experiment with AI-assisted test prioritization: use risk signals (code change volume, business criticality) to identify the highest-value tests for each build.
- [ ] Evaluate AI-assisted test maintenance: when a Next.js component or FastAPI endpoint changes, use LLMs to identify which tests need updating.
- [ ] `[Lead]` Assess the ROI of current AI tooling investment: time saved on test case generation, defects found earlier, coverage improvement rate. Prepare a brief summary for leadership.

---

## Week 7–8: Scale & Future Planning

### Documentation, Knowledge Sharing & Feedback

- [ ] Collect structured feedback from the 4 developers: what works, what is friction, what is missing in the QA process?
- [ ] Finalize and publish all QA documentation: framework guide, test plan, contribution guidelines, naming conventions, PCI test safety rules, and the environment strategy document.
- [ ] Add QA onboarding documentation to the team knowledge base — the next developer joining should be able to understand the QA function from documentation alone.
- [ ] `[Lead]` Present a 90-day QA progress summary to leadership: coverage achieved, defects prevented, CI integration status, PCI test coverage, performance baselines, AI tooling ROI, and the roadmap ahead.

### Future Planning

- [ ] Identify remaining coverage gaps and reprioritize them for the next quarter: accessibility testing (WCAG compliance for e-commerce), visual regression for the product catalogue and checkout UI, security testing beyond PCI basics (OWASP Top 10 relevant to e-commerce).
- [ ] Propose the next QA investment wave: exploratory security testing, chaos/resilience testing for microservices, expanded performance test suite covering seasonal traffic peaks.
- [ ] Define a roadmap for deepening AI-driven testing: automated test generation on PR, AI-powered defect prediction from code change history, LLM-assisted accessibility audit.
- [ ] Define a test suite maintenance cadence: quarterly review, coverage gap analysis, retirement of obsolete tests.
- [ ] `[Lead]` Assess whether QA capacity needs to grow: a 4-person team with PCI obligations and high-traffic concerns may need a second QA Automation Engineer within 6 months. Prepare a business case if warranted.
- [ ] `[Lead]` Define team-level quality OKRs for the next quarter, tied to the success metrics below, and share them with the Engineering Manager.

**Phase 3 Deliverable (Day 90):** 90-day QA retrospective and roadmap for the next quarter — presented to the team and leadership. Includes: coverage summary, PCI test coverage status, performance baselines, AI tooling ROI, and prioritised next investments.

---

## What Good Looks Like at 90 Days

At the 90-day mark, you should feel confident that:

- Quality is a visible, measurable part of the team's Definition of Done — not an afterthought.
- The automation suite is stable, trusted, and actively preventing regressions on every PR.
- PCI-relevant test cases are documented, automated, and integrated into CI — audit-ready.
- Performance baselines are established and SLOs are defined and monitored.
- Contract tests are covering the critical microservice boundaries, preventing integration breakages.
- AI-driven testing is saving real time and improving coverage quality for a lean team.
- The 4 developers are engaged with the testing process and contributing tests as part of feature development.
- Stakeholders see QA as a quality partnership, not a release bottleneck.
- You have a clear, realistic roadmap for the next quarter and leadership is aligned on it.

---

## Key Deliverables Summary

| Phase   | Milestone       | Deliverable                                                                                         |
| ------- | --------------- | --------------------------------------------------------------------------------------------------- |
| Phase 1 | End of Week 1–2 | QA current-state assessment: coverage gaps, PCI scope, environment inventory, open questions        |
| Phase 1 | Day 30          | Test Strategy document: tool decisions, PCI constraints, environment strategy, AI plan — signed off |
| Phase 2 | Week 3          | Framework live in CI with smoke tests and PCI-compliant test patterns                               |
| Phase 2 | Day 60          | Smoke, API, contract, and PCI tests in CI; developer contribution guidelines in place               |
| Phase 3 | Day 90          | 90-day retrospective + QA roadmap: performance baselines, AI ROI, next quarter priorities           |

---

## Success Metrics

| Metric                          | Description                                                      | Indicative Target                                                     |
| ------------------------------- | ---------------------------------------------------------------- | --------------------------------------------------------------------- |
| **Automation Coverage**         | % of identified test scenarios automated                         | >50% by Day 60; >75% by Day 90                                        |
| **Smoke Suite Pass Rate**       | % of smoke tests passing on each build                           | >98% — near-zero tolerance for broken smoke                           |
| **Regression Suite Pass Rate**  | % of regression tests passing before each release                | >95%                                                                  |
| **PCI Test Coverage**           | % of PCI-relevant flows covered by automated tests               | 100% of in-scope flows by Day 90                                      |
| **Contract Test Coverage**      | % of microservice boundaries covered by Pact contracts           | All checkout/payment-path services by Day 60; full coverage by Day 90 |
| **Defect Detection Rate**       | Defects found by QA before production                            | Trending upward month-over-month                                      |
| **Escaped Defects**             | Defects found in production that QA should have caught           | Trending toward zero                                                  |
| **Flaky Test Rate**             | % of tests producing inconsistent results                        | <5%; resolve any test with >10% flake rate immediately                |
| **CI Test Stage Duration**      | Time for the automated test stage to complete                    | Establish baseline; optimize if smoke suite exceeds 8 minutes         |
| **Performance SLO Adherence**   | % of builds where critical flows meet defined SLO thresholds     | Establish baseline by Day 75; set target once baseline exists         |
| **Developer Contribution Rate** | % of new feature stories delivered with accompanying tests       | >50% by Day 90                                                        |
| **AI-Assisted Coverage Gain**   | % of test cases initially drafted or improved with AI assistance | Track to quantify ROI; target >30% of new tests by Day 90             |

---

## Ongoing Practices

- **Participate in sprint ceremonies** — Engage in planning and refinement to surface testability concerns before development begins.
- **Review requirements early** — Identify ambiguities, missing edge cases, and PCI implications in user stories before they are built.
- **Maintain PCI compliance hygiene** — Regularly verify that no real cardholder data exists in test environments or test data files. Treat this as a standing obligation, not a one-time check.
- **Continuously evolve AI usage** — Reassess AI tools and prompting strategies quarterly; the tooling landscape changes rapidly.
- **Maintain the test suite** — Review, refactor, and retire outdated tests quarterly. An unmaintained suite becomes a liability, especially across a microservices architecture.
- **Track and share metrics** — Report QA metrics in sprint reviews or a shared dashboard to make testing impact visible.
- **Advocate for testability** — Provide feedback on FastAPI endpoint design, microservice interface contracts, and Next.js component structure to make the product easier to test and easier to keep compliant.
- **Stay current** — Follow developments in Playwright, k6, Pact, AI-assisted testing, PCI DSS updates, and OWASP e-commerce guidance.

---

## Test Plan Components Reference

When finalising your Test Plan (Phase 1, Day 30), ensure it covers:

- **Objective** — Establish a QA function from scratch for a PCI-compliant, high-traffic e-commerce platform.
- **Scope** — All e-commerce flows with emphasis on checkout, payment, and cardholder data handling; all FastAPI microservice boundaries; Next.js UI critical paths.
- **Test Types** — Smoke, regression, API, contract (Pact), database integrity, performance (k6), PCI compliance, exploratory, security (OWASP basics).
- **Browser / Device Matrix** — Chrome and Firefox (latest); mobile viewport (375px minimum) — e-commerce platforms have high mobile traffic.
- **Test Environment Strategy** — Staging environment isolation, no real cardholder data policy, synthetic card data only, payment provider mocking strategy, microservices availability management.
- **Data Handling Strategy** — Synthetic card data (Stripe test cards or equivalent), `.env` for all credentials, no secrets in test code, PostgreSQL seed scripts for consistent test state.
- **PCI Compliance Test Coverage** — TLS enforcement, sensitive data masking, session management, input validation, audit logging verification.
- **AI Tooling Plan** — GitHub Copilot for scripting, LLMs for test case generation from OpenAPI spec; PCI guardrails on AI tool data access.
- **Defect Management** — Jira for defect tracking, P1 (production blocker), P2 (regression), P3 (edge case); P1 defects block release.
- **Reporting** — Allure for test results, Slack notifications for CI failures, weekly QA summary to Engineering Manager.
- **CI/CD Integration** — Smoke on PR, full regression on merge to main, extended + performance nightly in GitHub Actions.
- **Release Gate Criteria** — Smoke suite green, no open P1 defects, PCI tests passing, no known regressions since last release.
