---
name: analyze-change
description: 处理需求变更请求——分类、影响分析并提出 CCB 决策建议。
argument-hint: "<变更请求描述和上下文>"
uses:
  - change-control-process
  - change-impact-analysis
  - requirements-traceability
outputs:
  - 已分类的变更请求
  - 包含工作量估算的影响分析
  - CCB 决策建议
---

# /analyze-change

将收到的变更请求通过影响分析处理为可提交 CCB 审议的建议。

## 调用方式

```text
/analyze-change CR-003: Add barcode scanning for chemical registration — requested by lab technicians
```

## 工作流

1. 使用 `change-control-process` 对变更请求类型（缺陷、增强、新功能）进行分类。
2. 使用 `requirements-traceability` 追踪受影响的需求。
3. 使用 `change-impact-analysis` 分析影响（工作量、进度、风险）。
4. 准备包含建议的 CCB 决策包。

## 检查点

- 在分析之前，变更请求须有明确的业务理由。
- 影响分析须覆盖所有受影响的工作产品（不仅仅是代码）。
- 进度和风险影响须量化，而非仅做描述。

## 后续步骤

- 将分析结果提交给 CCB 进行决策。
- 如果批准，更新需求基线和可追溯性矩阵。
- 如果延期，使用 `requirements-status-tracking` 将其添加到发布待办列表。
