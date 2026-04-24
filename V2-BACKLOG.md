# V2 Backlog

Things intentionally deferred from v1. Each item has a short reason for
punting and, where applicable, the signal that would trigger building
it.

## First-principles critical thinking references

Optional checkpoint between stages 02 and 03. Reads the captured
workflow and asks the Musk "five principles" questions against it —
*after* it's been captured faithfully. The framing: "Before we finalize
this as the canonical workflow, do you want a 10-minute sanity check on
whether this is the right workflow to automate at all?"

**Source material (to credit in the eventual files):**
- "Automation Principles for CRE Professionals" —
  https://www.adventuresincre.com/automation-principles-multiplier-framework/
- Musk's five principles: make requirements less dumb → delete → simplify
  → accelerate → automate. Automation is the last 20%, not the first 80%.
- The Multiplier Framework: audit → quantify → identify → prioritize →
  execute (Manual → Implementing → Iterating → Automating).

**Proposed files (not yet built):**
- `shared/first-principles-check.md` — sequential pre-automation audit
  based on Musk's five principles.
- `shared/multiplier-framework.md` — what to automate, in priority order,
  with the manual-to-automating phases.

**Why deferred:** stage 02's job is capturing what IS. Mixing first-
principles redesign into elicitation muddies the capture. Belongs in
its own opt-in checkpoint, sized as a distinct deliverable.

**Signal to build:** users regularly finish stage 03 and then say "now
that I see it written out, I don't think this is the right workflow
after all."

---

## Webapp infrastructure (from `webapp-handoff.md`)

Items explicitly V2 in the webapp build:

- **Branded landing page + design polish.** Functional not beautiful in
  v1. Typography, color, illustrations, marketing copy, testimonials —
  V2.
- **Automation tool recommendations in stage 04** with specific brand
  suggestions per workflow pattern. Tied to fit-criteria rubric.
  (Partially addressed by `tool-selection-matrix.md` but could go deeper.)
- **Turnstile / CAPTCHA bot gate.** Add if v1 logs show bot traffic.
  Low implementation cost; skip until data shows need.
- **Email verification before interview start.** Flip email capture from
  export-time to entry-time. Only if spend cap isn't sufficient.
- **Fingerprint-based rate limiting.** Replace IP-only limiting with
  FingerprintJS if VPN abuse becomes visible.
- **Browser fallbacks for speech-to-text** in Firefox and iOS.
- **Vercel KV / Redis for distributed rate limiting.** Current in-memory
  Map works for single-region Vercel deploys; switch for multi-region.
- **Saved interviews / user accounts.** Requires DB, auth, different
  privacy posture. V2+.
- **Zero Data Retention agreement with Anthropic** for regulated
  workflows. Requires enterprise contract.
- **Analytics** (Plausible or Umami, cookieless) when ready to measure
  conversion.
- **Custom branding / white-label** for consultants distributing to
  clients.

---

## Sibling lead magnet: workspace builder webapp

A second lead magnet that walks users through building their *own* ICM
workspace for any domain — wrapping the upstream `workspace-builder`
from Jake Van Clief's repo. Same thin-web-app architecture as the
workflow identifier.

**Why deferred:** build the first lead magnet end-to-end before adding
a second. Learn from real usage before replicating.

---

## Implementation guide architecture diagrams (paths 4-5)

Considered including Mermaid architecture diagrams in paths 4-5
implementation guides showing the deterministic engine + supervisor or
planner/executor pattern. Decided against for v1: clear prose in the
process, tool stack, and HITL sections carries the explanation. Would
add ~300-600 output tokens per run for marginal comprehension gain.

**Signal to build:** users of v1 report the implementation guide is
hard to visualize or they ask for a picture.
