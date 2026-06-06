# RE-Skills — Requirements Engineering Skills for AI Agents

```text
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│   ██████╗ ███████╗    ███████╗██╗  ██╗██╗██╗     ██╗     ███████╗│
│   ██╔══██╗██╔════╝    ██╔════╝██║ ██╔╝██║██║     ██║     ██╔════╝│
│   ██████╔╝█████╗      ███████╗█████╔╝ ██║██║     ██║     ███████╗│
│   ██╔══██╗██╔══╝      ╚════██║██╔═██╗ ██║██║     ██║     ╚════██║│
│   ██║  ██║███████╗    ███████║██║  ██╗██║███████╗███████╗███████║│
│   ╚═╝  ╚═╝╚══════╝    ╚══════╝╚═╝  ╚═╝╚═╝╚══════╝╚══════╝╚══════╝│
│                                                                  │
│   44 requirements engineering skills across 8 phases             │
│   Claude Code · Cowork · Codex · and any agent that reads markdown│
│                                                                  │
│   v1.0 · Apr 2026 · Based on Software Requirements, 3rd Edition │
└──────────────────────────────────────────────────────────────────┘
```

**Teach your AI agents (and yourself) how to do requirements engineering at a professional level.** 

44 battle-tested skills covering the full requirements engineering lifecycle — from business vision through change management. Every skill teaches the *why* behind the technique, provides step-by-step guidance an agent can execute, and includes templates, worked examples, and cross-references.

Based on Karl Wiegers & Joy Beatty's *Software Requirements, Third Edition* — the definitive reference for requirements engineering practice.

**Works with:** Claude Code, Cowork, OpenAI Codex, and any AI agent that can read structured markdown.

---

## What This Is

A complete requirements engineering skill library organized into **8 phases** covering both **Requirements Development** (Elicitation, Analysis, Specification, Validation) and **Requirements Management** (Baselining, Change Control, Traceability, Status Tracking).

Each skill follows a standard anatomy — Purpose, Key Concepts, Application, Examples, Common Pitfalls, References — and includes fill-in templates, worked examples with a consistent running scenario (ChemTrack chemical inventory system), and cross-references to related skills.

---

## Three-Tier Architecture

```text
┌───────────────────────────────────────────────────────────────┐
│  WORKFLOW SKILLS (8)                                          │
│  End-to-end RE processes spanning days to weeks               │
│  Example: "Run a complete requirements development lifecycle" │
└───────────────────────────────────────────────────────────────┘
                         ↓ orchestrates
┌───────────────────────────────────────────────────────────────┐
│  INTERACTIVE SKILLS (7)                                       │
│  Guided discovery with adaptive questions and recommendations │
│  Example: "Which elicitation technique should I use?"         │
└───────────────────────────────────────────────────────────────┘
                         ↓ uses
┌───────────────────────────────────────────────────────────────┐
│  COMPONENT SKILLS (29)                                        │
│  Templates for specific RE deliverables                       │
│  Example: "Write a use case specification"                    │
└───────────────────────────────────────────────────────────────┘
```

---

## Getting Started

| You want to... | Start here |
|----------------|-----------|
| Launch a new project | [`vision-and-scope`](skills/vision-and-scope/SKILL.md) → [`stakeholder-analysis`](skills/stakeholder-analysis/SKILL.md) |
| Plan elicitation | [`elicitation-technique-selector`](skills/elicitation-technique-selector/SKILL.md) → [`requirements-elicitation-workshop`](skills/requirements-elicitation-workshop/SKILL.md) |
| Write requirements | [`srs-document`](skills/srs-document/SKILL.md) + [`writing-requirements`](skills/writing-requirements/SKILL.md) |
| Model requirements | [`analysis-advisor`](skills/analysis-advisor/SKILL.md) → choose from use cases, process models, data models, etc. |
| Review requirements | [`requirements-review-advisor`](skills/requirements-review-advisor/SKILL.md) → [`requirements-validation-process`](skills/requirements-validation-process/SKILL.md) |
| Prioritize requirements | [`prioritization-advisor-re`](skills/prioritization-advisor-re/SKILL.md) → MoSCoW or value/cost/risk |
| Manage changes | [`change-control-advisor`](skills/change-control-advisor/SKILL.md) → [`change-control-process`](skills/change-control-process/SKILL.md) |
| Do agile RE | [`agile-requirements-process`](skills/agile-requirements-process/SKILL.md) |
| Run the full RE lifecycle | [`requirements-development-process`](skills/requirements-development-process/SKILL.md) |

