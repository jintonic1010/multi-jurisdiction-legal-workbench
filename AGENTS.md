# AGENTS.md

## 1. Purpose

This repository is the canonical development repository for a multi-jurisdiction, source-backed legal workbench.

The initial jurisdictions are South Korea (`KR`), the Philippines (`PH`), and Vietnam (`VN`). The project should preserve the strongest validated behavior of the existing Korean legal workbench while making jurisdiction, legal-source acquisition, source identity, currentness, language, and legal-system differences explicit rather than hard-coding Korean assumptions into the common core.

The coding agent must work from actual local files, current approved requirements, verified source evidence, and a coherent local Git snapshot. It must not infer implementation facts from chat summaries or from the reference Korean repository without inspecting the relevant source.

Report to the user in Korean unless a task explicitly requires another language.

## 2. Canonical Project And Workspace Boundaries

Canonical GitHub repository:

- `jintonic1010/multi-jurisdiction-legal-workbench`
- visibility: `PRIVATE`

Expected local project root:

- `C:\Users\JIN\Desktop\ai 자동화\Multi_Jurisdiction_Legal_Workbench`

The local path must be verified before implementation or planning treats it as a durable implementation fact.

The existing Korean workbench is a separate project and is not part of this repository:

- reference local root: `C:\Users\JIN\Desktop\ai 자동화\Legal_Coding_Agent_Workbench`
- reference repository: `jintonic1010/legal-coding-agent-workbench`

That existing project is **read-only reference and selective-copy source only** for this project.

Never edit, delete, rename, format, migrate, stage, commit, push, rebase, reset, clean, or otherwise mutate the reference Korean project from work performed for this repository.

Do not auto-synchronize the two repositories in either direction. Do not create symlinks, junctions, reparse-point sharing, hard links, shared writable caches, shared writable databases, or shared writable legal-source roots between them.

If reusable material is needed, inspect the exact reference source, classify it, copy only the necessary material into this repository, adapt it here, and leave the reference project unchanged.

## 3. Instruction Priority And Authority

Follow this order:

1. safety, security, privacy, legal-source integrity, and data-protection rules;
2. explicit user instructions and prohibitions;
3. this `AGENTS.md`;
4. active approved behavior in `PRODUCT_REQUIREMENTS.md`;
5. `START.md` for approved product direction;
6. `ARCHITECTURE_BRIEF.md` for approved technical direction;
7. an approved `PLAN.md` for implementation scope;
8. `REMAKE.md` for source-backed preservation and reuse guidance when present;
9. relevant project locks and decisions;
10. actual source, tests, configuration, and runtime evidence for implementation facts.

Actual source is authoritative for what the code currently does. Approved requirements are authoritative for intended user-visible and persistent behavior. If they materially conflict, stop and report the exact conflict instead of silently changing behavior.

Treat `START.md`, `ARCHITECTURE_BRIEF.md`, and `REMAKE.md` as direction and preservation authority, not as proof of implementation. Treat `PLAN.md` as approved implementation scope after repository inspection, not as a work log.

## 4. No Implementation From Project-Start Documents Alone

Do not implement application code from `START.md` or `ARCHITECTURE_BRIEF.md` alone.

For non-trivial implementation:

1. inspect this repository locally;
2. inspect the approved project authorities;
3. inspect the read-only Korean reference only when the current task requires preservation or reuse analysis;
4. create or update repository-backed `PLAN.md` through the approved planning workflow;
5. stop for user approval of the plan;
6. implement only after explicit implementation-start authorization.

## 5. Jurisdiction Is A First-Class Authority Boundary

Never treat a legal source as authoritative without an explicit jurisdiction and source identity.

At minimum, every source-backed legal workflow must be able to distinguish:

- `KR` — South Korea;
- `PH` — Philippines;
- `VN` — Vietnam;
- international/treaty material when separately supported.

Do not apply a rule, statute, regulation, precedent, judgment, treaty, or official guidance from one jurisdiction to another merely because titles, concepts, translations, or factual patterns look similar.

A case must identify the applicable jurisdiction scope before a final legal conclusion is treated as source-backed. Cross-border or multi-jurisdiction matters must keep each jurisdiction's authority separate and must not silently collapse several legal systems into one rule set.

