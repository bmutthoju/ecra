# ECRA Reference Application — VS-L01 Case Evidence Review

> Status: APPROVED
> Authority: ENGINEERING / INFORMATIVE
> Generation: GEN1
> Scope: Detailed P0 vertical-slice specification for Case Evidence Review
> Matrix Basis: Approved ECRA Reference Implementation — Cross-Slice Capability Matrix
> Portfolio Basis: Approved ECRA Reference Application — Vertical Slice Portfolio

## 1. Purpose and Scope

### 1.1 Purpose

VS-L01 defines an evidence-review workflow for a case-document corpus. The workflow identifies material factual claims and associates relevant case evidence with those claims, preserving document locations, versions, provenance, competing accounts, limitations, and assessment state.

The slice demonstrates that the reference implementation can operate over legal or case-review material without requiring the ECRA reference core to become a legal reasoning, adjudication, or legal-authority engine.

The system represents claims, sources, artifacts, evidence, relationships, assessments, provenance, traceability, uncertainty, and limitations. It does not itself determine liability, guilt, innocence, legal validity, admissibility, litigation strategy, or the correct legal interpretation of a matter.

### 1.2 Intended Users

Primary users include:

- lawyers;
- legal researchers;
- case reviewers;
- litigation-support reviewers;
- investigators working with authorized case material;
- authorized legal or assurance analysts.

The slice does not prescribe a legal practice methodology, jurisdiction-specific legal standard, evidentiary rule, or professional judgment framework.

### 1.3 Workflow Boundary

The workflow begins with an authorized case-document corpus and a defined review scope. It ends with material factual claims, explicit evidence associations, source/document locations, competing or corroborating evidence, assessments, provenance, limitations, and a traceable case-evidence report.

### 1.4 Legal-Context Neutrality

Case materials may contain allegations, testimony, statements of fact, legal arguments, expert opinions, procedural assertions, documentary records, correspondence, and other content with different roles.

The application shall preserve the distinction between what a document says, what evidence bears on a factual claim, and any downstream legal conclusion.

A document's legal status, provenance, authorship, or apparent authority shall not automatically determine the truth of a factual proposition.

### 1.5 Non-Goals

VS-L01 does not establish:

- legal advice;
- legal conclusions;
- liability, guilt, innocence, or fault determinations;
- admissibility determinations;
- credibility scores for witnesses or parties;
- jurisdiction-specific evidentiary rules;
- autonomous legal research as a universal capability;
- autonomous legal reasoning;
- legal precedent ranking as a shared core capability;
- unrestricted legal-document crawling;
- universal document search infrastructure;
- a legal knowledge graph;
- generalized entity or party identity resolution;
- generalized workflow orchestration;
- distributed deployment architecture;
- a new ECRA semantic root type for Case, Party, Witness, Legal Issue, Legal Argument, or Evidence.

Case-specific and jurisdiction-specific structures remain application-level unless an authoritative ECRA specification establishes otherwise.

### 1.6 Assumptions and Limitations

Case corpora may be incomplete, duplicated, redacted, inaccessible, historically revised, inconsistently indexed, or internally conflicting.

A review result may therefore be partial or unresolved. Missing documents, unavailable pages, uncertain identity, or incomplete context shall be represented explicitly rather than silently inferred.

---

## 2. Scenario and Preconditions

### 2.1 Primary Scenario

An authorized reviewer has a defined case corpus and wants to understand the evidentiary support for material factual claims.

The application:

1. registers case sources and artifacts;
2. identifies material factual claims;
3. records exact or sufficiently precise document locations;
4. identifies relevant evidence;
5. registers evidence and provenance;
6. associates evidence explicitly with claims;
7. preserves competing, corroborating, or qualifying evidence;
8. records assessment state and uncertainty;
9. preserves document and evidence versions;
10. generates a traceable case-evidence report.

### 2.2 Example Review Questions

The application may support questions such as:

- What factual claims are material to the current review scope?
- Where does each claim originate?
- Which case documents contain evidence relevant to each claim?
- Which documents support, contradict, qualify, or leave a claim unresolved?
- Do multiple documents provide materially different accounts?
- Which evidence is direct, attributed, derived, or otherwise qualified within the review?
- Which document versions were reviewed?
- Which claims remain unsupported or insufficiently evidenced?
- What provenance and document locations underlie each assessment?

These are review questions, not legal conclusions.

### 2.3 Required Inputs

The minimum workflow input is:

- an authorized case-review context;
- a defined review scope;
- a case-document corpus or supported document acquisition input.

The exact representation of a legal case or matter remains application-specific unless an applicable ECRA specification defines a canonical representation.

### 2.4 Optional Inputs

Optional inputs may include:

- case identifier;
- matter metadata;
- jurisdiction;
- document identifiers;
- document types;
- parties or named subjects;
- filing dates;
- document dates;
- source metadata;
- reviewer questions;
- existing factual claims;
- existing evidence associations;
- document versions;
- reviewer notes;
- selected text spans;
- procedural or temporal scope;
- issue labels supplied by the reviewer.

Optional metadata does not become evidence merely because it was supplied.

### 2.5 Document Availability

A document may be available, partial, redacted, inaccessible, withdrawn, superseded, duplicated, malformed, historical, or supplied without independent verification.

