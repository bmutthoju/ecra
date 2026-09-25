# ECRA Reference Application — VS-R01 Lecture or Sermon Claim Review

> Status: REVIEW
> Authority: ENGINEERING / INFORMATIVE
> Generation: GEN1
> Scope: Detailed P0 vertical-slice specification for Lecture or Sermon Claim Review
> Matrix Basis: Approved ECRA Reference Implementation — Cross-Slice Capability Matrix
> Portfolio Basis: Approved ECRA Reference Application — Vertical Slice Portfolio

## 1. Purpose and Scope

### 1.1 Purpose

VS-R01 demonstrates an end-to-end, claim-first evidence-review workflow for lectures, sermons, religious talks, and closely related historical or educational presentations.

The slice is intended to demonstrate that the ECRA reference implementation can represent and trace substantive claims across materially different claim types without silently converting evidence review into a domain-specific truth engine.

The workflow shall support:

- source-material intake and preservation;
- identification of substantive claims;
- reviewer selection and correction of claim spans;
- classification of claims where useful;
- identification and registration of relevant sources and evidence;
- explicit evidence-to-claim relationships;
- provenance and source-location preservation;
- assessment of support, contradiction, qualification, or unresolved status;
- explicit uncertainty and limitations;
- preservation of claim and assessment history;
- semantic machine representation and logical round-trip behavior;
- a user-visible evidence report.

### 1.2 Intended Users

Primary users include:

- readers reviewing a lecture or sermon;
- researchers studying religious or historical claims;
- educators performing source-based review;
- reviewers checking citations or factual assertions;
- analysts comparing claims with primary and secondary sources.

The slice does not require the reviewer to belong to, represent, or endorse the religious tradition discussed in the source material.

### 1.3 Workflow Boundary

The slice begins with a lecture, sermon, or religious-talk transcript or an application-accessible source artifact and ends with an auditable evidence-review result and report.

The workflow may include user-provided source material, source metadata, citations, or additional evidence.

The workflow does not define:

- theological adjudication;
- religious authority;
- a universal interpretation engine;
- automated determination of doctrinal truth;
- generalized web crawling or search;
- a universal source-ranking engine;
- a generalized knowledge graph;
- autonomous religious-content moderation;
- a universal reasoning engine;
- a generalized workflow/orchestration platform;
- a distributed deployment architecture.

### 1.4 Domain-Neutrality Principle

The application shall distinguish at least the following broad claim characteristics where useful:

- factual claims;
- historical claims;
- textual/source claims;
- interpretive claims;
- theological or doctrinal claims;
- quotations or attributed statements;
- normative or prescriptive statements;
- opinions, rhetorical statements, or predictions.

These classifications are application-level review aids. They do not establish new ECRA semantic root types.

A classification shall not itself determine whether a claim is true, false, authoritative, or theologically valid.

### 1.5 Core Review Principle

The system shall represent what the available evidence establishes, contradicts, qualifies, or leaves unresolved.

It shall not silently transform:

- source integrity into truth;
- source authenticity into truth;
- source authority into truth;
- citation presence into evidentiary support;
- reviewer assertion into established fact;
- religious affiliation into evidentiary authority;
- absence of evidence into evidence of falsehood.

Where the evidence is insufficient, conflicting, ambiguous, inaccessible, or interpretation-dependent, the result shall preserve that limitation.

## 2. Scenario and Preconditions

### 2.1 Primary Scenario

A reviewer provides a transcript of a lecture, sermon, or religious talk and asks the application to identify substantive claims and examine the available evidence for those claims.

A typical workflow is:

```text
Lecture / sermon transcript
    → identify substantive claims
    → review and correct claim selection
    → identify relevant sources
    → acquire/register evidence
    → associate evidence with claims
    → assess support / contradiction / qualification / unresolved status
    → preserve provenance and traceability
    → generate evidence report
```

### 2.2 Supported Input Forms

The initial reference application may accept:

- plain-text transcripts;
- text extracted from an uploaded document;
- application-readable text artifacts;
- transcript text supplied by the reviewer;
- source metadata supplied by the reviewer.

The implementation shall preserve the distinction between:

1. original source material;
2. an acquired or extracted artifact;
3. text selected from that artifact;
4. claims derived from selected text;
5. evidence obtained from other sources.

### 2.3 Optional Inputs

Optional inputs may include:

- speaker/presenter name;
- title;
- date;
- event or venue;
- transcript provenance;
- publication/source URL or locator;
- cited references;
- language;
- reviewer notes;
- reviewer-specified claims;
- reviewer-selected text spans;
- candidate evidence sources.

