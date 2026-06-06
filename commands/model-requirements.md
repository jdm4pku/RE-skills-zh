---
name: model-requirements
description: 创建完整的需求建模文档，涵盖功能模型（用例）、行为模型（流程/状态/决策/会话）和数据模型（DFD + ER图），生成 PlantUML 图表并渲染为图片，最终输出 Markdown 文档。
argument-hint: "<项目名称或愿景与范围文档路径>"
uses:
  - use-case
  - process-modeling
  - state-modeling
  - decision-table
  - dialog-map
  - data-flow-diagram
  - data-modeling
outputs:
  - Markdown 需求建模文档（含内嵌图片）
  - 用例规约 + 用例图
  - 每个用例的活动图和序列图
  - 系统状态全局概览图 + 各对象详细状态图
  - 决策表
  - 系统全局导航图 + 各用例详细会话图
  - 数据流图（DFD Level 0 + Level 1）
  - 数据模型（ER 图）
  - 模型交叉验证报告
---

# /model-requirements

从愿景与范围文档出发，一次性产出完整的需求建模 Markdown 文档。覆盖功能、行为、数据三类模型，每个用例配套独立的活动图和序列图，状态模型和会话图均先给出系统全局概览再展开细节，每种图形模型使用 PlantUML 生成图片并嵌入文档。

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
│   ├── activity-UCxx.puml     # 每个用例的活动图源码
│   ├── activity-UCxx.png      # 每个用例的活动图（渲染后）
│   ├── sequence-UCxx.puml     # 每个用例的序列图源码
│   ├── sequence-UCxx.png      # 每个用例的序列图（渲染后）
│   ├── state-overview.puml    # 系统状态全局概览图源码
│   ├── state-overview.png     # 系统状态全局概览图（渲染后）
│   ├── state-XXX.puml         # 每个对象的详细状态图源码
│   ├── state-XXX.png          # 每个对象的详细状态图（渲染后）
│   ├── dialog-overview.puml   # 系统全局导航图源码
│   ├── dialog-overview.png    # 系统全局导航图（渲染后）
│   ├── dialog-XXX.puml        # 每个用例的会话图源码
│   ├── dialog-XXX.png         # 每个用例的会话图（渲染后）
│   ├── dfd-level0.puml        # Level 0 数据流图源码
│   ├── dfd-level0.png         # Level 0 数据流图（渲染后）
│   ├── dfd-level1-XXX.puml    # Level 1 数据流图源码（按过程）
│   ├── dfd-level1-XXX.png     # Level 1 数据流图（渲染后）
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

### 步骤 2：行为模型 — 活动图与序列图（process-modeling）

**为步骤 1 中的每个用例分别创建一张活动图和一张序列图。**

1. 遍历步骤 1 产出的用例列表，为**每个用例**（UC-xx）创建：
   - **一张泳道活动图**（activity-UCxx）：展示该用例的完整事件流（含异常流分支），使用泳道区分参与者和系统。
   - **一张序列图**（sequence-UCxx）：展示该用例中参与者与系统各模块之间的消息交互时序。
2. 使用 `process-modeling` 技能，标注决策点、并行路径和跨职能交接点。
3. 每张图单独一个 `.puml` 文件，文件名包含用例编号。

**活动图示例（每个用例一张）：**

```plantuml
@startuml activity-UC03
title UC-03 发布求助帖 — 活动图
|用户|
start
:选择求助类型;
:填写求助信息;
:提交求助帖;
|系统|
:验证信息完整性;
if (信息完整?) then (是)
    :保存求助帖;
    :LBS匹配附近志愿者;
    if (有可用志愿者?) then (是)
        :推送接单通知;
    else (否)
        :扩大匹配范围;
        :加入等待队列;
    endif
    |用户|
    :收到发布成功通知;
else (否)
    |用户|
    :收到信息不完整提示;
    :补充信息;
endif
stop
@enduml
```

**序列图示例（每个用例一张）：**