The system shall preserve the applicable state and shall not represent inaccessible material as inspected evidence.

---

## 3. End-to-End Workflow

```text
Authorized case corpus + review scope
    ↓
Document/source intake and registration
    ↓
Identify material factual claims
    ↓
Locate claims in documents
    ↓
Identify relevant evidence
    ↓
Register evidence and document/artifact state
    ↓
Associate evidence with claims
    ↓
Compare corroborating / conflicting / qualifying material
    ↓
Assess support / contradiction / qualification / unresolved state
    ↓
Record provenance, versions, limitations, and reviewer actions
    ↓
Generate case-evidence report
    ↓
Reviewer inspection and follow-up
```

### 3.1 Review Scope

The reviewer establishes the matter context, purpose, document corpus, temporal or procedural scope where applicable, review questions, and any application-specific review criteria.

Scope is contextual information. It is not automatically a factual claim about the case.

### 3.2 Document and Artifact Registration

Each material document/source shall have applicable:

- source identity;
- artifact identity;
- document identity;
- document type or role where known;
- acquisition state;
- version/revision;
- date metadata where available;
- location;
- provenance;
- integrity information;
- authenticity information;
- authority/context information where applicable.

Document classification provides context and does not automatically establish factual truth.

### 3.3 Claim Identification

Claims may be suggested from pleadings, statements, testimony, reports, correspondence, filings, exhibits, expert material, records, or other authorized case documents.

Reviewers shall be able to inspect, correct, accept, reject, or supplement candidate claims.

Claim wording, source location, origin, and provenance shall be preserved.

### 3.4 Claim Qualification

Claims may be descriptively classified as:

- factual assertion;
- allegation;
- attributed statement;
- historical assertion;
- event/timeline assertion;
- documentary assertion;
- expert assertion;
- procedural assertion;
- opinion;
- inference;
- prediction;
- ambiguous statement;
- otherwise reviewable proposition.

Classification is descriptive and shall not itself determine truth, credibility, admissibility, or legal effect.

### 3.5 Evidence Identification and Registration

Relevant evidence may include:

- documentary records;
- statements or testimony;
- communications;
- photographs or media;
- expert reports;
- financial or operational records;
- filings;
- correspondence;
- contemporaneous records;
- later records bearing on historical claims;
- reviewer-supplied material;
- evidence derived through an explicit evidence chain.

Evidence discovery may be assisted by application functionality, but material evidence associations shall remain explicit and inspectable.

Where the review model characterizes evidentiary strength, that characterization shall be explicit, traceable, and supported by the available provenance and evidence. An attributed statement, eyewitness account, or word-of-mouth report shall not be treated as strong evidence merely because it exists or is attributed. Evidence that has stronger evidentiary support within the declared review criteria may include a verified recording, authentic source material, or information derived through a valid logical or mathematical proof. The report shall transparently identify the evidence basis, relevant verification or derivation, and any limitations rather than presenting evidence strength as an unqualified property of an evidence type.

### 3.6 Claim/Evidence Association

The implementation shall support:

- multiple evidence items for one claim;
- one evidence item relevant to multiple claims;
- corroborating evidence;
- contradictory evidence;
- qualifying evidence;
- evidence chains;
- claims with no currently identified evidence.

Evidence relevance shall not be inferred solely from document co-location or keyword similarity.

### 3.7 Document Comparison

For each material claim, the reviewer should be able to inspect:

- claim wording;
- originating document and location;
- document version;
- relevant statements or records in other documents;
- associated evidence;
- relationship/assessment state;
- provenance;
- limitations;
- relevant temporal context.

Document comparison is an application analysis/presentation capability. It does not require a universal legal-document ranking engine.

### 3.8 Assessment

The assessment representation shall support:

- supported;
- contradicted;
- partially supported or qualified;
- unresolved or insufficient evidence.

The assessment is an evidence-review result within the declared scope. It is not a legal conclusion.

### 3.9 Human Review and Correction

Reviewers may correct extracted claims, add claims, change evidence associations, identify missing documents, mark ambiguity, revise assessments, and add review notes.

A material reviewer correction or justification shall be represented as a reviewer-originated claim/assertion with explicit provenance rather than as an unqualified state change. The correction claim shall identify the prior and revised state where applicable. Its justification may itself contain one or more claims and shall be assessed against supporting evidence where applicable.

Material changes shall preserve reviewer identity where available, timestamp, prior state, revised state, justification, supporting evidence where applicable, assessment state, and provenance. Reviewer-generated claims, corrections, and justifications shall remain distinguishable from source-originated claims and shall not automatically override them.

### 3.10 Report Generation

The report shall show:

- review scope;
- material claims;
- originating documents and locations;
- relevant evidence;
- corroborating or conflicting material;
- assessments;
- evidentiary-strength characterizations and their basis where used;
- reviewer corrections and justifications, including their assessment state where used;
- limitations;
- document versions;
- provenance;
- unresolved questions;
- evidence gaps.

The report shall not present an aggregate legal-risk, liability, credibility, guilt, innocence, or case-outcome score unless separately established by an applicable specification.

---

## 4. Semantic Object Requirements

### 4.1 Review Context

