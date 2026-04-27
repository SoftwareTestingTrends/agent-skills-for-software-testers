---
name: qa-onboarding-plan
description: "Generate a tailored 90-day onboarding plan for a Software QA or Testing professional joining a new organization. Use when asked to create an onboarding plan, build a 30/60/90 day plan for QA, plan first months as a QA, draft a new hire onboarding plan, create an onboarding plan for a new QA hire, or onboard a QA Automation Developer, QA Automation Lead, SDET, QA Manager, Test Architect, QA Analyst, or Performance Engineer."
argument-hint: "Specify who the plan is for (yourself or a new hire), role (e.g. QA Analyst, SDET, QA Manager), seniority (Junior/Mid/Senior), team size and structure, product domain, tech stack, QA maturity (None — first QA hire / Partial — fragmented testing / Established — mature QA function), constraints (e.g. HIPAA, PCI, accessibility/WCAG, mobile-first, microservices), and work model (Fully remote / Hybrid / On-site)"
user-invocable: true
---

# QA Onboarding Plan Generator

## When to Use

Invoke this skill when a user asks to:

- Create, generate, or draft a 90-day (or first-month) onboarding plan for a QA or Software Testing professional
- Build a new-hire plan for any QA role
- Plan their own first weeks or months in a new QA position

Supported roles: QA Automation Developer/Engineer, QA Automation Lead, SDET, QA Manager, Test Architect, QA Analyst, Performance/Load Testing Engineer.

## Assets

- [Reference plan](./references/onboarding-plan-automation-developer-lead.md) — A fully worked example for a QA Automation Developer/Lead. Use as structural reference and benchmark.
- [QA Manager reference plan](./references/onboarding-plan-qa-manager.md) — A fully worked example for a QA Manager. Use as structural reference when role is QA Manager.
- [SDET reference plan](./references/onboarding-plan-sdet.md) — A fully worked example for an SDET. Use as structural reference when role is SDET.
- [Role profiles](./references/role-profiles.md) — Per-role emphasis, section adaptations, and tailoring rules.
- [Constraints](./references/constraints.md) — Per-constraint plan modifications for regulated industries, mobile-first, AI/ML products, microservices, and high-traffic platforms.

## Procedure

### Step 1 — Gather Inputs

**Before asking anything**, scan the user's initial message for any of the nine data points below. Pre-fill any answers already provided — only ask for what is genuinely missing.

Use the `vscode_askQuestions` tool to collect all missing inputs in a **single structured round-trip**. Configure each question as follows:

| Question header  | Question text                                                                                                                                                                                                          | Type     | Options (if applicable)                                                                                                               |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `plan_for`       | "Are you creating this plan for yourself or for someone you are hiring?"                                                                                                                                               | options  | For myself (I'm the one onboarding), For a new hire (I'm their manager)                                                               |
| `role`           | "What role are you onboarding into?"                                                                                                                                                                                   | options  | QA Automation Developer/Engineer, QA Automation Lead, SDET, QA Manager, Test Architect, QA Analyst, Performance/Load Testing Engineer |
| `seniority`      | "What seniority level?"                                                                                                                                                                                                | options  | Junior, Mid, Senior                                                                                                                   |
| `team_structure` | "How is the team structured? (e.g. '8 devs, 1 PM, no existing QA')"                                                                                                                                                    | freeform | —                                                                                                                                     |
| `product_domain` | "What type of product and domain? (e.g. SaaS B2B, mobile fintech, e-commerce, internal tooling)"                                                                                                                       | freeform | —                                                                                                                                     |
| `tech_stack`     | "What does the tech stack look like? (frontend, backend, APIs, databases, CI/CD)"                                                                                                                                      | freeform | —                                                                                                                                     |
| `qa_maturity`    | "How would you describe the current QA maturity?"                                                                                                                                                                      | options  | None — first QA hire, Partial — fragmented testing, Established — mature QA function                                                  |
| `constraints`    | "Any constraints or special focus areas? (e.g. regulated industry such as HIPAA or PCI, accessibility / WCAG compliance, mobile-first, AI/ML product, microservices, high-traffic platform — or leave blank for none)" | freeform | —                                                                                                                                     |
| `work_model`     | "How is the team working?"                                                                                                                                                                                             | options  | Fully remote, Hybrid, On-site                                                                                                         |

