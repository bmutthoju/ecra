# ECRA Reference Application — VS-B01 Company Due Diligence

> Status: REVIEW
> Authority: ENGINEERING / INFORMATIVE
> Generation: GEN1
> Scope: Detailed P0 vertical-slice specification for Company Due Diligence
> Matrix Basis: Approved ECRA Reference Implementation — Cross-Slice Capability Matrix
> Portfolio Basis: Approved ECRA Reference Application — Vertical Slice Portfolio

## 1. Purpose and Scope

### 1.1 Purpose

VS-B01 defines a claim-first, source-comparison workflow for reviewing material company claims against relevant evidence and producing a traceable due-diligence report.

The slice demonstrates that the reference implementation can handle a subject whose information is distributed across multiple source types, including company-provided material, public or regulatory records, independent sources, filings, reports, contracts, attestations, and other supplied evidence.

The system represents claims, sources, artifacts, evidence, relationships, assessments, provenance, limitations, and unresolved questions. It does not itself determine whether a company is trustworthy, investable, compliant, suitable, fraudulent, or otherwise fit for a downstream decision.

### 1.2 Intended Users

Primary users include:

- due-diligence reviewers;
- procurement or vendor reviewers;
- investors and research analysts;
- compliance and risk reviewers;
- journalists and researchers;
- authorized partnership or business reviewers.

The slice does not prescribe a legal, accounting, investment, procurement, or compliance methodology.

### 1.3 Workflow Boundary

The workflow begins with a target company or organizational subject, a defined review scope, and supplied or retrievable source material. It ends with material claims, explicit source/evidence associations, source comparisons, assessments, provenance, limitations, and a user-inspectable report.

### 1.4 Source-Comparison Principle

Company statements, external statements, public records, filings, certifications, attestations, historical records, and user-supplied material may have different provenance and authority characteristics.

The system shall preserve these distinctions. Source type, provenance, authenticity, authority, recency, completeness, or integrity shall not be silently converted into substantive truth judgments.

### 1.5 Non-Goals

VS-B01 does not establish:

- investment or procurement recommendations;
- credit ratings or company reputation scores;
- legal or accounting opinions;
- regulatory certification;
- autonomous fraud or misconduct determination;
- universal source-credibility or source-ranking engines;
- unrestricted web crawling or a general search engine;
- autonomous company surveillance;
- universal company knowledge graphs;
- generalized organization-identity inference;
- generalized workflow orchestration;
- distributed deployment architecture;
- a new ECRA semantic root type for Company, Organization, Risk, or Due Diligence.

Company-specific structures remain application-level unless an authoritative ECRA specification establishes otherwise.

### 1.6 Assumptions and Limitations

Sources may be complete or partial, current or historical, accessible or inaccessible, independently verified or not verified, and internally consistent or conflicting.

The result may therefore be incomplete. Missing information shall be represented as a limitation rather than silently filled.

---

## 2. Scenario and Preconditions

### 2.1 Primary Scenario

A reviewer is assessing a company for a defined business purpose. The reviewer identifies the target, scope, questions, and available sources. The application:

1. registers sources and artifacts;
2. identifies material claims;
3. records claim source locations;
4. identifies relevant evidence;
5. registers evidence and its provenance;
6. associates evidence explicitly with claims;
7. compares material claims across sources;
8. records support, contradiction, qualification, or unresolved states;
9. records versions, provenance, limitations, and reviewer actions;
10. generates a traceable report.

### 2.2 Example Review Questions

The application may support questions such as:

- What does the company state about a material product, capability, or business fact?
- What do relevant public or regulatory records state?
- Do independent sources materially differ from company statements?
- Which claims have supporting evidence?
- Which claims have contradictory or qualifying evidence?
- Which claims remain unresolved?
- Which source versions were used?
- What evidence and provenance underlie each assessment?

These are workflow examples, not a universal due-diligence methodology.

### 2.3 Required Inputs

The minimum workflow input is:

- a target company or organizational subject identifier sufficient to establish review scope;
- a review scope/context;
- at least one source/artifact or an explicit supported acquisition request.

The exact representation of an organizational subject is application-specific unless an applicable ECRA specification defines a canonical representation.

### 2.4 Optional Inputs

Optional inputs may include:

- company name and aliases;
- jurisdiction;
- registration identifiers;
- company documentation;
- filings and public records;
- contracts or proposals;
- product documentation;
- certifications or attestations;
- financial disclosures;
- historical source versions;
- reviewer questions;
- materiality criteria;
- review period;
- reviewer notes;
- pre-existing claims or evidence.

