---
name: data-dictionary
description: 使用正式的数据字典表示法定义数据元素、结构和组合。用于记录数据模型，消除关于每个数据项含义、内容及其与其他数据关系的歧义。
intent: >-
  创建结构化的数据字典（Data Dictionary），正式定义需求中引用的每个数据元素，包括基本类型、复合结构、重复组和有效值。使用数据字典消除"客户信息"或"订单详情"等未定义术语带来的歧义，通过数据流分析发现遗漏的需求，并为开发人员提供精确的数据规格说明。包括 CRUD 矩阵分析以进行完整性检查。
type: component
theme: re-artifacts
best_for:
  - "定义需求中引用的数据元素"
  - "通过数据流分析发现遗漏的需求"
  - "消除关于数据项含义和格式的歧义"
scenarios:
  - "需求中提到了'客户记录'，但没有人定义它包含哪些字段"
  - "我需要验证系统对每个数据实体都具备创建、读取、更新和删除的需求"
estimated_time: "初始字典 30-60 分钟；后续持续维护"
---


## 目的
创建结构化的数据字典（Data Dictionary），正式定义需求中引用的每个数据元素：基本类型、复合结构、重复组和有效值。使用数据字典消除歧义、发现遗漏的需求，并为开发人员提供精确的数据规格说明。

这不是数据库模式（schema）——而是需求层面的数据含义和结构定义，独立于实现技术。

## 关键概念

### 数据字典表示法

| 符号 | 含义 | 示例 |
|--------|---------|---------|
| `=` | 由……组成 | `customer = name + address + phone` |
| `+` | 与（顺序） | `name = first_name + last_name` |
| `[a | b]` | a 或 b（选择） | `payment = [credit_card | bank_transfer | cash]` |
| `{x}` | 零个或多个 x（重复） | `order = header + {line_item}` |
| `N{x}M` | N 到 M 个 x | `phone_list = 1{phone_number}3` |
| `(x)` | 可选 | `name = first_name + (middle_name) + last_name` |
| `"x"` | 字面值 | `country_code = "US"` |
| `*x*` | 注释 | `*ISO 8601 日期格式*` |

### 数据元素类型

**基本类型：** 不可再分解的原子数据元素。
```
CAS_number = *化学文摘社注册号*
             字符串，格式：NNN-NN-N，其中 N 为数字
```

**结构：** 由其他元素按固定顺序组合而成的复合类型。
```
chemical_record = chemical_name + CAS_number + quantity + 
                  storage_location + expiration_date +
                  (SDS_link) + date_added + added_by
```

**重复组：** 零个或多个实例的集合。
```
chemical_inventory = {chemical_record}
experiment_chemicals = 1{chemical_record}50
```

### CRUD 矩阵
CRUD（Create 创建、Read 读取、Update 更新、Delete 删除）矩阵将数据实体与系统功能进行交叉引用，以发现遗漏的需求：

|                     | Chemical | Alert | Report | User |
|---------------------|----------|-------|--------|------|
| Add Chemical        | C        |       |        |      |
| Search Catalog      | R        |       |        |      |
| Update Quantity     | U        |       |        |      |
| Dispose Chemical    | D        | D     |        |      |
| Generate Alert      | R        | C     |        |      |
| Generate Report     | R        | R     | C      |      |
| Manage Users        |          |       |        | CRUD |

**分析规则：**
- 每个实体都应具备全部四种 CRUD 操作（或记录说明为何不需要）
- 一个被创建（Create）但从未被读取（Read）的实体是可疑的（为什么要存储它？）
- 一个被读取（Read）但从未被创建（Create）的实体意味着它来自系统外部
- 空行或空列表示缺少功能或实体

### 反模式
- **未定义的复合类型** -- 需求中引用了"客户信息"，但没有定义它包含哪些字段
- **隐式假设** -- "姓名"——是名字？全名？还是姓在前？
- **未指定有效值** -- "状态"——有哪些可能的值？允许哪些状态转换？

## 应用

使用 `template.md` 作为填写结构。

### 步骤 1：盘点数据引用

