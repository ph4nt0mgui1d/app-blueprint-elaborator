# app-blueprint-elaborator

A Claude skill that transforms a rough app idea into a research-backed technical blueprint — ready to hand to a dev team or use in an investor pitch.

---

## What It Does

Given an application brief, this skill:

1. **Analyzes the brief** — identifies the core problem, technical domain, user personas, and scale expectations.
2. **Conducts live research** — runs targeted web searches on competitors, tech stacks, AI/ML integrations, regulatory concerns, and relevant third-party APIs.
3. **Elaborates the design** — fleshes out core mechanics and proposes 4–5 high-value add-on features grounded in research findings.
4. **Outputs a structured blueprint** — a concise, diagram-rich document including a Mermaid system diagram and cited references.

---

## Output Structure

Every blueprint follows this template:

- **🗺 The Blueprint** — 4–5 sentence technical summary of the architecture and approach
- **⚙️ Core Mechanics** — bullet-point breakdown of components, data flow, and tech decisions
- **💡 Suggested Features & Add-ons** — researched extensions with *why* and *how* for each
- **🔀 System / Workflow Diagram** — valid Mermaid flowchart or sequence diagram
- **📚 References** — at least 3 real, cited URLs from the research phase

---

## How to Trigger

Mention `app-blueprint-elaborator` alongside your app idea, or ask for a technical blueprint, architecture plan, or system design for a product concept.

**Examples:**

```
app-blueprint-elaborator: I want to build a voice journalling app where you speak and it saves transcribed entries.
```

```
Run app-blueprint-elaborator on this idea: a Slack bot that auto-triages customer support tickets using AI.
```

---

## Requirements

- Requires the **web_search tool** to be available (used in Steps 1–2 for live research).

---

## File Structure

```
app-blueprint-elaborator/
└── SKILL.md       # Skill definition and workflow instructions
```
