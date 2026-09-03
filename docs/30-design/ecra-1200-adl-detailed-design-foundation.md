# ECRA-1200 — ADL Detailed Design Foundation

> Status: REVIEW
> Authority: NORMATIVE
> Generation: GEN1
> Scope: Detailed design foundation for the ECRA Architecture Description Language
> Depends on: ECRA-1200 Architecture Description Language baseline

## 1. Purpose

This document establishes the first detailed-design increment for ECRA-1200. It translates the approved ECRA-1200 architecture baseline into a more precise logical design without prematurely defining implementation-specific schemas, storage structures, serialization formats, or runtime components.

The design establishes the canonical logical structure of an Architecture Description and the relationships among its principal ADL constructs. Subsequent design increments may refine individual constructs, invariants, representation rules, and implementation contracts without changing this foundation except through an approved architectural change.

## 2. Design Scope

This increment defines:

- the logical composition of an Architecture Description;
- the identity model for ADL-owned constructs;
- the logical structure of architectural elements and relationships;
- the logical structure of constraints and assertions;
- the logical relationship among stakeholders, concerns, viewpoints, and views;
- traceability participation;
- provenance and lifecycle participation;
- logical integrity rules;
- design boundaries for machine representation.

This increment does not define:

- programming-language classes or interfaces;
- database tables or storage engines;
- concrete JSON, YAML, XML, RDF, or binary schemas;
- transport or interchange protocols;
- executable validation algorithms;
- proof or reasoning engines;
- governance workflows;
- UI or visualization implementations.

## 3. Design Principles

The detailed design shall preserve the following architecture-level principles:

1. **Single semantic identity** — an ADL subject has one identity independent of its representations and views.
2. **Single semantic ownership** — shared concepts retain their authoritative semantics in their owning specifications.
3. **Explicit relationships** — semantic relationships are represented explicitly rather than inferred from presentation.
4. **Technology independence** — logical design is independent of implementation technology.
5. **Semantic preservation** — transformations must preserve required architectural meaning.
6. **Stable core, extensible edge** — extensions specialize existing constructs without silently redefining them.
7. **Explicit provenance and lifecycle** — material architectural content remains attributable and lifecycle-aware where applicable.

## 4. Logical Architecture Description Model

An Architecture Description is the bounded semantic container for architectural content described using ADL.

Conceptually:

```text
Architecture Description
|
+-- Architectural Elements
|   +-- properties
|   +-- lifecycle
|   +-- provenance
|   +-- constraints
|   +-- assertions
|   +-- relationships
|   +-- traceability
|
+-- Architectural Relationships
|
+-- Architectural Constraints
|
+-- Architectural Assertions
|
+-- Viewpoints
|
+-- Views
|
+-- Context References
|   +-- Architecture
|   +-- Stakeholders
|   +-- Concerns
|   +-- Requirements
|
+-- Extensions
```

The model is logical rather than a serialization schema. A conforming implementation may use another internal representation provided that the required semantics are preserved.

### 4.1 Ownership of the Description

ECRA-1200 owns the semantics of the **Architecture Description** as an ADL construct.

The Architecture Description may reference concepts owned by ECRA-1000, ECRA-1100, SSF, or other applicable specifications. Such references do not transfer ownership of those concepts to ECRA-1200.

### 4.2 Description Scope

Each Architecture Description shall have an explicit description scope sufficient to determine what architectural subject matter it intends to describe.

Scope may be expressed through references to architectural subjects, concerns, viewpoints, lifecycle boundaries, organizational boundaries, temporal boundaries, or other applicable context.

Scope is contextual and does not require a universal decomposition of architecture.

## 5. Identity Model

Every ADL-owned semantic subject shall have a stable identity that is independent of:

- its view;
- its notation;
- its physical representation;
- its storage location;
- its serialization format;
- its lifecycle state.

### 5.1 Identity Requirements

An identity shall:

- be unique within its applicable identity domain;
- remain stable across conforming representations of the same subject;
- be referenceable by related constructs;
- not depend on presentation labels;
- not be reused for a semantically different subject within the applicable lifecycle rules.

