# 90-Day Onboarding Plan: SDET (Software Development Engineer in Test)

## Overview

This plan covers the first 90 days for an SDET joining any engineering organization. It is structured in three phases — **Orient**, **Build**, and **Scale** — each roughly one month.

The SDET role sits at the intersection of software engineering and quality engineering. You are not a separate QA function — you are embedded in the development team, and your job is to make testability a first-class engineering property. Your leverage comes not from writing tests _in isolation_ but from raising the team's collective ability to build things that can be confidently tested and verified.

**The primary shift in mindset:** QA Automation Developers write tests _for_ the team. SDETs make the code itself _more testable_ alongside writing tests. Code review, pairing with developers, test utility design, and contract testing are as central to this role as test scripting.

> **How to use this plan:** This is a living document. Review and adjust it at each phase boundary. Because the SDET role is an individual contributor role, there are no `[Lead]`-tagged items — influence is exercised through code, pairing, and engineering conversations rather than formal authority.

---

## Guiding Principles

- **Embed, don't observe.** The SDET's value multiplies when you work _inside_ the development process — in code review, in pairing, in design conversations — not alongside it.
- **Testability is a design problem.** Many things that are hard to test are hard to test because of how they were built. The earlier you are in design conversations, the more impact you have.
- **Test utilities are production code.** Treat them with the same quality standards: reviewed, documented, and maintained.
- **Contract before implementation.** API contract tests are your fastest feedback signal on integration risk. Define them early.
- **Listen before you refactor.** There is almost always a reason legacy code is the way it is. Understand the constraints before proposing changes.
- **Influence through code.** The clearest way to show a team what "well-tested" looks like is to write it, review it, and pair on it — not to explain it in a meeting.
- **Document as you go.** Knowledge captured early becomes the onboarding guide for the next SDET, and the architecture guide for the next developer.

---

## Phase 1 — Orient & Discover (Weeks 1–4)

**Goal:** Build deep engineering and product context. Understand the codebase, the team's current testing practices, and the testability challenges you will be solving. Produce a clear Testability Assessment before writing a single production test or refactoring any existing code.

---

### Day 1–2: First Steps

The first two days are about getting your engineering environment fully operational and making your first connections — not writing code.

- [ ] Complete HR and IT onboarding: accounts, credentials, VPN, required software licences.
- [ ] Request access upfront: version control (read and write), CI/CD system, project management tool, test environments, staging credentials, shared documentation (Confluence, Notion, internal wikis), and any observability/monitoring tools (DataDog, Sentry, PagerDuty, etc.).
- [ ] Clone the primary repositories and get the application building and running locally — including any dependent services, seed data, and environment configuration. This is your first testability signal.
- [ ] Introduce yourself to every team member. Ask your direct teammates: _"What is the most painful part of testing this codebase right now?"_ — this question surfaces more useful context than any documentation.
- [ ] Ask your manager: _"What does success look like at 30, 60, and 90 days?"_
- [ ] Identify key ceremonies and add them to your calendar: standups, sprint planning, code review process, retrospectives, and any architecture or design review meetings.

---

## Week 1: Orientation & Discovery

**Goal:** Understand the engineering team, the product, the codebase, and the current state of testability.

### People & Engineering Culture

- [ ] Complete administrative and HR onboarding (accounts, tools, policies).
- [ ] Meet individually with key teammates: Engineering Manager, the developers you will be working most closely with, and any other QA or testing functions in the organization.
- [ ] Understand the team's development workflow: branching model, code review norms, PR size conventions, definition of done, and sprint cadence.
- [ ] Understand the engineering culture around quality: Do developers write unit tests? Is test coverage a PR requirement? Are tests skipped under deadline pressure? Understanding the culture tells you where resistance will come from — and where you will find allies.
- [ ] Identify who owns the CI/CD pipeline and understand the process for making changes to it.
- [ ] Identify who to go to for architecture questions, codebase history, and decisions about breaking changes.