**Conditional adjustments before asking:**

- If role is **QA Manager**: reframe `tech_stack` as "What tools and platforms does the team currently use? (test management, CI/CD, reporting)" — focus is on tooling landscape, not scripting stack.
- If role is **Performance/Load Testing Engineer**: add a note to `tech_stack` asking specifically about load testing tools (k6, JMeter, Locust, Gatling) and SLO/SLA expectations.
- If role is **QA Analyst**: reframe `tech_stack` as "What test management tool, defect tracker, and test environment do you use? (e.g. TestRail, Jira, Browserstack)" — focus is on QA tooling access, not engineering stack.
- If role is **Test Architect**: broaden `team_structure` to "How many engineering teams are there, and do they have their own QA practices? (e.g. '3 squads, each with 1 QA, no shared standards')"
- If `qa_maturity` is already known to be **None (first QA hire)**: mark `team_structure` as optional — the answer is often implicit.
- If the user's message clearly indicates they are a hiring manager creating a plan for someone else (e.g. "create a plan for my new SDET hire", "I'm onboarding a QA Analyst next week"), pre-fill `plan_for` as "For a new hire" without asking.
- If the user's message clearly indicates they are creating the plan for themselves (e.g. "I'm starting a new job as a QA Manager", "help me plan my first 90 days"), pre-fill `plan_for` as "For myself" without asking.

Once all required inputs are collected, proceed to Step 2.

### Step 2 — Load the Role Profile and Constraints

Load [role-profiles.md](./references/role-profiles.md) and identify the matching role profile. This determines which sections to include, which to adapt, and which emphasis areas apply.

If the user provided any constraints (HIPAA, PCI, SOC 2, mobile-first, AI/ML product, microservices, high-traffic, or other regulated industry), also load [constraints.md](./references/constraints.md). Identify every matching constraint section — multiple constraints can apply simultaneously and their modifiers stack.

### Step 3 — Generate the Plan

Use the [reference plan](./references/onboarding-plan-automation-developer-lead.md) as a structural reference. If the role is **QA Manager**, use [onboarding-plan-qa-manager.md](./references/onboarding-plan-qa-manager.md) as the primary structural reference instead — it provides a fully worked QA Manager example with the correct section titles, governance framing, and people-first orientation. If the role is **SDET**, use [onboarding-plan-sdet.md](./references/onboarding-plan-sdet.md) as the primary structural reference instead — it provides a fully worked SDET example with the correct section titles, testability framing, contract testing strategy, and embedded dev-team orientation.

**Plan voice — `plan_for` modifier:**

- If `plan_for` is **"For myself"**: write the entire plan in the **second person** ("you will", "ask your manager", "your goal is") — the reader is the person living the plan.
- If `plan_for` is **"For a new hire"**: write the entire plan in the **third person** ("the new hire will", "expect your hire to", "their goal is") and add a brief **Manager's Guide** section at the top of the document (after Overview, before Guiding Principles) covering: what the manager should do on Day 1 to set the hire up for success, how to conduct the 30/60/90-day check-ins, what early warning signs to watch for, and how to calibrate expectations per the declared seniority level.

Produce a complete 90-day plan in Markdown using this structure:

