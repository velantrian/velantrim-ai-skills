# 🔍 GitHub ↔ Notion Repository Audit

## Purpose

A reusable, project-neutral skill for evidence-based auditing of software and research repositories whose operational truth may span GitHub, Notion, CI, documentation, tests, governance, and other connected surfaces.

This skill is **external tooling**. It does not become part of the architecture, governance, scientific evidence, or authority model of any repository it inspects.

## Default mode

**READ-ONLY.**

Do not modify repositories, branches, pull requests, issues, rulesets, CI settings, Notion pages, releases, or external systems unless the user explicitly authorizes the exact write scope.

## ⚡ Quick start

Use this skill when the user asks for a deep repository audit, GitHub/governance/CI review, GitHub ↔ Notion/documentation consistency check, reproducibility review, or evidence-backed remediation assessment.

### Read first

```text
1. target repository live state
2. target project's AGENTS/governance/current-state docs, if present
3. this SKILL.md
4. relevant references/*
5. templates/* when producing the report
```

### Hard prohibitions in read-only mode

Do not:

- edit files or settings;
- create branches, PRs, issues, releases, or Notion pages;
- change rulesets/branch protection;
- select a license;
- convert a recommendation into authorization;
- infer inaccessible state.

### Minimum live baseline

Before findings, establish when available:

- repository/default branch/current HEAD;
- commit verification state;
- open PRs/issues/blockers;
- CI/Actions state;
- rulesets/branch protection;
- project documentation and machine state;
- connected knowledge surfaces;
- supported local test environment.

### Minimum output discipline

Every material finding should identify:

```text
evidence
→ confidence
→ failure mode
→ bounded impact
→ minimal remediation
→ Definition of Done
→ authorization status
→ explicit non-actions
```

If a surface cannot be verified, use `UNKNOWN` rather than guessing.

## Core operating principles

1. **Live-first.** Previous audits, handoffs, memories, cached summaries, and planning documents are hypotheses to re-check, not absolute truth.
2. **Discover authority before judging consistency.** Determine what the target project treats as source of truth, mirror, projection, planning surface, historical record, evidence surface, or non-authoritative orientation.
3. **Project rules override this skill.** Read the target project's own `AGENTS.md`, governance, architecture, decision records, security boundaries, contribution rules, operator-reserved decisions, and write constraints.
4. **Evidence before finding.** Distinguish observed facts, reproduced behavior, inference, unknown, declared limitation, risk, confirmed defect, and superseded history.
5. **Unknown stays UNKNOWN.** Permission failures, unavailable APIs, inaccessible Notion pages, missing credentials, unavailable databases, or missing local runtimes must never be silently inferred.
6. **Recommendation is not authorization.** A remediation proposal does not authorize implementation.
7. **No false equivalence.** Green CI is not production readiness; ordinary PR approval is not automatically independent scientific review; documentation sync is not runtime evidence; public visibility is not an open-source license; coverage is not correctness proof.
8. **Prefer minimal remediation.** Strengthen existing mechanisms before inventing new frameworks, control planes, or governance layers.
9. **Preserve historical semantics.** Evidence-bound or historical code should not be rewritten for aesthetics without golden regression protection and explicit authority.
10. **Separate current truth from chronology.** Current state must be readable without requiring a reader to reconstruct it from historical logs.

---

# 1. Audit entry protocol

Before analyzing implementation details, establish a live baseline.

Record, when available:

- repository identity and visibility;
- default branch;
- current HEAD SHA;
- commit verification/signature state;
- open pull requests;
- open issues and explicit blockers;
- current Actions/CI state;
- active rulesets / branch protection;
- releases/tags if operationally relevant;
- current documentation entry points;
- project machine-readable state if present;
- target Notion surfaces and their roles if connected;
- current runtime/test environment.

If a prior audit provides a baseline, compare it against live state and report deltas.

Do not continue from a stale handoff as though it were current.

---

# 2. Authority discovery

Build an authority map before declaring drift.

Possible roles include, but are not limited to:

- **SOURCE_OF_TRUTH** — authoritative source for a domain;
- **MACHINE_STATE** — structured current state used by automation;
- **ARCHITECTURE_AUTHORITY** — accepted architecture / decisions;
- **DECISION_RECORD** — accepted or proposed decision;
- **CURRENT_PROJECTION** — human- or AI-facing projection of current state;
- **MIRROR** — synchronized representation of another authority;
- **EVIDENCE_SURFACE** — immutable or bounded evidence/artifacts;
- **PLANNING_ONLY** — roadmap or future-work guidance;
- **HISTORICAL_RECORD** — chronology/provenance, not current authority;
- **NON_AUTHORITATIVE** — orientation, examples, commentary;
- **UNKNOWN** — role cannot be established.