Optional metadata does not become evidence merely because it was supplied.

### 2.5 Source Availability

A source may be available, partial, inaccessible, withdrawn, changed, historical, or supplied without independent verification. The system shall preserve the applicable state and shall not represent inaccessible material as reviewed evidence.

---

## 3. End-to-End Workflow

```text
Target company + diligence scope
    ↓
Source intake / registration
    ↓
Identify material claims
    ↓
Locate claims in source material
    ↓
Identify relevant evidence
    ↓
Register evidence and source/artifact state
    ↓
Associate evidence with claims
    ↓
Compare materially relevant claims across sources
    ↓
Assess support / contradiction / qualification / unresolved state
    ↓
Record provenance, versions, limitations, and reviewer actions
    ↓
Generate due-diligence report
    ↓
Reviewer inspection and follow-up
```

### 3.1 Review Scope

The reviewer establishes target subject, purpose, review period where applicable, material questions, source corpus, and optional materiality criteria.

Scope is context; it is not automatically a claim about the company.

### 3.2 Source and Artifact Registration

Each material source shall have applicable:

- source identity;
- source type or role;
- artifact identity;
- acquisition state;
- version/revision;
- location;
- provenance;
- integrity information;
- authenticity information;
- authority information where available.

Source type or role provides context and does not automatically determine the substantive assessment.

### 3.3 Claim Identification

Claims may be suggested from company documents, filings, reports, proposals, product descriptions, certifications, contracts, public records, or other material.

Reviewers shall be able to inspect, correct, accept, reject, or supplement candidate claims. Claim origin and source location shall be preserved.

### 3.4 Claim Qualification

Claims may be descriptively classified as company-stated, externally attributed, factual, historical, financial/operational, product/service, compliance-related, ownership/organizational, certification/attestation, opinion/prediction, ambiguous, or otherwise useful to the review.

Classification is descriptive and is not a truth judgment.

### 3.5 Evidence Identification and Registration

Relevant evidence may include another statement in the same source, an independent source, a filing or public record, a historical source, a contract, an attestation, an operational record, reviewer-supplied material, or an explicit evidence chain.

Evidence discovery may be automated by the application, but evidence associations shall remain explicit and inspectable.

### 3.6 Claim/Evidence Association

The implementation shall support:

- multiple evidence items for one claim;
- one evidence item relevant to multiple claims;
- partial support;
- conflicting evidence;
- evidence chains;
- claims with no currently identified evidence.

Evidence relevance shall not be inferred solely from co-location in a document.

### 3.7 Source Comparison

For each material claim, the reviewer should be able to inspect:

- claim wording;
- originating source and location;
- source version;
- relevant statements in other sources;
- associated evidence;
- support/contradiction/qualification/unresolved state;
- relevant source properties;
- provenance and limitations.

Source comparison is an application analysis/presentation capability. It does not require a generalized source-ranking engine.

### 3.8 Assessment

The assessment representation shall support:

- supported;
- contradicted;
- partially supported or qualified;
- unresolved or insufficient evidence.

Conflicting evidence shall remain visible. Missing evidence shall not automatically become contradiction.

### 3.9 Human Review and Correction

Reviewers may correct claims, add claims, change evidence associations, identify missing sources, mark ambiguity, revise assessments, and add review notes.

Material changes shall preserve reviewer identity where available, timestamp, prior state, revised state, justification, supporting evidence where applicable, and provenance.

### 3.10 Report Generation

The report shall show what was reviewed, material claims, source origins, source comparisons, evidence, assessments, conflicts, limitations, versions, provenance, and unresolved questions.

It shall not present an aggregate company truth score unless separately established by an applicable specification.

---

## 4. Semantic Object Requirements

### 4.1 Review Context

Represents target subject, diligence scope, review period, criteria, source corpus, and applicable reviewer context.

It reuses applicable ECRA context semantics and is not a new portfolio-wide root type.

### 4.2 Source

Represents an identifiable origin from which information is obtained or attributed.

It has stable identity and applicable metadata, provenance, source-state, and authority information.

### 4.3 Acquired Artifact

Represents material actually obtained by the system. It preserves stable identity, acquisition provenance, applicable version/revision, integrity information where available, and relationship to its source.

### 4.4 Claim