扫描你的需求、用例和用户故事。每个代表数据的名词都是数据字典的候选条目：
- 用户提供的输入
- 系统显示的输出
- 系统存储的数据
- 与外部系统交换的数据

### 步骤 2：定义基本类型

对每个原子数据元素：
```markdown
### [元素名称]
- **类型：** [字符串 / 整数 / 小数 / 日期 / 布尔 / 枚举]
- **格式：** [模式、长度、精度]
- **有效值：** [范围、枚举或约束]
- **默认值：** [默认值（如有）]
- **示例：** [代表性的值]
- **备注：** [补充说明]
```

### 步骤 3：定义结构

使用组合表示法从基本类型构建：
```
address = street_line_1 + (street_line_2) + city + state_code + 
          postal_code + country_code
```

### 步骤 4：定义重复组和选择

```
order = order_header + 1{order_line}999
payment_method = [credit_card | debit_card | bank_transfer | purchase_order]
```

### 步骤 5：构建 CRUD 矩阵

1. 列出所有数据实体（行）
2. 列出所有系统功能或用例（列）
3. 对每个单元格，标记适用的 C、R、U、D
4. 分析差距

### 步骤 6：验证

- [ ] 需求中的每个数据元素都有对应的字典条目
- [ ] 每个结构都分解到了基本类型
- [ ] 所有基本类型都指定了有效值和格式
- [ ] CRUD 矩阵没有无法解释的空单元格
- [ ] 字典条目具有一致性（同一元素在各处定义相同）

---

## 示例

完整的数据字典示例见 `examples/sample.md`。

简要示例：

```
chemical_name = 字符串，1-200 个字符，必须匹配 PubChem 数据库中的条目
                或由 EHS 官员手动验证

CAS_number = 字符串，格式：NNN-NN-N，其中 N = 数字
             *化学文摘社注册号，全球唯一*
             示例："7732-18-5"（水）

quantity = decimal(10,2)，>= 0，单位由 quantity_unit 指定
quantity_unit = ["mL" | "L" | "g" | "kg" | "units"]

chemical_record = chemical_name + CAS_number + quantity + quantity_unit +
                  storage_location + expiration_date + hazard_class +
                  (SDS_link) + date_added + added_by
```

## 常见陷阱

### 陷阱 1：跳过数据字典
**症状：** 需求中使用"客户数据"、"订单信息"或"报告字段"等术语但未加定义。

**后果：** 开发人员根据假设定义数据结构。不同的开发人员做出不同的假设。生产环境中出现数据不一致。

**修复：** 需求中的每个复合术语都必须在数据字典中分解为已定义的基本类型。

---

### 陷阱 2：有效值不完整
**症状：** "状态"字段被定义为"字符串"，但没有列举可能的值。

**后果：** 开发人员和测试人员自行编造状态值。数据库中出现"Active"、"active"、"ACTIVE"和"A"等多种写法。

**修复：** 显式定义枚举值：`status = ["Active" | "Inactive" | "Pending" | "Suspended"]`。

---

### 陷阱 3：未构建 CRUD 矩阵
**症状：** 需求看似完整，但某个关键实体缺少创建（Create）操作。

**后果：** 测试期间，有人问"这些数据是怎么进入系统的？"而没人能回答。

**修复：** 尽早构建 CRUD 矩阵。它能在开发开始之前可靠地暴露遗漏的需求。

## 参考资料

### 相关技能
- `skills/srs-document/SKILL.md` -- 数据字典是 SRS 的第 4 节
- `skills/context-diagram/SKILL.md` -- 上下文图中的数据流引用字典条目
- `skills/requirements-analysis-process/SKILL.md` -- 数据分析是分析过程的一部分

### 外部框架
- Tom DeMarco, *Structured Analysis and System Specification* (1979) -- 数据字典表示法
- Karl Wiegers & Joy Beatty, *Software Requirements, Third Edition* (2013) -- 第 13 章：A Picture Is Worth 1024 Words（数据建模）
- Peter Chen, "The Entity-Relationship Model" (1976) -- 实体关系建模

---

**技能类型：** 组件
**依赖：** 无
**被使用于：** `skills/srs-document/SKILL.md`、`skills/requirements-analysis-process/SKILL.md`
