# References

The shared bibliography lives in [`bibliography.bib`](./bibliography.bib).
Every paper note under `papers/` **must** have an entry here.

---

## Conventions

- One entry per DOI / arXiv ID. Use the **journal / venue-of-record**
  version where one exists; cite the conference version only if there is no
  journal version.
- BibTeX keys: `<firstauthor-lastname><year><keyword>`. Lowercase, no
  underscores. Examples:
  - `helbing1995social`
  - `ren2024crowdmm`
  - `li2024langcrowd`
- If two papers collide, append `a`, `b`, …
- URL field: prefer DOI URL (`https://doi.org/...`) over arXiv or vendor
  pages.
- Keep field order: `author`, `title`, `booktitle | journal`, `year`,
  `volume`, `number`, `pages`, `publisher`, `doi`, `url`, `eprint`,
  `archivePrefix`.

---

## Quality control

Before merging a PR that adds a citation:

- [ ] The key is unique and matches the convention.
- [ ] The DOI / URL resolves.
- [ ] The paper is in-scope in `papers/INDEX.md`.
- [ ] The paper note references the same key.

If a paper has a non-Latin-script title, include the transliterated title in
`title` and the original in a `note` field.