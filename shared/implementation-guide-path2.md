# Implementation Guide Template — Path 2

A fillable template for **Path 2: Click-together automation** per
`tool-selection-matrix.md`. Used when the recommended path is a
no-code automation via Zapier, Make, or similar — triggers and actions
connecting tools the user already has, no judgment calls.

The guide's job is to hand the user a recipe they can build in the tool
of their choice. Rationale and fit reasoning live in
`qualification-report.md`.

---

## How to use this template

- Fill every section. If a section genuinely doesn't apply, write "n/a"
  with a one-line reason.
- Substitution task: pull trigger, filter, and action values from the
  workflow record. Don't invent steps that aren't in the record.
- Tight bullets. Builders scan, they don't read.
- Output filename: `output/implementation-guide.md`.

---

## Template

```markdown
# Implementation Guide: [Workflow Name]

**What you're building:** [One sentence. E.g., "An automation that
adds new website form submissions to your CRM and sends a welcome
email, without you touching it."]

## The recipe

**Trigger:** [event + tool. E.g., "New row added in Google Sheet
'leads-intake.'"]

**Filter (if any):** [condition. E.g., "Only run if 'lead score' column
is greater than 50." If no filter is needed, write "none."]

**Actions, in order:**

1. **[Verb] in [tool]:** [what this step does. E.g., "Create contact in
   HubSpot using the row's name, email, and company fields."]
2. **[Verb] in [tool]:** [next step. E.g., "Send email via Gmail using
   the 'welcome-new-lead' template to the contact's email address."]
3. **[Verb] in [tool]:** [if more. E.g., "Post to the #new-leads Slack
   channel with contact name and source."]

## Recommended tool

[Zapier / Make / n8n — pick one based on the user's existing stack and
comfort level. Zapier is the safe default for non-technical users;
n8n self-hosted if data sensitivity from `tool-selection-matrix.md`
demands it.]

**Why this one:** [one line — e.g., "Zapier has the most beginner-
friendly interface and native integrations for every tool in this
recipe."]

## Monthly cost estimate

- **Tool subscription:** [~$20–50/mo depending on volume tier]
- **Volume this plan supports:** [number of runs/month at the tier above]
- **Upgrade trigger:** [when you'd need to bump the tier]

## How to set it up

Tool-by-tool, numbered.

1. [e.g., "Sign up for Zapier (free tier is fine to start)."]
2. [e.g., "Click 'Create Zap' → pick Google Sheets as the trigger app
   → authorize your account → select the 'leads-intake' sheet."]
3. [e.g., "Add a Filter step → set condition: 'Lead score' is greater
   than 50."]
4. [e.g., "Add Action → HubSpot → Create Contact → map name, email,
   company fields from the trigger data."]
5. [continue for each action step...]
6. [e.g., "Test the Zap with one real row → confirm the contact was
   created and the email sent → turn the Zap on."]

## Where it breaks

Honest limits.

- **Input format change:** if the source tool changes field names or
  layouts, the automation silently stops working. Check it weekly the
  first month.
- **Rigid logic:** any case not covered by the filter gets sent through
  the same path. If the workflow has judgment-based branches, you'll
  outgrow this path.
- **Error handling is minimal:** failures show up in a Zapier "error"
  inbox — if you don't check it, you won't know.

## Data handling

- **Where data goes:** through [Zapier / Make / n8n] servers between
  source and destination.
- **Retention:** [tool] keeps run logs for 30–90 days.
- **Sensitivity check:** not appropriate for HIPAA, PCI, or strict NDA
  data without an enterprise plan + BAA. For regulated data, consider
  self-hosted n8n (moves you toward Path 4).

## Maintenance expectations

- **Weekly in month one:** check the error log.
- **Monthly ongoing:** spot-check a few runs to confirm data is landing
  correctly.
- **On tool updates:** when source or destination tools announce API or
  UI changes, test the Zap before they roll out.

## Build estimate (DIY)

[Hours, typically 2–8]. Assumes you're learning as you go — if you've
never used [Zapier / Make] before, factor in an extra 1–2 hours to get
familiar with the interface.

**If you hire help:** a consultant will typically deliver this in a
fraction of the time because they've built dozens of these. Exact cost
varies — ask for a scoped estimate after a 15-minute call.

## What to do next

**If you want to build this yourself:** sign up for the recommended
tool's free tier and build the first action step. Get one thing working
end-to-end before adding the rest.

**If you want help:** for a single-recipe Path 2 build, most consultants
quote in hours, not days. A good engagement includes: scoping the
recipe, building it, testing with your real data, and handing off with
maintenance notes.
```
