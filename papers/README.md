# Papers

This folder holds **one Markdown file per paper** that the team has decided
to catalog. Every paper note follows [`_template.md`](./_template.md) and is
registered in [`INDEX.md`](./INDEX.md).

## How to add a paper

1. Copy `_template.md` to `<first-author-year-keyword>.md` (kebab-case, ASCII).
2. Fill in every required field (or write `N/A` and explain in one sentence).
3. Add the BibTeX entry to [`../references/bibliography.bib`](../references/bibliography.bib).
4. Register the entry in [`INDEX.md`](./INDEX.md) under the right status.
5. Cross-link from the relevant `taxonomy/*.md` page(s).
6. Open a pull request.

Full instructions: [`../CONTRIBUTING.md`](../CONTRIBUTING.md).

## Naming convention

`<last-name-of-first-author>-<year>-<keyword>.md`

Examples (illustrative — replace with real papers once the team adds them):

- `helbing-1995-social-force.md`
- `ren-2024-crowd-mm.md`
- `li-2024-language-crowd.md`

If the same first author publishes multiple papers in the same year,
disambiguate by topic keyword.

## Sub-folders (optional, discouraged early on)

Do not split into sub-folders until the database exceeds ~100 papers; a flat
structure is easier to search, lint, and cross-reference.

If you ever do split, the canonical split is:

```
papers/
├── foundational/         # rule-based, pre-deep-learning
├── data-driven/           # imitation / RL / behaviour cloning
├── llm-agents/            # LLM-driven agents
├── generative/            # diffusion / transformer generation
└── population/             # large-scale population / urban
```

This is recorded here so we do not bikeshed the split later.