Optional metadata supplied by a user shall not automatically acquire evidentiary status.

If optional user-supplied information is substantive and participates in the review, it may be represented as a claim or assertion and evaluated under the same evidence-backed rules.

### 2.4 Preconditions

Before evaluation begins, the application shall establish as much as is available of:

- source/artifact identity;
- accessible content;
- source location;
- acquisition or extraction information;
- source version/revision state where applicable.

A review may proceed with incomplete metadata when the remaining material is sufficient for a meaningful partial result.

The report shall identify material input-quality limitations.

### 2.5 Input Quality States

The application shall distinguish, as applicable:

- successfully acquired;
- represented from supplied content;
- partially acquired;
- incomplete;
- inaccessible;
- unavailable;
- malformed;
- changed since acquisition;
- not independently verified.

The application shall not silently treat an input-quality failure as a substantive evidentiary conclusion.

## 3. End-to-End Workflow

### 3.1 Stage 1 — Source Intake

The reviewer selects or supplies the lecture/sermon source.

The application registers the source and, where applicable, an acquired artifact containing the transcript.

The application shall preserve enough source-location information to allow the reviewer to return to the originating material.

### 3.2 Stage 2 — Artifact Inspection

The reviewer can inspect the supplied or acquired content.

The UI should permit the reviewer to open and read the originating source or acquired artifact subject to access restrictions.

If the artifact is derived from another representation, the application shall preserve relevant transformation provenance.

### 3.3 Stage 3 — Claim Identification

Candidate substantive claims may be identified automatically or manually.

Automated extraction is a convenience capability of the application layer. It shall not make a candidate claim authoritative without review.

The reviewer shall be able to:

- accept a candidate claim;
- reject a candidate claim;
- edit a candidate claim;
- select a portion of source text as the claim basis;
- enter a claim manually;
- identify a claim as ambiguous or requiring interpretation;
- record a material correction or exclusion.

### 3.4 Stage 4 — Claim Qualification

The application may record useful descriptive classifications, such as factual, historical, textual, interpretive, theological, normative, attributed quotation, opinion, or prediction.

A classification shall be represented as review metadata or an application-level construct unless an approved ECRA semantic construct is specifically required.

Where a statement is primarily rhetorical, opinion-based, predictive, or otherwise outside the factual evidence-review scope, the reviewer may exclude or classify it rather than forcing an unsupported factual assessment.

The excluded statement and reason should remain visible when necessary to preserve context.

### 3.5 Stage 5 — Evidence Identification

Evidence may be:

- cited by the original speaker;
- supplied by the reviewer;
- discovered through an application-level search or retrieval mechanism;
- derived from another evidence chain;
- manually selected from an accessible source.

Evidence discovery is not itself an ECRA semantic capability. The reference application shall keep discovery mechanisms replaceable.

### 3.6 Stage 6 — Evidence Registration

For each evidence item, the application records, as applicable:

- source identity;
- acquired artifact identity;
- version/revision;
- source location;
- relevant excerpt or evidence content;
- acquisition/provenance information;
- integrity information;
- authenticity information where available;
- authority information where available;
- access limitations.

Evidence characteristics shall remain distinct from the assessment conclusion.

### 3.7 Stage 7 — Evidence-to-Claim Association

The reviewer associates evidence with claims using explicit typed relationships.

A claim may have:

- multiple evidence items;
- supporting evidence;
- contradictory evidence;
- qualifying evidence;
- insufficient or inconclusive evidence;
- no currently available evidence.

An evidence item may be relevant to multiple claims.

The relationship itself shall be independently identifiable and traceable.

### 3.8 Stage 8 — Assessment

The application represents an assessment of the available evidence against the claim.

The slice supports, as applicable:

- Support;
- Contradiction;
- Qualification / Partial Support;
- Unresolved / Insufficient Evidence.

The assessment shall include uncertainty or limitations where they materially affect interpretation.

The application shall preserve the distinction between:

- evidence content;
- evidence relationship;
- source characteristics;
- assessment;
- reviewer conclusion or editorial interpretation.

### 3.9 Stage 9 — Human Review

Human review is authoritative only as a recorded review action, not as an automatic proof of the conclusion.

Material human corrections or evaluations shall record, where applicable:

- reviewer identity;
- time;
- prior state;
- revised state;
- justification;
- relevant evidence;
- provenance of the action.

A material reviewer assertion used as part of an evidentiary conclusion shall be subject to the same evidence-backed principles as other substantive claims.

