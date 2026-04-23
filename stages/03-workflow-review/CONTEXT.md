# Stage 03 — Workflow Review

## TODO: Full build pending

---

## Purpose

Dedicated quality pass. The user reviews the finalized diagram and record side-by-side to catch missing steps, wrong ordering, and hidden decisions. No new interview questions — this is a scrutiny stage, not an elicitation stage.

## Inputs

| Source | File | Scope | Why |
|--------|------|-------|-----|
| Workflow record | `../02-workflow-capture/output/workflow-record.md` | Full file | Record to review and correct |
| Flow diagram | `../02-workflow-capture/output/workflow-diagram.mmd` | Full file | Visual to verify against the record |
| Schema | `../../shared/as-is-schema.md` | Full file | Completeness check reference |

## Process

1. Present the Mermaid diagram and the workflow record to the user side-by-side.
2. Ask the user to read through both and flag anything that looks wrong, missing, or out of order. Use targeted prompts — "Does the sequence look right?" / "Any steps that should be here but aren't?" — not open-ended questions.
3. For each correction, update the record and diagram in real time.
4. Confirm with the user that the record is accurate before writing outputs.
5. Write updated outputs.

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Reviewed diagram | `output/workflow-diagram.mmd` | Mermaid flowchart, corrected |
| Reviewed record | `output/workflow-record-v2.md` | Markdown, matches `as-is-schema.md`, all corrections applied |