Represents the authorized review scope, document corpus, temporal/procedural context, reviewer context, and applicable review criteria.

It reuses applicable ECRA context semantics and is not a new portfolio-wide root type.

### 4.2 Source

Represents an identifiable origin from which information is obtained or attributed.

It has stable identity and applicable metadata, provenance, source-state, and authority/context information.

### 4.3 Acquired Artifact

Represents material actually obtained by the system. It preserves stable identity, acquisition provenance, version/revision where applicable, integrity information where available, and relationship to its source.

### 4.4 Case Document

A case document is an application-level specialization/contextual representation of an artifact or source relevant to the case.

It shall not establish a new portfolio-wide ECRA root type.

### 4.5 Claim

Represents an identifiable proposition submitted for evidence review.

It preserves stable identity, proposition content, source location where applicable, provenance, version/lineage, evidence relationships, and assessment state.

An allegation remains an identifiable claim even when the document containing it is authentic or authoritative.

### 4.6 Evidence

Represents information relevant to determining whether, or to what extent, a claim is established within the review scope.

It preserves stable identity, source, artifact/document, location, version/lineage where applicable, provenance, and applicable integrity/authenticity/authority information.

### 4.7 Claim–Evidence Relationship

Represents an explicit association between evidence and the claim(s) for which it is relevant.

Concrete relationship names, domain/range rules, and serialization remain governed by authoritative ECRA relationship semantics.

### 4.8 Document Location

Identifies where a claim or evidence item occurs within a document or artifact, such as page, paragraph, section, exhibit, table, record, timestamp, text span, or other supported location.

A location is a reference into a document/artifact and does not replace its identity.

### 4.9 Assessment / Evaluation Result

Represents the assessment of a claim relative to available evidence and the declared review scope.

It remains distinct from:

- document authenticity;
- document authority;
- provenance completeness;
- source type;
- witness/party identity;
- reviewer affiliation;
- legal conclusion.

Results may be incomplete or unresolved.

### 4.10 Reviewer Action / Correction Provenance

Material reviewer actions shall distinguish application-generated state, reviewer-confirmed state, reviewer-corrected state, rejected candidates, added claims/evidence, revised relationships, and revised assessments.

### 4.11 Integrity, Authenticity, and Authority

The Gen1 boundary shall be preserved:

- integrity concerns whether acquired information has been altered or corrupted under the applicable mechanism;
- authenticity concerns whether source/artifact identity or attribution is genuine under the applicable mechanism;
- authority concerns the basis for considering a source appropriate for the relevant evaluation.

These properties do not automatically establish the truth of a claim or the legal effect of evidence.

---

## 5. Relationship Requirements

### 5.1 Required Relationship Families

The workflow requires relationships corresponding to:

- review-context association with case material;
- claim origin from source/artifact;
- evidence origin from source/artifact;
- evidence relevance/bearing on claim;
- claim derivation where applicable;
- provenance association;
- version/lineage where applicable;
- assessment association;
- document-location association.

Concrete names shall be taken from authoritative ECRA relationship semantics.

### 5.2 Relationship Identity

Every material relationship shall have identifiable semantic endpoints.

Presentation labels, document filenames, page numbers, database rows, or textual similarity shall not substitute for semantic identity.

### 5.3 Multiplicity

The slice supports:

- zero or more evidence items per claim;
- one evidence item relevant to multiple claims;
- multiple documents relevant to one claim;
- multiple claims from one document;
- multiple document/artifact versions;
- multiple assessments across review revisions.

### 5.4 Competing Accounts

Different documents may contain materially different accounts of the same event or proposition.

Each statement, claim, source, document, location, version, relationship, assessment, and provenance shall remain represented.

The system shall not overwrite one account with another merely because one document is newer, preferred, or associated with a particular role.

### 5.5 Evidence Chains

An evidence chain may be:

```text
Claim A
  → Statement / Claim B
  → Document / Artifact C
  → Evidence D
```

The chain remains traversable.

Evidence reached through a chain does not automatically establish every intermediate proposition.

### 5.6 Temporal Relationships

Where material to the review, claims and evidence shall preserve applicable dates, time ranges, temporal source context, and version/lineage.

Temporal metadata is contextual information and does not itself establish the truth of an event claim.

### 5.7 Version Relationships

When a document or evidence artifact is revised:

- prior versions remain identifiable where retention permits;
- the new version has distinct version/lineage information;
- prior assessments remain associated with the source state on which they were based;
- affected claims may be reassessed.

---

## 6. Evidence and Assessment Requirements

### 6.1 Documentary Evidence

A document may provide evidence relevant to one or more claims.

The system shall preserve document identity, location, version, provenance, and applicable source properties.

Document existence or authenticity shall not automatically establish every proposition stated in the document.

### 6.2 Testimonial or Attributed Evidence

Statements attributed to a person or entity may be represented as evidence or as source claims, depending on the review model.

The implementation shall preserve attribution and provenance without turning attribution into an independent credibility judgment. An attributed statement, eyewitness account, or word-of-mouth report shall not be treated as strong evidence solely because it is a statement or because it has an identified speaker.

