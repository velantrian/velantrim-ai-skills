# 🔍 Repository Audit Report

**Repository:** `{{owner/repo}}`  
**Audit date:** `{{timestamp}}`  
**Audited HEAD:** `{{sha}}`  
**Mode:** `READ_ONLY` / `AUTHORIZED_CHANGE_REVIEW`

## 1. Executive summary

{{Concise description of technical state, strongest confirmed risks, important declared boundaries, and whether the project is reproducible/operational under its own stated goals.}}

## 2. Live baseline

| Surface | Live state | Evidence | Confidence |
|---|---|---|---|
| Default branch |  |  |  |
| HEAD |  |  |  |
| Commit verification |  |  |  |
| Open PRs |  |  |  |
| Open blockers/issues |  |  |  |
| CI |  |  |  |
| Rulesets/protection |  |  |  |
| External mirrors |  |  |  |

### Delta from previous audit/handoff

{{Only if applicable.}}

## 3. Authority map

| Surface | Role | Current/historical | Authority scope | Notes |
|---|---|---|---|---|
|  |  |  |  |  |

## 4. Confirmed findings

Use `finding.md` for each finding.

### Finding summary

| ID | Severity | Class | Confidence | Priority | Authorization | Short result |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

## 5. Previous findings verification

| Prior finding | Result | Evidence |
|---|---|---|
|  | CONFIRMED / PARTIALLY_CONFIRMED / SUPERSEDED / NOT_REPRODUCED / FALSE_POSITIVE |  |

## 6. Tests actually performed

| Test | Exact command/source | Environment | Result | Locally reproduced? |
|---|---|---|---|---|
|  |  |  |  |  |

Clearly distinguish local reproduction from CI observation.

## 7. Missing / negative-test matrix

| Risk/finding | Existing protection | Missing test | Recommended negative test | Risk if absent |
|---|---|---|---|---|
|  |  |  |  |  |

## 8. GitHub governance assessment

Include:

- maintainer topology;
- PR enforcement;
- approval policy;
- required checks;
- thread resolution;
- force push/deletion;
- bypass actors;
- actual vs observed enforcement;
- merge deadlock risk.

## 9. CI architecture assessment

Include workflow inventory and exact required-check safety analysis.

| Workflow/job | Trigger | Conditional/path-filtered | Mandatory? | Failure semantics | Notes |
|---|---|---|---|---|---|
|  |  |  |  |  |  |

## 10. Code / architecture assessment

Cover only evidence-backed areas relevant to the audit:

- architecture/implementation consistency;
- hidden coupling;
- duplicated/profile logic;
- serialization/identity;
- transaction/error semantics;
- dynamic loading;
- version/migration boundaries;
- dead-code candidates with appropriate caution.

## 11. Notion / documentation truth routing

If connected:

| Role/page | Intended role | Freshness evidence | Read-back | Drift/noise risk |
|---|---|---|---|---|
|  |  |  |  |  |

Include isolated-fragment retrieval-noise observations where relevant.

If Notion is unavailable, state `NOT_ASSESSED` or `UNKNOWN` rather than inferring.

## 12. Reproducibility / supply chain

| Dependency/tool | Reference form | Classification | Can bytes drift? | Recommendation |
|---|---|---|---|---|
|  |  |  |  |  |

## 13. Security / production boundary

Separate:

### Declared limitations

{{Known and already documented.}}

### Newly discovered security/correctness findings

{{Only evidence-backed new findings.}}

## 14. Prioritized remediation

Use `remediation-plan.md`.

For every proposed action, state whether it is:

- recommendation only;
- explicitly authorized;
- blocked pending owner/operator decision;
- blocked pending external evidence;
- not applicable.

Do not infer authorization from severity, priority, or GO/NO-GO wording.

## 15. External / operator blockers

| Blocker | Type | What cannot proceed | What evidence/decision is required |
|---|---|---|---|
|  |  |  |  |

## 16. GO / NO-GO matrix

| Proposed action | Decision | Authorization status | Evidence / condition |
|---|---|---|---|
| Bounded repository hygiene |  |  |  |
| CI/governance enforcement |  |  |  |
| Refactoring |  |  |  |
| Architecture changes |  |  |  |
| Runtime/experiment execution |  |  |  |
| License/contribution change |  |  |  |

Use project-specific action names where appropriate. A `GO` is scope-limited and is not blanket authorization unless explicit write authority is separately established.

## 17. Final boundaries

Explicitly restate applicable distinctions, such as:

```text
CI GREEN != production readiness
mirror synchronization != runtime evidence
recommendation != authorization
ordinary review != specialized independent qualification
UNKNOWN != false
```

## 18. Audit limitations

Describe inaccessible APIs, missing environments, skipped integration tests, non-performed penetration/security work, or other limitations that materially affect confidence.