### Product & Domain

- [ ] Review available product documentation: architecture diagrams, data flow diagrams, API documentation (OpenAPI/Swagger), and any design decision records.
- [ ] Understand the product's core user journeys and the most business-critical workflows — these map directly to your highest-priority test coverage.
- [ ] Review the product roadmap — understand what is stable, what is actively changing, and what is being built from scratch.
- [ ] Identify the areas of the product with the highest business risk (what would be catastrophic to break?). These are your contract testing anchors.

### Engineering & Testability Landscape

This is the most important section of Phase 1 for an SDET. Invest significant time here before forming any opinions about what to change.

- [ ] **Code coverage:** What is the current unit test coverage percentage? Is it tracked? Is it enforced as a CI gate? Where are the largest gaps?
- [ ] **Unit test quality:** Are existing unit tests testing behavior or implementation? Are they isolated and deterministic? How fast do they run? Are there patterns of test duplication or brittleness?
- [ ] **Integration test coverage:** What service-level integration tests exist? Are there contract tests for APIs consumed or produced by this service? Where are integration test gaps?
- [ ] **CI pipeline depth:** What runs on pull request? What runs on merge? What runs on a scheduled basis? Are there stages that regularly fail or are skipped?
- [ ] **Testability of existing code:** Are services testable in isolation? Are dependencies injected or hardcoded? Are there God classes, static singletons, or other patterns that make unit testing painful? Document these as testability debt items.
- [ ] **Test data management:** How is test data created and cleaned up? Are there seed scripts? Factories? Fixtures? Is there production data in non-production environments (a risk flag)?
- [ ] **External dependency handling:** How are third-party APIs, databases, and services handled in tests? Are they mocked, stubbed, or hit directly? Is there a consistent approach?
- [ ] **Test flakiness:** Are there known flaky tests? How does the team handle them — fix immediately, quarantine, or skip?

### Environment Setup

- [ ] Set up your full local development environment: application running, all dependent services available (database, message queue, third-party service stubs), and test suites executable.
- [ ] Run the full existing test suite locally and in CI. Note any failures, skips, or timeouts — these are your first data points.
- [ ] Understand all available environments: local, dev/integration, staging, pre-production. Document who controls them, how stable they are, and what level of testing they support.
- [ ] Identify environment gaps or instability that will block testing — this is commonly a bottleneck and is worth surfacing to the Engineering Manager early.
- [ ] Set up observability and debugging tools: log access, error tracking (Sentry, Rollbar), and any distributed tracing tooling relevant to the services you will be testing.

**Phase 1 Early Deliverable (End of Week 1–2):** A written Engineering & Testability Landscape assessment — current test coverage, identified testability debt, CI pipeline gaps, test data approach, and open questions — shared with your manager. Frame it as observations, not recommendations yet.

---

## Week 2: Analysis, Strategy & Test Design

**Goal:** Translate your observations into a concrete testability strategy and begin designing the most valuable test investments.

### Risk & Coverage Analysis

- [ ] Map the service's APIs, data models, and core business logic against the current test coverage. Identify the gaps with the highest business risk.
- [ ] Classify testing needs by type: unit, integration, contract, end-to-end, performance, data integrity, security.
- [ ] Identify the most valuable test types for this specific codebase — for some services, contract tests deliver more value than unit tests; for others, the inverse is true. Do not assume a fixed split.
- [ ] Review recent defects and production incidents: what types of issues have escaped? At what level of the test pyramid would they have been caught? This shapes your investment priorities.
- [ ] Identify data handling risks: are there sensitive data types in the test data? Is there test data pollution across environments? Are there schema validation gaps?

### API Contract Testing Strategy

