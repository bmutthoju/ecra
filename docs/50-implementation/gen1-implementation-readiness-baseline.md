# Gen1 Implementation Readiness Baseline

> Status: REVIEW
> Authority: IMPLEMENTATION
> Generation: GEN1
> Scope: Current implementation readiness and source-sufficiency baseline
> Baseline commit: 554e0f018bee4bca07bc4fdd38c4564df741097d

## 1. Purpose

This document records the implementation baseline after the initial Gen1 implementation foundation was merged and establishes whether the repository contains sufficient approved authority to begin the next substantive implementation increment.

It is an implementation-control artifact. It does not redefine ECRA semantics, requirements, architecture, or ownership.

## 2. Current Implementation State

PR #27 established and merged the initial executable Gen1 foundation.

The current implementation contains:

- Maven project configuration;
- Java 25 build target;
- Spring Boot application bootstrap;
- application-context test;
- minimal externalized configuration;
- GitHub Actions build and test workflow;
- Docker runtime packaging using a non-root user;
- local build, test, application, and Docker instructions in README.md.

The authoritative CI workflow successfully executed the Java 25 Maven verification build for the merged foundation.

The current application is intentionally not yet an HTTP service and does not yet implement VS-J01 business behavior.

## 3. Applicable Implementation Authority

The following approved implementation guidance is available and applicable:

- docs/50-implementation/ecra-1600-generation-1-reference-implementation-baseline.md
- docs/50-implementation/vertical-slice.md
- docs/50-implementation/testing-strategy.md
- docs/50-implementation/engineering-principles.md
- AGENTS.md

ECRA-1600 establishes VS-J01 as the first production capability and requires implementation to remain subordinate to approved requirements, architecture, detailed design, contracts, schemas, examples, test vectors, and verification criteria.

## 4. Available VS-J01 Authority

The repository contains the approved VS-J01 specification:

docs/00-project/ecra-p0-vs-j01-investigative-fact-check.md

It establishes the first vertical-slice workflow and identifies requirements involving source material and acquired artifacts, claims, evidence, explicit claim/evidence association, source locations, provenance and traceability, assessment, integrity/authenticity/authority information where applicable, evaluation/result representation, machine representation and semantic round-trip, UI inspection, and reporting.

The repository also contains approved Gen1 requirement documents covering claim and evidence, context and evaluation, traceability and engineering, and the requirements model and identifier scheme.

The approved ECRA-1200 architecture and detailed design foundation are also present.

## 5. Source Sufficiency Check

### 5.1 Sufficient for implementation-foundation work

The repository is sufficient for the already-completed implementation foundation because ECRA-1600 establishes the applicable implementation baseline and the foundation does not introduce substantive ECRA semantic behavior.

### 5.2 Not sufficient for VS-J01 domain implementation

The repository is not yet source-sufficient for the next domain/contract implementation increment.

The following higher-authority or implementation-enabling artifacts are currently absent from main:

| Missing artifact | Impact |
|---|---|
| ECRA-1000 — Evidence-Centric Reference Architecture | Required architectural/semantic authority referenced by current Gen1 requirements and VS-J01 |
| ECRA-1100 — Requirements Traceability Framework | Required requirements/traceability authority referenced by current Gen1 requirements |
| ECRA-0010 — Shared Semantic Foundation | Required portfolio-wide semantic ownership and shared identity/lifecycle/provenance/relationship semantics |
| ECRA-1300 — Architecture Interchange Format | Required before implementing concrete canonical machine representation |
| ECRA-1400 — Architecture Validation & Conformance Framework | Required for concrete validation/conformance integration |
| ECRA-1500 — Architecture Verification & Proof Framework | Required for concrete verification/proof integration |
| Approved ADRs under docs/40-decisions/ | Material implementation decisions are not yet recorded in repository ADR artifacts |
| Executable contracts/schemas/examples/test vectors under specs/ | Concrete cross-component and machine-representation contracts are not yet available |
| Verification artifacts under docs/60-verification/ | Formal verification/release evidence baseline is not yet present |

These are repository-state findings. They are not permission to reconstruct missing authority from historical discussions or implementation convenience.

## 6. Consequence for the Next Increment

The next substantive increment must not introduce the VS-J01 domain model yet.

In particular, implementation should not independently define shared identity types, portfolio-wide relationship semantics, canonical provenance semantics, canonical lifecycle/version semantics, domain ownership boundaries, concrete serialization contracts, validation/conformance interfaces, or verification/proof interfaces.

Those decisions depend on missing higher-authority artifacts.

## 7. What Can Proceed

The following work can proceed without inventing missing authority:

1. maintain the executable Gen1 foundation;
2. maintain CI/build/container documentation;
3. prepare implementation traceability and coverage records;
4. reconcile the missing-authority dependency list;
5. establish the repository baseline for the next implementation increment;
6. once the missing semantic authorities are present, perform a fresh source-sufficiency check before domain implementation.

## 8. Readiness Decision

| Area | Status |
|---|---|
| Repository build foundation | READY |
| Automated CI verification | READY |
| Local development workflow | READY |
| Gen1 implementation architecture baseline | READY |
| VS-J01 specification baseline | READY |
| Gen1 functional requirement baseline | PARTIAL — higher-level authorities referenced by the requirements are absent |
| Shared semantic domain baseline | BLOCKED |
| VS-J01 domain implementation | BLOCKED |
| Persistence implementation | BLOCKED |
| Canonical serialization implementation | BLOCKED |
| Validation/conformance implementation | BLOCKED |
| Verification/proof implementation | BLOCKED |
| Full VS-J01 vertical slice | BLOCKED |

## 9. Required Next Action

Before implementing VS-J01 domain semantics, restore the missing authoritative specification baseline in the repository.

The highest-priority prerequisite is the Shared Semantic Foundation, together with the applicable ECRA-1000 and ECRA-1100 authorities.

After those artifacts are available, repeat the source-sufficiency check and derive the smallest domain increment directly from the approved semantics.

## 10. Scope Boundary

This document does not introduce new ECRA semantic concepts, change the frozen Gen1 architecture, redefine requirements, create implementation contracts, prescribe persistence schemas, prescribe serialization formats, promote deferred capabilities, or authorize speculative infrastructure.

Its sole purpose is to make the current implementation-readiness state explicit and prevent implementation from outrunning repository authority.
