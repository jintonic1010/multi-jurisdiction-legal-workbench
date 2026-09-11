# START.md

## Purpose

This document is the initial handoff for the independent multi-jurisdiction legal workbench.

The project expands the source-backed legal-workbench concept from one Korean legal-source environment into a jurisdiction-aware system that can support South Korea (`KR`), the Philippines (`PH`), and Vietnam (`VN`) without turning each country into a separate forked application.

This document defines product direction and startup constraints. It is not implementation authority and must not be used by itself to start application coding.

Do not implement application code from this `START.md` alone. Use it only as initial project direction. For non-trivial implementation, inspect the repository and the read-only Korean reference, create repository-backed `PLAN.md`, stop for user approval, and begin implementation only after a separate implementation-start instruction.

## Source-Management Target

- Canonical repository: `jintonic1010/multi-jurisdiction-legal-workbench`
- Repository visibility: `PRIVATE`
- Default branch: `main`
- Verified initial governance commit: `0931bfe05e78cb6d204ab7cab200209690edd77e`
- Expected local project root: `C:\Users\JIN\Desktop\ai 자동화\Multi_Jurisdiction_Legal_Workbench`
- Local root status: expected from the user's prepared workspace; Codex must verify it before treating it as implementation fact.

Reference-only Korean project:

- Local root: `C:\Users\JIN\Desktop\ai 자동화\Legal_Coding_Agent_Workbench`
- Repository: `jintonic1010/legal-coding-agent-workbench`
- Role: read-only reference and selective-copy source only
- Automatic synchronization: prohibited
- Modification of the reference project from this project: prohibited

Approved initial source-management documents:

- `AGENTS.md`
- `START.md`
- `ARCHITECTURE_BRIEF.md`
- `PRODUCT_REQUIREMENTS.md`
- `docs/requirement-changelog.md`

Files intentionally not created yet:

- application/source scaffolding;
- package/runtime configuration;
- importers/crawlers;
- schemas beyond the initial requirement authority;
- tests;
- `PLAN.md`;
- `REMAKE.md`;
- local legal-source corpora;
- DB/index/cache files;
- deployment files;
- provider/API runtime integrations.

## Project Overview

The project will be a source-backed legal analysis workbench for multiple legal jurisdictions. The first target jurisdictions are South Korea, the Philippines, and Vietnam.

The existing Korean legal workbench has already established valuable patterns for structured consultation handoff, fact separation, legal-source manifests, source/evidence/claim/reasoning boundaries, final reports, legal-document drafting, private-case protection, stale/currentness handling, and source-backed verification. Those capabilities are not automatically copied. They are a preservation and reuse reference to be inspected and classified before porting.

The new project should preserve proven jurisdiction-neutral behavior while replacing Korean-only assumptions with explicit jurisdiction contracts, country-specific source adapters, source-type semantics, language/translation metadata, official-source identity, update/currentness rules, and local corpus handling.

The initial useful product is not three unrelated country bots. It is one legal-workbench core that selects and validates the correct legal-source lane for the matter's jurisdiction and produces source-backed analysis without cross-jurisdiction contamination.

## User Intent

The user wants to keep the existing Korean legal AI intact and build a separate stronger international/multi-jurisdiction version.

The user specifically wants the new system to be usable for people dealing with Philippine and Vietnamese law, including friends living in those countries, while retaining South Korean capability.

The user wants:

- a separate local project root and separate private GitHub repository;
- the existing Korean project left untouched;
- selective reuse of proven Korean workbench behavior rather than a destructive rewrite;
- official or primary legal sources for each country where practical;
- the ability to obtain large or complete legal corpora through official APIs, bulk sources, or controlled official-source ingestion when available;
- a system that can later grow to additional countries without cloning the whole application per country;
- local legal-source data separated from the code repository;
- the AI to manage technical structure, source contracts, verification, and documentation without making the user manually maintain project state.

The user wants to avoid:

- modifying or destabilizing the existing `Legal_Coding_Agent_Workbench`;
- manually duplicating the same legal core for every country;
- treating translations, catalogs, or model memory as legal authority;
- mixing one country's law into another country's analysis;
- putting huge legal corpora or private case material into GitHub;
- creating a short-lived prototype that must be rebuilt as soon as another jurisdiction is added.

