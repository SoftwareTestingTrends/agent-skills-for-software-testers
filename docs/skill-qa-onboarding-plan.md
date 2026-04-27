# Skill: QA Onboarding Plan

A structured, role-aware 90-day onboarding plan for Software QA and Testing professionals joining a new organization.

## Files

All content lives inside the Copilot Skill folder:

| File                                                                                                                                                                                     | Description                                                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`.github/skills/qa-onboarding-plan/references/onboarding-plan-automation-developer-lead.md`](.github/skills/qa-onboarding-plan/references/onboarding-plan-automation-developer-lead.md) | Reference 90-day plan for a QA Automation Developer / Lead. Used by the skill and readable as a standalone example.                                                               |
| [`.github/skills/qa-onboarding-plan/references/onboarding-plan-qa-manager.md`](.github/skills/qa-onboarding-plan/references/onboarding-plan-qa-manager.md)                               | Reference 90-day plan for a QA Manager. People-first structure with governance framing. Used as primary reference when role is QA Manager.                                        |
| [`.github/skills/qa-onboarding-plan/references/onboarding-plan-sdet.md`](.github/skills/qa-onboarding-plan/references/onboarding-plan-sdet.md)                                           | Reference 90-day plan for an SDET. Testability-first structure with contract testing, test utilities, and embedded dev-team framing. Used as primary reference when role is SDET. |
| [`.github/skills/qa-onboarding-plan/references/role-profiles.md`](.github/skills/qa-onboarding-plan/references/role-profiles.md)                                                         | Per-role tailoring rules, section adaptations, emphasis areas, and seniority modifiers for all 7 supported roles.                                                                 |
| [`.github/skills/qa-onboarding-plan/references/constraints.md`](.github/skills/qa-onboarding-plan/references/constraints.md)                                                             | Per-constraint plan modifications for regulated industries, accessibility/WCAG, mobile-first, AI/ML products, microservices, and high-traffic platforms.                          |

## Copilot Skill: QA Onboarding Plan Generator

The primary way to use this toolkit is via the **Skill**, which is invoked as a slash command in Copilot Chat.

**Skill location:** [`.github/skills/qa-onboarding-plan/`](.github/skills/qa-onboarding-plan/)

```
.github/skills/qa-onboarding-plan/
├── SKILL.md                              # Skill definition and procedure
└── references/
    ├── onboarding-plan-automation-developer-lead.md  # Reference plan (QA Automation Developer / Lead)
    ├── onboarding-plan-qa-manager.md     # Reference plan (QA Manager)
    ├── onboarding-plan-sdet.md           # Reference plan (SDET)
    ├── role-profiles.md                  # Per-role tailoring rules
    └── constraints.md                    # Constraint-specific plan modifiers

onboarding-plans/               # Generated plans saved here (created on first run)
    └── <role-slug>-onboarding-plan.md
```

### Supported Roles

- QA Automation Developer / Engineer
- QA Automation Lead
- SDET (Software Development Engineer in Test)
- QA Manager
- Test Architect
- QA Analyst (manual or transitioning to automation)
- Performance / Load Testing Engineer

### How to Use

1. Open GitHub Copilot Chat in VS Code.
2. Type `/qa-onboarding-plan` to invoke the skill.
3. Provide your context inline (optional — the skill will ask for anything missing):

   > `/qa-onboarding-plan SDET, senior level, joining a 30-person fintech team, partial QA maturity, stack is Node/React/PostgreSQL with GitHub Actions, hybrid`

   > `/qa-onboarding-plan for my new QA Manager hire, mid-level, first QA hire, 15-person startup building an edtech SaaS product, fully remote`

4. The skill collects all inputs in a single structured round-trip (not multiple back-and-forth messages) before generating the plan.

### What the Skill Produces

A complete, role-adapted 90-day onboarding plan in Markdown, structured in three phases. The plan is **automatically saved** to `onboarding-plans/<role-slug>-onboarding-plan.md` (e.g., `onboarding-plans/sdet-onboarding-plan.md`).

After saving, the skill offers to **export the plan as a PDF** using the Markdown PDF VS Code extension — installed automatically if not already present.

- **Phase 1 — Orient & Discover (Weeks 1–4):** People, product, process, and QA landscape discovery. Ends with a signed-off Test Strategy or QA Strategy document.
- **Phase 2 — Build & Integrate (Weeks 5–8):** Hands-on delivery — framework setup, initial automation, team integration, or process design (depending on role).
- **Phase 3 — Stabilize & Scale (Weeks 9–12):** Reliability, feedback loops, documentation, and a QA roadmap for the next quarter.

