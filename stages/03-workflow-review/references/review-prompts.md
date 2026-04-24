# Review Prompts

Targeted prompts for the stage 03 scrutiny pass. **Not open-ended
questions** — each prompt points the user at a specific dimension of
the record so they can scan deliberately instead of staring at the whole
thing at once.

Walk the dimensions in order. Ask one prompt at a time. Update the
record in real time as corrections surface.

## Dimension 1 — Sequence

*Is the order right?*

- "Does the order of steps in the diagram match how this actually
  happens?"
- "Is there anything that shows up earlier or later than the diagram
  has it?"
- "Are there steps that happen in parallel that the diagram shows as
  sequential?"

## Dimension 2 — Completeness

*What's missing?*

- "Any steps that should be here but aren't?"
- "Any decisions you make that aren't shown as branches?"
- "Anything you do that isn't in the 'official' version of this
  workflow but happens in practice?"

## Dimension 3 — Decision rules

*Are the if/then rules right?*

- "For [decision], the rule says [rule from record]. Is that how you
  actually decide?"
- "Are there exceptions to this rule that aren't listed?"
- "Is there a case where the rule doesn't apply — where you go on
  judgment instead?"

If any decision reads as "it depends" or "sometimes," push one probe to
tighten it: "What would make you pick X vs. Y in that case?"

## Dimension 4 — Exceptions

*What breaks?*

- "The record lists [exceptions]. Are there others that happen
  regularly?"
- "Are the frequencies on these exceptions roughly right?"
- "Is there a failure mode that's rare but expensive — not frequent,
  but high-stakes when it happens?"

## Dimension 5 — Terminology

*Is everything named consistently?*

- Scan the record and diagram for the same tool, system, or entity
  referred to by different names (e.g., "the tracker" in one place,
  "Excel" in another, "the spreadsheet" in a third).
- Flag each mismatch: "The record says 'X' here and 'Y' there — same
  thing?"
- Confirm the canonical name with the user and replace throughout.

## Dimension 6 — Diagram-record alignment

*Does the picture match the text?*

- Every node in the diagram should correspond to a step, decision, or
  exception in the record.
- Every step, decision, and exception in the record should appear in
  the diagram.
- Flag any orphan nodes (in the diagram but not the record) or
  unreferenced record items (in the record but not the diagram).

## Handling corrections

- **Small correction** (rewording, a single tool name fix, a step
  inserted between two existing steps): update the record and diagram
  inline; confirm the change looks right; move on.
- **Medium correction** (a decision rule rewritten, an exception
  added, a step re-ordered): update; re-render the diagram in the
  affected region; confirm before moving on.
- **Major gap** (a whole section of the workflow missing, a
  misunderstood trigger, a skipped decision branch): apply the
  **kick-back rule** — re-enter stage 02 at the relevant section only,
  walk that section's questions, re-mirror, return to stage 03.

## When the user disagrees with what's on the page

Trust the user. The record is wrong, not them. Update it.

If they disagree with something they told you earlier in stage 02 — the
record faithfully reflects what they said, but they now see it
differently — that's fine. The review exists for exactly this reason.
Update without re-litigating.

## When nothing needs to change

Also fine. If the user reads through and confirms each dimension
without corrections, the review is done. Short reviews happen when
stage 02 went well.