### 3.10 Stage 10 — Report Generation

The report shall present:

- the reviewed claim;
- source location;
- selected and excluded text portions where applicable;
- claim classification where recorded;
- evidence items;
- evidence locations;
- relationship type and direction;
- assessment;
- uncertainty and limitations;
- source integrity/authenticity/authority information where applicable;
- provenance;
- traceability;
- version/history information where relevant.

The report shall not silently omit context needed to understand a selected claim.

## 4. Semantic Object Requirements

The following objects are required or conditionally required based on the workflow. They reuse approved ECRA semantics and do not establish new portfolio-wide semantic ownership.

### 4.1 Source

**Role:** identifies the originating source of the lecture, sermon, talk, or supporting evidence.

Required where source identity is material to the review.

The source shall retain relevant identity, authority, provenance, and version information according to applicable ECRA semantics.

### 4.2 Acquired Artifact

**Role:** preserves the representation actually used by the application.

Examples include:

- transcript file;
- extracted text;
- retrieved web artifact;
- document snapshot.

The artifact shall be distinguishable from the abstract source.

Where historical reproducibility is required, prior artifact versions or sufficient historical copies/lineage shall be retained subject to applicable permissions.

### 4.3 Claim

**Role:** represents a substantive proposition extracted from or supplied about the source material.

A claim shall have stable identity and traceability to its source location or derivation.

Claims may be:

- factual;
- historical;
- textual;
- interpretive;
- theological/doctrinal;
- normative;
- attributed;
- reviewer-supplied.

The classification does not determine the claim's truth status.

### 4.4 Evidence

**Role:** represents material used to assess a claim.

Evidence shall have sufficient provenance and source-location information to support inspection and audit.

Evidence may itself be associated with other claims. A chain of claims and evidence shall remain traversable.

### 4.5 Claim–Evidence Relationship

**Role:** explicitly represents how evidence bears on a claim.

The relationship shall distinguish at least the supported assessment categories needed by the workflow rather than relying on textual implication.

The relationship shall preserve source, target, type, provenance, and lifecycle information where applicable.

### 4.6 Source Location

**Role:** identifies where a claim or evidence item occurs.

Depending on the source, a location may include:

- transcript timestamp;
- paragraph;
- page;
- section;
- heading;
- table or figure;
- quotation boundaries;
- document offset;
- web locator associated with a preserved/retrieved artifact.

### 4.7 Provenance

**Role:** records origin, derivation, transformation, review, and other material processing history.

Provenance shall cover material user actions such as claim selection, correction, exclusion, evidence association, and assessment.

### 4.8 Assessment / Evaluation Result

**Role:** represents the structured outcome of reviewing available evidence against a claim.

The result shall preserve uncertainty, limitations, and relevant evidence relationships.

It shall not be represented as an unconditional truth assertion when the evidence does not justify that interpretation.

### 4.9 Integrity, Authenticity, and Authority Information

These properties may participate in source and evidence assessment.

They shall remain distinct:

- integrity concerns whether the represented artifact is intact according to the applicable integrity mechanism;
- authenticity concerns the source/artifact's identity or origin according to the applicable mechanism;
- authority concerns the source's standing or relevance for the question under review.

None of these properties alone establishes substantive truth.

### 4.10 Reviewer Action / Correction Provenance

Material reviewer changes are represented through provenance and lifecycle/version semantics rather than by creating a new ECRA root type.

A correction should preserve the prior state where historical reconstruction is required.

## 5. Relationship Requirements

The slice requires explicit relationships including, as applicable:

| Relationship purpose | Source | Target | Direction | Notes |
|---|---|---|---|---|
| claim origin | Claim | Source location / originating artifact | Claim → origin | Preserves where the claim came from |
| evidence origin | Evidence | Source/artifact/location | Evidence → origin | Preserves evidence provenance |
| evidence bearing | Evidence | Claim | Evidence → Claim | Direction shall follow the authoritative relationship semantics used by the implementation |
| claim/evidence assessment | Assessment | Claim/evidence context | Assessment → subject/context | Assessment remains distinct from evidence |
| provenance association | Provenance record | governed subject | Provenance → subject | Uses approved provenance semantics |
| claim derivation | Claim | preceding claim/evidence chain | Claim → predecessor | Used when a claim is derived from another reviewed proposition |

The concrete relationship type names, domain/range, multiplicity, and serialization are governed by the applicable ECRA specifications. This slice does not invent a competing relationship ontology.

