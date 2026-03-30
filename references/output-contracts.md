# 输出契约

使用以下确切的顶级标题。

## Artifact 1 — Research Brief

```md
# Research Brief

## Topic

## Report Goal

## Audience

## Geography

## Time Scope

## Must-Answer Questions

## Constraints And Boundaries

## Source Preferences

## Full-Report Requirement
```

这是强制用户确认的 artifact。
写完 `Research Brief` 后，暂停等待用户明确确认，然后再撰写 `Search Plan`。

## Artifact 2 — Search Plan

```md
# Search Plan

## Search Facets

## Priority Source Classes

## Bilingual Query Set

## First-Pass Coverage Targets

## Known Risk Areas
```

这是强制用户确认的 artifact。
写完 `Search Plan` 后，暂停等待用户明确确认，然后再启动第一轮搜索。

在 `## Priority Source Classes` 下，默认使用多种来源类型的组合，而非单一发布方类别。对于行业、市场、竞争、渠道或广告支出类主题，在合理情况下应包含公司财报以及至少两类非公司目标来源，例如咨询或行业协会研究、监管机构或官方平台研究、测量来源，以及券商或银行分析。

在 `## First-Pass Coverage Targets` 下，标明在起草前哪些主要章节仍需要非公司分析类来源的支持。

## Artifact 3 — Source Index

```md
# Source Index

## Search Records

## Must-Use Sources

## Section Coverage Map

## Blocked Or Gated Sources

## Remaining Open Evidence Needs
```

在 `## Must-Use Sources` 中，每条来源必须包含官方页 URL 和 PDF URL（如有）。当更广泛的外部分析合理存在时，不要仅依赖公司财报。

在 `## Section Coverage Map` 中，标注哪些章节仍仅由发行方披露支撑，以及在起草前是否需要另一轮搜索。

搜索记录保存在 `report_runs/<slug>/search-records/` 下，格式参见 `references/search-record-format.md`。

## Artifact 4 — Storyline Packet

```md
# Storyline Packet

## Title

## Thesis

## Narrative Arc

## Proposed Sections

## Section Evidence Plan

## Open Questions

## Boundaries
```

这是强制用户确认的 artifact。
写完 `Storyline Packet` 后，暂停等待用户明确确认，然后再起草报告。

## Artifact 5 — 报告

```md
# 报告

## Research Question

## Executive Summary

## Report Body

## Current Evidence Limits
```

在 `## Report Body` 内部，依赖来源的段落必须包含可点击的 Markdown 引用，例如 `[来源标题](URL)`。裸名称不通过引用链接关卡。

跨公司、全市场或全渠道的论断，在更广泛的外部来源合理存在时，不应仅依赖发行方自我描述。

报告按版本递增命名：`05-report-v1.md`、`08-report-v2.md`，等等。

## Artifact 6 — 评审

```md
# 评审

## Overall Verdict

## Scores

## Gate Checks

## Findings

## Missing Or Thin Sections

## Required Next Action

## Follow-Up Search Requests

## Blocked Items
```

在 `## Findings` 中，指出 `Research Brief` 中任何仍缺乏充分支撑的 `Must-Answer Questions`。
不要在未明确标注为需要用户审批的 scope 缩减的情况下，按照一个更窄的非官方论点来进行审批。

`## Required Next Action` 的路由决定为以下之一：`improve`、`search`、`improve+search`、`blocked`、`pass`。

## Artifact 7 — Follow-up Search Brief

```md
# Follow-up Search Brief

## Why Another Search Is Needed

## Priority Gaps

## Target Source Types

## Query Additions

## Expected Report Sections Affected
```

这不是常规用户确认 artifact。
用它来规范额外的搜索轮次，仅当新一轮搜索改变了 scope 或引入了用户协助依赖时才暂停等待用户确认。

## Artifact 8 — run-status.md

```md
# 运行状态

## 当前阶段

## 已完成

## 阻塞项

## 待整合材料

## 下一步
```

断点恢复的核心文件。当路由为 `blocked` 或会话中断时写入运行目录。新会话读取此文件 + 最新评审文件继续工作。

## Artifact 9 — Final Report

```md
# Final Report

## Executive Summary

## Report Body

## What This Report Can Reliably Support

## What Still Needs Human Input
```

在 `## Report Body` 内部，依赖来源的段落必须包含可点击的 Markdown 引用，例如 `[来源标题](URL)`。裸名称不通过引用链接关卡。

跨公司、全市场或全渠道的论断，在更广泛的外部来源合理存在时，不应仅依赖发行方自我描述。

## Artifact 10 — Evidence Gap Log

```md
# Evidence Gap Log

## Confirmed Evidence

## Assumptions

## Gaps Requiring Search

### Gap N
- Gap:
- Why it matters:
- Best public path already tried:
- What is needed:
- Impact on current report:

## Gaps Requiring Human Help

### Blocked Source N
- Item:
- Why it matters:
- Best public path already tried:
- Access blocker:
- Suggested human action:
- Impact on current report:
```

`## Gaps Requiring Search` 下的每个条目使用 `### Gap N` 模板；`## Gaps Requiring Human Help` 下的每个条目使用 `### Blocked Source N` 模板。详见 `references/evidence-gap.md`。
