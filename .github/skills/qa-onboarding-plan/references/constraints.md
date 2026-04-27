# Constraints Reference

This file defines how each constraint or special focus area modifies the generated 90-day onboarding plan. Load this file in Step 3 when the user has provided one or more constraints. Apply all matching modifiers — they stack.

---

## HIPAA (Healthcare / Health Data)

**Risk profile:** Protected Health Information (PHI) exposure, access control, audit logging, breach notification.

**Plan modifications:**

- **Day 1–2:** Add mandatory HIPAA training and BAA acknowledgement to the first-steps checklist.
- **Week 1 (Product & Domain):** Explicitly map which features involve PHI — collection, storage, transmission, and access. Flag this as a Phase 1 priority.
- **Week 1 (Landscape/Tools):** Immediately verify whether any real PHI exists in test or staging environments. If yes, flag as a P1 risk requiring immediate remediation before any testing begins.
- **Week 2 (Risk & Coverage):** Elevate the following as highest-risk areas regardless of other context: role-based access control, audit trail completeness, data masking/de-identification, session management, and encryption in transit and at rest.
- **Test Data Strategy:** PHI must never be used in non-production environments. Add an explicit test data strategy item: synthetic data generation or de-identification pipeline. This is mandatory, not optional.
- **Phase 2:** Introduce a HIPAA compliance test checklist as a mandatory release gate. Include: audit log validation, RBAC tests, data masking confirmation, session timeout, and access revocation scenarios.
- **QA Governance Reference (if Manager role):** Add HIPAA escalation path: any defect with potential PHI exposure is automatically P1; notify compliance officer within 2 hours.
- **Ongoing Practices:** Add quarterly HIPAA compliance review to the ongoing practices section.

---

## PCI-DSS (Payment Card / Financial Transactions)

**Risk profile:** Cardholder data exposure, payment flow integrity, fraud vectors, network segmentation.

**Plan modifications:**

- **Week 1 (Product & Domain):** Map all payment flows and identify where cardholder data (PAN, CVV, expiry) is handled, transmitted, or stored.
- **Week 1 (Landscape/Tools):** Verify that no real cardholder data exists in test environments (PCI DSS Requirement 6). Flag immediately if found.
- **Week 2 (Risk & Coverage):** Elevate as highest-risk: payment flow end-to-end, tokenisation validation, encryption of cardholder data, authentication on payment entry, and error handling that does not leak card data.
- **Test Data Strategy:** Use only synthetic or tokenised card numbers (e.g. Stripe test card numbers, Luhn-valid generated PANs). Never use real card data in testing.
- **Phase 2:** Introduce a PCI compliance test checklist as a mandatory release gate for any release touching payment flows. Include: payment flow integrity, card data masking in logs, access control on payment data, and error message sanitisation.
- **Ongoing Practices:** Add evidence of test coverage for PCI-scoped features to the release readiness report.

---

## SOC 2 / ISO 27001 (General Security & Compliance Audits)

**Risk profile:** Access control, availability, confidentiality, data integrity, audit evidence.

**Plan modifications:**

- **Week 1 (Landscape/Tools):** Identify which controls map to QA responsibility (access control testing, availability monitoring, change management evidence).
- **Week 2 (Risk & Coverage):** Add control-mapped test coverage areas: authentication, authorisation, data integrity, audit logging, and availability under load.
- **Phase 2:** Include a controls evidence checklist — ensure test results and coverage reports can serve as audit evidence for relevant controls.
- **Ongoing Practices:** Add quarterly review of control coverage to ensure evidence remains current for audits.

---

## Mobile-First

**Risk profile:** Device/OS fragmentation, offline behaviour, push notifications, app store release constraints, gesture interactions.

**Plan modifications:**