Where evidentiary strength is characterized, the assessment shall consider the available verification and evidence basis. Examples of evidence that may warrant a stronger characterization within the declared review criteria include a verified video or audio recording, authentic source material, or logically derived information supported by valid proof techniques. Such characterization shall remain transparent and traceable to the evidence and its provenance.

### 6.3 Corroboration

Evidence may corroborate a claim when it independently or additionally bears on the proposition in a way that supports the applicable assessment.

The report shall identify the evidence and locations.

### 6.4 Contradiction

Contradiction requires materially incompatible evidence relevant to the claim.

It shall not be inferred merely because:

- a document is silent;
- a document is inaccessible;
- a document has a different source role;
- the reviewer prefers another source;
- an assertion is disputed without identified evidence.

### 6.5 Qualification / Partial Support

Evidence may support only part of a broad claim or may establish a condition, exception, limitation, or narrower proposition.

The application shall allow supported and unsupported portions, qualifying conditions, evidence, and locations to be distinguished.

### 6.6 Unresolved / Insufficient Evidence

A claim may remain unresolved because:

- evidence is insufficient;
- relevant documents are unavailable;
- documents conflict without a resolved basis;
- source material is incomplete;
- relevant context is missing;
- the review scope is insufficient.

Absence of evidence shall not automatically become contradiction.

### 6.7 Conflicting Evidence

All materially relevant evidence shall remain represented with source provenance, version, location, and resulting uncertainty or qualification.

The application shall not silently select a preferred account.

### 6.8 Evidence Scope

The report shall distinguish:

- evidence found within the reviewed corpus;
- evidence not found within the reviewed corpus;
- evidence that could not be accessed;
- evidence known to exist but not included;
- evidence outside the declared scope.

These states shall not be collapsed.

### 6.9 Temporal Relevance

Evidence may have a different temporal relationship to the claimed event.

The application shall preserve relevant dates and context rather than silently treating later records as contemporaneous evidence or vice versa.

### 6.10 Human Assessment

Human assessment changes shall preserve reviewer, timestamp, previous state, revised state, rationale, supporting evidence where applicable, and provenance.

### 6.11 Assessment Limitations

The result shall distinguish evidence, access, integrity, authenticity, authority, processing, scope, temporal, and substantive limitations rather than collapsing them into a generic confidence score.

### 6.12 Legal-Conclusion Boundary

The application may expose evidence patterns relevant to a reviewer but shall not automatically transform an evidence assessment into a legal conclusion.

For example, an assessment that evidence contradicts a factual claim does not by itself establish liability, negligence, intent, admissibility, or another legal conclusion.

---

## 7. Provenance and Traceability

### 7.1 Required Provenance

Preserve provenance for:

- review creation;
- source/document registration;
- acquisition;
- document version;
- claim identification/correction;
- evidence discovery/registration/association;
- document comparison;
- assessment;
- reviewer actions;
- report generation;
- applicable transformations.

### 7.2 Traceability Path

```text
Review Scope
   ↓
Claim
   ↓
Claim Document Location
   ↓
Artifact / Document
   ↓
Source
   ↓
Evidence
   ↓
Evidence Document Location
   ↓
Assessment
   ↓
Provenance
```

The implementation shall support navigation through the material path needed to explain a result.

### 7.3 Document-Comparison Traceability

A comparison shall remain traceable to:

- compared claims/statements;
- documents/artifacts;
- locations;
- versions;
- applicable temporal context;
- processing/reviewer action;
- resulting assessment.

### 7.4 Historical Reconstruction

Released or baselined reviews shall preserve sufficient information to reconstruct the review state subject to retention and access constraints.

Later changes shall not silently rewrite historical results.

### 7.5 Claim Revision

When a material claim changes:

1. preserve the prior state and assessment;
2. record the revised claim and lineage;
3. identify the source/document location of the revised claim;
4. mark prior assessment stale/superseded where applicable;
5. permit reassessment.

### 7.6 Evidence Revision

When evidence changes:

1. preserve the prior evidence version where retained;
2. register the new version;
3. keep affected assessments traceable to the version used;
4. identify affected claims;
5. permit reassessment.

### 7.7 Document Redaction or Replacement

If a document is redacted, replaced, or withdrawn, preserve the applicable prior state and access status where retention permits.

The system shall not silently represent a newly inaccessible document as though it remains fully reviewable.

---

## 8. Input / Output Contracts

### 8.1 Review Request

Conceptually:

```text
CaseEvidenceReviewRequest
├── caseContext
├── reviewScope
├── documentInputs
├── initialClaims [optional]
├── reviewQuestions [optional]
├── temporalScope [optional]
├── reviewerContext [optional]
└── criteria [optional]
```

Exact programming-language representation is implementation-specific.

### 8.2 Document Input

Supports:

- source reference;
- artifact/document reference;
- document metadata;
- document type/role where available;
- version/revision;
- location;
- access state;
- provenance;
- integrity/authenticity information where available.

### 8.3 Claim Input

Supports:

- claim identity when known;
- claim content;
- source/document reference;
- source location;
- descriptive classification where available;
- provenance;
- version/lineage.

### 8.4 Evidence Input

Supports:

- evidence identity;
- source/document/artifact reference;
- document location;
- version/lineage;
- content or reference;
- provenance;
- applicable integrity/authenticity/authority information.

### 8.5 Result Contract