- [ ] Identify all APIs this service consumes (dependencies) and produces (contracts it offers to consumers).
- [ ] Assess whether contract testing exists. If not, this is typically your highest-priority Phase 2 investment for integration risk reduction.
- [ ] Evaluate contract testing tooling appropriate for the stack (e.g., Pact for REST/HTTP, Pactflow for broker-based workflows, Spring Cloud Contract for JVM services, gRPC contract testing approaches).
- [ ] Map the dependencies and determine whether a consumer-driven or provider-driven contract testing approach is more appropriate for the team's context.

### Testability Debt Inventory

- [ ] Document every pattern or code structure you have found that makes testing painful — tightly coupled dependencies, untestable static methods, missing seams, global state, etc.
- [ ] For each item, estimate the test coverage value unlocked if the debt were resolved, and the approximate effort to fix it.
- [ ] Prioritise the list: high-coverage-unlock, low-refactor-effort items are your Phase 2 quick wins. High-effort refactors with low coverage unlock are candidates to defer or discard.
- [ ] Validate the list with a developer — they often know the history of why the code is structured the way it is, and can identify where a refactor would require wider coordination.

### AI-Driven Testing Strategy

- [ ] Evaluate available LLMs and AI tooling (GitHub Copilot, ChatGPT, Claude) for SDET-specific use cases: generating test utility functions, unit test scaffolding, edge case identification for complex business logic, and reviewing test code for common anti-patterns.
- [ ] Identify where AI adds the most value in your specific codebase context: generating test data factories, scaffolding contract test stubs, writing boilerplate harness code, or analyzing code for testability issues.
- [ ] Identify where AI is not reliable enough without careful review — AI-generated unit tests frequently test the wrong behavior or assert against implementation rather than specification. Establish review checkpoints.
- [ ] Advocate for AI tooling access if not already available (GitHub Copilot licences, LLM API access) — make the case to the Engineering Manager with concrete examples of accelerated output.

### Testability Strategy Draft

- [ ] Define the target test pyramid for this service: unit / integration / contract / E2E ratio, with rationale.
- [ ] Define scope: what will be addressed in 90 days, what is deferred, and why.
- [ ] Propose the contract testing approach: tooling choice, provider and consumer coverage, broker strategy if applicable.
- [ ] Propose a testability debt resolution roadmap: prioritised list of refactors, with estimated effort and coverage value.
- [ ] Define how tests will be run: local, CI on PR, CI on merge, scheduled. Define what constitutes a build failure.
- [ ] Present the strategy draft to the Engineering Manager and lead developer — this is a conversation, not a sign-off document. Expect pushback on the refactor prioritisation.

### Tooling Evaluation

- [ ] Evaluate test framework options appropriate for the stack (e.g., Jest, Vitest, JUnit 5, pytest, Go testing, RSpec).
- [ ] Evaluate API testing and contract testing tooling (e.g., Pact, Supertest, REST Assured, Postman/Newman).
- [ ] Evaluate test reporting and CI integration options.
- [ ] Select tooling and document the rationale — involving at least one developer in the decision creates shared ownership.

**Phase 1 Deliverable (Day 30):** Testability Assessment — engineering landscape, coverage gaps, testability debt inventory, contract testing strategy, tooling decisions, and a prioritised 90-day roadmap — reviewed with the Engineering Manager and at least one developer.

---

## What Good Looks Like at 30 Days

At the 30-day mark, you should feel confident that:

- You can build, run, and debug the application locally without assistance.
- You have a clear, evidence-based picture of the codebase's current testability state.
- You have identified the highest-value test investments and the most impactful testability debt items.
- The development team understands what you are here to do and sees you as a contributor to their workflow, not a gatekeeper.
- You have not yet refactored production code or rewritten existing tests — that comes in Phase 2, with team input.
- The Testability Assessment has been reviewed by your manager and at least one developer.

---

## Phase 2 — Build & Integrate (Weeks 5–8)

**Goal:** Deliver the core testability investments. Establish contract testing, build foundational test utilities and harnesses, deepen unit and integration coverage, and integrate meaningfully into the development team's daily workflow.

---

## Week 3: Test Utilities, Contract Testing & AI-Assisted Development