- **Week 1 (Environment Setup / Tools):** Add device lab or cloud device farm access (BrowserStack, Sauce Labs, AWS Device Farm) to environment setup. Document the target device matrix (OS versions, screen sizes, manufacturers).
- **Week 2 (Risk & Coverage):** Add mobile-specific risk areas: OS version compatibility (especially the two latest iOS and Android versions), network condition degradation (3G, offline), deep link handling, push notification delivery, background/foreground state transitions, and accessibility on mobile viewports.
- **Tooling Evaluation:** Add evaluation of mobile test frameworks (Appium, Detox, XCUITest, Espresso) to the tooling selection section.
- **Phase 2:** Include a device matrix test run as part of the regression suite. Define minimum device coverage required for release sign-off.
- **Success Metrics:** Add mobile-specific metric: test pass rate across the defined device matrix.

---

## AI/ML Product

**Risk profile:** Non-deterministic outputs, model drift, data pipeline quality, prompt injection (if LLM-facing), fairness and bias, explainability.

**Plan modifications:**

- **Week 1 (Product & Domain):** Identify which features are AI/ML-driven. Understand the model(s) in use, input data sources, and output surfaces exposed to users.
- **Week 2 (Risk & Coverage):** Add AI-specific risk areas: output non-determinism (tests must tolerate acceptable variance ranges, not exact match), model drift detection, data pipeline integrity, adversarial inputs, and — if the product exposes an LLM interface — prompt injection and jailbreak scenarios.
- **Test Strategy:** Include a section on testing strategies for non-deterministic systems: property-based testing, statistical sampling, golden dataset regression, and threshold-based assertions rather than equality checks.
- **Phase 2:** Define a model regression baseline: a curated set of input/output pairs with acceptable variance thresholds. Flag if model updates require re-baselining.
- **Ongoing Practices:** Add periodic model regression runs (especially after model updates or retraining) to ongoing practices.

---

## Microservices / Distributed Systems

**Risk profile:** Inter-service contract drift, distributed failure modes, data consistency across services, observability gaps.

**Plan modifications:**

- **Week 1 (Landscape):** Map the service dependency graph. Identify which services are owned by the team vs. upstream/downstream dependencies.
- **Week 2 (Risk & Coverage):** Add microservices-specific risk areas: API contract adherence between services, failure and retry behaviour, distributed transaction consistency, and timeout/circuit-breaker handling.
- **Test Strategy:** Prioritise contract testing (consumer-driven contracts with Pact or similar) and component-level integration tests over full end-to-end tests wherever possible. End-to-end tests should be reserved for critical user journeys only.
- **Environment Strategy:** Flag that full end-to-end testing may require service virtualisation or mocking for upstream dependencies. Add this as a Week 2 environment strategy item.
- **Phase 2:** Introduce API contract tests as a mandatory CI gate — failing contracts block merge.
- **Ongoing Practices:** Add contract test review cadence when service APIs change.

---

## High-Traffic / High-Availability Platform

**Risk profile:** Performance degradation under load, availability SLOs, data consistency at scale, caching invalidation.

**Plan modifications:**

- **Week 1 (Landscape):** Gather current traffic patterns (peak RPS, P95 response times), SLOs/SLAs, and known performance bottlenecks.
- **Week 2 (Risk & Coverage):** Add performance as a first-class risk category alongside functional coverage. Identify the top 5 highest-traffic user journeys — these need both functional and load test coverage.
- **Test Environment Strategy:** Flag that load testing requires a production-equivalent environment or a clearly documented delta. Add environment sizing as a Phase 1 item.
- **Phase 2:** Introduce performance regression gates in CI — at minimum, a smoke load test (target load) on the critical paths must pass before release.
- **Success Metrics:** Add performance metrics alongside functional ones: P95 response time target, error rate under peak load, and throughput baseline.
- **Ongoing Practices:** Add performance regression run to the release readiness checklist.

---

## Regulated Industry (General — FDA, FedRAMP, GDPR, etc.)

**Risk profile:** Audit evidence requirements, validation documentation, change control traceability.

