# ARCHITECTURE_BRIEF.md

## 1. Purpose

This document defines the approved technical direction for the multi-jurisdiction legal workbench before repository-backed implementation planning.

The project must support multiple legal jurisdictions without cloning the whole application per country and without weakening source authority, privacy, currentness, or provenance protections.

This brief is not implementation fact and is not an executable plan. Codex must verify actual repository and reference-project facts before creating `PLAN.md`.

## 2. Confirmed Product Direction

- Canonical project: `jintonic1010/multi-jurisdiction-legal-workbench`.
- Initial jurisdictions: South Korea (`KR`), Philippines (`PH`), Vietnam (`VN`).
- Existing Korean project remains independent and read-only for this project.
- Reuse from the Korean workbench is selective and source-backed, never automatic synchronization.
- Final legal support must be bound to verified official/primary legal sources for the applicable jurisdiction.
- Candidate catalogs, indexes, translations, aggregators, and model memory remain advisory unless a specific official source record is verified as authority.
- Large legal corpora and case/runtime data remain outside the Git code repository by default.
- Future jurisdictions should be addable through stable extension seams without rebuilding the common core.

## 3. Non-Goals

The first project phase does not aim to:

- support every country at once;
- create a separate full application for each country;
- bulk-download every available foreign judgment before source/storage/rights rules are settled;
- treat foreign-law aggregators or translations as a substitute for issuing-jurisdiction authority;
- provide autonomous filing, court submission, external publication, or legal representation;
- add a direct OpenAI, local LLM, or other provider runtime merely because the product is AI-assisted;
- migrate or mutate the existing Korean workbench;
- publish foreign-law corpora to GitHub without an explicit rights and publication decision;
- prebuild unused microservices, vector databases, distributed queues, or cloud infrastructure.

## 4. Target Architecture Envelope

The useful-scale product is one source-backed legal-workbench platform with explicit jurisdiction boundaries.

Expected end-to-end capability:

```text
user/case intake
    -> jurisdiction scope
    -> jurisdiction-specific candidate discovery
    -> official-source acquisition / local source corpus
    -> canonical source identity + currentness
    -> case source selection + source manifest
    -> facts / evidence / claims
    -> source-backed legal reasoning
    -> report / strategy / legal-document projections
    -> validation / history / package boundaries
```

The common core should own semantics that are genuinely jurisdiction-neutral, such as:

- stable case and artifact identity;
- supplied-fact/certainty/provenance separation;
- source manifest integrity;
- evidence/claim relationships;
- stale/currentness propagation interfaces;
- reasoning/report dependency integrity;
- privacy and non-echo controls;
- history and validation boundaries;
- deterministic projections and package integrity where portable.

Jurisdiction modules should own or configure semantics that differ materially, such as:

- official source providers and acquisition methods;
- legal source categories and hierarchy;
- official document identifiers;
- promulgation/effectivity/repeal/amendment/currentness rules;
- language and official-translation status;
- court/precedent/jurisprudence categories and authority levels;
- local citation formats;
- candidate discovery metadata;
- jurisdiction-specific validation that cannot safely be generalized.

The first implementation must not assume that Korean `law`, `administrative_rule`, and `precedent` categories can represent Philippine or Vietnamese legal systems without loss.

## 5. Delivery Slicing Principle

Start from the architecture envelope, then implement the smallest coherent end-to-end slice.

The preferred sequence to evaluate in `PLAN.md` is:

1. verify local/project/reference boundaries;
2. perform read-only remake analysis of the Korean workbench and create `REMAKE.md`;
3. establish a minimal common jurisdiction/source identity contract;
4. selectively port the smallest proven common source-manifest/core behavior;
5. prove a `KR` path using the new common contract without mutating the reference project;
6. add one official `PH` source path and one official `VN` source path;
7. validate adapter → persisted source → manifest → consumer flow;
8. prove cross-jurisdiction substitution and unverified-translation substitution fail closed.