Conceptually:

```text
CaseEvidenceReviewResult
├── caseContext
├── reviewScope
├── sources
├── artifacts
├── documents
├── claims
├── evidence
├── relationships
├── assessments
├── limitations
├── provenance
├── traceability
└── report
```

### 8.6 Incomplete Results

Partial completion is supported.

Unavailable documents, inaccessible pages, failed extraction, unresolved claims, or processing failures shall not require discarding successfully processed material.

### 8.7 Deterministic Structural Validation

Validate deterministically:

- required identities;
- valid references;
- valid relationship endpoints;
- source/artifact/document consistency;
- required locations where applicable;
- version-reference consistency;
- required provenance for material actions.

Structural validation remains distinct from substantive assessment and legal interpretation.

### 8.8 Result Completeness

The result shall identify whether the review is complete within declared scope, partially complete, or incomplete because of source/access/processing limitations.

An incomplete review shall not be presented as comprehensive.

---

## 9. UI Demonstration

### 9.1 Review Setup

Allow the reviewer to establish:

- case/review context;
- scope;
- document corpus;
- temporal or procedural scope where applicable;
- review questions;
- optional criteria.

### 9.2 Document Intake

Allow inspection of:

- registered documents;
- document/source identity;
- document type/role;
- artifact state;
- version;
- dates where available;
- access state;
- originating material subject to authorization.

### 9.3 Claim Review

Allow the reviewer to:

- inspect candidate claims;
- accept/reject claims;
- correct claims;
- add claims;
- classify claims descriptively;
- identify ambiguity;
- navigate to originating document locations.

### 9.4 Evidence Review

Allow inspection of:

- evidence;
- source/document;
- exact location;
- version;
- provenance;
- integrity/authenticity/authority information where available;
- explicit claim association.

### 9.5 Competing-Evidence View

The minimum evidence view shall show:

| Element | Demonstration |
|---|---|
| Claim | Material factual proposition |
| Origin | Document and location |
| Document version | Version/revision used |
| Evidence | Relevant supporting, contradictory, or qualifying material |
| Evidence location | Exact document location |
| Relationship | Support, contradiction, qualification, or unresolved relevance |
| Temporal context | Relevant dates/time context where applicable |
| Assessment | Current evidence-review state |
| Limitations | Missing, inaccessible, conflicting, redacted, or incomplete material |
| Provenance | Origin of evidence and assessment |

Display order shall not imply legal preference, credibility, or admissibility.

### 9.6 Assessment View

Show:

- support;
- contradiction;
- qualification/partial support;
- unresolved/insufficient evidence;
- conflicting evidence;
- uncertainty;
- rationale;
- provenance;
- limitations.

### 9.7 Traceability View

Allow navigation through:

```text
Claim ↔ Document ↔ Artifact ↔ Evidence ↔ Assessment ↔ Provenance
```

and between retained document/evidence versions.

### 9.8 Report View

Show:

- review scope;
- document corpus;
- material claims;
- originating locations;
- evidence;
- competing accounts;
- assessments;
- limitations;
- versions;
- provenance;
- unresolved questions;
- evidence gaps.

The report shall preserve enough context to prevent misleading extraction of isolated statements.

---

## 10. Negative and Boundary Cases

### 10.1 Missing Review Scope

Reject or hold substantive processing and identify the missing scope information.

### 10.2 Empty Case Corpus

Represent the review as incomplete.

Do not infer negative findings from the absence of documents.

### 10.3 Malformed Document

Preserve registration where possible, identify malformed portions, and avoid silently extracting unsupported claims.

### 10.4 Inaccessible Document

Identify the document and access limitation.

Do not represent inaccessible material as reviewed evidence.

### 10.5 Redacted Document

Preserve redaction state and available context.

Do not infer content that is unavailable because of redaction.

### 10.6 Conflicting Accounts

Preserve each statement, source, document, location, version, conflict, and resulting assessment.

Do not silently select one account.

### 10.7 Source Silence

Distinguish:

- no evidence found;
- document does not address the claim;
- document inaccessible;
- corpus incomplete;
- search/review incomplete.

Silence is not contradiction.

### 10.8 Duplicate Document

Distinguish duplicate representations from distinct document versions and avoid accidental double-counting at the application layer.

### 10.9 Historical Document

Preserve date/version and temporal relevance.

Do not silently represent historical material as contemporaneous or current.

### 10.10 Changed Document

Preserve the previously used version where permitted, register the new version, preserve prior assessments, identify affected claims, and permit reassessment.

### 10.11 Unsupported Factual Claim

Preserve the claim and evidence gap.

Represent unresolved/insufficient status where applicable.

Do not automatically conclude that the claim is false or legally invalid.

### 10.12 Partial Support

Identify supported and unsupported portions, qualifying conditions, evidence, and locations.

### 10.13 Ambiguous Statement

Preserve original wording and context, identify ambiguity, allow relevant interpretations to be evaluated separately, and do not silently select one.

### 10.14 Incorrect Automated Extraction

Preserve candidate, corrected claim, reviewer information where available, correction rationale, and processing provenance.

### 10.15 User-Supplied Assertion

Preserve user-supplied provenance.

Do not treat it as independently verified merely because it was supplied.