```
# 90-Day Onboarding Plan: [Role Title]

## Overview
## Guiding Principles

--- Phase 1 — Orient & Discover (Weeks 1–4) ---
### Day 1–2: First Steps
## Week 1: Orientation & Discovery
  - People & Culture
  - Product & Domain
  - [Role-appropriate landscape section]
  - Environment Setup (technical roles) / Process & Tools Landscape (Manager)
**Phase 1 Early Deliverable (End of Week 1–2)**

## Week 2: Assessment & Strategy
  - Risk & Coverage Analysis
  - Test Environment Strategy           [technical roles only]
  - AI-Driven Testing Strategy          [technical roles only; skip for Manager/Analyst]
  - [Role-specific strategy section]
  - Test Strategy Draft / QA Process Design
  - Tooling Evaluation & Selection
  - Planning
**Phase 1 Deliverable (Day 30)**

## What Good Looks Like at 30 Days

--- Phase 2 — Build & Integrate (Weeks 5–8) ---
## Week 3: [Role-appropriate title]
  [Role-specific subsections]
**Week 3 Deliverable**

## Week 4: [Role-appropriate title]
  [Role-specific subsections]
**Phase 2 Deliverable (Day 60)**

## What Good Looks Like at 60 Days

--- Phase 3 — Stabilize & Scale (Weeks 9–12) ---
## Week 5–6: Stabilize & Deepen
## Week 7–8: Scale & Future Planning
**Phase 3 Deliverable (Day 90)**

## What Good Looks Like at 90 Days

--- Reference Sections ---
## Key Deliverables Summary        [table]
## Success Metrics                 [table with indicative targets]
## Ongoing Practices
## Test Plan Components Reference  [or QA Governance Reference for Manager]
```

**Rules:**

- Every section must be adapted to the declared role and context — never generic.
- If constraints were provided, apply every matching modifier from [constraints.md](./references/constraints.md) before writing each section. Constraint modifiers override generic defaults — e.g. if HIPAA applies, the test data strategy is mandatory and non-negotiable, not a recommendation.
- Apply `[Lead]` tags only to items relevant to Lead, Architect, or Manager roles.
- For all technical roles, AI-driven testing is a core investment: include tooling evaluation, LLM-assisted test generation, prompt library development, AI-assisted maintenance, and ROI tracking.
- For QA Manager: replace framework/scripting sections with people management, hiring plan, metrics and reporting, and cross-team governance.
- For Performance Engineer: replace UI/API automation sections with baseline definition, SLO/SLA identification, load tool setup, and CI performance gates.
- For SDET: replace UI automation sections with test utility libraries, API contract testing, test harness design, and developer pairing; frame all work as embedded in the dev team.
- For Test Architect: scope all activities to cross-team impact; replace sprint-level work with ADRs, shared utility design, standards governance, and cross-team enablement.
- For QA Analyst: rename "Test Strategy Draft" to "Test Design Approach"; omit CI/CD integration sections unless the role is explicitly transitioning to automation (defer to Phase 3 if so); keep AI guidance introductory.
- **Seniority modifiers** — apply on top of the role profile:
  - **Junior**: extend the orientation phase; add explicit mentorship/pairing expectations; simplify deliverables to foundational tasks; reduce scope of strategy ownership.
  - **Mid**: balanced plan as described in the role profile — owns delivery, contributes to strategy, limited leadership scope.
  - **Senior**: accelerate orientation (assume faster ramp); add explicit expectations to drive strategy, influence decisions, mentor others, and contribute to team standards from Phase 1.
