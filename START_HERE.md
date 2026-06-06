# Start Here

If you are new to this repo, you are in the right place.

You do **not** need to be a programmer to use RE Skills well.

## 0) Read This First (2 Minutes)

This repository contains **44 requirements engineering skills** and **9 slash commands** that work with AI agents like Claude Code, Codex, Cowork, Cursor, and others.

If you only remember one thing:
- Pick **one skill** (or one `/command`)
- Give a **real project context** (product name, stakeholders, constraints)
- Ask for **clarifying questions first**

## 1) Choose Your Comfort Level

### A) "I just want results in chat" (non-technical)

Upload the skill file to Claude Desktop, ChatGPT, or any chat-based AI:

```text
Use the uploaded RE skill as my framework.
Ask up to 3 clarifying questions first.
Then produce the output in markdown.
End with assumptions, gaps, and next steps.
```

See `docs/Using RE Skills with Chat.md`

### B) "I can use a terminal" (higher control)

Use Claude Code, Codex, or Cursor with this repo cloned:

```text
Using skills/vision-and-scope/SKILL.md, create a vision and scope document for a patient scheduling system. Ask questions one at a time, then produce the document.
```

Or use slash commands for multi-skill workflows:

```text
/develop-requirements Patient scheduling system for a multi-site hospital network
```

See `docs/Using RE Skills with Claude Code.md`

### C) "I need repeatable workflows" (automation)

Use the `commands/` directory with agent orchestration platforms:
- n8n, LangFlow, CrewAI, or Python agents
- Each command defines `uses` (skill chain) and `outputs`

## 2) Pick Your First Outcome

### I need an RE artifact

```text
Read skills/use-case/SKILL.md and write a use case specification for user login with SSO.
```

### I need help deciding

```text
Read skills/elicitation-technique-selector/SKILL.md — I have 3 stakeholder groups, 2 weeks, and a mix of domain experts and end users. Which elicitation techniques should I use?
```

### I need end-to-end guidance

```text
/develop-requirements ChemTrack chemical inventory system for university labs
```

## 3) Find the Right Skill Fast

**By phase:**

| I'm working on... | Start with... |
|-------------------|---------------|
| Project kickoff | `vision-and-scope` + `stakeholder-analysis` |
| Gathering requirements | `/elicit` command |
| Modeling & analysis | `/analyze` command |
| Writing the SRS | `/write-srs` command |
| Reviewing requirements | `/validate` command |
| Prioritizing features | `/prioritize` command |
| Managing changes | `/analyze-change` command |
| Agile/Scrum RE | `/agile-re` command |

**By skill type:**
- **Component skills (29):** Templates and artifacts — fill in the template, get a deliverable
- **Interactive skills (8):** Ask questions, get tailored recommendations
- **Workflow skills (7):** Multi-phase processes that chain skills together

Full catalog: `LIST.md` or `catalog/skills-index.yaml`

## 4) If You Feel Stuck

- Start with one simple request and one skill file
- Use real context (project name, stakeholders, constraints, deadlines)
- Ask the agent to explain its reasoning, not just produce output
- Check `examples/sample.md` in any skill directory for quality benchmarks

## 5) Platform Guides

- Claude Code: `docs/Using RE Skills with Claude Code.md`
- Codex (OpenAI): `docs/Using RE Skills with Codex.md`
- Chat-based (Claude Desktop, ChatGPT): `docs/Using RE Skills with Chat.md`
- Full skill catalog: `LIST.md`
- Agent instructions: `CLAUDE.md` (Claude), `CODEX.md` (Codex), `AGENTS.md` (all agents)
