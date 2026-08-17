# 🔐 GitHub Governance Checklist

Use this checklist after establishing the target repository's own governance rules.

## Repository / branch model

- [ ] Default branch identified.
- [ ] Active rulesets identified.
- [ ] Classic branch protection checked when accessible.
- [ ] Ruleset target refs confirmed.
- [ ] Force-push policy known.
- [ ] Deletion policy known.
- [ ] Allowed merge methods known.
- [ ] Bypass actors known or reported UNKNOWN.

## Pull-request enforcement

- [ ] Pull request required before merge?
- [ ] Required approvals count known?
- [ ] Stale approvals dismissed after push?
- [ ] Last-push approval required?
- [ ] Code-owner review required?
- [ ] Conversation/review-thread resolution required?
- [ ] Branch must be up to date?

## Required status checks

For every required check:

- [ ] Exact visible check name identified.
- [ ] Name is unique and stable.
- [ ] Check exists on every applicable PR.
- [ ] No path filter can make the required check disappear.
- [ ] No `if:` condition can silently omit it.
- [ ] Fork PR / secret behavior is safe.
- [ ] Failure blocks merge.
- [ ] Cancellation blocks merge or is explicitly handled.
- [ ] Unexpected skipped/absent dependency cannot silently pass.
- [ ] Ruleset can actually see/select the check.

## Maintainer topology

Classify:

- `SINGLE_MAINTAINER`
- `MULTI_MAINTAINER`
- `EXTERNAL_REVIEW_DEPENDENT`
- `UNKNOWN`

Before recommending approvals, test:

```text
required approval + no eligible reviewer = merge deadlock
```

Do not equate repository approval with specialized independent review, scientific reproduction, security certification, or project-specific reviewer qualification.

## Evidence language

Report separately:

- **observed green CI**;
- **enforced required checks**;
- **observed review practice**;
- **enforced review policy**.

Never use one as shorthand for the other.
