---
name: model-requirements
description: 创建完整的需求建模文档，涵盖功能模型（用例）、行为模型（流程/状态/决策/会话）和数据模型（ER图），生成 PlantUML 图表并渲染为图片，最终输出 Markdown 文档。
argument-hint: "<项目名称或愿景与范围文档路径>"
uses:
  - use-case
  - process-modeling
  - state-modeling
  - decision-table
  - dialog-map
  - data-modeling
outputs:
  - Markdown 需求建模文档（含内嵌图片）
  - 用例规约 + 用例图
  - 流程模型（泳道活动图）
  - 状态模型（状态转换图 + 状态表）
  - 决策表
  - 会话图（Dialog Map）
  - 数据模型（ER 图）
  - 模型交叉验证报告
---

# /model-requirements

从愿景与范围文档出发，一次性产出完整的需求建模 Markdown 文档。覆盖功能、行为、数据三类模型，每种图形模型使用 PlantUML 生成图片并嵌入文档。

## 调用方式

```text
/model-requirements ChemTrack 化学试剂库存管理系统
/model-requirements 社区老弱病残孕智慧关爱互助平台
```

如果项目已有愿景与范围文档，可直接指定文件路径：

```text
/model-requirements vision-and-scope.md
```

## 前置条件

需要本地安装 PlantUML（`brew install plantuml`）。命令执行时会自动调用 `plantuml` CLI 将 `.puml` 文件渲染为 PNG 图片。

## 输出结构

命令在项目目录下创建以下文件结构：

```
requirements-modeling/
├── README.md                  # 主文档，引用下方所有图片
├── diagrams/
│   ├── use-case-diagram.puml  # 用例图 PlantUML 源码
│   ├── use-case-diagram.png   # 用例图（渲染后）
│   ├── activity-XXX.puml      # 活动图源码
│   ├── activity-XXX.png       # 活动图（渲染后）
│   ├── state-XXX.puml         # 状态图源码
│   ├── state-XXX.png          # 状态图（渲染后）
│   ├── dialog-XXX.puml        # 会话图源码
│   ├── dialog-XXX.png         # 会话图（渲染后）
│   ├── erd.puml               # ER 图源码
│   └── erd.png                # ER 图（渲染后）
```

主文档 `README.md` 通过 `![图名](diagrams/xxx.png)` 引用图片。

## 工作流

### 步骤 1：功能模型 — 用例建模（use-case）

1. 从愿景与范围文档的特性列表（FE-x）出发，识别所有参与者（Actor）和用例。
2. 使用 `use-case` 技能，为每个用例编写完整的用例描述，包含 7 个要素：
   - 用例名称与编号（UC-xx）
   - 简要描述
   - 前置条件
   - 事件流（基本流 + 异常流，异常流用分支编号如 3a、5b）
   - 后置条件
   - 约束说明（交叉引用 FE-x、BO-x、LI-x 等编号）
3. 生成 PlantUML 用例图并渲染为 PNG：

```plantuml
@startuml use-case-diagram
left to right direction
skinparam actorStyle awesome

actor "特殊群体用户" as User
actor "家属" as Family
actor "志愿者" as Volunteer
actor "管理员" as Admin

rectangle "关爱平台" {
    usecase "登录验证" as UC01
    usecase "紧急求助" as UC02
    usecase "发布求助帖" as UC03
    usecase "实时定位监护" as UC04
    usecase "注册登记" as UC05
    usecase "认领求助帖" as UC06
    usecase "账号管理" as UC07
}

User -- UC01
User -- UC02
User -- UC03
Family -- UC01
Family -- UC03
Family -- UC04
Volunteer -- UC01
Volunteer -- UC05
Volunteer -- UC06
Admin -- UC07
@enduml
```

将 `.puml` 写入 `diagrams/use-case-diagram.puml`，执行 `plantuml diagrams/use-case-diagram.puml` 生成 PNG。在 README.md 中插入：

```markdown
![用例图](diagrams/use-case-diagram.png)
```

### 步骤 2：行为模型 — 流程建模（process-modeling）

1. 识别跨角色的核心业务流程（通常对应高优先级用例或涉及多个参与者的工作流）。
2. 使用 `process-modeling` 技能，为每个核心流程创建泳道活动图。
3. 标注决策点、并行路径和跨职能交接点。
4. 生成 PlantUML 活动图：

```plantuml
@startuml activity-help-request
|用户|
start
:发布求助帖;
|系统|
:LBS匹配志愿者;
if (有可用志愿者?) then (是)
    :推送接单通知;
    |志愿者|
    :查看并接单;
    |系统|
    :更新订单状态;
    :通知用户;
else (否)
    :扩大匹配范围;
endif
|用户|
:收到通知;
stop
@enduml
```

### 步骤 3：行为模型 — 状态建模（state-modeling）

1. 识别具有生命周期的关键领域对象（如订单、工单、用户账号、求助帖）。
2. 使用 `state-modeling` 技能，为每个对象创建：
   - 状态列表（初始态、正常态、异常态、终止态）
   - 事件/触发器列表
   - 状态转换表（状态×事件矩阵，审查每个空单元格）
3. 生成 PlantUML 状态图：

