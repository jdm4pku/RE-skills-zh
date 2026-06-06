# 命令

斜杠命令将多个需求工程技能串联为单次调用的工作流。

## 可用命令

| 命令 | 描述 | 使用的技能 |
|------|------|-----------|
| `/develop-requirements` | 完整的需求开发生命周期 | 7 个技能 |
| `/manage-requirements` | 建立变更控制、可追溯性和状态跟踪 | 6 个技能 |
| `/elicit` | 规划和执行需求获取会议 | 5 个技能 |
| `/write-srs` | 编写完整的 SRS 文档 | 5 个技能 |
| `/analyze` | 使用合适的技术对需求进行建模 | 9 个技能 |
| `/validate` | 在基线化之前进行评审和验证 | 5 个技能 |
| `/prioritize` | 对需求进行排序以确定实现优先级 | 4 个技能 |
| `/agile-re` | 敏捷需求工程工作流 | 5 个技能 |
| `/analyze-change` | 通过影响分析处理变更请求 | 4 个技能 |

## 命令的工作方式

每个命令包含：
- **YAML 前置元数据**，包括 `name`、`description`、`argument-hint`、`uses`（使用的技能）和 `outputs`
- **调用示例**，展示如何调用该命令
- **工作流**，列出逐步的技能链
- **检查点**，作为质量关卡
- **后续步骤**，指向逻辑上的下一个命令

## 示例

```text
/develop-requirements ChemTrack chemical inventory system for university labs
```

该命令串联以下技能：`vision-and-scope` -> `stakeholder-analysis` -> `context-diagram` -> `elicitation-technique-selector` -> `analysis-advisor` -> `srs-document` -> `requirements-validation-process`

## 命令流程

```
/develop-requirements ──> /manage-requirements
        │                         │
        ├── /elicit               ├── /analyze-change
        ├── /analyze              │
        ├── /write-srs            │
        ├── /validate             │
        └── /prioritize           │
                                  │
/agile-re ────────────────────────┘
```