## User Working Style

For this project, collaboration should follow these durable preferences:

- give the conclusion first;
- recommend one strong default direction rather than many equal alternatives;
- reduce repeated questions and manual relay work;
- inspect actual source and GitHub evidence instead of asking the user to summarize technical state;
- let the coding agent handle dependency discovery, documentation, verification, and Git hygiene;
- preserve exact scope when the user says to do only a specific thing;
- distinguish confirmed facts, assumptions, recommendations, and unverified items;
- stop only for material risk, missing authority, destructive or difficult-to-reverse actions, privacy/security concerns, or decisions that materially change product direction.

## Confirmed Product Requirements

### Product Requirements

- The project is an independent multi-jurisdiction legal workbench, not an in-place modification of the Korean workbench.
- Initial jurisdictions are `KR`, `PH`, and `VN`.
- Jurisdiction must be explicit in legal-source selection and legal analysis.
- The existing Korean workbench must remain untouched and may be used only as a read-only reference/selective-copy source.
- The system should retain a common legal-analysis core where behavior is genuinely jurisdiction-neutral.
- Country-specific legal-source acquisition and legal-system semantics must be isolated behind jurisdiction-aware boundaries rather than duplicated whole-application forks.
- Final legal support must rely on verified official/primary legal-source material, not only a candidate index, translation service, search result, or LLM memory.
- Large legal-source corpora must remain outside the Git code repository by default.
- The architecture must keep future country expansion feasible without requiring a structural rewrite.

### Technical Requirements

- Maintain independent Git history for this repository.
- Do not auto-sync with `jintonic1010/legal-coding-agent-workbench`.
- Do not create symlinks, junctions, hard links, or shared writable runtime/source stores between the new project and the Korean reference project.
- Use explicit jurisdiction/source identity and preserve official source provenance, language, version/currentness, and integrity evidence.
- Keep acquisition, normalization, indexing, source selection, legal reasoning, and report projection as separate responsibilities.
- Preserve source-language authority separately from translations and presentation language.
- Use repository-backed planning before implementation.
- Use only safe synthetic fixtures in Git; keep real case data and bulk legal corpora outside Git.

### Documentation Requirements

- `PRODUCT_REQUIREMENTS.md` is the active behavior ledger.
- `ARCHITECTURE_BRIEF.md` defines the approved multi-jurisdiction technical envelope.
- A later source-backed `REMAKE.md` must classify what from the Korean reference project is safe to copy, port/rewrite, use only as reference, or never copy.
- Codex must create `PLAN.md` only after inspecting both the new repository and the relevant read-only reference source.
- Future structure maps and file maps should be created only when the real implementation makes them useful.

### Legacy / Remake Preservation Requirements

The Korean project is a preservation reference, not the canonical project being edited.

A later remake analysis must inspect and classify at least these behavior families when they exist in the current Korean source:

- consultation/intake and structured handoff;
- fact/certainty/provenance handling;
- candidate-source discovery;
- source manifest and currentness;
- evidence and claim contracts;
- structured legal reasoning;
- final Markdown/JSON reports;
- citation appendices;
- legal-document deliverables;
- private-case preservation boundaries;
- package/finalization/history behavior;
- review/change tracking;
- source-pack/manual ChatGPT integration where still applicable.

Nothing in this list authorizes copying a file or implementation before source-backed classification.

## Assumptions