---

## All 44 Skills

### Component Skills (29)

| Skill | Use When You Need To... |
|-------|------------------------|
| **[acceptance-criteria](skills/acceptance-criteria/SKILL.md)** | Write testable acceptance criteria using Given/When/Then, checklist, or rule-based formats |
| **[business-rule](skills/business-rule/SKILL.md)** | Document business rules as structured, traceable specifications separate from functional requirements |
| **[change-impact-analysis](skills/change-impact-analysis/SKILL.md)** | Assess implications, affected work products, and effort for a proposed requirements change |
| **[context-diagram](skills/context-diagram/SKILL.md)** | Define system boundaries with external entities and data flows |
| **[data-dictionary](skills/data-dictionary/SKILL.md)** | Define data elements, structures, and compositions using formal notation and CRUD analysis |
| **[data-modeling](skills/data-modeling/SKILL.md)** | Create entity-relationship diagrams to model data entities, attributes, and relationships |
| **[decision-table](skills/decision-table/SKILL.md)** | Specify complex combinatorial business logic with decision tables and trees |
| **[dialog-map](skills/dialog-map/SKILL.md)** | Model user-system navigation flows, screen inventories, and transition rules |
| **[elicitation-interview](skills/elicitation-interview/SKILL.md)** | Plan and conduct stakeholder interviews using structured question progressions |
| **[moscow-prioritization](skills/moscow-prioritization/SKILL.md)** | Categorize requirements into Must/Should/Could/Won't with allocation guidelines |
| **[observation-analysis](skills/observation-analysis/SKILL.md)** | Discover unstated requirements by watching users work in their environment |
| **[process-modeling](skills/process-modeling/SKILL.md)** | Create activity diagrams and swim-lane diagrams for cross-functional processes |
| **[quality-attribute](skills/quality-attribute/SKILL.md)** | Specify NFRs with Planguage notation — measurable scales, goals, and trade-off analysis |
| **[questionnaire-design](skills/questionnaire-design/SKILL.md)** | Design requirements questionnaires with effective question types and bias-resistant ordering |
| **[requirements-baselining](skills/requirements-baselining/SKILL.md)** | Establish requirements baselines with version control and approval processes |
| **[requirements-reuse](skills/requirements-reuse/SKILL.md)** | Reuse requirements across projects using patterns, catalogs, and product-line strategies |
| **[requirements-risk-assessment](skills/requirements-risk-assessment/SKILL.md)** | Identify and mitigate risks specific to requirements engineering |
| **[requirements-status-tracking](skills/requirements-status-tracking/SKILL.md)** | Track requirements through their lifecycle from Proposed to Verified |
| **[requirements-testing](skills/requirements-testing/SKILL.md)** | Derive test cases from requirements to verify testability and plan acceptance testing |
| **[requirements-traceability](skills/requirements-traceability/SKILL.md)** | Build traceability matrices linking objectives, requirements, design, and tests |
| **[specification-review-checklist](skills/specification-review-checklist/SKILL.md)** | Review requirements and SRS documents using structured quality checklists |
| **[srs-document](skills/srs-document/SKILL.md)** | Build a Software Requirements Specification with EARS templates and labeling conventions |
| **[stakeholder-analysis](skills/stakeholder-analysis/SKILL.md)** | Identify and classify stakeholders, user classes, and their influence on requirements |
| **[state-modeling](skills/state-modeling/SKILL.md)** | Create state-transition diagrams and state tables for object lifecycle behavior |
| **[use-case](skills/use-case/SKILL.md)** | Write structured use case specifications with triggers, flows, and exceptions |
| **[user-story-re](skills/user-story-re/SKILL.md)** | Write requirements-focused user stories with INVEST criteria and structured acceptance criteria |
| **[value-cost-risk-analysis](skills/value-cost-risk-analysis/SKILL.md)** | Prioritize requirements using a multi-factor value/cost/risk scoring model |
| **[vision-and-scope](skills/vision-and-scope/SKILL.md)** | Create a vision and scope document with business objectives, scope boundaries, and stakeholder context |
| **[writing-requirements](skills/writing-requirements/SKILL.md)** | Write clear, testable, unambiguous requirements using EARS templates and quality checklists |

