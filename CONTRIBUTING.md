# Contributing to RE-Skills

Thanks for your interest in contributing! This repository helps requirements engineers work better with AI by providing structured RE frameworks in an agent-ready format.

---

## Design Philosophy

Skills in this repository serve two audiences simultaneously:
1. **AI agents** executing RE work at a professional level
2. **Human practitioners** learning the *why* behind each technique

Every skill should teach, not just produce. Explanation is load-bearing, not decorative. Anti-patterns are as important as correct patterns. Stripping learning scaffolding to tighten copy is a defect.

**Protected sections** (do not remove or shorten):
- "Why This Works" explanations
- Anti-Patterns with consequences
- Common Pitfalls with named failure modes
- Educational preambles explaining framework origins

---

## What to Contribute

### New Skills
- RE techniques not yet covered (check `LIST.md` first)
- Must be grounded in *Software Requirements, Third Edition* or equivalent authority
- Use ChemTrack as the running example for consistency

### Improvements
- Better examples (especially "bad" examples showing common mistakes)
- Clearer instructions where existing skills are ambiguous
- Cross-references between related skills
- Additional Common Pitfalls from real-world experience

### Not a Good Fit
- Company-specific processes (skills should be universally applicable)
- Generic advice without a specific technique or framework
- Duplicate content (check existing skills first)

---

## Skill Format

Every skill must follow the standard anatomy:

```
skills/skill-name/
  SKILL.md            # Main skill (required)
  template.md         # Fill-in template (component skills only)
  examples/
    sample.md         # Worked examples (required)
```

### YAML Frontmatter (Required)

```yaml
---
name: skill-name-kebab-case
description: Trigger-oriented, ≤200 chars — "Write X when Y" or "Use when Z"
intent: >-
  Richer multi-line description of what the skill does and when to use it.
type: component|interactive|workflow
best_for:
  - "Use case 1"
  - "Use case 2"
scenarios:
  - "I need to..."
estimated_time: "15-30 min"
---
```

### Required Sections

1. **Purpose** -- What it does and when to use it
2. **Key Concepts** -- Frameworks, "Why This Works," anti-patterns
3. **Application** -- Step-by-step instructions
4. **Examples** -- Worked examples (reference `examples/sample.md`)
5. **Common Pitfalls** -- Named failure modes with consequences and fixes (minimum 3)
6. **References** -- Related skills, external frameworks, book citations

---

## Quality Checklist

- [ ] YAML frontmatter complete (name, description, intent, type, best_for, scenarios, estimated_time)
- [ ] All 6 standard sections present
- [ ] Agent-ready: an AI can follow the Application section without ambiguity
- [ ] At least 3 Common Pitfalls with named failure modes
- [ ] Cross-references use `skills/skill-name/SKILL.md` format
- [ ] Examples use ChemTrack scenario
- [ ] Component skills have `template.md` and `examples/sample.md`
- [ ] Book chapter citation in References
- [ ] Pedagogic content preserved (Why This Works, Anti-Patterns, educational preambles)

---

## How to Submit

1. Fork this repository
2. Create a branch: `git checkout -b add-skill-name`
3. Add your skill following the format above
4. Update `LIST.md` with the new skill
5. Submit a pull request with a clear description of what the skill covers

---

## Skill Types

| Type | When to Use | Structure |
|------|------------|-----------|
| **Component** | Reusable template for a specific RE artifact | SKILL.md + template.md + examples/sample.md |
| **Interactive** | Adaptive Q&A that gathers context and recommends | SKILL.md + examples/sample.md (3-5 questions, numbered options) |
| **Workflow** | Multi-phase process orchestrating other skills | SKILL.md + examples/sample.md (phases, decision points, skill references) |
