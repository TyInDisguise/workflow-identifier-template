# Tool Selection Matrix

Maps a documented workflow to an implementation path — in plain language
a business owner can act on. Used in stage 04 to recommend what to build,
who builds it, what it costs, and what to watch out for.

**Core idea:** don't recommend tools, recommend *paths*. Each path is a
concrete picture of how the workflow gets done, who sets it up, and what
data handling looks like. The user leaves knowing whether they can DIY,
whether they need help, and what kind of help.

---

## First: is the data sensitive?

Before picking a path, ask:

- Does this workflow touch customer PII, health records, financial data,
  or anything under NDA?
- Would you be uncomfortable if the contents of this workflow were logged
  on a vendor's server for 30 days?
- Is this covered by a regulation (HIPAA, PCI-DSS, GDPR, SOX)?

**If yes to any**, the paths below still work but have real constraints.
Paths 1–3 require careful provider choice and configuration. Paths 4–5
are often *easier* to make compliant because the user controls more of
the stack. Flag data sensitivity in the qualification report.

---

## The five paths

### Path 1 — Templates & shortcuts

**In plain English:** You set up email templates, saved searches,
spreadsheet macros, or a reusable ChatGPT prompt. No connections between
tools, no subscriptions beyond what you already pay for.

- **Who builds it:** You, in an afternoon.
- **Build cost:** 1–3 hours.
- **Run cost:** $0–10/month.
- **Where it breaks:** Doesn't scale. Every instance still needs you to
  trigger it manually.
- **Data handling:** Stays local in your existing tools (email,
  spreadsheet, browser). Using ChatGPT/Claude consumer apps sends data
  to those providers — and by default *trains on it* unless you turn
  that off in settings. Never paste customer data into consumer AI chat.
- **When to upgrade:** When you're doing the same copy-paste more than
  a few times a week.

### Path 2 — Click-together automation

**In plain English:** Tools like Zapier or Make connect your existing
apps so one thing automatically triggers another. "When a form is filled,
add a row to this sheet and send this email." No code.

- **Who builds it:** You over a weekend, or a tech-comfortable teammate
  in a few hours.
- **Build cost:** 2–8 hours to learn and set up one workflow.
- **Run cost:** $20–50/month.
- **Where it breaks:** Any change in input format breaks the automation.
  A vendor changes their email layout → your Zap silently stops working.
  No judgment, no adaptability.
- **Data handling:** Data flows through Zapier/Make servers. They're
  SOC 2 compliant and don't train on your data, but they *do* retain run
  logs for 30–90 days. Fine for most business data. Not appropriate for
  HIPAA, PCI, or strict NDA data without an enterprise plan + BAA.
- **When to upgrade:** When inputs are too varied for rigid rules, or
  when you're spending more time fixing broken Zaps than they save.

### Path 3 — AI assistant for one bounded task

**In plain English:** A small AI helper that does one specific job —
drafting replies, categorizing emails, extracting data from documents,
summarizing meeting notes — inside the tools you already use.

- **Who builds it:** You if you're comfortable with ChatGPT and a little
  configuration. Better and more reliable with a consultant who sets up
  proper guardrails (evals, output format enforcement, error handling).
- **Build cost:** 4 hours DIY for a rough version. 1–3 days with a
  consultant for a reliable version.
- **Run cost:** $20–80/month depending on volume.
- **Where it breaks:** The AI occasionally invents information or goes
  off-format. Without review or guardrails, errors ship silently.
- **Data handling:** Data is sent to the LLM provider (Anthropic, OpenAI)
  via API. Default API terms: retained up to 30 days for abuse
  monitoring, **not used for training** (very different from consumer
  apps). For sensitive data, ask the provider about a Zero Data Retention
  (ZDR) agreement — available on enterprise contracts. Or use a
  self-hosted open-source model.
- **When to upgrade:** When the task needs to run automatically (not
  on-demand), handle exceptions, or coordinate multiple systems.

### Path 4 — Supervised automation

**In plain English:** A system that runs your workflow mostly
automatically and calls for help when it gets stuck. A deterministic
engine (like n8n) handles the normal runs; an AI supervisor watches,
fixes common problems, and escalates the rest to a human.

- **Who builds it:** An AI consultant or AI-enabled builder. Not a
  typical IT person — this requires familiarity with both automation
  platforms and LLM integration.
- **Build cost:** 1–3 weeks.
- **Run cost:** $100–500/month.
- **Where it breaks:** The supervisor misreads a failure and proposes
  the wrong fix. Mitigated by human-in-the-loop gates during the first
  weeks of operation.
- **Data handling:** This is where real control starts. The workflow
  engine can be **self-hosted** (your server, your data never leaves)
  while the supervisor calls an external LLM. Or go fully self-hosted
  by running a local model as the supervisor too. Trade-off: more
  initial setup and ongoing maintenance.
- **When to upgrade:** When the workflow is mission-critical, touches
  many systems, or needs to adapt to changes without constant human
  re-configuration.

### Path 5 — Full custom agent

**In plain English:** A custom-built AI agent that handles the workflow
end-to-end. It plans, acts across multiple systems, handles exceptions,
maintains state across runs, and integrates deeply with your specific
tools and data.

- **Who builds it:** An AI engineer. Multi-week project with ongoing
  maintenance.
- **Build cost:** 3–12 weeks.
- **Run cost:** $300–2,000+/month depending on volume and complexity.
- **Where it breaks:** Without evals and monitoring, behavior drifts
  silently as models update or context grows. Higher ongoing ownership
  cost than any other path.
- **Data handling:** Fully configurable. Can be built on enterprise LLM
  contracts with ZDR, private cloud deployments, or fully on-premise
  with self-hosted models. This path exists in part *because* some
  businesses need this level of control.
- **When to upgrade:** You're already at path 5 — this is the top of the
  ladder. Next moves are horizontal (more workflows) or organizational
  (build an internal AI team).

---

## How to pick a path

Apply in order; first match wins:

1. **If data accessibility scored 1 in `fit-criteria.md`** → no path
   yet. The prerequisite is getting the data into a reachable system.
   Flag this as a precursor project in the qualification report.
2. **If volume is < 20 runs/month AND the output is mostly boilerplate**
   → Path 1. Automation overhead exceeds savings.
3. **If decisions are fully rule-based AND inputs are stable** → Path 2.
4. **If one well-defined task benefits from AI (drafting,
   categorization, extraction) BUT the rest is manual** → Path 3.
5. **If the workflow touches 2+ systems AND has exceptions that need
   judgment** → Path 4.
6. **If the workflow is judgment-heavy end-to-end AND the stakes justify
   the investment** → Path 5.

Override: if data is highly sensitive (HIPAA/PCI/NDA), push the
recommendation one path deeper than the rules above suggest — the extra
control is worth the extra build cost.

---

## Output format for stage 04

In `qualification-report.md`, include:

1. **Recommended path** — one path, one sentence why.
2. **What this looks like in your week** — concrete picture of the
   workflow post-automation.
3. **Who builds it** — yourself / teammate / consultant / engineer.
4. **Rough cost** — build + monthly run.
5. **Data handling note** — specific to the user's sensitivity answer.
6. **What to do next** — two options:
   - *If you want to build this yourself:* [specific first step].
   - *If you want help:* [what kind of help, what a good engagement
     looks like].

The "what to do next" block serves users on both sides — DIY builders
get a starting point, and users who need help get honest signal about
what kind of help fits.
