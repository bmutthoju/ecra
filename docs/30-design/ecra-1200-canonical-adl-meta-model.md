# ECRA-1200 — Canonical ADL Meta-Model

> Status: REVIEW
> Authority: NORMATIVE
> Generation: GEN1
> Scope: Canonical conceptual meta-model for the ECRA Architecture Description Language
> Depends on: ECRA-1200 Architecture Description Language baseline; ECRA-1200 ADL Detailed Design Foundation

## 1. Purpose

This document defines the canonical conceptual meta-model for ECRA-1200 Architecture Description Language (ADL).

It refines the approved ADL detailed-design foundation by establishing the principal constructs, their containment, reference relationships, cardinality expectations, and compositional rules. It is intentionally technology-independent and does not define a concrete serialization schema, implementation class model, storage schema, API, or interchange protocol.

The meta-model is the normative conceptual model from which later machine-representation and implementation contracts shall be derived.

## 2. Scope

This increment defines:

- the canonical ADL construct set;
- construct identity and identity-domain rules;
- Architecture Description membership, containment, and reference semantics;
- cardinality and compositional rules;
- canonical relationships among Architecture Description, elements, relationships, constraints, assertions, viewpoints, views, and extensions;
- treatment of externally owned concepts, including reference integrity and preserved external snapshots;
- model-wide invariants required by the canonical structure.

This increment does not define:

- concrete JSON, YAML, XML, RDF, or binary syntax;
- programming-language classes or interfaces;
- database or repository schemas;
- transport protocols;
- executable validation algorithms;
- proof or reasoning engines;
- the normative relationship catalog;
- detailed constraint/assertion expression languages;
- canonical viewpoint catalog;
- conformance assessment procedures;
- storage, archival, synchronization, or monitoring mechanisms for preserved external snapshots.

Those concerns remain deferred to their designated design increments.

## 3. Conformance to the Foundation

This meta-model is subordinate to the approved ECRA-1200 ADL architecture baseline and the approved ADL Detailed Design Foundation.

Where this document refines a foundation concept, the refinement shall be interpreted consistently with the foundation. It shall not establish competing ownership for concepts governed by SSF, ECRA-1000, ECRA-1100, ECRA-1300, ECRA-1400, or ECRA-1500.

The term **subject** retains the meaning established by the foundation: a semantic referent that an ADL construct can describe, relate, constrain, assert about, or reference. It is a semantic role, not a new portfolio-wide root type.

## 4. Canonical Meta-Model Overview

The canonical ADL meta-model is:

```text
Architecture Description
|
+-- contains --> Architecture Description Members [0..*]
|                  |
|                  +-- Architectural Element
|                  +-- Architectural Relationship
|                  +-- Architectural Constraint
|                  +-- Architectural Assertion
|                  +-- Viewpoint
|                  +-- View
|                  +-- Context Reference
|                  +-- Extension
|
+-- contains --> Architectural Elements [0..*]
|                  |
|                  +-- properties [0..*]
|                  +-- constraints [0..*]
|                  +-- assertions [0..*]
|                  +-- traceability references [0..*]
|                  +-- extension metadata [0..*]
|
+-- contains --> Architectural Relationships [0..*]
|                  |
|                  +-- source --> Subject [1]
|                  +-- target --> Subject [1]
|
+-- contains --> Architectural Constraints [0..*]
|                  +-- subject references [1..*]
|
+-- contains --> Architectural Assertions [0..*]
|                  +-- subject references [0..*]
|
+-- contains --> Viewpoints [0..*]
|                  +-- concerns --> Concern [0..*]
|                  +-- stakeholders --> Stakeholder [0..*]
|
+-- contains --> Views [0..*]
|                  +-- viewpoint --> Viewpoint [1]
|                  +-- source description --> Architecture Description [1]
|                  +-- represented subjects [0..*]
|
+-- contains --> Context References [0..*]
|
+-- contains --> Extensions [0..*]
```

The diagram expresses semantic structure and cardinality expectations. It is not a concrete object or serialization hierarchy. The Architecture Description Member role is the canonical membership mechanism; the repeated construct lines show the member construct categories for readability and do not introduce a second containment mechanism.

## 5. Canonical Construct Set

The canonical ADL construct set consists of:

1. Architecture Description;
2. Architecture Description Member as a membership role;
3. Architectural Element;
4. Architectural Relationship;
5. Architectural Constraint;
6. Architectural Assertion;
7. Viewpoint;
8. View;
9. Context Reference;
10. Extension.

Architecture Description Member is a role applied to an ADL-owned construct that establishes membership in an Architecture Description. It is not a new semantic root type or an independently modeled portfolio concept.

Shared concepts such as Entity, Artifact, Relationship, Constraint, lifecycle, provenance, and identity are reused according to SSF and applicable owning specifications. Externally owned concepts are referenced rather than reproduced as ADL-owned root constructs.

## 6. Architecture Description

### 6.1 Definition

An **Architecture Description** is the ADL-owned semantic container that organizes an architecture description and its relevant architectural context.

### 6.2 Canonical Components

An Architecture Description may contain or reference:

| Component | Cardinality | Semantics |
|---|---:|---|
| Architecture Description Members | 0..* | Membership role for ADL-owned constructs contained in the description |
| Architectural Elements | 0..* | ADL-owned identifiable architectural subjects |
| Architectural Relationships | 0..* | Explicit semantic associations |
| Architectural Constraints | 0..* | Conditions applicable to subjects |
| Architectural Assertions | 0..* | Explicit architectural statements |
| Viewpoints | 0..* | Conventions for constructing/interpreting views |
| Views | 0..* | Projections or representations of architectural content |
| Context References | 0..* | References to relevant external concepts |
| Extensions | 0..* | Controlled specializations/extensions |

The construct-specific rows are the member categories represented by the Architecture Description Member role. They shall not be interpreted as independent ownership relationships in addition to membership.

### 6.3 Structural Validity and Descriptive Completeness

The 0..* cardinalities in this meta-model describe the permitted structural cardinality of the corresponding collections. They do not imply that every Architecture Description is substantively complete merely because it is structurally valid.

An Architecture Description may therefore contain zero Architecture Description Members and remain structurally valid, provided that the Architecture Description itself satisfies its mandatory identity and scope requirements. Such a description represents an explicitly declared but substantively empty or not-yet-populated description context.

Descriptive completeness is a separate semantic property determined against the Architecture Description's declared scope, purpose, and applicable requirements. A structurally valid Architecture Description may be **incomplete** without being structurally invalid. The determination of completeness is outside this increment unless imposed by an applicable specialization or conformance requirement.

### 6.4 Containment and Membership

An Architecture Description is the logical owner of the ADL constructs that form its description scope. Logical containment does not require physical co-location in storage or serialization.

An **Architecture Description Member** establishes that an ADL-owned construct belongs to the logical composition of the Architecture Description. Membership is a containment role, not a new identity-bearing construct. A member retains the identity and type of the construct to which the role applies.

A conforming representation shall be able to distinguish an ADL-owned construct that is a member of an Architecture Description from a semantic subject that is merely referenced by that Architecture Description or one of its members.

A referenced externally owned concept is not thereby contained as an ADL-owned concept.

### 6.5 Scope

An Architecture Description shall have sufficient scope information to determine the architectural subject matter to which the description applies. Scope may be contextual and does not imply a universal decomposition of architecture.

## 7. Identity and Identity Domains

### 7.1 Identity-Bearing Constructs

The following ADL-owned constructs are independently referenceable and therefore identity-bearing:

- Architecture Description;
- Architectural Element;
- Architectural Relationship;
- Architectural Constraint;
- Architectural Assertion;
- Viewpoint;
- View;
- Extension, when independently declared and referenceable.

Architecture Description Member is not independently identity-bearing; it is a membership role applied to an identity-bearing ADL construct.

A Context Reference may carry an identifier required to resolve the external concept, but that identifier does not establish ownership of the referenced external concept.

### 7.2 Identity Domain

Every identity-bearing construct shall have an applicable identity domain. The identity domain determines the scope within which the identity is unique and resolvable.

An identity shall be stable across conforming representations and shall not depend on labels, notation, storage location, or serialization syntax.

### 7.3 Identity Uniqueness

Within an applicable identity domain:

- two semantically distinct identity-bearing subjects shall not share the same identity;
- the same semantic subject shall not acquire multiple identities merely because it appears in multiple views or representations;
- an identity shall not be reused for a semantically different subject in violation of applicable lifecycle rules.

## 8. Architectural Element

### 8.1 Definition

An **Architectural Element** represents an identifiable architectural subject within an Architecture Description.