### Test Utility Library

- [ ] Set up a dedicated test utilities module in the repository — separate from the production code, but treated with the same engineering standards (reviewed, documented, tested).
- [ ] Build foundational utilities first: test data factories (not raw fixtures), assertion helpers for domain-specific validations, and request builders for API tests.
- [ ] Implement database test helpers: transaction rollback between tests, seed data management, and schema validation utilities.
- [ ] Walk the development team through the utilities: where they live, how to use them, and how to contribute new ones. This is as important as building them — utilities only scale if the team adopts them.
- [ ] Document contribution guidelines for the test utilities module — naming conventions, required tests for new utilities, code review expectations.

### API Contract Testing

- [ ] Implement consumer-driven contract tests for the APIs this service consumes — starting with the highest-traffic or most business-critical integrations.
- [ ] Implement provider contract verification for the APIs this service exposes — ensuring the service honours the contracts its consumers depend on.
- [ ] Configure the contract test pipeline: contract tests should run on PR and block merge if contracts are broken.
- [ ] If a contract broker (e.g., Pactflow) is being introduced, work with the Engineering Manager to establish the broker and document the workflow for the team.
- [ ] Conduct a short walkthrough with the team: what contract testing is, why it matters for integration risk, and how to add new contracts as new API interactions are developed.

### AI-Assisted Test Development

- [ ] Use LLMs to generate initial unit test scaffolding for the highest-priority uncovered business logic — treat AI output as a first draft requiring careful review.
- [ ] Use GitHub Copilot (or equivalent) to accelerate writing test utility functions and harness code; review all AI-generated code for correctness and maintainability.
- [ ] Use LLMs to identify edge cases and boundary conditions for complex business logic — AI is particularly useful for surfacing cases that human analysis tends to miss (null handling, concurrent access, numeric overflow, etc.).
- [ ] Begin building a prompt library: document which prompts produce reliable, high-quality test outputs for your specific language and business domain. Share it with the team.

### First Test Contributions

- [ ] Implement unit tests for the highest-priority business logic identified in the Testability Assessment — starting with pure functions and domain logic that has no external dependencies.
- [ ] Implement integration tests for the most critical service boundaries — database interactions, message queue consumers/producers, and internal service calls.
- [ ] Conduct a code review of your initial test contributions with a developer — set the quality bar explicitly and invite feedback on style and coverage approach.

**Week 3 Deliverable:** Test utility library in the repository with documented contribution guidelines; initial contract tests running in CI; first unit and integration test contributions reviewed and merged.

---

## Week 4: Developer Integration, Testability Refactors & Coverage Depth

### Developer Pairing & Code Review

- [ ] Begin actively participating in code review — not just reviewing for test coverage, but identifying testability issues (untestable patterns, hardcoded dependencies, missing seams) and raising them constructively.
- [ ] Pair with developers on at least two features during Phase 2. Pairing is your highest-leverage activity for culture change: it shows developers _in their workflow_ what testable code looks like and removes the friction of "I'll figure out how to test this later."
- [ ] When pairing, focus on test-first discussion: "How would we write a unit test for this before we write the code?" — not mandating TDD, but introducing the habit of designing for testability from the start.
- [ ] Establish a recurring check-in with at least one developer: a lightweight pair on a shared codebase area, not a formal meeting.

### Testability Refactors

- [ ] Execute the highest-priority items from the testability debt inventory (high coverage value, low refactor effort).
- [ ] Approach refactors collaboratively — propose the change in a code review comment or design conversation before implementing it. Refactors made unilaterally, even good ones, create friction.
- [ ] Ensure each refactor is accompanied by tests that prove the behavior is preserved before and after — this is non-negotiable. Refactoring without tests is just rewriting.
- [ ] Track testability debt items resolved and coverage unlocked — this becomes evidence of your impact in Phase 3.

### Coverage Expansion