```plantuml
@startuml sequence-UC03
title UC-03 发布求助帖 — 序列图
actor 用户
participant "前端界面" as UI
participant "求助服务" as HelpSvc
participant "匹配引擎" as Match
participant "通知服务" as Notify
database "数据库" as DB

用户 -> UI : 填写求助信息并提交
UI -> HelpSvc : 创建求助帖请求
HelpSvc -> DB : 保存求助帖
DB --> HelpSvc : 保存成功
HelpSvc -> Match : 请求匹配志愿者
Match -> DB : 查询附近可用志愿者
DB --> Match : 返回志愿者列表
alt 有可用志愿者
    Match --> HelpSvc : 返回匹配结果
    HelpSvc -> Notify : 推送接单通知
    Notify -> 志愿者 : 发送通知
else 无可用志愿者
    Match --> HelpSvc : 无匹配，加入等待队列
end
HelpSvc --> UI : 发布成功
UI --> 用户 : 显示发布结果
@enduml
```

### 步骤 3：行为模型 — 状态建模（state-modeling）

**先创建系统级全局状态概览图，再为每个关键对象创建详细状态图。**

1. **系统全局状态概览图**：创建一张总览图，展示系统中所有关键领域对象及其主要状态的全貌，帮助读者快速理解系统整体的状态空间。

```plantuml
@startuml state-system-overview
title 系统状态全局概览

state "用户账号" as User {
    [*] --> 未激活
    未激活 --> 已激活
    已激活 --> 已冻结
    已冻结 --> 已激活
}

state "求助帖" as Post {
    [*] --> 待审核
    待审核 --> 已发布
    已发布 --> 已接单
    已接单 --> 已完成
}

state "服务订单" as Order {
    [*] --> 待接单
    待接单 --> 已接单
    已接单 --> 服务中
    服务中 --> 已完成
}
@enduml
```

2. **逐个对象的详细状态图**：识别具有生命周期的关键领域对象（如订单、工单、用户账号、求助帖），使用 `state-modeling` 技能为每个对象创建：
   - 状态列表（初始态、正常态、异常态、终止态）
   - 事件/触发器列表
   - 状态转换表（状态×事件矩阵，审查每个空单元格）
   - 详细状态转换图

```plantuml
@startuml state-service-order
title 服务订单 — 详细状态图
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

**先创建系统级全局导航图，再为每个核心用例创建详细会话图。**

1. **系统全局导航图**：创建一张总览图，展示系统所有主要界面和它们之间的导航关系全貌，帮助读者快速理解系统的整体 UI 结构。

```plantuml
@startuml dialog-system-overview
title 系统全局导航图
skinparam backgroundColor white

state "SCR-01 首页" as S01
state "SCR-02 紧急求助" as S02
state "SCR-03 服务大厅" as S03
state "SCR-04 帖子列表" as S04
state "SCR-05 帖子详情" as S05
state "SCR-06 发布求助帖" as S06
state "SCR-07 志愿者注册" as S07
state "SCR-08 定位监护" as S08
state "SCR-09 消息中心" as S09
state "SCR-10 个人中心" as S10
state "SCR-11 登录/注册" as S11

[*] --> S11
S11 --> S01 : 登录成功

S01 --> S02 : 紧急求助
S01 --> S03 : 服务大厅
S01 --> S04 : 求助帖
S01 --> S09 : 消息
S01 --> S10 : 我的

S03 --> S06 : 发布求助
S03 --> S07 : 志愿者注册

S04 --> S05 : 查看详情
S05 --> S06 : 回复/接单

S10 --> S08 : 定位监护
@enduml
```

2. **屏幕清单与导航路径**：基于用例事件流，使用 `dialog-map` 技能建立：
   - 屏幕/界面清单表（SCR-ID、名称、用途、关联用例、访问角色）
   - 导航路径表（源界面、触发动作、守卫条件、目标界面）
   - 用例步骤 → 屏幕映射表

3. **逐个用例的详细会话图**：为每个核心用例的 UI 流程生成 PlantUML 会话图：

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

### 步骤 6：数据模型 — 数据流图（data-flow-diagram）

1. 从上下文图或用例列表出发，识别系统内部 3-7 个主要过程和数据存储。
2. 使用 `data-flow-diagram` 技能，绘制 Level 0 DFD，展示过程、数据存储和外部实体之间的数据流。
3. 验证平衡性：上下文图（如果有）中的每条外部数据流在 Level 0 中均有对应。
4. 对最复杂的过程进行 Level 1 分解。
5. 生成 PlantUML 图：

```plantuml
@startuml dfd-level0
skinparam backgroundColor white
skinparam componentStyle rectangle