### 8.2 Canonical Structure

```text
Architectural Element
+-- identity [1]
+-- type [1]
+-- properties [0..*]
+-- lifecycle [0..1]
+-- provenance [0..1]
+-- relationships [0..*]
+-- constraints [0..*]
+-- assertions [0..*]
+-- traceability references [0..*]
+-- extensions [0..*]
```

### 8.3 Type

Every Architectural Element shall identify a semantic type. The type may be a core ADL type, a permitted specialization, or an externally governed type reference.

The detailed normative type catalog is outside this increment.

### 8.4 Properties

A property is an explicitly identified semantic characteristic of the element. Presentation-only information shall not become a semantic property merely because it is associated with an element.

### 8.5 Element Membership

An Architectural Element may participate in exactly one Architecture Description as an ADL-owned member within a given description context unless an explicit composition rule permits otherwise.

The same semantic element may be referenced from multiple Views without being duplicated semantically.

## 9. Architectural Relationship

### 9.1 Definition

An **Architectural Relationship** represents an explicit semantic association between two architectural subjects.

### 9.2 Canonical Structure

```text
Architectural Relationship
+-- identity [1]
+-- relationship type [1]
+-- source [1]
+-- target [1]
+-- properties [0..*]
+-- lifecycle [0..1]
+-- provenance [0..1]
+-- constraints [0..*]
+-- assertions [0..*]
+-- extensions [0..*]
```

### 9.3 Endpoints

Every Architectural Relationship shall identify exactly one semantic source and exactly one semantic target.

The source and target shall resolve to identifiable semantic subjects permitted by the relationship type. The detailed domain, range, directionality, and multiplicity rules for relationship types are deferred to the normative relationship catalog.

### 9.4 Relationship Identity

A relationship has its own semantic identity where it is independently referenceable. The identity of a relationship shall not be inferred solely from the identities of its endpoints.

This permits two semantically distinct relationships between the same subjects when their relationship types or other semantics distinguish them.

### 9.5 Relationship Membership

An Architectural Relationship is an ADL-owned member of its Architecture Description within the applicable description context. It may additionally be referenced from its source, target, views, constraints, assertions, or traceability structures.

## 10. Architectural Constraint

### 10.1 Definition

An **Architectural Constraint** represents a semantic condition applicable to one or more subjects.

### 10.2 Canonical Structure

```text
Architectural Constraint
+-- identity [1]
+-- subject references [1..*]
+-- expression / condition [1]
+-- semantic operators [0..*]
+-- status [0..1]
+-- provenance [0..1]
+-- lifecycle [0..1]
+-- extensions [0..*]
```

### 10.3 Subject Applicability

A constraint shall identify at least one subject to which its condition applies.

A constraint may apply to multiple subjects. Subject references shall resolve according to their applicable identity domains.

### 10.4 Expression Boundary

The expression/condition is semantic content. This meta-model establishes its presence but does not define a complete expression grammar or executable evaluation model.

The currently established logical operators remain AND, OR, NOT, IMPLIES, and EQUIVALENT.

### 10.5 Status

Constraint status is descriptive semantic state. Permitted values remain those established by the foundation unless extended through an approved semantic change.

### 10.6 Constraint Membership

An Architectural Constraint is an ADL-owned member of its Architecture Description within the applicable description context. Its subject references identify the subjects to which the condition applies and do not themselves establish additional membership.

## 11. Architectural Assertion

### 11.1 Definition

An **Architectural Assertion** represents an explicit architectural statement about one or more subjects, relationships, properties, conditions, or interpretations.

### 11.2 Canonical Structure

```text
Architectural Assertion
+-- identity [1]
+-- subject references [0..*]
+-- statement [1]
+-- provenance [0..1]
+-- lifecycle [0..1]
+-- associated constraints [0..*]
+-- associated evidence references [0..*]
+-- associated requirement references [0..*]
+-- associated decision references [0..*]
+-- extensions [0..*]
```

### 11.3 Subject Association

An assertion may be contextual rather than tied to a single subject; therefore subject references have cardinality 0..* at this meta-model level. Where the assertion semantics require a subject, the applicable specialization shall impose the stronger cardinality.

### 11.4 Ownership Boundary

An assertion does not become an Architecture Decision, Discovery Evidence item, Validation Result, Requirement, or other externally owned construct merely by referencing one.

