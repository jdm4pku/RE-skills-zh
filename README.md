# RE-Skills-zh — 面向 AI 智能体的需求工程技能库

```text
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│   ██████╗ ███████╗    ███████╗██╗  ██╗██╗██╗     ██╗     ███████╗│
│   ██╔══██╗██╔════╝    ██╔════╝██║ ██╔╝██║██║     ██║     ██╔════╝│
│   ██████╔╝█████╗      ███████╗█████╔╝ ██║██║     ██║     ███████╗│
│   ██╔══██╗██╔══╝      ╚════██║██╔═██╗ ██║██║     ██║     ╚════██║│
│   ██║  ██║███████╗    ███████║██║  ██╗██║███████╗███████╗███████║│
│   ╚═╝  ╚═╝╚══════╝    ╚══════╝╚═╝  ╚═╝╚═╝╚══════╝╚══════╝╚══════╝│
│                                                                  │
│   45 个需求工程技能 · 覆盖 8 个生命周期阶段                      │
│   Claude Code · Codex · 以及任何能读取 Markdown 的 AI 智能体     │
│                                                                  │
│   v1.0 · 2026 年 4 月 · 基于《软件需求》第三版                  │
└──────────────────────────────────────────────────────────────────┘
```

**让你的 AI 智能体（以及你自己）掌握专业级的需求工程方法。**

45 个经过验证的技能，覆盖从业务愿景到变更管理的完整需求工程生命周期。每个技能都教授技术背后的"为什么"，提供 AI 可执行的分步指导，并包含模板、范例和交叉引用。

基于 Karl Wiegers & Joy Beatty 的《软件需求》第三版（*Software Requirements, Third Edition*）——需求工程实践的权威参考。

**适用平台：** Claude Code、Codex，以及任何能读取结构化 Markdown 的 AI 智能体。

> **如果觉得有用，请给个 Star 支持一下！** 你的 Star 是我们持续改进这个技能库的最大动力。

---

## 这是什么

一套完整的需求工程技能库，按 **8 个阶段**组织，覆盖**需求开发**（获取、分析、规约、验证）和**需求管理**（基线化、变更控制、追踪、状态跟踪）。

每个技能遵循标准结构——目的、关键概念、应用步骤、示例、常见陷阱、参考资料——并包含填空模板、基于统一场景（ChemTrack 化学试剂库存系统）的完整范例，以及与相关技能的交叉引用。

---

## 三层架构

```text
┌───────────────────────────────────────────────────────────────┐
│  工作流技能 (8)                                                │
│  跨越数天到数周的端到端 RE 流程                                │
│  示例："运行完整的需求开发生命周期"                             │
└───────────────────────────────────────────────────────────────┘
                         ↓ 编排
┌───────────────────────────────────────────────────────────────┐
│  交互式技能 (7)                                                │
│  通过自适应问题引导发现，提供推荐方案                           │
│  示例："我应该使用哪种需求获取技术？"                           │
└───────────────────────────────────────────────────────────────┘
                         ↓ 使用
┌───────────────────────────────────────────────────────────────┐
│  组件技能 (29)                                                 │
│  针对特定 RE 交付物的模板                                      │
│  示例："编写一份用例规约"                                      │
└───────────────────────────────────────────────────────────────┘
```

---

## 快速开始

| 你想要... | 从这里开始 |
|-----------|-----------|
| 启动新项目 | [`vision-and-scope`](skills/vision-and-scope/SKILL.md) → [`stakeholder-analysis`](skills/stakeholder-analysis/SKILL.md) |
| 规划需求获取 | [`elicitation-technique-selector`](skills/elicitation-technique-selector/SKILL.md) → [`requirements-elicitation-workshop`](skills/requirements-elicitation-workshop/SKILL.md) |
| 编写需求 | [`srs-document`](skills/srs-document/SKILL.md) + [`writing-requirements`](skills/writing-requirements/SKILL.md) |
| 需求建模 | [`analysis-advisor`](skills/analysis-advisor/SKILL.md) → 选择用例、流程模型、数据模型等 |
| 评审需求 | [`requirements-review-advisor`](skills/requirements-review-advisor/SKILL.md) → [`requirements-validation-process`](skills/requirements-validation-process/SKILL.md) |
| 优先级排序 | [`prioritization-advisor-re`](skills/prioritization-advisor-re/SKILL.md) → MoSCoW 或 价值/成本/风险 |
| 管理变更 | [`change-control-advisor`](skills/change-control-advisor/SKILL.md) → [`change-control-process`](skills/change-control-process/SKILL.md) |
| 敏捷 RE | [`agile-requirements-process`](skills/agile-requirements-process/SKILL.md) |
| 运行完整 RE 生命周期 | [`requirements-development-process`](skills/requirements-development-process/SKILL.md) |

