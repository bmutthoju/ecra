# ECRA Reference Implementation — Cross-Slice Capability Matrix

> Status: REVIEW
> Authority: ENGINEERING / INFORMATIVE
> Generation: GEN1
> Scope: Derivation of reference-implementation capabilities from the approved vertical-slice portfolio

## 1. Purpose

This document establishes the first cross-slice capability matrix for the ECRA reference implementation.

Its purpose is to determine which capabilities are demonstrated as necessary by the approved P0 vertical slices, which capabilities are enabling infrastructure, and which capabilities should remain deferred because the current evidence does not justify implementing them.

The matrix is an implementation-planning artifact. It does not create new ECRA semantic requirements, alter normative ownership, or expand the approved ECRA specifications.

## 2. Governing Principle

The reference implementation shall implement the smallest coherent capability set sufficient to support the selected vertical slices while preserving applicable normative ECRA contracts.

Capability inclusion follows three levels:

- **Level 1 — Demonstrated necessity:** directly required by one or more selected vertical slices. Default: implement.
- **Level 2 — Enabling infrastructure:** necessary to implement Level 1 capabilities cleanly and consistently. Default: implement when justified.
- **Level 3 — Speculative capability:** permitted by the specifications or potentially useful but not demonstrated as necessary by the selected slices. Default: defer.

A capability shall not enter the core merely because an ECRA specification permits it.

## 3. Source Basis

The primary source for slice selection and workflow expectations is the approved ECRA Reference Application — Vertical Slice Portfolio.

The principal normative implementation requirement source currently available in the repository is the approved Gen1 Claim and Evidence Requirements. That document requires identifiable claims and evidence, explicit evidence-to-claim associations, stable identity, source representation, acquired-artifact preservation where applicable, provenance, integrity information, and explicit claim/evidence traceability. It also establishes important boundaries such as integrity not implying truth and authenticity not implying authority.

The matrix also respects the approved ECRA-1200 architecture and detailed-design foundations, particularly stable identity, explicit relationships, provenance/lifecycle, traceability boundaries, and semantic-preserving machine representation.

## 4. Selected P0 Slices

The initial proving portfolio consists of:

| ID | Vertical slice | Primary workflow orientation |
|---|---|---|
| VS-J01 | Investigative Fact Check | Claim-first |
| VS-R01 | Lecture or Sermon Claim Review | Claim-first |
| VS-B01 | Company Due Diligence | Claim-first / source comparison |
| VS-L01 | Case Evidence Review | Claim-first / evidence review |
| VS-F01 | Incident / Digital Forensic Investigation | Evidence-first |
| VS-E01 | Engineering Design Evidence Review | Architecture/design-first and requirement/traceability |

VS-C01 is P1 and VS-AI01 is P2/Future; they are retained as future validation inputs but are not used to enlarge the initial P0 implementation commitment.

## 5. Capability Taxonomy

For planning purposes, capabilities are grouped into the following areas:

1. Source and artifact handling
2. Semantic identity
3. Claim and evidence representation
4. Relationship and assessment representation
5. Provenance and traceability
6. Integrity and source-state handling
7. Architecture/design representation
8. Machine representation
9. Evaluation support
10. User interaction and reporting
11. Validation and verification integration
12. Operational enabling infrastructure

The taxonomy is implementation-oriented. It does not imply that each item is a new ECRA semantic type.

## 6. Cross-Slice Capability Matrix

Legend:

- **D** — directly demonstrated as necessary by the slice
- **E** — enabling infrastructure for another required capability
- **—** — not required by the current slice
- **F** — future/deferred or insufficient evidence