- **QA maturity modifiers** — apply across all three phases based on the declared maturity level:
  - **None (first QA hire):**
    - Phase 1: spend more time on people and product context; the landscape section will be sparse by definition — frame observations as "what exists" vs. "what is needed"; the Day 30 deliverable is a QA foundation proposal, not an audit of existing practices.
    - Phase 2: everything is being built from scratch — test strategy, tooling, environments, test data approach, and team process. Frame Phase 2 as "establish" not "improve". Do not reference auditing or migrating existing frameworks.
    - Phase 3: focus on stabilising and socialising the new function; add explicit items for gaining team adoption and measuring early signal (even if baselines are still forming).
    - Success Metrics: targets should be framed as "establish baseline by Day 30", "define targets by Day 60", "first trend data available by Day 90" — not numerical targets, since there is no historical data.
  - **Partial (fragmented testing):**
    - Phase 1: the landscape section is critical — document what exists, who owns it, and its quality. Identify what to keep, what to consolidate, and what to replace. Flag any contradictory or abandoned test assets.
    - Phase 2: frame as "assess and consolidate" — evaluate existing tests before adding new ones; avoid duplicating effort; prioritise migrating or deprecating conflicting test assets before expanding coverage.
    - Phase 3: frame as "standardise and scale" — enforce the chosen approach across the team; measure improvement against the fragmented baseline.
    - Success Metrics: include a before/after comparison against the fragmented baseline. Targets should show directional improvement vs. current state (e.g. "reduce escaped defects by X% vs. Day 1 baseline").
  - **Established (mature QA function):**
    - Phase 1: accelerate the landscape section — a mature function has documentation; use it. Focus observation time on gaps and improvement opportunities, not basic discovery. The Day 30 deliverable should propose optimisations, not just describe the current state.
    - Phase 2: frame as "audit and optimise" — benchmark current practices against industry standards, identify waste or technical debt in the test suite, and propose improvements without disrupting what is working.
    - Phase 3: focus on innovation and raising the bar — advanced coverage (contract testing, mutation testing, visual regression, AI-assisted maintenance), contribution to engineering standards, and measurable quality improvement beyond the existing baseline.
    - Success Metrics: targets should benchmark against the existing baseline and show improvement. Use precise numerical targets where historical data exists.
- **Work model modifiers** — apply to Day 1–2 and Week 1 People & Culture sections based on `work_model`:
  - **Fully remote:** Replace any in-person framing with async-first equivalents. Day 1–2 must explicitly include: setting up async communication norms with the manager (preferred channels, response time expectations, working hours), scheduling a structured virtual introduction with every team member individually (not a single group call), and requesting written context (team wiki, architecture docs, decision logs) as a substitute for hallway conversations. Week 1 People & Culture must include: deliberate relationship-building through scheduled 1:1s rather than organic interaction; using written check-ins to stay visible; and identifying the team's async communication tools and norms (Slack conventions, document-first culture, async standup format if applicable). Pairing and collaboration items should specify video call + screen sharing rather than assuming co-location.
  - **Hybrid:** Note which days the team is typically in-office and plan high-context activities (introductions, pairing, whiteboarding) for in-office days. Flag the risk of context asymmetry — remote team members may miss informal decisions made in-office. Add an item in Week 1 to understand the team's hybrid norms and whether there is a documented remote-first communication policy.
  - **On-site:** Standard in-person framing applies. No special modifiers needed beyond the default plan.
- **Product domain risk modifiers** — use the declared `product_domain` to sharpen risk prioritisation in Phase 1 and coverage emphasis throughout. Apply the closest matching profile; if the domain spans multiple categories, apply all relevant ones:
  - **Healthcare / Health Tech:** Data integrity and privacy are the highest-risk areas. Prioritise PHI handling, audit trail completeness, access control, and clinical workflow accuracy above all other coverage. If HIPAA was not listed as an explicit constraint but the domain is healthcare, treat HIPAA modifiers as applicable by default.
  - **Fintech / Financial Services:** Payment flow integrity, fraud vectors, and regulatory traceability are the highest-risk areas. Prioritise transaction accuracy, double-payment prevention, error handling that does not leak financial data, and audit logging. If PCI-DSS was not listed as an explicit constraint but the domain involves card payments, treat PCI modifiers as applicable by default.
  - **E-commerce / Retail:** Checkout flow, inventory consistency, third-party integrations (payment gateways, shipping providers), and performance under promotional traffic spikes are the highest-risk areas. Prioritise end-to-end purchase journey coverage, cart and pricing accuracy, and load behaviour during peak events.
  - **SaaS B2B / Enterprise:** Multi-tenancy isolation, role-based access control, data segregation between tenants, and integration reliability (webhooks, APIs, SSO) are the highest-risk areas. Prioritise cross-tenant data leakage scenarios, permission boundary testing, and API contract stability.
  - **Mobile (consumer app):** Device/OS fragmentation, offline behaviour, notification reliability, and app store release constraints are the highest-risk areas. Apply mobile-first constraint modifiers if not already applied.
  - **Internal Tooling / Developer Tools:** Correctness of core workflows and resilience to edge-case inputs are the highest-risk areas. Lower regulatory risk but higher tolerance for exploratory testing. Prioritise coverage of the primary use cases used by the internal team, and ensure environment parity (the tool should be tested on the same setup as its users).
  - **AI/ML Product:** Apply AI/ML constraint modifiers if not already applied. Non-deterministic output validation and data pipeline integrity are the highest-risk areas.
  - **If the domain does not match any of the above:** Apply no special modifier. Ensure the Overview section acknowledges the domain and that Risk & Coverage Analysis reflects any domain-specific user expectations or failure modes mentioned by the user.
