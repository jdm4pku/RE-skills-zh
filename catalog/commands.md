# Commands

Generated from `commands/*.md`. Do not edit manually.

## Available Commands (10)

### /develop-requirements
Run the complete requirements development lifecycle from vision through validated, baselined requirements.
- **Uses:** requirements-development-process, vision-and-scope, stakeholder-analysis, context-diagram, elicitation-technique-selector, srs-document, requirements-validation-process
- **Outputs:** Vision and scope document, Stakeholder register, Baselined SRS with validated requirements
- Path: `commands/develop-requirements.md`

### /manage-requirements
Set up and run requirements management for baselined requirements.
- **Uses:** requirements-management-process, requirements-baselining, change-control-process, change-impact-analysis, requirements-traceability, requirements-status-tracking
- **Outputs:** Baselined requirements with version control, Change control board charter, Traceability matrix, Status tracking dashboard
- Path: `commands/manage-requirements.md`

### /elicit
Plan and execute requirements elicitation with technique selection.
- **Uses:** elicitation-technique-selector, elicitation-interview, observation-analysis, questionnaire-design, requirements-elicitation-workshop
- **Outputs:** Elicitation strategy, Prepared session guides, Captured requirements
- Path: `commands/elicit.md`

### /write-srs
Create a structured SRS document with data dictionary and acceptance criteria.
- **Uses:** srs-document, writing-requirements, data-dictionary, acceptance-criteria, specification-review-checklist
- **Outputs:** Structured SRS document, Data dictionary, Acceptance criteria, Self-review results
- Path: `commands/write-srs.md`

### /analyze
Model and refine requirements using appropriate analysis techniques.
- **Uses:** analysis-advisor, use-case, user-story-re, process-modeling, data-modeling, state-modeling, decision-table, dialog-map, quality-attribute
- **Outputs:** Selected modeling techniques, Analysis models, Quality attribute specifications
- Path: `commands/analyze.md`

### /validate
Review and validate requirements before baselining.
- **Uses:** requirements-review-advisor, requirements-validation-process, requirements-testing, prototyping-strategy, specification-review-checklist
- **Outputs:** Validation plan, Defect log, Validation report
- Path: `commands/validate.md`

### /prioritize
Select the right prioritization method and rank requirements.
- **Uses:** prioritization-advisor-re, moscow-prioritization, value-cost-risk-analysis, requirements-allocation
- **Outputs:** Prioritization method selection, Ranked requirements, Release allocation plan
- Path: `commands/prioritize.md`

### /agile-re
Run requirements engineering in an agile context.
- **Uses:** agile-requirements-process, vision-and-scope, user-story-re, acceptance-criteria, requirements-validation-process
- **Outputs:** Lightweight vision and scope, Seeded product backlog, Sprint-ready requirements
- Path: `commands/agile-re.md`

### /analyze-change
Process a requirements change request through impact analysis.
- **Uses:** change-control-process, change-impact-analysis, requirements-traceability
- **Outputs:** Classified change request, Impact analysis, CCB decision recommendation
- Path: `commands/analyze-change.md`

### /model-requirements
创建完整的需求建模文档，涵盖功能模型（用例）、行为模型（流程/状态/决策/会话）和数据模型（ER图），生成 PlantUML 图表并渲染为图片，输出 Markdown 文档。
- **Uses:** use-case, process-modeling, state-modeling, decision-table, dialog-map, data-modeling
- **Outputs:** Markdown 建模文档（含内嵌图片）、用例规约+用例图、流程模型、状态模型、决策表、会话图、ER 图、交叉验证报告
- Path: `commands/model-requirements.md`
