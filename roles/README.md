# 🎭 AI Role Router

Reusable, project-neutral role guidance for AI agents working on software and research projects.

Roles are **operational hats**, not authority. A role does not grant permission, reviewer qualification, scientific independence, merge authority, runtime authority, or owner/operator powers.

## ⚡ Fast selection

```text
What does the current task primarily require?

🔍 Establish facts / inspect live state / find risks
→ AUDITOR

🧠 Reconcile evidence / find root cause / compare options
→ ANALYST

🛠️ Apply an explicitly authorized bounded change
→ IMPLEMENTER

🧨 Try to break a proposed or implemented change
→ RED TEAM

🧪 Independently verify a claimed result
→ VERIFIER

🧭 Coordinate several roles, handoffs and authority boundaries
→ COORDINATOR
```

## 🧭 Role-routing decision tree

```text
                         📨 TASK
                            │
                            ▼
                  Is a role explicitly assigned?
                    ┌───────┴────────┐
                   YES              NO
                    │                │
                    ▼                ▼
              use that role      identify primary need
                                     │
          ┌──────────┬──────────┬────┼────┬──────────┐
          ▼          ▼          ▼         ▼          ▼
       🔍 facts   🧠 reason   🛠️ change  🧨 attack  🧪 verify
      AUDITOR     ANALYST    IMPLEMENTER RED TEAM   VERIFIER
                                     │
                                     └──── if several lanes
                                              ▼
                                         🧭 COORDINATOR
```

## Core routing rules

1. **Explicit assignment wins.** If the user or target-project workflow assigns a role, do not self-promote into another role.
2. **Choose one primary role for the current stage.** A multi-stage task may require handoffs, but independence-critical roles must not be silently collapsed.
3. **Role does not equal authorization.** `IMPLEMENTER` still needs explicit write authorization; `AUDITOR`, `ANALYST`, `RED TEAM`, and `VERIFIER` remain read-only unless separately authorized.
4. **Target-project governance wins.** Read the target project's own agent/governance/architecture/security rules before acting.
5. **Unknown stays UNKNOWN.** A role never grants permission to infer inaccessible state.
6. **Evidence must cross handoffs.** Transfer concrete artifacts, SHAs, commands, findings, unresolved questions, and authority boundaries—not only prose conclusions.

## Independence rule

For material changes, do not let authorship masquerade as independent verification.

```text
who found the issue
    may differ from
who decides the root cause
    may differ from
who implements the patch
    SHOULD differ from
who independently attacks/verifies the result
```

A different model/provider is useful when available because it reduces correlated error. If the same model/provider is reused for an independence-sensitive role, prefer a **fresh isolated context** and do not treat the previous session's reasoning as evidence.

The same actor that implemented a change may run self-checks, but those checks must be labeled `AUTHOR_SELF_CHECK`, not `INDEPENDENT_VERIFICATION`.

## Role matrix

| Role | Primary question | Default mode | Typical output | Must not silently do |
|---|---|---|---|---|
| 🔍 [Auditor](auditor.md) | What is true now? | Read-only | Evidence ledger, findings, unknowns | Fix findings |
| 🧠 [Analyst](analyst.md) | What does the evidence mean? | Read-only | Root cause, options, minimal plan | Invent facts or authority |
| 🛠️ [Implementer](implementer.md) | How do I apply the authorized change? | Write only when authorized | Bounded patch/PR + self-checks | Expand scope or self-approve |
| 🧨 [Red Team](red-team.md) | How can this fail? | Read-only / safe tests | Attack matrix, counterexamples | Quietly repair what it breaks |
| 🧪 [Verifier](verifier.md) | Is the claimed result actually proven? | Read-only / safe tests | Exact-head verification, GO/NO-GO | Trust author claims by default |
| 🧭 [Coordinator](coordinator.md) | Who should do what, in what order? | Read-only by default | Role plan, handoffs, conflict map | Override owner/operator decisions |

## Before starting a task

If no role was explicitly assigned, state briefly:

```yaml
primary_role: <AUDITOR|ANALYST|IMPLEMENTER|RED_TEAM|VERIFIER|COORDINATOR>
why: <one sentence>
default_mode: <READ_ONLY|AUTHORIZED_WRITE>
scope: <bounded task>
forbidden: <main role boundary>
next_handoff: <role/condition, if any>
```

Then read the relevant role file and the target project's own authority documentation.

## Common workflows

### Small bounded change

```text
🔍/🧠 inspect & plan
      ↓
🛠️ implement
      ↓
🧪 independent verify
```

### Medium architecture or governance change

```text
🔍 AUDITOR
    ↓
🧠 ANALYST
    ↓
🛠️ IMPLEMENTER
    ↓
🧨 RED TEAM ─┐
             ├─► 🧪 VERIFIER
🧪 regression┘
```

### Critical research / authority-sensitive change

```text
🔍 AUDITOR A ─┐
              ├─► 🧠 ANALYST ─► 👤 OWNER/OPERATOR GO
🔍 AUDITOR B ─┘                         │
                                       ▼
                                  🛠️ IMPLEMENTER
                                       │
                           ┌───────────┴───────────┐
                           ▼                       ▼
                      🧨 RED TEAM              🧪 VERIFIER
                           └───────────┬───────────┘
                                       ▼
                                  🧭 RECONCILE
                                       ▼
                                   👤 FINAL GO
```

These are reusable patterns, not mandatory governance. Use them only when proportionate to the target project's risk and authority model.

## Handoff minimum

A role handoff should preserve:

- target repository / surface;
- exact live baseline or SHA when relevant;
- assigned role and completed scope;
- evidence collected;
- tests actually run vs merely observed;
- findings and confidence;
- unresolved `UNKNOWN`s;
- explicit authorization state;
- decisions reserved for owner/operator/external reviewer;
- exact next role and bounded task.

Do not pass a recommendation as though it were an authorization.