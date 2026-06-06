---
name: write-srs
description: 创建结构化的 SRS 文档，包含编写规范的需求、数据字典和验收标准。
argument-hint: "<需要规约的项目或功能领域>"
uses:
  - srs-document
  - writing-requirements
  - data-dictionary
  - acceptance-criteria
  - specification-review-checklist
outputs:
  - 结构化的 SRS 文档
  - 数据字典
  - 所有功能需求的验收标准
  - 自审结果
---

# /write-srs

编写一份完整的、可供评审的 SRS 文档。

## 调用方式

```text
/write-srs ChemTrack chemical registration and expiration management modules
```

## 工作流

1. 使用 `srs-document` 模板构建 SRS 结构。
2. 使用 `writing-requirements` 质量标准编写单条需求。
3. 使用 `data-dictionary` 定义所有数据元素。
4. 使用 `acceptance-criteria` 编写可测试的验收标准。
5. 在正式评审之前，对照 `specification-review-checklist` 进行自审。

## 检查点

- 每条需求都有唯一标识符。
- 所有待定项（TBD）已解决或已明确标注负责人。
- 数据字典覆盖需求中引用的所有数据元素。
- 所有功能需求都有对应的验收标准。

## 后续步骤

- 运行 `/validate` 对 SRS 进行正式评审。
- 运行 `/prioritize` 对需求按实现顺序进行排序。
