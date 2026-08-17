# 🤖 AI Entry — Velantrim AI Skills

This is the compact machine/agent-oriented entry point for `velantrian/velantrim-ai-skills`.

Use it to orient quickly, then read the selected skill and the target project's own authority surfaces.

```yaml
repository: velantrian/velantrim-ai-skills
role: project-neutral external AI tooling
canonical_storage: GitHub
current_operating_mode: READ_ONLY_BY_DEFAULT
write_rule: EXPLICIT_SCOPE_AUTHORIZATION_REQUIRED
project_authority_rule: TARGET_PROJECT_RULES_OVERRIDE_GENERIC_SKILL_DEFAULTS
unknown_rule: INACCESSIBLE_OR_UNVERIFIED_STATE_REMAINS_UNKNOWN
recommendation_rule: RECOMMENDATION_IS_NOT_AUTHORIZATION
notion_requirement: OPTIONAL
machine_state_file: NOT_REQUIRED_AT_CURRENT_REPOSITORY_SCOPE
license: NOT_SELECTED
first_skill: skills/github-notion-repository-audit/SKILL.md
```

## ⚡ Quick routing

```text
Need repository-wide boundaries?
→ AGENTS.md

Need available skills?
→ skills/README.md

Need deep GitHub + documentation/Notion audit?
→ skills/github-notion-repository-audit/SKILL.md

Need governance details?
→ selected skill/references/github-governance-checklist.md

Need CI gate/deadlock checks?
→ selected skill/references/ci-gate-checklist.md

Need Notion/documentation truth routing?
→ selected skill/references/notion-truth-routing-checklist.md

Need finding severity/confidence rules?
→ selected skill/references/audit-severity-guidance.md

Need output format?
→ selected skill/templates/
```

## 📖 Mandatory reading order for agents

1. `AGENTS.md`
2. this file
3. `skills/README.md`
4. the selected `SKILL.md`
5. relevant `references/*`
6. relevant `templates/*`
7. **then the target project's own** agent/governance/architecture/current-state documentation

The target project's own rules, authority hierarchy, security boundaries and operator-reserved decisions are not inherited from this repository and must be discovered live.

## 🧭 Core invariants

```text
live state > stale handoff
project authority > generic skill defaults
evidence > inference
UNKNOWN != false
recommendation != authorization
CI GREEN != production readiness
public repository != open-source license
mirror synchronization != runtime evidence
ordinary review != specialized independent qualification
```

## 🔒 Write boundary

This repository's skills are read-only unless the user explicitly authorizes a bounded write scope.

Before any write:

1. re-check live state;
2. read target-project write rules;
3. state the exact intended change set;
4. avoid unrelated cleanup;
5. verify the changed state after mutation.

## 🧠 Why this is Markdown + YAML, not a separate JSON state file

The repository currently contains versioned methodologies rather than a dynamic operational state machine. A separate JSON file would duplicate stable documentation and create another truth surface to synchronize.

If future automation genuinely needs changing machine-readable state, add a versioned JSON schema deliberately and define its authority role. Until then, this compact YAML block is an orientation aid, not a second source of truth.