### Interactive Skills (7)

| Skill | What It Does |
|-------|-------------|
| **[analysis-advisor](skills/analysis-advisor/SKILL.md)** | Select the right analysis/modeling techniques based on requirement type, system complexity, and team experience |
| **[change-control-advisor](skills/change-control-advisor/SKILL.md)** | Evaluate change requests with impact analysis and scope creep detection |
| **[elicitation-technique-selector](skills/elicitation-technique-selector/SKILL.md)** | Choose the right elicitation technique based on project context and stakeholder access |
| **[prioritization-advisor-re](skills/prioritization-advisor-re/SKILL.md)** | Select a prioritization method — MoSCoW, value/cost/risk, pairwise, $100, or others |
| **[prototyping-strategy](skills/prototyping-strategy/SKILL.md)** | Select the right prototyping approach based on risks, uncertainty, and evaluation needs |
| **[re-tool-selection](skills/re-tool-selection/SKILL.md)** | Select and evaluate requirements engineering tools based on project context and integration needs |
| **[requirements-review-advisor](skills/requirements-review-advisor/SKILL.md)** | Choose and plan review approaches from informal walkthroughs to formal Fagan inspections |

### Workflow Skills (8)

| Skill | What It Does |
|-------|-------------|
| **[agile-requirements-process](skills/agile-requirements-process/SKILL.md)** | Orchestrate requirements engineering for agile projects with just-in-time elaboration |
| **[change-control-process](skills/change-control-process/SKILL.md)** | Establish and operate a change control process with CCB governance |
| **[re-process-improvement](skills/re-process-improvement/SKILL.md)** | Assess, plan, pilot, and measure improvements to your RE processes |
| **[requirements-analysis-process](skills/requirements-analysis-process/SKILL.md)** | Transform raw elicitation outputs into analyzed, modeled, and structured requirements |
| **[requirements-development-process](skills/requirements-development-process/SKILL.md)** | Orchestrate the complete requirements development lifecycle from vision through validation |
| **[requirements-elicitation-workshop](skills/requirements-elicitation-workshop/SKILL.md)** | Plan and execute structured elicitation sessions using multiple techniques |
| **[requirements-management-process](skills/requirements-management-process/SKILL.md)** | Establish baselines, version control, attribute tracking, and status monitoring |
| **[requirements-validation-process](skills/requirements-validation-process/SKILL.md)** | Validate requirements through reviews, inspections, prototyping, and conceptual testing |

---

## Skills by Phase

The 44 skills map to 8 phases of the requirements engineering lifecycle:

```text
Phase 1: Foundation          Phase 2: Elicitation         Phase 3: Analysis & Modeling
├─ vision-and-scope          ├─ elicitation-technique-     ├─ use-case
├─ stakeholder-analysis      │  selector                   ├─ user-story-re
├─ context-diagram           ├─ elicitation-interview      ├─ process-modeling
└─ business-rule             ├─ observation-analysis       ├─ data-modeling
                             ├─ questionnaire-design       ├─ state-modeling
                             └─ requirements-              ├─ decision-table
                                elicitation-workshop       ├─ dialog-map
                                                           ├─ analysis-advisor
                                                           └─ requirements-
                                                              analysis-process
Phase 4: Specification       Phase 5: Validation           Phase 6: Prioritization
├─ srs-document              ├─ requirements-review-       ├─ prioritization-advisor-re
├─ writing-requirements      │  advisor                    ├─ value-cost-risk-analysis
├─ quality-attribute         ├─ requirements-testing       └─ moscow-prioritization
├─ data-dictionary           ├─ prototyping-strategy
├─ acceptance-criteria       ├─ specification-review-
└─ specification-review-     │  checklist
   checklist                 └─ requirements-
                                validation-process

Phase 7: Management          Phase 8: Cross-Cutting
├─ change-control-advisor    ├─ requirements-risk-
├─ change-control-process    │  assessment
├─ change-impact-analysis    ├─ requirements-reuse
├─ traceability             ├─ re-process-improvement
│  (requirements-            ├─ re-tool-selection
│   traceability)            ├─ requirements-development-
├─ requirements-baselining   │  process
├─ requirements-status-      └─ agile-requirements-
│  tracking                     process
└─ requirements-
   management-process
```