actor "特殊群体用户" as E1
actor "家属" as E2
actor "志愿者" as E3
actor "管理员" as E4

usecase "1.0\n管理求助帖" as P1
usecase "2.0\n匹配与\n派单" as P2
usecase "3.0\n服务执行\n与评价" as P3
usecase "4.0\n用户与\n权限管理" as P4
usecase "5.0\n实时定位\n监护" as P5

database "D1 求助帖库" as D1
database "D2 用户表" as D2
database "D3 服务订单库" as D3

E1 --> P1 : 求助信息
P1 --> D1 : 写入求助帖
D1 --> P2 : 读取待匹配帖
P2 --> E3 : 接单通知
E3 --> P3 : 服务确认
P3 --> D3 : 写入订单记录
P3 --> E1 : 服务完成通知
E1 --> P4 : 注册信息
P4 --> D2 : 写入用户数据
E2 --> P5 : 监护请求
D2 --> P5 : 读取被监护人信息
P5 --> E2 : 位置与状态信息
@enduml
```

### 步骤 7：数据模型 — ER 图（data-modeling）

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

### 步骤 8：渲染图片与组装文档

1. 将所有 `.puml` 文件写入 `requirements-modeling/diagrams/` 目录。
2. 执行批量渲染：
   ```bash
   plantuml -tpng requirements-modeling/diagrams/*.puml
   ```
3. 组装 `requirements-modeling/README.md`，结构如下：
   - `# 需求建模文档：[项目名称]`
   - `## 1. 功能模型` — 用例描述 + `![用例图](diagrams/use-case-diagram.png)`
   - `## 2. 行为模型`
     - `### 2.1 活动图与序列图` — 按用例编号逐个展示：
       - `#### UC-01 xxx` — 用例简述 + `![活动图](diagrams/activity-UC01.png)` + `![序列图](diagrams/sequence-UC01.png)`
       - `#### UC-02 xxx` — 同上
       - ……
     - `### 2.2 状态模型` — 系统全局概览图 + 各对象的详细状态表和状态图：
       - `![系统状态全局概览](diagrams/state-overview.png)`
       - `#### 服务订单状态` — 状态表 + `![状态图](diagrams/state-service-order.png)`
       - ……
     - `### 2.3 决策表` — Markdown 表格
     - `### 2.4 会话图` — 系统全局导航图 + 屏幕清单 + 各用例的详细会话图：
       - `![系统全局导航图](diagrams/dialog-overview.png)`
       - `#### UC-03 xxx 会话图` — `![会话图](diagrams/dialog-UC03.png)`
       - ……
   - `## 3. 数据模型`
     - `### 3.1 数据流图` — Level 0 DFD + 数据流表 + Level 1 分解（如有）：
       - `![Level 0 DFD](diagrams/dfd-level0.png)`
       - `#### Level 1：xxx` — `![Level 1 DFD](diagrams/dfd-level1-xxx.png)`
     - `### 3.2 ER 图` — 实体属性表 + `![ER图](diagrams/erd.png)`
   - `## 4. 模型交叉验证报告`

## 检查点

完成全部步骤后，执行以下交叉验证：

- **特性覆盖**：每个 FE-x 特性至少被一个用例（UC-xx）覆盖
- **屏幕覆盖**：每个用例的每个步骤可映射到会话图中的一个屏幕
- **数据覆盖**：ER 图中的每个实体至少在一个用例中被引用
- **DFD 平衡**：DFD Level 0 中的外部数据流与上下文图（或用例列表）一致；DFD 数据存储与 ER 图实体对应
- **状态追溯**：状态图中的每个状态转换可追溯到用例事件流中的一个动作
- **一致性**：用例中提及的数据在 ER 图中有对应实体，用例中的界面操作在会话图中有对应屏幕
- **图片完整**：所有 `.puml` 文件均已渲染为 `.png`，Markdown 中的图片引用均可正常显示
- 将验证结果输出为模型交叉验证报告

## 后续步骤

- 运行 `/write-srs` 将建模结果转化为正式的软件需求规格说明书。
- 运行 `/validate` 对模型和需求进行评审验证。
- 如果建模过程中发现了需求空白，运行 `/elicit` 补充需求获取。
