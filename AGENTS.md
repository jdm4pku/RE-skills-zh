# AGENTS.md — Agent Operating Philosophy

**Purpose:** Define how AI agents should approach requirements engineering work using this skill library.

---

## Core Principle: Teach While Doing

Every skill in this repository serves two audiences simultaneously:
1. **The AI agent** executing RE work at a professional level
2. **The human** learning the "why" behind each technique

When using these skills, agents should:
- **Explain reasoning**, not just produce outputs
- **Name the technique** being applied and cite its source
- **Flag trade-offs** and assumptions made during execution
- **Teach through examples** — show the thinking, not just the result

---

## Operating Rules

### 1. Follow the Skill Structure
Each skill has a deliberate structure. Follow it:
- Read the **Purpose** to confirm the skill applies
- Review **Key Concepts** to understand the framework
- Execute the **Application** steps in order
- Validate against **Common Pitfalls** before delivering output
- Reference **Related Skills** when the work naturally flows to the next phase

### 2. Use Templates for Consistency
Component skills include `template.md` files. Use them:
- Fill in every section of the template
- Don't skip sections — empty sections reveal gaps in requirements
- Note where information is missing with explicit "[TBD — needs input from...]"

### 3. Cross-Reference Within the Library
Skills form a network. When working on one skill, reference others:
- A use case specification naturally leads to acceptance criteria
- An SRS document needs a data dictionary and quality attributes
- A vision and scope document feeds stakeholder analysis
- Every requirement should trace to a business objective

### 4. Maintain the Running Example
The ChemTrack chemical inventory system is the consistent example across all skills. When demonstrating techniques or providing examples:
- Use ChemTrack entities (Lab Technician, EHS Officer, chemicals, containers, etc.)
- Maintain consistency with examples from other skills
- If the user's context differs, adapt the technique but keep the teaching example for illustration

### 5. Be Opinionated, Not Neutral
Skills take stances on what works. Follow them:
- Recommend specific techniques for specific contexts
- Name when a technique is wrong for a situation
- Don't list all options equally — rank them by fit
- State assumptions explicitly rather than hedging

---

## Quality Standards for Outputs

When producing RE artifacts (requirements, use cases, SRS sections, etc.):

1. **Traceability** — Every requirement traces back to a business objective or user need
2. **Testability** — Every requirement has verifiable acceptance criteria
3. **Unambiguity** — No requirement uses vague terms (adequate, appropriate, user-friendly, etc.)
4. **Completeness** — Missing information is flagged, not silently omitted
5. **Consistency** — No two requirements contradict each other

### What Good Looks Like
- Requirements follow EARS templates when applicable
- NFRs use Planguage with measurable scales and targets
- Use cases have clear triggers, preconditions, normal flows, and exception handling
- Data dictionaries define every element, not just the obvious ones
- Traceability matrices have no orphan requirements and no orphan tests

### What Bad Looks Like
- "The system shall be user-friendly" (unmeasurable)
- Requirements that describe solutions instead of behaviors
- Use cases with only happy paths (no exceptions or alternatives)
- Data models with undefined relationships or missing cardinality
- Prioritization without stakeholder input

---

## When Skills Conflict

If guidance from two skills seems contradictory:
1. Check which skill is more specific to the context — prefer the specific over the general
2. Check the "When to Use / When NOT to Use" sections — one may not apply
3. Workflow skills take precedence over component skills for process decisions
4. The book (*Software Requirements, Third Edition*) is the final authority

### 6. Use Commands for Multi-Skill Workflows
The `commands/` directory defines slash commands that chain skills:
- Each command has YAML frontmatter (`name`, `uses`, `outputs`) and a documented workflow
- When the user's request maps to a command, follow the command workflow instead of selecting individual skills
- Commands include checkpoints — verify each before proceeding to the next step
- See `catalog/commands-index.yaml` for the machine-readable command index

---

## Adapting for Different Development Approaches

### Traditional/Waterfall
- Follow the `requirements-development-process` workflow end to end
- Produce a complete SRS before development begins
- Use formal Fagan inspections for validation

### Agile/Iterative
- Follow the `agile-requirements-process` workflow
- Use user stories with acceptance criteria instead of full use cases
- Elaborate requirements just-in-time for upcoming iterations
- Keep the vision and scope as the lightweight anchor document

### Hybrid
- Use the vision and scope and stakeholder analysis up front
- Mix use cases (for complex interactions) with user stories (for simpler features)
- Baseline high-level requirements; elaborate iteratively
- Apply change control for baselined requirements; use backlog grooming for everything else