- [ ] Extend unit test coverage to the next tier of priority business logic, now that foundational utilities are in place.
- [ ] Add schema validation tests: ensure API request/response shapes are validated against a schema, not just manually inspected.
- [ ] Add data integrity tests where applicable: verify that database transactions, constraints, and migrations behave correctly under failure and edge-case conditions.
- [ ] Introduce or expand API test coverage at the service level: happy paths, error cases, authentication and authorisation boundaries, and rate limiting where relevant.

### Definition of Done Integration

- [ ] Propose additions to the team's Definition of Done: new features should include unit tests (minimum coverage threshold), and new API endpoints should include a consumer contract test. Discuss with the Engineering Manager before adding as a hard gate.
- [ ] If a coverage gate does not already exist in CI, propose adding one — with an agreed threshold that reflects the current baseline plus a small increment, not an aspirational number that creates immediate debt.
- [ ] Document the testing expectations for new features in the team's contribution guide or README.

**Phase 2 Deliverable (Day 60):** Contract tests running in CI covering the highest-priority API integrations; test utility library actively used by at least one developer; unit and integration coverage measurably improved vs. Day 1 baseline; at least two testability debt items resolved with tests in place.

---

## What Good Looks Like at 60 Days

At the 60-day mark, you should feel confident that:

- Contract tests are live in CI and providing real integration signal.
- The development team is using the test utilities you built — they are not the only person contributing to them.
- You have reviewed code and paired with at least one developer in a way that changed how they thought about testability.
- Unit and integration coverage has measurably improved vs. the Day 1 baseline.
- AI tooling is actively part of your workflow, saving real time on boilerplate and edge case identification.
- At least one testability debt item has been resolved and you can point to the tests that prove the behavior is preserved.

---

## Phase 3 — Stabilize & Scale (Weeks 9–12)

**Goal:** Mature the testability posture, drive measurable coverage improvements, contribute to engineering standards, and establish a sustainable model for ongoing quality investment.

---

## Week 5–6: Stabilize & Deepen

### Test Suite Health

- [ ] Execute a full audit of the unit and integration test suite: are tests deterministic? Are they testing behavior or implementation? Are there duplicates? Are there tests that no longer provide meaningful signal?
- [ ] Audit contract tests: are all critical API integrations covered? Are there gaps opened by new features developed in Phase 2?
- [ ] Identify and resolve any test flakiness introduced during Phase 2 — flaky tests erode trust faster than missing tests. Treat them with the same urgency as production bugs.
- [ ] Measure the full CI pipeline: how long does each test stage take? Are there bottlenecks? Propose optimisations (parallelisation, test sharding, smarter test selection) if test stage duration is a team pain point.

### Advanced AI Integration

- [ ] Use LLMs to analyze test failure logs and surface patterns — are failures systemic (likely a design problem) or isolated (likely a flaky test or data issue)?
- [ ] Experiment with AI-assisted test coverage analysis: use code change history and risk signals to identify the areas of the codebase most likely to introduce regressions, and target coverage efforts there.
- [ ] Evaluate AI-assisted maintenance: when the production code changes, use LLMs to identify which tests are affected and how they need to be updated — particularly valuable for contract test stubs and data factories.
- [ ] Share findings with the team: document which AI workflows are production-ready vs. still experimental in the team's testing documentation.

### Testability Debt Resolution

- [ ] Execute the next tier of the testability debt roadmap — higher-effort refactors that were deferred from Phase 2.
- [ ] For any refactor that affects public APIs or shared modules, coordinate with other team members before implementing — propose via ADR (Architecture Decision Record) or design document if the change is non-trivial.
- [ ] Measure coverage unlocked vs. effort invested for each resolved debt item — this builds the evidence base for continuing the investment in Phase 3 and into the next quarter.

---

## Week 7–8: Scale & Future Planning

### Engineering Standards Contribution

