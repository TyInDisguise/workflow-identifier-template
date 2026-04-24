# Fit Criteria — Automation Readiness

A scoring rubric for evaluating whether a documented workflow is a strong
candidate for AI agent automation. Score each dimension 1–5 against the
reviewed workflow record from stage 03. Total = sum, max 40.

Use this rubric in stage 04 to produce `qualification-report.md` and to
rank candidates in `priority-ranking.md`.

## Dimensions

### 1. Structure
How rule-based is the decision logic? Can every decision be written as
explicit if/then, or does it require human judgment on ambiguous inputs?

| Score | Meaning |
|-------|---------|
| 5 | Every decision is a clear if/then. No judgment calls. |
| 3 | Most decisions are rule-based; a few require contextual judgment. |
| 1 | Core decisions require expert judgment that is hard to articulate. |

### 2. Volume
How often does this workflow run? Automation ROI scales with frequency.

| Score | Meaning |
|-------|---------|
| 5 | Daily or more. High cumulative hours per month. |
| 3 | Weekly. Meaningful time spent. |
| 1 | Monthly or less. Marginal time savings. |

### 3. Data accessibility
Where do the inputs live, and how hard is it for an agent to reach them?

| Score | Meaning |
|-------|---------|
| 5 | Inputs are in APIs, databases, or structured files the agent can read directly. |
| 3 | Inputs are in common SaaS tools (Gmail, Sheets, Slack) with available integrations. |
| 1 | Inputs live in people's heads, phone calls, or closed systems with no integration path. |

### 4. Standardization
How consistent are the inputs and outputs from run to run?

| Score | Meaning |
|-------|---------|
| 5 | Inputs and outputs follow the same format every time. |
| 3 | Mostly consistent with occasional format variation. |
| 1 | Every run looks different; inputs vary wildly. |

### 5. Stakes
What happens if the agent gets it wrong? Reversibility matters.

| Score | Meaning |
|-------|---------|
| 5 | Low stakes — mistakes are easily caught and reversed (drafts, internal notes). |
| 3 | Medium stakes — mistakes cost time or minor money but are recoverable. |
| 1 | High stakes — mistakes cost significant money, compliance exposure, or customer trust. |

(High-stakes workflows aren't disqualified — they just need stronger
human-in-the-loop gates in the agent spec.)

### 6. Current pain
Is this worth solving? Workflows that don't hurt usually don't get fixed.

| Score | Meaning |
|-------|---------|
| 5 | The user named this as a top frustration or bottleneck. Verbatim pain quote captured. |
| 3 | The user acknowledged friction but it's tolerable. |
| 1 | The user shrugged. "It's fine." |

### 7. Handoff complexity
How many people or systems does the workflow pass through?

| Score | Meaning |
|-------|---------|
| 5 | One person, one system. No handoffs. |
| 3 | 2–3 handoffs across people or systems. |
| 1 | Many handoffs; coordination is the workflow. |

Low scores here aren't always disqualifying — handoff-heavy workflows
can still automate well with orchestration — but they increase build cost.

### 8. Human-in-the-loop need
Can the agent run unattended, or does every run need review?

| Score | Meaning |
|-------|---------|
| 5 | Runs unattended. Human only sees exceptions. |
| 3 | Runs unattended with scheduled review (e.g., weekly QA sample). |
| 1 | Every output requires human approval before acting. |

## Scoring guide

| Total | Interpretation |
|-------|---------------|
| 32–40 | Strong candidate. Proceed to agent spec. |
| 24–31 | Viable. Agent spec should call out the weak dimensions explicitly. |
| 16–23 | Marginal. Document why the user might still want to build it — or recommend a non-agent solution (macro, Zap, template). |
| 8–15  | Poor fit for agent automation. Recommend human process improvement instead. |

## Notes for the qualifier

- A low score on ONE dimension can disqualify an otherwise strong workflow
  (e.g., a 1 on data accessibility means the agent literally cannot reach
  the inputs — total score is misleading).
- Always write a one-sentence rationale per dimension. A number without
  reasoning isn't useful to the user or to a future agent builder.
- If the user disagrees with your scoring, note it. Their judgment beats
  the rubric — this is a tool for thinking, not a verdict.
