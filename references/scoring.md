# Scoring

## Primary score dimensions

Use this weighted score for the partner review:

```text
Total Score =
0.28 * Coverage
+ 0.22 * Logic
+ 0.18 * Insight
+ 0.16 * Expression
+ 0.16 * Style Fit
```

Score each dimension on a 10-point scale.

## Dimension definitions

### Coverage
- the report addresses the must-answer questions
- major sections are actually developed
- the draft reads like a full report, not a stub
- the evidence base is broad enough for the topic, not artificially narrow

### Logic
- arguments are internally consistent
- conclusions do not jump beyond support
- section-to-section reasoning holds together

### Insight
- goes beyond listing facts
- identifies mechanisms, distinctions, tradeoffs, or implications
- helps the reader think more clearly about the topic

### Expression
- prose is readable and structured
- redundancy is controlled
- definitions and transitions are clear

### Style Fit
- matches user style rules
- stays calm, useful, and discussion-ready
- avoids unsupported certainty or salesy language

## Gates

These gates are pass/fail. Do not hide them inside the numeric score.

### Full-report gate

Pass only if the draft is a genuine long-form report.
Fail if it is skeletal, abbreviated, or mostly outline text.

### Evidence hygiene gate

Pass only if:
- Evidence / Assumption / Gap are clearly separated
- unsupported claims are not written as facts
- evidence limitations are visible, not buried

### Citation link gate

Pass only if source-dependent sections use clickable Markdown citations.
Fail if the draft names reports, articles, or sources without linking them where the support is being invoked.

### Brief-alignment gate

Pass only if the draft materially addresses the approved `Research Brief`, especially the stated `Report Goal` and `Must-Answer Questions`.
Fail if the drafter or reviewer quietly narrows the thesis and then grades the report against that narrower version without user approval.

### Deep-research source-mix gate

Pass only if, for industry, market, competition, channel, or ad-spend claims where broader external sources plausibly exist:
- the draft is not built mostly on company filings alone
- major cross-company or market-wide claims have at least one non-company analytical source class behind them, or the missing class is explicitly documented as searched but unavailable or gated

### Source adequacy gate

Pass only if each major section has enough supporting material for the current confidence level.
Fail if the report is thin because the source base is weak or incomplete.

## Routing logic

- `pass`
  Use when total score is at least 8.2 / 10 and all gates pass.

- `rewrite`
  Use when gates pass or nearly pass, but the main lift is still in structure, logic, insight, expression, or style.

- `search-again`
  Use when `Brief-alignment gate`, `Source adequacy gate`, or `Deep-research source-mix gate` fails and likely public or licensed sources still exist.

- `human-assist`
  Use when `Brief-alignment gate`, `Source adequacy gate`, or `Deep-research source-mix gate` fails mainly because the needed material is gated, login-only, internal, or otherwise inaccessible to the agent.

## Plateau logic

The run is on a plateau when:
- the last 2 review rounds improve by less than about 0.7 total points each, and
- the remaining weaknesses are mostly blocked on human access or non-public inputs

When that happens, stop iterating and document the blocker clearly.