Every plan includes:

- Day 1–2 first steps checklist
- Weekly goals and phase-level deliverables
- "What Good Looks Like" milestones at 30, 60, and 90 days
- Success metrics table with a **Current Baseline column** and maturity-calibrated targets
- Ongoing practices and role-appropriate reference section

### Inputs the Skill Collects

| Input                      | Examples                                                                                            |
| -------------------------- | --------------------------------------------------------------------------------------------------- |
| Plan for                   | Myself (I'm onboarding) / A new hire (I'm their manager)                                            |
| Role                       | QA Automation Lead, SDET, QA Manager, etc.                                                          |
| Seniority                  | Junior / Mid / Senior                                                                               |
| Team size and structure    | "5 devs, 1 PM, no QA team"                                                                          |
| Product type and domain    | SaaS B2B, mobile fintech, e-commerce                                                                |
| Technology stack           | React, Node, PostgreSQL, GitHub Actions                                                             |
| QA maturity                | None (first QA hire) / Partial (fragmented testing) / Established (mature QA function)              |
| Constraints or focus areas | HIPAA, PCI-DSS, SOC 2, accessibility/WCAG, mobile-first, AI/ML product, microservices, high-traffic |
| Work model                 | Fully remote / Hybrid / On-site                                                                     |

### How the Plan Is Tailored

The plan is shaped by all nine inputs — not just the role. The skill applies multiple layers of adaptation simultaneously:

| Layer               | What it changes                                                                                                                                                              |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Plan for**        | "For myself" writes in second person; "For a new hire" writes in third person and adds a Manager's Guide section with Day 1 setup, check-in cadence, and early warning signs |
| **Role profile**    | Which sections to include, skip, or rename; emphasis areas; key deliverables                                                                                                 |
| **Seniority**       | Junior extends orientation and simplifies deliverables; Senior accelerates and adds strategy ownership from Phase 1                                                          |
| **QA maturity**     | None = build from scratch; Partial = assess and consolidate; Established = audit and optimise                                                                                |
| **Constraints**     | Section-by-section modifiers — e.g. HIPAA mandates a test data strategy and compliance checklist; PCI requires synthetic card data only                                      |
| **Product domain**  | Risk prioritisation — e.g. Healthcare raises PHI and audit trail coverage; Fintech raises payment integrity and fraud vectors                                                |
| **Work model**      | Fully remote rewrites Day 1–2 and Week 1 people sections for async-first; Hybrid flags context asymmetry risk                                                                |
| **Success Metrics** | Targets anchored to QA maturity — None uses "establish baseline" framing; Established uses precise numerical targets against existing data                                   |

### Constraints Reference

The skill supports the following constraint types. Multiple constraints can apply and their modifiers stack:

| Constraint                       | Key modifications                                                                                                                                                                                             |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **HIPAA**                        | PHI mapping, mandatory test data strategy, compliance checklist as release gate, quarterly review                                                                                                             |
| **PCI-DSS**                      | Payment flow mapping, synthetic card data only, PCI release gate, audit evidence requirements                                                                                                                 |
| **SOC 2 / ISO 27001**            | Control-mapped coverage, audit evidence checklist, quarterly review                                                                                                                                           |
| **Accessibility / WCAG**         | VPAT/audit check, axe-core CI gate (Critical + Serious block merge), keyboard navigation checklist per journey, screen reader smoke test (NVDA + VoiceOver), colour contrast checks, violation count baseline |
| **Mobile-First**                 | Device lab access, device matrix, OS compatibility risk assessment, mobile framework evaluation, matrix regression gate                                                                                       |
| **AI/ML Product**                | Non-determinism testing, prompt injection scenarios, model regression baseline, statistical assertions                                                                                                        |
| **Microservices**                | Service dependency mapping, contract testing (Pact), service virtualisation, API contract CI gate                                                                                                             |
| **High-Traffic / HA**            | Traffic pattern gathering, performance as first-class risk, production-equivalent load environment, performance CI gates                                                                                      |
| **Regulated Industry (General)** | Traceability matrix, audit evidence in defect lifecycle, regulation-specific review cadence                                                                                                                   |

### PDF Export

After the plan is saved, the skill will offer to export it as a PDF:

1. Checks whether the **Markdown PDF** extension (`yzane.markdown-pdf`) is installed.
2. If not installed, installs it automatically.
3. Converts the saved `.md` file to a `.pdf` in the same folder.

No manual steps required — accept the offer in the chat and the PDF is generated.