The first slice should create real source-backed value but should not attempt full corpus breadth, every document family, or every multi-jurisdiction conflict-of-laws scenario.

## 6. System And Module Boundaries

The exact names are not prescribed, but planning should preserve these responsibilities.

### A. Jurisdiction Registry / Scope

Responsibilities:

- canonical jurisdiction identifiers;
- primary jurisdiction for a matter;
- explicit additional jurisdiction or international-source scope when supported;
- prevention of implicit cross-jurisdiction fallback;
- routing to jurisdiction-owned source semantics.

First-version simplification may support one primary jurisdiction per case while preserving an extension seam for multi-jurisdiction matters. Do not silently design the persisted contract in a way that makes later cross-border matters impossible.

### B. Source Provider Adapters

Country/provider-specific acquisition layer.

Candidate providers to re-verify during planning include:

- KR official national legal-information sources;
- World MOLEG foreign-law API as discovery/translation/reference support;
- Philippine official legislative and judicial sources;
- Vietnamese official national legal-document and court sources;
- treaty/international providers in a later approved lane.

Provider availability discovered in conversation is not implementation authority. Planning must verify endpoint/API/bulk-download behavior, terms, identifiers, update rules, and automation constraints.

### C. Raw Source Store

Responsibilities:

- preserve fetched official bytes where technically and legally appropriate;
- record retrieval metadata;
- keep raw data outside Git;
- use immutable/versioned storage where practical;
- never treat a fetch result as selected case authority merely because it exists locally.

### D. Canonical Normalization Layer

Responsibilities:

- deterministic decoding/normalization;
- source identity mapping;
- document metadata extraction;
- raw/canonical integrity binding;
- language/translation status;
- version/effectivity/currentness metadata;
- no legal-applicability judgment.

Each transformation must have one explicit owner. Avoid repeated decoding/normalization across adapters and consumers.

### E. Candidate Search / Index

Responsibilities:

- efficient local discovery over large corpora;
- jurisdiction and source-type filters;
- candidate ranking/search aids;
- no authority promotion.

Index technology is intentionally not fixed yet. SQLite/FTS or another portable local index is a preferred candidate if corpus scale and update behavior justify it. `PLAN.md` must decide from actual data shape and performance needs.

### F. Canonical Source Manifest

Responsibilities:

- bind a case to exact verified legal sources;
- preserve jurisdiction, provider, official identity, source type, language, version/currentness, path, and integrity evidence;
- distinguish selected, excluded when relevant, missing, stale, and not-verified sources;
- reject cross-jurisdiction substitution;
- support downstream reasoning/report dependency checks.

The new manifest must not be designed by blindly copying the Korean schema. Remake analysis must first identify which fields are jurisdiction-neutral and which encode Korean assumptions.

### G. Facts / Evidence / Claims / Reasoning Core

Port only source-backed jurisdiction-neutral semantics.

This layer should not know how to crawl a Philippine website or parse a Vietnamese portal response. It should consume validated canonical source records and jurisdiction-aware legal structures.

Where substantive legal reasoning depends on country-specific hierarchy or doctrine, use explicit jurisdiction-aware contracts or adapters rather than generic text labels.

### H. Report / Legal-Document Projection

User-facing output may be multilingual, but every material legal assertion must remain traceable to the underlying jurisdiction and authoritative source.

Presentation language and legal authority language are separate concerns.

Existing Korean report/document behaviors should be ported only after remake analysis proves their contracts are suitable.

## 7. Data, Storage, And State Direction

Keep code and large operational data physically separate.

Preferred shape:

```text
C:\Users\JIN\Desktop\ai 자동화\
├─ Multi_Jurisdiction_Legal_Workbench\     # Git checkout / program
├─ Multi_Jurisdiction_Legal_Resources\     # large local source data, expected direction
│  ├─ KR\
│  ├─ PH\
│  └─ VN\
└─ Legal_Coding_Agent_Workbench\           # read-only reference for this project
```

