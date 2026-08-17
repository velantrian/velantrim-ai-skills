# 🚦 Audit Severity & Confidence Guidance

Severity should describe plausible impact under the target project's actual authority model, not emotional importance.

## Severity

### P0 / Critical
Use only when there is a demonstrated path to immediate corruption, unsafe authority transition, irreversible loss, security compromise, or equivalent project-defined catastrophic failure.

### High
A confirmed control or correctness weakness that can plausibly admit materially invalid state, evidence, release, merge, or decision without another reliable barrier.

### Medium
A real defect/risk with bounded impact, maintainability consequences, observability gaps, drift potential, or failure modes that require additional conditions.

### Low
Minor correctness/ergonomics/hygiene debt with limited impact.

### Informational
Useful observation that does not presently justify remediation.

Do not inflate a declared non-production limitation into a new High/Critical finding unless implementation violates the declared boundary.

## Finding class

Prefer one of:

- `CONFIRMED_DEFECT`
- `CONFIRMED_RISK`
- `SPECIFICATION_GAP`
- `INTEROPERABILITY_RISK`
- `MAINTAINABILITY_DEBT`
- `DECLARED_LIMITATION`
- `SUPERSEDED`
- `NOT_REPRODUCED`
- `FALSE_POSITIVE`
- `UNKNOWN`

## Confidence

### High confidence
Directly observed in live configuration/code or independently reproduced behavior.

### Medium confidence
Strong evidence plus a bounded inference, but not fully reproduced.

### Low confidence
Plausible hypothesis needing targeted verification.

### Unknown confidence
The relevant evidence surface cannot currently be accessed, reproduced, or classified well enough to assign evidentiary confidence.

Use `Unknown` for inaccessible or genuinely unobservable state. Do **not** downgrade inaccessible state to `Low`: low confidence means there is some weak evidence, while unknown confidence means the required evidence is not available.

Never present low-confidence inference or unknown state as a confirmed defect.

## Evidence hierarchy

Prefer, roughly:

1. live authoritative configuration / current code;
2. independently reproduced behavior;
3. exact current tests/CI artifacts;
4. accepted decision records / machine state;
5. current role-specific documentation;
6. historical records;
7. prior audits / handoffs;
8. inference.

The target project's own authority hierarchy may override this ordering.

## Remediation priority

Severity and implementation priority are related but not identical.

A High issue can be `BLOCKED_OPERATOR_DECISION`; a Medium issue can be an easy P0 hygiene fix if it prevents repeated drift.

Use:

- `P0_SAFE_NOW`
- `P1_BOUNDED_NEXT`
- `P2_FUTURE_MAINTENANCE`
- `BLOCKED_EXTERNAL_EVIDENCE`
- `BLOCKED_OPERATOR_DECISION`
- `NOT_AUTHORIZED`
- `NO_ACTION`

Always state why.
