# Implementation Guide Template — Path 3

A fillable template for **Path 3: AI assistant for one bounded task**
per `tool-selection-matrix.md`. Used when the recommended path is a
single bounded AI helper — drafting, categorizing, extracting,
summarizing — inside the user's existing tools. One LLM call per
invocation, no multi-step orchestration, no multi-system integration.

The guide's job is to give the user a working prompt + setup
instructions. Rationale and fit reasoning live in
`qualification-report.md`.

---

## How to use this template

- Fill every section. If a section genuinely doesn't apply, write "n/a"
  with a one-line reason.
- Substitution task: pull task definition, prompt content, and
  evaluation examples from the workflow record. Don't compose fresh
  prose where the record has answers.
- Bullets over paragraphs.
- Output filename: `output/implementation-guide.md`.

---

## Template

```markdown
# Implementation Guide: [Workflow Name]

**What you're building:** [One sentence. E.g., "An AI helper that reads
incoming support emails and tags each one with the right team — billing,
technical, or account — so your team doesn't have to sort them by hand."]

## The task

- **Input:** [what goes in. E.g., "The full text of a support email,
  including subject line."]
- **Output:** [what comes out. E.g., "A single tag: 'billing,'
  'technical,' or 'account.' Plus a one-sentence reason."]
- **One invocation does:** [one sentence. E.g., "categorizes one email
  at a time."]

## The prompt

The exact prompt the AI runs every time. Copy-paste ready.

```
[Full prompt text here. Include role framing, task definition, output
format, examples if helpful. Example:

You are a support email classifier. Read the email below and classify it
into exactly one of: billing, technical, or account.

Respond in this format:
Tag: [billing | technical | account]
Reason: [one sentence explaining why]

Email:
{email_text}
]
```

## Tool stack

A good starting place, not the only option.

| What it does | Tool | Why this one |
|--------------|------|--------------|
| The AI that classifies | [e.g., Claude by Anthropic via API] | [e.g., reliable on classification tasks, API doesn't train on your data] |
| Where it runs inside your workflow | [e.g., Zapier with the Anthropic integration, or a simple script] | [e.g., plugs directly into your existing email setup] |

## Human-in-the-loop

**Autonomy is earned through testing, not granted at launch.** Even a
bounded task should start with human review.

- **Launch posture:** you review every classification for the first
  week. Flag any you disagree with.
- **After accuracy is proven:** spot-check 10% of outputs weekly.
- **If you see a wrong classification:** flag it and add the example to
  your test set (see Evaluation below).

## Data handling

- **Where data goes:** the email content is sent to [AI provider]'s API.
- **Retention:** [API provider] retains for up to 30 days for abuse
  monitoring; **not used for training** under API terms.
- **Sensitivity check:** if emails contain customer PII or regulated
  data, request a Zero Data Retention agreement from the provider or
  use a self-hosted model.

## Evaluation plan

Before going live, test against real examples.

- **Test set:** pull the last [15–30] real cases from your workflow.
  Include easy cases, edge cases, and at least one case you remember
  being tricky.
- **Pass criteria:** the AI matches your judgment on [e.g., 90%+ of
  cases] before you trust it to run without approval.
- **If it fails:** adjust the prompt (add examples, tighten the output
  format) and re-test. Two or three rounds is normal.

## Success metrics

- **Volume handled:** [e.g., "100% of incoming emails classified within
  1 minute."]
- **Accuracy:** [e.g., "matches human judgment on 95%+ of cases during
  weekly spot-checks."]
- **Time saved:** [estimated hours/week reclaimed, derived from volume
  × time-per-classification from the workflow record.]
- **Baseline:** [current state — e.g., "15 minutes per day sorting
  emails manually; ~5 errors per week."]

## Where it breaks

- **Unfamiliar cases:** emails that don't fit any of your defined
  categories may get mis-tagged. Add an "other" category or watch for
  low-confidence outputs.
- **Format changes:** if your input format shifts (e.g., you start
  accepting emails in a new language), re-test against new examples.
- **Provider downtime:** the AI service occasionally has outages. Build
  a fallback (send to manual queue) if the workflow can't pause.

## Build estimate (DIY)

[Hours, typically 4–12]. Assumes you're comfortable with ChatGPT and
basic tool configuration. If you've never connected an AI to a tool via
API before, factor in an extra 2–4 hours to get familiar.

**If you hire help:** a consultant typically delivers this in a day or
two — they've written similar prompts and know the common failure
modes. Exact cost varies; ask for a scoped estimate.

## What to do next

**If you want to build this yourself:**
1. Test the prompt manually in ChatGPT or Claude with 5 real examples
   from your workflow.
2. If it's getting them right most of the time, wire it into your tool.
3. Run the full evaluation plan above before trusting it.

**If you want help:** for a single bounded task, a good engagement looks
like: scoping the task precisely, testing 20–30 real examples, tuning
the prompt, wiring it in, and documenting what to watch for. Typically
a few days of work.
```
