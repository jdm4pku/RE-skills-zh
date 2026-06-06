# 上下文图示例

## 示例：ChemTrack 上下文图

```markdown
# 上下文图：ChemTrack

**日期：** 2025-03-20
**作者：** Sarah Chen

---

## 系统
ChemTrack -- 大学实验室化学品库存管理系统

## 外部实体

| 实体 | 类型 | 描述 |
|------|------|------|
| 实验室技术员 | 用户 | 主要用户；管理日常化学品库存 |
| 实验室主任 | 用户 | 审核报告并审批采购 |
| EHS 官员 | 用户 | 生成法规合规报告 |
| PubChem API | 外部系统 | 用于 CAS 编号验证的化学品数据库 |
| 大学 SSO | 外部系统 | Active Directory 身份认证服务 |
| 标签打印机 | 设备 | 为化学品容器打印条形码标签 |
| 邮件服务器 | 外部系统 | 大学 SMTP 服务器，用于警报送达 |
| EPA 报告门户 | 外部系统 | 接收季度合规提交 |

## 数据流

| 来源 | 目标 | 数据流名称 | 描述 |
|------|------|-----------|------|
| 实验室技术员 | ChemTrack | chemical_entry | 新增或更新的化学品记录数据 |
| 实验室技术员 | ChemTrack | search_query | 化学品查询的搜索条件 |
| ChemTrack | 实验室技术员 | search_results | 匹配的化学品记录 |
| ChemTrack | 实验室技术员 | expiration_alert | 过期化学品的电子邮件通知 |
| EHS 官员 | ChemTrack | report_request | 报告生成参数 |
| ChemTrack | EHS 官员 | compliance_report | 格式化的法规报告 |
| 实验室主任 | ChemTrack | approval_decision | 批准或拒绝采购请求 |
| ChemTrack | 实验室主任 | approval_request | 需要授权的化学品采购 |
| ChemTrack | PubChem API | CAS_lookup_request | 待验证的 CAS 编号 |
| PubChem API | ChemTrack | CAS_validation_result | 验证状态和化学品数据 |
| ChemTrack | 大学 SSO | auth_request | 用于身份认证的用户凭证 |
| 大学 SSO | ChemTrack | auth_token | 认证结果和用户档案 |
| ChemTrack | 标签打印机 | label_data | 容器标签的条形码和文本 |
| ChemTrack | 邮件服务器 | alert_email | 格式化的过期警报消息 |
| ChemTrack | EPA 报告门户 | EPA_submission | EPA 格式的季度法规数据 |

## 图示（文本表示）

```
                    [大学 SSO]
                     ^           |
                auth_request  auth_token
                     |           v
[实验室技术员] <--search_results-- (ChemTrack) --compliance_report--> [EHS 官员]
       |                                  ^  |
  chemical_entry                          |  +--label_data--> [标签打印机]
  search_query                            |  |
  expiration_alert(out)                   |  +--alert_email--> [邮件服务器]
                                          |  |
                [PubChem API] <--CAS_lookup_request--+
                     |                       |
              CAS_validation_result          +--EPA_submission--> [EPA 门户]
                     |                       |
                     +-->                    |
                            [实验室主任] --approval_decision-->
                                   <--approval_request--
```

## 导出的需求

| 数据流 | 方向 | 需要定义的需求 |
|--------|------|--------------|
| chemical_entry | 输入 | 必填字段、CAS 格式验证、重复检测 |
| search_query | 输入 | 支持的搜索条件、部分匹配行为 |
| search_results | 输出 | 显示字段、排序方式、最大结果数、响应时间 |
| expiration_alert | 输出 | 触发时间（30/7/1 天）、内容、接收人规则 |
| compliance_report | 输出 | 报告格式、内容、法规标准 |
| CAS_lookup_request | 输出 | API 协议、超时处理、不可用时的回退方案 |
| auth_request | 输出 | SSO 协议（SAML/OAuth）、角色映射 |
| label_data | 输出 | 标签格式、条形码标准、打印机协议 |
| EPA_submission | 输出 | EPA 数据格式、提交计划、确认处理 |
```

**为什么这个示例有效：**
- 单一系统气泡（ChemTrack）
- 利益相关者分析中的所有用户类别都已表示
- 所有外部系统集成都已识别
- 每个数据流都有描述性名称
- 导出的需求表将图表转化为可操作的工作
- 外部实体之间没有数据流