| Capability | J01 | R01 | B01 | L01 | F01 | E01 | Level | Initial disposition |
|---|:---:|:---:|:---:|:---:|:---:|:---:|---|---|
| Source material registration | D | D | D | D | D | D | 1 | Implement |
| Acquired artifact preservation | D | D | D | D | D | D | 1 | Implement |
| Source location / citation | D | D | D | D | D | D | 1 | Implement |
| Stable semantic identity | D | D | D | D | D | D | 1 | Implement |
| Claim representation | D | D | D | D | D | E | 1 | Implement |
| Evidence representation | D | D | D | D | D | D | 1 | Implement |
| Evidence-to-claim association | D | D | D | D | D | D | 1 | Implement |
| Typed relationship representation | D | D | D | D | D | D | 1 | Implement |
| Support / contradiction / qualification assessment | D | D | D | D | D | D | 1 | Implement |
| Unresolved / uncertainty representation | D | D | D | D | D | D | 1 | Implement |
| Provenance representation | D | D | D | D | D | D | 1 | Implement |
| Traceability traversal | D | D | D | D | D | D | 1 | Implement |
| Source version / revision state | D | D | D | D | D | D | 1 | Implement |
| Artifact integrity information | D | D | D | D | D | D | 1 | Implement |
| Source authenticity result | E | E | D | D | D | D | 1/2 | Implement where mechanism applies |
| Source authority information | D | D | D | D | D | D | 1 | Implement |
| Transformation provenance | E | E | E | E | D | D | 1/2 | Implement as required by processing |
| Architecture / design representation | — | — | — | — | — | D | 1 | Implement bounded support |
| Requirement linkage | — | — | — | — | — | D | 1 | Implement through approved traceability semantics |
| Decision-related representation | — | — | — | — | — | D | 1 | Implement only to the extent required by selected E01 workflow and owning semantics |
| Machine-readable representation | D | D | D | D | D | D | 1 | Implement |
| Semantic round-trip preservation | D | D | D | D | D | D | 1 | Implement |
| Structured assessment result | D | D | D | D | D | D | 1 | Implement |
| Report generation | D | D | D | D | D | D | 1 | Implement |
| UI source selection / ingestion | D | D | D | D | D | D | 1 | Implement |
| UI claim / observation inspection | D | D | D | D | D | D | 1 | Implement |
| UI evidence inspection | D | D | D | D | D | D | 1 | Implement |
| UI relationship inspection | D | D | D | D | D | D | 1 | Implement |
| UI provenance / location inspection | D | D | D | D | D | D | 1 | Implement |
| UI assessment / uncertainty inspection | D | D | D | D | D | D | 1 | Implement |
| UI traceability navigation | D | D | D | D | D | D | 1 | Implement |
| UI report inspection | D | D | D | D | D | D | 1 | Implement |
| Validation/conformance integration boundary | E | E | E | E | E | E | 2 | Implement boundary, not full engine |
| Verification integration boundary | E | E | E | E | E | E | 2 | Implement boundary, not full framework |
| Deterministic validation of required input structure | D | D | D | D | D | D | 1/2 | Implement |
| Reproducible processing record | E | E | E | E | D | D | 2 | Implement minimum necessary form |
| Generic search engine | — | — | — | — | — | — | 3 | Defer |
| Universal reasoning engine | — | — | — | — | — | — | 3 | Defer |
| Generic ontology inference | — | — | — | — | — | — | 3 | Defer |
| Graph-database dependence | — | — | — | — | — | — | 3 | Defer |
| Universal query language | — | — | — | — | — | — | 3 | Defer |
| General workflow engine | — | — | — | — | — | — | 3 | Defer |
| Distributed microservice architecture | — | — | — | — | — | — | 3 | Defer |
| AI-specific semantic core | F | F | F | F | F | F | 3 | Defer |

## 7. Core Capability Set Indicated by the P0 Portfolio

The matrix indicates a relatively small shared core despite the domain diversity of the P0 portfolio.

### 7.1 Semantic core capabilities

The P0 portfolio provides strong evidence for a shared semantic core containing:

- stable identity;
- source and acquired-artifact representation;
- claim representation;
- evidence representation;
- explicit typed relationships;
- support/contradiction/qualification and unresolved assessment semantics as applicable;
- provenance;
- source locations;
- traceability;
- source/version state;
- integrity and authenticity/authority distinctions;
- structured assessment results;
- uncertainty and limitations;
- semantic-preserving machine representation.

These capabilities should remain domain-neutral.

### 7.2 Application-level capabilities

The following should remain primarily application/workflow concerns rather than being promoted into the semantic core merely because the P0 slices use them:

- claim extraction from natural-language documents;
- evidence discovery and retrieval strategies;
- source ranking or search strategies;
- domain-specific classification;
- report presentation formats;
- user-interface workflows;
- ingestion connectors;
- document parsing strategies;
- investigative or research methodologies.

The reference implementation may provide reusable interfaces for such capabilities where necessary, but their domain-specific behavior should remain replaceable.

## 8. ECRA-1200-Specific Implementation Boundary

VS-E01 demonstrates that architecture/design representation is required somewhere in the reference implementation. The P0 portfolio therefore provides implementation evidence for a bounded use of ECRA-1200 capabilities, including:

- architecture descriptions;
- architectural elements;
- architectural relationships;
- applicable constraints and assertions;
- viewpoints/views where required to demonstrate the selected workflow;
- provenance and traceability associated with architectural information;
- semantic-preserving machine representation.

This does not justify implementing the full breadth of ECRA-1200 before the selected workflow requires it.

In particular, the P0 portfolio does not by itself justify a generic architecture reasoning engine, a full architecture repository platform, or implementation of every ADL extension point.

## 9. Capability Dependencies

The capability matrix implies several important dependency chains.

### 9.1 Evidence-analysis chain

```text
Source / Artifact
    → Identity
    → Claim / Evidence
    → Typed Relationship
    → Assessment
    → Provenance / Traceability
    → Report
```

### 9.2 Engineering chain

```text
Requirement
    → Architecture / Design
    → Decision / Claim
    → Evidence
    → Traceability
    → Assessment
    → Report
```

### 9.3 Round-trip chain

```text
Logical model
    → machine representation
    → read-back
    → logically equivalent model
```

The round-trip requirement concerns semantic preservation rather than byte-for-byte serialization equality.

## 10. Minimum Reference Core Candidate

Subject to detailed P0 slice analysis, the initial reference core should be limited to the following capability families:

1. **Identity and entity references**
2. **Source and artifact registration**
3. **Claim and evidence objects**
4. **Typed relationship and assessment representation**
5. **Provenance and traceability**
6. **Integrity/authenticity/authority metadata boundaries**
7. **Minimal architecture/design representation needed by VS-E01**
8. **Machine representation and semantic round-trip support**
9. **Validation/conformance and verification integration contracts**
10. **Persistence/storage abstractions sufficient for the selected workflows**
11. **Application-facing APIs/services for the above capabilities**

The list is a candidate implementation boundary, not a commitment to a particular technology stack.

## 11. Capabilities Explicitly Deferred

The following remain deferred unless a selected slice or later evidence establishes a concrete need:

- universal semantic inference;
- generic reasoning engines;
- arbitrary graph analytics;
- universal search infrastructure;
- generalized workflow/orchestration engines;
- generalized multi-tenant platform features;
- domain-specific knowledge models;
- AI-specific semantic abstractions;
- broad plugin marketplaces;
- distributed deployment architecture;
- comprehensive policy/rules engines beyond the approved contracts;
- full implementation of all ECRA specification capabilities.

Deferral does not prohibit future implementation. It preserves the evidence-driven boundary.

## 12. Evolutionary Architecture and Deferred Capability Implementability

Deferral is an implementation-scope decision, not permission to introduce architectural coupling that makes future evolution unnecessarily expensive.

The reference implementation shall therefore be designed so that deferred capabilities can be introduced, replaced, or decomposed with minimal **avoidable** rework where reasonably foreseeable. This does not require predicting the final architecture or guaranteeing that every future capability can be added with little change.

The implementation should, as appropriate:

- maintain explicit responsibilities and cohesive component boundaries;
- define stable, technology-independent contracts between major capabilities;
- depend on replaceable abstractions/interfaces rather than concrete infrastructure where this materially improves replaceability;
- apply dependency inversion and other appropriate SOLID principles;
- use established design patterns where they simplify evolution rather than adding abstraction speculatively;
- avoid unnecessary coupling between persistence, messaging, external integrations, processing components, and application services;
- keep semantic contracts and core data models independent of deployment topology;
- isolate infrastructure-specific concerns from domain/semantic behavior;
- preserve clear boundaries between shared reference-core capabilities and application-specific behavior.

The reference implementation does **not** need to adopt a distributed or microservice architecture now. Distributed deployment is a possible future evolution path. The current architecture should nevertheless avoid decisions that would make later decomposition into separate processes or services require avoidable changes to ECRA semantic contracts or core responsibilities.

This principle applies equally to other deferred capabilities: future promotion should preferably occur through composition, extension, replacement, or decomposition of well-bounded components rather than invasive restructuring.

## 13. Capability Promotion Lifecycle

A capability that is initially deferred shall have an explicit mechanism for promotion when subsequent evidence establishes that it should be implemented.

The promotion lifecycle is:

```text
Deferred
   ↓
Candidate
   ↓
Evidence Collected
   ↓
Qualified
   ↓
Approved for Implementation
   ↓
Implemented
   ↓
Verified
```