Do not assume these roles exist or use these names. Derive them from the target project.

For every apparent contradiction, first ask whether the two surfaces are intended to represent the same role and time horizon.

---

# 3. GitHub repository audit

Inspect:

## Repository state

- default branch and live HEAD;
- archived/private/public state;
- branch/tag/release structure where relevant;
- repository permissions visible to the auditor;
- commit verification when material to the project's evidence model.

## Pull requests

- open/draft/stale PRs;
- mergeability;
- review state;
- unresolved review threads;
- delayed reviews/comments after merge where relevant;
- exact-head vs post-merge validation distinctions;
- whether a PR claims more authority than its evidence supports.

## Issues

- active blockers;
- architecture or governance decisions;
- explicitly operator-owned decisions;
- stale/superseded issues;
- whether issue state matches current code/docs/roadmap.

## Governance

Use `references/github-governance-checklist.md`.

Never infer enforcement from workflow success alone.

---

# 4. CI / Actions audit

Inventory all relevant workflows.

For each workflow record:

- trigger (`pull_request`, `push`, manual, schedule, etc.);
- branch filters;
- `paths` / `paths-ignore`;
- job IDs and visible check names;
- matrix dimensions;
- `needs` dependencies;
- `if:` conditions;
- `continue-on-error`;
- services/containers;
- permissions;
- secrets requirements;
- concurrency/cancellation behavior;
- artifacts;
- whether the job is critical, optional, or diagnostic.

Use `references/ci-gate-checklist.md` before recommending required checks.

### Required-check safety rule

A required check that is not guaranteed to exist on every applicable pull request can create a permanent merge deadlock.

Before recommending a check as required, prove that it:

1. has a stable, unique name;
2. runs on every applicable PR;
3. cannot disappear because of path filters or conditional job creation;
4. does not require secrets unavailable to the relevant PR source;
5. handles failure, cancellation, and skipped dependencies explicitly;
6. can be observed by the repository rules mechanism;
7. completes deterministically enough to be an enforcement gate.

If an aggregate gate is appropriate, prefer explicit dependency/result semantics over parsing UI state.

---

# 5. Governance and reviewer model

Do not automatically recommend `required approvals = 1`.

First determine whether the repository is effectively:

- **single-maintainer**;
- **multi-maintainer**;
- **external-review-dependent**;
- **unknown**.

Explicitly test the deadlock risk:

```text
required approval
+
no eligible second reviewer
=
merge deadlock
```

Separate ordinary merge safety from project-specific independence requirements.

Examples of distinct concepts that must not be conflated:

- ordinary GitHub approval;
- code-owner review;
- independent scientific review;
- external reproducibility review;
- security certification;
- compliance approval;
- project-specific reviewer qualification.

### Safe baseline for a single-maintainer repository

This is a model to evaluate, not a universal prescription.

Prefer controls that the current maintainer topology can actually satisfy:

- require PR-based change flow when useful and available;
- require stable CI/status checks only after proving they always run;
- require conversation resolution only if the workflow can satisfy it without an unavailable reviewer;
- do **not** require an external approval that no eligible actor can provide;
- treat owner self-review/acknowledgment as ordinary process evidence only when the target project explicitly accepts it;
- if genuine independence is required, report that work as blocked rather than pretending ordinary self-review satisfies it.

### Stronger baseline for a multi-maintainer repository

Use only after proving that eligible reviewers actually exist and the repository can sustain the policy:

- require peer or code-owner review where project policy supports it;
- define stale-approval and latest-push semantics explicitly;
- require relevant stable checks;
- require conversation resolution where appropriate;
- inspect bypass actors and emergency paths;
- keep scientific/security/regulatory independence separate unless the project explicitly binds those roles to GitHub review.

If needed, recommend two configurations:

- **immediate safe configuration** for current maintainer topology;
- **stronger future configuration** once eligible reviewers exist.

Neither model is automatic authorization to change repository settings.

---

# 6. Source-code and architecture audit

Inspect only after authority and baseline are understood.

Look for:

- architecture/code mismatch;
- implicit assumptions not documented in contracts;
- hidden coupling;
- circular dependencies;
- duplicated logic and drift risk;
- transaction and rollback semantics;
- error handling and fail-open/fail-closed behavior;
- serialization/canonicalization assumptions;
- identity/hash boundaries;
- concurrency assumptions;
- migration/version compatibility;
- implicit global state;
- dynamic code loading/evaluation;
- environment/runtime assumptions;
- duplicated profile/backend implementations;
- dead-code candidates.

