# Workflow

## Fixed sequence

1. Create the run directory and initialize the markdown artifact trail
2. Write `Research Brief`
3. Wait for explicit user approval of `Research Brief`
4. Write `Search Plan`
5. Wait for explicit user approval of `Search Plan`
6. Run `high-quality-source-research` for search round 1
7. Write `Source Index`
8. Write `Storyline Packet`
9. Wait for explicit user approval of `Storyline Packet`
10. Write a full `Baseline Report`
11. Run an independent `Partner Review`
12. Route the next action
13. Repeat search or rewrite rounds as needed
14. Write `Final Report` and `Evidence Gap Log`

## Milestone user-confirmation rule

The workflow has exactly three mandatory user-approval checkpoints:
- `Research Brief`
- `Search Plan`
- `Storyline Packet`

Do not proceed past each checkpoint until the user explicitly approves it or requests revisions.

Do not add routine approval stops for:
- `Follow-up Search Brief`
- additional search rounds
- normal rewrite rounds after review

If a later round proposes a narrower scope, a major thesis change, or a new dependency on human-held material, stop and ask the user to approve that change before proceeding.

## Review availability rule

Independent review must be performed by a separate agent.
If no separate agent can be run, stop the workflow and report that completion is blocked on independent review availability.
Do not substitute self-review.

## Deep-research coverage rule

For industry, market, channel, competition, or ad-spend reports, read `references/deep-research.md` and enforce source-mix coverage before drafting.

Default expectation when plausible:
- company filings or official disclosures
- consulting, association, regulator, platform, or measurement research
- broker, bank, or public capital-markets analysis

Before drafting `Baseline Report`, satisfy one of these:
- the `Source Index` shows non-company analytical support for the main sections
- the missing source classes are already documented as searched, gated, or unavailable

If the source base is still mostly company filings and broader external research likely exists, do not route to `rewrite`.
Route to `search-again` or `human-assist`.

## Brief-alignment rule

The approved `Research Brief` is the binding scope for review.
The drafter and reviewer must judge the report against the brief's `Report Goal` and `Must-Answer Questions`, not against a quietly reduced "current thesis".

If the draft only supports a narrower thesis than the approved brief:
- do not route to `pass`
- explicitly name which brief questions remain under-supported
- route to `search-again` if the missing support is likely reachable
- route to `human-assist` if the missing support is blocked or non-public

Only the user may approve a narrower scope.
The agent may propose a narrower thesis, but it must be presented as a scope change, not as if the original brief were already satisfied.

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
This artifact is for disciplined search routing, not a mandatory user-approval gate unless the search round also changes scope or requires human help.

## Full-report rule

The baseline and final report must both be real long-form reports.
For deep-research topics, they must also show real source breadth instead of stretching one source family across all claims.

Fail this rule if the draft is mainly:
- bullets without developed prose
- an outline pretending to be a report
- section stubs with one or two lines each
- a short memo when the user asked for a full report

## Review rule

The drafting agent does not approve its own work.
The partner reviewer must be a separate agent.
The partner reviewer reads the latest `Research Brief`, the latest report, the source index, and the latest search artifacts before deciding what happens next.

## Stop rule

Stop when all are true:
- the report materially answers the main question
- the report materially addresses the approved brief rather than a silently reduced thesis
- the independent partner review route is `pass`, or the only remaining blockers are human-blocked items
- the remaining limitations are documented in `Evidence Gap Log` or `Human Assist Request`

## Human-input pause rule

If gated or human-held material is the main blocker, pause optimization and output:
- current best report
- `Human Assist Request`
- `Evidence Gap Log`

Do not continue pretending the report can become complete without that input.
This pause is separate from the three normal milestone gates and exists whenever human intervention becomes the main blocker.