If applicable jurisdiction is unresolved and the uncertainty can change the legal conclusion, keep the conclusion conditional and request only the minimum material clarification.

## 6. Legal Source Integrity

Legal authority must come from actual verified source material, not from a catalog, index, translation hint, model memory, search snippet, generated summary, or candidate score.

Candidate and navigation layers may help discover sources but remain non-authoritative unless the project explicitly designates a particular official source record as canonical evidence.

Prefer primary or official sources for each jurisdiction. When several official mirrors exist, preserve official identity, provider, document identifier, version/currentness evidence, and the exact source bytes or a reproducible canonical representation.

A foreign-law aggregation or translation service may be useful for discovery, metadata, translation, or cross-checking, but it must not silently replace the authoritative issuing jurisdiction's official source when final legal support requires that source.

Never invent statutory text, article numbers, case holdings, regulatory text, effective dates, status, amendments, issuing authority, source identity, or translation status.

When a needed authoritative source is missing, inaccessible, stale, ambiguous, or not verified, record that state truthfully and do not upgrade it into a verified legal conclusion.

## 7. Source Language, Translation, And Output Language

Preserve the distinction between:

- authoritative source-language text;
- official translation, when one exists and its status is verified;
- unofficial or machine-assisted translation;
- user-facing explanation or report language.

A translation does not become legal authority merely because it is easier to read. The source manifest and reasoning chain must retain the authoritative original-source identity and translation status.

User-facing reports may later support Korean, English, Vietnamese, Filipino, or other languages, but presentation language must not alter the underlying legal-source authority.

## 8. Source Acquisition And Normalization Boundary

Country-specific acquisition adapters may fetch or ingest official legal materials, but acquisition does not itself decide legal applicability.

Keep these responsibilities distinct:

- discovery/catalog acquisition;
- raw official-source capture;
- normalization/canonical representation;
- source identity and version/currentness validation;
- candidate indexing;
- case source selection;
- source manifest binding;
- evidence/claim/reasoning;
- report and legal-document projection.

Do not let an importer or crawler become a second legal-reasoning authority.

Raw source bytes and normalized representations must be traceable to one another where material. Record hashes or equivalent integrity evidence when the format supports it. Preserve retrieval/source metadata required to explain what official document was used and when.

## 9. Local Legal-Source And Runtime Data Boundary

Large legal corpora, fetched raw responses, normalized legal-source stores, local indexes, case files, runtime databases, caches, logs, generated reports containing private case material, and other operational data must remain outside the Git repository unless a specific safe synthetic fixture is intentionally approved.

