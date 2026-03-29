# auto-strategy-report-writer

一个面向**完整研究报告**的双 agent 长流程写作 Skill（Claude Code 插件）。

## 安装

```bash
claude plugins install "/path/to/auto-strategy-report-writer"
```

安装后重启 Claude Code 或打开新会话。

## 架构

采用双 agent 架构，参考 Anthropic《[Harness design for long-running application development](https://www.anthropic.com/engineering/harness-design-long-running-apps)》的核心原则：

- **规划/评审 Agent**（独立子 agent）：制定标准 → 评审报告 → 打分 → 路由决定
- **执行 Agent**（主会话）：搜索资料 → 写报告 → 根据评审反馈修改

核心约束：

- **先搜再写** — 搜索能力内置，不依赖外部技能
- **规划者即评审者** — 定标准的人最适合判断是否达标
- **自动迭代** — 评审-修改循环持续运行，直到质量无法再提升或信息获取受阻
- **不能悄悄缩题** — 评审必须对照已批准的 Research Brief
- **可点击 citation** — 所有引用必须是 `[标题](URL)` 格式的可点击链接
- **断点恢复** — `run-status.md` 记录完整状态，跨会话可恢复

## 工作流

1. 写 `Research Brief` → 等用户确认
2. 写 `Search Plan` → 等用户确认
3. 搜索 + 建 `Source Index` + 写 `Storyline Packet` → 等用户确认
4. 全力写报告 v1
5. 评审-修改循环（自动）：
   - `improve` — 优化逻辑结构表达
   - `search` — 补搜公开信息
   - `improve+search` — 两者都做
   - `blocked` — 暂停，记录断点，等待用户提供材料
   - `pass` — 完成
6. 产出 `final-report.md` + `evidence-gap-log.md`

## 落盘

所有中间 artifact 保存到 `report_runs/<slug>/`：

```
01-research-brief.md
02-search-plan.md
03-source-index.md
04-storyline-packet.md
05-report-v1.md
06-review-v1.md
...
run-status.md
final-report.md
evidence-gap-log.md
search-records/
```

## 插件结构

```
.claude-plugin/plugin.json
skills/auto-strategy-report-writer/SKILL.md
references/
  workflow.md              — 固定流程、路由规则
  artifact-storage.md      — 存储规范
  output-contracts.md      — artifact 格式
  scoring.md               — 评分维度和关卡
  partner-review.md        — 规划/评审 agent 职责
  deep-research.md         — 行业级来源组合
  evidence-gap.md          — 证据/缺口处理
  harness-principles.md    — 双 agent 架构原则
  source-priority.md       — 来源优先级阶梯
  china-source-map.md      — 中国市场来源地图
  query-patterns.md        — 搜索查询模式
  broker-research-playbook.md — 券商研究策略
  search-record-format.md  — 搜索存档格式
```
