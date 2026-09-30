# Taxonomy

Every catalogued paper is classified on **three orthogonal axes**:

1. **Semantic input level** — what kind of input the model consumes.
2. **Generation mechanism** — how the model produces behaviour.
3. **Simulation target** — what scale / scene the paper evaluates on.

A paper can sit on multiple categories within an axis (e.g. *high-level +
mid-level*) and should be cross-linked accordingly in `taxonomy/`.

---

## Axis 1 — Semantic Input Level

| Level | Examples | Typical representation |
|---|---|---|
| Low-level | trajectories, velocity, motion primitives | point clouds, optical flow, skeletons |
| Mid-level | activities, navigation goals, interaction rules | discrete activity labels, waypoints |
| High-level | natural language, social intention, environmental context, world knowledge | text, scene graphs, knowledge bases |

### Rules

- Pick the **highest** level the paper conditions its behaviour on. If the
  paper uses multiple, list all and pick one as the *primary*.
- The same paper may legitimately be *high-level + mid-level* if it grounds
  language into waypoints.
- The full cross-cut lives in [`taxonomy/by-semantic-level.md`](../taxonomy/by-semantic-level.md).

---

## Axis 2 — Generation Mechanism

| Category | Brief |
|---|---|
| Rule-based simulation | hand-crafted force models, cellular automata, social-force, RVO |
| Data-driven learning | supervised / imitation learning over motion data |
| Neural behaviour generation | RL, diffusion, VAE, GAN on behaviour representations |
| Generative models | diffusion / transformer-based generation of motion, scenes, or agents |
| LLM-based agents | agents driven (wholly or partly) by an LLM |
| Multi-agent systems | MAS frameworks, agent communication, emergent interaction |

### Rules

- A paper that combines LLM + RL is `LLM-based agents` (primary) + `Neural
  behaviour generation` (secondary).
- "Generative models" is reserved for papers whose contribution is the
  generative model itself, not merely the use of an existing diffusion model.
- The full cross-cut lives in
  [`taxonomy/by-generation-mechanism.md`](../taxonomy/by-generation-mechanism.md).

---

## Axis 3 — Simulation Target

| Target | Scale | Examples |
|---|---|---|
| Individual virtual human | one agent | single-character motion synthesis |
| Small groups | 2–10 agents | dyadic interaction, team navigation |
| Dense crowds | tens–hundreds of agents | pedestrian flows, evacuation |
| Large-scale virtual worlds | thousands+ of agents | city-scale populations |
| Urban environments | environmental focus | street / building / transit |

### Rules

- Pick the scale of the **evaluation**, not the maximum scale mentioned in
  related work.
- A paper may target multiple scales (e.g. small group *and* dense crowd) —
  list both and pick a primary.
- The full cross-cut lives in
  [`taxonomy/by-simulation-target.md`](../taxonomy/by-simulation-target.md).

---

## How axes interact

A useful shorthand for talking about a paper in the survey text is:

> *"[Paper] is a [high-level] [LLM-based] [dense-crowd] system for …"*

When in doubt about classification, raise it in the weekly sync. Re-classification
is cheap; misclassification in the final draft is expensive.

---

## Versioning

This is **v0.1** of the taxonomy. Edit only after discussion; record the change
in `CHANGELOG.md` and link the discussion thread.