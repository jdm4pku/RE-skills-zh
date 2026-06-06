# CODEX.md — OpenAI Codex Instructions

**Purpose:** Instructions for OpenAI Codex agents on how to use the RE-Skills repository.

---

## Repository Overview

This repository contains **44 requirements engineering skills** organized into 3 types:
- **Component Skills (29):** Templates and artifacts. Each has `SKILL.md`, `template.md`, and `examples/sample.md`.
- **Interactive Skills (8):** Multi-turn conversational flows with adaptive questions and numbered recommendations.
- **Workflow Skills (7):** Multi-phase processes that orchestrate component and interactive skills.

Plus **9 slash commands** in `commands/` that chain multiple skills into single-invocation workflows.

---

## How to Use Skills

1. **Read the SKILL.md** file completely before applying it.
2. **Follow the Application section** step by step.
3. **Use template.md** (component skills) to structure the output.
4. **Reference examples/sample.md** for quality benchmarks.
5. **Cross-reference related skills** in the References section.

### Skill Selection

| User wants to... | Use this skill or command |
|-------------------|--------------------------|
| Start a new project | `/develop-requirements` or `vision-and-scope` + `stakeholder-analysis` |
| Gather requirements | `/elicit` or `elicitation-technique-selector` |
| Model requirements | `/analyze` or `analysis-advisor` |
| Write the SRS | `/write-srs` or `srs-document` + `writing-requirements` |
| Review requirements | `/validate` or `requirements-review-advisor` |
| Prioritize requirements | `/prioritize` or `prioritization-advisor-re` |
| Handle change requests | `/analyze-change` or `change-impact-analysis` |
| Do agile RE | `/agile-re` or `agile-requirements-process` |

### Interactive Skill Protocol

- Ask **one question at a time**
- Present **numbered options** (3-5 choices)
- Allow selection by number, combination, or custom input
- Adapt subsequent questions based on previous answers

---

## File Structure

```
skills/
  skill-name/
    SKILL.md            # Main skill content
    template.md         # Fill-in template (component skills only)
    examples/
      sample.md         # Worked examples
commands/
  command-name.md       # Slash command workflow (YAML frontmatter + workflow steps)
catalog/
  skills-index.yaml     # Machine-readable skill index
  commands-index.yaml   # Machine-readable command index
```

---

## Running Example

All skills use **ChemTrack** (a chemical inventory management system for university laboratories) as the running example for consistency.

---

## Quality Standards

- Requirements must be: unambiguous, testable, traceable, consistent, complete
- Missing information is flagged with `[TBD -- needs input from...]`, not silently omitted
- Every requirement traces to a business objective
- EARS templates used for functional requirements (Wiegers & Beatty)
- Planguage notation used for nonfunctional requirements (Gilb)

---

## Source Authority

*Software Requirements, Third Edition* by Karl Wiegers & Joy Beatty (2013, Microsoft Press) is the authoritative source for all techniques in this repository.
