---
name: auto-strategy-report-writer
description: Use when the user needs a full research report, industry study, or company analysis that requires multiple search rounds and may face source-access gaps.
allowed-tools: [Read, Write, Edit, Glob, Grep, WebFetch, WebSearch, Bash, AskUserQuestion, Agent, TaskCreate, TaskUpdate]
---

# Auto Strategy Report Writer

## 概述

双 agent 研究报告 harness。

- **规划/评审 Agent**（通过 Agent tool 启动为独立子 agent）：制定计划、设定标准、评审报告、打分、路由决定
- **执行 Agent**（主会话 agent）：搜索资料、写报告、根据评审反馈修改
- **通信方式**：通过 artifact 文件（写入 `report_runs/<slug>/`），不通过对话历史
- 自动迭代直到质量无法再提升或信息获取受阻
- 默认产出中文报告，搜索以中文为主，聚焦中国市场

## 适用场景

适合：
- 完整研究报告
- 行业或公司研究
- 需要多轮搜索才能补齐内容的长文档
- 部分所需材料可能在付费墙、登录墙或内部权限后面的研究任务

不适合：
- 只需要 source packet 而不需要综合分析
- 需要明确选项排名的决策 memo
- 以执行排期为核心的执行方案

## 工作流概览

1. 规划/评审 agent 写 Research Brief → 等用户确认
2. 规划/评审 agent 写 Search Plan → 等用户确认
3. 执行 agent 搜索 + 建 Source Index + 写 Storyline Packet
4. 规划/评审 agent 审核 Storyline Packet → 等用户确认
5. 执行 agent 全力写报告 v1
6. 评审-修改循环：规划/评审 agent 评审打分路由 → 执行 agent 根据反馈行动 → 循环
7. 平台期检测：连续 2 轮提升 < 0.7 分且剩余弱点主要被信息获取阻塞 → 停止

详见 `references/workflow.md`

## 搜索操作规则

搜索能力内置于执行 agent，不依赖外部技能。6 步流程：

1. **分解搜索面** — 把报告需求拆成主题、地域（默认中国）、时间范围、来源类型、文档类型
2. **按优先级搜索** — 读取 `references/source-priority.md`、`references/china-source-map.md`、`references/query-patterns.md`、`references/broker-research-playbook.md`。先搜官方域名，穷尽后才扩大范围
3. **验证文档** — 确认标题、出版方、日期、原创性；优先出版方自己的 PDF URL；明确标记付费墙和镜像
4. **排序去重** — 按权威性、相关性、时效性、原创性排序；去掉薄弱摘要和 SEO 页面
5. **交付 Source Index** — 每条来源必须包含官方页 URL 和 PDF URL（如有）
6. **存档搜索记录** — 写入 `report_runs/<slug>/search-records/`，格式见 `references/search-record-format.md`，每条来源强制记录可访问链接

## 报告写作规则

- 每一版报告都必须全力写作，不存在"先交个及格版再说"
- **可点击 citation 是硬性要求**：所有依赖来源的段落必须在相关段落末尾添加可点击 Markdown 链接，格式为 `[来源标题](URL)`
- 不允许只写来源名称不加链接
- 跨公司、市场级、渠道级的论断不能仅依赖公司自述，需要非公司分析来源支撑
- 评审 agent 的关卡检查中包含"引用链接关卡"：未加链接即不通过

## 评审规则

规划/评审 agent 通过 Agent tool 作为独立子 agent 启动。

- 评审时读取：最新 Research Brief + 最新报告 + Source Index + 搜索记录
- 打分维度见 `references/scoring.md`（Coverage / Logic / Insight / Expression / Style Fit）
- 6 个关卡检查：完整报告关卡、证据卫生关卡、引用链接关卡、Brief 对齐关卡、深度研究来源组合关卡、来源充分性关卡
- 评审者必须具体、怀疑、行动导向，不泛泛表扬
- 核心优势：评审者就是制定标准的人，不存在理解偏差
- 详见 `references/partner-review.md`

## 路由逻辑

评审后路由为以下之一：

- `improve` — 优化逻辑、结构、表达（不需要新信息），自动继续
- `search` — 补搜公开信息，自动继续
- `improve+search` — 两者都做，自动继续
- `blocked` — 信息被阻塞（付费墙/登录/内部），暂停，写 run-status.md 记录断点
- `pass` — 质量已到极限，产出 final-report.md 和 evidence-gap-log.md

## 断点恢复

当路由为 `blocked` 或会话中断时：

- 自动写 `run-status.md` 到运行目录，记录当前阶段、已完成项、阻塞项、待整合材料、下一步
- 用户在新会话中提供新材料后，skill 读取 `run-status.md` + 最新评审文件，按完整标准继续迭代
- 恢复后仍然使用 skill 的全套质量标准，不退化为无 skill 的普通写作
- 详见 `references/artifact-storage.md`

## 危险信号

出现以下情况时立即停下检查：

- 你在搜索之前就在写正文
- 你把 source packet 或大纲当作完整报告
- 你准备在没有独立评审的情况下批准草稿
- 内容薄弱因为证据缺失，但你只在改写文字
- 来源主要是年报和公司自述，而更广泛的外部研究很可能存在
- 起草者或评审者在悄悄重新定义论题以适应可用来源
- 你跳过了 Research Brief、Search Plan 或 Storyline Packet 的用户确认
- 需要的来源被阻塞但你没有写 run-status.md 记录
- 你在没有先写 Follow-up Search Brief 的情况下启动新一轮搜索
- 依赖来源的段落提到了报告名称但没有可点击链接
- 搜索时只用了中文或只用了英文，没有覆盖双语
- 你准备把关键工作状态遗漏在 artifact 链之外

## 常见错误

- 在做正式来源搜索之前就开始起草
- 跳过 3 个必需用户确认节点
- 停在公司年报而从未检查咨询、券商、协会、监管、平台或测量研究
- 让报告悄悄从已批准的 brief 漂移到更小的论题
- 让执行 agent 自己评审自己的报告
- 只写报告名称而不添加可点击 Markdown 引用
- 用户要求完整报告时产出了缩短的 memo
- 真正的阻塞是缺少门控材料时继续改写
- 未保存中间 artifact，导致长流程工作难以恢复
- 搜索时不验证文档真实性，返回无效链接
- 评审时用更窄的"当前论题"替代已批准的 brief 来放行

## 引用文档

按需读取：

- `references/workflow.md` — 固定流程、路由规则、停止规则、断点恢复协议
- `references/artifact-storage.md` — artifact 保存位置、命名规则、run-status.md 规范
- `references/output-contracts.md` — 每个 artifact 的精确格式
- `references/scoring.md` — 评分维度、关卡、通过阈值
- `references/partner-review.md` — 规划/评审 agent 职责说明
- `references/deep-research.md` — 行业级研究的来源组合预期
- `references/evidence-gap.md` — 证据/假设/缺口/被阻塞来源处理
- `references/harness-principles.md` — 双 agent 架构原则
- `references/source-priority.md` — 来源优先级阶梯
- `references/china-source-map.md` — 中国市场来源地图
- `references/query-patterns.md` — 搜索查询模式
- `references/broker-research-playbook.md` — 券商研究获取策略
- `references/search-record-format.md` — 搜索档案存档格式
