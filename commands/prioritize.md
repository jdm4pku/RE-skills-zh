---
name: prioritize
description: 选择合适的优先级排序方法，按价值、成本和风险对需求进行排序。
argument-hint: "<需求集合、约束条件和决策上下文>"
uses:
  - prioritization-advisor-re
  - moscow-prioritization
  - value-cost-risk-analysis
  - requirements-allocation
outputs:
  - 包含选择理由的优先级排序方法
  - 已排序的需求
  - 发布分配计划
---

# /prioritize

选择合适的方法并对需求进行排序以确定实现顺序。

## 调用方式

```text
/prioritize 58 ChemTrack requirements for Release 1 — EPA audit deadline, limited dev capacity
```

## 工作流

1. 使用 `prioritization-advisor-re` 选择合适的优先级排序方法。
2. 使用 `moscow-prioritization` 进行 MoSCoW 分类，或使用 `value-cost-risk-analysis` 进行价值/成本/风险评分。
3. 使用 `requirements-allocation` 将需求分配到各版本。

## 检查点

- 干系人须参与优先级排序（而非仅由业务分析师决定）。
- 业务目标驱动优先级，而非开发人员偏好。
- 必须有（Must-Have）的需求须在已知产能约束内可实现。

## 后续步骤

- 运行 `/write-srs` 对最高优先级的需求进行完整规约。
- 运行 `/manage-requirements` 对已确定优先级的需求集进行基线化。