---

## How Skills Connect

```text
                    ┌──────────────────┐
                    │  Vision & Scope  │
                    │  Stakeholders    │
                    │  Context Diagram │
                    └────────┬─────────┘
                             │
                    ┌────────▼─────────┐
                    │   Elicitation    │
                    │  Interviews      │
                    │  Workshops       │
                    │  Observation     │
                    └────────┬─────────┘
                             │
                    ┌────────▼─────────┐
                    │    Analysis      │
                    │  Use Cases       │
                    │  Data Models     │
                    │  State Models    │
                    │  Process Models  │
                    └────────┬─────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
     ┌────────▼───────┐ ┌───▼───────┐ ┌───▼────────────┐
     │ Specification  │ │Validation │ │ Prioritization │
     │ SRS Document   │ │ Reviews   │ │ MoSCoW         │
     │ Writing Reqs   │ │ Testing   │ │ Value/Cost/Risk│
     │ Quality Attrs  │ │ Prototypes│ │                │
     └────────┬───────┘ └───┬───────┘ └───┬────────────┘
              │              │              │
              └──────────────┼──────────────┘
                             │
                    ┌────────▼─────────┐
                    │   Management     │
                    │  Baselining      │
                    │  Change Control  │
                    │  Traceability    │
                    │  Status Tracking │
                    └──────────────────┘
```

---

## Skill Anatomy

Every skill follows this structure:

```
skills/
  skill-name/
    SKILL.md            # Main skill (Purpose, Key Concepts, Application,
                        #   Examples, Common Pitfalls, References)
    template.md         # Fill-in template (component skills only)
    examples/
      sample.md         # Worked examples (good, bad, and edge cases)
```

Each `SKILL.md` includes YAML frontmatter:

```yaml
---
name: skill-name                    # Kebab-case identifier
description: Trigger-oriented...    # ≤200 chars, answers "use when..."
intent: >-                          # Richer explanation of purpose
  Multi-line description...
type: component|interactive|workflow
best_for:                           # 2-3 primary use cases
  - "Use case 1"
  - "Use case 2"
scenarios:                          # Real-world trigger examples
  - "I need to..."
estimated_time: "30-60 min"
---
```

**Standard sections:**
1. **Purpose** — What it does and when to use it
2. **Key Concepts** — Frameworks, definitions, "Why This Works," anti-patterns
3. **Application** — Step-by-step guidance (templates for components, questions for interactive, phases for workflows)
4. **Examples** — Worked examples using ChemTrack running scenario
5. **Common Pitfalls** — Named failure modes with consequences and fixes
6. **References** — Related skills, external frameworks, book citations

---

## Repository Structure

```
RE-Skills-zh/
├── README.md                 # This file
├── START_HERE.md             # New-user onboarding guide
├── LIST.md                   # Complete skill catalog for review
├── CLAUDE.md                 # Agent instructions for Claude Code
├── CODEX.md                  # Agent instructions for OpenAI Codex
├── AGENTS.md                 # Agent operating philosophy (all platforms)
├── CONTRIBUTING.md           # Contributor guide
├── skills/                   # All 44 skill directories
│   ├── skill-name/
│   │   ├── SKILL.md          # Main skill content
│   │   ├── template.md       # Fill-in template (29 component skills)
│   │   └── examples/
│   │       └── sample.md     # Worked examples
│   └── ...
├── commands/                 # 9 slash commands for multi-skill workflows
│   ├── develop-requirements.md
│   ├── elicit.md
│   ├── analyze.md
│   ├── write-srs.md
│   ├── validate.md
│   ├── prioritize.md
│   ├── manage-requirements.md
│   ├── agile-re.md
│   └── analyze-change.md
├── catalog/                  # Machine-readable indexes
│   ├── skills-index.yaml
│   ├── skills-by-type.md
│   ├── commands-index.yaml
│   └── commands.md
└── docs/                     # Platform integration guides
    ├── Using RE Skills with Claude Code.md
    ├── Using RE Skills with Codex.md
    └── Using RE Skills with Chat.md
```