### 5.1 Relationship Multiplicity

The workflow shall support:

- zero or more evidence items for a claim;
- multiple evidence items with different assessment bearings;
- one evidence item associated with multiple claims;
- claims without currently available evidence;
- evidence chains with multiple intermediate propositions.

### 5.2 Evidence Chains

When a source or evidence item is identified through a chain of claims and evidence, the chain shall be preserved.

The application shall not imply that support for one relationship proves every intermediate claim.

Each material intermediate claim and evidence relationship may be assessed independently.

Where a chain supplies a source for a later claim, the report shall identify the chain-derived origin rather than presenting the source as directly established by the later claim alone.

## 6. Evidence and Assessment Requirements

### 6.1 Evidence Bearing

The slice shall support the following review outcomes where applicable:

- supported by available evidence;
- contradicted by available evidence;
- partially supported or qualified;
- unresolved or insufficiently evidenced.

These are evidence-review outcomes, not universal truth labels.

### 6.2 Conflicting Evidence

When credible or otherwise relevant evidence conflicts, the application shall preserve the conflict.

It shall not silently select one item merely because it was discovered first, entered first, or supplied by a particular user.

The report should identify:

- the conflicting evidence;
- the source of each item;
- relevant source characteristics;
- the relationship of each item to the claim;
- the resulting uncertainty or unresolved status.

### 6.3 Interpretive and Theological Claims

Interpretive and theological claims may require a different evidentiary basis from straightforward empirical claims.

The application shall therefore avoid forcing every claim into a binary factual classification.

Where multiple interpretations are materially plausible, the reviewer may record multiple interpretations or mark the claim as ambiguous.

The system shall not silently select one interpretation.

### 6.4 Ambiguous Claims

If a claim is ambiguous such that fair evaluation depends on missing context, the application shall:

1. identify the ambiguity;
2. preserve the source context;
3. avoid presenting a single interpretation as established;
4. optionally present plausible interpretations for reviewer selection;
5. evaluate the selected interpretation separately where evidence permits.

For example, an isolated statement such as “Kill everyone” may have materially different meanings depending on whether its surrounding context concerns people, animals, pests, fiction, quotation, metaphor, or another subject. The application should preserve the surrounding context rather than enabling an evaluator to make a contextless conclusion.

### 6.5 Excluded Text

If a reviewer excludes a portion of source text from assessment, the result should preserve:

- the excluded text or a reference to it;
- its source location;
- the reason for exclusion;
- the surrounding context needed to understand the exclusion.

This is intended to reduce contextless reuse of partial statements.

### 6.6 Human Corrections

A material human correction to an extracted or previously reviewed claim shall:

- preserve the prior state;
- record the revised state;
- record who and when;
- record justification;
- be reassessed where the correction changes substantive meaning;
- preserve the previous assessment as historical rather than silently replacing it.

A human correction shall not become evidentiary merely because a reviewer entered it.

### 6.7 Partial Inputs

If only part of the source or evidence corpus is available, the application may produce a partial result.

The report shall clearly identify:

- what was evaluated;
- what was unavailable or excluded;
- material input-quality limitations;
- claims or evidence not evaluated;
- uncertainty introduced by incomplete inputs.

### 6.8 Integrity and Source State

A successfully verified artifact integrity state shall not be interpreted as evidence that the content is true.

Likewise, an authentic source is not necessarily authoritative for every question, and an authoritative source may still contain claims requiring independent evaluation.

## 7. Provenance and Traceability

### 7.1 Required Provenance

Where material to the workflow, provenance shall capture:

- source identity;
- artifact identity;
- acquisition time and method;
- source version/revision;
- claim origin;
- selected text span;
- evidence origin;
- evidence version;
- relationship creation/modification;
- assessment origin;
- reviewer actions;
- corrections and exclusions;
- relevant transformations.

### 7.2 Traceability Traversal

The reference application shall support traversal of a path such as:

```text
Claim
  → source location
  → originating artifact
  → source
  → evidence
  → evidence source/location
  → assessment
  → provenance
```

For chain-derived evidence:

```text
Claim
  → intermediate claim/evidence relationship
  → intermediate source
  → downstream evidence
  → assessment
```

The application shall preserve enough information for the reviewer to inspect the path.

### 7.3 Versioning and Historical Reconstruction

Multiple versions of a source, artifact, claim, or assessment may coexist.

When a newer source replaces an older source:

- the prior version shall not be silently discarded where historical reconstruction is required;
- prior claims and assessments shall remain attributable to the prior source state;
- a revised source may trigger reassessment;
- prior reports shall remain reconstructable.

