# Scoring Guide

How to apply `shared/fit-criteria.md` to the reviewed workflow record
without being mechanical. Scoring is a thinking tool, not a verdict
engine.

## Core mechanics

1. Score every dimension 1, 3, or 5 against the anchors in
   `fit-criteria.md`. A 2 or 4 is available but should be the exception
   — usually the anchors force an honest pick.
2. Write a **one-sentence rationale** for every score. Pull specifics
   from the workflow record (steps, decisions, exception list, tools).
   A number without reasoning is not useful to the user or to a future
   builder.
3. Sum the total (max 40).

## Handling veto dimensions

A low score on ONE dimension can disqualify an otherwise strong workflow.
Flag these explicitly in the qualification report — do not let a good
total mask a critical gap.

- **Data accessibility scored 1:** total is misleading. The agent
  literally cannot reach the inputs. Path recommendation: "no path yet
  — solve data access first."
- **Standardization scored 1:** automation that can't trust its inputs
  fails constantly. Recommend process improvement before automation.
- **Stakes scored 1 (high-stakes):** not disqualifying, but drives
  stronger HITL requirements and shifts the path recommendation one
  deeper (more human review).

## Computing total monthly cost

Synthesized from the workflow record, not a separate question.

- **Time spent:** volume (from section A) × time-per-run (from section
  B) = hours/month.
- **Error cost:** from section E, question 20 ("what does it cost you
  when this goes wrong"). Translate verbally if the user gave a
  qualitative answer ("customer complaints happen" → "time spent
  handling complaints + trust impact").
- **Present as:** "[N] hours/month on the workflow itself, plus [error
  cost] when it goes wrong."

Cost grounds the fit score in dollars and hours — it's what tells the
user whether the automation ROI is real.

## Presenting scores to the user

Show the scorecard as a table, not prose:

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Structure | 3 | Most decisions are rule-based; allocation method requires judgment on exceptions. |
| Volume | 5 | Daily; ~40 hours/month documented in stage 02. |
| ... | ... | ... |

Then the total and the monthly cost estimate.

Ask: **"Any scores you'd adjust?"** The user's judgment on their own
workflow beats the rubric. If they push back on a score, rewrite the
rationale to match their view or rescore — don't defend the number.

## Rough ranking other candidates

After scoring the documented workflow, optionally rank the other
candidates from the stage 01 inventory. Apply
`rough-ranking-guide.md` for this — the shallow data only supports
shallow scoring.

**Skip the ranking entirely if fewer than 2 other candidates have enough
info.** A one-candidate "ranking" isn't useful.

## Audit before advancing

Before writing outputs, confirm:
- Every fit-criteria dimension has a score + one-sentence rationale.
- Any 1-score dimension is flagged as a veto or driver.
- Total and monthly cost are both stated.
- If ranking other candidates, confidence labels are present.
