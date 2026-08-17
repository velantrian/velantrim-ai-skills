# 🧰 Skills

This directory contains reusable, project-neutral AI operational skills.

## Available skills

### 🔍 `github-notion-repository-audit/`

A repeatable, evidence-based methodology for auditing GitHub repositories and connected Notion/documentation surfaces without inheriting project-specific assumptions.

It covers:

- live-first repository baselining;
- authority discovery;
- GitHub rulesets and merge governance;
- CI / required-check deadlock safety;
- source-code and architecture review;
- supported test execution and negative-test thinking;
- coverage interpretation;
- Notion truth routing and per-role freshness;
- reproducibility / supply-chain review;
- security and production-boundary separation;
- remediation prioritization and GO / NO-GO reporting.

Package:

```text
skills/
└── github-notion-repository-audit/
    ├── SKILL.md
    ├── references/
    │   ├── github-governance-checklist.md
    │   ├── ci-gate-checklist.md
    │   ├── notion-truth-routing-checklist.md
    │   └── audit-severity-guidance.md
    └── templates/
        ├── audit-report.md
        ├── finding.md
        └── remediation-plan.md
```

## Requirements for generic skills

A generic skill must:

- discover target-project authority instead of assuming it;
- operate read-only by default;
- distinguish facts, inferences, unknowns, risks and declared limitations;
- respect project-specific governance and operator-reserved decisions;
- avoid hard-coded project identifiers or frozen state from one repository;
- avoid turning recommendations into authorization;
- explicitly report inaccessible state as `UNKNOWN`;
- consider single-maintainer and multi-maintainer governance separately when relevant;
- test required-check deadlock risk before recommending merge enforcement;
- keep external tooling separate from the architecture of inspected projects.

Project-specific skills, if ever added, must be clearly named and scoped so they cannot be mistaken for neutral tooling.
