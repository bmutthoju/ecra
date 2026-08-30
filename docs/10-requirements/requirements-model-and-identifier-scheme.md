# ECRA Generation 1 — Requirements Model and Identifier Scheme

> Status: DRAFT
> Authority: IMPLEMENTATION
> Generation: GEN1
> Scope: Requirements model and identifier scheme

## 1. Purpose

This document defines the requirements model and identifier scheme used to establish the ECRA Generation 1 requirements baseline.

It provides the structural contract for expressing, identifying, versioning, classifying, tracing, and governing Gen1 requirements. It does not itself define the complete set of Gen1 functional requirements.

## 2. Authority and Scope

The Gen1 requirements baseline is governed by the repository document authority hierarchy defined in `AGENTS.md`.

ECRA-1100 is the requirements and requirements-traceability authority. ECRA-1000 remains the authority for architectural semantics. Shared semantic concepts are governed by the applicable approved ECRA semantic foundation.

This document defines how Gen1 requirements are represented; it does not redefine ECRA-1000, ECRA-1100, or the Shared Semantic Foundation.

## 3. Requirements Model

A Gen1 requirement is an explicit, uniquely identifiable, versioned statement of required system behavior, property, constraint, capability, or quality characteristic that is within the approved Gen1 scope.

The requirements model distinguishes:

- requirement identity;
- requirement version;
- requirement statement;
- requirement classification;
- requirement rationale and source basis;
- applicability and scope;
- dependencies and constraints;
- lifecycle state;
- provenance;
- traceability relationships;
- verification and acceptance criteria;
- baseline and release association.

A requirement is not defined by its representation format. JSON, YAML, Markdown, a database record, or another representation is an implementation or exchange concern unless explicitly standardized elsewhere.

## 4. Requirement Identity

Every Gen1 requirement MUST have a stable logical identity.

Identity MUST remain stable across revisions of the same logical requirement.

A revision MUST NOT be represented as a new logical requirement merely because its statement, rationale, metadata, or verification information changes.

Identity and version are distinct concepts:

```text
Requirement Identity
    |
    +-- Version 1
    +-- Version 2
    +-- Version 3
```

Published requirement history MUST remain reconstructable.

## 5. Requirement Identifier Scheme

### 5.1 Canonical Identifier

The canonical Gen1 requirement identifier scheme is:

```text
ECRA-G1-<DOMAIN>-<NNNN>
```

where:

- `ECRA` identifies the project;
- `G1` identifies Generation 1;
- `<DOMAIN>` identifies the requirement domain;
- `<NNNN>` is a zero-padded sequential numeric identifier within the domain.

Examples:

```text
ECRA-G1-FUN-0001
ECRA-G1-SEM-0001
ECRA-G1-INT-0001
ECRA-G1-EVL-0001
ECRA-G1-OPS-0001
ECRA-G1-VRF-0001
```

The identifier is an identity, not a version number and not a lifecycle state.

### 5.2 Domain Codes

The initial domain vocabulary is:

| Code | Domain | Purpose |
|---|---|---|
| `FUN` | Functional | Required system capabilities and behaviors |
| `SEM` | Semantic | Semantic representation, identity, relationships, and constraints |
| `INT` | Integrity | Evidence, source, provenance, and contextual integrity |
| `EVL` | Evaluation | Evaluation behavior and evaluation results |
| `TRC` | Traceability | Gen1 engineering traceability obligations |
| `OPS` | Operations | Persistence, observability, security, reliability, and operational behavior |
| `VRF` | Verification | Verification, conformance, reproducibility, and acceptance obligations |
|

Additional domain codes require an explicit approved decision when they introduce a materially distinct requirements domain.

### 5.3 Identifier Properties

A canonical identifier MUST:

- be unique within the Gen1 requirements baseline;
- remain stable for the lifetime of the logical requirement;
- be independent of storage location;
- be independent of serialization format;
- not encode lifecycle state;
- not encode requirement version;
- not be reused after retirement;
- be suitable for use in traceability relationships.

## 6. Requirement Version

A requirement version identifies a particular revision of a logical requirement.

The recommended representation is:

```text
<Requirement Identifier>@<major>.<minor>
```

For example:

```text
ECRA-G1-FUN-0001@1.0
ECRA-G1-FUN-0001@1.1
ECRA-G1-FUN-0001@2.0
```

The exact versioning policy is governed by the applicable ECRA-0000 versioning rules and shall not be duplicated here.

A version MUST preserve its relationship to its predecessor and successor where applicable.

Published versions MUST be immutable.

## 7. Requirement Classification

Each requirement MUST have a primary classification.

The initial classifications are:

- Functional
- Semantic
- Integrity
- Evaluation
- Traceability
- Operational
- Verification

A requirement MAY have secondary tags or classifications when necessary, but a primary classification MUST remain available for deterministic organization and analysis.

Classification does not determine ownership. Semantic ownership follows the ECRA portfolio ownership model.

## 8. Requirement Statement

A normative requirement statement MUST express one materially distinct obligation whenever practical.

Normative language MUST follow the canonical project terminology and normative-language conventions.

A requirement SHOULD be atomic enough that its satisfaction can be independently assessed.

A requirement SHOULD avoid embedding implementation technology unless the technology is itself an approved requirement.

A requirement MUST NOT silently introduce capabilities excluded by the approved Gen1 scope.

## 9. Requirement Metadata

A Gen1 requirement record SHOULD provide, as applicable:

```text
id
version
classification
statement
rationale
scope
status
source_basis
owner
applicability
predecessor
successor
dependencies
constraints
acceptance_criteria
verification_reference
architecture_reference
implementation_reference
provenance
baseline
```