Represents an identifiable proposition submitted for review. It preserves stable identity, proposition content, source location where applicable, provenance, version/lineage, evidence relationships, and assessment state.

A company-stated claim remains a claim even when the source is authentic or authoritative.

### 4.5 Evidence

Represents information relevant to determining whether, or to what extent, a claim is established.

It preserves stable identity, source, artifact, location, version/lineage where applicable, provenance, and applicable integrity/authenticity/authority information.

### 4.6 Claim–Evidence Relationship

Represents an explicit association between evidence and the claim(s) for which it is relevant.

Concrete relationship names, domain/range rules, and serialization remain governed by authoritative ECRA relationship semantics.

### 4.7 Source Location

Identifies where a claim or evidence item occurs within a source or artifact, such as page, section, paragraph, span, timestamp, table, record, or other supported location.

A location is a reference into a source/artifact, not a replacement for its identity.

### 4.8 Assessment / Evaluation Result

Represents the assessment of a claim relative to available evidence. It remains distinct from integrity, authenticity, authority, provenance completeness, source type, and reviewer affiliation.

Results may be incomplete or unresolved.

### 4.9 Reviewer Action / Correction Provenance

Material actions shall distinguish application-generated state, reviewer-confirmed state, reviewer-corrected state, rejected candidates, added claims/evidence, and revised assessments.

### 4.10 Integrity, Authenticity, and Authority

The Gen1 boundary shall be preserved:

- integrity concerns whether acquired information has been altered or corrupted under the applicable mechanism;
- authenticity concerns whether source/artifact identity or attribution is genuine under the applicable mechanism;
- authority concerns the basis for considering a source appropriate for the relevant evaluation.

These properties are not interchangeable and do not automatically determine claim truth.

---

## 5. Relationship Requirements

### 5.1 Required Relationship Families

The workflow requires relationships corresponding to:

- review-context association with the target subject;
- claim origin from source/artifact;
- evidence origin from source/artifact;
- evidence relevance/bearing on claim;
- claim derivation where applicable;
- provenance association;
- version/lineage where applicable;
- assessment association.

Concrete names shall be taken from authoritative ECRA relationship semantics.

### 5.2 Identity

Every material relationship shall have identifiable semantic endpoints. Presentation labels, URLs, database rows, or textual similarity shall not substitute for semantic identity.

### 5.3 Multiplicity

The slice supports:

- zero or more evidence items per claim;
- one evidence item relevant to multiple claims;
- multiple sources relevant to one claim;
- multiple claims from one source;
- multiple source/artifact versions;
- multiple assessments across review revisions.

### 5.4 Conflicting Source Statements

Different sources may contain materially different statements about the same subject. Each statement, source, location, version, comparison relationship, assessment, and provenance shall remain represented.

The system shall not overwrite one statement with another merely because one source is newer, more authoritative, or preferred by a reviewer.

### 5.5 Evidence Chains

An evidence chain may be:

```text
Claim A
  → Claim / source statement B
  → Source / artifact C
  → Evidence D
```

The chain remains traversable. Evidence reached through a chain does not automatically establish every intermediate claim.

### 5.6 Version Relationships

When a source is revised, prior versions remain identifiable where retention permits; the new version has distinct version/lineage information; prior assessments remain associated with the source state on which they were based; affected claims may be reassessed.

---

## 6. Evidence and Assessment Requirements

### 6.1 Company-Provided Evidence

Company-provided material may be relevant evidence for statements about products, capabilities, commitments, disclosures, or operations.

The system shall record its provenance. It shall not infer that a self-reported statement is false because it is self-reported, nor true merely because it is self-reported.

### 6.2 External Evidence

External evidence may include public records, regulatory records, independent reports, customer or supplier documentation, third-party attestations, dated historical records, or other authorized material.

Source type remains explicit.

### 6.3 Support

Evidence may support a claim when it bears on the proposition in a way that supports the applicable assessment. The report shall identify the evidence and location.

### 6.4 Contradiction

Contradiction requires materially incompatible evidence relevant to the claim. It shall not be inferred merely because a source is silent, inaccessible, or not preferred.

### 6.5 Qualification / Partial Support

Evidence may support only part of a broad claim. The application shall allow supported and unsupported portions, qualifying conditions, evidence, and locations to be distinguished.

### 6.6 Unresolved / Insufficient Evidence

A claim may remain unresolved because evidence is insufficient, relevant sources are unavailable, sources conflict without a resolved basis, source material is incomplete, or the scope is insufficient.

