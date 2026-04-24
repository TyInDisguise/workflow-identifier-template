# Stage 01 — Intake

## Purpose

Frame the user's business context, surface 5-10 candidate workflows, and
select one for deep-dive documentation in stage 02. This is the
**breadth pass** — short, surface-level questions across many workflows.
Depth comes in stage 02.

## Inputs

| Source | File | Scope | Why |
|--------|------|-------|-----|
| User profile | `../../_config/user-profile.md` | Full file | Business context and tech comfort for calibration |
| Inventory questions | `references/inventory-questions.md` | Full file | Breadth question flow and per-candidate capture |
| Selection guide | `references/selection-guide.md` | Full file | Criteria for picking one workflow for stage 02 |

## Process

1. Read `_config/user-profile.md` to understand the user's role, company,
   and tech comfort.
2. Frame the session: tell the user we'll spend a few minutes surfacing
   workflows together, then pick one to go deep on in stage 02.
3. Ask the framing questions in `inventory-questions.md` to sketch the
   business context. Capture as a short business summary.
4. Walk the inventory questions to surface 5-10 candidate workflows.
   For each candidate, capture: name, rough frequency, who performs it,
   and why it feels like it could be improved. Keep each candidate
   shallow — one or two lines each. Don't elicit process detail here.
5. After the inventory is built, CHECKPOINT: mirror the list back to
   the user. Invite them to add, remove, or edit candidates.
6. Present the inventory and help the user select one workflow using
   the criteria in `selection-guide.md`. The agent helps the user
   choose; it does not choose for them.
7. CHECKPOINT: restate the selected workflow with a one-paragraph scope
   description. Confirm before advancing.
8. Run the Audit below.
9. If audit passes, finalize the three output files.
10. If audit fails, return to the relevant step and re-elicit.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|------------|---------------|---------------|
| Business context captured | 3-line business summary (industry, team, what they do) | Confirm or correct before inventory |
| Inventory built | List of 5-10 candidates with frequency and performer | Add, remove, or edit candidates before selection |
| Workflow selected | Restated selection with one-paragraph scope description | Confirm this is the right one before stage 02 |

## Audit

Run before writing to `output/`. If any check fails, revise before saving.

| Check | Pass Condition |
|-------|---------------|
| Inventory size | 5-10 candidates (prompt for more if fewer than 5; trim if more than 10) |
| Candidate completeness | Every candidate has name, frequency, performer, interest reason, and stability flag |
| Specificity | Selected workflow is concrete (e.g., "qualifying inbound leads from the website form") — not an umbrella term ("sales process") |
| Ownership | The interviewee performs the selected workflow, or has direct handoff visibility into it |
| Pain or value | Selected workflow has at least one stated reason to automate — pain, volume, or strategic value |
| Scope | Selected workflow can be described in under 30 minutes of stage 02 depth elicitation (if broader, scope down to a subset) |

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Business context | `output/business-context.md` | Markdown — company, team, industry snapshot |
| Workflow inventory | `output/workflow-inventory.md` | Markdown table — name, frequency, performer, interest reason, stability flag |
| Selected workflow | `output/selected-workflow.md` | Markdown — name + one-paragraph scope description |
