# ⚙️ CI Gate Checklist

Use this before recommending any aggregate or required merge gate.

## Workflow inventory

For each relevant workflow record:

- trigger events;
- branch filters;
- path filters;
- job IDs;
- visible check names;
- matrix expansion;
- `needs` dependencies;
- `if:` expressions;
- `continue-on-error`;
- permissions;
- credentials requirements;
- services/containers;
- concurrency/cancellation;
- artifacts;
- approximate cost/runtime where relevant.

## Required-context outcome taxonomy

Classify the enforcement state precisely rather than calling every non-green state a deadlock.

| State | Meaning |
|---|---|
| `PASS` | The intended required context exists for the current applicable head and satisfies policy. |
| `RECOVERABLE_BLOCK` | Merge is blocked now, but a policy-compliant rerun/fix/review path can still produce a valid context. |
| `DEADLOCK` | Policy requires a context, but no permitted path can create or complete it for the applicable head/change class. |
| `FALSE_PASS` | The rule is satisfied by the wrong or non-equivalent context, often because names collide or scope is ambiguous. |
| `UNKNOWN` | Available evidence cannot establish whether the context is required, emitted, visible, or runnable. |

Core distinction:

```text
required context + no policy-compliant producer/path = DEADLOCK
required name + wrong/non-equivalent passing producer = FALSE_PASS
```

Do not collapse these into one failure class.

## Mandatory-state semantics

For every mandatory dependency, answer explicitly:

| Dependency state | Aggregate gate behavior |
|---|---|
| success | pass candidate |
| failure | must fail |
| cancelled | must fail or explicitly block |
| skipped by intended policy | explicitly modeled |
| skipped unexpectedly | must not silently pass |
| job absent | must not silently pass |
| timed out | must fail/block |

Do not assume default GitHub semantics are sufficient without verifying the actual workflow graph.

## Fork and restricted-context checks

A job that cannot run for some applicable pull-request sources must not be made universally required unless the repository has an explicit safe policy for that path.

Classify first:

```text
job runs safely for all applicable PRs
→ eligible for required-check evaluation

job is intentionally unavailable for some PR sources
→ model that path explicitly

job is required but cannot run for an applicable PR
→ merge-deadlock risk

availability cannot be verified
→ UNKNOWN
```

Do not weaken repository security boundaries merely to make a required check runnable.

## Merge queue / merge-group compatibility

Only apply this check when the repository actually uses a merge queue or queue-generated candidate refs/events.

- [ ] Required workflows run for the queue/merge-group event used by the repository.
- [ ] The required context is emitted for the queue-generated candidate head, not only for the ordinary PR head.
- [ ] A PR that is green before entering the queue cannot become permanently blocked because the queue event has no check producer.
- [ ] Queue-specific required contexts have stable, unambiguous names.

Do not impose merge-queue logic on projects that do not use a merge queue.

## Deadlock and false-pass checks

- [ ] Required check always exists on applicable PRs.
- [ ] Path filters cannot remove the final required check.
- [ ] Conditional jobs have an explicit neutral/required interpretation.
- [ ] Fork/restricted PRs can satisfy every universally required check.
- [ ] Matrix check names are not ambiguous.
- [ ] Duplicate job names across workflows cannot let a non-equivalent check satisfy the required context.
- [ ] Strict branch-up-to-date policy is compatible with the workflow trigger model.
- [ ] Concurrency cancellation cannot leave the current PR without a usable required check.
- [ ] Merge-queue heads are covered when merge queue is part of the repository model.

## Aggregate gate guidance

Prefer a stable final gate whose result is derived from explicit dependencies.

Avoid:

- scraping/parsing the Actions UI;
- relying on a job that only exists for some paths;
- treating `skipped` as success without policy;
- embedding heavy tests directly in the final aggregator when reusable jobs already exist.

When possible, structure as:

```text
unit ───────────┐
integration ────┤
governance ─────┤──► aggregate gate ─► required check
profile/backend ┘
```

The final gate should be boring, stable, and easy to reason about.