### Duplication rule

Do not call similar implementations a defect until deciding whether the duplication represents:

- intentional profile/backend independence;
- test fixture duplication;
- historical preservation;
- generated code;
- uncontrolled drift.

Prefer parity/equivalence tests before common-code refactoring.

---

# 7. Test audit

Run only project-supported, safe test paths unless the user explicitly authorizes broader experimentation.

Record:

- exact command;
- runtime/language version;
- relevant database/service versions;
- environment assumptions;
- pass/fail/skip counts;
- duration;
- whether results were locally reproduced or only observed in CI.

Never claim independent reproduction when only CI output was inspected.

Look for:

- unit tests;
- integration tests;
- regression tests;
- negative/fail-closed tests;
- property/fuzz tests where relevant;
- equivalence/parity tests;
- migration/version tests;
- evidence/verifier tests;
- missing tests around authority transitions or governance logic.

### Negative-test reasoning patterns

Consider, when relevant:

- contradictory current-state surfaces → fail;
- immutable/frozen identifier changes unexpectedly → fail;
- artifact/content hash mismatch → fail;
- invalid provenance → fail;
- exact-type contract violation → fail;
- mandatory CI dependency fails → aggregate gate fails;
- mandatory CI dependency is cancelled → aggregate gate fails;
- mandatory CI dependency unexpectedly does not exist → gate must not silently pass;
- self-review where independence is required → fail;
- stale approval after material new push → enforcement according to selected policy.

These are patterns, not universal mandatory tests.

---

# 8. Coverage audit

Treat coverage as observability, not correctness.

Do not interpret `70% coverage` as `30% broken/dead code`.

Separate where possible:

- unit/imported-code coverage;
- integration coverage;
- subprocess/child-process coverage;
- database/profile/backend coverage;
- generated or intentionally historical code.

Default recommendation:

1. reproduce a stable baseline;
2. collect at least two stable runs if the environment is noisy;
3. block unexplained regression relative to baseline;
4. raise absolute thresholds only if the target project explicitly adopts them.

Low coverage is a triage signal, not a defect by itself.

---

# 9. Notion audit

If Notion is connected, discover the role of each relevant page rather than assuming a fixed page model.

Possible roles can include Hub, Current State, Roadmap, Architecture, Decision Ledger, Risk Ledger, Evidence Ledger, Sync Log, AI Context, or Historical Archive.

For each relevant page determine:

- intended role;
- current vs historical content;
- last verified update if available;
- relationship to GitHub authority;
- whether it is a mirror, projection, planning surface, or independent decision surface;
- duplicated chronology;
- stale/superseded text;
- ambiguous status labels;
- read-back evidence if synchronization is claimed.

Use `references/notion-truth-routing-checklist.md`.

### Per-role freshness

Do not assume one global Notion synchronization SHA is sufficient.

Different pages may legitimately have different freshness because their roles differ.

Prefer a role-specific representation conceptually:

```yaml
role:
  synchronized_through: <project-defined identity>
  read_back: true|false|unknown
  verified_at: <timestamp if available>
```

Do not claim a page is synchronized through a commit merely because another Notion page is.

A frozen experiment/source/checkpoint identity must not be confused with the freshness of a mirror or projection.

### Retrieval-noise test

Sample isolated fragments from long pages and ask whether a reader seeing that fragment alone could distinguish:

- CURRENT;
- HISTORICAL;
- SUPERSEDED;
- PROPOSED;
- PLANNING_ONLY;
- NOT_AUTHORIZED.

If not, classify it as a truth-routing/retrieval risk.

Do not delete provenance automatically. Prefer one full chronology surface plus concise current projections elsewhere when that matches the project's role model.

---

# 10. Security / production boundary

Separate **declared limitations** from **newly discovered defects**.

Do not turn every item in `SECURITY.md` into a new audit finding.

Explicitly preserve these distinctions:

```text
CI GREEN != production readiness
public repository != open-source license
Notion synchronization != runtime evidence
future-work document != authorization
test coverage != correctness proof
ordinary review != specialized independent qualification
```

If the project declares itself research-only or non-production, assess whether implementation and documentation remain consistent with that boundary.

---

# 11. Dependency and supply-chain audit

Inventory, when relevant:

- GitHub Actions references;
- container images/tags/digests;
- language/package dependencies;
- lockfiles and hashes;
- downloaded binaries/tools;
- source tarballs/build sources;
- registries/mirrors;
- artifact signing/verification.

Classify dependencies as:

