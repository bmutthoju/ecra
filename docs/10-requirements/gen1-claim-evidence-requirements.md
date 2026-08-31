# ECRA Generation 1 — Claim and Evidence Requirements

> Status: APPROVED
> Authority: IMPLEMENTATION
> Generation: GEN1
> Scope: Claim and evidence requirements

## 1. Purpose

This document defines the first set of ECRA Generation 1 product requirements for the Claim and Evidence portion of the approved evaluation path.

It establishes requirements for representing claims, evidence, sources, acquired artifacts, integrity, and provenance. It does not define the complete Gen1 evaluation engine, context model, operational platform, or verification framework.

Concrete real-life examples and usage scenarios are intentionally kept outside this normative requirements document. They should be provided by a separate informative examples/scenarios document when needed.

## 2. Authority and Scope

The [approved Gen1 project vision](../00-project/vision.md) and [approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md) establish the product scope and objectives. The [approved Gen1 terminology](../00-project/terminology.md) establishes canonical product-domain terminology.

ECRA-1000 provides the architectural foundation; ECRA-1100 provides the requirements and traceability framework; and the applicable approved shared semantic foundation governs genuinely portfolio-wide semantic concepts. These authorities MUST be used rather than redefined locally.

This document operationalizes those authorities for Gen1. It MUST NOT redefine their domain semantics.

The requirements in this document are product/system requirements. ECRA-1100 remains the authority for how these requirements are identified, versioned, traced, baselined, and verified.

The repository follows a document hierarchy in which higher-level documents establish scope, terminology, and governing constraints, while lower-level documents elaborate them. Detailed references should point to the applicable higher-level authority rather than duplicating or redefining it.

## 3. Requirement Identifier Allocation

The requirements in this document use the identifier scheme established by `requirements-model-and-identifier-scheme.md`.

Initial identifiers are allocated in the `FUN`, `INT`, `SEM`, and `TRC` domains according to the primary obligation of each requirement. The domain identifies the requirement's primary obligation; it does not imply exclusive semantic ownership of every concept mentioned by the requirement.

## 4. Claim Requirements

### ECRA-G1-FUN-0001 — Claim representation

The system MUST represent a claim as a uniquely identifiable proposition that can be submitted for evaluation.

**Rationale:** A claim is the primary subject of Gen1 evaluation.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md), [approved Gen1 vision](../00-project/vision.md).

**Verification criteria:** Demonstrate that an identifiable claim can be represented, retrieved, and submitted to the Gen1 evaluation path.

**Verification method:** Contract and integration verification.

### ECRA-G1-FUN-0002 — Claim evaluation eligibility

The system MUST be able to determine whether a represented claim has the minimum information required to enter the Gen1 evaluation path.

**Rationale:** The evaluation path must reject structurally incomplete inputs deterministically rather than treating missing information as successful evaluation input.

**Source basis:** [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md); approved Claim and Evidence domain scope.

**Verification criteria:** Demonstrate deterministic acceptance and rejection of representative claim inputs at the evaluation boundary.

**Verification method:** Boundary-condition verification.

### ECRA-G1-SEM-0001 — Claim identity

Each represented claim MUST have a stable identity that is independent of its storage location and serialization format.

**Rationale:** Stable identity is required for provenance and bidirectional traceability.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md); ECRA-1100 identity and traceability principles; applicable shared semantic identity foundation.

**Verification criteria:** Demonstrate that supported representation or storage changes do not change the logical claim identity.

**Verification method:** Identity and contract verification.

## 5. Evidence Requirements

### ECRA-G1-FUN-0003 — Evidence representation

The system MUST represent evidence as information that is relevant to determining whether, or to what extent, a claim is established.

**Rationale:** Evidence is a primary input to claim evaluation.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md); [approved Gen1 vision](../00-project/vision.md).

**Verification criteria:** Demonstrate representation of evidence and its association with an evaluable claim.

**Verification method:** Integration verification.

### ECRA-G1-FUN-0004 — Evidence-to-claim association

The system MUST support an explicit association between evidence and the claim or claims for which the evidence is relevant.

**Rationale:** Evidence relevance must be represented explicitly rather than inferred solely from storage or retrieval context.

