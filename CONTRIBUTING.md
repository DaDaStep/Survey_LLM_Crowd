# Contributing

Thanks for collaborating on this survey! This document explains the day-to-day
workflow so that everyone's notes end up in the same shape.

> **TL;DR.** One paper = one Markdown file under `papers/`, copied from
> `papers/_template.md`. Register it in `papers/INDEX.md`, link it from the
> relevant taxonomy pages, then open a pull request.

---

## 1. Ground Rules

These mirror [`AGENTS.md`](./AGENTS.md) and apply to every human contributor
and any AI assistant they delegate to:

- ❌ **Do not fabricate.** No invented experimental results, no invented
  citations, no invented numbers.
- ❌ **Do not override consensus.** Final taxonomy and paper structure are
  decided by the team in meetings and tracked in `ROADMAP.md`.
- ✅ **Cite primary sources.** Always cite from the original paper. If you only
  read a secondary mention, mark the claim explicitly as such.
- ✅ **Use the template.** Every paper note starts from
  `papers/_template.md`. No blank required fields.
- ✅ **Write for the team.** Plain, neutral English. Avoid jargon that only one
  sub-field uses; if you must use it, define it inline.

---

## 2. Branching & Commits

- Default branch: `main` (this branch is protected — only merge via PR).
- One topic per branch. Suggested prefixes:
  - `papers/<first-author-year>` — adding or revising a single paper note
  - `taxonomy/<axis>` — taxonomy updates
  - `survey/<section>` — survey draft text
  - `docs/<topic>` — research framing docs
- Commit messages: short imperative summary + optional body explaining why.
  Example:

  ```
  papers: add CrowdMM note (Ren et al., 2024)

  Discusses language-conditioned crowd motion generation; classifies as
  high-level / generative / dense crowds.
  ```

---

## 3. Adding a Paper

1. Pick a paper that fits the scope in
   [`docs/research-questions.md`](./docs/research-questions.md). If unsure,
   open an issue tagged **Proposed paper** first.
2. Create a new branch: `git checkout -b papers/<key>`.
3. Copy the template:
   `cp papers/_template.md papers/<first-author-year-keyword>.md`
4. Fill in **every** required field. If a field genuinely does not apply,
   write `N/A` and explain in one sentence.
5. Add the citation to `references/bibliography.bib` (BibTeX).
6. Register the entry in `papers/INDEX.md` (alphabetical by first author).
7. Add the paper to the relevant taxonomy page(s) under `taxonomy/`:
   - `by-semantic-level.md`
   - `by-generation-mechanism.md`
   - `by-simulation-target.md`
8. Run the pre-PR checklist (see below), then open the PR using
   [`.github/PULL_REQUEST_TEMPLATE.md`](./.github/PULL_REQUEST_TEMPLATE.md).

---

## 4. Pre-PR Checklist

Before clicking "Create pull request":

- [ ] File lives under `papers/` and starts from `papers/_template.md`.
- [ ] All required fields are filled or explicitly marked `N/A`.
- [ ] Citation appears in `references/bibliography.bib`.
- [ ] Paper is listed in `papers/INDEX.md`.
- [ ] Paper is cross-linked from the appropriate `taxonomy/*.md` files.
- [ ] No claim is sourced from a non-primary source unless flagged.
- [ ] No invented numbers, screenshots, or quotes.
- [ ] Markdown renders correctly (preview locally if possible).
- [ ] Filename uses the convention `papers/<firstauthor-year-keyword>.md`
      (kebab-case, ASCII only).

---

## 5. Reviewing

- One approving review is enough for paper notes.
- Two approving reviews are required for changes to `taxonomy/`,
  `surveys/outline.md`, and `docs/research-questions.md`.
- Reviewers should check: factual accuracy against the paper, taxonomy
  classification, and template compliance.

---

## 6. AI Assistant Use

You may use AI assistants to help draft, but the human reviewer is
accountable for:

- Verifying every factual claim against the source paper.
- Ensuring no hallucinated citations or results.
- Owning the final wording — do not paste AI output uncritically.

The assistant's stand-alone rules are in [`AGENTS.md`](./AGENTS.md).

---

## 7. Questions?

Open an issue with the **question** label, or ask in your team channel.