# CLAUDE.md — Requirements Engineering Skills Protocol

**Purpose:** Instructions for AI agents (Claude Code, Codex, etc.) on how to use and extend the RE-Skills repository.

---

## Repository Overview

This repository contains **45 requirements engineering skills** organized into 3 types (component, interactive, workflow) across 8 phases of the RE lifecycle. All skills are derived from *Software Requirements, Third Edition* by Karl Wiegers & Joy Beatty.

### Skill Types

- **Component Skills (30):** Self-contained templates and artifacts. Each has `SKILL.md`, `template.md`, and `examples/sample.md`.
- **Interactive Skills (7):** Multi-turn conversational flows with 3-4 adaptive questions and enumerated recommendations.
- **Workflow Skills (8):** Multi-phase processes that orchestrate component and interactive skills.

### Slash Commands (10)

Commands chain multiple skills into single-invocation workflows. Defined in `commands/` with YAML frontmatter.

| Command | Description |
|---------|-------------|
| `/develop-requirements` | Full requirements development lifecycle |
| `/manage-requirements` | Change control, traceability, status tracking |
| `/elicit` | Plan and run elicitation sessions |
| `/write-srs` | Produce a complete SRS document |
| `/analyze` | Model requirements with appropriate techniques |
| `/validate` | Review and validate before baselining |
| `/prioritize` | Rank requirements for implementation |
| `/agile-re` | Agile requirements engineering workflow |
| `/analyze-change` | Process a change request through impact analysis |
| `/model-requirements` | 创建完整的需求建模文档（用例+流程+状态+决策+会话+ER图） |

### File Structure

```
skills/
  skill-name/
    SKILL.md            # Main skill content
    template.md         # Fill-in template (component skills only)
    examples/
      sample.md         # Worked examples
commands/
  command-name.md       # Slash command (YAML frontmatter + workflow)
catalog/
  skills-index.yaml     # Machine-readable skill index
  commands-index.yaml   # Machine-readable command index
  skills-by-type.md     # Skills grouped by type
  commands.md           # Command descriptions
docs/
  Using RE Skills with Claude Code.md
  Using RE Skills with Codex.md
  Using RE Skills with Chat.md
```

---

## How to Use Skills

### When a User Asks for RE Help

1. **Identify the RE phase** they're working in (Foundation, Elicitation, Analysis, Specification, Validation, Prioritization, Management, or Cross-Cutting)
2. **Find the matching skill** using the name, description, or `best_for` fields in YAML frontmatter
3. **Read the SKILL.md** file completely before applying it
4. **Follow the Application section** step by step
5. **Use the template.md** for component skills to structure the output
6. **Reference examples/sample.md** for quality benchmarks

### Skill and Command Selection Logic

| User wants to... | Command | Individual skills |
|-------------------|---------|-------------------|
| Start a new project | `/develop-requirements` | `vision-and-scope` → `stakeholder-analysis` |
| Gather requirements | `/elicit` | `elicitation-technique-selector` → technique skill |
| Model requirements | `/analyze` | `analysis-advisor` → modeling skills |
| Create full modeling doc | `/model-requirements` | `use-case` + `process-modeling` + `state-modeling` + `dialog-map` + `data-flow-diagram` + `data-modeling` |
| Write the SRS | `/write-srs` | `srs-document` + `writing-requirements` |
| Specify NFRs | — | `quality-attribute` |
| Review requirements | `/validate` | `requirements-review-advisor` → `requirements-validation-process` |
| Prioritize requirements | `/prioritize` | `prioritization-advisor-re` → MoSCoW or value/cost/risk |
| Handle change requests | `/analyze-change` | `change-impact-analysis` |
| Track requirements | `/manage-requirements` | `requirements-status-tracking` + `requirements-traceability` |
| Do agile RE | `/agile-re` | `agile-requirements-process` |
| Run the full lifecycle | `/develop-requirements` | `requirements-development-process` |

When the user provides a project-level request, prefer the **command** (chains skills automatically). When the user asks for a specific artifact, use the **individual skill**.

### Interactive Skill Protocol

When running an interactive skill:
- Ask **one question at a time**
- Present **numbered options** (3-5 choices) at each step
- Allow the user to select by number, combine options, or provide custom input
- Adapt subsequent questions based on previous answers
- Provide final recommendation with rationale tied to their answers

### Running Example

All skills use **ChemTrack** (a chemical inventory management system for university laboratories) as the running example. When creating examples or demonstrating techniques, use this scenario for consistency.

---

## Skill Anatomy (Standard Structure)

Every skill follows this format:

```yaml
---
name: skill-name-kebab-case
description: Trigger-oriented, ≤200 chars
intent: >-
  Richer multi-line description
type: component|interactive|workflow
best_for:
  - "Use case 1"
  - "Use case 2"
scenarios:
  - "I need to..."
estimated_time: "30-60 min"
---
```

**Required sections:**
1. **Purpose** — What it does and when to use it
2. **Key Concepts** — Frameworks, "Why This Works," anti-patterns, when/when-not to use
3. **Application** — Step-by-step instructions
4. **Examples** — Worked examples (reference `examples/sample.md`)
5. **Common Pitfalls** — Named failure modes with consequences and fixes
6. **References** — Related skills, external frameworks, book citations

---

## Creating New Skills

When adding a new skill:

1. Create directory: `skills/skill-name/` with `examples/` subdirectory
2. Write `SKILL.md` following the standard anatomy above
3. For component skills, write `template.md` (fill-in structure)
4. Write `examples/sample.md` with good, bad, and edge-case examples
5. Use ChemTrack as the running example
6. Cross-reference related skills in the References section
7. Update `LIST.md` with the new skill
8. Cite the specific chapter from *Software Requirements, Third Edition*

### Quality Checklist

- [ ] YAML frontmatter complete (name, description, intent, type, best_for, scenarios, estimated_time)
- [ ] All 6 standard sections present
- [ ] Content is agent-ready (an AI can follow the Application section without ambiguity)
- [ ] At least 3 Common Pitfalls with named failure modes
- [ ] Cross-references to related skills use `skills/skill-name/SKILL.md` format
- [ ] Examples are specific (ChemTrack), not generic
- [ ] Component skills have template.md and examples/sample.md
- [ ] Book chapter citation included in References

---

## Important Notes for Agents

- **Read before recommending:** Always read a skill's SKILL.md before suggesting it to the user
- **Follow the Application section:** The steps are designed to be followed sequentially
- **Use templates:** For component skills, the template.md provides the fill-in structure
- **Cross-reference:** Skills reference each other — follow the dependency chain
- **ChemTrack context:** All examples use the chemical inventory system scenario
- **Pedagogic intent:** Skills teach the "why" behind techniques, not just the "how" — preserve this in any output
- **Source authority:** *Software Requirements, Third Edition* is the authoritative source — cite specific chapters when relevant

---

## Source Material

- **Primary:** Karl Wiegers & Joy Beatty, *Software Requirements, Third Edition* (2013, Microsoft Press)
- **Supporting:** Cockburn (use cases), Gilb (Planguage), DeMarco (DFDs), Fagan (inspections), Cohn (user stories), IEEE 29148, ISO 25010
