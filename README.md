# Workflow Identifier

A structured workspace for identifying, documenting, and qualifying business workflows as candidates for AI agent automation. Built on the Interpreted Context Methodology (ICM) — folder structure as agent architecture. Credit to Jake Van Clief for describing and providing example versions of this process.

## What This Does

Guides a business owner or employee through a four-stage process:

| Stage | Name | What Happens |
|-------|------|-------------|
| 01 | Intake | Frame your business context, surface 5-10 candidate workflows, select one to document |
| 02 | Workflow Capture | Deep-dive interview on the selected workflow; produces an As-Is record and Mermaid flow diagram |
| 03 | Workflow Review | Side-by-side review of the diagram and record to catch missing steps or errors |
| 04 | Agent Qualification | Score the workflow against automation fit criteria; draft an agent spec for the top candidate |

## How to Start

1. Open this folder in Claude Code
2. Type `setup` — answer seven questions about your role and company (takes ~5 minutes)
3. Type `start` — begin at stage 01

If you have already completed setup, type `start` to go directly to stage 01.

## One Workflow at a Time

This workspace runs one workflow per session. Each new run overwrites the output folders. Before starting a new workflow, copy the contents of `stages/*/output/` somewhere else if you want to keep them.

## How It Works

Each stage reads a `CONTEXT.md` file that tells the agent exactly what to load, what to do, and what to produce. Outputs from one stage become inputs to the next. You can open any output file, edit it, and the next stage picks up your changes.

```
stages/01-intake/output/        → feeds stage 02
stages/02-workflow-capture/output/  → feeds stage 03
stages/03-workflow-review/output/   → feeds stage 04
stages/04-agent-qualification/output/  → final deliverables
```

## Output Files

A completed run produces:

- `workflow-record.md` — structured As-Is documentation of the workflow
- `workflow-diagram.mmd` — Mermaid flowchart (paste into mermaid.live to render)
- `elicitation-transcript.md` — full Q&A transcript
- `qualification-report.md` — automation fit scores and rationale
- `agent-spec.md` — draft specification for an AI agent to automate the workflow

## Ideal Interviewee

The person who actually performs the work — not the person who designed or manages it. They know how it's really done, not how it's supposed to be done.
