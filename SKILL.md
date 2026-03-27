---
name: auto-strategy-report-writer
description: Use when the user needs a full research report, industry study, or company analysis with nontrivial evidence needs, possible source-access gaps, and a requirement to preserve the work in markdown artifacts.
---

# Auto Strategy Report Writer

Use this skill as a **long-running research harness**, not a one-shot writer.

**REQUIRED SUB-SKILL:** Use `high-quality-source-research` before drafting the report body and again whenever review identifies evidence or coverage gaps.
For industry, market, channel, advertising, or competition topics, the first serious search pass must deliberately reach beyond company filings into consulting, association, regulator, platform, measurement, and broker or bank research when those source classes plausibly exist.

**REQUIRED PARTNER AGENT:** Use a separate partner agent to review the report. If the environment cannot run an independent agent review, do not mark the report complete and do not replace the independent review with self-review.

**REQUIRED USER GATES:** Pause for explicit user confirmation after `Research Brief`, `Search Plan`, and `Storyline Packet`. Do not add routine approval stops for each follow-up search round unless the user asks for tighter control.

## When to Use

Use when the deliverable is mainly:
- a full research report
- an industry or company study
- a report that may require several search rounds before the content is complete
- a report where some needed materials may be behind login, paywall, or internal access controls

Do not use when the main output must be:
- a simple source packet without synthesis
- a hard go/no-go decision memo with explicit option ranking
- an execution plan centered on owners, milestones, and rollout steps

## Operating Rules

1. Start with a run folder and artifact trail.
   Read `references/artifact-storage.md` and `references/output-contracts.md`.

2. Compile a stable brief before searching or drafting.
   Required fields live in `references/output-contracts.md`.
   Ask only for missing boundaries that would materially change the report.
   After writing `Research Brief`, stop for user confirmation before moving to `Search Plan`.

3. Search first, draft second.
   After writing `Search Plan`, stop for user confirmation before running search round 1.
   Use `high-quality-source-research` for the first pass.
   Read `references/deep-research.md` when the report is about an industry, market structure, channels, ad spend, competition, or any topic where mixed external evidence should exist.
   Keep the search packet and link it from the run artifacts.

4. Build a `Source Index` and `Storyline Packet` before the body draft.
   For deep-research topics, do not treat company filings alone as enough if broader external analysis is still plausibly reachable.
   The storyline should reflect both the question and the actual evidence coverage, not an idealized report structure.
   Do not silently narrow the thesis below the approved `Research Brief` just because the first search round was thin.
   After writing `Storyline Packet`, stop for user confirmation before drafting `Baseline Report`.

5. Draft a full baseline report.
   The baseline must be a real report, not an outline, slide skeleton, or abbreviated memo.

6. Cite source-dependent sections with clickable links.
   In article-like analysis sections, add clickable Markdown citations near the end of the relevant paragraph or subsection, for example `[Report Title](URL)`.
   Do not write a bare report name without a link when the source is being used as support.

7. Run an independent partner review.
   Read `references/partner-review.md` and `references/scoring.md`.
   The reviewer must be a separate agent, must return findings first, and must route the next action as `rewrite`, `search-again`, `human-assist`, or `pass`.

8. Route feedback precisely.
   If content is thin because public evidence likely exists, run another search round.
   If content is thin because the source is gated, intercepted, login-only, or human-held, write a `Human Assist Request`.
   If evidence is good enough and the problem is argumentation or prose, rewrite without searching again.
   Do not use a narrower unofficial "current thesis" to justify a pass when the approved brief is broader.

9. Stop only at the right boundary.
   Finish when the partner review passes, or when the remaining weaknesses are clearly blocked on human help and are documented in the final artifacts.

## Quick Reference

| Situation | What to do |
|---|---|
| User wants a full report | Run the full harness |
| User wants only sources | Use `high-quality-source-research`, not this skill |
| User wants milestone approvals but not constant interruptions | Pause at `Research Brief`, `Search Plan`, and `Storyline Packet`, then let follow-up search loops run without extra approval stops |
| Missing content seems publicly available | Create `Follow-up Search Brief` and search again |
| Needed source is login-only or blocked by the site | Create `Human Assist Request` |
| Independent reviewer is unavailable | Stop and state that completion is blocked until an independent agent can review |
| Industry report leans on annual reports only | Fail the deep-research gate and search consulting, broker, association, regulator, platform, or measurement sources before treating the report as complete |
| Reviewer says "acceptable for the current thesis" | Compare it back to the approved `Research Brief`; if scope was silently reduced, fail the brief-alignment gate |
| Article section cites a report by name only | Replace it with a clickable Markdown citation like `[Title](URL)` |
| Draft looks skeletal | Fail the full-report gate and expand before review |
| Drafter wants to self-approve | Do not allow it; use a separate reviewer |

## Red Flags

- you are writing the report body before running `high-quality-source-research`
- you are treating a source packet or outline as if it were already a full report
- you are about to approve a draft without an independent partner agent review
- the environment cannot run an independent reviewer, but you still want to mark the report complete
- the content is thin because evidence is missing, but you are only rewriting prose
- the source base is mostly annual reports, filings, or issuer self-description even though broader external research probably exists
- the drafter or reviewer is quietly redefining the thesis to fit the available sources instead of the approved brief
- you passed `Research Brief`, `Search Plan`, or `Storyline Packet` without getting the user's explicit confirmation first
- the needed source is blocked by login, click interception, paywall, or internal access, but you have not written `Human Assist Request`
- you are starting another search round without first writing `Follow-up Search Brief`
- a source-dependent paragraph mentions a report or article name without a clickable link
- you are about to leave key work state out of the markdown artifact trail

## Common Mistakes

- drafting before doing a serious source pass
- skipping the required user approval gates for `Research Brief`, `Search Plan`, or `Storyline Packet`
- stopping at company filings and never checking consulting, broker, association, regulator, platform, or measurement research
- letting the report quietly drift from the approved brief into a smaller "current thesis"
- letting the drafting agent grade its own report
- replacing independent review with a self-review fallback
- treating a source list as if it were already a report
- citing a report by name only instead of adding a clickable Markdown citation
- producing a shortened memo when the user asked for a full report
- continuing to rewrite when the real blocker is access to gated or internal material
- failing to save intermediate artifacts, which makes long-running work hard to resume

## References

Read these files as needed:
- `references/workflow.md` — fixed sequence, routing rules, stop rule
- `references/artifact-storage.md` — where to save markdown artifacts and how to name them
- `references/output-contracts.md` — exact headings for every artifact
- `references/deep-research.md` — source-mix expectations for true industry-grade research
- `references/partner-review.md` — reviewer posture, responsibilities, and action routing
- `references/scoring.md` — score dimensions, gates, and pass thresholds
- `references/evidence-gap.md` — Evidence / Assumption / Gap / Blocked Source handling
- `references/harness-principles.md` — the planner / drafter / evaluator principles behind the workflow