**详细的安装和使用教程请参阅 [`docs/学生使用指南.md`](docs/学生使用指南.md)**

---

## 全部 45 个技能

### 组件技能 (30)

| 技能 | 用途 |
|------|------|
| **[acceptance-criteria](skills/acceptance-criteria/SKILL.md)** | 使用 Given/When/Then、检查清单或基于规则的格式编写可测试的验收标准 |
| **[business-rule](skills/business-rule/SKILL.md)** | 将业务规则记录为结构化、可追踪的规约 |
| **[change-impact-analysis](skills/change-impact-analysis/SKILL.md)** | 评估需求变更的影响范围、受影响工作产品和工作量 |
| **[context-diagram](skills/context-diagram/SKILL.md)** | 用外部实体和数据流定义系统边界 |
| **[data-dictionary](skills/data-dictionary/SKILL.md)** | 使用形式化表示法和 CRUD 分析定义数据元素、结构和组成 |
| **[data-flow-diagram](skills/data-flow-diagram/SKILL.md)** | 创建分层数据流图（DFD），将系统分解为过程、数据存储和数据流 |
| **[data-modeling](skills/data-modeling/SKILL.md)** | 创建实体关系图（ER 图），建模数据实体、属性和关系 |
| **[decision-table](skills/decision-table/SKILL.md)** | 用决策表和决策树描述复杂的组合业务逻辑 |
| **[dialog-map](skills/dialog-map/SKILL.md)** | 建模用户-系统导航流、屏幕清单和转换规则 |
| **[elicitation-interview](skills/elicitation-interview/SKILL.md)** | 使用结构化问题序列规划和执行干系人访谈 |
| **[moscow-prioritization](skills/moscow-prioritization/SKILL.md)** | 将需求分为 Must/Should/Could/Won't 并附带分配指南 |
| **[observation-analysis](skills/observation-analysis/SKILL.md)** | 通过观察用户工作环境发现未明确表述的需求 |
| **[process-modeling](skills/process-modeling/SKILL.md)** | 为跨职能流程创建活动图和泳道图 |
| **[quality-attribute](skills/quality-attribute/SKILL.md)** | 使用 Planguage 表示法描述非功能需求——可度量的尺度、目标和权衡分析 |
| **[questionnaire-design](skills/questionnaire-design/SKILL.md)** | 设计需求问卷，包含有效的题型和抗偏差的题目排列 |
| **[requirements-baselining](skills/requirements-baselining/SKILL.md)** | 建立需求基线，包含版本控制和审批流程 |
| **[requirements-reuse](skills/requirements-reuse/SKILL.md)** | 使用模式、目录和产品线策略跨项目复用需求 |
| **[requirements-risk-assessment](skills/requirements-risk-assessment/SKILL.md)** | 识别和缓解需求工程特有的风险 |
| **[requirements-status-tracking](skills/requirements-status-tracking/SKILL.md)** | 跟踪需求从"已提议"到"已验证"的生命周期状态 |
| **[requirements-testing](skills/requirements-testing/SKILL.md)** | 从需求导出测试用例以验证可测试性，并规划验收测试 |
| **[requirements-traceability](skills/requirements-traceability/SKILL.md)** | 构建追踪矩阵，链接目标、需求、设计和测试 |
| **[specification-review-checklist](skills/specification-review-checklist/SKILL.md)** | 使用结构化质量检查清单评审需求和 SRS 文档 |
| **[srs-document](skills/srs-document/SKILL.md)** | 使用 EARS 模板和标签约定构建软件需求规格说明书 |
| **[stakeholder-analysis](skills/stakeholder-analysis/SKILL.md)** | 识别和分类干系人、用户类别及其对需求的影响 |
| **[state-modeling](skills/state-modeling/SKILL.md)** | 创建状态转换图和状态表，建模对象生命周期行为 |
| **[use-case](skills/use-case/SKILL.md)** | 编写包含触发器、事件流和异常处理的结构化用例规约 |
| **[user-story-re](skills/user-story-re/SKILL.md)** | 使用 INVEST 准则和结构化验收标准编写需求导向的用户故事 |
| **[value-cost-risk-analysis](skills/value-cost-risk-analysis/SKILL.md)** | 使用多因素价值/成本/风险评分模型进行需求优先级排序 |
| **[vision-and-scope](skills/vision-and-scope/SKILL.md)** | 创建包含业务目标、范围边界和干系人上下文的愿景与范围文档 |
| **[writing-requirements](skills/writing-requirements/SKILL.md)** | 使用 EARS 模板和质量检查清单编写清晰、可测试、无歧义的需求 |