Absence of evidence shall not automatically become evidence of contradiction.

### 6.7 Conflicting Evidence

All materially relevant evidence remains represented with source provenance, version, location, and resulting uncertainty or qualification.

The application shall not silently select preferred evidence.

### 6.8 Materiality

Materiality criteria may be supplied as review context. They are not universal ECRA truth criteria.

### 6.9 Source Authority

Authority may depend on the review question, jurisdiction, source role, time, and other context. The implementation shall preserve authority information rather than hard-coding a universal source hierarchy.

### 6.10 Human Assessment

Human assessment changes shall preserve reviewer, timestamp, previous state, revised state, rationale, supporting evidence where applicable, and provenance.

### 6.11 Assessment Limitations

The result shall distinguish evidence, access, integrity, authenticity, authority, processing, scope, and substantive limitations rather than collapsing them into a generic confidence score.

---

## 7. Provenance and Traceability

### 7.1 Required Provenance

Preserve provenance for review creation, source registration, acquisition, source version, claim identification/correction, evidence discovery/registration/association, source comparison, assessment, reviewer actions, report generation, and applicable transformations.

### 7.2 Traceability Path

```text
Review Scope
   ↓
Claim
   ↓
Claim Source Location
   ↓
Artifact
   ↓
Source
   ↓
Evidence
   ↓
Evidence Source Location
   ↓
Assessment
   ↓
Provenance
```

The implementation shall support navigation through the material path needed to explain a result.

### 7.3 Source-Comparison Traceability

A comparison remains traceable to compared claims/statements, sources, artifacts, locations, versions, identifying processing/reviewer action, and resulting assessment.

### 7.4 Historical Reconstruction

Released or baselined reviews shall preserve sufficient information to reconstruct the review state subject to retention and access constraints. Later changes shall not silently rewrite historical results.

### 7.5 Claim Revision

When a material claim changes, preserve the prior state and assessment, record the revised claim and lineage, mark prior assessment stale/superseded where applicable, and permit reassessment.

### 7.6 Evidence Revision

When evidence changes, preserve the prior version where retained, register the new version, keep affected assessments traceable to the version used, and permit reassessment.

---

## 8. Input / Output Contracts

### 8.1 Review Request

Conceptually:

```text
CompanyDueDiligenceRequest
├── targetSubject
├── reviewScope
├── reviewPeriod [optional]
├── materialityCriteria [optional]
├── sourceInputs
├── initialClaims [optional]
├── reviewQuestions [optional]
└── reviewerContext [optional]
```

Exact programming-language representation is implementation-specific.

### 8.2 Source Input

Supports source reference, artifact or supported acquisition request, source metadata, version/revision, location, access state, and provenance.

### 8.3 Claim Input

Supports claim identity when known, claim content, source/artifact reference, source location, classification where available, provenance, and version/lineage.

### 8.4 Evidence Input

Supports evidence identity, source/artifact reference, location, version/lineage, content/reference, provenance, and applicable integrity/authenticity/authority information.

### 8.5 Result Contract

Conceptually:

```text
CompanyDueDiligenceResult
├── reviewContext
├── targetSubject
├── sources
├── artifacts
├── claims
├── evidence
├── relationships
├── assessments
├── sourceComparisons
├── limitations
├── provenance
├── traceability
└── report
```

### 8.6 Incomplete Results

Partial completion is supported. Failed retrievals, inaccessible sources, unresolved claims, or processing failures shall not require discarding successfully processed material.

### 8.7 Deterministic Structural Validation

Validate deterministically:

- required identities;
- valid references;
- valid relationship endpoints;
- source/artifact consistency;
- required locations where applicable;
- version-reference consistency;
- required provenance for material actions.

Structural validation remains distinct from substantive assessment.

### 8.8 Result Completeness

The result shall identify whether the review is complete within scope, partially complete, or incomplete because of source/access/processing limitations. An incomplete review shall not be presented as comprehensive.

---

## 9. UI Demonstration

### 9.1 Review Setup

Allow the reviewer to identify the target company, define scope and questions, optionally specify review period/materiality, and select or provide source material.

### 9.2 Source Intake

Allow inspection of registered sources, source role/type, artifact state, source version, access state, and originating material where permitted.

### 9.3 Claim Review

Allow inspection, acceptance/rejection, correction, addition, classification, ambiguity marking, and source-location navigation for claims.

