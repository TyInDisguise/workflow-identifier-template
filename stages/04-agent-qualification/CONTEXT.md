# Stage 04 — Agent Qualification

## TODO: Full build pending

---

## Purpose

Score the documented workflow against automation fit criteria, rank it against the full inventory from stage 01, and draft an agent spec for the top candidate.

## Inputs

| Source | File | Scope | Why |
|--------|------|-------|-----|
| Reviewed record | `../03-workflow-review/output/workflow-record-v2.md` | Full file | The workflow to qualify |
| Fit criteria | `../../shared/fit-criteria.md` | Full file | Scoring dimensions for automation readiness |
| Tool selection matrix | `../../shared/tool-selection-matrix.md` | Full file | Which automation tools fit which workflow types |
| Agent spec template | `../../shared/agent-spec-template.md` | Full file | Structure for the output spec |

## Process

1. Read the reviewed workflow record.
2. Score the workflow against each dimension in `fit-criteria.md`. Produce a scored summary.
3. Pull the workflow inventory from `01-intake/output/workflow-inventory.md` and rank all candidates by fit score.
4. For the top-ranked candidate (which may or may not be the one just documented), draft an agent spec using `agent-spec-template.md`.
5. Write outputs.

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Qualification report | `output/qualification-report.md` | Markdown — fit scores and rationale per dimension |
| Priority ranking | `output/priority-ranking.md` | Markdown table — all inventoried workflows ranked by score |
| Agent spec | `output/agent-spec.md` | Markdown, matches `agent-spec-template.md` |
