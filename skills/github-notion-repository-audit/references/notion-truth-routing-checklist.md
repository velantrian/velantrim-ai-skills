# 🧭 Notion Truth-Routing Checklist

Use this only when Notion is part of the target project's operating model.

## Discover page roles

For each relevant page, determine rather than assume:

- human navigation / hub;
- current state;
- roadmap/planning;
- architecture/decision authority;
- risks;
- evidence;
- synchronization chronology;
- AI orientation/context;
- historical archive;
- other project-specific role.

Classify each page as one or more of:

`SOURCE_OF_TRUTH`, `CURRENT_PROJECTION`, `MIRROR`, `PLANNING_ONLY`, `HISTORICAL_RECORD`, `EVIDENCE_SURFACE`, `NON_AUTHORITATIVE`, `UNKNOWN`.

## Current vs historical

- [ ] Current block is clearly identifiable.
- [ ] Historical blocks are explicitly labeled.
- [ ] Superseded decisions are visibly superseded.
- [ ] Planning content does not look authorized by default.
- [ ] Old SHAs/statuses are not presented as current unless their role is intentionally frozen.

## Freshness

Do not assume one global sync identity represents every page.

For each role/page ask:

- synchronized through what identity, if any?
- was the page actually written?
- was it read back after the write?
- when was it last verified?
- is that identity a freshness marker, or a deliberately frozen subject/checkpoint?

Never set a page's freshness from another page's update unless the project explicitly defines them as one atomic projection.

## Retrieval-noise test

Sample isolated fragments from long pages.

Can a reader seeing only the fragment determine whether it is:

- `CURRENT`;
- `HISTORICAL`;
- `SUPERSEDED`;
- `PROPOSED`;
- `PLANNING_ONLY`;
- `NOT_AUTHORIZED`?

If no, record a retrieval/truth-routing risk.

## Duplication

Do not automatically delete duplicated chronology.

First determine whether repetition is intentional provenance or accidental role overlap.

A common low-noise pattern is:

```text
one full chronology / sync log / archive
+
short role-specific current projections
+
links/pointers to history
```

Use only if consistent with the target project's authority model.

## Synchronization claims

A synchronization claim should ideally distinguish:

- target role/page;
- source authority identity;
- write completion;
- read-back status;
- verification time;
- semantic change vs docs-only/no-state-change.

`Notion synchronized` is never runtime evidence by itself.