- **IMMUTABLE_IDENTITY**;
- **PINNED_VERSION**;
- **VERSION_RANGE**;
- **MAJOR_TAG**;
- **FLOATING_TAG**;
- **UNVERIFIED_DOWNLOAD**;
- **UNKNOWN**.

Ask whether the same repository commit can resolve to different external bytes in the future.

Where evidence reproducibility matters, consider separating:

- **EVIDENCE LANE** — immutable/pinned dependencies;
- **COMPATIBILITY LANE** — moving supported versions.

Do not claim an active vulnerability without actual evidence.

If a security/dependency setting cannot be read because of permissions or API errors, report `UNKNOWN`.

---

# 12. License and contribution state

Check whether a license exists and whether contribution terms are explicit.

If no license exists, report the practical effect on reuse/contribution/distribution, but do not choose MIT, Apache, GPL, or another license without owner authorization.

Public visibility alone does not grant open-source permissions.

---

# 13. Refactoring discipline

Do not recommend broad refactoring merely because code is old, duplicated, dynamic, or stylistically awkward.

For historical/evidence-bound code:

1. identify the authority/evidence role;
2. create or identify golden regression tests;
3. freeze expected observable behavior;
4. define explicit interfaces;
5. refactor only when the risk/reward is justified.

Avoid blanket auto-fix tools on dynamic, historical, generated, or evidence-sensitive code unless the project explicitly supports them.

A useful intermediate policy is often:

```text
preserve old frozen mechanism
+
stop adding new instances of the risky pattern
+
refactor later at a bounded maintenance boundary
```

---

# 14. Finding classification

Use `references/audit-severity-guidance.md`.

Every finding should include:

- ID;
- title;
- classification/severity;
- evidence;
- confidence;
- affected authority surface(s);
- failure mode;
- impact;
- minimal remediation;
- Definition of Done;
- authorization status / owner-decision dependency;
- explicit non-actions / boundaries.

Recommended status vocabulary:

- `CONFIRMED_DEFECT`;
- `CONFIRMED_RISK`;
- `SPECIFICATION_GAP`;
- `MAINTAINABILITY_DEBT`;
- `DECLARED_LIMITATION`;
- `SUPERSEDED`;
- `NOT_REPRODUCED`;
- `FALSE_POSITIVE`;
- `UNKNOWN`.

---

# 15. Remediation priority

Prioritize by demonstrated risk, not by how interesting a redesign would be.

Suggested categories:

- **P0 — immediate demonstrated control/correctness risk**;
- **P1 — important bounded improvement**;
- **P2 — maintainability/future hardening**;
- **BLOCKED_EXTERNAL_EVIDENCE**;
- **BLOCKED_OPERATOR_DECISION**;
- **NOT_AUTHORIZED**;
- **NO_ACTION**.

When possible, use the sequence:

```text
evidence
→ reproduced finding
→ missing protection/test
→ minimal remediation
→ Definition of Done
→ authority boundary
```

---

# 16. Required final report

Use `templates/audit-report.md` as the default report structure.

At minimum include:

1. Executive summary;
2. Live baseline;
3. Authority map;
4. Confirmed findings;
5. Tests actually performed;
6. Missing/negative-test matrix;
7. GitHub governance assessment;
8. CI architecture assessment;
9. Code/architecture assessment;
10. Notion truth-routing assessment when connected;
11. Reproducibility/supply-chain assessment;
12. Security/production boundary;
13. Prioritized remediation plan;
14. Operator/external blockers;
15. Final GO / NO-GO matrix for proposed work.

If a previous audit is being reviewed, classify each prior finding as:

- `CONFIRMED`;
- `PARTIALLY_CONFIRMED`;
- `SUPERSEDED`;
- `NOT_REPRODUCED`;
- `FALSE_POSITIVE`.

---

# 17. Write mode

This skill does not authorize writes.

If the user explicitly asks to implement remediation:

1. re-read live state;
2. re-read target project write/governance rules;
3. state the exact bounded change set;
4. avoid unrelated cleanup;
5. verify exact-head results;
6. verify post-merge state when a merge occurs;
7. synchronize external mirrors only when their role requires it;
8. do not convert a recommendation into broader architecture or runtime authority.

---

# 18. Neutrality self-check

Before using or publishing a generic revision of this skill, verify that it does **not** hard-code:

- repository IDs or URLs;
- project names;
- Notion page IDs;
- specific experiment/gate names;
- frozen SHAs;
- one project's architecture vocabulary;
- one project's operator decisions;
- one maintainer topology;
- one CI provider or programming language unless explicitly scoped.

If such content is necessary, move it into a project-specific overlay rather than the neutral core.
