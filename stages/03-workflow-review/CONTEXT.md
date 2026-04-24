# Stage 03 — Workflow Review

## Purpose

Quality pass. The user reviews the finalized diagram and record
side-by-side to catch missing steps, wrong ordering, and hidden
decisions. A **scrutiny stage**, not elicitation — no new interview
questions.

## Inputs

| Source | File | Scope | Why |
|--------|------|-------|-----|
| Workflow record | `../02-workflow-capture/output/workflow-record.md` | Full file | Record to review and correct |
| Flow diagram | `../02-workflow-capture/output/workflow-diagram.mmd` | Full file | Visual to verify against the record |
| Schema | `../../shared/as-is-schema.md` | Full file | Completeness check reference |
| Review prompts | `references/review-prompts.md` | Full file | Targeted questions by review dimension |

## Process

1. Present the Mermaid diagram and the workflow record to the user
   side-by-side. Give them a moment to read through both before
   starting the targeted review.
2. Walk the review dimensions in `references/review-prompts.md` in
   order: sequence → completeness → decision rules → exceptions →
   terminology → diagram-record alignment. Ask the targeted prompts
   under each dimension, not open-ended questions.
3. For each correction the user flags, update the record and diagram
   in real time. Confirm the update with the user before moving on.
4. **Kick-back rule:** if review surfaces a major gap (a whole section
   missing, a misunderstood trigger, a skipped decision branch),
   re-enter stage 02 at just the relevant section — walk that section's
   questions, re-mirror, update the record, then return to stage 03 and
   resume. The rest of the captured work stays intact.
5. CHECKPOINT: after all dimensions have been reviewed, present a
   summary of corrections applied. Ask if anything else was missed
   before finalizing.
6. Draft the updated record as `workflow-record-v2.md` and the
   corrected diagram. Show the final versions to the user for
   confirmation.
7. Run the Audit below.
8. If audit passes, write the two output files.
9. If audit fails, return to the relevant dimension and re-review.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|------------|---------------|---------------|
| Side-by-side shown | Diagram + record rendered together | Ready to start review, or need a re-read first |
| Review complete | Summary of corrections applied across all dimensions | Anything else missed before finalizing |
| Final record drafted | Updated `workflow-record-v2.md` + corrected `workflow-diagram.mmd` | Confirm before writing to output |

## Audit

Run before writing to `output/`. If any check fails, revise before saving.

| Check | Pass Condition |
|-------|---------------|
| Sequence | User confirmed step order reflects reality |
| Completeness | All gaps identified during review have been added; no review dimension was skipped |
| Decision logic | Every decision in the record reads as an explicit if/then, not "it depends" |
| Diagram alignment | Mermaid nodes match record steps exactly; no orphan nodes or unreferenced branches |
| Terminology consistency | Same tool, system, or entity called the same name across the record and diagram |

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Reviewed diagram | `output/workflow-diagram.mmd` | Mermaid flowchart, corrected |
| Reviewed record | `output/workflow-record-v2.md` | Markdown, matches `as-is-schema.md`, all corrections applied |