The exact resource-root name and final layout must be verified and approved by repository-backed planning.

Within each jurisdiction, planning should evaluate separation of:

- raw/origin source bytes;
- canonical normalized source;
- metadata/currentness state;
- indexes/search data;
- update/download state;
- synthetic fixtures;
- case-selected source copies or references when required.

Do not share writable state with the Korean reference project.

Prefer portable, backup-friendly, inspectable formats. Use SQLite when structured local state or indexing benefits from transactions/querying, but do not force it for immutable raw source storage when files are simpler.

## 8. External Integrations

External integrations are source providers, not legal-decision owners.

For every provider, planning must establish:

- official/non-official status;
- supported jurisdictions/source types;
- API, bulk export, HTML/PDF, or other acquisition mode;
- authentication requirements;
- stable document identity;
- update and currentness semantics;
- rate/automation limits;
- terms, licensing, redistribution constraints;
- raw response format and encoding;
- recoverable retry behavior;
- how failures are represented without inventing source content.

No source provider may receive private case content unless a separate approved workflow explicitly requires and permits that disclosure.

## 9. Security And Privacy Boundaries

- Code repository contains no private case data or bulk operational legal corpus by default.
- Secrets and credentials remain outside Git and are never printed.
- User-supplied narrative strings never become trusted control-plane configuration.
- Source fetchers use typed trusted configuration.
- Verification prefers temporary paths and process-scoped overrides.
- Legal-source acquisition and private-case workflows use separate roots and data policies.
- Future full-fidelity private-case behavior must be explicitly ported and revalidated for this project.
- Public/shareable output remains a separate decision from canonical private/local artifacts.

## 10. Must-Preserve Behavior

During selective porting, preserve these behavior classes when source-backed remake analysis confirms them as applicable:

- confirmed vs uncertain fact separation;
- no fabricated legal text or holdings;
- candidate layer vs actual source authority separation;
- source-manifest traceability;
- missing/not-verified source disclosure;
- exact provenance and currentness binding;
- evidence/claim/reasoning boundaries;
- stale dependency rejection;
- deterministic final report projection;
- full diff-to-requirement mapping;
- private/runtime/generated data exclusion from Git;
- truthful verification and review status.

Do not preserve a Korean-specific implementation detail merely because it already exists.

## 11. Quality Attributes

### Maintainability

Country-specific changes should not require editing every shared consumer. Shared semantics should have one canonical owner.

### Portability

The workbench should remain usable as a local/private project without requiring a cloud backend for basic legal-source processing.

### Recoverability

Raw source acquisition and normalization should be repeatable or restorable. Mutable indexes and state should have rebuild or backup paths.

### Performance

The source/search architecture must be able to handle substantially larger corpora than the current Korean candidate catalogs, especially for Philippine statutes/jurisprudence and Vietnamese legal documents/judgments.

### Testability

Adapters, source normalization, manifest binding, jurisdiction routing, and currentness must be testable with safe synthetic fixtures and controlled snapshots without requiring private case data.

### Extensibility

Adding a new jurisdiction should primarily require a new jurisdiction profile/source adapter and targeted semantics, not a fork of the full reasoning/report application.

## 12. Preferred Technical Directions When Suitable

- Markdown for human-readable project and source-management documentation: `preferred`.
- JSON for machine-readable source manifests, contracts, and exchange artifacts: `preferred` where structured validation is valuable.
- YAML: `deferred`; use only where it adds clear operator value without schema ambiguity.
- SQLite for local metadata/index/state: `preferred candidate`, subject to corpus and update inspection.
- Flat immutable files for raw official-source snapshots: `preferred candidate` when simpler and more recoverable than DB blobs.
- Searchable local full-text index: `preferred candidate`, technology not yet fixed.
- Obsidian links: `not required`; use only if project documentation navigation benefits.
- Vector/semantic search: `deferred`; candidate search must first work deterministically and source integrity must not depend on embeddings.
- Direct LLM API runtime: `deferred / not approved by project start`.
- Local LLM runtime: `deferred / not approved by project start`.
- Web/mobile/desktop frontends: `deferred`; preserve API/contract seams but do not prebuild.
- Automation for source refresh: `preferred future capability` after provider/update rules are stable.