- [ ] Propose additions or updates to the team's engineering standards or contribution guide based on testability patterns learned in the first 90 days. Focus on 2–3 high-impact, widely applicable rules rather than an exhaustive list.
- [ ] If the organisation has a shared tooling or standards function (Test Architect, Platform Engineering, Engineering Excellence team), share your testability debt findings and contract testing approach — patterns that worked in your team may apply elsewhere.
- [ ] Conduct a testability retrospective with the development team: what testing patterns are working well? What is still painful? What would they change about the current approach? Feed the answers back into the next quarter's roadmap.

### Documentation & Knowledge Transfer

- [ ] Finalize and publish all testability documentation: test utility contribution guide, contract testing workflow, testability debt register (with resolution status), and a "how to test this service" README section.
- [ ] Add SDET onboarding documentation to the team's knowledge base — what the next SDET (or developer picking up testing responsibilities) needs to know to get productive quickly.
- [ ] Present a 90-day testing progress summary to the Engineering Manager: coverage improvements vs. baseline, contract tests added, testability debt resolved, AI tooling ROI, and the roadmap for the next quarter.

### Future Planning

- [ ] Identify remaining coverage gaps and prioritise them for the next quarter.
- [ ] Propose the next wave of testability investment: mutation testing to validate test quality, performance test integration at the service level, security testing of authentication and authorisation boundaries, or chaos/resilience testing for distributed service interactions.
- [ ] Define a roadmap for deeper AI integration: automated test generation pipelines for new API endpoints, AI-assisted contract test maintenance as APIs evolve, AI-powered defect prediction from code change history.
- [ ] Define a test suite maintenance cadence: who reviews and prunes the test suite, and how often. An unmaintained test suite becomes a liability faster than almost any other engineering debt.
- [ ] Outline a scalability plan for testability: as the team grows or more services are added, what needs to change in the contract testing strategy, the utility library structure, or the CI pipeline design?

**Phase 3 Deliverable (Day 90):** 90-day testability retrospective and testing roadmap for the next quarter — shared with the Engineering Manager. Coverage baseline to Day 90 comparison documented. All key testability patterns and utilities documented in the team's knowledge base.

---

## What Good Looks Like at 90 Days

At the 90-day mark, you should feel confident that:

- Code coverage (unit + integration) is measurably higher than the Day 1 baseline, with the improvement concentrated in the highest-risk areas of the codebase.
- Contract tests are running in CI and providing real integration risk signal on every PR that affects covered APIs.
- At least one developer has adopted testability patterns you introduced through pairing or code review — the impact extends beyond your own contributions.
- The test utility library is actively used and contributed to by the development team.
- The testability debt register is up to date, with completed items documented and the remaining backlog prioritised.
- AI tooling is saving measurable time on boilerplate, edge case generation, and test maintenance.
- Testability is part of how the team talks about new feature design — not an afterthought.
- You feel genuinely embedded in the engineering team, and you have identified the areas where you still want to grow.

---

## Key Deliverables Summary

| Phase   | Milestone       | Deliverable                                                                                         |
| ------- | --------------- | --------------------------------------------------------------------------------------------------- |
| Phase 1 | End of Week 1–2 | Engineering & Testability Landscape assessment (written, shared with manager)                       |
| Phase 1 | Day 30          | Testability Assessment — coverage gaps, debt inventory, contract testing strategy, tooling, roadmap |
| Phase 2 | Week 3          | Test utility library live; initial contract tests running in CI                                     |
| Phase 2 | Week 4          | Testability refactors executed; coverage expanded; Definition of Done updated                       |
| Phase 2 | Day 60          | Coverage measurably improved; contract tests covering critical integrations; team using utilities   |
| Phase 3 | Week 5–6        | Test suite audit complete; flakiness resolved; AI integration deepened                              |
| Phase 3 | Week 7–8        | Engineering standards contribution; full testability documentation published                        |
| Phase 3 | Day 90          | 90-day retrospective and roadmap; all documentation complete; baseline-to-Day-90 comparison         |

---

## Success Metrics

