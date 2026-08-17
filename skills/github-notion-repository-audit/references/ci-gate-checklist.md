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

## Deadlock checks

- [ ] Required check always exists on applicable PRs.
- [ ] Path filters cannot remove the final required check.
- [ ] Conditional jobs have an explicit neutral/required interpretation.
- [ ] Fork/restricted PRs can satisfy every universally required check.
- [ ] Matrix check names are not ambiguous.
- [ ] Duplicate job names across workflows do not collide.
- [ ] Strict branch-up-to-date policy is compatible with the workflow trigger model.
- [ ] Concurrency cancellation cannot leave the current PR without a usable required check.

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
