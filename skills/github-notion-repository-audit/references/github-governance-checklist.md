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
- [ ] Check exists on every applicable PR/ref/head class.
- [ ] No path filter can make the required check disappear.
- [ ] No `if:` condition can silently omit it.
- [ ] Fork/restricted PR behavior is safe.
- [ ] Failure blocks merge.
- [ ] Cancellation blocks merge or is explicitly handled.
- [ ] Unexpected skipped/absent dependency cannot silently pass.
- [ ] Ruleset can actually see/select the check.

### External status providers

If a required context is emitted by an external GitHub App, service, or status provider rather than repository-local workflow code, verify separately:

- [ ] provider/app is installed or otherwise available in every applicable repository/ref/PR context;
- [ ] the exact context name is stable and unique;
- [ ] the provider actually emits the context for every policy-applicable head class;
- [ ] ruleset visibility/scope matches provider scope;
- [ ] transferred/forked/new-ref/queue contexts are assessed when they exist;
- [ ] inaccessible provider configuration is reported `UNKNOWN`, not inferred absent or safe.

A status observed on one ordinary internal PR does not prove that the provider can satisfy a universal required-check policy.

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