## 13. Rejected Or Disfavored Directions

- one repository/application fork per country;
- editing the Korean reference project to make the new project work;
- bidirectional sync between old and new repositories;
- symlink/junction/shared writable source-data shortcuts;
- treating translations or aggregator metadata as primary authority by default;
- a single generic `law` source type that erases material country-specific distinctions;
- putting bulk foreign legal corpora into Git because they are publicly viewable;
- downloading entire large judgment corpora before rights, scope, indexing, and update needs are established;
- model-memory legal conclusions without verified source support;
- premature microservices or distributed architecture;
- an under-structured one-off PH/VN scraper that bypasses common source identity and manifest contracts.

## 14. Assumptions And Verification Gaps

- The exact local checkout path for the new repository must be verified.
- The exact sibling legal-resource root is not yet durable authority.
- Public API/bulk endpoints and automation permissions for Philippine and Vietnamese official sources must be re-verified at implementation planning time.
- World MOLEG API availability, fields, and license metadata should be re-verified before adapter design.
- The Korean reference project's current reusable contract boundaries must be established through read-only source inspection, not chat memory.
- The correct common source taxonomy is not yet approved.
- The correct local indexing technology is not yet approved.
- Conflict-of-laws and multi-jurisdiction reasoning semantics beyond explicit source separation are deferred.
- User-facing language selection behavior is not yet fully specified.
- External LLM/provider runtime behavior is not part of the approved first architecture.

## 15. Planning Handoff

Before writing `PLAN.md`, Codex must first complete remake analysis against the read-only Korean reference.

Remake analysis should answer:

- Which Korean files/contracts are genuinely jurisdiction-neutral?
- Which contain Korean source categories, law.go.kr identity, Korean language, paths, Excel catalogs, source hierarchy, or currentness assumptions?
- Which schemas can be copied unchanged?
- Which require versioned extension or replacement?
- Which tests prove behavior worth preserving?
- Which privacy/private-case rules can be ported safely?
- Which report/document layers depend on Korean-specific legal semantics?
- Which source acquisition code must remain KR-only?
- Which old implementation or artifacts must never be copied?

The target architecture envelope that `PLAN.md` must preserve:

- one common core;
- explicit jurisdiction boundary;
- provider/adapters separated from reasoning authority;
- official-source-first authority;
- source language and translation status separation;
- code/data separation;
- no reference-project mutation;
- no automatic repository synchronization;
- safe future country expansion.

The smallest coherent delivery slice to evaluate:

- common jurisdiction/source identity foundation;
- minimum reusable source-manifest/core port;
- one verified KR control path;
- one PH official-source path;
- one VN official-source path;
- cross-jurisdiction fail-closed validation.

Deferred capabilities and extension seams to keep open:

- treaty/international-law overlays;
- additional countries;
- multi-jurisdiction conflict-of-laws analysis;
- multilingual user-facing output;
- large judgment-corpus indexing;
- semantic/vector search;
- external provider/LLM automation;
- public or hosted application surfaces.

Decisions `PLAN.md` must not silently override:

- Korean reference remains read-only;
- new repository remains independent;
- large corpora remain outside Git by default;
- official source identity is stronger than candidate/translation layers;
- jurisdiction separation must fail closed;
- no application implementation before plan approval.

Safe implementation flexibility left to Codex:

- exact module/file names;
- programming/package layout consistent with selectively ported stack;
- exact schema split after reference inspection;
- local index technology;
- adapter interfaces;
- fixture layout;
- internal storage representations that preserve the approved source/data boundaries.
