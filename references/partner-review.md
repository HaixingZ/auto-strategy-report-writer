# Partner Review

## Purpose

The report writer does not grade its own work.
Use a separate partner reviewer agent to pressure-test completeness, evidence quality, and reasoning.

## Hard rule

The reviewer must be a separate agent from the drafter.
If the environment cannot provide a separate agent reviewer, the report cannot be approved as complete.
Do not replace this with self-review.

## Reviewer posture

The reviewer should be skeptical, specific, and action-oriented.

Do:
- read the latest report artifact
- read the latest source index
- inspect the latest search records linked from the source index
- look for missing sections, thin evidence, logical jumps, and weak synthesis
- check whether source-dependent sections use clickable Markdown citations instead of bare source names
- route the next action clearly

Do not:
- review a draft written by the same agent as if that were independent review
- approve the draft with generic praise
- ask for a rewrite when the real blocker is missing sources
- ask for more searching when the sources are already adequate and the issue is writing quality
- treat bare report names as acceptable citations when a clickable source link should be present

## Required outputs

The reviewer must produce:
- findings first
- score breakdown
- gate check status
- one route decision: `rewrite`, `search-again`, `human-assist`, or `pass`

## Action matrix

- `rewrite`
  The report has enough source support, but the argument, structure, or prose needs work.

- `search-again`
  One or more must-answer questions remain under-supported and the missing material is likely still reachable through external search.

- `human-assist`
  The missing material is blocked by login, paywall, internal access, click interception, or human-held files.

- `pass`
  The report is full-length, evidence-aware, and decision-useful for its intended purpose.

## Findings standard

Findings should be concrete.
Bad finding:
- "Need more depth."

Good finding:
- "The competition section names major players but does not explain the mechanism behind share shifts, so the report cannot yet support the claim that distribution reach is the main advantage."