### 9.4 Evidence Review

Allow inspection of evidence, source location, version, integrity/authenticity/authority information, and explicit association with claims.

### 9.5 Source Comparison View

The minimum comparison view shall show:

| Element | Demonstration |
|---|---|
| Claim | Material proposition under review |
| Origin | Source and location |
| Source version | Version/revision used |
| Comparison source | Other relevant source |
| Comparison statement | Relevant statement/evidence |
| Relationship | Support, contradiction, qualification, or unresolved relevance |
| Evidence | Evidence underlying the relationship |
| Assessment | Current assessment state |
| Limitations | Missing, inaccessible, conflicting, or incomplete material |
| Provenance | Origin of comparison and assessment |

Display order shall not imply that one source is preferred.

### 9.6 Assessment View

Show support, contradiction, qualification/partial support, unresolved/insufficient evidence, conflict, uncertainty, rationale, and provenance.

### 9.7 Traceability View

Allow navigation through:

```text
Claim ↔ Source ↔ Artifact ↔ Evidence ↔ Assessment ↔ Provenance
```

and between retained source versions.

### 9.8 Report View

Show review scope, target, material claims, source origins, comparisons, evidence, assessments, conflicts, limitations, source versions, provenance, unresolved questions, and follow-up evidence needs.

The report shall preserve sufficient context to prevent misleading extraction of isolated statements.

---

## 10. Negative and Boundary Cases

### 10.1 Missing Target

Reject or hold substantive processing and identify the missing scope information.

### 10.2 No Source Material

Represent the review as incomplete. Do not infer negative findings from the absence of sources.

### 10.3 Malformed Source

Preserve registration where possible, identify malformed portions, and avoid silently extracting unsupported claims.

### 10.4 Inaccessible Source

Identify the source and access limitation; do not represent it as reviewed evidence.

### 10.5 Conflicting Company and External Statements

Preserve each statement, source, location, version, conflict, and resulting assessment. Do not silently select one.

### 10.6 Conflicting External Sources

Preserve the conflict. Do not resolve it merely from source type unless an applicable rule establishes such a basis.

### 10.7 Source Silence

Distinguish no evidence found, source does not address the claim, source inaccessible, and incomplete search. Silence is not contradiction.

### 10.8 Duplicate Evidence

Distinguish duplicate representations from distinct evidence and avoid accidental double-counting at the application layer.

### 10.9 Historical or Outdated Source

Preserve date/version and relevance context. Do not silently represent historical material as current.

### 10.10 Changed Source

Preserve the previously used version where permitted, register the new version, preserve prior assessments, identify affected claims, and permit reassessment.

### 10.11 Unsupported Company Claim

Preserve the claim and evidence gap; represent unresolved/insufficient status where applicable; do not automatically mark it false.

### 10.12 Partial Support

Identify supported and unsupported portions, qualifying conditions, evidence, and locations.

### 10.13 Ambiguous Statement

Preserve the original wording and context, identify ambiguity, allow relevant interpretations to be evaluated separately, and do not silently choose one.

### 10.14 Incorrect Automated Extraction

Preserve candidate, corrected claim, reviewer information where available, correction rationale, and processing provenance.

### 10.15 User-Supplied Assertion

Preserve user-supplied provenance. Do not treat it as independently verified merely because it was supplied.

### 10.16 Claim Changed After Assessment

Preserve prior claim and assessment, record revised claim/lineage, mark prior assessment stale/superseded as applicable, and permit reassessment.

### 10.17 Evidence Changed After Assessment

Preserve prior evidence version and assessment where retention permits, then permit reassessment against the new evidence.

### 10.18 Source Identity Ambiguity

Do not silently merge organizations with similar names. Expose ambiguity and require sufficient identifying information.

### 10.19 Multiple Names or Aliases

Preserve historical/trade names and aliases as context. Do not silently merge distinct legal entities.

### 10.20 Evidence Chain

Preserve the chain and each intermediate step. Do not imply that all intermediate claims are established.

### 10.21 Partial Processing Failure

Retain successfully processed material and identify failed portions and their effect on completeness.

### 10.22 Round-Trip Failure

Report representation/conformance failure rather than silently dropping source, claim, evidence, relationship, provenance, or assessment information.

---

## 11. Acceptance Criteria

