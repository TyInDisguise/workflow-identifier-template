# Implementation Guide Template — Paths 4 and 5

A fillable template for paths 4 (supervised automation) and 5 (full
custom agent) per `tool-selection-matrix.md`. Path 5 typically requires
more depth on state management, agent architecture, and tool
orchestration within the existing sections — the section list is the
same.

Path 3 uses `implementation-guide-path3.md` (lighter template).
Paths 1-2 use `implementation-guide-path1.md` and
`implementation-guide-path2.md` respectively.

This guide is the handoff document between "we documented a workflow"
and "someone can build this." It should be specific enough that a
builder could scope and price the work from it, and clear enough that
the user recognizes their own workflow in it.

---

## How to use this template

- Fill every section. If a section genuinely doesn't apply, write "n/a"
  with a one-line reason.
- Write in the user's language, not engineer shorthand. This document
  goes to the user first; if they hand it to a builder later, the
  builder can translate it themselves.
- Pull from `workflow-record-v2.md` (stage 03 output) — don't re-elicit.
- Prefer tight bullets over paragraph prose. Keep the guide scannable.

---

## Template

```markdown
# Implementation Guide: [Workflow Name]

**What this looks like:** [One to two sentences of concrete
infrastructure and implementation, in plain language. E.g., "An AI
assistant runs inside your existing Gmail, reads incoming invoices,
extracts the key fields, and drafts accounting entries in QuickBooks for
your review. You review and approve before anything is finalized."]

**Date:** [YYYY-MM-DD]
**Based on workflow record:** `stages/03-workflow-review/output/workflow-record-v2.md`

## 1. Purpose

One paragraph. What job does this system do, for whom, and why? Include
the pain quote from the workflow record if there is one.

## 2. Trigger

When does the system run?

- **Event-based:** describe the event (email arrives, form submitted,
  schedule fires, file lands in a folder).
- **Frequency:** how often does the trigger fire in a typical month?
- **Start-of-day state:** what must already be true before the system
  can run? (e.g., "the invoice must already be in the shared inbox").

## 3. Inputs

Everything the system needs to do its job.

| Input | Source | Format | Required? |
|-------|--------|--------|-----------|
| [e.g., invoice PDF] | [e.g., Gmail label "vendors"] | [PDF attachment] | Yes |
| [e.g., project code] | [subject line, "Project: XYZ"] | string | Yes |

Flag any input that isn't reachable via API or integration — that's a
prerequisite the user must solve before building.

## 4. Process

Numbered list of what the system does, in order. Each step should be
something a builder can implement and something the user recognizes
from their workflow.

Example:
1. Read the invoice PDF and extract vendor name, invoice number, amount,
   and line items.
2. Look up the project code in [system] to determine the allocation
   method.
3. Apply the allocation method to split the invoice across cost codes.
4. Create a draft entry in [accounting system].
5. If the amount exceeds [threshold], route for human approval before
   finalizing.

## 5. Decision logic

Every decision the system makes, as explicit if/then rules pulled from
the workflow record. If a decision requires judgment that can't be
reduced to rules, note it here — it'll need stronger prompting, a
human-in-the-loop gate, or examples (few-shot) to handle.

- **If** [condition] **then** [action]
- **If** [condition] **then** [action]
- **Edge cases:** [list cases the system should escalate rather than decide]

## 6. Outputs

What the system produces, and where it lands.

| Output | Destination | Format | Notifications |
|--------|-------------|--------|---------------|
| [e.g., accounting entry] | [system] | [format] | [who gets told, how] |

## 7. Human-in-the-loop gates

**Autonomy is earned through testing, not granted at launch.** Any
agent should start with human approval on every run, then graduate to
human-in-the-loop on exceptions only, then to monitoring-only, as
accuracy is proven. Never deploy a new agent with full autonomy — even
a well-spec'd agent behaves differently in the wild than in testing.

- **Launch posture:** human approval required on every run.
- **After accuracy is proven:** human review on exceptions only
  (define what counts as an exception).
- **Escalation path:** when the agent can't complete a run, who gets
  notified, how, and with what context.
- **Day-to-day monitoring:** what the user sees to know the system is
  working (dashboard, daily digest email, Slack channel, etc.).

## 8. Tool stack

A good starting place for this path, not the only stack that could do
this. Alternatives exist at every layer; these are chosen for
accessibility and track record.

| What it does | Tool | Why this one |
|--------------|------|--------------|
| The "brain" that reads and makes decisions | [e.g., Claude by Anthropic] | [e.g., strong at judgment tasks; API access doesn't train on your data] |
| Where the workflow actually runs | [e.g., n8n self-hosted] | [e.g., your data stays on your server; visual editor shows what's happening] |
| How systems talk to each other | [list specific connectors — Gmail, QuickBooks, Slack, etc.] | [one-line why each is needed] |
| Where data and logs live | [your server / vendor's cloud] | [one-line why] |

**For path 5 specifically:** add state management (where does run state
persist between steps), agent architecture pattern (planner/executor,
tool-use loops), and error-recovery mechanism as additional rows or
sub-bullets.

## 9. Data handling

Pulled from the sensitivity triage in `tool-selection-matrix.md`.

- **Sensitivity level:** [none / business-confidential / regulated]
- **Where data goes:** [list every service that sees the data]
- **Retention:** [how long data is kept at each hop]
- **Compliance needs:** [HIPAA / PCI / GDPR / NDA, or "none"]
- **Mitigations if needed:** [Zero Data Retention agreement /
  self-hosted model / on-premise deployment]

## 10. Success metrics

How the user will know the system is working.

- **Volume handled:** [% of runs completed without human intervention]
- **Accuracy:** [how correctness is measured — sample review, exception
  rate, user correction rate]
- **Time saved:** [estimated hours/week reclaimed, derived from volume
  × time-per-run captured in the workflow record]
- **Baseline:** [current state these metrics will be compared against,
  including error cost from stage 02 section E]

## 11. Known risks

Honest list of what could go wrong and how it's mitigated.

| Risk | What you're trying to avoid | Likelihood | Mitigation |
|------|------------------------------|------------|------------|
| Model invents a vendor name not in the document | An invoice logged against the wrong vendor, causing payment errors or reconciliation work | Medium | Require verbatim extraction; flag any vendor name that doesn't match your known vendor list |
| Input format changes | Silent automation failure; backlog builds before anyone notices | Medium | Monitor for extraction failures; alert on rate spikes |
| API outage | Workflow stalls | Low | Retry queue; notify operator after N failed retries |

## 12. Evaluation plan

Before going live, how will the builder verify the system works?

- **Test set:** [N representative past cases collected from the user —
  include typical cases, exceptions, and the tricky ones you remember]
- **Pass criteria:** [e.g., "matches human decision on 90%+ of test cases"]
- **Review cadence:** [how often outputs are spot-checked after launch,
  and by whom]

## 13. Build estimate (DIY)

[Range in hours or days]. This assumes you're learning as you go — if
you've never used [specific tool] before, factor in an extra [X] hours
to get familiar with it before the build itself makes sense.

**If you hire help:** a consultant or engineer will typically deliver
this noticeably faster than the DIY estimate, because they've built
similar systems before. Exact timelines vary — ask anyone you consider
for a scoped estimate after they've seen your data.

## 14. What to do next

**If you want to build this yourself:**
[Specific first step — e.g., "start with an n8n trial and build the
core flow for one vendor before generalizing."]

**If you want help, here's how good engagements tend to look:**

- **What to look for:** someone who has shipped production AI systems
  similar to what you need, or who has hands-on experience in your
  industry before moving into AI. Either one is a strong signal. Generic
  AI experience, without direct exposure to your business or problem,
  tends to be less effective — the hard part of this work is usually
  understanding the domain, not the AI.
- **What a good engagement usually includes:** a discovery conversation,
  a written plan before building starts, testing against real past
  examples from your own workflow before going live, and scope for
  iterative improvement after launch. Automations rarely land perfectly
  on the first try — the best builders expect to refine once real use
  starts.
- **A few things to be cautious of:** prices quoted before anyone has
  looked at your data, no prior work to show, no plan for testing
  against your real examples.
- **Duration and cost:** varies by consultant. Ask for a scoped estimate
  after a discovery call.

---

**Internal reference:** recommended path [4 / 5] per
`shared/tool-selection-matrix.md`.
```

---

## Notes for the qualifier

- The template is a **starting structure**, not a rigid form. If a
  workflow needs an extra section (e.g., a migration plan for moving
  off an existing manual process), add it.
- Keep plain language. A builder can translate to technical terms later;
  the user can't translate technical terms to plain language.
- Where the workflow record doesn't have an answer, say so explicitly —
  don't invent fields. Missing fields become builder questions.
- **Output filename:** `output/implementation-guide.md` (consistent
  across all five paths).
