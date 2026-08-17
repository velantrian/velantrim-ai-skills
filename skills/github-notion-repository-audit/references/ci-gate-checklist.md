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
- secrets;
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

## Deadlock checks

- [ ] Required check always exists on applicable PRs.
- [ ] Path filters cannot remove the final required check.
- [ ] Conditional jobs have an explicit neutral/required interpretation.
- [ ] Fork PRs do not depend on unavailable secrets for mandatory checks.
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
