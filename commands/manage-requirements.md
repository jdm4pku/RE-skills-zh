---
name: manage-requirements
description: 为基线化的需求建立和运行需求管理——变更控制、可追溯性和状态跟踪。
argument-hint: "<项目名称和基线上下文>"
uses:
  - requirements-management-process
  - requirements-baselining
  - change-control-process
  - change-impact-analysis
  - requirements-traceability
  - requirements-status-tracking
outputs:
  - 包含版本控制的基线化需求
  - 变更控制委员会章程和流程
  - 可追溯性矩阵
  - 状态跟踪仪表板
---

# /manage-requirements

在需求基线化之后，建立完整的需求管理基础设施。

## 调用方式

```text
/manage-requirements ChemTrack Release 1 — 58 baselined requirements, EPA audit deadline in 3 months
```

## 工作流

1. 使用 `requirements-baselining` 建立需求基线。
2. 使用 `change-control-process` 建立 CCB 和变更控制流程。
3. 使用 `requirements-traceability` 构建可追溯性矩阵。
4. 使用 `requirements-status-tracking` 建立状态跟踪。
5. 使用 `change-impact-analysis` 处理后续变更。

## 检查点

- 在激活变更控制之前，基线须经干系人批准。
- 可追溯性矩阵须将每条需求链接到业务目标和测试用例。
- 变更控制流程须有明确的决策标准和升级路径。

## 后续步骤

- 收到变更请求时，运行 `/analyze-change`。
- 运行 `/develop-requirements` 为下一个版本进行迭代开发。