When a claim changes after assessment, the prior claim and assessment shall be preserved, and the stale assessment shall be marked superseded or otherwise invalid for the revised claim.

Concrete retention and storage mechanisms remain implementation concerns.

## 8. Input/Output Contracts

### 8.1 Logical Input — `LectureClaimReviewRequest`

The logical request shall support, as applicable:

```text
LectureClaimReviewRequest
+-- source reference or supplied artifact
+-- source metadata
+-- reviewer context
+-- optional reviewer-selected claims
+-- optional evidence sources
+-- review scope
+-- processing options
```

The contract is logical and technology-independent.

### 8.2 Review Scope

The review scope may identify:

- entire transcript;
- selected sections;
- selected claims;
- selected text spans;
- selected evidence corpus.

A selected span is an application/UI input mapped to ordinary claim and source-location semantics; it does not require a specialized semantic-core capability.

### 8.3 Logical Output — `LectureClaimReviewResult`

The logical result shall support:

```text
LectureClaimReviewResult
+-- reviewed source/artifact
+-- claim set
+-- claim classifications where recorded
+-- evidence set
+-- claim/evidence relationships
+-- assessments
+-- uncertainty and limitations
+-- provenance
+-- traceability
+-- version/history references
+-- report representation
```

### 8.4 Incomplete Results

The result shall support partial completion.

A failed evidence retrieval shall not require discarding claims and evidence that were successfully processed.

Failures and omissions shall be represented explicitly.

### 8.5 Deterministic Structural Validation

The application shall deterministically validate structural conditions such as:

- required identity;
- valid source/artifact references;
- required relationship endpoints;
- valid source locations where applicable;
- consistent version references;
- required provenance for material actions.

Semantic conclusions remain evidence-review results and shall not be reduced to structural validation.

## 9. UI Demonstration

The minimum UI shall support the following workflow.

### 9.1 Source Intake

The reviewer can:

- upload or select a transcript;
- inspect source metadata;
- inspect acquisition state;
- open/read the originating artifact where permitted.

### 9.2 Claim Review

The reviewer can:

- inspect candidate claims;
- select a text span;
- edit or correct a claim;
- add a claim;
- classify a claim;
- mark ambiguity;
- exclude a statement with a reason.

### 9.3 Evidence Review

The reviewer can:

- inspect evidence items;
- open/read source material where permitted;
- inspect source location;
- inspect version;
- inspect integrity/authenticity/authority information;
- associate evidence with one or more claims.

### 9.4 Relationship and Assessment

The reviewer can inspect:

- evidence bearing;
- support/contradiction/qualification/unresolved state;
- uncertainty;
- conflicting evidence;
- reviewer justification;
- provenance.

### 9.5 Traceability

The reviewer can navigate:

```text
Claim ↔ Source ↔ Artifact ↔ Evidence ↔ Assessment ↔ Provenance
```

and inspect intermediate chain relationships where present.

### 9.6 Report View

The report shall show enough context to prevent misleading extraction of isolated statements.

At minimum it should show:

- claim text;
- source location;
- selected text;
- excluded text and reason where applicable;
- relevant surrounding context;
- claim classification;
- evidence;
- evidence source/location;
- assessment;
- uncertainty;
- provenance;
- version state;
- unresolved questions.

## 10. Negative and Boundary Cases

### 10.1 Missing Transcript

Expected behavior:

- identify missing input;
- do not generate substantive claim assessments;
- provide a clear input failure state.

### 10.2 Malformed or Partial Transcript

Expected behavior:

- process valid portions where feasible;
- identify missing or malformed portions;
- preserve input-quality limitations.

### 10.3 No Substantive Claims

A transcript containing only greetings, rhetorical language, personal preference, or other non-substantive material may yield no reviewable claims.

The result should explain the classification/exclusion rather than fabricating claims.

### 10.4 Opinion or Prediction

Opinion or prediction shall not be silently assessed as a factual claim.

It may be classified or excluded while preserving the relevant context.

### 10.5 Ambiguous Statement

Preserve context, identify ambiguity, and avoid silently choosing an interpretation.

### 10.6 Insufficient Evidence

The claim remains unresolved or insufficiently evidenced.

The application shall not infer contradiction merely because supporting evidence was not found.

### 10.7 Conflicting Evidence

Preserve both sides of the conflict and represent the resulting uncertainty.

### 10.8 Inaccessible Evidence

