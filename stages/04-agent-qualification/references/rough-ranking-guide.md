# Rough Ranking Guide

How to roughly rank the non-documented candidates from the stage 01
workflow inventory. Used only when the user wants a "what should I
document next" list. Skip entirely if fewer than 2 other candidates
have enough info.

## Why this is rough

The stage 01 inventory captures only five fields per candidate:
- Name
- Frequency
- Performer
- Interest reason
- Stability flag (yes/no/unsure on 6-12 month change risk)

That's enough to estimate **some** fit-criteria dimensions but not
others. Rough ranking acknowledges the gap and labels every score as
provisional. The real scoring happens only after stage 02 deep elicitation.

## Which fit-criteria dimensions can be roughly scored

**Inferrable from shallow data:**

- **Volume (dimension 2)** — frequency field gives this directly.
- **Current pain (dimension 6)** — the "interest reason" maps to pain
  level. "Causes errors all the time" = 5. "Takes forever" = 4. "Would
  be nice to speed up" = 3. No pain mentioned = 1.
- **Standardization (dimension 4)** — roughly inferrable from the
  interest reason. "Every case is different" = 1. "Mostly the same"
  = 3. Not mentioned = use 3 as a neutral.

**Not inferrable without deep data:**

- Structure (dimension 1) — need decision logic
- Data accessibility (dimension 3) — need tool/system detail
- Stakes (dimension 5) — need failure impact detail
- Handoff complexity (dimension 7) — need step detail
- Human-in-the-loop need (dimension 8) — need process detail

Score these as "n/a — needs deep documentation" rather than inventing.

## Output format

A short table in `priority-ranking.md`:

```markdown
# Priority Ranking

**Ranking is rough — based only on the shallow data from stage 01
intake. Fit scores above 1–5 dimensions are confidence-flagged; the
full 8-dimension score requires running stage 02 on each candidate.**

| Workflow | Volume | Pain | Standardization | Rough Total | Confidence |
|----------|--------|------|-----------------|-------------|------------|
| [Workflow we deep-documented] | 5 | 5 | 3 | [full 8-dim score] | Full (stage 02 complete) |
| [Candidate 2] | 5 | 4 | 3 | 12 / 15 | Rough — deep documentation recommended |
| [Candidate 3] | 3 | 4 | n/a | 7 / 10 | Rough — deep documentation recommended |
| ... | | | | | |
```

**Key elements:**
- The deep-documented workflow is always listed first with its full
  score.
- Other candidates show the 3 dimensions that can be roughly inferred.
- Confidence label is explicit on every row.
- "Rough total" is out of the dimensions actually scored, not out of
  40 — transparency beats a fake number.

## When to skip the ranking

Skip and omit `priority-ranking.md` entirely if:

- Fewer than 2 non-documented candidates have a frequency estimate AND
  an interest reason.
- The user explicitly says they don't want the ranking.
- The stage 01 inventory was tiny (2-3 total candidates).

Note the skip in the qualification report: "Not enough inventory data
to produce a useful priority ranking. Worth running stage 01 again if
you want a prioritized list."

## The lead-magnet hook

The ranking table is a natural "document the next one" prompt. Add
this line at the end of `priority-ranking.md`:

> To score any of these rigorously and get an implementation guide,
> run the interview again for that workflow. This one took ~15 minutes.

Non-pushy, accurate, and it's the honest next step for anyone who found
the first pass valuable.
