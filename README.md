# Survey: High-Level Semantic Driven Virtual Human Crowd Simulation

> A collaborative literature review on leveraging high-level semantic information
> (language, goals, social context, world knowledge) to drive virtual human crowd
> simulation.

---

## 🎯 Research Question

**How can high-level semantic information enable more realistic, controllable,
and scalable virtual human crowd simulation?**

The review addresses five core sub-questions:

1. How have traditional crowd simulations represented human behavior?
2. What limitations exist in rule-based and data-driven approaches?
3. How can LLMs and generative models provide semantic-level control?
4. How can individual agents generate emergent crowd behaviors?
5. What challenges remain for realistic virtual world population?

---

## 📚 Scope

This survey sits at the intersection of:

- 🚶 **Crowd simulation**
- 👤 **Virtual humans**
- 🤖 **Multi-agent systems**
- 🧠 **Large Language Models (LLMs)**
- 🎨 **Generative AI**
- 🛰️ **Semantic scene understanding**
- 🏙️ **Procedural population generation**
- 🧭 **Behavior generation**
- 🧬 **Agent-based simulation**

---

## 🗂️ Repository Structure

```
Survey_LLM-Crowds/
├── README.md                  ← you are here
├── README.zh-CN.md            ← 中文版项目说明
├── AGENTS.md                  ← agent / collaborator guidance (do not delete)
├── CONTRIBUTING.md            ← how to contribute
├── CODE_OF_CONDUCT.md         ← community guidelines
├── ROADMAP.md                 ← research roadmap & timeline
├── CHANGELOG.md               ← milestone log
├── CITATION.cff               ← how to cite this work
│
├── docs/                      ← research framing documents
│   ├── research-questions.md
│   ├── taxonomy.md
│   ├── search-strategy.md
│   └── related-surveys.md
│
├── papers/                    ← individual paper notes (one file per paper)
│   ├── _template.md           ← REQUIRED template — copy this before each note
│   └── INDEX.md               ← master index of all catalogued papers
│
├── taxonomy/                  ← curated cross-cuts of the paper database
│   ├── by-semantic-level.md
│   ├── by-generation-mechanism.md
│   └── by-simulation-target.md
│
├── surveys/                   ← the survey paper itself
│   ├── outline.md
│   └── writing-progress.md
│
├── references/                ← shared bibliography
│   ├── bibliography.bib
│   └── README.md
│
└── meetings/                  ← team meeting notes (one file per meeting)
    └── README.md
```

---

## 🚀 Getting Started

1. Read [`AGENTS.md`](./AGENTS.md) to understand the agent / collaborator rules
   (what the AI assistant may and may not do, citation hygiene, etc.).
2. Read [`docs/research-questions.md`](./docs/research-questions.md) to
   understand the framing of the survey.
3. Read [`docs/taxonomy.md`](./docs/taxonomy.md) to understand the three-axis
   classification scheme (semantic level × generation mechanism × simulation
   target).
4. Open [`papers/_template.md`](./papers/_template.md) — every paper note must
   follow this template.
5. Read [`CONTRIBUTING.md`](./CONTRIBUTING.md) for the pull-request workflow.

---

## 👥 Contributing

Contributions are welcome from any teammate.

- ➕ **Add a paper**: copy `papers/_template.md`, fill it in, register the
  entry in `papers/INDEX.md`, and open a pull request.
- 🏷️ **Improve taxonomy**: edit the relevant file in `taxonomy/` and link the
  paper from the appropriate axis.
- 📝 **Draft survey text**: work in `surveys/drafts/`, see
  `surveys/outline.md` for the agreed structure.
- 🐛 **Report an issue**: use the `.github/ISSUE_TEMPLATE/` forms.

See [`CONTRIBUTING.md`](./CONTRIBUTING.md) for the full workflow.

---

## 📌 Status

🚧 **Pre-kickoff.** The scaffolding has just been created; the paper database
is empty. See [`ROADMAP.md`](./ROADMAP.md) for the work plan.

---

## 📄 License

Code, scripts and non-textual artifacts are released under the [MIT License](./LICENSE).
Paper notes and survey text are released under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) unless a paper
publisher's policy overrides this — see `surveys/writing-progress.md` for the
current target venue and any policy notes.

---

## 📬 Contact

Open an issue or discussion in this repository. For private coordination,
refer to the team channel listed in `ROADMAP.md`.