### 交互式技能 (7)

| 技能 | 功能 |
|------|------|
| **[analysis-advisor](skills/analysis-advisor/SKILL.md)** | 根据需求类型、系统复杂度和团队经验选择合适的分析/建模技术 |
| **[change-control-advisor](skills/change-control-advisor/SKILL.md)** | 通过影响分析和范围蔓延检测评估变更请求 |
| **[elicitation-technique-selector](skills/elicitation-technique-selector/SKILL.md)** | 根据项目上下文和干系人可及性选择合适的获取技术 |
| **[prioritization-advisor-re](skills/prioritization-advisor-re/SKILL.md)** | 选择优先级排序方法——MoSCoW、价值/成本/风险、成对比较、$100 等 |
| **[prototyping-strategy](skills/prototyping-strategy/SKILL.md)** | 根据风险、不确定性和评估需求选择合适的原型策略 |
| **[re-tool-selection](skills/re-tool-selection/SKILL.md)** | 根据项目上下文和集成需求选择和评估需求工程工具 |
| **[requirements-review-advisor](skills/requirements-review-advisor/SKILL.md)** | 选择和规划评审方法，从非正式走查到正式 Fagan 审查 |

### 工作流技能 (8)

| 技能 | 功能 |
|------|------|
| **[agile-requirements-process](skills/agile-requirements-process/SKILL.md)** | 为敏捷项目编排需求工程，采用即时细化策略 |
| **[change-control-process](skills/change-control-process/SKILL.md)** | 建立和运行包含 CCB 治理的变更控制流程 |
| **[re-process-improvement](skills/re-process-improvement/SKILL.md)** | 评估、规划、试点和度量 RE 流程改进 |
| **[requirements-analysis-process](skills/requirements-analysis-process/SKILL.md)** | 将原始获取输出转化为经过分析、建模和结构化的需求 |
| **[requirements-development-process](skills/requirements-development-process/SKILL.md)** | 编排从愿景到验证的完整需求开发生命周期 |
| **[requirements-elicitation-workshop](skills/requirements-elicitation-workshop/SKILL.md)** | 规划和执行使用多种技术的结构化获取会议 |
| **[requirements-management-process](skills/requirements-management-process/SKILL.md)** | 建立基线、版本控制、属性跟踪和状态监控 |
| **[requirements-validation-process](skills/requirements-validation-process/SKILL.md)** | 通过评审、审查、原型和概念测试验证需求 |

---

## 按阶段分类

45 个技能对应需求工程生命周期的 8 个阶段：

```text
阶段 1: 基础                 阶段 2: 需求获取              阶段 3: 分析与建模
├─ vision-and-scope          ├─ elicitation-technique-     ├─ use-case
├─ stakeholder-analysis      │  selector                   ├─ user-story-re
├─ context-diagram           ├─ elicitation-interview      ├─ process-modeling
└─ business-rule             ├─ observation-analysis       ├─ data-flow-diagram
                             ├─ questionnaire-design       ├─ data-modeling
                             ├─ questionnaire-design       ├─ state-modeling
                             └─ requirements-              ├─ decision-table
                                elicitation-workshop       ├─ dialog-map
                                                           ├─ analysis-advisor
                                                           └─ requirements-
                                                              analysis-process
阶段 4: 需求规约             阶段 5: 需求验证              阶段 6: 优先级排序
├─ srs-document              ├─ requirements-review-       ├─ prioritization-advisor-re
├─ writing-requirements      │  advisor                    ├─ value-cost-risk-analysis
├─ quality-attribute         ├─ requirements-testing       └─ moscow-prioritization
├─ data-dictionary           ├─ prototyping-strategy
├─ acceptance-criteria       ├─ specification-review-
└─ specification-review-     │  checklist
   checklist                 └─ requirements-
                                validation-process

阶段 7: 需求管理             阶段 8: 跨领域
├─ change-control-advisor    ├─ requirements-risk-
├─ change-control-process    │  assessment
├─ change-impact-analysis    ├─ requirements-reuse
├─ traceability             ├─ re-process-improvement
│  (requirements-            ├─ re-tool-selection
│   traceability)            ├─ requirements-development-
├─ requirements-baselining   │  process
├─ requirements-status-      └─ agile-requirements-
│  tracking                     process
└─ requirements-
   management-process
```

