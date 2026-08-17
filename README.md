# 🧩 Velantrim AI Skills

Reusable, project-neutral AI operational skills for repository auditing, CI and governance review, GitHub ↔ Notion truth routing, reproducibility, evidence validation, documentation quality, risk analysis, and engineering workflows.

## 🎯 Purpose

This repository is a neutral tooling layer. Skills stored here may inspect or assist other projects, but they do **not** become part of those projects' architecture and do **not** inherit authority from them.

The repository is intended to support Velantrim projects and other software or research repositories where repeatable, evidence-based AI workflows are useful.

## 🧭 Boundaries

This repository is **not** part of the architecture of:

- Velantrim Native Kernel;
- Velantrim Titan;
- Velantrim Exo-Cortex Crystal;
- Mentaury Soul;
- Mentaury Kernel;
- Velantrim Continuum;
- or any other repository inspected by a skill.

A skill may read a target project's source, documentation, tests, CI, governance and connected knowledge surfaces when authorized. The target project's own rules remain authoritative.

## 🔒 Default operating mode

```text
project-specific authority > generic skill defaults
read-only by default
writes require explicit authorization
unknown state stays UNKNOWN
recommendation ≠ authorization
CI success ≠ production readiness
sync metadata ≠ runtime evidence
```

Skills must not silently change repositories, external systems, governance settings, issues, pull requests, or documentation merely because a remediation appears obvious.

## 🧰 Repository structure

```text
velantrim-ai-skills/
├── README.md
├── README.ru.md
├── AGENTS.md
└── skills/
    ├── README.md
    └── github-notion-repository-audit/
        ├── SKILL.md
        ├── references/
        └── templates/
```

## 🔍 First reusable skill

[`skills/github-notion-repository-audit/`](skills/github-notion-repository-audit/SKILL.md) is the first neutral skill in this repository.

It provides an evidence-based audit method for GitHub repositories and connected Notion/documentation surfaces, including live-first baselining, authority discovery, merge-governance review, CI gate/deadlock analysis, tests, truth routing, reproducibility, supply-chain review, and bounded remediation planning.

The skill is intentionally project-neutral. It does not contain target-project SHAs, experiment names, page IDs, operator decisions, or one project's architecture vocabulary.

## 📚 Authority model

For this repository itself, GitHub is the technical source of truth for versioned skill content and history.

For any repository being inspected, the skill must discover that project's authority hierarchy rather than imposing one from Velantrim AI Skills.

## ⚖️ License

No license has been selected yet. Public visibility does not by itself grant permission to copy, modify, redistribute, or reuse the repository contents. License selection remains an owner decision.
