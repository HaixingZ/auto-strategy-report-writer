# Workflow

## Fixed sequence

1. Create the run directory and initialize the markdown artifact trail
2. Write `Research Brief`
3. Write `Search Plan`
4. Run `high-quality-source-research` for search round 1
5. Write `Source Index`
6. Write `Storyline Packet`
7. Write a full `Baseline Report`
8. Run an independent `Partner Review`
9. Route the next action
10. Repeat search or rewrite rounds as needed
11. Write `Final Report` and `Evidence Gap Log`

## Review availability rule

Independent review must be performed by a separate agent.
If no separate agent can be run, stop the workflow and report that completion is blocked on independent review availability.
Do not substitute self-review.

## Routing rules after review

- `rewrite`
  Use when the source base is already good enough and the main problems are structure, logic, insight, expression, or style.

- `search-again`
  Use when one or more must-answer questions are thinly supported and the missing support is likely available from public or licensed external sources.

- `human-assist`
  Use when the next-best sources are blocked by login, click interception, subscription, internal access, or another access barrier the agent cannot clear alone.

- `pass`
  Use when the report is full-length, materially answers the question, passes all gates, and any remaining limitations are explicitly documented.

## Search loop rule

Every additional search round must start from a written `Follow-up Search Brief`.
Do not launch a vague second search.
Name the missing sections, missing evidence types, target source classes, and expected report impact first.

## Full-report rule

The baseline and final report must both be real long-form reports.

Fail this rule if the draft is mainly:
- bullets without developed prose
- an outline pretending to be a report
- section stubs with one or two lines each
- a short memo when the user asked for a full report

## Review rule

The drafting agent does not approve its own work.
The partner reviewer must be a separate agent.
The partner reviewer reads the latest report, the source index, and the latest search artifacts before deciding what happens next.

## Stop rule

Stop when all are true:
- the report materially answers the main question
- the independent partner review route is `pass`, or the only remaining blockers are human-blocked items
- the remaining limitations are documented in `Evidence Gap Log` or `Human Assist Request`

## Human-input pause rule

If gated or human-held material is the main blocker, pause optimization and output:
- current best report
- `Human Assist Request`
- `Evidence Gap Log`

Do not continue pretending the report can become complete without that input.