### 10.16 Claim Changed After Assessment

Preserve prior claim and assessment, record revised claim/lineage, mark prior assessment stale/superseded as applicable, and permit reassessment.

### 10.17 Evidence Changed After Assessment

Preserve prior evidence version and assessment where retention permits, then permit reassessment against the new evidence.

### 10.18 Entity or Party Identity Ambiguity

Do not silently merge similarly named persons, organizations, or other subjects.

Expose ambiguity and require sufficient identifying information for application-level resolution.

### 10.19 Multiple Names or Aliases

Preserve aliases and contextual names.

Do not silently merge distinct subjects.

### 10.20 Evidence Chain

Preserve the chain and every intermediate step.

Do not imply that all intermediate propositions are established.

### 10.21 Temporal Inconsistency

Expose material conflicts between dates, timelines, and source versions.

Do not silently normalize conflicting temporal information.

### 10.22 Partial Processing Failure

Retain successfully processed material and identify failed portions and their effect on completeness.

### 10.23 Round-Trip Failure

Report representation/conformance failure rather than silently dropping document, claim, evidence, relationship, provenance, assessment, or limitation information.

### 10.24 Legal-Conclusion Request

If the workflow receives a legal-conclusion request, preserve the underlying factual/evidence-review task where possible, but do not silently transform evidence assessment into a legal conclusion.

---

## 11. Acceptance Criteria

| ID | Acceptance criterion |
|---|---|
| AC-L01-01 | A reviewer can establish a case evidence review with a declared scope. |
| AC-L01-02 | Case sources and acquired artifacts/documents can be registered with stable identity and applicable provenance. |
| AC-L01-03 | Document version/revision and access state can be represented and inspected. |
| AC-L01-04 | Material factual claims can be identified or supplied with originating document locations. |
| AC-L01-05 | Claim classification remains descriptive and does not determine truth, credibility, admissibility, or legal effect. |
| AC-L01-06 | Evidence can be registered with source, artifact/document, location, version, and provenance. |
| AC-L01-07 | Evidence can be explicitly associated with one or more claims. |
| AC-L01-08 | Support, contradiction, qualification/partial support, and unresolved/insufficient states can be represented. |
| AC-L01-09 | Corroborating and conflicting evidence remain distinguishable and traceable. |
| AC-L01-10 | Material claims can be compared across case documents without silently overwriting or selecting a preferred account. |
| AC-L01-11 | Document silence, inaccessible material, incomplete corpus, and insufficient evidence are distinguishable from contradiction. |
| AC-L01-12 | Document and evidence locations can be inspected and navigated from claims and evidence. |
| AC-L01-13 | Temporal context and relevant document dates can be represented without silently resolving conflicting timelines. |
| AC-L01-14 | Human claim corrections are represented as reviewer-originated claims/assertions and preserve prior state, reviewer provenance, and justification. |
| AC-L01-15 | Human assessment changes preserve prior and revised states and provenance. |
| AC-L01-16 | Reviewer corrections and their justifications can be assessed against supporting evidence where applicable, with the assessment and provenance preserved. |
| AC-L01-16 | Evidence chains remain traversable without implying support for every intermediate proposition. |
| AC-L01-17 | Document changes preserve historical version lineage and prior assessment context where permitted. |
| AC-L01-18 | Claim changes after assessment preserve the prior claim and prevent silent reuse of its assessment for the revised claim. |
| AC-L01-19 | Reviewers can open/read originating case material subject to authorization and access restrictions. |
| AC-L01-20 | The UI exposes scope, documents, claims, evidence, relationships, provenance, assessments, limitations, and report output. |
| AC-L01-21 | The report preserves enough context to distinguish source statements, evidence, assessments, conflicts, and unresolved questions. |
| AC-L01-22 | Integrity, authenticity, and authority remain distinct from substantive evidence assessment. |
| AC-L01-23 | Incomplete or failed document retrieval does not discard successfully processed material and is visible in the result. |
| AC-L01-24 | Identity ambiguity does not result in silent merging of distinct persons, organizations, or subjects. |
| AC-L01-25 | Historical/superseded document versions remain distinguishable from current state. |
| AC-L01-26 | Machine round-trip preserves identity, documents, relationships, provenance, traceability, source/version state, assessments, and limitations. |
| AC-L01-27 | Structural validation detects invalid identities, references, endpoints, and required provenance deterministically. |
| AC-L01-28 | A complete end-to-end UI workflow can be demonstrated from review setup through report inspection. |
| AC-L01-29 | Redacted, excluded, unavailable, or non-reviewable material is represented with sufficient explanation and context. |
| AC-L01-30 | The report identifies material evidence gaps and unresolved factual questions without converting evidence gaps into unsupported legal conclusions. |

---

## 12. Reference-Core versus Application Responsibilities

### 12.1 Shared Reference Core

The shared core shall provide only capabilities demonstrated as reusable and necessary across the P0 portfolio, including:

- stable semantic identity;
- source/artifact representation;
- source/document location;
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

VS-L01 does not justify a new legal-specific semantic root type.

### 12.2 Reusable Enabling Infrastructure

Potential reusable enabling infrastructure includes:

