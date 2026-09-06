# ECRA Reference Application — P0 Vertical Slice Specification Framework

> Status: APPROVED
> Authority: ENGINEERING / INFORMATIVE
> Generation: GEN1
> Scope: Common specification framework for detailed P0 vertical-slice specifications

## 1. Purpose

This document establishes the common specification framework that shall be used to define the selected P0 vertical slices in sufficient detail for implementation planning, reference-implementation design, UI development, and end-to-end verification.

It is an implementation-planning artifact. It does not introduce new ECRA semantic requirements, alter normative ownership, or commit the reference implementation to a particular technology stack or deployment architecture.

## 2. Source Basis

The framework is derived from the approved ECRA Reference Application — Vertical Slice Portfolio and the approved ECRA Reference Implementation — Cross-Slice Capability Matrix.

The detailed slice specifications shall additionally identify and apply the authoritative normative ECRA requirements relevant to each selected workflow.

## 3. P0 Specification Set

The initial detailed specification set shall cover:

| ID | Vertical slice | Primary orientation |
|---|---|---|
| VS-J01 | Investigative Fact Check | Claim-first |
| VS-R01 | Lecture or Sermon Claim Review | Claim-first |
| VS-B01 | Company Due Diligence | Claim-first / source comparison |
| VS-L01 | Case Evidence Review | Claim-first / evidence review |
| VS-F01 | Incident / Digital Forensic Investigation | Evidence-first |
| VS-E01 | Engineering Design Evidence Review | Architecture/design-first and requirement/traceability |

The specifications shall be developed incrementally. A detailed specification shall not imply that every capability in the cross-slice matrix is required for that slice; slice-specific analysis shall establish the actual requirement.

## 4. Specification Structure

Each P0 vertical-slice specification shall contain, at minimum, the following sections.

### 4.1 Purpose and Scope

Define:

- the user problem being solved;
- the intended user or user role;
- the workflow boundary;
- the intended outcome;
- explicit non-goals;
- assumptions and known limitations.

### 4.2 Scenario and Preconditions

Define:

- concrete or realistically structured source inputs;
- required user/context information;
- preconditions;
- initial system state;
- applicable source availability or access assumptions;
- expected input quality boundaries.

The specification shall distinguish mandatory inputs from optional inputs and shall not assume ideal source material.

### 4.3 End-to-End Workflow

Describe the complete user-visible workflow from initial input through final result.

The workflow shall identify:

1. source selection or ingestion;
2. source/artifact registration;
3. claim, observation, requirement, or hypothesis identification as applicable;
4. evidence identification and association;
5. relationship and assessment steps;
6. provenance and traceability capture;
7. validation or verification where applicable;
8. result/report generation;
9. user inspection and follow-up actions where applicable.

The workflow shall distinguish application processing from ECRA semantic representation.

### 4.4 Semantic Object Requirements

Identify the ECRA semantic objects required by the slice and the reason each is needed.

For each object, specify:

- semantic role;
- required identity;
- required properties or attributes;
- ownership/reference behavior;
- lifecycle/provenance expectations;
- relevant relationships;
- applicable normative source.

A semantic object shall not be added merely because it is available in an ECRA specification.

### 4.5 Relationship Requirements

Identify the relationships required by the workflow.

For each relationship, specify:

- source;
- target;
- relationship semantic;
- direction where applicable;
- multiplicity where applicable;
- required properties;
- provenance/traceability implications;
- applicable relationship authority.

Concrete relationship semantics shall be derived from the applicable authoritative ECRA specifications rather than invented at the application layer.

### 4.6 Evidence and Assessment Requirements

Specify:

- what constitutes evidence for the workflow;
- evidence selection/discovery expectations;
- evidence-to-claim or evidence-to-subject association;
- support, contradiction, qualification, or unresolved states where applicable;
- uncertainty representation;
- limitations and gaps;
- human versus automated assessment responsibilities;
- distinctions between evidence properties and conclusions.

The application shall not silently convert evidence characteristics such as integrity, provenance, authenticity, or authority into truth judgments unless an applicable specification explicitly defines such semantics.