```plantuml
@startuml state-service-order
[*] --> 待接单 : 用户发布求助

待接单 --> 已接单 : 志愿者认领
待接单 --> 已过期 : 超时未接
待接单 --> 已取消 : 用户取消

已接单 --> 服务中 : 志愿者到达
已接单 --> 已取消 : 志愿者取消

服务中 --> 待评价 : 服务完成
待评价 --> 已完成 : 双方评价

已完成 --> [*]
已取消 --> [*]
已过期 --> [*]
@enduml
```

### 步骤 4：行为模型 — 决策表（decision-table）

1. 从用例事件流中识别包含复杂条件逻辑的场景（多条件分支、权限判断、匹配规则等）。
2. 使用 `decision-table` 技能，为每个复杂场景创建决策表。
3. 验证完备性：二值条件应覆盖 2^N 条规则。
4. 决策表以 Markdown 表格形式直接写入文档（无需生成图片）。

### 步骤 5：行为模型 — 会话图（dialog-map）

1. 基于用例事件流，使用 `dialog-map` 技能建立：
   - 屏幕/界面清单表（SCR-ID、名称、用途、关联用例、访问角色）
   - 导航路径表（源界面、触发动作、守卫条件、目标界面）
   - 用例步骤 → 屏幕映射表
2. 为每个核心用例的 UI 流程生成 PlantUML 会话图：

```plantuml
@startuml dialog-claim-post
(*) --> "首页"
"首页" --> "帖子列表" : 认领求助帖
"首页" <-- "帖子列表" : 返回

"帖子列表" --> "帖子详情" : 选择帖子
"帖子详情" --> "申请界面" : 发起申请
"帖子详情" --> "私信页面" : 私信地址
"帖子详情" <-- "私信页面" : 返回

"申请界面" --> "确认页" : 确认信息
"申请界面" --> "帖子详情" : 取消

"确认页" --> "成功提示" : 确认成功
"确认页" --> "申请界面" : 修改意见
"成功提示" --> (*)
@enduml
```

### 步骤 6：数据模型 — ER 图（data-modeling）

1. 从用例描述中提取所有数据实体、属性和关系。
2. 使用 `data-modeling` 技能，为每个实体定义：
   - 实体描述和主键
   - 属性表（属性名、类型、是否必填、描述）
3. 定义实体间关系（动词短语、基数 1:1/1:N/M:N、参与约束）。
4. 生成 PlantUML ER 图：

```plantuml
@startuml erd
entity "用户 (User)" as User {
    * user_id : INT <<PK>>
    --
    * name : VARCHAR
    * phone : VARCHAR
    * role : ENUM
    address : VARCHAR
}

entity "求助帖 (HelpPost)" as HelpPost {
    * post_id : INT <<PK>>
    --
    * user_id : INT <<FK>>
    * type : ENUM
    * description : TEXT
    * status : ENUM
    * created_at : DATETIME
}

entity "志愿者 (Volunteer)" as Volunteer {
    * volunteer_id : INT <<PK>>
    --
    * user_id : INT <<FK>>
    * skills : JSON
    * available_time : VARCHAR
    * rating : DECIMAL
}

entity "服务订单 (ServiceOrder)" as Order {
    * order_id : INT <<PK>>
    --
    * post_id : INT <<FK>>
    * volunteer_id : INT <<FK>>
    * status : ENUM
    * start_time : DATETIME
    * end_time : DATETIME
}

User ||--o{ HelpPost : "发布"
Volunteer ||--o{ Order : "认领"
HelpPost ||--o| Order : "生成"
User ||--o{ Volunteer : "注册为"
@enduml
```

### 步骤 7：渲染图片与组装文档

1. 将所有 `.puml` 文件写入 `requirements-modeling/diagrams/` 目录。
2. 执行批量渲染：
   ```bash
   plantuml -tpng requirements-modeling/diagrams/*.puml
   ```
3. 组装 `requirements-modeling/README.md`，结构如下：
   - `# 需求建模文档：[项目名称]`
   - `## 1. 功能模型` — 用例描述 + `![用例图](diagrams/use-case-diagram.png)`
   - `## 2. 行为模型`
     - `### 2.1 流程模型` — 流程说明 + `![活动图](diagrams/activity-xxx.png)`
     - `### 2.2 状态模型` — 状态表 + `![状态图](diagrams/state-xxx.png)`
     - `### 2.3 决策表` — Markdown 表格
     - `### 2.4 会话图` — 屏幕清单 + `![会话图](diagrams/dialog-xxx.png)`
   - `## 3. 数据模型` — 实体属性表 + `![ER图](diagrams/erd.png)`
   - `## 4. 模型交叉验证报告`

## 检查点

完成全部步骤后，执行以下交叉验证：

- **特性覆盖**：每个 FE-x 特性至少被一个用例（UC-xx）覆盖
- **屏幕覆盖**：每个用例的每个步骤可映射到会话图中的一个屏幕
- **数据覆盖**：ER 图中的每个实体至少在一个用例中被引用
- **状态追溯**：状态图中的每个状态转换可追溯到用例事件流中的一个动作
- **一致性**：用例中提及的数据在 ER 图中有对应实体，用例中的界面操作在会话图中有对应屏幕
- **图片完整**：所有 `.puml` 文件均已渲染为 `.png`，Markdown 中的图片引用均可正常显示
- 将验证结果输出为模型交叉验证报告

## 后续步骤

- 运行 `/write-srs` 将建模结果转化为正式的软件需求规格说明书。
- 运行 `/validate` 对模型和需求进行评审验证。
- 如果建模过程中发现了需求空白，运行 `/elicit` 补充需求获取。