### 11.5 Assertion Membership

An Architectural Assertion is an ADL-owned member of its Architecture Description within the applicable description context. Its associations to constraints, evidence, requirements, decisions, and other subjects do not transfer ownership of those referenced concepts.

## 12. Viewpoint

### 12.1 Definition

A **Viewpoint** specifies conventions for constructing, interpreting, and organizing Views that address particular concerns and stakeholder interests.

### 12.2 Canonical Structure

```text
Viewpoint
+-- identity [1]
+-- purpose [1]
+-- addressed concerns [0..*]
+-- intended stakeholders [0..*]
+-- permitted / required content [0..*]
+-- modeling conventions [0..*]
+-- relationship conventions [0..*]
+-- presentation conventions [0..*]
+-- consistency expectations [0..*]
+-- specialization metadata [0..1]
```

### 12.3 Concern and Stakeholder References

Addressed concerns and intended stakeholders are references to concepts governed by ECRA-1000. They are not ADL-owned replacements.

A Viewpoint may address zero or more concerns at the generic meta-model level; applicable conformance or viewpoint definitions may require one or more.

### 12.4 Viewpoint Independence

A Viewpoint defines conventions and expectations. It does not contain independent semantic copies of the architectural subjects presented by Views constructed under it.

### 12.5 Viewpoint Membership

A Viewpoint is an ADL-owned member of its Architecture Description within the applicable description context. Its references to concerns and stakeholders remain external references governed by ECRA-1000.

## 13. View

### 13.1 Definition

A **View** is a representation or projection of architectural content constructed according to a Viewpoint.

### 13.2 Canonical Structure

```text
View
+-- identity [1]
+-- viewpoint reference [1]
+-- source Architecture Description [1]
+-- represented subject references [0..*]
+-- presentation information [0..*]
+-- semantic projection metadata [0..*]
+-- provenance [0..1]
+-- lifecycle [0..1]
+-- extensions [0..*]
```

### 13.3 Viewpoint Reference

Every View shall identify exactly one Viewpoint that governs its construction and interpretation.

### 13.4 Source Description Reference

Every View shall identify exactly one source Architecture Description from which its semantic content is derived or against which its references are interpreted.

### 13.5 Represented Subjects

Represented subjects are references to underlying semantic subjects. A visual symbol, node, connector, table row, or other presentation object does not acquire an independent architectural identity merely by appearing in a View.

### 13.6 Projection Semantics

A View may select, aggregate, filter, or otherwise project underlying architectural content. Such projection does not alter the semantic identity of the represented subjects.

The precise projection and aggregation semantics remain deferred.

### 13.7 View Membership

A View is an ADL-owned member of its Architecture Description within the applicable description context. Its source Architecture Description reference identifies the semantic context from which its content is derived and does not create a second Architecture Description.

## 14. Context Reference

### 14.1 Definition

A **Context Reference** identifies a concept outside the ADL-owned semantic core that is relevant to an Architecture Description.

### 14.2 Canonical Targets

Context References may identify, as applicable:

- Architecture;
- Stakeholder;
- Concern;
- Requirement;
- Architecture Decision;
- Validation Rule;
- Validation Result;
- Discovery Evidence;
- other externally governed concepts.

### 14.3 Ownership

A Context Reference records participation or dependency on an externally governed concept. It does not transfer ownership or redefine that concept.

### 14.4 Resolution

A context reference shall contain sufficient information to resolve its target according to the identity and reference semantics of the owning specification. Concrete URI, key, registry, or transport mechanisms are outside this increment.

### 14.5 Reference Integrity and Preservation

Where a Context Reference identifies an externally controlled resource or concept whose continued availability or content is material to the Architecture Description, the reference shall support sufficient integrity metadata to establish what resource was observed and relied upon.

The integrity metadata may include, as applicable:

- reference identity;
- external locator;
- owning authority or namespace;
- external version, revision, or equivalent identifier, where available;
- observed state;
- last verified timestamp;
- integrity or fingerprint information, where applicable;
- change-detection information;
- dependency or criticality information;
- mitigation or impact reference.

A Context Reference may additionally include a **Preserved External Snapshot**: a preserved copy of the externally referenced resource as observed at a particular point in time.

A Preserved External Snapshot shall be associated with the corresponding external reference observation and, where applicable, shall preserve:

- snapshot identity;
- snapshot content or preserved representation;
- capture timestamp;
- integrity or fingerprint information;
- provenance sufficient to establish the snapshot's origin and observation context.

A preserved snapshot records historical observed content. It shall not, by itself, be interpreted as the current authoritative external resource or as evidence that the external resource remains available or unchanged.

The preservation capability is a semantic resilience and provenance mechanism. This increment does not prescribe snapshot storage technology, archival systems, synchronization services, monitoring mechanisms, retention periods, or mitigation workflows.

External reference state shall distinguish, as applicable, between an externally available and verified resource, a changed resource, an unavailable resource, and an unverified resource. The definitive state vocabulary and operational transition rules may be refined by an applicable later design increment.

### 14.6 Context Reference Membership

A Context Reference is an ADL-owned member of its Architecture Description. The externally referenced concept or resource is not thereby made an ADL-owned member.

## 15. Extension

### 15.1 Definition

An **Extension** declares controlled additional semantics associated with an existing ADL construct.

### 15.2 Canonical Structure

```text
Extension
+-- identity / namespace [1]
+-- base construct [1]
+-- extension type [1]
+-- compatibility metadata [0..*]
+-- semantic additions [0..*]
```

### 15.3 Extension Rules

An extension shall:

- identify the construct it extends or specializes;
- preserve the base construct's semantics unless an explicit specialization rule applies;
- remain distinguishable from the base construct;
- provide sufficient identity information for recognition and compatibility assessment.

An extension shall not silently redefine an existing normative construct.

### 15.4 Extension Membership

An Extension is an ADL-owned member of its Architecture Description when it is declared as part of that description. Its base construct reference does not create an additional declaration or alter the base construct's membership.

## 16. Containment versus Reference

The meta-model distinguishes logical containment from semantic reference.

### 16.1 Containment

Containment establishes that a construct belongs to the logical composition of an Architecture Description. The **Architecture Description Member** role represents this containment relationship without creating a new semantic root type.

A contained construct may still be referenced by other constructs.

### 16.2 Reference

A reference identifies an existing semantic subject without establishing another semantic subject.

References shall be used when:

- a View represents an existing architectural subject;
- an Architectural Relationship identifies its endpoints;
- a Constraint identifies applicable subjects;
- an Assertion identifies subjects or associated governed artifacts;
- a Viewpoint identifies stakeholders or concerns;
- an ADL construct participates in externally owned semantics;
- a View identifies its source Architecture Description;
- a Context Reference identifies an externally governed concept or resource.

### 16.3 Membership versus Reference

Membership and reference are distinct semantics:

- **membership** establishes that an ADL-owned construct forms part of the Architecture Description's logical composition;
- **reference** identifies an existing semantic subject without making that subject an additional ADL-owned construct.

An externally governed concept may be referenced by an Architecture Description without becoming an Architecture Description Member. An ADL-owned construct may be a member while also containing references to other members or external subjects.

### 16.4 No Implicit Duplication

A reference shall not be interpreted as semantic duplication. A conforming representation shall preserve the distinction between an existing referenced subject and a newly declared subject.

## 17. Cardinality and Compositional Rules

The following rules are normative for the canonical meta-model.

| Rule | Requirement |
|---|---|
| CM-01 | Every Architecture Description is independently identity-bearing. |
| CM-02 | Every identity-bearing ADL construct has exactly one semantic identity within its applicable identity domain. |
| CM-03 | Every Architectural Element has exactly one type. |
| CM-04 | Every Architectural Relationship has exactly one relationship type, one source, and one target. |
| CM-05 | Every Architectural Constraint has at least one subject reference and exactly one semantic condition. |
| CM-06 | Every Architectural Assertion has exactly one statement; subject association may be zero or more at this generic level. |
| CM-07 | Every View has exactly one Viewpoint reference and exactly one source Architecture Description reference. |
| CM-08 | Every reference resolves to the intended semantic subject or is explicitly classified as unresolved according to applicable representation/conformance rules. |
| CM-09 | Logical containment does not imply transfer of ownership of externally governed concepts. |
| CM-10 | A presentation object does not acquire an independent semantic identity merely through inclusion in a View. |
| CM-11 | Extensions identify their base construct and preserve its semantics unless an explicit specialization rule applies. |
| CM-12 | Lifecycle state does not by itself establish a new semantic identity. |
| CM-13 | Multiple Views of the same subject reference the same semantic identity. |
| CM-14 | A semantic reference shall not silently be converted into a new declaration during representation or reconstruction. |
| CM-15 | Every ADL-owned member has one Architecture Description membership within the applicable description context unless an explicit composition rule permits otherwise. |
| CM-16 | Architecture Description Member is a containment role and does not establish an additional semantic identity. |
| CM-17 | Structural validity does not imply descriptive completeness; completeness is assessed against declared scope, purpose, and applicable requirements. |
| CM-18 | Where an external reference is material to the Architecture Description, its integrity metadata shall be sufficient to identify the observed resource and support impact assessment when its state changes or becomes unavailable. |
| CM-19 | A preserved external snapshot represents historical observed content and shall not be treated as the current authoritative external resource solely because it is preserved. |

