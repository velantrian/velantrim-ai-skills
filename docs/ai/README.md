# 🤖 AI Entry — Velantrim AI Skills

This is the compact machine/agent-oriented entry point for `velantrian/velantrim-ai-skills`.

Use it to orient quickly, select or confirm the current operational role, then read the relevant skill and the target project's own authority surfaces.

```yaml
repository: velantrian/velantrim-ai-skills
role: project-neutral external AI tooling
canonical_storage: GitHub
current_operating_mode: READ_ONLY_BY_DEFAULT
write_rule: EXPLICIT_SCOPE_AUTHORIZATION_REQUIRED
project_authority_rule: TARGET_PROJECT_RULES_OVERRIDE_GENERIC_SKILL_DEFAULTS
unknown_rule: INACCESSIBLE_OR_UNVERIFIED_STATE_REMAINS_UNKNOWN
recommendation_rule: RECOMMENDATION_IS_NOT_AUTHORIZATION
role_router: roles/README.md
role_rule: ROLE_DOES_NOT_GRANT_AUTHORITY_OR_WRITE_PERMISSION
independence_rule: AUTHOR_SELF_CHECK_IS_NOT_INDEPENDENT_VERIFICATION
notion_requirement: OPTIONAL
machine_state_file: NOT_REQUIRED_AT_CURRENT_REPOSITORY_SCOPE
license: NOT_SELECTED
first_skill: skills/github-notion-repository-audit/SKILL.md
```

## ⚡ Quick routing

```text
Need repository-wide boundaries?
→ AGENTS.md

Need to decide what kind of AI work this task requires?
→ roles/README.md

Need role-specific boundaries?
→ roles/<role>.md

Need available skills/methodologies?
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

## 🎭 Role selection protocol

If the user or target-project workflow explicitly assigns a role, use that role.

If no role is assigned, read `roles/README.md`, select **one primary role for the current stage**, state it briefly, and apply its boundaries.

```yaml
primary_role: <AUDITOR|ANALYST|IMPLEMENTER|RED_TEAM|VERIFIER|COORDINATOR>
why: <one sentence>
default_mode: <READ_ONLY|AUTHORIZED_WRITE>
scope: <bounded current-stage task>
forbidden: <main role boundary>
next_handoff: <role/condition if needed>
```

Do not self-promote from read-only analysis into implementation. Assigning `IMPLEMENTER` does not itself authorize a write.

For independence-sensitive work, the author of a change may perform self-checks, but those checks must not be labeled independent verification. Prefer a different actor/model/provider or a fresh isolated context that independently fetches the evidence.

## 📖 Mandatory reading order for agents

1. `AGENTS.md`
2. this file
3. `roles/README.md`
4. selected `roles/<role>.md`
5. `skills/README.md`
6. selected `SKILL.md`
7. relevant `references/*`
8. relevant `templates/*`
9. **then the target project's own** agent/governance/architecture/current-state documentation

If the task is not skill-based, steps 5–8 may be unnecessary. The target project's own rules, authority hierarchy, security boundaries and operator-reserved decisions must still be discovered live.

## 🧭 Core invariants

```text
live state > stale handoff
project authority > generic skill/role defaults
evidence > inference
UNKNOWN != false
recommendation != authorization
role assignment != authority
IMPLEMENTER role != write permission
AUTHOR_SELF_CHECK != INDEPENDENT_VERIFICATION
CI GREEN != production readiness
public repository != open-source license
mirror synchronization != runtime evidence
ordinary review != specialized independent qualification
```

## 🔒 Write boundary

This repository's roles and skills are read-only unless the user explicitly authorizes a bounded write scope.

Before any write:

1. re-check live state;
2. read target-project write rules;
3. state the exact intended change set;
4. avoid unrelated cleanup;
5. verify the changed state after mutation;
6. hand material changes to an independent Red Team/Verifier when proportionate to risk.

## 🧠 Why this is Markdown + YAML, not a separate JSON state file

The repository currently contains versioned methodologies and role guidance rather than a dynamic operational state machine. A separate JSON file would duplicate stable documentation and create another truth surface to synchronize.

If future automation genuinely needs changing machine-readable state, add a versioned JSON schema deliberately and define its authority role. Until then, this compact YAML block is an orientation aid, not a second source of truth.