**Source basis:** [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md); ECRA-1000 evidence and traceability semantics.

**Verification criteria:** Demonstrate creation, retrieval, and traversal of the evidence-to-claim association.

**Verification method:** Relationship contract verification.

### ECRA-G1-INT-0001 — Evidence integrity

The system MUST preserve sufficient information to determine whether an acquired evidence artifact has been altered or corrupted after acquisition, where the applicable acquisition mechanism permits such determination.

**Rationale:** Evidence integrity is an explicit Gen1 goal and is necessary for trustworthy evaluation.

**Source basis:** [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md); [approved Gen1 terminology](../00-project/terminology.md).

**Verification criteria:** Demonstrate detection or representation of integrity failure for supported integrity mechanisms.

**Verification method:** Integrity verification.

### ECRA-G1-SEM-0002 — Evidence identity and lineage

An evidence item MUST have stable identity and MUST preserve its applicable version or lineage information independently of its representation format.

**Rationale:** Evidence must remain traceable across representations and revisions.

**Source basis:** Applicable shared semantic identity/version foundation; ECRA-1000 provenance semantics.

**Verification criteria:** Demonstrate reconstruction of supported evidence history across supported representations or revisions.

**Verification method:** Identity and lineage verification.

## 6. Source Requirements

### ECRA-G1-FUN-0005 — Source representation

The system MUST represent the identifiable origin from which source material or evidence was obtained or attributed.

**Rationale:** Evaluation requires explicit distinction between information and its source.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md).

**Verification criteria:** Demonstrate association of source material or evidence with an identifiable source.

**Verification method:** Integration verification.

### ECRA-G1-INT-0002 — Source authenticity

Where authenticity can be assessed by the supported acquisition or validation mechanism, the system MUST preserve the result and relevant basis of source-authenticity assessment.

**Rationale:** Source authenticity is an explicit Gen1 trust property and MUST NOT be collapsed into source authority.

**Source basis:** [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md); [approved Gen1 terminology](../00-project/terminology.md).

**Verification criteria:** Demonstrate that authenticity assessment results are represented distinctly from source-authority information.

**Verification method:** Contract and boundary verification.

### ECRA-G1-INT-0003 — Source authority

The system MUST represent source-authority information separately from source authenticity information when determining the basis on which a source is considered authoritative for an evaluation.

**Rationale:** Authenticity establishes whether a source is genuine or attributable; authority concerns whether it is appropriate to rely upon for the relevant evaluation.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md); [approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md).

**Verification criteria:** Demonstrate independent representation and retrieval of authenticity and authority information.

**Verification method:** Contract verification.

## 7. Acquired Artifact Requirements

### ECRA-G1-FUN-0006 — Acquired artifact preservation

Where ECRA acquires source material for evaluation, the system MUST preserve a representation of the acquired artifact sufficient to support subsequent integrity, provenance, and traceability processing.

**Rationale:** The acquired representation is the object actually obtained by ECRA and must not be conflated with an abstract source or claim.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md).

**Verification criteria:** Demonstrate preservation and retrieval of an acquired artifact together with its applicable identity and provenance.

**Verification method:** Integration verification.

### ECRA-G1-INT-0004 — Artifact integrity information

Where an acquired artifact is subject to an applicable integrity mechanism, the system MUST preserve the information necessary to reproduce or assess the artifact-integrity determination.

**Rationale:** Artifact integrity is distinct from source authenticity and must remain auditable.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md); approved evidence-integrity goal.

**Verification criteria:** Demonstrate that supported integrity metadata remains associated with the acquired artifact and permits the applicable integrity determination to be reproduced or assessed.

**Verification method:** Integrity verification.

## 8. Provenance Requirements

### ECRA-G1-INT-0005 — Provenance preservation

The system MUST preserve provenance sufficient to reconstruct the relevant origin, acquisition, transformation where applicable, and association history of claims, evidence, sources, and acquired artifacts within the Gen1 evaluation path.

**Rationale:** Provenance is required to support trustworthy evaluation and traceability.

**Source basis:** [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md); [approved Gen1 terminology](../00-project/terminology.md); ECRA-1000 provenance semantics.

