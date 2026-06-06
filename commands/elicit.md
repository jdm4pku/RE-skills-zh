---
name: elicit
description: 规划和执行需求获取——选择技术、准备会议并捕获干系人需要。
argument-hint: "<干系人群体、功能领域或获取目标>"
uses:
  - elicitation-technique-selector
  - elicitation-interview
  - observation-analysis
  - questionnaire-design
  - requirements-elicitation-workshop
outputs:
  - 包含技术选择理由的获取策略
  - 已准备的会议指南（访谈/观察/研讨会）
  - 已捕获的需求和发现
---

# /elicit

规划和执行与干系人及上下文匹配的需求获取会议。

## 调用方式

```text
/elicit Understand lab technician workflow and pain points for chemical registration
```

## 工作流

1. 使用 `elicitation-technique-selector` 选择合适的技术。
2. 如需访谈：使用 `elicitation-interview` 进行准备。
3. 如需观察：使用 `observation-analysis` 进行准备。
4. 如需问卷：使用 `questionnaire-design` 进行设计和分发。
5. 如需研讨会：使用 `requirements-elicitation-workshop` 进行规划和引导。

## 检查点

- 在安排会议之前确认干系人的可用性。
- 根据干系人特征（领域专业知识、可用性、群组规模）验证技术选择。
- 在进入分析阶段之前审查已捕获需求的完整性。

## 后续步骤

- 运行 `/analyze` 对已捕获的需求进行建模和细化。
- 运行 `/write-srs` 将需求编写为结构化文档。
