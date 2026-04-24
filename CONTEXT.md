# Workflow Identifier — Stage Routing

## Pipeline

| Stage | Folder | Purpose |
|-------|--------|---------|
| 01 | `stages/01-intake/` | Frame business context, inventory 5-10 candidate workflows, select one to deep-dive |
| 02 | `stages/02-workflow-capture/` | Socratic deep-dive on the selected workflow; build As-Is record and Mermaid diagram |
| 03 | `stages/03-workflow-review/` | User scrutinizes finalized diagram and record to catch gaps |
| 04 | `stages/04-agent-qualification/` | Score against fit criteria, recommend implementation path, produce qualification report and implementation guide |

## How to Start a Run

1. Read `_config/user-profile.md`. If it is empty or missing, run `setup` first.
2. Once the profile is populated, proceed to `stages/01-intake/CONTEXT.md`.
3. Walk the stages in order. Each stage's `output/` folder is the next stage's primary input.

## Handoff Rule

Stage N produces files in `stages/0N-name/output/`; stage N+1's CONTEXT.md reads from that folder. Output files can be edited by hand between stages — the agent picks up whatever is there.

## One-Workflow Constraint

This workspace runs one workflow at a time. Each new run overwrites `stages/*/output/`. Export finished records manually before starting a new run.
