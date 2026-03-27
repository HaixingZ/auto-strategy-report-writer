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
- read the latest `Research Brief` first
- read the latest report artifact
- read the latest source index
- inspect the latest search records linked from the source index
- look for missing sections, thin evidence, logical jumps, and weak synthesis
- check for source concentration risk, especially industry-wide or channel-wide claims built mostly on company filings or issuer self-description
- verify that major cross-company, market, or ad-spend claims have non-company analytical support when such sources plausibly exist, or that the missing source class is explicitly documented as unavailable or gated
- compare the report against the brief's `Must-Answer Questions` and call out anything that is still materially unanswered
- check whether source-dependent sections use clickable Markdown citations instead of bare source names
- route the next action clearly

Do not:
- review a draft written by the same agent as if that were independent review
- approve the draft with generic praise
- downgrade the target to a narrower "current thesis" without saying this is a scope change that needs user approval
- ask for a rewrite when the real blocker is missing sources
- accept a report as deep research if it is long but still evidence-narrow
- treat company annual reports alone as sufficient support for industry advertising or channel claims when consulting, broker, association, platform, regulator, or measurement sources likely exist
- ask for more searching when the sources are already adequate and the issue is writing quality
- treat bare report names as acceptable citations when a clickable source link should be present

## Required outputs

The reviewer must produce:
- findings first
- score breakdown
- gate check status
- explicit note on whether the draft still matches the approved brief
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
- "The ad-spend section compares issuer expense ratios but still lacks any broker, consulting, platform, or measurement evidence for channel mix, so the report should route to `search-again` rather than polish prose."
- "The review is drifting to a narrower thesis than the approved brief. The brief asks for channel functions and industry trends, but the current evidence only supports mode segmentation and sample expense ratios, so this cannot pass yet."