Mark the evidence as unavailable/inaccessible and preserve the reason where known.

The claim may remain unresolved.

### 10.9 Changed Source

If a source changes after review:

- preserve the prior source/artifact version where permitted;
- retain prior claim/assessment lineage;
- identify the newer version;
- allow reassessment.

### 10.10 Duplicate Evidence

Duplicate representations of the same evidence should remain distinguishable from genuinely distinct evidence while avoiding accidental double-counting in application-level assessment logic.

### 10.11 Incorrect Automated Extraction

Preserve:

- original candidate;
- corrected claim;
- reviewer;
- timestamp;
- justification;
- processing provenance.

### 10.12 User-Supplied Source Metadata

If supplied metadata is itself substantive, it may be represented as a claim/assertion.

It shall not become an underlying source of information merely because the user supplied it.

### 10.13 Claim Changed After Assessment

The application shall:

- preserve the prior claim;
- preserve the prior assessment;
- record the revised claim;
- mark the prior assessment stale/superseded as appropriate;
- require or permit reassessment.

### 10.14 Excluded Portion

The report shall preserve the excluded portion and reason when necessary to understand the evaluated statement.

### 10.15 Chain-Derived Evidence

Preserve the chain and identify the source reached through it.

Do not imply that every intermediate claim is supported merely because a downstream source was found.

### 10.16 Partial Processing Failure

Successfully processed claims/evidence shall remain available.

The result shall identify failed portions and their effect on completeness.

### 10.17 Round-Trip Failure

If machine representation cannot be read back into a logically equivalent model, the implementation shall report a representation/conformance failure rather than silently dropping semantic information.

## 11. Acceptance Criteria

The following acceptance criteria are required for VS-R01 completion.

| ID | Acceptance criterion |
|---|---|
| AC-R01-01 | A reviewer can provide a lecture/sermon transcript and obtain a registered source/artifact representation. |
| AC-R01-02 | The application can identify or accept substantive claims while preserving source locations. |
| AC-R01-03 | A reviewer can select a source-text portion as the basis of a claim through the UI. |
| AC-R01-04 | Material claim corrections preserve prior state, reviewer provenance, and justification. |
| AC-R01-05 | Claims can be classified without the classification being treated as a truth judgment. |
| AC-R01-06 | Evidence can be registered with source, artifact, location, version, and relevant provenance information. |
| AC-R01-07 | Evidence can be associated explicitly with one or more claims. |
| AC-R01-08 | The application represents support, contradiction, qualification/partial support, and unresolved/insufficient evidence where applicable. |
| AC-R01-09 | Conflicting evidence is preserved and exposed rather than silently collapsed. |
| AC-R01-10 | Ambiguous claims preserve relevant context and do not receive a silently selected interpretation. |
| AC-R01-11 | Human corrections and material human evaluations retain provenance and evidence-backed justification. |
| AC-R01-12 | Evidence chains remain traversable and do not imply support for every intermediate proposition automatically. |
| AC-R01-13 | Partial inputs can produce a partial result with explicit limitations and unevaluated portions. |
| AC-R01-14 | Source/artifact version changes preserve historical review lineage where permitted. |
| AC-R01-15 | A claim change after assessment preserves the prior assessment and prevents it from being silently treated as the assessment of the revised claim. |
| AC-R01-16 | Reviewers can open/read originating source or artifact material subject to access restrictions. |
| AC-R01-17 | The UI exposes claim, evidence, relationship, location, provenance, assessment, and uncertainty information needed to demonstrate the workflow. |
| AC-R01-18 | The generated report preserves enough context to distinguish selected and excluded text and explains material exclusions. |
| AC-R01-19 | Integrity, authenticity, and authority information remain distinct from substantive assessment. |
| AC-R01-20 | Machine representation round-trip preserves logical semantic identity, relationships, provenance, traceability, and other required information. |
| AC-R01-21 | Structural validation detects invalid identities, references, relationship endpoints, and other required contract violations deterministically. |
| AC-R01-22 | A complete end-to-end UI workflow can be demonstrated from source intake through report inspection. |
| AC-R01-23 | The implementation can preserve and report incomplete, unavailable, or failed evidence retrieval without discarding valid completed work. |
| AC-R01-24 | Excluded or non-reviewable statements are represented with sufficient explanation and context to prevent misleading isolated reuse. |

## 12. Reference-Core versus Application Responsibilities

### 12.1 Shared ECRA Reference Core

The shared core shall provide only capabilities demonstrated by this and the other selected P0 slices to be reusable and necessary, including:

- stable semantic identity;
- source/artifact representation;
- claim representation;
- evidence representation;
- typed relationship representation;
- assessment representation;
- provenance and traceability;
- source-state/integrity/authenticity/authority metadata boundaries;
- machine representation and semantic round-trip support;
- persistence/storage abstractions;
- applicable validation/verification integration boundaries.

### 12.2 VS-R01 Application Layer

The application layer owns:

- lecture/sermon transcript ingestion UX;
- claim extraction suggestions;
- claim classification UX;
- evidence discovery/search connectors;
- domain-specific source selection;
- reviewer workflows;
- ambiguity presentation;
- context display;
- report presentation;
- user comments and review controls;
- source-reading UI.

These capabilities shall remain replaceable and shall not be promoted into the ECRA semantic core merely because VS-R01 needs them.

### 12.3 External Dependencies

Potential external dependencies include:

- document/text extraction;
- source retrieval;
- search services;
- external repositories;
- authentication/access-control services.

The slice does not prescribe a particular provider.

## 13. Capability Coverage

VS-R01 maps directly to the approved capability matrix for:

- source material registration;
- acquired artifact preservation;
- source location/citation;
- stable semantic identity;
- claim representation;
- evidence representation;
- evidence-to-claim association;
- typed relationship representation;
- support/contradiction/qualification assessment;
- unresolved/uncertainty representation;
- provenance representation;
- traceability traversal;
- source version/revision state;
- artifact integrity information;
- source authenticity where applicable;
- source authority information;
- transformation provenance where processing occurs;
- machine-readable representation;
- semantic round-trip preservation;
- structured assessment result;
- report generation;
- UI source/claim/evidence/relationship/provenance/assessment/report inspection;
- validation/conformance and verification integration boundaries;
- deterministic structural validation;
- reproducible processing records.

### 13.1 No New Core Promotion from R01 Alone

The following remain application-level or deferred unless evidence from additional slices justifies promotion:

- generalized religious knowledge models;
- theological reasoning engines;
- generalized source-ranking engines;
- universal evidence discovery;
- generalized interpretation engines;
- generalized semantic inference;
- universal workflow orchestration;
- domain-specific ontologies.

If implementation evidence reveals a missing shared capability, the capability matrix shall be versioned through its approved promotion lifecycle rather than silently diverging.

## 14. Security, Privacy, and Operational Considerations

### 14.1 Sensitive Material

Lecture/sermon material may include private recordings, unpublished transcripts, personal information, copyrighted material, or restricted source material.

The application shall respect applicable access restrictions.

### 14.2 Provenance Integrity

Material review history shall be protected from silent alteration.

The implementation should preserve an auditable history of:

- source changes;
- claim changes;
- evidence changes;
- reviewer actions;
- assessment changes.

### 14.3 Reproducibility

Released or baselined results should remain reconstructable from retained source/artifact versions or sufficient historical representations where permitted.

### 14.4 Storage Durability

The reference implementation shall use an appropriate durability mechanism for its agreed storage SLA, including mechanisms such as redundancy, replication, recoverable historical copies, or deterministic reconstruction from retained source and derived material as justified by implementation design.

The concrete SLA and storage technology are not prescribed by this slice.

### 14.5 External Dependency Failure

External search/retrieval failures shall not corrupt already registered evidence or assessments.

The application shall isolate external-service failure and represent resulting incompleteness.

### 14.6 Observability

The implementation should provide sufficient operational records to diagnose:

- failed ingestion;
- failed extraction;
- failed evidence retrieval;
- representation errors;
- assessment processing errors;
- source-version mismatches.

The level of observability shall remain proportionate to the reference implementation.

## 15. Explicit Exclusions

VS-R01 does not require:

- automated theological adjudication;
- doctrinal truth scoring;
- religious authority ranking;
- universal interpretation or hermeneutics engines;
- automated determination of religious truth;
- universal web search/crawling;
- generalized evidence curation;
- generalized source credibility scoring;
- universal semantic reasoning;
- generalized graph analytics;
- generalized workflow/orchestration;
- distributed microservices;
- generalized multi-tenancy;
- a domain-specific religious knowledge graph;
- implementation of all ECRA semantic constructs.

The application may use domain-specific services or knowledge sources where useful, but they remain replaceable application dependencies unless later evidence promotes a capability through the approved lifecycle.

## 16. Implementation and Evolution Constraints

The implementation shall preserve the evolutionary architecture principles established by the approved capability matrix.

### 16.1 Semantic Contract Stability

