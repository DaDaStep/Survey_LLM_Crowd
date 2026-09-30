# Search Strategy

This document describes how we collect candidate papers, so that the corpus
is reproducible and defensible at review time.

---

## 1. Source databases

Primary:

- arXiv (cs.CV, cs.CL, cs.MA, cs.AI, cs.GR).
- Google Scholar.
- Semantic Scholar.
- Connected Papers / Litmaps (for citation-graph exploration).

Secondary (snowball from the primary set):

- ACM Digital Library, IEEE Xplore, Elsevier ScienceDirect.
- DBLP for venue / year verification.

Domain-specific:

- Eurographics / ACM SIGGRAPH papers (graphics venue filtering).
- Crowd-simulation community venues (Pedestrian and Evacuation Dynamics,
  Transportation Research Board).

---

## 2. Seed queries

The following queries are starting points. Refine per axis as coverage gaps
appear.

| Axis | Query |
|---|---|
| LLM-driven agents | `"large language model" AND ("crowd simulation" OR "multi-agent simulation" OR "virtual agent")` |
| Generative crowd | `("diffusion model" OR "generative model") AND ("crowd" OR "pedestrian" OR "multi-agent")` |
| Language-driven behaviour | `"language-guided" OR "text-driven" AND ("motion" OR "navigation" OR "behavior")` |
| Semantic scene understanding | `"scene graph" AND ("pedestrian" OR "human behavior" OR "crowd")` |
| Procedural population | `"procedural" AND ("population" OR "urban simulation" OR "virtual world")` |
| Crowd simulation foundations | `"social force model" OR "RVO" OR "ORCA" OR "cellular automata" AND crowd` |

Queries are **starting points**, not the final list. Each query should yield
≥20 distinct candidate titles; if not, broaden the query.

---

## 3. Inclusion criteria

A paper is **in scope** if it satisfies all of:

1. It proposes a method, model, framework, or empirical study for **virtual
   human crowd simulation** (or a closely-related sub-task).
2. It explicitly handles **high-level semantics**, or it is a foundational
   paper that the team agrees must be cited (e.g. Helbing's social-force
   model).
3. It is published in a recognised venue or as a peer-reviewed preprint.

If the paper is borderline, open a discussion issue with the tag
`scope-question` and assign to the lead.

---

## 4. Exclusion criteria

- Pure low-level trajectory prediction with no simulation context.
- Pure NLP papers without a virtual-world / crowd anchor.
- Vision papers that only predict behaviour from video (no simulation).
- Workshop abstracts / non-archival extended abstracts unless they are the
  only available record of an influential system.

---

## 5. Deduplication & versioning

- One canonical paper per DOI / arXiv ID. If a paper has both a conference
  and a journal version, cite the journal version and note the conference
  version in `papers/INDEX.md`.
- Versioning: each paper note records the version it was written against
  (e.g. `arXiv v3, 2024-08-12`).

---

## 6. Tracking

- Every accepted candidate is registered in `papers/INDEX.md` with status
  `candidate | in-scope | out-of-scope | duplicate`.
- The BibTeX entry lives in `references/bibliography.bib`.
- Every in-scope paper has a full note in `papers/`.

---

## 7. Reporting coverage

Run the following weekly during the annotation phase:

```bash
# number of in-scope papers per axis (rough, manual)
grep -c "^## Semantic Level" papers/*.md
grep -c "^## Crowd Simulation Aspect" papers/*.md
```

Targets:

| Axis | Target count |
|---|---|
| In-scope papers | ≥120 |
| High-level (primary) | ≥50 |
| LLM-based | ≥25 |
| Dense-crowd + large-scale | ≥60 |

If a target is off by ≥30% at the end of Phase 2, raise it at the sync.