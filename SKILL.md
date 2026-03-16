---
name: auto-strategy-report-writer
description: Write research-style strategy reports with a gated, self-improving workflow. Use when the user wants a research report, strategy report, industry analysis, research framework, report outline, or interview-informed study that does not require a hard recommendation. The skill focuses on clear structure, strong logic, useful insight, explicit Evidence/Assumption/Gap labeling, and iterative scoring until quality plateaus.
---

# Auto Strategy Report Writer

Use this skill to produce **research-type strategy reports** that aim to clarify the problem, sharpen the framework, and surface insight, without forcing a strong recommendation.

## What this skill is for

Use this skill when the deliverable is primarily:
- a research report
- an industry or company analysis report
- a report outline that will become a full report
- a structured research memo
- a report that may depend on future interviews or internal inputs

Do **not** use this skill when the user explicitly needs:
- a hard go/no-go recommendation
- a decision memo with explicit option ranking
- an execution plan with owners and milestones as the primary output

## Core operating model

Treat report writing as an **optimization loop**, not a one-shot generation task.

The system goal is:
1. produce a baseline report
2. review it against fixed dimensions
3. rewrite only the most important weaknesses
4. repeat until quality plateaus
5. stop and output the report plus evidence gaps and next-input requests

## Workflow

### 1. Compile the brief

First normalize the task into a stable brief:
- topic
- purpose
- audience
- time scope
- geography
- object definition
- must-answer questions
- known materials
- style rules
- forbidden patterns
- boundaries

If critical boundary information is missing, ask only for what is necessary to avoid a wrong report.

### 2. Lock the storyline first

Before writing the body, produce a `Storyline Packet`.

Read:
- `references/workflow.md`
- `references/output-contracts.md`

Stop after the storyline if user confirmation is needed.

### 3. Plan the modules

Split the report into modules. For each module define:
- purpose
- must-answer questions
- expected evidence needs
- acceptance focus

Keep modules stable unless the thesis itself changes.

### 4. Draft a baseline report

Generate a first integrated version that is good enough to review, not perfect.

The baseline must:
- answer the main question as far as current information allows
- clearly separate Evidence / Assumption / Gap
- avoid pretending missing information already exists
- follow the user's writing constitution

### 5. Review with fixed dimensions

Score the draft using the research-report scoring system.

Read:
- `references/scoring.md`
- `references/evidence-gap.md`

Primary score dimensions:
- Structure
- Logic
- Insight
- Expression
- Style Fit

`Evidence` is not a main optimization score. It is a **gate check**:
- mark Evidence / Assumption / Gap clearly
- never present inference as fact
- output an Evidence Gap log when information is missing

### 6. Rewrite only the highest-leverage weaknesses

Do not rewrite everything at once.

For each iteration:
- pick the 1-2 most important weaknesses
- revise only those areas
- preserve improvements already earned
- avoid adding whole new sections unless necessary

### 7. Stop when quality plateaus

Stop when all are true:
- the report is clear, logically sound, insightful, and stylistically aligned
- recent iterations show minimal score improvement
- remaining weaknesses mostly depend on outside input, interviews, or internal materials

When stopping, output:
- Final Report
- Evidence Gap Log
- Next-input Request

## Evidence policy

Use this hierarchy:
- **Evidence**: supported by user-provided material or external sources already available
- **Assumption**: reasoned inference that is useful but not fully verified
- **Gap**: information missing and required for stronger confidence

If evidence cannot improve without human input, do not force fake completeness. Instead, write a precise gap.

## Style policy

Follow explicit current-turn style rules first.

Always preserve these house rules when the user has not overridden them:
- optimize for clarity, structure, and reusable thinking
- prefer definitions, mechanisms, and business meaning over slogans
- avoid unsupported certainty
- keep the text direct and discussion-ready
- respect banned sentence patterns from the user

## Output discipline

Use lightweight Markdown only.

Preferred public artifacts:
- `Storyline Packet`
- `Baseline Report`
- `Review Round`
- `Final Report`
- `Evidence Gap Log`
- `Next-input Request`

## References

Read these files as needed:
- `references/workflow.md` — overall sequence and stop rules
- `references/output-contracts.md` — artifact formats
- `references/scoring.md` — dimensions, weights, plateau logic
- `references/evidence-gap.md` — how to label Evidence / Assumption / Gap and write gap requests
