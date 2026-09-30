# 综述：高层语义驱动的虚拟人群仿真

> 这是一个协作式文献调研项目，研究如何利用高层语义信息（语言、目标、社会语境、
> 世界知识）来驱动虚拟人群的仿真。

---

## 🎯 研究问题

**高层语义信息如何使虚拟人群仿真更加真实、可控、可扩展？**

综述回答五个核心子问题：

1. 传统人群仿真如何表示人的行为？
2. 基于规则和数据驱动的方法存在哪些局限？
3. 大语言模型与生成式模型如何提供语义层级的控制？
4. 个体智能体如何涌现出人群级行为？
5. 在真实虚拟世界人口生成上还存在哪些挑战？

---

## 📚 研究范围

本综述处于以下方向的交叉：

- 🚶 **人群仿真**
- 👤 **虚拟人**
- 🤖 **多智能体系统**
- 🧠 **大语言模型（LLM）**
- 🎨 **生成式 AI**
- 🛰️ **语义场景理解**
- 🏙️ **程序化人口生成**
- 🧭 **行为生成**
- 🧬 **基于智能体的仿真**

---

## 🗂️ 仓库结构

```
Survey_LLM-Crowds/
├── README.md                  ← 项目说明（英文）
├── README.zh-CN.md            ← 你正在阅读
├── AGENTS.md                  ← 协作 / 智能体守则（请勿删除）
├── CONTRIBUTING.md            ← 贡献指南
├── CODE_OF_CONDUCT.md         ← 社区规范
├── ROADMAP.md                 ← 研究路线图与时间表
├── CHANGELOG.md               ← 里程碑日志
├── CITATION.cff               ← 如何引用本工作
│
├── docs/                      ← 研究框架文档
│   ├── research-questions.md  ← 研究问题
│   ├── taxonomy.md            ← 分类体系
│   ├── search-strategy.md     ← 检索策略
│   └── related-surveys.md     ← 相关综述
│
├── papers/                    ← 单篇论文笔记（每篇一篇文件）
│   ├── _template.md           ← 必读 —— 复制此模板再开始写
│   └── INDEX.md               ← 论文总索引
│
├── taxonomy/                  ← 按维度交叉索引
│   ├── by-semantic-level.md   ← 按语义层级
│   ├── by-generation-mechanism.md  ← 按生成机制
│   └── by-simulation-target.md     ← 按仿真目标
│
├── surveys/                   ← 综述论文本身
│   ├── outline.md             ← 大纲
│   └── writing-progress.md    ← 写作进度
│
├── references/                ← 共享文献库
│   ├── bibliography.bib
│   └── README.md
│
└── meetings/                  ← 团队会议记录
    └── README.md
```

---

## 🚀 快速开始

1. 阅读 [`AGENTS.md`](./AGENTS.md) —— 了解协作规则与智能体权限。
2. 阅读 [`docs/research-questions.md`](./docs/research-questions.md) —— 了解综述的研究框架。
3. 阅读 [`docs/taxonomy.md`](./docs/taxonomy.md) —— 了解三轴分类方案
   （语义层级 × 生成机制 × 仿真目标）。
4. 打开 [`papers/_template.md`](./papers/_template.md) —— 每篇论文笔记都必须按此模板撰写。
5. 阅读 [`CONTRIBUTING.md`](./CONTRIBUTING.md) —— 了解 PR 工作流。

---

## 👥 如何贡献

欢迎所有团队成员贡献：

- ➕ **添加一篇论文**：复制 `papers/_template.md`，填好后注册到 `papers/INDEX.md`，发起 PR。
- 🏷️ **完善分类**：编辑 `taxonomy/` 下对应文件，把论文链接到合适的维度。
- 📝 **撰写综述正文**：在 `surveys/drafts/` 下工作，参考 `surveys/outline.md` 共识结构。
- 🐛 **报告问题**：使用 `.github/ISSUE_TEMPLATE/` 中的模板。

详见 [`CONTRIBUTING.md`](./CONTRIBUTING.md)。

---

## 📌 状态

🚧 **项目筹备期**。脚手架已建立，论文库为空。工作计划见 [`ROADMAP.md`](./ROADMAP.md)。

---

## 📄 许可

代码与非文本资源以 [MIT License](./LICENSE) 发布。
论文笔记与综述正文以 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 发布
（如期刊政策覆盖此许可，则以期刊政策为准），具体见
`surveys/writing-progress.md` 的目标期刊与说明。

---

## 📬 联系方式

在本仓库提交 Issue 或 Discussion。私人协调渠道见 `ROADMAP.md`。