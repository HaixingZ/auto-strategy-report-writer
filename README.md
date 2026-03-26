# auto-strategy-report-writer

一个面向**完整研究报告**的长流程写作 Skill。

它不是“一次搜一点资料，然后快速拼一版摘要”的工具，而是一个带有明确分工和落盘机制的 research harness：

- 先定义问题和边界
- 先做高质量资料搜索
- 再锁主线和章节
- 产出完整 baseline report
- 交给独立 partner reviewer 挑问题
- 如果缺的是内容，就继续搜索
- 如果缺的是被拦截、需登录、需内部权限的资料，就明确请求人类协助
- 文章相关部分要在对应段落或小节后补上可点击 citation，不能只写报告名称
- 全流程把关键中间状态落成 markdown 文档

## 核心设计

这个 Skill 的核心是把研究报告写作拆成 4 个角色：

1. planner
2. researcher
3. drafter
4. partner reviewer

其中最关键的约束有两个：

- **先搜再写**：正文写作之前，必须先用 `high-quality-source-research` 做第一轮资料搜索。
- **独立评审**：写报告的 agent 不能自己批准自己的报告；必须由独立 partner reviewer agent 给出 findings 和下一步动作。如果环境不支持独立 agent review，这个流程就不能宣称完成，不能拿自评兜底。

这套结构参考了 Anthropic 2026-03-24 发布的文章 [Harness design for long-running application development](https://www.anthropic.com/engineering/harness-design-long-running-apps) 中真正可迁移的原则：

- 规划者 / 生成者 / 评估者分离
- 用结构化 artifact 保存中间状态
- 评估者必须独立、具体、怀疑而不是客气
- 当问题是“信息没拿到”时，不要假装还能继续优化文字

## 工作流

完整流程如下：

1. 写 `Research Brief`
2. 写 `Search Plan`
3. 用 `high-quality-source-research` 做第 1 轮搜索
4. 写 `Source Index`
5. 写 `Storyline Packet`
6. 写完整 `Baseline Report`
7. 由独立 reviewer 写 `Partner Review`
8. 根据评审结果决定：
   - `rewrite`
   - `search-again`
   - `human-assist`
   - `pass`
9. 最终产出 `Final Report` 和 `Evidence Gap Log`

## 落盘规则

除了搜索 skill 自己在 `research/` 下保存的检索档案，这个 Skill 还会把主流程 artifact 写到：

```text
report_runs/<slug>/
```

典型文件包括：

- `01-research-brief.md`
- `02-search-plan.md`
- `03-source-index.md`
- `04-storyline-packet.md`
- `05-baseline-report.md`
- `06-partner-review-r1.md`
- `07-follow-up-search-brief-r1.md`
- `08-human-assist-request-r1.md`
- `09-revised-report-r1.md`
- `10-final-report.md`
- `11-evidence-gap-log.md`

这样做的目标是：

- 让长流程研究任务可恢复
- 让 reviewer 真正基于证据链工作
- 让人类能快速接手被卡住的环节
- 避免“最后只剩一篇稿，过程全部丢失”

## 适用范围

适合：

- 行业研究报告
- 公司研究报告
- 需要多轮搜索和迭代补料的长文档
- 可能依赖 gated source、内部材料或人类协助的研究任务

不适合：

- 只要 source packet 的请求
- 必须直接做 option ranking 的决策 memo
- 以执行排期和 owner 为核心的执行方案