| ID | Acceptance criterion |
|---|---|
| AC-B01-01 | A reviewer can establish a company due-diligence review with a target and declared scope. |
| AC-B01-02 | Sources and acquired artifacts can be registered with stable identity and applicable provenance. |
| AC-B01-03 | Source version/revision and access state can be represented and inspected. |
| AC-B01-04 | Material claims can be identified or supplied with originating source locations. |
| AC-B01-05 | Claim classification remains descriptive and is not treated as truth. |
| AC-B01-06 | Evidence can be registered with source, artifact, location, version, and provenance. |
| AC-B01-07 | Evidence can be explicitly associated with one or more claims. |
| AC-B01-08 | Support, contradiction, qualification/partial support, and unresolved/insufficient states can be represented. |
| AC-B01-09 | Company-provided and external evidence remain distinguishable by provenance/source context. |
| AC-B01-10 | Material claims can be compared across source statements without silently overwriting or selecting a preferred source. |
| AC-B01-11 | Conflicting source statements and evidence remain represented and traceable. |
| AC-B01-12 | Source silence, unavailable sources, and insufficient evidence are distinguishable from contradiction. |
| AC-B01-13 | Materiality/review criteria can be represented as context without becoming universal truth criteria. |
| AC-B01-14 | Human claim corrections preserve prior state, reviewer provenance, and justification. |
| AC-B01-15 | Human assessment changes preserve prior and revised states and provenance. |
| AC-B01-16 | Evidence chains remain traversable without implying support for every intermediate proposition. |
| AC-B01-17 | Source changes preserve historical version lineage and prior assessment context where permitted. |
| AC-B01-18 | Claim changes after assessment preserve the prior claim and prevent silent reuse of its assessment for the revised claim. |
| AC-B01-19 | Reviewers can open/read originating source material subject to access restrictions. |
| AC-B01-20 | The UI exposes scope, claims, sources, evidence, comparisons, relationships, provenance, assessments, limitations, and report output. |
| AC-B01-21 | The report preserves enough context to distinguish company statements, external evidence, comparisons, and unresolved questions. |
| AC-B01-22 | Integrity, authenticity, and authority remain distinct from substantive assessment. |
| AC-B01-23 | Incomplete or failed retrieval does not discard successfully processed material and is visible in the result. |
| AC-B01-24 | Source identity ambiguity does not result in silent merging of distinct organizations. |
| AC-B01-25 | Historical/superseded source versions remain distinguishable from current state. |
| AC-B01-26 | Machine round-trip preserves identity, relationships, provenance, traceability, source/version state, and assessment information. |
| AC-B01-27 | Structural validation detects invalid identities, references, endpoints, and required provenance deterministically. |
| AC-B01-28 | A complete end-to-end UI workflow can be demonstrated from review setup through report inspection. |
| AC-B01-29 | Excluded, unavailable, or non-reviewable material is represented with sufficient explanation and context. |
| AC-B01-30 | The report identifies material evidence gaps and unresolved questions without converting absence of evidence into unsupported negative conclusions. |

---

## 12. Reference-Core versus Application Responsibilities

### 12.1 Shared Reference Core

The shared core shall provide only capabilities demonstrated as reusable and necessary across the P0 portfolio, including:

- stable semantic identity;
- source/artifact representation;
- source location/citation;
- claim representation;
- evidence representation;
- typed relationship representation;
- assessment representation;
- provenance and traceability;
- source-state/version handling;
- integrity/authenticity/authority metadata boundaries;
- machine representation and semantic round-trip;
- persistence/storage abstractions;
- validation/verification integration boundaries.

VS-B01 does not justify a new company-specific semantic root type.

### 12.2 Reusable Enabling Infrastructure

Potential reusable enabling infrastructure includes source/artifact version storage, source-location handling, deterministic structural validation, provenance capture, report assembly, and comparison-oriented application interfaces.

These remain cohesive and replaceable.

### 12.3 Application Layer

The B01 application owns:

- due-diligence workflow;
- target identification UX;
- review-scope configuration;
- review-question management;
- materiality configuration;
- company-specific source collection;
- source comparison presentation;
- claim extraction suggestions;
- evidence discovery;
- domain-specific source selection;
- reviewer workflow;
- alias handling UX;
- report presentation;
- follow-up evidence requests.

These shall not be promoted into the semantic core merely because B01 needs them.

### 12.4 External Dependencies

Potential external dependencies include public-record repositories, regulatory/filing repositories, document retrieval, search services, financial-data providers, certification registries, document extraction, and access-control services.

No provider is prescribed.