- **Success Metrics table calibration** — the metrics table must reflect what is actually measurable and achievable given the declared `qa_maturity`. Do not use generic or aspirational numbers that are disconnected from the starting point:
  - **None (first QA hire):** No historical data exists. Every metric cell in the Day 30 column should read "Establish baseline". Day 60 column should read "Define target based on baseline". Day 90 column should read "First trend data available — review and set quarter target". Do not invent numbers. Include a note in the table: _Targets will be set once a baseline is established at Day 30._
  - **Partial (fragmented testing):** Use the current state as the baseline for every metric. Express targets as relative improvement: "Reduce escaped defects by 20% vs. Day 1 baseline", "Increase regression pass rate from current X% to Y%". If the current value is unknown, the Day 30 column should read "Measure and document current state". Do not use absolute targets until the baseline is confirmed.
  - **Established (mature QA function):** Historical data exists — use it. Targets should be specific, time-bound, and benchmarked against the existing baseline. Where industry benchmarks are relevant (e.g. >95% regression pass rate, <2% escaped defect rate), reference them as aspirational context alongside the team-specific target. Flag any metric where the current baseline already meets or exceeds the benchmark — in those cases, the target is "maintain" rather than "improve".
  - **All maturity levels:** Include a "Current Baseline" column in the metrics table alongside phase targets. This makes progress measurable from day one rather than only visible in retrospect.
- Do not include a preamble or explanation — output the Markdown document directly.

### Step 4 — Save the Plan

After generating the plan, save it as a Markdown file using the `create_file` tool:

- **Path:** `onboarding-plans/<role-slug>-onboarding-plan.md`
  - Derive `<role-slug>` from the role name, lowercased and hyphenated (e.g., `qa-automation-developer`, `sdet`, `qa-manager`).
  - Example: `onboarding-plans/sdet-onboarding-plan.md`
- **Content:** The full Markdown document generated in Step 3.

Confirm to the user that the file has been saved and show the path.

Then offer to export the plan as a PDF:

> "Would you like to export this plan as a PDF?
> This uses the **Markdown PDF** VS Code extension. If it's not installed, I'll install it for you first."

If the user confirms:

1. Use the `vscode_searchExtensions_internal` tool to check whether the extension `yzane.markdown-pdf` is already installed.
2. If not installed, use the `install_extension` tool with extension ID `yzane.markdown-pdf` to install it. Inform the user it has been installed.
3. Use the `run_vscode_command` tool to run `markdown-pdf.convert` with the saved file's absolute path as the argument to generate the PDF in the same directory as the Markdown file.
4. Confirm to the user that the PDF has been exported and show the path (same directory as the `.md` file, same name with `.pdf` extension).

### Step 5 — Iterate

After saving the plan:

1. Identify the two or three sections most likely to need refinement given the specific context.
2. Ask the user whether those sections need adjusting or whether any context has changed.
3. Offer to produce a standalone Phase 1 artifact based on the role:
   - **QA Automation Developer/Engineer, QA Automation Lead, SDET, Test Architect, Performance Engineer** → offer the **Phase 1 Test Strategy document**
   - **QA Manager** → offer the **QA Governance Design document** (release criteria, defect lifecycle, escalation policy, reporting cadence)
   - **QA Analyst** → offer a **Test Design Approach and coverage charter** for the first sprint
