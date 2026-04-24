# Path Decision

How to walk through `shared/tool-selection-matrix.md` to recommend one
of the five paths, then load the right implementation guide
just-in-time.

## Step 1 — Sensitivity triage first

Before scoring or selecting, run the triage from
`tool-selection-matrix.md`:

- Does this workflow touch customer PII, health records, financial
  data, or anything under NDA?
- Would the user be uncomfortable if contents were logged on a vendor's
  server for 30 days?
- Is this covered by a regulation (HIPAA, PCI-DSS, GDPR, SOX)?

Capture the answer. It's needed for the override in Step 3 and for the
data handling section of every implementation guide.

## Step 2 — Apply selection rules in order

From `tool-selection-matrix.md`, apply the rules; first match wins:

1. **Data accessibility scored 1** → no path yet. Recommend solving
   data access first. Stop here; do not proceed to spec.
2. **Volume < 20 runs/month AND output is mostly boilerplate** → Path 1.
3. **Decisions are fully rule-based AND inputs are stable** → Path 2.
4. **One well-defined AI task (drafting, categorization, extraction)
   BUT the rest is manual** → Path 3.
5. **Touches 2+ systems AND has exceptions needing judgment** → Path 4.
6. **Judgment-heavy end-to-end AND stakes justify the investment** →
   Path 5.

## Step 3 — Sensitivity override

If the sensitivity triage flagged regulated data (HIPAA/PCI/NDA), push
the recommendation **one path deeper** than Step 2 suggests. Extra
control is worth the extra build cost.

- Path 1 → Path 2 (adds self-hosted n8n option)
- Path 2 → Path 3 (API-based LLM with known retention terms)
- Path 3 → Path 4 (self-hosted orchestration)
- Path 4 → Path 5 (full self-hosted + custom control)

Note the override in the qualification report.

## Step 4 — Present the recommendation

Show the user:

1. **Recommended path** — name + one plain-English sentence.
2. **What this looks like** — the concrete infrastructure picture from
   `tool-selection-matrix.md`.
3. **Who builds it** — yourself / teammate / consultant / engineer.
4. **Rough cost** — build + monthly run.
5. **Why this path, not one simpler** — what simpler tools would miss.
6. **Why this path, not one deeper** — what deeper tools would overkill.

Ask: **"Does this feel right for how you want to tackle this?"**

If the user pushes back (e.g., "I'd want to build this myself; can we
go simpler?"), treat their preference as a constraint and re-run
selection with that constraint. The user owns the choice.

## Step 5 — Load the right implementation guide (JIT)

Based on the confirmed path, load exactly ONE of:

- Path 1 → `shared/implementation-guide-path1.md`
- Path 2 → `shared/implementation-guide-path2.md`
- Path 3 → `shared/implementation-guide-path3.md`
- Path 4 or 5 → `shared/implementation-guide-path4-5.md`

Do not load the others. This is the token-saving step.

## Step 6 — Draft the implementation guide

Fill the loaded template using the workflow record + scoring decisions.
Substitution, not composition. Pull specifics from the record, don't
invent them.

## Audit before writing output

- Path recommendation matches the selection rules in
  `tool-selection-matrix.md` (or override applied with reason noted).
- "What this looks like" is in plain English, not jargon.
- The right implementation guide template was loaded and filled.
- Output filename is `output/implementation-guide.md` (consistent
  across all five paths).
