# Evidence / Assumption / Gap

## Purpose

Use this file to keep evidence discipline without over-penalizing reports that depend on interviews, internal materials, or future user input.

## Definitions

### Evidence
Information directly supported by:
- user-provided material
- available public sources
- already supplied internal documents

### Assumption
Reasoned inference that helps the report move forward, but is not fully verified.
Write it carefully and label it.

### Gap
A missing input that materially limits confidence.
A gap should not be hidden or blurred into prose.

## Required behavior

When a key point lacks support:
- do not fake certainty
- do not endlessly try to optimize around the missing input
- write an explicit gap
- explain what additional information is needed

## Standard gap template

```md
### Gap N
- Gap:
- Why it matters:
- What is needed:
- Who can provide it:
- Impact on current report:
```

## Example

```md
### Gap 1
- Gap: 缺少目标用户对该产品真实复购动因的一手反馈
- Why it matters: 这影响对增长机制是否可持续的判断
- What is needed: 5-8 位目标用户访谈或客服反馈记录
- Who can provide it: 用户、业务同学、一线访谈材料
- Impact on current report: 当前只能判断增长已发生，不能高置信解释其驱动来源
```