---

## 技能如何关联

```text
                    ┌──────────────────┐
                    │  愿景与范围       │
                    │  干系人分析       │
                    │  上下文图         │
                    └────────┬─────────┘
                             │
                    ┌────────▼─────────┐
                    │    需求获取       │
                    │  访谈             │
                    │  工作坊           │
                    │  观察             │
                    └────────┬─────────┘
                             │
                    ┌────────▼─────────┐
                    │    分析与建模     │
                    │  用例             │
                    │  数据模型         │
                    │  状态模型         │
                    │  流程模型         │
                    └────────┬─────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
     ┌────────▼───────┐ ┌───▼───────┐ ┌───▼────────────┐
     │   需求规约      │ │ 需求验证  │ │ 优先级排序     │
     │ SRS 文档        │ │ 评审      │ │ MoSCoW         │
     │ 需求编写        │ │ 测试      │ │ 价值/成本/风险 │
     │ 质量属性        │ │ 原型      │ │                │
     └────────┬───────┘ └───┬───────┘ └───┬────────────┘
              │              │              │
              └──────────────┼──────────────┘
                             │
                    ┌────────▼─────────┐
                    │    需求管理       │
                    │  基线化           │
                    │  变更控制         │
                    │  追踪             │
                    │  状态跟踪         │
                    └──────────────────┘
```

---

## 技能结构

每个技能遵循以下结构：

```
skills/
  skill-name/
    SKILL.md            # 主文件（目的、关键概念、应用步骤、
                        #   示例、常见陷阱、参考资料）
    template.md         # 填空模板（仅组件技能）
    examples/
      sample.md         # 完整范例（好的、差的、边界情况）
```

每个 `SKILL.md` 包含 YAML frontmatter：

```yaml
---
name: skill-name                    # kebab-case 标识符
description: 触发导向的描述...       # ≤200 字符，回答"何时使用..."
intent: >-                          # 更详细的目的说明
  多行描述...
type: component|interactive|workflow
best_for:                           # 2-3 个主要使用场景
  - "使用场景 1"
  - "使用场景 2"
scenarios:                          # 真实触发示例
  - "我需要..."
estimated_time: "30-60 min"
---
```

**标准章节：**
1. **目的** — 做什么、何时使用
2. **关键概念** — 框架、定义、"为什么有效"、反模式
3. **应用** — 分步指导（组件用模板、交互用问题、工作流用阶段）
4. **示例** — 使用 ChemTrack 统一场景的完整范例
5. **常见陷阱** — 命名的失败模式，附后果和修复方法
6. **参考资料** — 相关技能、外部框架、书籍引用

---

## 仓库结构

```
RE-Skills-zh/
├── README.md                 # 本文件
├── START_HERE.md             # 新用户入门指南
├── LIST.md                   # 完整技能目录
├── CLAUDE.md                 # Claude Code 的 agent 指令
├── CODEX.md                  # OpenAI Codex 的 agent 指令
├── AGENTS.md                 # 通用 agent 操作规范
├── CONTRIBUTING.md           # 贡献者指南
├── skills/                   # 全部 45 个技能目录
│   ├── skill-name/
│   │   ├── SKILL.md          # 技能主体内容
│   │   ├── template.md       # 填空模板（29 个组件技能）
│   │   └── examples/
│   │       └── sample.md     # 完整范例
│   └── ...
├── commands/                 # 10 个斜杠命令（多技能工作流）
│   ├── develop-requirements.md
│   ├── model-requirements.md
│   ├── elicit.md
│   ├── analyze.md
│   ├── write-srs.md
│   ├── validate.md
│   ├── prioritize.md
│   ├── manage-requirements.md
│   ├── agile-re.md
│   └── analyze-change.md
├── catalog/                  # 机器可读索引
│   ├── skills-index.yaml
│   ├── skills-by-type.md
│   ├── commands-index.yaml
│   └── commands.md
└── docs/                     # 使用指南
    ├── 学生使用指南.md
    ├── Using RE Skills with Claude Code.md
    ├── Using RE Skills with Codex.md
    └── Using RE Skills with Chat.md
```

