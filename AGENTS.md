# 🤖 Agent Operating Boundaries

This repository contains project-neutral AI operational skills.

## Core rules

1. **Read-only by default.** Do not mutate this repository, an inspected repository, Notion, GitHub governance, issues, pull requests, CI settings, or external systems unless the user explicitly authorizes the write.
2. **Discover authority first.** Never assume that this repository's conventions are authoritative for a target project.
3. **Project-specific rules override generic skill defaults.** Read and follow the target repository's own `AGENTS.md`, governance, architecture, decision records, security boundaries, contribution rules, and operator-reserved decisions.
4. **No authority inheritance.** A skill inspecting Native Kernel, Titan, Crystal, Mentaury, Continuum, or another project does not become part of that project's architecture and gains no authority from it.
5. **Live state beats handoff.** Previous reports, memory, summaries, and handoffs are inputs to re-check, not absolute truth.
6. **Evidence before recommendation.** Distinguish observed facts, inferences, unknowns, declared limitations, risks, and confirmed defects.
7. **Recommendation is not authorization.** A remediation proposal must not silently become an implementation decision.
8. **Unknown stays UNKNOWN.** Permission errors, inaccessible APIs, missing connected surfaces, or unavailable environments must be reported explicitly instead of inferred.
9. **No false equivalence.** Examples: ordinary PR approval is not automatically independent scientific review; green CI is not production readiness; documentation sync is not runtime evidence; public visibility is not an open-source license.
10. **Prefer minimal remediation.** Do not invent new governance or architecture when a bounded change to existing mechanisms closes the demonstrated risk.

## Skill authoring

Reusable skills belong under `skills/<skill-name>/`.

Each skill should be project-neutral unless its name and documentation explicitly declare otherwise. Generic skills must not hard-code repository IDs, Notion page IDs, experiment names, project-specific gates, frozen SHAs, architecture terms, or operator decisions from one inspected project.

A skill may include:

- `SKILL.md` — methodology and decision rules;
- `references/` — compact checklists or supporting guidance;
- `templates/` — reusable output structures.

Avoid unnecessary framework code. Prefer inspectable Markdown procedures, explicit evidence requirements, and bounded templates.

## Writes

When a user authorizes a write, state the exact intended scope before changing external state. Keep changes small, auditable, and reversible where possible.
