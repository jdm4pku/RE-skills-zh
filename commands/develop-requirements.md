---
name: develop-requirements
description: 运行完整的需求开发生命周期，从愿景到经过验证的基线化需求。
argument-hint: "<项目、产品或系统名称及上下文>"
uses:
  - requirements-development-process
  - vision-and-scope
  - stakeholder-analysis
  - context-diagram
  - elicitation-technique-selector
  - srs-document
  - requirements-validation-process
outputs:
  - 愿景和范围文档
  - 干系人登记册
  - 包含已验证需求的基线化 SRS
---

# /develop-requirements

运行完整的需求开发生命周期，无需手动拼接各项技能。

## 调用方式

```text
/develop-requirements ChemTrack chemical inventory system for university labs
```

## 工作流

1. 使用 `vision-and-scope` 和 `stakeholder-analysis` 建立项目基础。
2. 使用 `context-diagram` 定义系统边界。
3. 使用 `elicitation-technique-selector` 选择需求获取技术。
4. 使用 `analysis-advisor` 选择合适的模型进行需求分析和建模。
5. 使用 `srs-document` 和 `writing-requirements` 在结构化的 SRS 中规约需求。
6. 使用 `requirements-validation-process` 验证需求。

## 检查点

- 在需求获取之前确认愿景和范围已批准。
- 在完成需求获取之前验证所有干系人类别均已咨询。
- 在正式验证之前，对照 `specification-review-checklist` 对 SRS 进行自审。
- 在基线化之前解决所有关键缺陷。

## 后续步骤

- 运行 `/manage-requirements` 为基线化的需求建立变更控制和可追溯性。
- 如果项目采用 Scrum/Kanban 而非传统交付方式，运行 `/agile-re`。
