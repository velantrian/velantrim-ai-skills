# Remediation Plan Template

## Baseline

- Repository: `{{owner/repo}}`
- Audited HEAD: `{{sha}}`
- Date/time: `{{timestamp}}`
- Mode: `READ_ONLY_AUDIT` / `AUTHORIZED_REMEDIATION`

## Priority map

| Priority | Work | Finding(s) | Why now | Blocker | Definition of Done |
|---|---|---|---|---|---|
| P0 |  |  |  |  |  |
| P1 |  |  |  |  |  |
| P2 |  |  |  |  |  |

## Ordering

```text
{{control / truth / test / implementation ordering}}
```

Explain dependencies between remediation steps. Do not place a later enforcement step before the mechanism it depends on is proven stable.

## Safe-now work

### {{Work item}}

- Scope:
- Existing mechanism to strengthen:
- Tests/negative tests required:
- Exact authority boundary:
- Rollback/reversibility:
- Done when:

## Blocked work

### {{Work item}}

**Blocked by:** `OPERATOR_DECISION` / `EXTERNAL_EVIDENCE` / `MISSING_ACCESS` / `NOT_AUTHORIZED`

Do not substitute internal machinery for the missing blocker.

## Verification after change

For each remediation distinguish:

- exact-head verification;
- merge-policy behavior verification;
- post-merge verification;
- external mirror/read-back verification if applicable.

## Explicit non-goals

- {{not production certification unless scoped}}
- {{not architecture redesign unless authorized}}
- {{not historical rewrite}}
- {{not unrelated cleanup}}