The semantic model shall remain independent of:

- UI framework;
- persistence technology;
- search provider;
- retrieval provider;
- processing engine;
- deployment topology.

### 16.2 Replaceability

Evidence discovery, text extraction, retrieval, and presentation components should be replaceable through explicit boundaries.

### 16.3 Cohesive Responsibilities

Claim modeling, evidence modeling, provenance, assessment, source retrieval, and presentation shall have clear responsibilities.

### 16.4 Future Decomposition

The implementation should permit future separation of source ingestion, evidence retrieval, assessment, reporting, and other responsibilities into separate processes or services without changing ECRA semantic contracts where reasonably foreseeable.

No microservice architecture is required for VS-R01.

### 16.5 Determinism and Reproducibility

Structural validation and representation operations shall be deterministic.

Where evidence retrieval or external services are inherently time-dependent, the application shall preserve enough provenance and version information to make the resulting review state reproducible to the extent reasonably possible.

## 17. Design and Implementation Traceability

This specification is derived from and shall remain traceable to:

1. Approved ECRA Reference Application — Vertical Slice Portfolio.
2. Approved ECRA Reference Implementation — Cross-Slice Capability Matrix.
3. Approved ECRA P0 Vertical Slice Specification Framework.
4. Approved Gen1 Claim and Evidence Requirements.
5. Approved Gen1 Context and Evaluation Requirements.
6. Approved Gen1 Traceability and Engineering Requirements.
7. Applicable ECRA-1200 Architecture Description Language boundaries.
8. Applicable ECRA-1200 detailed-design foundation.

The specification does not supersede any normative ECRA document.

Where this slice needs a semantic capability not established by the cited authoritative sources, the capability shall be identified as an implementation/design gap rather than silently promoted into the normative ECRA model.

## 18. Verification Strategy

Verification shall include:

### 18.1 Contract Tests

Verify:

- required request/result structures;
- identity requirements;
- valid references;
- relationship endpoint integrity;
- version consistency;
- incomplete-result handling.

### 18.2 Semantic Integration Tests

Verify:

- claim/evidence representation;
- explicit evidence relationships;
- support/contradiction/qualification/unresolved assessment representation;
- provenance;
- traceability;
- distinction between source properties and substantive assessment.

### 18.3 Negative Tests

Verify:

- missing input;
- malformed transcript;
- inaccessible evidence;
- conflicting evidence;
- ambiguous claims;
- insufficient evidence;
- changed source;
- incorrect extraction;
- stale assessment after claim revision;
- partial processing failure.

### 18.4 Reproducibility Tests

Verify that a baselined review can be reconstructed from retained source/artifact versions and recorded processing/provenance information, subject to permitted retention.

### 18.5 Representation Round-Trip Tests

Verify:

```text
Logical VS-R01 semantic state
    → machine representation
    → reconstructed logical state
```

The reconstructed state shall be logically equivalent with required identity, relationships, provenance, traceability, assessment, and version semantics preserved.

Byte-for-byte serialization equality is not required.

### 18.6 UI End-to-End Test

Demonstrate:

```text
Source intake
    → claim review
    → evidence review
    → relationship/assessment
    → traceability
    → report
```

The UI demonstration is part of slice completion.

## 19. Deliverable and Completion Definition

VS-R01 is complete only when:

1. the logical workflow is implemented;
2. required shared-core capabilities are available;
3. application-specific responsibilities are implemented;
4. the complete workflow is demonstrable through the UI;
5. acceptance criteria are verified;
6. negative and boundary cases are tested;
7. semantic machine representation round-trip is verified;
8. provenance and traceability are demonstrated;
9. relevant capability-matrix evidence is recorded;
10. the implementation remains within the approved reference-core boundary.

Implementation completion does not require implementing excluded or deferred ECRA capabilities.

## 20. Open and Deferred Items

The following remain intentionally open or deferred:

1. concrete evidence-discovery provider(s);
2. concrete source-retrieval mechanisms;
3. detailed source-authority metadata vocabulary beyond applicable normative semantics;
4. concrete storage technology and SLA parameters;
5. detailed UI technology;
6. generalized ambiguity/interpretation assistance;
7. generalized religious or historical knowledge models;
8. generalized search and source-ranking infrastructure;
9. broader capability promotion based on evidence from later P0 slices.

These items shall be resolved only when implementation evidence or an authoritative specification requires them.

## 21. Status

This specification is currently **REVIEW** and is intended for review before implementation of the VS-R01 reference-application vertical slice.