**Plan modifications:**

- **Week 1 (Product & Domain):** Identify the specific regulation and understand which product features fall within its scope.
- **Week 2 (Risk & Coverage):** Add traceability as a first-class requirement: every test must be traceable to a requirement or user story for audit purposes.
- **Test Strategy:** Include a test traceability matrix as a Phase 1 deliverable alongside the test strategy.
- **Phase 2:** Ensure the defect lifecycle captures required fields for audit evidence (root cause, resolution evidence, regression test confirmation).
- **Ongoing Practices:** Add regulation-specific review cadence (e.g. annual validation reviews for FDA-regulated software).

---

## Accessibility / WCAG

**Risk profile:** WCAG 2.1/2.2 AA non-compliance, keyboard navigation failures, screen reader incompatibility, insufficient colour contrast, broken focus management, inaccessible dynamic content.

**Applicable context:** Consumer-facing products (e-commerce, edtech, health tech, government, financial services) and any product with legal accessibility obligations (ADA, Section 508, EN 301 549, European Accessibility Act).

**Plan modifications:**

- **Week 1 (Product & Domain):** Identify all user-facing surfaces (web, mobile web, native app). Confirm the target WCAG conformance level — typically WCAG 2.1 AA. Check whether an existing VPAT or accessibility audit exists and obtain it. Flag whether the product is in a domain with legal accessibility obligations.
- **Week 1 (Landscape / Tools):** Add automated accessibility scanning to the environment setup. Minimum tooling: axe-core (via axe DevTools browser extension, or Playwright/Cypress integration) and Lighthouse. Identify the screen reader matrix — at minimum: NVDA + Chrome (Windows), VoiceOver + Safari (macOS/iOS), TalkBack + Chrome (Android).
- **Week 2 (Risk & Coverage):** Add accessibility as a first-class risk category alongside functional coverage. Highest-risk areas to assess:
  - **Keyboard navigation:** All interactive elements (links, buttons, forms, modals, menus) reachable and operable by keyboard alone; no keyboard traps.
  - **Focus management:** Focus is correctly set after route changes, modal opens/closes, and dynamic content updates.
  - **ARIA semantics:** Landmark roles, live regions, labels, and described-by attributes are correct and not redundant.
  - **Colour contrast:** Normal text ≥ 4.5:1; large text and UI components ≥ 3:1 against their background.
  - **Screen reader announcements:** State changes (loading, errors, success, toggle states) are announced correctly without visual dependency.
  - **Text resize:** UI remains usable at 200% text zoom without loss of content or functionality.
- **Test Strategy:** Structure accessibility testing in layers:
  1. **Automated (CI-integrated):** axe-core or Lighthouse run against every PR. Catches approximately 30–40% of WCAG issues. Critical and Serious violations block merge.
  2. **Keyboard-only walkthrough:** All critical user journeys completed without a mouse. Documented as a checklist per journey.
  3. **Screen reader smoke test:** Core journeys (sign-up, primary workflow, error recovery) validated with at least NVDA + Chrome and VoiceOver + Safari.
  4. **Manual visual checks:** Colour contrast spot-check on new UI components; focus indicator visible in all interactive states.
- **Phase 2:** Introduce an automated accessibility CI gate — axe-core violations at Critical or Serious severity block merge for all new and changed pages. Add keyboard navigation coverage to the regression checklist.
- **Success Metrics:** Add accessibility-specific metrics:
  - Automated violations (Critical + Serious) trending toward zero — establish baseline count in Week 1.
  - Keyboard navigation coverage: percentage of critical user journeys with a documented keyboard-only pass.
  - WCAG 2.1 AA criteria with documented test coverage (target: all Level A and Level AA criteria mapped by end of Phase 2).
- **Ongoing Practices:** Add accessibility regression to the release readiness checklist. New UI components must pass axe-core and keyboard navigation review before merging. Schedule a manual screen reader review for any significant UI redesign.