## 18. Cross-Construct Cardinality Matrix

| Source construct | Relationship | Target | Cardinality |
|---|---|---|---:|
| Architecture Description | contains members | Architecture Description Member | 0..* |
| Architecture Description Member | applies to | ADL-owned construct | 1 |
| Architecture Description | contains | Architectural Element | 0..* |
| Architecture Description | contains | Architectural Relationship | 0..* |
| Architecture Description | contains | Architectural Constraint | 0..* |
| Architecture Description | contains | Architectural Assertion | 0..* |
| Architecture Description | contains | Viewpoint | 0..* |
| Architecture Description | contains | View | 0..* |
| Architecture Description | contains | Context Reference | 0..* |
| Architecture Description | contains | Extension | 0..* |
| Architectural Relationship | source | Subject | 1 |
| Architectural Relationship | target | Subject | 1 |
| Architectural Constraint | applies to | Subject | 1..* |
| Architectural Assertion | concerns | Subject | 0..* |
| View | governed by | Viewpoint | 1 |
| View | derived from / interpreted against | Architecture Description | 1 |
| View | represents | Subject | 0..* |
| Viewpoint | addresses | Concern | 0..* |
| Viewpoint | intended for | Stakeholder | 0..* |
| Context Reference | identifies | External Concept / Resource | 1 |
| Context Reference | may preserve | Preserved External Snapshot | 0..* |
| Extension | extends / specializes | Base Construct | 1 |

The matrix expresses canonical structural expectations. Detailed relationship semantics, including permitted target types and relationship-specific multiplicities, remain the responsibility of the later relationship catalog.

A Context Reference may have zero, one, or multiple historical preserved snapshots. Concrete collection representation is deferred to machine-representation design.

## 19. Lifecycle and Provenance Composition

Lifecycle and provenance are orthogonal to construct identity and type.

Where applicable, each identity-bearing construct may carry or reference lifecycle and provenance information without changing its construct identity.

A lifecycle transition shall not implicitly duplicate, merge, or retype a semantic subject.

A provenance record may identify origin, derivation, transformation, or attribution without becoming a competing architectural element.

For external references and preserved snapshots, provenance shall be sufficient to distinguish the external observation from the preserved historical copy. Preservation does not transfer authority over the external resource to ECRA.

The authoritative vocabularies and detailed semantics remain governed by SSF and applicable owning specifications.

## 20. Semantic Ownership Constraints

The canonical meta-model shall preserve the following ownership boundaries:

| Concept | Owner | Meta-model treatment |
|---|---|---|
| Architecture | ECRA-1000 | External reference / permitted specialization |
| Stakeholder | ECRA-1000 | External reference |
| Concern | ECRA-1000 | External reference |
| Requirement | ECRA-1100 | External reference / traceability participation |
| Shared identity/lifecycle/provenance semantics | SSF | Reuse |
| Architecture Decision | Current portfolio allocation: ECRA-1300 | External reference only; ownership unresolved at portfolio level |
| Validation Rule | ECRA-1400 | External reference only |
| Validation Result | ECRA-1400 | External reference only |
| Discovery Evidence | ECRA-1500 | External reference only |

This meta-model does not resolve the existing Architecture Decision ownership inconsistency.

## 21. Model-Wide Semantic Invariants

The canonical structure shall satisfy the following invariants:

1. **Identity uniqueness** — identity-bearing subjects are uniquely identifiable within their applicable identity domains.
2. **Reference resolution** — required references resolve to the intended semantic subject.
3. **Containment integrity** — contained ADL constructs belong to the intended Architecture Description context.
4. **Membership integrity** — Architecture Description Member roles identify the ADL-owned constructs that form part of the Architecture Description without creating duplicate semantic identities.
5. **Endpoint integrity** — relationship source and target references resolve to permitted subjects.
6. **View integrity** — each View has one governing Viewpoint and one source Architecture Description.
7. **View identity preservation** — a View does not establish new identities for subjects it represents.
8. **Ownership integrity** — externally governed concepts retain their authoritative semantics.
9. **Extension integrity** — extensions remain distinguishable and semantically compatible with their base constructs.
10. **Lifecycle integrity** — lifecycle transitions do not silently change semantic identity.
11. **External reference integrity** — material external references retain sufficient identity, version/revision, observation, and integrity information to establish what was relied upon and to support impact assessment when the external resource changes or becomes unavailable.
12. **Snapshot integrity** — a preserved external snapshot is attributable to a specific external observation, has sufficient integrity information where feasible, and remains distinguishable from the current external resource.
13. **Representation integrity** — representation and reconstruction preserve the canonical model subject to explicitly defined semantic equivalence rules.
14. **Completeness distinction** — structural validity and descriptive completeness remain distinct properties; an empty or partially populated Architecture Description may be structurally valid while incomplete against its declared scope or purpose.

These invariants refine the design-level integrity rules of the approved foundation. They remain semantic conditions rather than executable validation algorithms.

## 22. Relationship to Machine Representation

The canonical meta-model is the conceptual source for concrete machine representation.

A conforming representation shall be capable of representing the canonical constructs, membership roles, references, cardinalities, and semantic distinctions defined here. In particular, it shall preserve the distinction between:

- declaration and reference;
- membership/containment and semantic reference;
- semantic identity and presentation identity;
- ADL-owned and externally owned concepts;
- semantic construct and extension;
- external resource and preserved external snapshot;
- logical model and concrete syntax.

The representation shall participate in the bidirectional semantic mapping and round-trip integrity requirements established by the approved detailed-design foundation.

This section does not prescribe concrete field names, syntax, serialization technology, or interchange protocol.

## 23. Traceability to the Approved Foundation

| Foundation concern | Canonical meta-model realization |
|---|---|
| Architecture Description | §§6, 16, 18 |
| Stable semantic identity | §7 |
| Architectural Elements | §8, §§16–18 |
| Architectural Relationships | §9, §§17–18 |
| Architectural Constraints | §10, §§17–18 |
| Architectural Assertions | §11, §§17–18 |
| Stakeholder / Concern boundaries | §§12, 14, 20 |
| Viewpoints | §12 |
| Views | §13, §§17–18 |
| Context / external references | §14, §20 |
| External reference integrity / preservation | §14, §§17, 19, 21–22 |
| Extensions | §15, §17 |
| Containment, membership, and reference semantics | §6, §16 |
| Cardinality and composition | §§17–18 |
| Lifecycle / provenance | §19 |
| Semantic ownership | §20 |
| Model integrity | §21 |
| Machine representation boundary | §22 |

## 24. Deferred Design Increments

The following remain separate from this canonical meta-model:

1. **Normative relationship catalog** — concrete relationship types, domain/range, directionality, and relationship-specific multiplicity.
2. **Constraint and assertion semantics** — precise expression structures, evaluation-independent semantics, and association rules.
3. **Viewpoint and view specification model** — canonical viewpoint definitions and detailed view-conformance structures.
4. **Consistency model** — detailed machine-checkable invariant definitions.
5. **Machine representation design** — concrete abstract representation structures, mapping rules, equivalence rules, and compatibility behavior.
6. **ADL conformance model** — conformance subjects, requirements, and assessment boundaries.
7. **Implementation contracts** — APIs, persistence, executable validation interfaces, external-reference monitoring/preservation services, and other implementation-specific contracts after design approval.

No deferred increment shall silently alter the ownership or cardinality rules established here; changes requiring architectural impact shall follow the applicable ECRA change process.

## 25. Design Status

This document is the **ECRA-1200 Canonical ADL Meta-Model** and is submitted for review.

Approval establishes the canonical conceptual structure for subsequent ECRA-1200 detailed-design increments. It does not authorize implementation of concrete serialization, storage, transport, validation, proof, monitoring, or archival behavior not defined by this document.
