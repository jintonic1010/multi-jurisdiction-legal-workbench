# Multi-Jurisdiction Legal Workbench — Active Product Requirements

This file records active approved product behavior for the new independent multi-jurisdiction legal workbench.

Actual source defines implementation facts. These requirements define intended behavior until explicitly changed. Omission from a later request does not deactivate an active requirement.

## Active Requirements

### MJLW-REQ-001 — This project is an independent canonical workbench

- Status: active
- Type: addition
- Requirement: `jintonic1010/multi-jurisdiction-legal-workbench` is the canonical repository for the new multi-jurisdiction legal workbench. It has independent history, requirements, plans, implementation, review state, and releases.
- Preserve: the existing Korean workbench remains a separate project.

### MJLW-REQ-002 — The Korean workbench is read-only reference and selective-copy source

- Status: active
- Type: addition
- Requirement: `C:\Users\JIN\Desktop\ai 자동화\Legal_Coding_Agent_Workbench` and `jintonic1010/legal-coding-agent-workbench` may be inspected for proven behavior and selected reusable material but must not be modified by this project.
- Requirement: reuse must be source-backed and classified before broad porting.
- Prohibited: automatic synchronization, bidirectional propagation, edits, Git writes, symlink/junction/hard-link sharing, or shared writable runtime/source state.

### MJLW-REQ-003 — Initial jurisdictions are KR, PH, and VN

- Status: active
- Type: addition
- Requirement: the first supported jurisdiction set is South Korea (`KR`), the Philippines (`PH`), and Vietnam (`VN`).
- Requirement: future jurisdictions must be addable without cloning the whole application per country.

### MJLW-REQ-004 — Jurisdiction is explicit legal authority context

- Status: active
- Type: addition
- Requirement: every source-backed legal analysis must identify the applicable jurisdiction scope before a final legal conclusion is treated as source-backed.
- Requirement: a source from one jurisdiction cannot satisfy another jurisdiction's source requirement merely because text, title, translation, or subject is similar.
- Requirement: unresolved jurisdiction that can change the conclusion remains an explicit uncertainty.

### MJLW-REQ-005 — One common core is preferred over country forks

- Status: active
- Type: addition
- Requirement: jurisdiction-neutral behavior should live in one common legal-workbench core, while country-specific source acquisition, source categories, hierarchy, identity/currentness, language, and doctrine-sensitive rules remain in jurisdiction-aware modules or adapters.
- Boundary: a separate full product per country requires later source-backed justification and approval.

### MJLW-REQ-006 — Verified official or primary sources control final legal support

- Status: active
- Type: addition
- Requirement: final legal support must be grounded in actual verified official/primary legal-source material for the applicable jurisdiction when such a source is required and available.
- Requirement: catalogs, candidate indexes, search snippets, translations, aggregators, summaries, model memory, and rankings are navigation/advisory layers unless a specific record is separately verified as authoritative.
- Requirement: legal text, article numbers, holdings, status, effective dates, amendments, and issuing authority must never be invented.

### MJLW-REQ-007 — Source acquisition is separate from legal reasoning authority

- Status: active
- Type: addition
- Requirement: API clients, crawlers, bulk importers, parsers, and normalizers may acquire and structure source material but cannot decide substantive legal applicability merely because a document was fetched or indexed.
- Requirement: candidate discovery → official source → canonical identity/currentness → case source selection → source manifest → reasoning must remain distinguishable stages.

### MJLW-REQ-008 — Source identity is jurisdiction-aware and traceable

- Status: active
- Type: addition
- Requirement: selected legal sources must retain enough metadata to identify the jurisdiction, source provider/authority, source type, official document identity, language, version or effective/currentness state, local path or stable reference, and integrity evidence needed to reproduce the source decision.
- Requirement: raw and normalized representations must remain traceable when normalization is used.

### MJLW-REQ-009 — Translation status never silently changes authority

- Status: active
- Type: addition
- Requirement: authoritative source-language text, verified official translation, unofficial translation, machine-assisted translation, and user-facing explanation must remain distinguishable.
- Requirement: a translation does not become legal authority solely because the report is written in that language.
- Requirement: source manifest and downstream reasoning retain original authoritative-source identity.

