# 在 Codex 中使用 RE Skills

## 准备工作

在 Codex 工作区中打开本仓库。Codex 会自动读取 `CODEX.md` 中的 agent 指令。

```bash
git clone https://github.com/jdm4pku/RE-skills-zh.git
```

## 使用技能

通过文件路径引用技能：

```text
使用 skills/srs-document/SKILL.md，为大学实验室化学试剂管理系统创建一份 SRS 文档。按照 skills/srs-document/template.md 中的模板结构输出。
```

## 使用命令

命令定义在 `commands/` 目录中，通过 YAML frontmatter 描述多技能工作流：

```text
读取 commands/develop-requirements.md，为化学试剂库存管理系统执行完整的需求开发工作流。
```

每个命令包含：
- `uses`：依次调用的技能链
- `outputs`：产出的交付物
- 工作流步骤和检查点

## 查找技能

可通过以下文件浏览技能目录：
- `catalog/skills-index.yaml` — 44 个技能的机器可读索引
- `catalog/commands-index.yaml` — 10 个命令的机器可读索引
- `LIST.md` — 带描述的人类可读目录

## 使用技巧

- 在生成输出前，先参考 `examples/sample.md` 了解质量标准
- 按照 SKILL.md 中"应用"部分的步骤逐步执行
- 对于组件类技能，使用 `template.md` 作为输出结构
- 注意参考"References"部分列出的相关技能，形成完整的技能链
