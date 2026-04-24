# Stage 02 — Workflow Capture

## Purpose

Deep-dive Socratic elicitation on ONE selected workflow. Produce a populated As-Is workflow record and Mermaid flow diagram.

## Inputs

| Source | File | Scope | Why |
|--------|------|-------|-----|
| Prior stage | `../01-intake/output/selected-workflow.md` | Full file | Which workflow to elicit |
| User profile | `../../_config/user-profile.md` | Full file | Calibrate tone and depth |
| Schema | `../../shared/as-is-schema.md` | Full file | Fields to populate |
| Questions | `references/question-template.md` | Full file | Question flow and coverage guarantee |
| Probing | `references/probing-patterns.md` | Full file | When and how to dig deeper |
| Mirroring | `references/mirroring-guide.md` | Full file | How to confirm understanding |

## Process

1. Load the selected workflow name from `01-intake/output/selected-workflow.md`. Confirm with the user that this is still the one to document.
2. Walk the question template covering all 20 topics across sections A-E. **The 20 topics are a coverage guarantee, not an optional menu.** Every topic gets an answer before its mirror gate. Pareto applies to depth per question and order within a section — skip the literal wording of a question whose answer is already on the table; reorder when the conversation leads naturally elsewhere; spend more turns on surprising answers, fewer on simple ones. Do not skip topics.
3. Ask ONE question at a time. Wait for the answer.
4. Apply probing patterns whenever the answer contains vague language.
5. After each section (A-E), CHECKPOINT: mirror back what you heard in the structured mini-record format (see `references/mirroring-guide.md`). Invite correction before advancing.
6. **Build artifacts incrementally and silently.** After each answer, append the corresponding fields to `workflow-record.md` and update `workflow-diagram.mmd`. Do not narrate these updates. Re-read the full record only at mirror gates or when the user asks.
7. **Phase boundaries:** After section B, after section D, and after section E, give a short progress signal (e.g., "About a third of the way through — the core workflow is captured. Next, we'll get into the decisions and handoffs."). Purposeful, not cheerleading.
8. Once all sections are populated, run the Audit below.
9. If audit passes, finalize all three output files.
10. If audit fails, return to the relevant section and re-elicit.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|------------|---------------|---------------|
| Section A complete | Structured mini-record of trigger and context fields | Correct or confirm before section B |
| Section B complete | Structured mini-record of steps, tools, and waits | Correct or confirm before section C |
| Section C complete | Structured mini-record of decisions and exceptions | Correct or confirm before section D |
| Section D complete | Structured mini-record of outputs and handoffs | Correct or confirm before section E |
| Section E complete | Structured mini-record of pain points | Correct or confirm before audit |

## Audit

Run before writing to `output/`. If any check fails, revise before saving.

| Check | Pass Condition |
|-------|---------------|
| Schema coverage | Every field in `as-is-schema.md` is populated or explicitly marked "n/a" with a reason |
| Decision rules | All decisions are written as explicit if/then, not "it depends" |
| Exception frequency | Each exception listed has an approximate frequency |
| Pain in their words | At least one pain point captured as a verbatim quote |
| Consistent tool names | Same name used for the same tool throughout (no "the spreadsheet" then "Excel" then "the tracker") |
| Trigger specificity | Trigger and frequency are both specific — not "sometimes," not "when needed" |
| Diagram alignment | Mermaid diagram reflects the final record — nodes match steps, decisions branch correctly |

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Workflow record | `output/workflow-record.md` | Markdown, matches `as-is-schema.md` |
| Flow diagram | `output/workflow-diagram.mmd` | Mermaid flowchart |
| Transcript | `output/elicitation-transcript.md` | Markdown, raw Q&A with timestamps |
