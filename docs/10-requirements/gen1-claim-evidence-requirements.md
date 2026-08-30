# ECRA Generation 1 — Claim and Evidence Requirements

> Status: DRAFT
> Authority: IMPLEMENTATION
> Generation: GEN1
> Scope: Claim and evidence requirements

## 1. Purpose

This document defines the first set of ECRA Generation 1 product requirements for the Claim and Evidence portion of the approved evaluation path.

It establishes requirements for representing claims, evidence, sources, acquired artifacts, integrity, and provenance. It does not define the complete Gen1 evaluation engine, context model, operational platform, or verification framework.

## 2. Authority and Scope

The approved Gen1 project scope is the primary product-scope authority. ECRA-1000 provides the architectural foundation; ECRA-1100 provides the requirements and traceability framework; and the applicable approved shared semantic foundation governs genuinely portfolio-wide semantic concepts.

This document operationalizes those authorities for Gen1. It MUST NOT redefine their domain semantics.

The requirements in this document are product/system requirements. ECRA-1100 remains the authority for how these requirements are identified, versioned, traced, baselined, and verified.

## 3. Requirement Identifier Allocation

The requirements in this document use the identifier scheme established by `requirements-model-and-identifier-scheme.md`.

Initial identifiers are allocated in the `FUN`, `INT`, and `SEM` domains according to the primary obligation of each requirement.

## 4. Claim Requirements

### ECRA-G1-FUN-0001 — Claim representation

The system MUST represent a claim as a uniquely identifiable proposition that can be submitted for evaluation.

**Rationale:** Claim is the primary subject of Gen1 evaluation.

**Source basis:** Approved Gen1 project terminology and vision.

**Verification:** Contract and integration verification MUST demonstrate creation, retrieval, and evaluation submission of an identifiable claim.

### ECRA-G1-FUN-0002 — Claim evaluation eligibility

The system MUST be able to determine whether a represented claim has the minimum information required to enter the Gen1 evaluation path.

**Rationale:** The evaluation path must reject structurally incomplete inputs deterministically rather than treating missing information as successful evaluation input.

**Source basis:** Approved Gen1 scope; Claim and Evidence domain.

**Verification:** Boundary-condition tests MUST demonstrate deterministic acceptance and rejection of representative claim inputs.

### ECRA-G1-SEM-0001 — Claim identity

Each represented claim MUST have a stable identity that is independent of its storage location and serialization format.

**Rationale:** Stable identity is required for provenance and bidirectional traceability.

**Source basis:** Approved project terminology; ECRA-1100 identity and traceability principles; shared semantic identity foundation.

**Verification:** Identity persistence and serialization-independence tests MUST demonstrate that representation changes do not change logical claim identity.

## 5. Evidence Requirements

### ECRA-G1-FUN-0003 — Evidence representation

The system MUST represent evidence as information that is relevant to determining whether, or to what extent, a claim is established.

**Rationale:** Evidence is a primary input to claim evaluation.

**Source basis:** Approved Gen1 terminology and evaluation scope.

**Verification:** Integration verification MUST demonstrate association of evidence with an evaluable claim.

### ECRA-G1-FUN-0004 — Evidence-to-claim association

The system MUST support an explicit association between evidence and the claim or claims for which the evidence is relevant.

**Rationale:** Evidence relevance must be represented explicitly rather than inferred solely from storage or retrieval context.

**Source basis:** Gen1 evaluation path; ECRA-1000 evidence and traceability semantics.

**Verification:** Relationship contract tests MUST demonstrate creation, retrieval, and traversal of the association.

### ECRA-G1-INT-0001 — Evidence integrity

The system MUST preserve sufficient information to determine whether an acquired evidence artifact has been altered or corrupted after acquisition, where the applicable acquisition mechanism permits such determination.

**Rationale:** Evidence integrity is an explicit Gen1 goal and is necessary for trustworthy evaluation.

**Source basis:** Approved Gen1 goals and terminology.

**Verification:** Tests MUST demonstrate detection or representation of integrity failure for supported integrity mechanisms.

### ECRA-G1-SEM-0002 — Evidence identity and lineage

An evidence item MUST have stable identity and MUST preserve its applicable version or lineage information independently of its representation format.

**Rationale:** Evidence must remain traceable across representations and revisions.

**Source basis:** Shared semantic identity/version foundation; ECRA-1000 provenance semantics.

**Verification:** Version-lineage tests MUST demonstrate reconstructability of supported evidence history.

## 6. Source Requirements

### ECRA-G1-FUN-0005 — Source representation

The system MUST represent the identifiable origin from which source material or evidence was obtained or attributed.

**Rationale:** Evaluation requires explicit distinction between information and its source.

**Source basis:** Approved Gen1 terminology.

**Verification:** Integration tests MUST demonstrate association of source material/evidence with an identifiable source.

### ECRA-G1-INT-0002 — Source authenticity

Where authenticity can be assessed by the supported acquisition or validation mechanism, the system MUST preserve the result and relevant basis of source-authenticity assessment.

**Rationale:** Source authenticity is an explicit Gen1 trust property and MUST NOT be collapsed into source authority.

**Source basis:** Approved Gen1 goals and terminology.

**Verification:** Tests MUST demonstrate that authenticity assessment results are represented distinctly from source-authority information.

### ECRA-G1-INT-0003 — Source authority

The system MUST represent source-authority information separately from source authenticity information when determining the basis on which a source is considered authoritative for an evaluation.

**Rationale:** Authenticity establishes whether a source is genuine or attributable; authority concerns whether it is appropriate to rely upon for the relevant evaluation.

