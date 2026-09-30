# Roadmap

This file tracks the project's research and writing timeline. Update it when
milestones shift, and reference it from every team meeting.

---

## 🎯 Goal

Produce a peer-reviewable survey paper on **High-Level Semantic Driven Virtual
Human Crowd Simulation**, targeting a high-quality venue (TBD — see
`surveys/writing-progress.md`).

---

## 👥 Team & Roles

| Role | Responsibility |
|---|---|
| Lead | Final say on taxonomy and structure; chairs meetings. |
| Sub-reviewer (×N) | Lead on a survey section; recruits papers in that area. |
| Note-taker | Rotating; writes the meeting note in `meetings/`. |
| Tooling | Maintains templates, lint, citation hygiene. |

> Insert concrete names and handles once the team is finalised. Keep this list
> in version control so it is easy to update.

---

## 🛣️ Phases

### Phase 0 — Scaffolding (current)

- ✅ Repo structure created.
- ✅ Templates, taxonomy axes, contribution rules in place.
- 🔲 First team meeting; agree on venues and scope boundaries.
- 🔲 Initial seed paper list (≥30 candidate papers).

### Phase 1 — Paper Collection

- 🔲 Search strategy finalised in `docs/search-strategy.md`.
- 🔲 ≥150 candidate papers identified, deduplicated.
- 🔲 Each candidate screened for relevance (in/out decision logged in
  `papers/INDEX.md`).

### Phase 2 — Annotation

- 🔲 Each in-scope paper has a `papers/*.md` note conforming to the template.
- 🔲 Every paper classified on all three taxonomy axes.
- 🔲 Cross-cuts in `taxonomy/` reviewed by ≥2 reviewers per axis.

### Phase 3 — Drafting

- 🔲 `surveys/outline.md` agreed.
- 🔲 Section drafts in `surveys/drafts/<section>.md`.
- 🔲 Figure / table placeholders assigned.

### Phase 4 — Consolidation & Submission

- 🔲 Single coherent draft.
- 🔲 Internal review by all co-authors.
- 🔲 External review (advisor / external collaborator).
- 🔲 Submission to chosen venue.

---

## 📅 Milestones

| Date (target) | Milestone |
|---|---|
| YYYY-MM-DD | Kickoff meeting |
| +2 weeks | Search strategy agreed; ≥30 candidate papers |
| +6 weeks | ≥150 candidate papers; first 50 annotated |
| +12 weeks | All in-scope papers annotated |
| +16 weeks | First full draft of the survey |
| +20 weeks | Internal review complete |
| +22 weeks | Submission |

> Replace placeholders with real dates during the kickoff meeting.

---

## 📡 Communication

- **Async**: GitHub Issues and Discussions in this repo.
- **Sync**: weekly team meeting; notes in `meetings/`.
- **Chat**: link goes here once the team channel exists.

---

## 🧭 Decision-making protocol

This section is for high-level decisions that affect the survey structure
itself (taxonomy axes, in/out scope, venue). Anything else can be settled by
a PR.

| Decision | Process |
|---|---|
| Add a paper | PR + 1 reviewer |
| Update taxonomy axis description | PR + 2 reviewers |
| Add / rename / remove a survey section | Discussion + lead approval |
| Change the timeline | PR against this file + lead approval |
| Change the venue | Meeting + lead approval, logged in `surveys/writing-progress.md` |

---

## 🪪 License note for this file

This file is project metadata. It is released under the same terms as the rest
of the project (MIT for code-like content, CC BY 4.0 for prose).