**Verification criteria:** Demonstrate reconstruction of provenance for a representative evaluation input, including applicable transformations where they occur.

**Verification method:** End-to-end verification.

### ECRA-G1-SEM-0003 — Provenance identity references

Provenance records MUST reference affected entities by stable identity rather than relying solely on mutable storage locations or serialized content.

**Rationale:** Provenance must remain reconstructable when storage or representation changes.

**Source basis:** Applicable shared semantic identity foundation; ECRA-1100 traceability principles.

**Verification criteria:** Demonstrate provenance continuity across supported representation or storage changes.

**Verification method:** Contract and serialization verification.

## 9. Integrity Boundary Requirements

### ECRA-G1-INT-0006 — Integrity status shall not imply truth

The system MUST NOT treat successful artifact, evidence, or source-integrity checks as proof that the substantive claim represented by the information is true.

**Rationale:** Integrity establishes properties of information or origin; it does not by itself establish the truth of a claim.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md); [approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md).

**Verification criteria:** Demonstrate that integrity success cannot by itself produce a positive claim-evaluation result.

**Verification method:** Negative verification.

### ECRA-G1-INT-0007 — Authenticity shall not imply authority

The system MUST NOT treat successful source-authenticity assessment as sufficient evidence that the source is authoritative for a particular evaluation.

**Rationale:** Source authenticity and source authority are distinct approved Gen1 concepts.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md); [approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md).

**Verification criteria:** Demonstrate independent handling of authenticity and authority.

**Verification method:** Negative and boundary verification.

## 10. Traceability Requirements

### ECRA-G1-TRC-0001 — Claim/evidence traceability

The system MUST maintain explicit, typed, and traversable traceability between an evaluated claim and the evidence, source, acquired artifact, and provenance entities materially used in its evaluation.

**Rationale:** Gen1 evaluation results must be explainable and reconstructable from their inputs.

**Source basis:** [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md); ECRA-1100 traceability framework; ECRA-1000 provenance and evidence semantics.

**Verification criteria:** Demonstrate traversal from an evaluation input to its supporting entities and reconstruction of the corresponding relationships. The required semantic relationships need not be physically materialized in both directions when canonical inverse rules permit derivation.

**Verification method:** End-to-end and relationship verification.

### ECRA-G1-TRC-0002 — Traceability preservation

Traceability relationships used by a Gen1 evaluation MUST remain reconstructable for the corresponding released or baselined evaluation record.

**Rationale:** Historical evaluation results must remain auditable after subsequent changes to source or repository state.

**Source basis:** ECRA-1100 baseline, lineage, and historical reconstruction principles.

**Verification criteria:** Demonstrate reconstruction of the applicable traceability relationships after creation of a later revision.

**Verification method:** Baseline and replay verification.

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
| [Approved Gen1 project vision](../00-project/vision.md) | Product scope and objectives |
| [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md) | Gen1 scope boundaries and implementation objectives |
| [Approved Gen1 terminology](../00-project/terminology.md) | Canonical product-domain terminology |
| ECRA-1000 | Architecture, evidence, provenance, and architectural semantics |
| ECRA-1100 | Requirement identity, traceability, lifecycle, evidence linkage, and engineering governance |
| Shared Semantic Foundation | Shared identity, relationship, provenance, and constraint foundations where approved/applicable |

ECRA-1000, ECRA-1100, and the applicable Shared Semantic Foundation references will be linked to their authoritative repository documents when those documents are incorporated into the repository. Until then, their names are retained as authoritative source references rather than replaced with guessed repository paths.

The document hierarchy is intentional: project-level documents establish scope and terminology; requirements documents define what the system must do; architecture and design documents elaborate how it is structured and behaves; implementation documents provide implementation guidance; and verification documents establish conformance.

## 13. Open Items

The following remain outside this PR and MUST be resolved before the relevant later implementation work:

- final canonical SSF relationship names and inverse rules;
- complete Context requirements;
- complete Evaluation requirements;
- evaluation decision/result semantics beyond the Claim/Evidence boundary;
- concrete acquisition mechanisms;
- complete operational requirements;
- complete verification/conformance requirements.

Concrete real-life examples and scenarios for these requirements should be maintained separately as informative material rather than embedded in this normative requirements document.