**Source basis:** Approved Gen1 terminology.

**Verification:** Contract tests MUST demonstrate independent representation and retrieval of authenticity and authority information.

## 7. Acquired Artifact Requirements

### ECRA-G1-FUN-0006 — Acquired artifact preservation

Where ECRA acquires source material for evaluation, the system MUST preserve a representation of the acquired artifact sufficient to support subsequent integrity, provenance, and traceability processing.

**Rationale:** The acquired representation is the object actually obtained by ECRA and must not be conflated with an abstract source or claim.

**Source basis:** Approved Gen1 terminology.

**Verification:** Integration verification MUST demonstrate preservation and retrieval of an acquired artifact together with its applicable identity and provenance.

### ECRA-G1-INT-0004 — Artifact integrity information

Where an acquired artifact is subject to an applicable integrity mechanism, the system MUST preserve the information necessary to reproduce or assess the artifact-integrity determination.

**Rationale:** Artifact integrity is distinct from source authenticity and must remain auditable.

**Source basis:** Approved Gen1 terminology and evidence-integrity goal.

**Verification:** Tests MUST demonstrate that supported integrity metadata remains associated with the acquired artifact.

## 8. Provenance Requirements

### ECRA-G1-INT-0005 — Provenance preservation

The system MUST preserve provenance sufficient to reconstruct the relevant origin, acquisition, transformation, and association history of claims, evidence, sources, and acquired artifacts within the Gen1 evaluation path.

**Rationale:** Provenance is required to support trustworthy evaluation and traceability.

**Source basis:** Approved Gen1 goals and terminology; ECRA-1000 provenance semantics.

**Verification:** End-to-end verification MUST demonstrate reconstruction of provenance for a representative evaluation input.

### ECRA-G1-SEM-0003 — Provenance identity references

Provenance records MUST reference affected entities by stable identity rather than relying solely on mutable storage locations or serialized content.

**Rationale:** Provenance must remain reconstructable when storage or representation changes.

**Source basis:** Shared semantic identity foundation and ECRA-1100 traceability principles.

**Verification:** Repository and serialization tests MUST demonstrate provenance continuity across supported representation changes.

## 9. Integrity Boundary Requirements

### ECRA-G1-INT-0006 — Integrity status shall not imply truth

The system MUST NOT treat successful artifact, evidence, or source-integrity checks as proof that the substantive claim represented by the information is true.

**Rationale:** Integrity establishes properties of information or origin; it does not by itself establish the truth of a claim.

**Source basis:** Approved Gen1 terminology and evaluation scope.

**Verification:** Negative tests MUST demonstrate that integrity success cannot by itself produce a positive claim-evaluation result.

### ECRA-G1-INT-0007 — Authenticity shall not imply authority

The system MUST NOT treat successful source-authenticity assessment as sufficient evidence that the source is authoritative for a particular evaluation.

**Rationale:** Source authenticity and source authority are distinct approved Gen1 concepts.

**Source basis:** Approved Gen1 terminology.

**Verification:** Negative and boundary tests MUST demonstrate independent handling of authenticity and authority.

## 10. Traceability Requirements

### ECRA-G1-TRC-0001 — Claim/evidence traceability

The system MUST maintain explicit, typed, and traversable traceability between an evaluated claim and the evidence, source, acquired artifact, and provenance entities materially used in its evaluation.

**Rationale:** Gen1 evaluation results must be explainable and reconstructable from their inputs.

**Source basis:** Approved Gen1 provenance/traceability goals; ECRA-1100 traceability framework.

**Verification:** End-to-end tests MUST demonstrate bidirectional traversal from an evaluation input to its supporting entities and back to the evaluation input.

### ECRA-G1-TRC-0002 — Traceability preservation

Traceability relationships used by a Gen1 evaluation MUST remain reconstructable for the corresponding released or baselined evaluation record.

**Rationale:** Historical evaluation results must remain auditable after subsequent changes to source or repository state.

**Source basis:** ECRA-1100 baseline, lineage, and historical reconstruction principles.

**Verification:** Baseline/replay tests MUST demonstrate reconstruction after creation of a later revision.

## 11. Scope Boundaries

These requirements do not establish:

- a general-purpose web crawler;
- unrestricted source acquisition;
- a general content-generation system;
- a general-purpose search engine;
- a Generation 2 reasoning or agent platform;
- a universal semantic registry service;
- a complete verification methodology;
- a complete compliance/certification service.

Such capabilities require separate approved scope or standards and MUST NOT be inferred from these requirements.

## 12. Requirement-to-Source Alignment

The principal source categories for this requirement set are:

| Source | Role |
|---|---|
| Approved Gen1 project vision/goals | Product scope and objectives |
| Approved Gen1 terminology | Canonical product-domain terminology |
| ECRA-1000 | Architecture, evidence, provenance, and architectural semantics |
| ECRA-1100 | Requirement identity, traceability, lifecycle, evidence linkage, and engineering governance |
| Shared Semantic Foundation | Shared identity, relationship, provenance, and constraint foundations where approved/applicable |

The detailed repository-level source links will be added when the corresponding authoritative ECRA documents are incorporated into the repository.

## 13. Open Items

The following remain outside this PR and MUST be resolved before the relevant later implementation work:

- final canonical SSF relationship names and inverse rules;
- complete Context requirements;
- complete Evaluation requirements;
- evaluation decision/result semantics beyond the Claim/Evidence boundary;
- concrete acquisition mechanisms;
- complete operational requirements;
- complete verification/conformance requirements.
