# 🧩 Velantrim AI Skills

> **Reusable, project-neutral AI operational skills and role guidance for repository auditing, analysis, implementation, adversarial review, verification, CI/governance, truth routing, reproducibility, and bounded engineering workflows.**

🌍 Built for Velantrim projects **and** other software/research repositories.  
🔒 Read-only by default.  
🧭 Target-project authority always wins over generic role/skill guidance.  
🎭 AI role router: [`roles/README.md`](roles/README.md)  
🤖 AI entry point: [`docs/ai/README.md`](docs/ai/README.md)

---

## 👤 Start here — what is this?

`velantrim-ai-skills` is a neutral external toolbox for AI agents.

It contains two complementary layers:

- 🎭 **roles** — define what an AI is responsible for in the current stage and what it must not silently do;
- 🧰 **skills** — reusable methodologies/checklists for performing a specific kind of work.

A role or skill can help inspect, reason about, change, attack, or verify a project, but it **does not become part of that project's architecture and does not inherit authority from it**.

```text
                         🧩 Velantrim AI Skills
                                  │
                    neutral external tooling layer
                                  │
                 ┌────────────────┴────────────────┐
                 ▼                                 ▼
          🎭 WHO should AI be?               🧰 HOW should it work?
              roles/                               skills/
                 │                                 │
      ┌──────────┼──────────┐                      │
      ▼          ▼          ▼                      ▼
   🔍 Audit   🛠️ Build   🧨 Attack          reusable methodology
      │          │          │                      │
      └──────────┴────┬─────┴──────────────────────┘
                      ▼
             🧭 target project
                      │
                      ▼
          project-specific authority wins
```

---

## 🎭 AI roles — separation of duties

When an AI receives a task, it should either use the role explicitly assigned by the user or consult the [Role Router](roles/README.md).

```text
🔍 AUDITOR      → What is true now?
🧠 ANALYST      → What does the evidence mean?
🛠️ IMPLEMENTER  → How do I apply the authorized bounded change?
🧨 RED TEAM     → How can this fail or be bypassed?
🧪 VERIFIER     → Is the claimed result actually proven?
🧭 COORDINATOR  → Who should do what, in what order?
```

The important separation is:

```text
finding a problem
      !=
proving its root cause
      !=
implementing the fix
      !=
independently attacking/verifying the fix
```

For material work, the same model may perform author self-checks, but those are not independent verification. A different actor/model/provider—or at least a fresh isolated context that re-fetches evidence—is preferable for Red Team and Verifier roles.

➡️ [`roles/README.md`](roles/README.md)

---

## 🌳 Repository tree

```text
🧩 velantrim-ai-skills/
├── 📖 README.md                    # human-first English entry
├── 📖 README.ru.md                 # human-first Russian entry
├── 🤖 AGENTS.md                    # repository-wide AI boundaries
├── 🤖 docs/
│   └── ai/
│       └── README.md               # compact AI entry + routing
├── 🎭 roles/
│   ├── README.md                   # role router
│   ├── 🔍 auditor.md
│   ├── 🧠 analyst.md
│   ├── 🛠️ implementer.md
│   ├── 🧨 red-team.md
│   ├── 🧪 verifier.md
│   └── 🧭 coordinator.md
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
- ⚙️ CI gate, false-pass and deadlock analysis;
- 🧪 supported test execution and negative-test gaps;
- 📚 GitHub ↔ Notion/documentation truth routing;
- 🔁 per-role freshness instead of one misleading global sync marker;
- 📦 dependency and reproducibility review;
- 🧯 declared limitation vs newly discovered defect;
- 🛠️ minimal remediation + Definition of Done;
- 🚦 explicit recommendation/authorization boundaries.

The skill intentionally does **not** hard-code target-project SHAs, issue numbers, experiment names, page IDs, architecture vocabulary, reviewer policy, runtime, language, or database assumptions.

---

## ⚡ Example: efficient multi-AI workflow

```text
              ┌── 🔍 code/GitHub audit ──┐
START ────────┼── 🔍 CI/governance ──────┼──► 🧠 ANALYST
              └── 🔍 docs/knowledge ──────┘         │
                                                     ▼
                                              👤 authority GO
                                                     │
                                                     ▼
                                              🛠️ IMPLEMENTER
                                                     │
                                          ┌──────────┴──────────┐
                                          ▼                     ▼
                                     🧨 RED TEAM            🧪 VERIFIER
                                          └──────────┬──────────┘
                                                     ▼
                                              🧭 reconcile
```

Read-only audit lanes may run in parallel. Implementation should begin only after evidence is reconciled and the required authority exists. Red Team and independent verification should not be silently collapsed into the authoring session when independence matters.

---

## 🔒 Operating boundaries

```text
project-specific authority > generic role/skill defaults
read-only by default
role assignment != authority
IMPLEMENTER role != write permission
writes require explicit authorization
UNKNOWN stays UNKNOWN
recommendation != authorization
AUTHOR_SELF_CHECK != INDEPENDENT_VERIFICATION
CI success != production readiness
mirror/sync metadata != runtime evidence
ordinary review != specialized independent qualification
public repository != open-source license
```

This repository is **not** part of the architecture of Native Kernel, Titan, Crystal, Mentaury, Continuum, or any other target project. Those names are possible consumers, not authority relationships.

---

## 🤖 For AI agents

Do **not** reconstruct operating rules from this README alone.

Use this reading order:

```text
1. AGENTS.md
2. docs/ai/README.md
3. roles/README.md
4. selected roles/<role>.md
5. skills/README.md              # when a reusable methodology is needed
6. selected skill/SKILL.md
7. relevant references/templates
8. target project's own authority/governance docs
```

The AI entry point contains compact structured metadata and the exact routing rule.

➡️ [`docs/ai/README.md`](docs/ai/README.md)

---

## 📚 Authority model

For **this repository**, GitHub is the technical source of truth for versioned role/skill content and history.

For **any target repository**, roles and skills must discover that project's authority hierarchy rather than imposing one from Velantrim AI Skills.

No generic role or skill can promote itself into target-project authority.

---

## 🧠 Why no `project-state.json` yet?

A separate machine-state file is useful only if this repository develops meaningful changing operational state that automation must consume.

Today it mainly contains versioned methodologies and role guidance. A JSON state file would duplicate Markdown truth and create another drift surface. The AI entry therefore uses concise structured YAML metadata inside Markdown.

If genuine machine-state appears later, add a versioned JSON schema deliberately rather than using JSON as decorative duplication.

---

## ⚖️ License

No license has been selected yet. Public visibility does not by itself grant permission to copy, modify, redistribute, or reuse the repository contents. License selection remains an owner decision.