---

## 13. Capability Coverage

### 13.1 Demonstrated / Required Capabilities

B01 requires the approved matrix capabilities for:

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
- provenance;
- traceability traversal;
- source version/revision state;
- artifact integrity information;
- source authenticity where applicable;
- source authority information;
- transformation provenance;
- machine-readable representation;
- semantic round-trip;
- structured assessment result;
- report generation;
- UI inspection of source/claim/evidence/relationship/provenance/assessment/report;
- validation/conformance and verification integration;
- deterministic structural validation;
- reproducible processing records.

### 13.2 Application-Specific Capabilities

The following remain application-level:

- company review setup;
- source-comparison presentation;
- materiality configuration;
- company/source alias handling;
- domain-specific source discovery;
- source corpus selection;
- company-provided versus external source presentation.

### 13.3 No New Core Promotion from B01 Alone

B01 does not justify:

- universal source-ranking infrastructure;
- universal company knowledge models;
- autonomous risk scoring;
- investment recommendation engines;
- generalized organization-identity resolution;
- universal web crawling;
- financial-analysis engines;
- legal-analysis engines;
- compliance-certification engines;
- generalized semantic inference;
- generalized workflow orchestration;
- distributed deployment architecture;
- domain-specific company ontology.

If implementation evidence reveals a missing shared capability, the approved capability-promotion lifecycle shall be used rather than silently changing the matrix.

---

## 14. Security, Privacy, and Operational Considerations

### 14.1 Sensitive Information

Due-diligence material may contain confidential business information, personal information, financial information, contractual information, security-sensitive material, or restricted records. Access controls and retention shall follow applicable deployment and data-governance requirements.

### 14.2 Provenance Integrity

The implementation should preserve auditable history of source, artifact, claim, evidence, comparison, reviewer, assessment, and report changes.

### 14.3 Access-Controlled Sources

Access state shall be represented. Unauthorized users shall not receive protected content, and the review shall not claim that protected material was inspected when it was not accessible.

### 14.4 External Dependency Failure

Retrieval/search failure shall not corrupt already registered material. Resulting incompleteness shall be represented.

### 14.5 Reproducibility

Released/baselined results should remain reconstructable from retained source/artifact versions and recorded processing state, subject to retention and access constraints.

### 14.6 Storage Durability

The implementation shall use an appropriate durability mechanism for its agreed storage SLA. Concrete storage technology and SLA parameters remain implementation decisions.

### 14.7 Observability

Operational records should diagnose source acquisition, parsing, claim extraction, evidence discovery, identity ambiguity, version mismatch, representation, assessment, and report-generation failures.

### 14.8 Auditability

The implementation shall preserve enough history to determine which sources and versions were reviewed, which claims/evidence were assessed, which material changes occurred, and which limitations were present.

---

## 15. Explicit Exclusions

VS-B01 does not require:

- autonomous investment decisions or recommendations;
- credit ratings;
- legal or accounting opinions;
- regulatory certification;
- universal company reputation scoring;
- autonomous fraud determination;
- universal source-credibility scoring;
- unrestricted web crawling;
- generalized search infrastructure;
- universal company knowledge graphs;
- generalized organization-identity inference;
- generalized risk engines;
- generalized workflow orchestration;
- distributed microservices;
- generalized multi-tenancy;
- domain-specific company semantic roots;
- implementation of all ECRA semantic constructs.

Specialized services may be used as replaceable dependencies when needed.

---

## 16. Implementation and Evolution Constraints

### 16.1 Semantic Contract Stability

The semantic model shall remain independent of UI framework, persistence technology, search/retrieval provider, financial-data provider, processing engine, and deployment topology.

### 16.2 Replaceability

Source retrieval, comparison, evidence discovery, extraction, and reporting components should be replaceable through explicit interfaces.

### 16.3 Cohesive Responsibilities

Maintain clear boundaries between source/artifact management, claim/evidence representation, provenance, assessment, discovery, comparison, workflow, and presentation.

### 16.4 Future Decomposition

The implementation should permit future separation of ingestion, retrieval, extraction, assessment, and reporting into separate processes/services without changing stable ECRA semantic contracts where reasonably foreseeable.

No microservice architecture is required for B01.

### 16.5 Determinism and Reproducibility

Structural validation and representation operations shall be deterministic. Time-dependent external retrieval shall preserve source identity, acquisition time, version, artifact identity, and retrieval provenance sufficient for reproducibility to the extent reasonably possible.