### 4.7 Provenance and Traceability

Define the provenance and traceability information necessary to reproduce and audit the workflow.

At minimum, consider:

- source identity;
- source location;
- acquired artifact identity;
- relevant version/revision state;
- processing or transformation provenance;
- claim/evidence origin;
- relationship origin;
- assessment origin;
- user actions that materially affect the result;
- links back to the originating semantic objects.

The specification shall distinguish semantic traceability from application navigation convenience.

### 4.8 Input/Output Contracts

Define the externally observable contracts for the slice.

Inputs should identify:

- format or structural expectations;
- required fields or content;
- acceptable alternatives;
- validation behavior;
- invalid or incomplete input handling.

Outputs should identify:

- semantic results;
- assessment results;
- provenance and traceability information;
- user-facing report/result;
- failure or incomplete-result states.

Contracts shall remain technology-independent unless a technology-specific choice is itself required by an approved constraint.

### 4.9 UI Demonstration

Define the minimum UI required to demonstrate the complete workflow.

The specification shall identify screens, views, or user interactions needed to:

1. provide or select source material;
2. inspect identified claims, observations, requirements, or hypotheses;
3. inspect evidence;
4. inspect relationships;
5. inspect source locations and provenance;
6. inspect assessment and uncertainty;
7. follow relevant traceability links;
8. generate and inspect the resulting report.

The UI shall expose sufficient semantic information to demonstrate the workflow without exposing implementation internals unnecessarily.

### 4.10 Negative and Boundary Cases

Each specification shall identify important failure and boundary conditions, including as applicable:

- missing source material;
- malformed or incomplete input;
- inaccessible sources;
- changed or unavailable external references;
- conflicting evidence;
- duplicate or overlapping evidence;
- insufficient evidence;
- unresolved claims;
- ambiguous source locations;
- invalid relationships;
- provenance gaps;
- processing failures;
- partial completion;
- user correction or review.

The specification shall state the expected semantic and user-visible behavior for each important case.

### 4.11 Acceptance Criteria

Acceptance criteria shall be observable and testable.

They shall cover, as applicable:

- end-to-end workflow completion;
- semantic correctness;
- identity preservation;
- relationship correctness;
- provenance and traceability preservation;
- assessment correctness;
- uncertainty/limitation handling;
- UI behavior;
- report correctness;
- deterministic or reproducible behavior where required;
- machine representation and semantic round-trip behavior where applicable;
- negative and boundary-case behavior.

### 4.12 Reference-Core versus Application Responsibilities

For every significant capability, the specification shall identify whether it belongs to:

- the shared ECRA reference core;
- reusable enabling infrastructure;
- the slice-specific application layer; or
- an external dependency/service.

The allocation shall be justified using the approved capability-promotion and derivation rules.

A slice-specific capability shall not be promoted into the shared core solely for convenience.

### 4.13 Capability Coverage

Each specification shall map its required capabilities to the approved cross-slice capability matrix.

The mapping shall identify:

- capability;
- Level 1/2/3 classification where applicable;
- source requirement or evidence;
- implementation placement;
- acceptance/verification evidence;
- lifecycle state where promotion is involved.

Where slice analysis disproves or changes an earlier matrix classification, the specification shall record the rationale and identify the required matrix update rather than silently diverging from it.

### 4.14 Security, Privacy, and Operational Considerations

Where relevant to the slice, identify:

- sensitive source material;
- access-control expectations;
- provenance integrity concerns;
- data-retention considerations;
- auditability;
- failure isolation;
- observability;
- reproducibility;
- external-service dependency risks.

These considerations shall be scoped to demonstrated slice needs and shall not introduce generalized platform requirements speculatively.

### 4.15 Explicit Exclusions

Each specification shall state capabilities deliberately excluded from the slice.

Exclusions should identify, where relevant:

- deferred ECRA capabilities;
- speculative infrastructure;
- domain-specific capabilities intentionally left to the application layer;
- future workflow extensions;
- deployment features not required by the slice.