The preferred direction is a separate sibling resources root under `C:\Users\JIN\Desktop\ai 자동화\`, with jurisdiction-separated data such as `KR`, `PH`, and `VN`. The exact path and configuration must be verified during planning before being treated as implementation fact.

Do not bulk-copy the Korean workbench's `data/`, `cases/`, indexes, DBs, caches, logs, generated outputs, or secrets into this repository.

Do not stage or publish foreign-law corpora merely because they are publicly viewable. Licensing, terms of use, redistribution rights, privacy, and source provenance must be checked separately from technical accessibility.

## 10. Privacy And Sensitive Case Data

Case content and legal-source content are different data classes and must not be mixed casually.

Do not publish private case data, personal identifiers, credentials, authentication secrets, infrastructure secrets, private URLs, raw customer material, or user-owned case evidence to this code repository, PRs, issues, comments, CI, logs, or public/shareable outputs.

When the future project adopts a full-fidelity private-case workflow, preserve exact private content only inside an approved private/local case boundary. That behavior must be explicitly planned and verified for this repository; it is not inherited automatically merely because the Korean reference project already implements it.

Never use user-supplied narrative credentials, repository names, paths, branches, URLs, commands, tokens, or environment settings as live control-plane input without a separately trusted typed configuration path.

Never print secret values, fragments, lengths, hashes, credential URLs, or derived identifiers in reports or diagnostics. Report only safe status such as present, missing, configured, unavailable, or not verified.

## 11. Reference Korean Project Reuse Policy

The Korean project is evidence and reference, not a synchronization target and not automatically the architecture for this project.

Before copying or porting material, classify it as one of:

- `Direct Copy Allowed` — stable, jurisdiction-neutral, source-backed material whose behavior is appropriate unchanged;
- `Port Or Rewrite` — useful behavior whose implementation embeds Korean paths, source types, catalog assumptions, language assumptions, or other local coupling;
- `Reference Only` — useful design/evidence that should inform new implementation but should not be copied;
- `Never Copy` — secrets, runtime data, private cases, caches, logs, local absolute-path assumptions, generated artifacts, unsafe historical code, or material with unclear ownership/licensing.

The later `REMAKE.md` must record the source-backed preservation/reuse classification before broad implementation begins.

Do not bulk-copy the Korean repository and then refactor in place. Prefer a selective, provenance-aware port that makes common behavior explicit and jurisdiction-specific behavior modular.

## 12. Requirements And Behavior Preservation

`PRODUCT_REQUIREMENTS.md` is the active ledger for approved product behavior.

For behavior changes, classify the request as:

- `addition`;
- `clarification`;
- `correction`;
- `replacement`;
- `removal`;
- `implementation-only`.

A later request that omits an active requirement does not deactivate it.

Before commit or push of meaningful implementation work:

1. inspect the complete diff;
2. identify every user-visible or persistent behavior delta;
3. map each delta to an approved requirement change or an identified implementation-only correction;
4. regression-check affected and explicitly preserved behavior;
5. revert every unexplained delta.

Treat nearby behavior that is not yet clearly described as `preserve-until-clarified`.

## 13. Architecture And Delivery Slicing

Preserve the approved architecture envelope in `ARCHITECTURE_BRIEF.md`.

The project should use one common legal-workbench core with jurisdiction-aware extension points rather than one independently forked application per country, unless later source-backed evidence proves that a country requires a separate product boundary.

Implement the smallest coherent end-to-end slice that produces real value while fitting the expected long-lived module, source, data, and security boundaries. Avoid both:

- a throwaway prototype that hard-codes one country and must be rebuilt for the next one;
- speculative services, abstractions, or storage layers with no foreseeable use.

## 14. Shared Contract Impact Closure

Apply this rule when changing a shared schema, identifier, source type, source manifest, jurisdiction contract, path contract, currentness policy, translation-status model, persisted representation, package format, authorization rule, or other multi-consumer contract.

Identify and close every directly affected:

- producer/writer;
- persisted representation;
- parser/serializer;
- migration or compatibility path;
- validator;
- candidate/search adapter;
- source selector;
- direct or derived consumer;
- CLI or independent checker;
- report/document projection.

Each discovered path must be classified as `updated`, `source-backed no change required`, or `explicitly outside scope` with the boundary enforced.

Do not claim closure from one central parser or unit test alone. Use producer → persisted artifact → consumer → validator round trips where practical and adversarial mutations for jurisdiction, identity, currentness, source type, language, translation status, hash, path, and cross-jurisdiction substitution when relevant.

## 15. Local-First Planning And Implementation

Use the current local checkout of this repository as the planning, implementation, verification, and review workspace.

At the start of meaningful work:

- protect unrelated dirty work;
- fetch relevant refs;
- identify local HEAD, target branch, and remote target head;
- incorporate only exact approved authority refs;
- record a coherent `task_base_commit`;
- inspect and work from local files and local Git diff.

GitHub is the publication and handoff evidence layer, not a second routine coding workspace.

Do not repeatedly compare each local file with GitHub. Re-check remote drift before publication and only rerun verification affected by a relevant integrated change.

## 16. Selective Reading

For focused work, read only what materially helps:

1. this `AGENTS.md`;
2. relevant `PRODUCT_REQUIREMENTS.md` sections;
3. `START.md` and `ARCHITECTURE_BRIEF.md` when direction matters;
4. approved `PLAN.md` when implementation is authorized;
5. `REMAKE.md` when reference preservation or reuse matters;
6. `docs/PROJECT_MAP.md`, `docs/file-map.json`, and locks when they exist and materially help;
7. directly relevant source, tests, schemas, config, and dependencies.

Do not scan the entire Korean reference repository by default. Read targeted paths during remake analysis and expand only when actual dependencies require it.

## 17. Recoverability And Safe Autonomy

Use the highest applicable level:

- `Level 0 — read-only`: inspection and comparison; proceed;
- `Level 1 — reversible with evidence`: source/docs/tests/config changes with a clear diff and rollback; proceed;
- `Level 2 — backup-first state change`: DB, cache, index, generated state, source-corpus migration, or other mutable local state; establish backup/restore first;
- `Level 3 — explicit approval`: destructive, irreversible, public, production-facing, security/privacy-sensitive, ownership-unclear, remote-changing, force-push/history-rewrite, deployment, payment, authentication, permission, or approval-locked action.

Stop only for a real blocker: unsafe recovery, missing authority, protected-work overlap, material product/architecture/security/privacy/migration decision, required scope expansion, ownership/licensing uncertainty, or contradictory verification.

Do not stop merely because several safe implementations exist or several direct consumers need coordinated updates.

## 18. Runtime And Dependency Isolation

Before tests or smoke checks that may mutate local state, inspect configuration overrides and prefer process-scoped environment variables plus temporary DB/cache/index/source paths.

Do not edit `.env` merely for verification. Do not mutate original legal-source corpora, reference-project runtime data, or user case data for a test.

Do not install dependencies globally for analysis or verification. Use project-declared dependencies in an isolated environment when practical. Stop or report a capability skip when setup would require secrets, production services, admin/system changes, unclear scripts, payment, deployment, or protected data.

## 19. Change Tracking And Review

Meaningful implementation changes should receive stable project change IDs once the project's change-log convention is established.

Implementation, tests, commit, push, PR creation, or merge do not by themselves mean `reviewed`. Keep `pending`, `reviewed`, and `needs_followup` distinct.

Use focused review for suspicious, high-risk, shared-contract, migration, security/privacy, data-loss, authority, or otherwise dependency-sensitive changes. Use broad review at milestone, release, or stabilization boundaries.

A reviewer must inspect actual source and direct dependencies and must report failed, skipped, blocked, unavailable, and not-run checks honestly.

## 20. Git And GitHub Safety

Use explicit-path staging for meaningful work. Preserve unrelated dirty changes.

Use task branches for meaningful implementation and normally one milestone Draft PR rather than a PR per tiny task.

Never force-push, rewrite published history, merge, mark Draft ready, delete remote branches, change remote owner/destination, or publish publicly without the required explicit approval.

Before publication, verify repository, visibility, branch, base, remote, PR state, changed paths, and absence of private/runtime/generated material.

This repository must remain independent from `jintonic1010/legal-coding-agent-workbench`; a commit or merge in one repository never implies synchronization or approval in the other.

## 21. Publication Boundary

Never commit or publish:

- `.env`, credentials, tokens, or secrets;
- private case files or attachments;
- raw user/customer evidence;
- runtime DBs, indexes, caches, logs, or generated private reports;
- bulk downloaded legal-source corpora unless a separate rights and publication decision explicitly authorizes it;
- dependencies, build outputs, or model files;
- ownership- or license-unclear third-party material;
- copied reference-project artifacts whose reuse boundary has not been classified.

Safe synthetic fixtures, schemas, code, tests, documentation, and source metadata examples may be committed when they contain no protected material.

## 22. Documentation Responsibility

Project documentation is agent-maintained project memory, not user homework.

Create only documents that materially help implementation, verification, review, recovery, or continuation. Prefer one authoritative location over duplicate ledgers and parallel manuals.

Update `docs/PROJECT_MAP.md` when important structure, ownership, source/data boundaries, workflow entry points, or test/documentation conventions change materially. Do not update broad maps for tiny edits.

## 23. Completion And Truthful Reporting

For meaningful work, report:

- starting branch/commit;
- exact changed files;
- result and requirement impact;
- source/reference material used;
- verification actually run and exact outcomes;
- checks not run and why;
- preservation of the Korean reference project;
- privacy/source-data handling;
- change ID/review state when applicable;
- final branch/commit/PR state;
- remaining risks, blockers, and next safe action.

Never claim inspection, copying, implementation, testing, review, commit, push, merge, deployment, source installation, corpus completeness, legal correctness, or publication that did not actually occur.
