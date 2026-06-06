# 在 Claude Code 中使用 RE Skills

## 准备工作

将仓库克隆到本地：

```bash
git clone https://github.com/jdm4pku/RE-skills-zh.git
cd RE-skills-zh
```

在项目目录下启动 Claude Code，它会自动读取 `CLAUDE.md` 和 `AGENTS.md` 中的技能指令。

## 使用单个技能

直接引用技能文件路径：

```text
使用 skills/vision-and-scope/SKILL.md，为"社区老弱病残孕智慧关爱互助平台"创建愿景与范围文档。请逐个问我澄清问题，然后生成文档。
```

对于组件类技能，可以要求按模板结构输出：

```text
读取 skills/use-case/template.md，为"用户紧急求助"编写用例规约。
```

## 使用斜杠命令

命令将多个技能串联为端到端的工作流：

```text
/develop-requirements 社区老弱病残孕智慧关爱互助平台
/elicit 了解老年用户的求助需求和使用习惯
/write-srs 求助帖发布与志愿者匹配模块
/model-requirements 社区老弱病残孕智慧关爱互助平台
/validate 社区关爱平台 SRS v1.0 — 38 条需求
/prioritize 38 条需求，第一期发布，3 个月工期
/analyze-change CR-003: 增加语音求助功能
/agile-re Sprint 2 — 志愿者服务管理
```

## 交互式技能

交互式技能会通过自适应问题引导你。让它来主导对话：

```text
读取 skills/elicitation-technique-selector/SKILL.md — 我有 4 个干系人群体，2 周时间，需要同时覆盖功能需求和质量属性。帮我选择合适的获取技术。
```

技能会逐个提出 3-4 个问题，然后给出带编号的推荐方案。

## 使用技巧

- 提供**真实的项目背景**（项目名称、干系人、约束条件、截止日期），效果更好
- 查看任意技能目录中的 `examples/sample.md`，了解输出质量标准
- 使用 `LIST.md` 或 `catalog/skills-index.yaml` 查找合适的技能
- 技能之间有交叉引用——让 Claude 沿着技能链继续读取下一个相关技能
