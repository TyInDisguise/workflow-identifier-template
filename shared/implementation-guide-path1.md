# Implementation Guide Template — Path 1

A fillable template for **Path 1: Templates & shortcuts** per
`tool-selection-matrix.md`. Used when the recommended path is a reusable
template, saved search, spreadsheet macro, or reusable AI prompt — no
integrations, no code.

The guide's job is to hand the user a copy-paste-ready artifact plus
just enough setup instruction to use it. This is the pure build
document; rationale and fit reasoning live in `qualification-report.md`.

---

## How to use this template

- Fill every section. If a section genuinely doesn't apply, write "n/a"
  with a one-line reason.
- This is a **substitution task**, not a composition task. Pull field
  values from the workflow record and the qualification decisions —
  don't compose fresh prose.
- Keep it scannable. Bullets beat paragraphs.
- Output filename: `output/implementation-guide.md`.

---

## Template

```markdown
# Implementation Guide: [Workflow Name]

**What you're building:** [One sentence. E.g., "A saved email template
you reuse every time a new client signs the engagement letter."]

## The template

[The actual copy-paste-ready artifact. A template email body, a
spreadsheet formula, a ChatGPT prompt, a keyboard shortcut recipe —
whatever the Path 1 recommendation is. The user should be able to
copy this and use it without translation.]

## How to set it up

Numbered list. Tool-specific, concrete.

1. [e.g., "Open Gmail → Settings → See all settings → Advanced →
   Enable Templates."]
2. [e.g., "Compose a new email → paste the template above → click the
   three-dot menu → Templates → Save draft as template."]
3. [e.g., "Give it a name you'll recognize — 'client-onboarding-v1' works."]

## How to use it each time

- **Trigger:** [when you'd reach for this — e.g., "whenever a client
  returns a signed engagement letter."]
- **Steps:** [one or two lines — e.g., "Compose a new email → Templates
  → insert → personalize the name and date → send."]
- **Expected time:** [e.g., "~30 seconds per use."]

## Where it breaks

Honest limits.

- [e.g., "Doesn't handle clients who need a different onboarding
  sequence — you'll need a second template or a new path."]
- [e.g., "Doesn't scale past 5-10 uses a week before you want real
  automation (Path 2)."]
- [e.g., "No tracking — you won't have a record of who got the template
  unless you look at your sent folder."]

## Data handling

- **Where data lives:** in your existing email / spreadsheet / local
  tool. No new services involved.
- **If you use an AI-prompt template:** check the AI tool's training
  policy. Turn off "use my data for training" in ChatGPT / Claude
  consumer settings.

## Build estimate (DIY)

[Hours or less.] This is the DIY path by design. Most Path 1
implementations are under an hour.

## What to do next

**If you want to build this yourself:** do it now. You have everything
you need above. Start with one test run — send it to yourself first to
check formatting and personalization fields.

**If this is the wrong path for you:** sign that automation needs are
past Path 1 usually looks like doing the same copy-paste more than a
few times a week. When you get there, re-run the interview and you'll
likely end up at Path 2 or Path 3.
```
