# 🧰 Skills

This directory contains reusable, project-neutral AI operational skills.

## Planned first skill

`github-notion-repository-audit/`

Purpose: a repeatable, evidence-based methodology for auditing repositories and their connected documentation/knowledge surfaces without inheriting project-specific assumptions.

Expected package shape:

```text
skills/
└── github-notion-repository-audit/
    ├── SKILL.md
    ├── references/
    └── templates/
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
- consider single-maintainer and multi-maintainer governance separately when relevant.

Project-specific skills, if ever added, must be clearly named and scoped so they cannot be mistaken for neutral tooling.