## 5. Vertical-Slice Completeness Rule

A P0 slice specification is complete only when it is sufficiently precise to derive:

- the required semantic model;
- the required implementation capability set;
- the application workflow;
- the minimum UI demonstration;
- the verification strategy;
- the acceptance criteria;
- the principal negative and boundary cases.

Completeness of the specification does not imply implementation of every described capability. The capability matrix and evidence-driven promotion lifecycle remain authoritative for implementation scope.

## 6. Evidence-Driven Refinement Rule

The detailed specifications are expected to refine the cross-slice capability matrix.

When detailed slice analysis reveals that a capability is:

- necessary but missing from the matrix, it shall be added through the capability-promotion process;
- not actually required, its classification shall be corrected with recorded rationale;
- useful only to one slice, it should normally remain application-specific;
- reusable across multiple slices, its potential promotion into the shared core shall be evaluated explicitly.

The capability matrix shall be versioned as the implementation evidence base evolves. Each material refinement shall produce a new matrix version, with the change rationale, triggering vertical slice(s), implementation status, and relevant verification evidence recorded. This version history shall make progress and capability evolution visible after each vertical slice is specified, implemented, and verified.

The versioned matrix is the authoritative engineering record of the evolving reference-implementation capability baseline; individual slice specifications shall reference the matrix version against which their capability analysis was performed.

This establishes a controlled feedback loop:

```text
P0 Slice Specification
        ↓
Capability Evidence
        ↓
Versioned Capability Matrix
        ↓
Reference-Core Design
        ↓
Implementation
        ↓
Verification
        ↓
Lessons Learned
        └──────────────→ P0 Slice Specification / Matrix refinement
```

## 7. Implementation and Evolution Constraints

The detailed slice specifications shall preserve the evolutionary-architecture principles established by the capability matrix.

They shall:

- keep semantic contracts independent of deployment topology;
- prefer cohesive responsibilities and explicit interfaces;
- avoid unnecessary coupling to persistence, messaging, external services, or specific processing engines;
- preserve replaceability where practical;
- permit future decomposition into separate processes or services without requiring changes to ECRA semantic contracts where reasonably foreseeable;
- avoid introducing microservices or other distributed infrastructure merely because future decomposition is possible.

These are architectural constraints on implementation planning, not a commitment to a distributed deployment architecture.

## 8. Specification Identifier Convention

Each detailed slice specification shall use a stable identifier derived from its approved vertical-slice identifier.

Recommended pattern:

```text
VS-<family><number>
```

Examples:

- VS-J01
- VS-R01
- VS-B01
- VS-L01
- VS-F01
- VS-E01

The vertical-slice identifier shall remain stable even if implementation technology, UI structure, or internal component boundaries change.

## 9. Development Sequence

The detailed P0 specifications should be developed in an order that maximizes early reuse while preserving semantic diversity:

1. **VS-J01 — Investigative Fact Check**
2. **VS-R01 — Lecture or Sermon Claim Review**
3. **VS-B01 — Company Due Diligence**
4. **VS-L01 — Case Evidence Review**
5. **VS-F01 — Incident / Digital Forensic Investigation**
6. **VS-E01 — Engineering Design Evidence Review**

VS-J01 is a suitable first slice because it exercises the central claim → evidence → assessment → report workflow without requiring the broader architecture/design semantics of VS-E01. VS-R01 should follow closely because it tests whether the same semantic workflow remains domain-neutral across factual, historical, interpretive, and theological material.

## 10. Deliverable for Each Slice

Each P0 slice shall ultimately produce a specification that can be reviewed independently and traced to:

```text
Approved Vertical Slice Portfolio
        ↓
P0 Slice Specification
        ↓
Capability Matrix
        ↓
Reference-Core Component(s)
        ↓
Application/UI Workflow
        ↓
Acceptance / Verification Evidence
```

## 11. Status

This framework is **APPROVED**. It establishes the common structure for the detailed P0 vertical-slice specifications and does not itself constitute an implementation commitment beyond the approved capability-planning boundaries.
