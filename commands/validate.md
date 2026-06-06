---
name: validate
description: 使用合适的正式程度评审和验证需求——走查、审查、测试或原型。
argument-hint: "<需要验证的 SRS 或需求集>"
uses:
  - requirements-review-advisor
  - requirements-validation-process
  - requirements-testing
  - prototyping-strategy
  - specification-review-checklist
outputs:
  - 包含技术选择的验证计划
  - 分类缺陷日志
  - 包含通过/未通过决定的验证报告
---

# /validate

在基线化之前验证需求——在缺陷修复成本较低时及时发现问题。

## 调用方式

```text
/validate ChemTrack SRS v1.0 — 58 requirements, EPA audit deadline in 3 months
```

## 工作流

1. 使用 `requirements-review-advisor` 选择验证方法。
2. 使用 `requirements-validation-process` 编排验证流程。
3. 使用 `requirements-testing` 进行概念测试。
4. 使用 `prototyping-strategy` 验证 UI/工作流需求。
5. 跟踪缺陷、管理返工并编写验证报告。

## 检查点

- 在正式验证之前完成自审（`specification-review-checklist`）。
- 在基线化决策之前解决所有关键和重大缺陷。
- 在返工完成后获得干系人签字确认。

## 后续步骤

- 运行 `/manage-requirements` 进行基线化并建立变更控制。
- 运行 `/write-srs` 对发现显著缺陷的章节进行返工。
