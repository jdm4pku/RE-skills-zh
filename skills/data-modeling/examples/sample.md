# 数据建模（ERD）示例

## 示例：ChemTrack 实体-关系图

```markdown
# 实体-关系图：ChemTrack

**版本：** 1.0
**日期：** 2025-04-01
**表示法：** 鸦爪（Crow's Foot）

---

## 实体

### Chemical（化学品）
- **主键：** chemical_id
- **属性：** chemical_name、CAS_number、quantity、quantity_unit、expiration_date、date_added、SDS_link（可选）

### StorageLocation（存储位置）
- **主键：** location_id（格式：Building.Room.Cabinet）
- **属性：** building、room、cabinet、storage_type（Ambient/Refrigerated/Freezer/Ventilated）、capacity

### Lab（实验室）
- **主键：** lab_id
- **属性：** lab_name、department

### User（用户）
- **主键：** user_id
- **属性：** name、email、role（Technician/EHS_Officer/Lab_Director/Admin）

### Experiment（实验）
- **主键：** experiment_id
- **属性：** title、start_date、end_date（可选）、status（Planned/Active/Completed/Cancelled）

### ExpirationAlert（过期警报，弱实体 -- 依赖于 Chemical）
- **主键：** alert_id
- **属性：** alert_type（30-Day/7-Day/Expired）、scheduled_date、sent_date、alert_status

---

## 关系

### Lab -- Chemical
- **动词短语：** Lab 存储 Chemical
- **基数：** 1:N
- **参与性：** Lab 可选（0..N）；Chemical 强制（恰好 1）

### Chemical -- StorageLocation
- **动词短语：** Chemical 存储于 StorageLocation
- **基数：** N:1
- **参与性：** Chemical 强制（恰好 1）；StorageLocation 可选（0..N）

### User -- Chemical
- **动词短语：** User 管理 Chemical
- **基数：** 1:N
- **参与性：** User 可选（0..N）；Chemical 强制（恰好 1）
- **业务规则：** 只有具有 Technician 角色的用户才能管理化学品

### Chemical -- Experiment（M:N 已解析）
- **动词短语：** Chemical 使用于 Experiment
- **通过以下关联实体解析：** ExperimentChemical
- **ExperimentChemical 属性：** quantity_used、quantity_unit、date_assigned、assigned_by

### Chemical -- ExpirationAlert
- **动词短语：** Chemical 触发 ExpirationAlert
- **基数：** 1:N
- **参与性：** Chemical 可选（0..N）；Alert 强制（恰好 1）
- **删除规则：** 删除化学品时删除其警报

---

## ERD 图（鸦爪表示法文本形式）

```
Lab ||--o{ Chemical : "存储"
Chemical }|--|| StorageLocation : "存储于"
User ||--o{ Chemical : "管理"
Chemical ||--o{ ExperimentChemical : "属于"
Experiment ||--o{ ExperimentChemical : "包含"
Chemical ||--o{ ExpirationAlert : "触发"
```

解读：一个 Lab 存储零个或多个 Chemical；每个 Chemical 属于恰好一个 Lab。
一个 Chemical 存储在恰好一个 StorageLocation 中。Chemical 和 Experiment
通过 ExperimentChemical 关联（M:N 已解析）。一个 Chemical 触发零个或
多个 ExpirationAlert；每个 Alert 属于一个 Chemical。
```

**为什么有效：**
- 每个实体都有清晰的主键和明确定义的属性
- 所有关系都明确标注了基数和参与性
- M:N 关系（Chemical-Experiment）通过具有自身属性的关联实体解析
- 弱实体（ExpirationAlert）记录了其删除依赖关系
- ERD 可与数据字典交叉参考以获取详细的属性格式