### 5.2 Labels

Human-readable names and labels are descriptive properties and shall not be treated as semantic identity unless an owning specification explicitly establishes such semantics.

### 5.3 Identity Across Views

When an architectural subject appears in multiple views, each representation shall refer to the same semantic identity where it represents the same subject.

A view-specific visual identifier shall not silently replace the underlying semantic identity.

## 6. Architectural Element Design

An Architectural Element is the principal ADL construct for representing an identifiable architectural subject.

The logical form is:

```text
Architectural Element
+-- identity
+-- type
+-- properties
+-- lifecycle state
+-- provenance
+-- relationships
+-- constraints
+-- assertions
+-- traceability references
+-- extension metadata
```

### 6.1 Element Type

Each element shall have a semantic type identifying the applicable ADL specialization or external/owned type.

Element types shall be extensible. A specialization shall identify its base semantic type and shall not introduce incompatible semantics without an explicit specialization rule.

### 6.2 Properties

Properties represent semantic characteristics of an element. A property shall have an identifiable meaning and applicable value semantics.

Presentation-only attributes shall not be treated as semantic properties unless explicitly defined as such.

### 6.3 Lifecycle

Lifecycle state is represented separately from semantic identity. A lifecycle transition shall not implicitly create a new semantic identity unless the applicable lifecycle semantics explicitly require a new subject.

### 6.4 Provenance

Where provenance is applicable, an element shall be capable of being associated with information identifying its origin, derivation, or relevant transformation history according to the applicable foundation semantics.

## 7. Architectural Relationship Design

An Architectural Relationship is an explicit semantic association between architectural subjects.

The logical form is:

```text
Architectural Relationship
+-- identity
+-- relationship type
+-- source
+-- target
+-- properties
+-- lifecycle
+-- provenance
+-- constraints
+-- assertions
+-- extension metadata
```

### 7.1 Endpoints

A relationship shall identify its semantic source and target, subject to the domain and range rules of its relationship type.

Endpoints shall resolve to identifiable semantic subjects. A presentation-only reference is insufficient to establish a relationship.

### 7.2 Directionality

Relationship direction shall be explicit whenever the relationship type has directional semantics. An implementation shall not infer direction solely from diagram position.

### 7.3 Relationship Type

Relationship types shall identify their applicable semantic category and specialization. The detailed normative relationship catalog is deferred to the subsequent relationship-design increment.

### 7.4 Relationship Multiplicity

Where a relationship type imposes cardinality or multiplicity constraints, those constraints shall be represented as semantic rules rather than implementation-specific assumptions.

## 8. Constraint Design

An Architectural Constraint represents a condition applicable to one or more architectural subjects.

The logical form is:

```text
Architectural Constraint
+-- identity
+-- subject references
+-- expression / condition
+-- semantic operators
+-- status
+-- provenance
+-- lifecycle
+-- extension metadata
```

The expression is descriptive semantic content. It is not an instruction to execute a particular evaluation algorithm.

The logical operator vocabulary established by the architecture baseline is:

```text
AND
OR
NOT
IMPLIES
EQUIVALENT
```

Constraint status values remain descriptive states:

```text
Satisfied
Violated
Unknown
Not Applicable
Not Evaluated
```

The meaning of these states shall not be conflated with the implementation mechanism used to determine them.

## 9. Assertion Design

An Architectural Assertion represents an explicit architectural statement.

The logical form is:

```text
Architectural Assertion
+-- identity
+-- subject references
+-- statement
+-- provenance
+-- lifecycle
+-- associated constraints
+-- associated evidence references
+-- associated requirement references
+-- associated decision references
+-- extension metadata
```

Associations to requirements, evidence, decisions, and other governed artifacts are references to the semantics owned by the applicable specification. They do not transfer ownership to ECRA-1200.

An assertion is not itself an Architecture Decision, Discovery Evidence item, Validation Result, or other portfolio-owned construct.

## 10. Stakeholder and Concern Participation

Stakeholders and Concerns remain externally owned concepts, with their foundational semantics governed by ECRA-1000.

Within an Architecture Description, the logical relationship is:

```text
Stakeholder
    |
    +-- has / expresses --> Concern
                              |
                              +-- addressed by --> Viewpoint
```

ECRA-1200 defines the participation of these concepts in viewpoints and views but does not establish alternative stakeholder or concern types.

## 11. Viewpoint Design

A Viewpoint is an ADL-owned construct that specifies conventions for constructing and interpreting Views.

The logical form is:

```text
Viewpoint
+-- identity
+-- purpose
+-- addressed concerns
+-- intended stakeholders
+-- permitted / required content
+-- modeling conventions
+-- relationship conventions
+-- presentation conventions
+-- consistency expectations
+-- specialization metadata
```

A viewpoint defines rules and conventions for views; it does not contain independent copies of the architectural subjects it governs.

## 12. View Design

A View is an ADL-owned representation or projection of architectural content constructed according to a Viewpoint.

The logical form is:

```text
View
+-- identity
+-- viewpoint reference
+-- source Architecture Description reference
+-- represented subject references
+-- presentation information
+-- semantic projection metadata
+-- provenance
+-- lifecycle
```

### 12.1 View-to-Description Relationship

A view shall identify the Architecture Description from which its semantic content is derived or against which its references are interpreted.

### 12.2 Represented Subjects

A view shall reference underlying semantic subjects rather than treating presentation objects as independent architectural identities.

### 12.3 Presentation Information

Presentation information may include layout, notation, visual grouping, filtering, and other view-specific information. Such information is subordinate to the underlying semantic model.

## 13. Context and External Concept References

ADL constructs may reference concepts owned by other specifications.

The following are explicit cross-specification reference boundaries:

| Concept | Owner | ADL treatment |
|---|---|---|
| Architecture | ECRA-1000 | Reference / specialization as permitted |
| Stakeholder | ECRA-1000 | Reference |
| Concern | ECRA-1000 | Reference |
| Requirement | ECRA-1100 | Reference |
| Traceability semantics | ECRA-1100 | Participate / reference |
| Shared identity/lifecycle/provenance semantics | SSF | Reuse |
| Architecture Decision | Current portfolio allocation: ECRA-1300 | Reference only; no redefinition |
| Validation Rule | ECRA-1400 | Reference only; no redefinition |
| Validation Result | ECRA-1400 | Reference only; no redefinition |
| Discovery Evidence | ECRA-1500 | Reference only; no redefinition |

The Architecture Decision ownership inconsistency remains a portfolio-level issue and is not resolved by this design.

## 14. Traceability Design

Traceability is represented as explicit semantic relationships between an ADL subject and a governed artifact or subject.

At the logical level:

```text
ADL Subject
    |
    +-- traceability relationship --> Governed Artifact / Subject
```

A traceability relationship shall preserve sufficient information to identify:

- the source subject;
- the target subject;
- the relationship type;
- applicable lifecycle state;
- provenance where required;
- the identity domain of referenced subjects.

ECRA-1100 remains authoritative for requirements traceability semantics.

## 15. Provenance and Lifecycle Design

Provenance and lifecycle are cross-cutting semantic dimensions rather than alternative architectural element types.

Where applicable, ADL-owned constructs shall expose or reference:

- lifecycle state;
- lifecycle transition information;
- origin or source information;
- derivation information;
- transformation history;
- attribution information.

The precise provenance and lifecycle vocabularies remain governed by SSF and applicable owning specifications.

## 16. Extension Design

Extensions shall be represented as explicit specializations or extensions of an existing semantic construct.

At minimum, an extension declaration shall identify:

```text
Extension
+-- identity / namespace
+-- base construct
+-- extension type
+-- compatibility metadata
+-- semantic additions
```

An extension shall not silently replace, redefine, or reinterpret the semantics of its base construct.

Unknown extensions shall remain distinguishable from known constructs. Implementations may preserve, ignore, reject, or otherwise handle unknown extensions according to the compatibility rules established by the representation and conformance specifications, but shall not silently reinterpret them as another semantic type.

## 17. Logical Integrity Rules

The following design-level integrity rules are mandatory targets for subsequent contracts and verification:

### DIR-01 — Identity Integrity

Every ADL-owned semantic subject has a stable identity within its applicable identity domain.

### DIR-02 — Reference Integrity

Every required internal reference resolves to the intended semantic subject.

### DIR-03 — Type Integrity

Every typed construct uses a recognized type or an explicitly declared extension type.

### DIR-04 — Relationship Endpoint Integrity

Every relationship endpoint satisfies the domain and range constraints of its relationship type.

### DIR-05 — View Integrity

Every View references an applicable Viewpoint and identifies its underlying Architecture Description or semantic source.

### DIR-06 — Constraint Integrity

Every Architectural Constraint identifies the subjects and semantic expression to which it applies.

### DIR-07 — Assertion Integrity

Every Architectural Assertion identifies the subject or semantic context of its statement and preserves applicable provenance.

### DIR-08 — Lifecycle Integrity

Lifecycle state and transitions do not silently alter semantic identity.

### DIR-09 — Traceability Integrity

Traceability references identify governed source and target subjects and do not redefine their owning semantics.

### DIR-10 — Extension Integrity

An extension identifies its base construct and does not silently change the meaning of an existing normative construct.

### DIR-11 — Semantic Ownership Integrity

An ADL construct shall not redefine a concept whose authoritative semantics belong to another ECRA specification.

### DIR-12 — View Identity Integrity

The same architectural subject represented in multiple views retains the same semantic identity.

## 18. Machine Representation Boundary

The logical model established here is the semantic source for machine-readable representation design.

The machine representation shall be capable of preserving the logical constructs and relationships defined here, including identity, type, relationships, lifecycle, provenance, views, viewpoints, constraints, assertions, traceability, and extensions.

This design does not prescribe:

- a concrete syntax;
- a wire format;
- a database schema;
- an API contract;
- a transport protocol.

Those concerns shall be developed in later design and contract increments and, where applicable, ECRA-1300.

## 19. Design-to-Architecture Traceability

This detailed-design increment directly realizes the following approved ECRA-1200 architecture baseline concerns:

| Architecture baseline | Detailed-design realization |
|---|---|
| Architecture Description | Logical container and scope model |
| Semantic Identity | Identity model and DIR-01 |
| Architectural Elements | Element logical structure |
| Architectural Relationships | Relationship logical structure and DIR-04 |
| Architectural Constraints | Constraint logical structure and DIR-06 |
| Architectural Assertions | Assertion logical structure and DIR-07 |
| Stakeholders / Concerns | External-reference participation model |
| Viewpoints | Viewpoint logical structure |
| Views | View logical structure and DIR-05 / DIR-12 |
| Consistency | DIR-01 through DIR-12 |
| Traceability | Explicit traceability relationship model |
| Machine Representation | Semantic source and preservation boundary |
| Extension Model | Explicit extension structure and DIR-10 |
| Semantic Ownership | Cross-specification ownership rules and DIR-11 |

## 20. Deferred Design Increments

The following should be addressed as separate small design increments rather than expanded into this foundation PR:

1. **Canonical ADL meta-model** — precise construct cardinalities and compositional rules.
2. **Relationship catalog** — normative relationship types, domain/range, directionality, and multiplicity.
3. **Constraint and assertion semantics** — precise expression structure and association rules.
4. **Viewpoint and view specification model** — canonical viewpoint definitions and view conformance structure.
5. **Consistency model** — detailed invariant definitions and machine-checkable conditions.
6. **Machine representation design** — abstract representation structures and compatibility behavior.
7. **ADL conformance model** — detailed conformance subjects and requirements.
8. **Implementation contracts** — APIs, persistence, validation, and executable interfaces after design approval.

These increments shall remain subordinate to this approved architecture baseline and shall not introduce new portfolio-level concept ownership without explicit architectural approval.

## 21. Design Status

This document is the **ECRA-1200 ADL Detailed Design Foundation** and is submitted for review.

Approval establishes the logical design foundation for subsequent ECRA-1200 detailed-design increments. It does not authorize implementation of unspecified behavior or resolve portfolio-level ownership questions outside ECRA-1200 scope.