The metadata model MUST remain compatible with the shared semantic foundation and ECRA-1100.

## 10. Requirement Lifecycle

Requirements MUST have an explicit lifecycle state.

The detailed lifecycle is governed by ECRA-1100. The Gen1 implementation MUST preserve lifecycle transitions, transition history, and applicable authorization information rather than treating status as an unconstrained mutable field.

At minimum, the implementation must distinguish requirements that are:

- being developed;
- proposed for approval;
- approved;
- superseded or deprecated; and
- retired.

The precise canonical lifecycle vocabulary SHALL be taken from the authoritative ECRA-1100 baseline and any approved shared semantic foundation.

## 11. Requirement Traceability

Requirements MUST participate in explicit typed traceability relationships.

The initial Gen1 traceability model shall support, where applicable:

```text
Requirement
   |
   +-- ALLOCATED_TO ------> Architecture Element
   +-- IMPLEMENTED_BY ----> Implementation Artifact
   +-- VERIFIED_BY -------> Verification Artifact
   +-- VALIDATED_BY ------> Validation Artifact
   +-- EVIDENCED_BY ------> Evidence
   +-- DERIVED_FROM ------> Requirement / Source
   +-- REFINES -----------> Requirement
   +-- DEPENDS_ON --------> Requirement / Artifact
   +-- CONSTRAINS --------> Artifact / Requirement
   +-- SUPERSEDES -------> Requirement Version
```

The canonical relationship ontology remains subject to the SSF reconciliation identified during implementation-baseline establishment. Existing ECRA-1100 relationship semantics MUST NOT be silently renamed or redefined as part of implementation.

Traceability is a graph capability. Matrices, reports, and dashboards are derived views and MUST NOT become competing semantic sources.

## 12. Requirement-to-Architecture Contract

ECRA-1100 requirements may reference and allocate to architectural elements defined by ECRA-1000.

ECRA-1100 MUST NOT redefine the semantic meaning of an ECRA-1000 architectural element.

The canonical relationship is conceptually:

```text
Requirement
    |
    | ALLOCATED_TO
    v
Architecture Element
```

The implementation SHOULD represent the architecture reference by stable identity rather than duplicating the architecture object inside the requirement record.

## 13. Requirement-to-Evidence Contract

Requirements-related assertions and conformance claims SHOULD be traceable to evidence where required by the applicable specification.

ECRA-1100 consumes ECRA evidence semantics; it does not create a competing definition of Evidence.

The implementation SHOULD reference evidence by stable identity and preserve provenance rather than copying evidence content into requirements records.

## 14. Requirement-to-Verification Contract

A requirement may be linked to verification artifacts or activities.

ECRA-1100 defines the requirements-traceability relationship; verification methodology and execution remain outside this document unless explicitly required by Gen1.

The implementation MUST preserve the distinction between:

- a requirement;
- a verification specification or activity;
- verification evidence; and
- a verification result.

## 15. Baselines and Releases

A requirements baseline is a named, immutable set of requirement versions selected for a defined purpose or release.

Once published, a baseline MUST be reconstructable and MUST NOT be silently rewritten.

Changes to a baseline MUST be represented through explicit versioning, change history, and impact relationships.

## 16. Requirement Quality Invariants

The implementation shall enforce or verify, as applicable:

1. every requirement has a stable identity;
2. every requirement version belongs to exactly one logical requirement identity;
3. version lineage is reconstructable;
4. published versions are immutable;
5. every typed relationship references valid endpoints;
6. relationship semantics are explicit;
7. requirement lifecycle transitions are governed;
8. requirements within a released baseline are identifiable;
9. applicable architecture, implementation, verification, and evidence links are traceable;
10. historical state can be reconstructed for a published baseline.

## 17. Requirement ID Allocation

Identifiers MUST be allocated centrally within the Gen1 requirements baseline to prevent collisions.

Identifiers MUST NOT be recycled.

A deleted or retired requirement identifier remains permanently associated with its historical requirement identity.

The allocation mechanism itself is an implementation concern and may initially be a repository-controlled registry or equivalent deterministic mechanism. A distributed semantic registry is deferred.

## 18. Requirements Traceability to the Project Scope

The first Gen1 requirement domains are derived from the approved project scope:

```text
Claim Evaluation
Evidence Integrity
Source Authenticity / Authority
Contextual Integrity
Provenance / Traceability
Deterministic Behavior
Production Quality
Verifiable Results
```

The project scope also establishes explicit non-goals, including unrestricted crawling, general-purpose content generation, speculative AI capabilities, ecosystem expansion, and Generation 2 architecture. Requirements MUST NOT be created for these capabilities unless the approved scope is explicitly changed.

## 19. Relationship to ECRA-1100

This document operationalizes the requirements-modeling portion of ECRA-1100 for the Gen1 reference implementation.

ECRA-1100 remains the authoritative requirements and traceability framework. This document must not be interpreted as a replacement for the ECRA-1100 standard.

Where this document conflicts with an approved ECRA-1100 requirement, the applicable higher-authority document takes precedence and the conflict must be recorded and resolved rather than hidden.

## 20. Open Items

The following remain intentionally unresolved until the relevant semantic or normative decisions are approved:

- final canonical SSF relationship names and inverse rules;
- final universal lifecycle vocabulary;
- final universal metadata contract;
- final semantic registry authority;
- final machine-readable representation contract;
- exact major/minor versioning semantics under ECRA-0000.

These open items MUST NOT be resolved through implementation convenience.
