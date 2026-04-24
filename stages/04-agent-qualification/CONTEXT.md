# Stage 04 — Agent Qualification

## Purpose

Score the documented workflow against `shared/fit-criteria.md`,
recommend an implementation path via `shared/tool-selection-matrix.md`,
and produce a concrete implementation guide — either a short template
(paths 1-2), a bounded AI helper spec (path 3), or a full agent spec
(paths 4-5). Optionally rank other inventory candidates when there's
enough data.

Every user leaves with at minimum: a qualification report + an
implementation guide. The form of the guide varies by path; the
commitment to ship something actionable does not.

## Inputs

| Source | File | Scope | Why |
|--------|------|-------|-----|
| Reviewed record | `../03-workflow-review/output/workflow-record-v2.md` | Full file | The workflow to qualify |
| Workflow inventory | `../01-intake/output/workflow-inventory.md` | Full file | Other candidates for rough ranking |
| Fit criteria | `../../shared/fit-criteria.md` | Full file | 8-dimension scoring rubric |
| Tool selection matrix | `../../shared/tool-selection-matrix.md` | Full file | Path definitions and selection rules |
| Scoring guide | `references/scoring-guide.md` | Full file | How to apply fit-criteria without being mechanical |
| Path decision | `references/path-decision.md` | Full file | How to walk the matrix + JIT-load the right implementation guide |
| Rough ranking | `references/rough-ranking-guide.md` | Full file | How to handle inventory candidates with shallow data |

Implementation guide templates are loaded **just-in-time** based on
the path decision — not upfront.

## Process

1. Read the reviewed workflow record from stage 03.
2. Run the sensitivity triage from `references/path-decision.md` — answer
   regulated / confidential / none. Capture the answer for later use.
3. Score the documented workflow against all 8 dimensions using
   `references/scoring-guide.md`. One-sentence rationale per dimension.
4. Compute total monthly cost: volume × time-per-run + error cost (from
   stage 02 question 20).
5. CHECKPOINT: present the scorecard + monthly cost to the user. Ask
   if any scores need adjustment before advancing.
6. Apply the selection rules in `references/path-decision.md`, including
   the sensitivity override. Arrive at one recommended path.
7. CHECKPOINT: present the path recommendation in plain English ("what
   this looks like," who builds it, cost, why this path vs. one
   simpler/deeper). Confirm before drafting.
8. Load the right implementation guide template just-in-time:
   - Path 1 → `shared/implementation-guide-path1.md`
   - Path 2 → `shared/implementation-guide-path2.md`
   - Path 3 → `shared/implementation-guide-path3.md`
   - Path 4 or 5 → `shared/implementation-guide-path4-5.md`
9. Fill the implementation guide using the workflow record + scoring
   decisions. Substitution, not composition.
10. If the stage 01 inventory has 2+ other candidates with enough data,
    apply `references/rough-ranking-guide.md` to produce
    `priority-ranking.md`. Otherwise skip it and note why in the
    qualification report.
11. Draft the qualification report: fit scorecard, monthly cost, path
    recommendation + rationale, veto flags if any, sensitivity
    override note if applied.
12. CHECKPOINT: present all drafts to the user (qualification report +
    implementation guide, plus priority ranking if produced). Confirm
    before writing to output.
13. Run the Audit below.
14. If audit passes, write the outputs.
15. If audit fails, return to the relevant step.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|------------|---------------|---------------|
| Scoring complete | 8-dimension scorecard + total + monthly cost estimate | Confirm or correct scores before path selection |
| Path selected | Path name + "what this looks like" plain-English summary + who builds it + rough cost | Confirm path before drafting implementation guide |
| Drafts complete | Qualification report + implementation guide (+ priority ranking if produced) | Confirm before writing outputs |

## Audit

Run before writing to `output/`. If any check fails, revise before saving.

| Check | Pass Condition |
|-------|---------------|
| Fit-criteria coverage | All 8 dimensions scored with one-sentence rationale |
| Veto flag | Any dimension scoring 1 is called out explicitly in the report |
| Data sensitivity | Triage answered; override applied if regulated |
| Path-rule alignment | Path recommendation matches the selection rules in `tool-selection-matrix.md` (or override noted) |
| Implementation guide completeness | Every section of the loaded guide template has either a filled value or an explicit "n/a" with reason |
| Ranking honesty | If `priority-ranking.md` produced, confidence labels present on every row and the deep-documented workflow is clearly distinguished |

## Outputs

| Artifact | Location | Format | Always produced? |
|----------|----------|--------|-----------------|
| Qualification report | `output/qualification-report.md` | Markdown — scorecard, monthly cost, path recommendation, rationale | Yes |
| Implementation guide | `output/implementation-guide.md` | Markdown — matches the loaded template for the recommended path | Yes |
| Priority ranking | `output/priority-ranking.md` | Markdown table — rough ranking of other inventory candidates with confidence labels | Only if ≥2 other candidates have enough data |
