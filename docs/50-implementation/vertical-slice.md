# ECRA Generation 1 Reference Implementation — Vertical Slice Execution

> Status: REVIEW
> Authority: IMPLEMENTATION
> Generation: GEN1
> Scope: Implementation sequence and execution rules for the approved vertical-slice portfolio

## 1. Purpose

This document defines the execution sequence for the ECRA Generation 1 reference implementation.

The implementation is driven by the approved P0 vertical-slice portfolio. A capability is implemented when a selected slice demonstrates that it is required, or when it is necessary enabling infrastructure for such a capability.

The objective is the smallest coherent production-quality implementation that demonstrates the approved ECRA contracts without implementing speculative generality.

## 2. Authoritative Inputs

Implementation shall be governed by approved Gen1 requirements, architecture, architecture/design decisions, detailed design, contracts and schemas when available, vertical-slice specifications, verification criteria, and this implementation guidance.

Informational and historical material shall not override approved project artifacts.

## 3. P0 Implementation Sequence

1. VS-J01 — Investigative Fact Check
2. VS-R01 — Lecture or Sermon Claim Review
3. VS-B01 — Company Due Diligence
4. VS-L01 — Case Evidence Review
5. VS-F01 — Incident / Digital Forensic Investigation
6. VS-E01 — Engineering Design Evidence Review

The sequence progressively exercises claim/evidence review, domain neutrality, source comparison, provenance/versioning, evidence-first investigation, and requirements/architecture traceability.

A later slice may expose a defect in an earlier shared capability. Such a defect is fixed at the shared boundary only when evidence demonstrates that the capability is genuinely cross-slice.

## 4. Implementation Levels

### Level 1 — Demonstrated Necessity
Directly required by the selected slice. Implement it.

### Level 2 — Enabling Infrastructure
Required to implement Level 1 cleanly, safely, or reproducibly. Implement it when the dependency is demonstrated.

### Level 3 — Speculative Capability
Permitted by the specifications but not required by the selected slice set. Defer it.

## 5. Slice Completion Sequence

```text
Slice specification
    ↓
Source sufficiency check
    ↓
Requirement / architecture / design traceability
    ↓
Capability impact assessment
    ↓
Foundation / domain contracts
    ↓
Application workflow
    ↓
Runtime execution
    ↓
Required persistence / infrastructure
    ↓
Observability and security
    ↓
API / integration boundary
    ↓
UI workflow
    ↓
Negative / boundary verification
    ↓
End-to-end demonstration
    ↓
Verification evidence
    ↓
Slice completion
```

A backend-only implementation is not sufficient for slice completion.

## 6. Work Item Traceability

Every meaningful implementation change shall be traceable through:

```text
Requirement → Architecture → Detailed design → Slice acceptance criterion
→ Implementation → Automated test → Verification evidence
```

If a change cannot be associated with an approved requirement, acceptance criterion, defect, or necessary enabling capability, treat it as potentially out of scope.

## 7. Reference-Core Promotion

A capability discovered inside an application shall not automatically become shared infrastructure.

Promotion requires evidence such as multiple selected slices requiring it, a normative requirement, necessary enabling infrastructure, or material reusable value without weakening boundaries.

Use the established lifecycle:

```text
Deferred → Candidate → Evidence Collected → Qualified
→ Approved for Implementation → Implemented → Verified
```

A qualified capability may remain application-local.

## 8. Initial Shared-Core Candidate Set

The initial candidate set is limited to capabilities already identified by the cross-slice analysis:

- stable semantic identity;
- source and artifact registration;
- claims and evidence;
- typed relationships;
- assessments;
- provenance and traceability;
- integrity/authenticity/authority metadata boundaries;
- bounded architecture/design representation when required by E01;
- machine representation and semantic round-trip;
- persistence abstraction;
- application-facing service/API boundaries;
- validation/conformance integration boundaries;
- verification integration boundaries.

This is not permission to implement all candidates immediately.

## 9. Application Boundary

Slice applications own domain-specific source selection, parsing/extraction, claim identification, evidence discovery, domain-specific interpretation, review criteria, report presentation, external-tool integration, and user interaction.

Application behavior shall use shared semantic capabilities without redefining their ownership.

## 10. Architecture and Deployment Boundary

Generation 1 shall use the approved architecture.

Do not introduce distributed microservices, service meshes, event-driven infrastructure, graph-database dependence, universal workflow engines, or generalized multi-tenancy unless an approved requirement or implementation decision promotes them.

The design shall preserve cohesive boundaries, dependency inversion, replaceable integrations, and contracts that can be separated later without avoidable semantic changes.

## 11. Persistence and Infrastructure

Persistence shall be introduced only to the extent required by the selected slice and approved architecture/design.

The implementation shall preserve stable identity, version/lineage, provenance, source locations, relationships, assessment state, and historical review state where required.

Do not define persistence contracts merely to suit a convenient storage engine.

## 12. Security and Operational Baseline

Every selected slice shall address applicable authorization boundaries, sensitive artifact handling, integrity metadata, provenance, auditability, deterministic validation, failure isolation, reproducibility, observability, and safe handling of untrusted artifacts.

Untrusted documents, scripts, models, binaries, or macros shall be treated as data unless explicitly authorized controlled execution is required.

## 13. End-to-End Requirement

A slice is complete only when the user-visible workflow demonstrates relevant input/source selection, semantic object inspection, relationships/traceability, evidence and assessment, provenance/source location, uncertainty/limitations, report/result generation, and applicable negative/boundary behavior.

Unit tests alone do not constitute slice completion.

## 14. Change Discipline

Implementation PRs shall remain narrow and reviewable. Do not combine unrelated refactoring, speculative infrastructure, future-slice functionality, architecture changes, or broad formatting changes.

If implementation reveals a conflict with an approved requirement or architecture, stop the affected work and record the conflict rather than silently changing the specification.

## 15. Current Execution State

The P0 slice specifications through VS-E01 are approved.

The repository currently contains the specification/design baseline but does not yet contain the production implementation tree or the implementation-specific execution documents referenced by the repository agent guidance.

Therefore this document establishes the controlled implementation sequence and does not authorize inventing a source language, runtime, persistence technology, public API, or deployment topology not established by the applicable approved architecture/design baseline.

## 16. First Implementation Increment

The first production implementation increment shall be VS-J01.

Before production code is introduced, J01 implementation work shall establish only the minimum foundation required by its approved specification:

- stable identity;
- source/artifact registration;
- claim representation;
- evidence representation;
- typed claim/evidence relationships;
- assessment representation;
- provenance and source locations;
- version/lineage where required;
- machine representation and round-trip;
- persistence abstraction sufficient for the slice;
- application workflow;
- UI demonstration;
- automated verification.

Capabilities discovered during J01 that are not required for the slice remain deferred.

## 17. Definition of Done

An implementation increment is ready for merge only when:

1. applicable specification and acceptance criteria are traceable;
2. implementation respects approved architecture;
3. automated tests cover normal, boundary, and failure behavior;
4. relevant contract behavior is verified;
5. provenance and identity are preserved;
6. required persistence behavior is verified;
7. observability and security boundaries are addressed;
8. the user-visible workflow is demonstrable;
9. no speculative capability has been introduced;
10. verification evidence is recorded in the PR.

## 18. Status

This implementation guidance is **REVIEW** and is intended to govern the first Generation 1 reference-implementation increments once approved.
