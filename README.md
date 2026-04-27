# Agent Skills for Software Testers

A collection of agent skills tailored for Software QA and Testing professionals. Skills can be invoked in any agentic IDE that supports the agent skills format — including GitHub Copilot, Claude Code, Cursor, Windsurf, and others.

## Learn About Agent Skills

New to agent skills? Watch: **[Agent Skills Explained: The New Way to Supercharge AI Agents](https://www.youtube.com/watch?v=L5rFa68GGKE)**

## Skills

| Skill                                                      | Description                                                        | Docs                                                                 |
| ---------------------------------------------------------- | ------------------------------------------------------------------ | -------------------------------------------------------------------- |
| [`qa-onboarding-plan`](.github/skills/qa-onboarding-plan/) | Generate a tailored 90-day onboarding plan for any QA/Testing role | [docs/skill-qa-onboarding-plan.md](docs/skill-qa-onboarding-plan.md) |

## Repository Structure

```
.github/skills/         # One folder per skill
  <skill-name>/
    SKILL.md            # Skill definition and procedure
    references/         # Supporting reference files (optional)

docs/                   # Documentation for each skill
  skill-<skill-name>.md
```

Each skill generates its output in a dedicated folder at the repo root (e.g. `onboarding-plans/`).

## How to Use a Skill

These skills work in any agentic IDE that supports the agent skills format. Invocation syntax may vary slightly by tool, but the general flow is the same:

1. Open your agentic IDE's chat or agent panel (e.g. Copilot Chat in VS Code, Cursor's agent mode, Windsurf's Cascade).
2. Invoke a skill by name, e.g. `/qa-onboarding-plan`.
3. Provide your context inline or let the skill ask for what it needs.

Example:

> `/qa-onboarding-plan SDET, senior level, joining a 30-person fintech team, Node/React/PostgreSQL, GitHub Actions`
