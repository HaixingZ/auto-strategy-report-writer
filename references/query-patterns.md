# 检索模式

使用从窄到宽的搜索循环。先从最可能的发行机构开始，只有在官方路径失败后才扩大范围。

## 核心操作符

- `site:domain.tld`
- `filetype:pdf`
- 引号短语，用于精确标题或主题词
- 年份过滤，如 `2024`、`2025`，或具体月份
- 主题、发行方和文档类型的中英文双语变体

## 搜索循环

### 1. 官方域名 PDF 查找

当已知可能的出版方时使用。

示例：
- `"semiconductor" filetype:pdf site:mckinsey.com`
- `"电动车" filetype:pdf site:bcg.com`
- `"AI infrastructure" "white paper" filetype:pdf site:company-domain`

### 2. 官方落地页查找

当 PDF 未被直接索引时使用。

示例：
- `"semiconductor report" site:mckinsey.com`
- `"生成式 AI" "白皮书" site:issuer-domain`
- `"2025 outlook" site:institution-domain`

### 3. 标题导向查找

当已从发现阶段获得可能的文档标题时使用。

示例：
- `"The State of AI in 2025" pdf`
- `"中国汽车行业白皮书" pdf`
- `"global chemicals outlook 2025" pdf`

### 4. 券商研报查找

使用机构官方名称加文档意图。

公开研究模式：
- `"institution name" sector outlook pdf`
- `"institution name" thematic report pdf`
- `"institution name" strategy outlook pdf`
- `"券商名" 行业 研报 pdf`
- `"券商名" 策略展望 pdf`

访问感知的回退模式：
- `"institution name" research portal sector`
- `"institution name" insights market outlook`
- `"券商名" 研究所 行业 观点`

如果官方页面存在但 PDF 受限：
- 返回官方页面
- 标注 `licensed/paywalled`
- 除非用户明确接受镜像站，否则不要用未经验证的转载替代

### 5. 白皮书查找

使用发行方加文档类别。

示例：
- `"topic" "white paper" pdf "issuer"`
- `"topic" 白皮书 pdf 机构名`
- `"topic" report pdf association`

### 6. 监管机构与交易所查找

使用主题加文档类别和管辖区域。

示例：
- `"short selling" report pdf regulator`
- `"数据要素" 指南 pdf 监管`
- `"listing rules" consultation paper pdf exchange`

## 双语扩展

当主题同时涉及中英文生态时：

1. 搜索英文主题 + 英文文档类型。
2. 搜索中文主题 + 中文文档类型。
3. 当机构名称为英文但市场在中国时，搜索混合形式。

文档类型扩展词：
- `report`
- `white paper`
- `outlook`
- `primer`
- `deck`
- `annual report`
- `investor presentation`
- `报告`
- `白皮书`
- `洞察`
- `展望`
- `研报`
- `路演材料`
- `投资者演示`

## 失败恢复

如果直接 PDF 搜索失败：
1. 搜索官方落地页
2. 不带 `site:` 搜索可能的标题
3. 搜索主题 + 发行方 + 年份
4. 在相邻的官方域名上搜索主题 + 文档类别
5. 最后才检查高质量的二手参考来源以获取原始标题和出版方

## 输出规范

对于每个保留的来源，记录：
- 标题
- 出版方
- 日期
- 来源类型
- 访问标签
- 官方页面 URL
- 直接 PDF URL（如可用）
- 一句话说明其相关性