**File counts:**
- 44 SKILL.md files (29 component + 7 interactive + 8 workflow)
- 29 template.md files (one per component skill)
- 44 examples/sample.md files (one per skill)
- 9 command workflow files
- **126+ total markdown files**

---

## Source Material

All skills are derived from:

- **Karl Wiegers & Joy Beatty**, *Software Requirements, Third Edition* (2013, Microsoft Press) — The primary source for all techniques, frameworks, and processes
- **Alistair Cockburn**, *Writing Effective Use Cases* (2001) — Use case levels and structure
- **Tom Gilb**, *Competitive Engineering* (2005) — Planguage notation for NFRs
- **Tom DeMarco**, *Structured Analysis and System Specification* (1979) — Data flow diagrams
- **Michael Fagan**, *Software Inspection* — Formal inspection process
- **IEEE 29148:2018** — Systems and software engineering requirements processes
- **ISO/IEC 25010:2011** — Systems and software quality models
- **Mike Cohn**, *User Stories Applied* (2004) — User story format
- **Stephen Withall**, *Software Requirement Patterns* (2007) — Requirements reuse

---

## Compatibility

These skills are plain markdown files with YAML frontmatter. They work with any AI agent or tool that can read structured text:

| Platform | How to Use |
|----------|-----------|
| **Claude Code** | Add `skills/` directory to your project; reference skills in conversation |
| **Cowork** | Upload skill files as project knowledge |
| **OpenAI Codex** | Include skill files in repository context |
| **Cursor / Windsurf** | Add to project rules or include in context |
| **Custom agents** | Read SKILL.md files and follow the Application section |

---

## Acknowledgements

This project's engineering architecture — skill types, YAML frontmatter schema, command workflows, catalog indexes, and agent integration patterns — is directly inspired by **[Product-Manager-Skills](https://github.com/deanpeters/Product-Manager-Skills)** by [Dean Peters](https://github.com/deanpeters).

Product-Manager-Skills is a pioneering open-source library of 47 product management skills designed for AI agents. It established the three-tier skill model (Component / Interactive / Workflow), the `commands/` slash-command abstraction layer for multi-skill orchestration, machine-readable `catalog/` indexes, and the multi-platform agent compatibility approach (Claude Code, Codex, Cowork, Cursor, and more). Its "ABC — Always Be Coaching" philosophy — that skills should teach humans while empowering agents — directly shaped how RE-Skills balances pedagogic intent with agent-readiness.

We adopted the following patterns from Product-Manager-Skills:

| Pattern | What We Learned |
|---------|----------------|
| YAML frontmatter schema (`name`, `description`, `intent`, `type`, `best_for`, `scenarios`) | Standardized metadata for skill discovery and agent routing |
| Three-tier type system (Component / Interactive / Workflow) | Clean separation of artifacts, guided flows, and orchestrations |
| `commands/` directory with YAML frontmatter | Slash commands that chain multiple skills into single-invocation workflows |
| `catalog/` with YAML + Markdown indexes | Machine-readable and human-readable skill discovery |
| `CLAUDE.md` + `CODEX.md` + `AGENTS.md` | Per-platform agent instructions for seamless integration |
| `START_HERE.md` with comfort-level branching | User onboarding that meets people where they are |
| `CONTRIBUTING.md` with quality checklists | Consistent contributor experience and skill quality |
| Interactive skill protocol (3-5 questions, numbered options, multi-select) | Structured conversational UX that agents can follow reliably |
| `examples/sample.md` per skill | Quality benchmarks that agents can reference before producing output |

If you're building skill libraries for other professional domains, Product-Manager-Skills is the reference architecture to start from.

---

## License

This repository is provided for educational and professional use.