### MJLW-REQ-010 — Candidate and source taxonomies may differ by jurisdiction

- Status: active
- Type: addition
- Requirement: the system must not force materially different Philippine or Vietnamese legal materials into Korean source categories when that would lose hierarchy or legal meaning.
- Requirement: a shared top-level source contract may exist, but country-specific legal source types/hierarchy must be preserved where material.

### MJLW-REQ-011 — Large legal corpora remain outside Git by default

- Status: active
- Type: addition
- Requirement: bulk legal-source downloads, raw responses, normalized corpora, large judgment collections, runtime databases, indexes, caches, logs, and generated operational data remain outside the code repository by default.
- Requirement: Git may contain code, schemas, documentation, safe metadata examples, and synthetic fixtures only, unless a separate explicit publication/rights decision authorizes more.

### MJLW-REQ-012 — Code and resource roots are physically independent

- Status: active
- Type: addition
- Requirement: the program Git checkout and large local legal-resource storage use separate roots.
- Preferred direction: a sibling resource root under `C:\Users\JIN\Desktop\ai 자동화\` separated into `KR`, `PH`, and `VN`; exact path/layout must be verified during planning.
- Prohibited: shared writable resource roots with the Korean reference project.

### MJLW-REQ-013 — Source currentness and historical status must be explicit

- Status: active
- Type: addition
- Requirement: where the issuing system exposes amendment, repeal, supersession, effectivity, consolidation, or version information, the project must preserve and validate that state rather than treating any downloaded text as automatically current.
- Requirement: stale, missing, superseded, ambiguous, or not-verified source state must not be promoted into a current verified conclusion.

### MJLW-REQ-014 — Foreign-law aggregators are support layers, not automatic authority replacements

- Status: active
- Type: addition
- Requirement: sources such as World MOLEG may support discovery, metadata, Korean translation, comparison, or reference, but they do not automatically replace the issuing jurisdiction's official primary source for final legal authority.
- Requirement: license/public-use metadata from such services must be retained where it affects reuse or redistribution.

### MJLW-REQ-015 — Provider-specific acquisition must be verifiable and recoverable

- Status: active
- Type: addition
- Requirement: each external source provider adapter must document or encode stable identity, acquisition mode, update behavior, failure representation, retry/recovery boundary, and source/rights constraints required for safe operation.
- Requirement: provider failure never authorizes fabricated source content or silent fallback to a different jurisdiction/provider.

### MJLW-REQ-016 — Korean behavior is selectively ported, not inherited by assertion

- Status: active
- Type: addition
- Requirement: behavior from `legal-coding-agent-workbench` becomes part of this project only after source-backed inspection and classification.
- Required classification: `Direct Copy Allowed`, `Port Or Rewrite`, `Reference Only`, or `Never Copy`.
- Requirement: a future `REMAKE.md` records the preservation/reuse findings before broad implementation.

### MJLW-REQ-017 — Core provenance boundaries should be preserved when applicable

- Status: active
- Type: addition
- Requirement: remake analysis should preserve validated jurisdiction-neutral concepts from the Korean workbench when source evidence supports them, including fact certainty/provenance, candidate-vs-authority separation, source manifest traceability, evidence/claim boundaries, legal reasoning dependency integrity, stale/currentness rejection, deterministic report projections, and truthful validation state.
- Boundary: Korean-specific source assumptions are not automatically preserved.

### MJLW-REQ-018 — Cross-jurisdiction substitution fails closed

- Status: active
- Type: addition
- Requirement: a `KR`, `PH`, or `VN` source record must not be interchangeable across jurisdictions unless a separately supported cross-jurisdiction/international relationship explicitly permits that use.
- Verification: future shared source contracts must include adversarial jurisdiction/identity/currentness substitution tests.

### MJLW-REQ-019 — Real case data remains private and outside the code repository

- Status: active
- Type: addition
- Requirement: real user case facts, attachments, identifiers, evidence, and private generated reports must not be committed to this code repository, PRs, issues, comments, CI, or logs.
- Requirement: any future full-fidelity private-case workflow must be explicitly ported, scoped, and revalidated for this repository before use.

### MJLW-REQ-020 — Secrets and narrative control-like text remain non-executable by default

- Status: active
- Type: addition
- Requirement: secrets, credentials, tokens, credential URLs, and infrastructure secrets never enter Git or logs.
- Requirement: user-supplied narrative paths, repository names, branches, commands, URLs, credentials, or configuration-like text cannot become trusted runtime/control-plane settings without a separately trusted typed configuration path.

### MJLW-REQ-021 — No direct LLM/provider runtime is approved by project start

- Status: active
- Type: clarification
- Requirement: starting this project does not itself authorize a direct OpenAI API, local LLM, cloud LLM, embedding/vector service, or automated provider submission runtime.
- Requirement: such integrations may be added later only through explicit requirements, privacy/source boundaries, and repository-backed planning.

### MJLW-REQ-022 — User-facing output language is separate from legal-source authority

- Status: active
- Type: addition
- Requirement: future reports may support different user-facing languages, but output language must not change the authoritative source identity or silently transform translation status.
- Current scope: exact language UX is deferred to later planning/requirements.

### MJLW-REQ-023 — First implementation must prove one common contract across KR, PH, and VN

- Status: active
- Type: addition
- Requirement: the first meaningful implementation milestone should prove the common jurisdiction/source foundation with at least one controlled end-to-end `KR` path, one official `PH` source path, and one official `VN` source path, subject to repository-backed plan review.
- Requirement: the milestone must demonstrate source identity/manifest binding and cross-jurisdiction fail-closed behavior before broad corpus expansion.

### MJLW-REQ-024 — Bulk corpus acquisition requires source and rights planning first

- Status: active
- Type: addition
- Requirement: do not start bulk or near-complete acquisition of statutes/judgments until the applicable provider's technical access, stable identifiers, update/currentness semantics, rate/automation limits, storage plan, licensing/terms, redistribution boundary, and recovery strategy are recorded and approved in the implementation plan.
- Requirement: technical accessibility alone does not establish redistribution permission.

### MJLW-REQ-025 — Planning follows remake analysis before implementation

- Status: active
- Type: addition
- Requirement: because this project intentionally reuses a mature Korean reference system, read-only remake analysis and `REMAKE.md` must precede broad repository-backed implementation planning.
- Requirement: after remake evidence is reviewed, Codex creates `PLAN.md`; implementation starts only after user approval and a separate implementation-start instruction.

### MJLW-REQ-026 — Documentation is agent-maintained project memory

- Status: active
- Type: addition
- Requirement: the user is not responsible for manually maintaining requirements, project maps, current-state files, change logs, schemas, source policy, or coding-agent handoffs.
- Requirement: agents create/update only documents that materially help implementation, verification, recovery, review, or continuation.

### MJLW-REQ-027 — Verification claims are exact and source-backed

- Status: active
- Type: addition
- Requirement: do not claim corpus completeness, currentness, legal correctness, official status, translation authority, redistribution safety, installation, test pass, review completion, commit, push, or merge without direct evidence for that exact claim.
- Requirement: failed, blocked, unavailable, skipped, and not-run checks remain explicit.

## Initial Deferred Decisions

The following are intentionally not yet fixed and must not be invented during implementation:

- exact common source-type taxonomy;
- exact `source-manifest` schema/version;
- exact local resource-root name and layout;
- index/search technology;
- Philippine and Vietnamese provider adapter endpoints and bulk strategies;
- treaty/international-law overlay contract;
- multi-jurisdiction conflict-of-laws reasoning;
- user-facing language selection UX;
- hosted/web/mobile/desktop surfaces;
- direct LLM/provider runtime;
- public redistribution of downloaded source corpora.

## Initial Next Workflow

`/리메이크분석` should inspect the existing Korean workbench as read-only reference and create `REMAKE.md` in this repository. Repository-backed `/작업계획` follows only after that preservation/reuse evidence is available and reviewed.