### 16.6 Source-Ranking Decoupling

The semantic model shall not depend on a particular source-ranking algorithm. Presentation ordering may change without changing the underlying source, evidence, provenance, or assessment semantics.

---

## 17. Design and Implementation Traceability

This specification is derived from and remains traceable to:

1. Approved ECRA Reference Application — Vertical Slice Portfolio.
2. Approved ECRA Reference Implementation — Cross-Slice Capability Matrix.
3. Approved ECRA P0 Vertical Slice Specification Framework.
4. Approved Gen1 Claim and Evidence Requirements.
5. Approved Gen1 Context and Evaluation Requirements.
6. Approved Gen1 Traceability and Engineering Requirements.
7. Applicable ECRA-1200 Architecture Description Language boundaries.
8. Applicable ECRA-1200 detailed-design foundation.

J01 and R01 were used only as implementation-pattern references for common P0 structure and previously demonstrated claim/evidence boundaries; they do not override the authoritative sources above.

The specification does not supersede any normative ECRA document.

Where B01 needs a semantic capability not established by these authorities, the gap shall be recorded rather than silently promoted into the normative ECRA model.

---

## 18. Verification Strategy

### 18.1 Contract Tests

Verify request/result structures, stable identity, valid references, relationship endpoints, source/version consistency, incomplete-result handling, and required provenance.

### 18.2 Semantic Integration Tests

Verify source/artifact, claim/evidence, explicit evidence relationships, source comparison traceability, support/contradiction/qualification/unresolved representation, provenance, traceability, version/lineage, and source-property boundaries.

### 18.3 Source-Comparison Tests

Verify that:

- the same material claim can be represented across multiple source statements;
- locations and versions remain distinguishable;
- conflicting statements remain represented;
- comparison does not overwrite a source;
- display order does not alter semantic state.

### 18.4 Identity Boundary Tests

Verify that similar names do not cause silent organization merging, aliases do not collapse distinct entities, and source/artifact identity remains stable across supported representation changes.

### 18.5 Negative Tests

Verify missing target/source, malformed or inaccessible material, source silence, conflicts, unsupported claims, partial support, ambiguity, source changes, incorrect extraction, duplicate evidence, stale assessments, identity ambiguity, and partial processing failure.

### 18.6 Reproducibility Tests

Verify reconstruction of a baselined review from retained source/artifact versions and recorded processing/provenance information, subject to permitted retention.

### 18.7 Representation Round-Trip

Verify:

```text
Logical VS-B01 semantic state
    → machine representation
    → reconstructed logical state
```

Required identity, sources, artifacts, claims, evidence, relationships, provenance, traceability, source/version state, assessments, and limitations shall be preserved. Byte-for-byte serialization equality is not required.

### 18.8 UI End-to-End Test

Demonstrate:

```text
Review setup
    → source intake
    → claim review
    → evidence review
    → source comparison
    → relationship/assessment
    → traceability
    → report
```

The UI demonstration is part of slice completion.

---

## 19. Deliverable and Completion Definition

VS-B01 is complete only when:

1. the logical workflow is implemented;
2. required shared-core capabilities are available;
3. application-specific capabilities are implemented;
4. the complete workflow is demonstrable through the UI;
5. acceptance criteria are verified;
6. negative and boundary cases are tested;
7. source-comparison behavior is demonstrated;
8. machine representation round-trip is verified;
9. provenance and traceability are demonstrated;
10. relevant capability-matrix evidence is recorded;
11. the implementation remains within the approved reference-core boundary.

Implementation completion does not require excluded or deferred capabilities.

---

## 20. Open and Deferred Items

The following remain intentionally open or deferred:

1. concrete public-record and filing providers;
2. concrete source-retrieval mechanisms;
3. detailed source-type vocabulary beyond applicable normative semantics;
4. detailed source-authority metadata vocabulary;
5. organization/entity identity-resolution behavior;
6. materiality configuration and UI;
7. concrete storage technology and SLA parameters;
8. detailed UI technology;
9. generalized source-ranking and discovery infrastructure;
10. financial-analysis-specific capabilities;
11. legal/compliance-specific domain models;
12. broader capability promotion based on later P0 slices.

These shall be resolved only when implementation evidence or an authoritative specification requires them.

---

## 21. Status

This specification is **REVIEW** and is intended to drive VS-B01 reference-application implementation planning and supporting verification once approved.