The following transitions are also permitted where justified:

```text
Candidate → Rejected / Remains Deferred
Implemented → Retired
```

### 13.1 Promotion triggers

A deferred capability may become a Candidate when one or more of the following provide credible evidence:

1. a selected or newly approved vertical slice cannot be implemented correctly without it;
2. an approved normative ECRA requirement requires it;
3. it becomes necessary enabling infrastructure for an already justified capability;
4. multiple vertical slices demonstrate a reusable need that warrants promotion into the shared core;
5. implementation evidence demonstrates a material architectural or operational need that was not reasonably foreseeable during initial planning.

### 13.2 Qualification evidence

Before approval for implementation, the promotion record should establish, as applicable:

- the triggering vertical slice(s) or normative requirement(s);
- the capability definition and proposed boundary;
- the rationale for promotion;
- dependency and architectural impact;
- reuse assessment across existing and expected slices;
- whether the capability belongs in the shared reference core or an application layer;
- impact on existing semantic and implementation contracts;
- acceptance and verification criteria;
- the approval decision and decision authority.

Qualification does not automatically require promotion into the shared core. A capability may be qualified but implemented at the application layer, or remain deferred pending broader evidence.

### 13.3 Recording promotion decisions

Promotion decisions shall be recorded in the implementation coverage matrix and, where the architectural impact is material, in the applicable implementation/design record.

The coverage model should therefore track at least:

- lifecycle state;
- promotion evidence or decision basis;
- architectural impact;
- implementation placement (shared core or application layer);
- verification status.

Promotion is evidence-driven and reversible. A capability may later be retired, moved between core and application boundaries, or returned to a deferred state when subsequent evidence justifies the change.

## 14. Implementation Coverage Matrix Contract

The matrix shall evolve into a traceable implementation coverage model with, at minimum, these dimensions:

| Dimension | Purpose |
|---|---|
| ECRA capability | Identifies the specification capability being exercised |
| Source authority | Identifies the normative or approved source |
| Vertical slice | Identifies the workflow requiring the capability |
| Requirement | Identifies applicable product/system requirement(s) |
| Reference implementation component | Identifies where the capability is implemented |
| Application component | Identifies slice-specific implementation |
| UI demonstration | Identifies the user-visible demonstration |
| Verification | Identifies test/verification evidence |
| Status | Tracks planned, implemented, verified, deferred, or retired state |
| Lifecycle state | Tracks deferred, candidate, evidence collected, qualified, approved, implemented, verified, rejected, or retired state |
| Promotion evidence / decision | Records why a deferred capability was promoted, retained, or rejected |
| Architectural impact | Records material architectural consequences of the capability decision |
| Rationale | Records why the capability is included, excluded, or placed at a particular layer |

This structure is intended to prevent both under-implementation of demonstrated requirements and speculative expansion of the reference core.

## 15. Derivation Rules for New Capabilities

A new reference-implementation capability shall be admitted only when one of the following is demonstrated:

1. a selected vertical slice cannot be implemented correctly without it;
2. an approved normative requirement requires it;
3. it is necessary enabling infrastructure for an already justified capability;
4. multiple vertical slices demonstrate a reusable need that warrants promotion into the shared core.

A capability that is useful for only one application should remain at the application layer unless there is a clear reason to promote it.

A capability justified only by hypothetical future use shall be recorded as deferred rather than implemented speculatively.

When a deferred capability meets one or more admission criteria, it shall enter the Capability Promotion Lifecycle defined in §13. The lifecycle record shall provide the evidence and approval necessary to determine whether it is implemented in the shared core, implemented at the application layer, remains deferred, or is rejected.

## 16. Next Increment

The next implementation-planning increment should be **Detailed P0 Vertical Slice Specifications**.

Each P0 slice should be specified with:

- concrete source inputs;
- user roles and workflow steps;
- input/output contracts;
- required ECRA semantic objects;
- required relationships;
- provenance and traceability expectations;
- assessment behavior and uncertainty handling;
- UI workflow and screens;
- negative and boundary cases;
- acceptance criteria;
- required reference-core capabilities;
- application-specific capabilities;
- explicit exclusions.

The detailed slice specifications should then be used to refine this matrix before implementation of the minimum reference core begins.

## 17. Status

This document is submitted for review. Its contents are intended to provide an implementation-planning baseline for subsequent P0 vertical-slice specification work and shall not be interpreted as new normative ECRA requirements.
