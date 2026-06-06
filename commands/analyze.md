---
name: analyze
description: 使用合适的分析技术对需求进行建模和细化——用例、数据模型、状态图等。
argument-hint: "<需要建模的功能领域或业务领域>"
uses:
  - analysis-advisor
  - use-case
  - user-story-re
  - process-modeling
  - data-modeling
  - state-modeling
  - decision-table
  - dialog-map
  - quality-attribute
outputs:
  - 包含选择理由的建模技术方案
  - 分析模型（用例、ER 图、状态图等）
  - 质量属性规约
---

# /analyze

使用与领域复杂度匹配的技术对需求进行建模。

## 调用方式

```text
/analyze Chemical expiration lifecycle — need to model states, transitions, and alert logic
```

## 工作流

1. 使用 `analysis-advisor` 选择合适的建模技术。
2. 使用 `use-case` 或 `user-story-re` 建模用户与系统的交互。
3. 使用 `process-modeling` 建模业务流程。
4. 使用 `data-modeling` 建模数据。
5. 使用 `state-modeling` 建模对象生命周期。
6. 使用 `decision-table` 捕获复杂规则。
7. 使用 `dialog-map` 映射 UI 流程。
8. 使用 `quality-attribute` 规约非功能需求。

## 检查点

- 分析技术的选择应基于领域特征（而非习惯）。
- 模型须根据需求获取的结果进行验证。
- 建模过程中发现的缺失需求须反馈到需求获取阶段。

## 后续步骤

- 运行 `/write-srs` 对分析后的需求进行规约编写。
- 如果建模揭示了需要干系人确认的空白点，运行 `/elicit`。
