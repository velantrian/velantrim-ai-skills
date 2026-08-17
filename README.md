# 🧩 Velantrim AI Skills

> **Reusable, project-neutral AI operational skills for repository auditing, CI/governance review, truth routing, reproducibility, evidence validation, documentation quality, risk analysis, and bounded engineering workflows.**

🌍 Built for Velantrim projects **and** other software/research repositories.  
🔒 Read-only by default.  
🧭 Target-project authority always wins over generic skill guidance.  
🤖 AI entry point: [`docs/ai/README.md`](docs/ai/README.md)

---

## 👤 Start here — what is this?

`velantrim-ai-skills` is a neutral tooling repository for reusable AI procedures.

A skill from this repository can inspect a project, help structure an audit, compare GitHub with connected documentation, identify CI/governance risks, or propose bounded remediation. It does **not** become part of the inspected project's architecture and does **not** inherit authority from it.

Think of it as an external toolbox:

```text
                     🧩 Velantrim AI Skills
                              │
                    neutral external tooling
                              │
          ┌───────────────────┼───────────────────┐
          ▼                   ▼                   ▼
     🔍 Audit skills      ⚙️ CI/governance    📚 Truth routing
          │                   │                   │
          └───────────────────┼───────────────────┘
                              ▼
                    🧭 Inspect target project
                              │
                              ▼
                  project-specific authority
                         remains in control
```

---

## 🌳 Repository tree

```text
🧩 velantrim-ai-skills/
├── 📖 README.md                    # human-first English entry
├── 📖 README.ru.md                 # human-first Russian entry
├── 🤖 AGENTS.md                    # repository-wide AI operating boundaries
├── 🤖 docs/
│   └── ai/
│       └── README.md               # compact AI entry + reading order
└── 🧰 skills/
    ├── README.md                   # skill catalogue entry
    └── 🔍 github-notion-repository-audit/
        ├── SKILL.md                # canonical audit methodology
        ├── references/             # focused checklists/guidance
        └── templates/              # reusable report/finding/remediation forms
```

---

## 🔍 First reusable skill

### [`github-notion-repository-audit`](skills/github-notion-repository-audit/SKILL.md)

A project-neutral, evidence-based method for auditing repositories whose operational truth may span GitHub, Notion or other documentation surfaces, CI, tests, governance, source code, reproducibility and supply-chain state.

It covers, when relevant:

- 🧭 live-first baselining and authority discovery;
- 🔐 branch/ruleset/merge-governance review;
- ⚙️ CI gate and deadlock analysis;
- 🧪 supported test execution and negative-test gaps;
- 📚 GitHub ↔ Notion/documentation truth routing;
- 🔁 per-role freshness instead of one misleading global sync marker;
- 📦 dependency and reproducibility review;
- 🧯 declared limitation vs newly discovered defect;
- 🛠️ minimal remediation + Definition of Done;
- 🚦 explicit recommendation/authorization boundaries.

The skill intentionally does **not** hard-code target-project SHAs, issue numbers, experiment names, page IDs, architecture vocabulary, reviewer policy, runtime, language, or database assumptions.

---

## 🔒 Operating boundaries

```text
project-specific authority  >  generic skill defaults
read-only by default
writes require explicit authorization
UNKNOWN stays UNKNOWN
recommendation != authorization
CI success != production readiness
mirror/sync metadata != runtime evidence
ordinary review != specialized independent qualification
public repository != open-source license
```

Skills must not silently change repositories, external systems, governance settings, issues, pull requests, CI, releases, or documentation merely because a remediation appears obvious.

This repository is **not** part of the architecture of Native Kernel, Titan, Crystal, Mentaury, Continuum, or any other inspected project. Those names are examples of possible consumers, not authority relationships.

---

## 🤖 For AI agents

Do **not** reconstruct operating rules from this README alone.

Use this reading order:

```text
1. AGENTS.md
2. docs/ai/README.md
3. skills/README.md
4. selected skill/SKILL.md
5. selected skill/references/* as needed
6. selected skill/templates/* when producing output
7. target project's own authority/governance docs
```

The dedicated AI entry point contains a compact structured summary and explains when project-specific rules override this repository.

➡️ [`docs/ai/README.md`](docs/ai/README.md)

---

## 📚 Authority model

For **this repository**, GitHub is the technical source of truth for versioned skill content and history.

For **any repository being inspected**, the selected skill must discover that project's authority hierarchy instead of imposing one from Velantrim AI Skills.

No generic skill can promote itself into target-project authority.

---

## 🧠 Why no `project-state.json` yet?

A separate machine-state file would only be useful if this repository develops meaningful changing operational state that automation must consume.

Today the repository mainly contains versioned methodologies. Adding a JSON state file now would duplicate Markdown truth and create another drift surface. The AI entry therefore uses concise structured metadata inside Markdown instead.

If genuine machine-state appears later, add a versioned JSON schema deliberately rather than using JSON as decorative duplication.

---

## ⚖️ License

No license has been selected yet. Public visibility does not by itself grant permission to copy, modify, redistribute, or reuse the repository contents. License selection remains an owner decision.