**文件统计：**
- 45 个 SKILL.md 文件（30 组件 + 7 交互 + 8 工作流）
- 30 个 template.md 文件（每个组件技能一个）
- 45 个 examples/sample.md 文件（每个技能一个）
- 10 个命令工作流文件
- **127+ 个 Markdown 文件**

---

## 参考资料

全部技能基于以下文献：

- **Karl Wiegers & Joy Beatty**,《软件需求》第三版 (*Software Requirements, Third Edition*, 2013, Microsoft Press) — 所有技术、框架和流程的主要来源
- **Alistair Cockburn**, *Writing Effective Use Cases* (2001) — 用例层级和结构
- **Tom Gilb**, *Competitive Engineering* (2005) — Planguage 非功能需求表示法
- **Tom DeMarco**, *Structured Analysis and System Specification* (1979) — 数据流图
- **Michael Fagan**, *Software Inspection* — 正式审查流程
- **IEEE 29148:2018** — 系统与软件工程需求过程
- **ISO/IEC 25010:2011** — 系统与软件质量模型
- **Mike Cohn**, *User Stories Applied* (2004) — 用户故事格式
- **Stephen Withall**, *Software Requirement Patterns* (2007) — 需求复用

---

## 兼容平台

这些技能是纯 Markdown 文件（含 YAML frontmatter），适用于任何能读取结构化文本的 AI 智能体或工具：

| 平台 | 使用方式 |
|------|---------|
| **Claude Code** | 将 `skills/` 目录复制到 `~/.claude/skills/`，全局可用 |
| **OpenAI Codex** | 将技能文件纳入仓库上下文 |
| **Cursor / Windsurf** | 添加到项目规则或上下文中 |
| **自定义 agent** | 读取 SKILL.md 文件并遵循"应用"部分的步骤 |

---

## 致谢

本项目的工程架构——技能类型、YAML frontmatter 模式、命令工作流、目录索引和 agent 集成模式——直接受到 **[Product-Manager-Skills](https://github.com/deanpeters/Product-Manager-Skills)** by [Dean Peters](https://github.com/deanpeters) 的启发。

Product-Manager-Skills 是一个开创性的开源产品管理技能库（47 个技能），专为 AI 智能体设计。它建立了三层技能模型（组件 / 交互 / 工作流）、用于多技能编排的 `commands/` 斜杠命令抽象层、机器可读的 `catalog/` 索引，以及多平台 agent 兼容方案。其"ABC — Always Be Coaching"理念——技能应在赋能 agent 的同时教育人类——直接影响了 RE-Skills 在教学意图和 agent 可执行性之间的平衡。

我们从 Product-Manager-Skills 采纳了以下模式：

| 模式 | 借鉴内容 |
|------|---------|
| YAML frontmatter 模式 (`name`, `description`, `intent`, `type`, `best_for`, `scenarios`) | 标准化元数据，用于技能发现和 agent 路由 |
| 三层类型系统（组件 / 交互 / 工作流） | 制品、引导流和编排的清晰分离 |
| `commands/` 目录（含 YAML frontmatter） | 将多技能串联为单次调用的斜杠命令 |
| `catalog/`（YAML + Markdown 索引） | 机器可读和人类可读的技能发现 |
| `CLAUDE.md` + `CODEX.md` + `AGENTS.md` | 按平台定制的 agent 指令 |
| `START_HERE.md`（分级入门） | 根据用户水平提供不同的入门路径 |
| `CONTRIBUTING.md`（质量检查清单） | 统一贡献者体验和技能质量 |
| 交互式技能协议（3-5 个问题、编号选项、多选） | agent 可可靠执行的结构化对话 UX |
| 每个技能的 `examples/sample.md` | agent 在产出前参考的质量基准 |

如果你正在为其他专业领域构建技能库，Product-Manager-Skills 是值得参考的架构起点。

---

## 许可证

本仓库供教育和专业用途使用。
