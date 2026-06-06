---
name: agile-re
description: 在敏捷环境中运行需求工程——愿景、待办事项种子化、即时细化和迭代验证。
argument-hint: "<需要进行敏捷需求工程的产品或功能领域>"
uses:
  - agile-requirements-process
  - vision-and-scope
  - user-story-re
  - acceptance-criteria
  - requirements-validation-process
outputs:
  - 轻量级愿景和范围
  - 包含细化用户故事的种子产品待办列表
  - 可进入迭代开发的需求及验收标准
---

# /agile-re

在 Scrum 或 Kanban 框架下运行需求工程，无需编写重量级 SRS 文档。

## 调用方式

```text
/agile-re ChemTrack Sprint 3 — expiration management epic needs elaboration
```

## 工作流

1. 使用 `vision-and-scope` 建立轻量级愿景（Sprint 0）。
2. 使用 `user-story-re` 以史诗和用户故事填充产品待办列表。
3. 使用 `acceptance-criteria` 对用户故事进行即时细化。
4. 使用 `requirements-validation-process` 在迭代评审中进行验证。
5. 使用 `agile-requirements-process` 遵循完整的敏捷需求工程生命周期。

## 检查点

- 在填充待办列表之前已建立愿景。
- 用户故事在进入迭代之前通过 INVEST 标准。
- 在开发开始之前已编写验收标准。
- 迭代评审根据验收标准验证已交付的用户故事。

## 后续步骤

- 如果某个用户故事足够复杂，需要建模（状态图、数据模型），则运行 `/analyze`。
- 运行 `/prioritize` 对下一个迭代的待办列表进行排序。
