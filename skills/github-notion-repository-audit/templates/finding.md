# Finding Template

## {{ID}} — {{Title}}

**Classification:** {{CONFIRMED_DEFECT | CONFIRMED_RISK | SPECIFICATION_GAP | ...}}  
**Severity:** {{Critical | High | Medium | Low | Informational}}  
**Confidence:** {{High | Medium | Low}}

### Evidence

- {{live configuration/code/test evidence}}
- {{reproduction evidence if available}}
- {{authority surface / source}}

### What is actually wrong

{{Describe the demonstrated mismatch, control gap, or failure mode. Avoid speculation.}}

### Failure mode

```text
{{precondition}}
→ {{mechanism}}
→ {{bad state/outcome}}
```

### Impact

{{Bounded consequence under the target project's real authority model.}}

### Minimal remediation

{{Smallest existing-mechanism change that closes the demonstrated risk.}}

### Definition of Done

- [ ] {{observable completion criterion}}
- [ ] {{negative/fail-closed criterion}}
- [ ] {{read-back or post-change verification}}

### Do not do

- {{scope expansion to avoid}}
- {{authority boundary not to cross}}

### Priority

{{P0_SAFE_NOW | P1_BOUNDED_NEXT | P2_FUTURE_MAINTENANCE | BLOCKED_* | NO_ACTION}}

### Notes / uncertainty

{{Anything not independently reproduced or still UNKNOWN.}}