Use the Current Baseline column to anchor targets to the actual starting point. Populate it at Day 30.

| Metric                                     | Current Baseline (Day 30) | Target at Day 60                               | Target at Day 90                                             |
| ------------------------------------------ | ------------------------- | ---------------------------------------------- | ------------------------------------------------------------ |
| **Unit + integration coverage (%)**        | Measure and document      | +10% vs. baseline or ≥60%, whichever is higher | +20% vs. baseline or ≥75%, whichever is higher               |
| **Contract test coverage**                 | 0 (if none exist)         | ≥3 critical API integrations covered           | All high-risk API integrations covered                       |
| **Testability debt items resolved**        | 0                         | ≥2 high-priority items resolved                | ≥5 items resolved; next tier prioritised                     |
| **CI test stage duration**                 | Measure and document      | Stable or improving vs. baseline               | No regression; optimisation proposed if >10 min              |
| **Defect detection rate (pre-production)** | Measure and document      | Trending upward vs. baseline                   | Measurably improved vs. Day 1                                |
| **Flaky test rate**                        | Measure and document      | <5%; any test >10% flake rate resolved         | <3%; zero tolerance for new flakes merged without quarantine |
| **AI-assisted coverage gain**              | Track from first AI use   | Track and document                             | Quantifiable ROI documented; shared with team                |

> **Calibration note:** If QA maturity is **None (first SDET hire)**, all Day 30 targets should read "Establish baseline". Do not set numerical targets until the baseline is confirmed. If maturity is **Established**, use existing historical data to set precise targets rather than the indicative values above.

---

## Ongoing Practices

- **Code review participation** — Every sprint, review at least as many PRs as you author. Flag testability issues alongside functional feedback.
- **Developer pairing** — At minimum once per sprint. Pairing is your highest-leverage culture-change activity.
- **Contract test maintenance** — When a new API endpoint is added or an existing contract changes, update contract tests in the same PR. Never let contracts drift.
- **Test suite health review** — Monthly audit: flag new flakiness, retire obsolete tests, and review coverage trends against the baseline.
- **Testability debt grooming** — Debt items should be reviewed and re-prioritised at the start of each quarter, not left to accumulate indefinitely.
- **AI tooling iteration** — Regularly reassess which AI workflows are producing reliable output. The tooling landscape changes rapidly.
- **Documentation maintenance** — Treat test utility docs and testability guides as living documents. Outdated documentation is worse than none — it actively misleads.
- **Advocacy** — Continue raising testability as a design concern in planning and architecture discussions. The goal is a team that automatically considers testability, not one that relies on a single SDET to enforce it.

---

## Testability Reference

When assessing and improving testability during Phase 1–2, use this reference to categorise what you find:

| Pattern                                  | Testability Impact                                                 | Typical Resolution                                                                     |
| ---------------------------------------- | ------------------------------------------------------------------ | -------------------------------------------------------------------------------------- |
| **Tightly coupled dependencies**         | Hard to unit test in isolation                                     | Introduce dependency injection; use interfaces or abstract types                       |
| **Static methods / singletons**          | Cannot be mocked or replaced in tests                              | Refactor to instance methods; inject via constructor                                   |
| **God classes / large modules**          | High coordination cost; tests become integration tests by accident | Decompose into smaller, single-responsibility modules                                  |
| **Global mutable state**                 | Tests interfere with each other; ordering matters                  | Eliminate or scope state; use setup/teardown hooks                                     |
| **Missing API contracts**                | Integration failures only caught in staging or production          | Add consumer-driven contract tests for all critical API interactions                   |
| **Production data in test environments** | Data privacy risk; test environment instability                    | Implement test data factories; anonymize or synthetic-generate all non-production data |
| **Hardcoded configuration**              | Tests require specific environment state                           | Externalize configuration; use test-specific config injection                          |
| **No test data management**              | Tests pollute each other; order-dependent failures                 | Implement transaction rollback, seed scripts, or factory reset utilities               |
