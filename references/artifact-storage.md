# Artifact Storage

All working state should be saved as markdown.

## Run directory

Create a per-report directory:

```text
report_runs/<slug>/
```

Use a short slug with the topic and date, for example:

```text
report_runs/ai-chip-packaging-260326/
```

## File sequence

Inside the run directory, save numbered files so the run can resume cleanly:

```text
01-research-brief.md
02-search-plan.md
03-source-index.md
04-storyline-packet.md
05-baseline-report.md
06-partner-review-r1.md
07-follow-up-search-brief-r1.md
08-human-assist-request-r1.md
09-revised-report-r1.md
10-final-report.md
11-evidence-gap-log.md
```

Not every run needs every file, but the numbering should remain stable.

## Search artifacts

`high-quality-source-research` writes its own archive files into:

```text
research/
```

Do not overwrite those records.
Instead, link them from `03-source-index.md` under `## Search Records`.

## Round rule

Never overwrite prior review rounds.
If the run loops, increment the round suffix:
- `06-partner-review-r2.md`
- `07-follow-up-search-brief-r2.md`
- `09-revised-report-r2.md`

This keeps the reasoning trail inspectable and makes long-running work resumable.
