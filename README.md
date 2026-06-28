# app-blueprint-elaborator

A Claude skill that transforms a rough app idea into a research-backed technical blueprint — with a built-in **critical layer** that pressure-tests the idea, two **depth modes**, and an optional **builder-ready handoff spec**. Ready to hand to a dev team or use in an investor pitch.

---

## What It Does

Given an application brief, this skill:

1. **Gates the optional modes first** — on activation it asks whether you want the deeper modes, and only runs them if you say yes (see [Two Modes](#two-modes--optional-handoff) below).
2. **Analyzes the brief** — core problem, job-to-be-done, technical domain, personas, scale, and regulatory surface. Handles thin briefs by asking ≤2 sharp questions or stating explicit assumptions rather than guessing silently.
3. **Conducts live research** — targeted web searches on competitors, tech stacks, AI/ML integrations, regulatory / scalability / data-isolation constraints, third-party APIs, and (in Deep mode) cost signals to inform build-vs-buy.
4. **Elaborates the design** — core mechanics + data model, tenancy / auth / security, and 4–5 researched add-on features. No buzzwords, no invented statistics.
5. **Pressure-tests it** — a *Risks & Open Questions* pass covering wrong-if-false assumptions, technical and market risks, and the decisions left to you.
6. **Outputs a structured blueprint** — Quick or Deep, diagram-rich, with cited references, plus an optional paste-ready handoff spec.

---

## Two Modes + Optional Handoff

The skill **always asks first** which to run — it never silently picks Deep or handoff:

- **Quick** — a tight blueprint (~500–600 words, one diagram) for pitching, validating direction, or early ideation. This is what runs if you decline the deeper modes.
- **Deep** — a hand-to-the-team build-spec: multiple diagrams (system + ER data model + key workflow), tenancy & security, non-functional requirements, MVP / v1 / later phasing, build-vs-buy calls, and a full risk section.
- **Prototype-handoff (optional add-on)** — a builder-ready, MVP-scoped spec tuned for **Lovable / Bolt / v0 / Replit**, with honest guidance on which tool fits the job.

**Deep mode and the handoff spec run only on an explicit yes.** The one exception: if your opening request already names the mode (e.g. *"deep spec with a Bolt handoff"*), it treats that as the yes and skips the question.

---

## Output Structure

**Quick mode:**

- **🗺 The Blueprint** — 3–5 sentence summary of the architecture and approach
- **⚙️ Core Mechanics** — components, data flow, tech decisions, and the tenancy/auth approach in one line each
- **💡 Suggested Features & Add-ons** — researched extensions with *why* and *how* for each
- **⚠️ Risks & Open Questions** — wrong-if-false assumptions, the biggest risk, open questions, and an MVP-first suggestion
- **🔀 System Diagram** — valid Mermaid flowchart or sequence diagram
- **📚 References** — at least 3 real, cited URLs from the research phase

**Deep mode** additionally produces: an *Assumptions* note, a dedicated *Data Model* (ER diagram), *Tenancy / Auth / Security*, *Non-Functional Requirements*, *Build vs Buy*, explicit *Phasing*, an expanded *Risks* section, and **≥3 diagrams**.

---

## How to Trigger

Mention `app-blueprint-elaborator` alongside your app idea, or ask for a technical blueprint, architecture plan, system design, or build plan for a product concept. On activation it will ask which mode(s) to run before producing anything.

**Examples:**

```
app-blueprint-elaborator: I want to build a voice journalling app where you speak and it saves transcribed entries.
```

```
Run app-blueprint-elaborator on this idea: a Slack bot that auto-triages customer support tickets using AI.
```

```
app-blueprint-elaborator — deep build-spec with a Bolt handoff for: a multi-tenant invoicing SaaS for freelancers.
```

*(The last example names the modes up front, so it skips the gate question.)*

---

## Installation

This skill ships as `app-blueprint-elaborator.skill` (a zip archive of the skill folder).

1. In Claude's **Settings → Skills / Capabilities**, choose to upload a skill.
2. Select `app-blueprint-elaborator.skill`.
3. Enable it, then trigger it as shown above.

*(The exact menu label may vary slightly by platform and plan.)*

---

## Requirements

- Requires the **web_search tool** to be available (used in Steps 1–2 for live research).
- The optional handoff mode references the current capabilities of external builders (Lovable / Bolt / v0 / Replit); the skill instructs Claude to **verify volatile tool and pricing facts at runtime** before stating them.

---

## File Structure

```
.
├── README.md                       # this file (project documentation)
└── app-blueprint-elaborator/       # the skill — packaged as app-blueprint-elaborator.skill
    ├── SKILL.md                    # gate, workflow, modes, Quick template, checklist
    └── references/
        ├── deep-template.md        # Deep-mode output template (loaded on opt-in)
        ├── handoff-mode.md         # optional builder-handoff spec (loaded on opt-in)
        └── mermaid-cheatsheet.md   # diagram syntax guardrails
```