- Assumption: the user has prepared a new local folder under `C:\Users\JIN\Desktop\ai 자동화\` corresponding to this repository.
  - Reason: the user stated that the local folder structure was being prepared separately.
  - What to verify: exact path, Git remote, and local checkout state before planning.

- Assumption: official Philippine and Vietnamese legal-source systems can provide enough primary-source coverage for a useful source-backed workbench even where a public developer API is absent.
  - Reason: earlier research identified official legal databases and downloadable official materials.
  - What to verify: exact API/bulk/download terms, coverage, update semantics, robots/terms, licensing, stable identifiers, and automation limits during source-adapter planning.

- Assumption: a meaningful portion of the Korean reasoning/report pipeline can become jurisdiction-neutral.
  - Reason: many existing concepts such as fact provenance, evidence binding, source manifests, claim support, currentness, and report integrity are structurally general.
  - What to verify: exact Korean assumptions embedded in schemas, enums, paths, source types, language handling, legal hierarchy, renderers, tests, and currentness logic.

- Assumption: large source corpora should use a sibling local resource root rather than living inside the Git checkout.
  - Reason: Philippine and Vietnamese source volumes may be large and may have redistribution restrictions.
  - What to verify: exact local resource root, backup strategy, index technology, update workflow, and configuration boundary.

## Recommended Initial Direction

Keep one common legal-workbench core and add explicit jurisdiction-aware source and legal-system boundaries.

The architecture should distinguish:

1. jurisdiction selection/scope;
2. country-specific source provider adapters;
3. raw and normalized source storage;
4. canonical source identity/currentness;
5. candidate discovery/indexing;
6. case source selection and manifest binding;
7. shared fact/evidence/claim/reasoning contracts where they are truly jurisdiction-neutral;
8. country-specific legal hierarchy, source-type, and currentness rules where necessary;
9. user-facing report/document projection and language selection.

Do not begin by copying the full Korean repository. First produce `REMAKE.md` from read-only inspection, then let repository-backed planning choose the smallest coherent port.

The preferred first implementation slice after remake analysis is:

- establish the common project skeleton and resource-path boundary;
- establish the jurisdiction contract and source identity model;
- port only the smallest validated common source-manifest/core infrastructure required for one end-to-end source-backed path;
- prove that one `KR` path works without mutating the reference project;
- then add one `PH` and one `VN` official-source path through the same common contract;
- prove that cross-jurisdiction substitution fails closed.

This is a planning recommendation, not implementation authority. `PLAN.md` must confirm the actual slice from repository and reference-source evidence.

## Suggested Project Structure

The following is a directional shape, not a mandatory implementation tree:

```text
Multi_Jurisdiction_Legal_Workbench/
├─ AGENTS.md
├─ START.md
├─ ARCHITECTURE_BRIEF.md
├─ PRODUCT_REQUIREMENTS.md
├─ docs/
├─ src/ or tools/                 # actual stack to be decided from source-backed planning
│  ├─ core/
│  ├─ jurisdictions/
│  │  ├─ kr/
│  │  ├─ ph/
│  │  └─ vn/
│  ├─ sources/
│  └─ reporting/
└─ tests/
```

Possible external resource shape:

```text
C:\Users\JIN\Desktop\ai 자동화\Multi_Jurisdiction_Legal_Resources\
├─ KR\
├─ PH\
└─ VN\
```

The exact paths, module names, storage layout, and stack must be chosen by `PLAN.md` after inspection. Do not create this tree merely to satisfy this document.

## Documentation Responsibility

The user is not responsible for manually maintaining project documentation.

Agents should create or update only documents that materially help current work, such as:

- `REMAKE.md` after reference-project analysis;
- `PLAN.md` after repository-backed planning;
- `docs/PROJECT_MAP.md` once real structure exists;
- `docs/source-policy.md` once jurisdiction/source policy needs a durable operational contract;
- `docs/current-state.md` when multi-session implementation begins;
- change-log/review evidence when meaningful implementation starts.

Avoid empty template documents and duplicate ledgers.

## Initial Docs To Create Or Update

Current startup set:

- `AGENTS.md`
  - Purpose: standalone runtime governance, source integrity, reference-read-only boundary, privacy, recovery, verification, Git, and review rules.

- `START.md`
  - Purpose: product direction and initial handoff.

- `ARCHITECTURE_BRIEF.md`
  - Purpose: multi-jurisdiction architecture envelope and extension boundaries.

- `PRODUCT_REQUIREMENTS.md`
  - Purpose: active approved product behavior.

- `docs/requirement-changelog.md`
  - Purpose: meaningful future requirement supersession/history; initial baseline only.

Do not create `PLAN.md` during project start.

## Initial Planning Guidance

The next source-backed workflow should be remake analysis before implementation planning.

The coding agent should eventually:

1. open the canonical local checkout of `multi-jurisdiction-legal-workbench`;
2. read this repository's `AGENTS.md`, `START.md`, `ARCHITECTURE_BRIEF.md`, and `PRODUCT_REQUIREMENTS.md`;
3. verify the exact read-only Korean reference path and repository state;
4. inspect the Korean reference without modifying it;
5. create `REMAKE.md` classifying reusable behavior and files as Direct Copy Allowed, Port Or Rewrite, Reference Only, or Never Copy;
6. preserve source-backed evidence for Korean assumptions that must not leak into the common core;
7. stop after remake analysis for review;
8. after approved remake evidence exists, create repository-backed `PLAN.md` for the first coherent end-to-end slice;
9. stop for user approval of that plan;
10. do not implement application code before the explicit implementation-start step.

## What The Coding Agent Should Inspect First

For the later remake analysis, inspect selectively:

### New canonical project

- `AGENTS.md`
- `START.md`
- `ARCHITECTURE_BRIEF.md`
- `PRODUCT_REQUIREMENTS.md`

### Read-only Korean reference

Start with navigation/authority rather than whole-repository scanning:

- reference `AGENTS.md`;
- reference `PRODUCT_REQUIREMENTS.md`;
- reference `START.md`;
- `docs/PROJECT_MAP.md` and `docs/file-map.json` if current and useful;
- current source-policy and case-flow documentation;
- directly relevant source contracts, schemas, tests, and adapters discovered from those maps.

Broaden only when dependency evidence requires it.

## Constraints

- Existing Korean project must remain unchanged.
- New repository is independent and private.
- No bulk legal-source corpus in Git by default.
- No private case data in the code repository.
- No unverified cross-jurisdiction legal conclusion.
- No translation promoted to authority without verified status.
- No direct LLM/API/provider runtime is assumed or approved merely by starting this project.
- No destructive migration or reuse of reference runtime state.
- No country-specific forked application unless later evidence proves it necessary.
- Preserve future extensibility to additional jurisdictions without speculative prebuilding.

## Do Not Do

- Do not modify `C:\Users\JIN\Desktop\ai 자동화\Legal_Coding_Agent_Workbench`.
- Do not bulk-copy the Korean repository into the new repository.
- Do not copy `.env`, credentials, cases, runtime DBs, source corpora, caches, indexes, logs, generated private output, or unclear licensed material.
- Do not assume Korean source types or legal hierarchy fit `PH` or `VN`.
- Do not treat World MOLEG or another translation/aggregation layer as automatically stronger than the issuing jurisdiction's official source.
- Do not hard-code one language as legal authority for all jurisdictions.
- Do not create crawlers or download millions of documents before terms, source identity, storage, update, and rights boundaries are planned.
- Do not implement code before `REMAKE.md`, repository-backed `PLAN.md`, plan review, and explicit implementation authorization.

## Risk Areas / Ask Before Doing

Explicit approval is required before:

- deleting or moving existing user data or source corpora;
- changing public visibility or repository ownership;
- bulk publication or redistribution of foreign legal-source corpora;
- using private/user credentials for external services;
- production deployment or external publication;
- destructive migrations;
- force-push or history rewrite;
- changing a locked privacy/security boundary;
- any implementation that would require modifying the Korean reference repository.

## Verification Direction

Later implementation should use practical source-backed verification including:

- jurisdiction substitution negatives (`KR` source cannot satisfy `PH`, etc.);
- source identity/currentness mutations;
- translation-status mutations;
- raw-to-normalized integrity checks;
- adapter → persisted source → source manifest → reasoning/report consumer round trips;
- stale/repealed/superseded source handling;
- missing-source fail-closed behavior;
- no mutation of the Korean reference tree;
- no private/runtime/generated material in Git.

If a check cannot be run, report why. Do not claim a corpus is complete, current, legally authoritative, or redistribution-safe without evidence for that exact claim.

## Final Handoff Rule

This `START.md` and `ARCHITECTURE_BRIEF.md` are approved initial direction only.

Next recommended workflow: source-backed remake analysis of the existing Korean workbench as a read-only reference. After `REMAKE.md` is reviewed, create `PLAN.md` from the new repository and reference evidence. Implementation begins only after plan approval and a separate implementation-start instruction.
