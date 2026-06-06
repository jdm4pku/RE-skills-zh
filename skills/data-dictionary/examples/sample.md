# 数据字典示例

## 示例：ChemTrack 数据字典（节选）

```markdown
# 数据字典：ChemTrack

**版本：** 1.0
**日期：** 2025-04-01

---

## 基本数据元素

### chemical_name
- **类型：** 字符串
- **格式：** 1-200 个字符，Unicode
- **有效值：** 必须匹配 PubChem 数据库条目或由 EHS 官员手动验证
- **示例：** "Sodium Hydroxide"
- **备注：** 为便于使用，优先采用通用名称而非 IUPAC 名称

### CAS_number
- **类型：** 字符串
- **格式：** NNN-NN-N，其中 N 为数字（即 3 位数字-短横线-2 位数字-短横线-1 位校验位）
- **有效值：** 必须通过 CAS 校验位算法
- **示例：** "1310-73-2"（Sodium Hydroxide）
- **备注：** 由化学文摘社（Chemical Abstracts Service）分配的全球唯一标识符

### quantity
- **类型：** decimal(10,2)
- **有效值：** >= 0
- **默认值：** 0
- **示例：** 2.50
- **备注：** 始终与 quantity_unit 配对使用

### quantity_unit
- **类型：** 枚举
- **有效值：** ["mL" | "L" | "g" | "kg" | "units"]
- **默认值：** "mL"

### storage_location
- **类型：** 字符串
- **格式：** 楼栋.房间.柜号（例如 "B3.204.C12"）
- **有效值：** 必须引用位置注册表中的现有位置
- **示例：** "B3.204.C12"

### expiration_date
- **类型：** 日期
- **格式：** ISO 8601（YYYY-MM-DD）
- **有效值：** 录入时必须为未来日期（90 天内到期时系统发出警告）
- **示例：** "2026-06-15"

### hazard_class
- **类型：** 枚举
- **有效值：** 参见下方危险类别枚举

---

## 数据结构

### chemical_record
```
chemical_record = chemical_name + CAS_number + quantity + quantity_unit +
                  storage_location + expiration_date + hazard_class +
                  (SDS_link) + date_added + added_by +
                  (date_last_modified) + (modified_by)
```
- **描述：** 库存中的单个化学品容器记录
- **使用场景：** UC-3（添加化学品）、UC-4（搜索目录）、UC-7（生成报告）

### expiration_alert
```
expiration_alert = alert_id + chemical_record + alert_type +
                   scheduled_date + sent_date + recipient_email +
                   alert_status
```
- **描述：** 化学品即将过期的通知记录
- **使用场景：** UC-5（生成过期警报）

### compliance_report
```
compliance_report = report_id + report_type + generated_date +
                    generated_by + reporting_period +
                    1{chemical_record}50000 + regulatory_format
```
- **描述：** 涵盖特定时间段的法规合规报告
- **使用场景：** UC-8（生成合规报告）

---

## 枚举

### hazard_class
| 值 | 显示标签 | 描述 |
|-------|--------------|-------------|
| FLAM | 易燃 | 闪点低于 100F |
| CORR | 腐蚀性 | 导致皮肤组织可见性破坏 |
| TOXI | 有毒 | 摄入、吸入或吸收后有害 |
| OXID | 氧化剂 | 可能引起或加剧火灾 |
| REAC | 反应性 | 不稳定，可能发生剧烈反应 |
| NONE | 无危险 | 无需特殊处理 |

### alert_status
| 值 | 显示标签 | 描述 |
|-------|--------------|-------------|
| PEND | 待发送 | 警报已计划但尚未发送 |
| SENT | 已发送 | 警报邮件已成功投递 |
| FAIL | 失败 | 警报投递失败（已排队重试） |
| ACKD | 已确认 | 接收人已确认收到 |

---

## CRUD 矩阵

|                        | chemical_record | expiration_alert | compliance_report | user_account |
|------------------------|----------------|-----------------|-------------------|-------------|
| Add Chemical (UC-3)    | C              |                 |                   |             |
| Search Catalog (UC-4)  | R              |                 |                   |             |
| Update Chemical (UC-6) | U              |                 |                   |             |
| Dispose Chemical (UC-9)| D              | D               |                   |             |
| Generate Alert (UC-5)  | R              | C               |                   |             |
| Acknowledge Alert      |                | U               |                   |             |
| Generate Report (UC-8) | R              | R               | C                 |             |
| View Report            |                |                 | R                 |             |
| Manage Users           |                |                 |                   | CRUD        |

### CRUD 分析发现
- **compliance_report** 没有更新（Update）或删除（Delete）操作——报告一旦生成即不可修改（法规要求）。这是正确的。
- **expiration_alert** 没有列出显式的只读（Read）功能——警报作为报告生成的一部分被读取。建议考虑添加"警报历史"视图（潜在的遗漏需求）。
```

**为什么这个示例有效：**
- 基本类型具有精确的格式和有效值约束
- 结构使用正式表示法展示组合关系
- 枚举是显式的（没有模糊的"状态"字段）
- CRUD 矩阵揭示了一个潜在的遗漏需求（警报历史视图）
- 注释解释了设计决策（报告不可修改）