- document/artifact version storage;
- source-location handling;
- deterministic structural validation;
- provenance capture;
- report assembly;
- document comparison interfaces;
- evidence-chain traversal.

These remain cohesive and replaceable.

### 12.3 Application Layer

The L01 application owns:

- case-review workflow;
- case/document corpus configuration;
- legal-document ingestion;
- document-type presentation;
- claim extraction suggestions;
- evidence discovery;
- document comparison presentation;
- temporal/timeline presentation;
- party/subject disambiguation UX;
- reviewer workflow;
- case-specific source selection;
- report presentation.

These shall not be promoted into the semantic core merely because L01 needs them.

### 12.4 External Dependencies

Potential external dependencies include:

- authorized document repositories;
- case-management systems;
- document retrieval;
- OCR/text extraction;
- search/indexing services;
- legal research providers;
- identity/access-control systems.

No provider is prescribed.

---

## 13. Capability Coverage

### 13.1 Demonstrated / Required Capabilities

L01 requires approved matrix capabilities for:

- source material registration;
- acquired artifact/document preservation;
- source/document location;
- stable semantic identity;
- claim representation;
- evidence representation;
- evidence-to-claim association;
- typed relationship representation;
- support/contradiction/qualification assessment;
- unresolved/uncertainty representation;
- provenance;
- traceability traversal;
- source/document version state;
- artifact integrity information;
- source authenticity where applicable;
- source authority information;
- transformation provenance;
- machine-readable representation;
- semantic round-trip;
- structured assessment result;
- report generation;
- UI inspection of documents/claims/evidence/relationships/provenance/assessment/report;
- validation/conformance and verification integration;
- deterministic structural validation;
- reproducible processing records.

### 13.2 Application-Specific Capabilities

The following remain application-level:

- case-review setup;
- case-document corpus selection;
- document comparison presentation;
- temporal/timeline presentation;
- document-type handling;
- party/subject identity disambiguation;
- legal-domain source discovery;
- authorized repository integration.

### 13.3 No New Core Promotion from L01 Alone

L01 does not justify:

- legal reasoning engines;
- legal precedent ranking engines;
- universal legal ontologies;
- autonomous legal research;
- credibility scoring;
- admissibility engines;
- liability/guilt/innocence scoring;
- universal case knowledge graphs;
- generalized party/entity identity resolution;
- universal document crawling;
- generalized workflow orchestration;
- distributed deployment architecture;
- jurisdiction-specific legal semantics in the shared core.

If implementation evidence reveals a missing shared capability, the approved capability-promotion lifecycle shall be used rather than silently changing the matrix.

---

## 14. Security, Privacy, and Operational Considerations

### 14.1 Confidential and Privileged Material

Case materials may contain highly sensitive, confidential, privileged, personal, financial, medical, or security-sensitive information.

Access control, authorization, retention, and handling shall follow the applicable deployment and data-governance requirements.

The reference slice shall not assume that all registered material is visible to every reviewer.

### 14.2 Access-Controlled Sources

Access state shall be represented.

Unauthorized users shall not receive protected content, and the review shall not claim that protected material was inspected when it was not accessible.

### 14.3 Provenance Integrity

The implementation should preserve auditable history of:

- source/document registration;
- acquisition;
- claims;
- evidence;
- relationships;
- reviewer actions;
- assessments;
- report changes.

### 14.4 External Dependency Failure

Repository, retrieval, OCR, parsing, or search failure shall not corrupt already registered material.

Resulting incompleteness shall be represented.

### 14.5 Reproducibility

Released/baselined results should remain reconstructable from retained document/artifact versions and recorded processing state, subject to retention and access constraints.

### 14.6 Storage Durability

The implementation shall use an appropriate durability mechanism for its agreed storage SLA.

Concrete storage technology and SLA parameters remain implementation decisions.

### 14.7 Observability

Operational records should diagnose:

- document acquisition;
- parsing/OCR;
- claim extraction;
- evidence discovery;
- identity ambiguity;
- version mismatch;
- location resolution;
- representation;
- assessment;
- report-generation failures.

### 14.8 Auditability

The implementation shall preserve enough history to determine:

- which documents and versions were reviewed;
- which claims/evidence were assessed;
- which reviewer actions occurred;
- which material changes occurred;
- which limitations were present.

### 14.9 Authorization Boundary

The slice shall not bypass repository or document authorization controls merely to improve review completeness.

---

## 15. Explicit Exclusions

VS-L01 does not require:

- legal advice generation;
- legal conclusions;
- liability, guilt, innocence, or fault scoring;
- admissibility determination;
- witness credibility scoring;
- autonomous legal reasoning;
- legal precedent ranking;
- universal legal search;
- unrestricted case-document crawling;
- universal legal knowledge graphs;
- generalized party/entity identity resolution;
- generalized risk engines;
- generalized workflow orchestration;
- distributed microservices;
- generalized multi-tenancy;
- jurisdiction-specific legal semantic roots;
- implementation of all ECRA semantic constructs.

Specialized legal services may be used as replaceable application dependencies when needed.

---

## 16. Implementation and Evolution Constraints

### 16.1 Semantic Contract Stability

The semantic model shall remain independent of:

- UI framework;
- persistence technology;
- document repository;
- OCR/extraction engine;
- search provider;
- legal research provider;
- assessment implementation;
- deployment topology.

