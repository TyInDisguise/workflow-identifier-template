# Stage 01 — Intake

## TODO: Full build pending

---

## Purpose

Frame the user's business context, surface 5-10 candidate workflows, and select one for deep-dive documentation in stage 02.

## Inputs

| Source | File | Scope | Why |
|--------|------|-------|-----|
| User profile | `../../_config/user-profile.md` | Full file | Business context and tech comfort for calibration |

## Process

1. Read `_config/user-profile.md` to understand the user's role, company, and tech comfort.
2. Ask the user to describe the work their team does most often — surface 5-10 candidate workflows through conversational questions. Keep this pass shallow and broad; depth comes in stage 02.
3. For each candidate, capture: workflow name, rough frequency, who performs it, and why it feels like it could be improved.
4. Present the inventory to the user and ask them to select one workflow for the stage 02 deep-dive.
5. Write outputs.

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Business context | `output/business-context.md` | Markdown — company, team, industry snapshot |
| Workflow inventory | `output/workflow-inventory.md` | Markdown table — name, frequency, performer, notes |
| Selected workflow | `output/selected-workflow.md` | Markdown — name + one-paragraph description of the chosen workflow |
