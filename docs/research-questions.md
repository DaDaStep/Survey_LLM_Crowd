# Research Questions

> Living document. Any change to the framing of the survey must be agreed in
> a team meeting and recorded in the corresponding `meetings/` note.

---

## Main Question

**How can high-level semantic information enable more realistic, controllable,
and scalable virtual human crowd simulation?**

---

## Sub-questions

| # | Question | Where it lands in the survey |
|---|---|---|
| Q1 | How have traditional crowd simulations represented human behavior? | Background & related work |
| Q2 | What limitations exist in rule-based and data-driven approaches? | Background & motivations |
| Q3 | How can LLMs and generative models provide semantic-level control? | Core methods (Sections on language-driven behavior generation) |
| Q4 | How can individual agents generate emergent crowd behaviors? | Core methods (Sections on multi-agent simulation) |
| Q5 | What challenges remain for realistic virtual world population? | Discussion & future directions |

---

## Operational definitions

These definitions are **working consensus** for the project. Edit them only
after discussion.

### High-level semantic information

Any input or intermediate representation that goes beyond low-level motion
or mid-level activity labels. Includes:

- **Natural language** instructions, descriptions, scene captions, dialogue
  between agents.
- **Goals, intentions, and social roles** that constrain behaviour.
- **Environmental / world knowledge**, e.g. floor plans, event context,
  cultural norms, time of day.
- **Commonsense reasoning** about objects, affordances, other agents.

### Crowd simulation

A computational process that produces trajectories and/or interactions of
many virtual agents over time in a virtual environment. Includes:

- Pedestrian navigation and path planning.
- Group behaviour and crowd dynamics.
- Procedural population and city-scale simulation.

### Virtual human crowd

A simulated population of virtual humans (often embodied agents with a
visual representation). Both 2D and 3D representations are in scope, as are
non-physically-grounded conversational crowds.

---

## Out-of-scope (for now)

Marking boundaries explicitly avoids scope creep. Things explicitly **not** in
the survey's core, though they may appear in related-work:

- Pure trajectory-prediction papers with no semantic input and no simulation.
- Generic multi-agent reinforcement learning papers that do not address
  crowd scenarios.
- General-purpose LLM agents without a virtual-world / crowd focus.
- Non-simulation uses of LLM (captioning, retrieval, etc.) unless they
  directly feed a simulator.

---

## Connections to the taxonomy

Every paper note must record which sub-question(s) it informs. This is how we
ensure coverage: at the end of the annotation phase, every Q1–Q5 should have
≥20 papers explicitly mapped to it.

| Sub-question | Primary taxonomy axis (see `taxonomy.md`) |
|---|---|
| Q1 — Traditional methods | Generation mechanism = rule-based / data-driven; Semantic level = low + mid |
| Q2 — Limitations | Same as Q1, but emphasise papers that explicitly identify limitations |
| Q3 — LLMs / generative | Generation mechanism = LLM-based / generative; Semantic level = high |
| Q4 — Emergent multi-agent | Generation mechanism = multi-agent / LLM-agent; Simulation target = group / crowd |
| Q5 — Open challenges | Cross-cut: read every paper's *Limitations* and *Future work* sections |

---

## Reviewer-facing version

When the survey is submitted, the abstract and introduction should state Q1–Q5
explicitly. This file is the source of truth for that language.