### 16.2 Replaceability

Document retrieval, extraction, search, evidence discovery, comparison, and reporting components should be replaceable through explicit interfaces.

### 16.3 Cohesive Responsibilities

Maintain clear boundaries between:

- source/artifact/document management;
- claim/evidence representation;
- provenance;
- assessment;
- document discovery;
- comparison;
- timeline presentation;
- case workflow;
- UI presentation.

### 16.4 Future Decomposition

The implementation should permit future separation of ingestion, extraction, retrieval, evidence discovery, assessment, and reporting into separate processes/services without changing stable ECRA semantic contracts where reasonably foreseeable.

No microservice architecture is required for L01.

### 16.5 Determinism and Reproducibility

Structural validation and representation operations shall be deterministic.

Time-dependent document retrieval shall preserve source identity, acquisition time, version, artifact identity, and retrieval provenance sufficient for reproducibility to the extent reasonably possible.

### 16.6 Legal-Domain Decoupling

The shared semantic model shall not depend on a particular jurisdiction, legal code, court system, legal research provider, or legal interpretation framework.

Application-level legal context may be supplied through replaceable domain components.

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

J01, R01, and B01 were used only as implementation-pattern references for common P0 structure and previously demonstrated claim/evidence boundaries; they do not override the authoritative sources above.

The specification does not supersede any normative ECRA document.

Where L01 needs a semantic capability not established by these authorities, the gap shall be recorded rather than silently promoted into the normative ECRA model.

---

## 18. Verification Strategy

### 18.1 Contract Tests

Verify:

- request/result structures;
- stable identity;
- valid references;
- relationship endpoints;
- document/version consistency;
- incomplete-result handling;
- required provenance.

### 18.2 Semantic Integration Tests

Verify:

- source/artifact/document;
- claim/evidence;
- explicit evidence relationships;
- document-location traceability;
- support/contradiction/qualification/unresolved representation;
- provenance;
- traceability;
- version/lineage;
- source-property boundaries.

### 18.3 Competing-Evidence Tests

Verify that:

- the same material claim can be represented across multiple documents;
- document locations and versions remain distinguishable;
- conflicting accounts remain represented;
- comparison does not overwrite a source;
- display order does not alter semantic state.

### 18.4 Temporal Tests

Verify that:

- relevant dates remain attached to source/document/claim/evidence context;
- conflicting dates remain visible;
- historical material is not silently treated as current;
- document versions remain distinguishable.

### 18.5 Identity Boundary Tests

Verify that:

- similarly named subjects do not cause silent merging;
- aliases do not collapse distinct subjects;
- source/document identity remains stable across representation changes.

### 18.6 Negative Tests

Verify:

- missing scope;
- empty corpus;
- malformed/inaccessible/redacted documents;
- conflicting accounts;
- source silence;
- unsupported claims;
- partial support;
- ambiguity;
- changed documents;
- incorrect extraction;
- duplicate documents;
- stale assessments;
- identity ambiguity;
- temporal inconsistency;
- partial processing failure.

### 18.7 Reproducibility Tests

Verify reconstruction of a baselined review from retained document/artifact versions and recorded processing/provenance information, subject to permitted retention.

### 18.8 Representation Round-Trip

Verify:

```text
Logical VS-L01 semantic state
    → machine representation
    → reconstructed logical state
```

Required identity, documents, claims, evidence, relationships, provenance, traceability, source/version state, assessments, and limitations shall be preserved.

Byte-for-byte serialization equality is not required.

### 18.9 UI End-to-End Test

Demonstrate:

```text
Review setup
    → document intake
    → claim review
    → evidence review
    → competing-evidence comparison
    → relationship/assessment
    → traceability
    → report
```

The UI demonstration is part of slice completion.

---

## 19. Deliverable and Completion Definition

VS-L01 is complete only when:

1. the logical workflow is implemented;
2. required shared-core capabilities are available;
3. application-specific capabilities are implemented;
4. the complete workflow is demonstrable through the UI;
5. acceptance criteria are verified;
6. negative and boundary cases are tested;
7. competing-evidence behavior is demonstrated;
8. document-location traceability is demonstrated;
9. machine representation round-trip is verified;
10. provenance and traceability are demonstrated;
11. relevant capability-matrix evidence is recorded;
12. the implementation remains within the approved reference-core boundary.

Implementation completion does not require excluded or deferred capabilities.

---

## 20. Open and Deferred Items

The following remain intentionally open or deferred:

1. concrete case-management/document repository providers;
2. concrete OCR/document extraction mechanisms;
3. detailed document-type vocabulary beyond applicable normative semantics;
4. detailed source/document authority metadata vocabulary;
5. party/subject identity-resolution behavior;
6. temporal/timeline visualization;
7. legal-domain search and discovery providers;
8. concrete storage technology and SLA parameters;
9. detailed UI technology;
10. jurisdiction-specific legal-domain models;
11. legal research/precedent capabilities;
12. broader capability promotion based on later P0 slices.

These shall be resolved only when implementation evidence or an authoritative specification requires them.

---

## 21. Status

This specification is **APPROVED** and is intended to drive the VS-L01 reference-application implementation and its supporting verification evidence.
