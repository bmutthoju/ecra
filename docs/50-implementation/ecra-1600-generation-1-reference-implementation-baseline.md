# ECRA-1600 — Generation 1 Reference Implementation Baseline

> Status: REVIEW
> Authority: IMPLEMENTATION
> Generation: GEN1
> Scope: Reference implementation baseline for ECRA Generation 1
> Document Class: Implementation Baseline
> Depends On: Approved Gen1 requirements, approved Gen1 architecture, approved detailed design, approved decisions, approved contracts/schemas, approved verification criteria
> Current Baseline State: REVIEW

## 1. Purpose

ECRA-1600 defines the implementation baseline for the ECRA Generation 1 reference implementation.

Its purpose is to answer:

> Given the approved Gen1 requirements, architecture, detailed design, and vertical-slice specifications, how should the reference implementation be structured, built, tested, operated, and evolved?

ECRA-1600 establishes implementation-level choices and boundaries. It does not redefine ECRA semantics, requirements, architectural ownership, or the ADL meta-model.

The baseline is intentionally evidence-driven and vertical-slice-oriented. The first production capability is VS-J01 — Investigative Fact Check.

## 2. Authority and Precedence

This document is subordinate to:

1. approved Gen1 requirements;
2. approved Gen1 architecture;
3. approved Architecture Decision Records;
4. approved detailed design;
5. approved contracts, schemas, examples, and test vectors;
6. approved verification and acceptance criteria.

It governs implementation where the higher-authority artifacts are silent.

If this baseline conflicts with higher-authority material, the higher-authority material prevails and the conflict must be recorded.

This document must not be used to resolve a semantic or architectural conflict by implementation convenience.

## 3. Source Sufficiency and Repository Baseline

The baseline has been derived from the currently available repository material, including:

- `AGENTS.md`;
- approved Gen1 claim/evidence requirements;
- approved Gen1 context/evaluation requirements;
- approved Gen1 traceability/engineering requirements;
- approved requirements model and identifier scheme;
- approved ECRA-1200 Architecture Description Language architecture;
- approved ECRA-1200 detailed design foundation;
- approved ECRA-1200 canonical ADL meta-model;
- approved P0 vertical-slice portfolio;
- approved P0 vertical-slice specification framework;
- approved VS-J01 specification;
- approved Gen1 vertical-slice implementation guidance;
- approved Gen1 testing strategy;
- approved Gen1 engineering principles.

### 3.1 Repository gaps

The current `main` branch does not currently contain repository artifacts for:

- ECRA-1000 architecture;
- ECRA-1100 requirements framework;
- ECRA-1300 AIF;
- ECRA-1400 AVCF;
- ECRA-1500 AVPF;
- approved ADRs under `docs/40-decisions/`;
- executable contracts or schemas under `specs/`;
- verification artifacts under `docs/60-verification/`;
- production source code and tests.

These gaps do not authorize reconstruction of missing normative content.

Accordingly, ECRA-1600 establishes implementation structure and baseline technology choices while explicitly deferring any behavior that requires a missing higher-authority contract or specification.

Before ECRA-1600 is marked APPROVED, the missing upstream authority should be reconciled or the affected scope should be explicitly accepted as deferred.

## 4. Gen1 Implementation Objectives

The reference implementation shall prioritize:

1. conformance to approved ECRA semantics;
2. complete execution of approved vertical slices;
3. preservation of semantic identity and provenance;
4. deterministic and reproducible behavior where required;
5. explicit contracts and failure behavior;
6. testability and verification;
7. security and authorization boundaries;
8. operational observability;
9. maintainability and replaceability;
10. appropriate performance without speculative infrastructure.

Gen1 is a reference implementation, not a feature-maximal product.

## 5. Implementation Scope

### 5.1 In scope

The Gen1 implementation baseline covers:

- the shared semantic/domain core required by approved slices;
- application/use-case orchestration;
- persistence abstraction and the initial persistence implementation;
- source and artifact handling required by approved slices;
- evidence, claims, relationships, assessment, provenance, traceability, identity, and version/lineage behavior established by approved requirements;
- machine representation and round-trip behavior where an approved contract exists;
- application-facing APIs required by the selected slice;
- a minimal UI sufficient to demonstrate the approved vertical slice;
- validation/conformance and verification integration at the approved boundaries;
- security, configuration, observability, testing, local development, CI, and runtime packaging required for production-quality Gen1 behavior.

### 5.2 Explicitly out of scope

Gen1 does not introduce, merely for implementation convenience:

- microservice deployment;
- service mesh;
- event streaming infrastructure;
- universal semantic inference;
- a generic reasoning engine;
- autonomous fact checking;
- universal search/crawling;
- generalized workflow orchestration;
- generalized multi-tenancy;
- graph analytics infrastructure;
- domain-specific knowledge models not required by a selected slice;
- AI-specific semantic abstractions;
- plugin marketplaces;
- broad policy engines;
- autonomous engineering decisions;
- speculative distributed transactions;
- speculative caching or asynchronous processing.

A future capability may be promoted only through the approved capability lifecycle.

## 6. Reference Implementation Architecture

The implementation shall use a cohesive modular architecture with explicit dependency direction.

Logical structure:

    External Interfaces / UI / API
                 |
                 v
          Application Layer
                 |
                 v
           Domain Core
                 |
          Stable Ports
                 |
                 v
      Infrastructure Adapters

The implementation may be packaged as a single deployable application in Gen1.

The logical boundaries are more important than physical process boundaries.

The architecture shall permit later extraction of cohesive modules without requiring Gen1 to deploy them as separate services.

### 6.1 Dependency direction

Dependencies shall point toward stable semantic and application contracts.

The domain core must not depend on:

- database implementations;
- HTTP frameworks;
- UI frameworks;
- external connectors;
- deployment infrastructure;
- serialization libraries where an abstraction is sufficient.

Infrastructure adapters implement stable ports defined by the appropriate inner boundary.

## 7. Initial Technology Baseline

The following technology choices are proposed as the Gen1 reference implementation baseline. They are implementation decisions for review and do not claim to have been established by the earlier ECRA documents.

| Concern | Gen1 baseline |
|---|---|
| Backend language/runtime | Java on a supported LTS JDK |
| Backend application framework | Spring Boot |
| Build/package management | Maven |
| Primary persistence | PostgreSQL |
| Persistence access | Explicit repository/persistence ports with a relational adapter |
| API style | HTTP/JSON at application boundaries where an API is required |
| Frontend | React with TypeScript |
| Unit testing | JUnit |
| Mocking/test doubles | Mockito where justified |
| Browser/UI testing | A repository-approved browser test framework selected during implementation |
| Containerization | Docker |
| Local multi-component runtime | Docker Compose only where integration testing requires it |
| CI/CD | GitHub Actions |
| Observability | Structured logs, metrics, traces, health/readiness signals as applicable |
| Source control | Git/GitHub |

### 7.1 Technology-selection principles

The technology baseline is intentionally conventional and replaceable.

A technology may be replaced only when:

- the replacement preserves approved semantics and contracts;
- architectural boundaries remain intact;
- the replacement does not introduce an avoidable Gen1 dependency;
- migration and verification costs are understood;
- the change is recorded when material.

Concrete dependency versions shall be pinned in the build configuration and updated through normal dependency review. This document does not prescribe a version number that is not required by an approved contract.

## 8. Module and Package Baseline

The initial backend implementation should use a modular structure equivalent to:

    <root>
      ├── domain
      │   ├── identity
      │   ├── source
      │   ├── artifact
      │   ├── claim
      │   ├── evidence
      │   ├── relationship
      │   ├── assessment
      │   ├── provenance
      │   └── traceability
      │
      ├── application
      │   ├── usecase
      │   ├── command
      │   ├── query
      │   └── port
      │
      ├── infrastructure
      │   ├── persistence
      │   ├── source
      │   ├── artifact
      │   ├── serialization
      │   └── external
      │
      └── interfaces
          ├── api
          └── configuration

The exact Java package names remain an implementation detail.

No package name creates a new ECRA semantic type.

The frontend shall be separately organized around user-facing workflows and API contracts rather than mirroring the database structure.

## 9. Domain Model Boundary

The domain model shall implement only semantics supported by approved requirements and design.

For VS-J01, the implementation is expected to require concepts corresponding to:

- stable identity;
- source;
- acquired artifact;
- claim;
- evidence;
- typed relationship;
- assessment;
- provenance;
- source location;
- version/lineage;
- integrity/authenticity/authority metadata where required;
- evaluation context/result where established by the approved requirements.

These are implementation realizations of approved semantics, not permission to create additional ECRA root concepts.

### 9.1 Domain rules

Domain behavior shall:

- preserve stable identity;
- preserve explicit relationships;
- preserve provenance;
- preserve relevant historical versions;
- distinguish observations/evidence from claims and assessments;
- preserve uncertainty and limitations where required;
- reject invalid state transitions explicitly;
- avoid silently replacing historical information.

## 10. Application Layer

The application layer owns use-case orchestration.

It shall:

- coordinate domain operations;
- enforce application-level authorization;
- coordinate ports and adapters;
- manage transaction boundaries where required;
- translate external requests into domain operations;
- return explicit application results/errors;
- avoid embedding storage-specific behavior.

For VS-J01, the application workflow shall support the approved sequence from source selection through artifact preservation, claim handling, evidence association, provenance/location capture, assessment, limitations, and reporting.

Application-specific discovery, extraction, source ranking, connector behavior, and presentation logic remain outside the domain core where the approved VS-J01 specification assigns them to the application.

## 11. Persistence Baseline

Persistence shall be isolated behind deliberate persistence ports.

PostgreSQL is the initial reference implementation store because the approved implementation principles require durable identity, relationships, provenance, version/lineage, assessment state, and historical preservation while discouraging storage-driven semantic design.

The implementation shall not expose relational tables as public application contracts.

### 11.1 Persistence requirements

The persistence implementation shall preserve, where applicable:

- stable identifiers;
- current and historical versions;
- provenance;
- source locations;
- relationships;
- assessments;
- integrity/authenticity/authority metadata;
- required traceability;
- lifecycle state.

Transaction and consistency boundaries shall be defined per use case.

Storage-specific optimization shall not redefine domain semantics.

### 11.2 Persistence evolution

The persistence port must permit a future storage implementation without changing the domain model.

A storage migration is not required merely because another database could support a future workload.

No distributed database, graph database, search cluster, or event store is part of the Gen1 baseline unless an approved slice demonstrates a requirement that cannot reasonably be met by the initial implementation.

## 12. Source and Artifact Handling

Source and artifact handling shall distinguish:

- source identity;
- acquired artifact identity;
- artifact version;
- source location;
- acquisition metadata;
- integrity metadata;
- provenance;
- user/application metadata.

The implementation shall preserve multiple versions where the approved requirements require historical preservation.

A newer artifact does not silently overwrite the historical artifact.

Untrusted content is treated as data unless controlled execution is explicitly authorized.

## 13. Relationship Handling

Relationships shall be explicit, typed, identifiable where required, and persisted independently of presentation.

The implementation shall not encode semantic relationships solely through database conventions, object references, or UI state.

The detailed canonical relationship catalog remains governed by the applicable ECRA semantic/design authority.

If a relationship required by an implementation is not defined by approved authority, implementation shall stop at that boundary rather than inventing a new semantic relationship.

## 14. Assessment and Evaluation

Assessment behavior shall preserve:

- the assessed subject;
- assessment outcome/state;
- supporting or contradicting evidence relationships;
- qualification/context where applicable;
- uncertainty and limitations;
- provenance;
- version context.

The implementation must not collapse assessment into a mandatory universal numeric truth score.

Automated processing may assist a workflow only where the approved slice explicitly authorizes it. Gen1 shall not introduce autonomous truth determination or universal reasoning.

## 15. Machine Representation and Round-Trip

Machine representation is an adapter boundary.

The implementation shall follow the approved ECRA-1300/AIF contracts when those contracts are available.

Until the applicable concrete serialization contract is present, Gen1 implementation shall not invent a competing canonical wire schema.

Where round-trip behavior applies:

    Logical Model
         ↓
    Machine Representation
         ↓
    Reconstructed Logical Model

Verification shall establish semantic equivalence for the applicable content, including identity, membership/reference, relationships, provenance, assessments, versions/lineage, limitations, and relevant metadata.

Byte-for-byte equality is not required unless an approved contract explicitly requires it.

## 16. API and Integration Baseline

The application shall expose only APIs required by approved vertical slices or qualified enabling capabilities.

API contracts shall:

- use stable identifiers;
- validate inputs;
- define explicit success and error behavior;
- avoid exposing persistence structures;
- preserve provenance/version context where required;
- support deterministic behavior where required;
- be independently contract-tested.

The API layer shall not become a second domain model.

Concrete endpoint names and request/response schemas shall be established in executable contract artifacts before production API implementation.

## 17. UI Baseline

The Gen1 UI exists to demonstrate approved vertical slices.

For VS-J01, the UI should support the approved user workflow, including:

1. source selection;
2. artifact/source review;
3. claim identification and correction;
4. evidence registration/association;
5. provenance and source-location inspection;
6. assessment;
7. limitations/uncertainty;
8. final review/report presentation.

The UI shall not introduce new core semantics merely because a screen appears to need them.

UI state and presentation models may differ from domain models.

## 18. Security Baseline

Security is part of Gen1 production quality.

The implementation shall apply, where relevant:

- authentication;
- authorization;
- least privilege;
- input validation;
- output safety;
- secret management;
- sensitive-data minimization;
- protected logging;
- integrity verification;
- provenance preservation;
- auditability;
- safe error handling;
- dependency/supply-chain review.

Authorization shall be enforced at the appropriate application boundary and must not rely solely on UI restrictions.

Untrusted documents, scripts, macros, binaries, and other artifacts must not be executed as part of normal evidence processing unless explicitly authorized.

## 19. Configuration and Environment Management

Configuration shall be externalized from source code where environment-specific behavior is required.

The implementation shall distinguish:

- application configuration;
- environment configuration;
- secrets;
- test configuration.

Secrets must not be committed to the repository.

Configuration must not silently change semantic behavior.

Hidden feature flags shall not be introduced for speculative future functionality.

## 20. Observability Baseline

The reference implementation shall provide sufficient observability to establish:

- what operation occurred;
- when it occurred;
- which request/correlation context was involved;
- which entity/artifact/version was involved;
- which dependency was used;
- whether processing completed or partially failed;
- how relevant behavior can be investigated and reproduced.

Use:

- structured application logs;
- metrics where material;
- traces across meaningful boundaries;
- correlation identifiers;
- health/readiness signals;
- domain/provenance records where required.

Do not log sensitive content merely to make debugging easier.

Observability artifacts may be used as authorized investigative inputs to VS-F01 within its approved workflow and authorization boundaries.

## 21. Reliability and Failure Handling

External and failure-prone operations shall have explicit behavior for:

- timeout;
- bounded retry where appropriate;
- idempotency where repeated requests are possible;
- partial failure;
- dependency failure;
- resource exhaustion;
- recovery.

Failures must not be hidden by silently substituting data.

Historical results must not be silently rewritten because a later external dependency changes.

Retries shall be used only where the operation is safe to retry or has explicit idempotency protection.

## 22. Concurrency and State Management

Gen1 shall use the simplest concurrency model that satisfies the selected slice.

The implementation shall:

- minimize shared mutable state;
- make ownership explicit;
- preserve consistency boundaries;
- define ordering guarantees where required;
- use immutable structures where practical;
- test concurrency-sensitive behavior;
- make repeated operations safe where idempotency is required.

No asynchronous messaging or distributed coordination mechanism is required merely for future scale.

## 23. DSA and Performance Baseline

Implementation choices shall be evidence-driven.

For each material data path:

1. identify the data shape;
2. identify access patterns;
3. select appropriate data structures/indexes;
4. analyze time and space complexity;
5. identify resource bounds;
6. test representative and boundary workloads;
7. optimize only when measurements justify it.

Expected baseline choices include:

- keyed lookup structures for stable identity;
- sets for uniqueness;
- ordered structures when deterministic ordering is required;
- relational indexes for demonstrated access paths;
- streaming for large artifacts only where required;
- bounded processing for externally supplied content.

Caching, asynchronous processing, specialized indexing, and distributed computation are not baseline requirements.

## 24. Testing Architecture

Testing shall follow the approved testing strategy:

- unit tests for deterministic domain/application behavior;
- component tests for cohesive modules;
- contract tests for API and cross-component contracts;
- integration tests for real persistence and adapter interactions;
- E2E tests for complete vertical-slice behavior.

The first implementation increment shall establish the test harness before substantial VS-J01 behavior is added.

Tests shall cover, where applicable:

- normal behavior;
- invalid input;
- boundary behavior;
- failure behavior;
- partial processing;
- version changes;
- provenance;
- conflicting evidence;
- authorization;
- external dependency failures;
- semantic round-trip.

Test data shall be deterministic, minimal, representative, safe, and free of secrets.

## 25. CI and Local Development

The implementation shall provide a repeatable local build/test workflow and CI pipeline.

The baseline CI stages are:

    Build
      ↓
    Unit Tests
      ↓
    Component / Contract Tests
      ↓
    Integration Tests
      ↓
    E2E Tests
      ↓
    Quality / Security Checks

The exact commands are determined by the selected technology configuration.

CI shall fail on:

- compilation/build failure;
- test failure;
- required contract incompatibility;
- required static/quality checks;
- required security checks.

Local development shall be reproducible without requiring undocumented manual infrastructure.

## 26. Runtime and Deployment Baseline

Gen1 shall initially target a single deployable application with externally managed persistent storage.

A minimal runtime topology is:

    Browser / Client
          |
        HTTP
          |
    ECRA Application
          |
    PostgreSQL

External source/artifact integrations are isolated behind adapters.

Containerization may be used to reproduce the application runtime and integration environment.

Gen1 does not require microservice deployment, Kubernetes, service mesh, distributed tracing infrastructure, or event streaming infrastructure as mandatory runtime components.

## 27. Versioning and Compatibility

The implementation shall preserve:

- stable identity;
- artifact/source versions;
- lineage;
- provenance;
- relevant historical assessments.

Version changes shall not silently mutate historical state.

Public contracts shall use explicit compatibility rules once the corresponding executable contracts are established.

Schema evolution shall preserve the ability to interpret supported historical data or provide an explicit migration strategy.

## 28. Vertical-Slice Implementation Strategy

Implementation follows the approved vertical-slice-first approach.

The sequence is:

    Foundation
        ↓
    Domain / Contracts
        ↓
    Application Behavior
        ↓
    Runtime Execution
        ↓
    Required Persistence / Infrastructure
        ↓
    Observability
        ↓
    API / Integration Boundary
        ↓
    End-to-End Verification

VS-J01 is the first implementation slice.

Shared capabilities shall be promoted only when:

- the selected slice cannot be implemented correctly without them;
- a normative Gen1 requirement requires them;
- they are necessary enabling infrastructure;
- multiple slices demonstrate the same reusable need;
- material architecture/operations evidence justifies them.

## 29. Capability Promotion and Deferral

Use the approved lifecycle:

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

Optional outcomes include Rejected/Remains Deferred and Retired.

A capability is not implemented merely because it is permitted by the architecture.

## 30. Traceability

Every meaningful implementation capability shall maintain traceability across:

    Requirement
        ↓
    Architecture
        ↓
    Design
        ↓
    Contract
        ↓
    Implementation
        ↓
    Test
        ↓
    Verification Evidence

For each VS-J01 increment, the implementation record should identify:

- requirement(s) satisfied;
- architecture/design owner;
- applicable contract;
- source/module;
- tests;
- acceptance criteria;
- verification result.

Missing upstream artifacts shall be recorded as a traceability gap rather than filled with assumptions.

## 31. Replaceability and Evolution

The following are intended to remain replaceable implementation concerns:

- persistence adapter;
- source/artifact connectors;
- serialization adapter;
- API transport;
- UI framework;
- deployment packaging.

The following are not casually replaceable because they are governed by ECRA semantics or approved architecture:

- semantic ownership;
- identity semantics;
- relationship semantics;
- provenance semantics;
- traceability semantics;
- lifecycle/version semantics;
- approved architectural boundaries;
- externally approved contracts.

Technology substitution must preserve the latter.

## 32. Production-Quality Definition

The Gen1 reference implementation is production-quality when the applicable slice demonstrates:

1. specification conformance;
2. architectural conformance;
3. explicit domain ownership;
4. stable contracts;
5. durable required state;
6. correct normal and boundary behavior;
7. explicit failure behavior;
8. security controls;
9. sufficient observability;
10. reproducible builds/tests;
11. semantic round-trip where applicable;
12. complete E2E workflow;
13. traceable verification evidence;
14. maintainable and replaceable infrastructure;
15. no speculative Gen1 capability.

Production-quality does not mean implementing every capability permitted by ECRA.

## 33. Explicit Deferred Decisions

The following remain deferred until sufficient authority exists:

- concrete ECRA-1300 serialization schema;
- complete canonical relationship catalog where not yet approved;
- validation/conformance implementation contracts;
- verification/proof contracts;
- persistence schema details that would encode unspecified semantics;
- API endpoint/request/response contracts not yet approved;
- external source connector contracts;
- deployment topology beyond the Gen1 single-application baseline;
- distributed deployment;
- asynchronous event infrastructure;
- generalized search/indexing;
- AI/LLM-specific semantic capabilities.

These deferrals are deliberate scope controls.

## 34. Required Follow-On Artifacts

Before substantial production implementation proceeds beyond the initial foundation, the following should be established where applicable:

1. missing upstream approved architecture/requirements documents in the repository;
2. implementation ADRs for material technology decisions;
3. executable API/domain/persistence contracts;
4. concrete machine-representation contracts from ECRA-1300;
5. applicable validation/conformance and verification contracts;
6. canonical examples and test vectors;
7. CI configuration;
8. initial source/test module structure.

The absence of one of these artifacts must not be hidden by implementation assumptions.

## 35. Implementation Decision Register

This baseline records the following proposed Gen1 implementation decisions for review:

| ID | Decision | Rationale | Status |
|---|---|---|---|
| ECRA-1600-D01 | Use a cohesive modular application rather than Gen1 microservices | Preserves boundaries while avoiding speculative distributed infrastructure | REVIEW |
| ECRA-1600-D02 | Use Java/JVM as the backend implementation platform | Suitable for a strongly typed, modular, testable reference implementation; does not alter ECRA semantics | REVIEW |
| ECRA-1600-D03 | Use Spring Boot as the backend application framework | Provides conventional application/runtime integration while keeping domain logic framework-independent | REVIEW |
| ECRA-1600-D04 | Use PostgreSQL as the initial reference persistence implementation | Fits durable relational identity, relationships, provenance, versioning, and transactional behavior without making storage the semantic authority | REVIEW |
| ECRA-1600-D05 | Use React/TypeScript for the reference UI | Provides a typed application UI suitable for demonstrating vertical slices without coupling UI models to persistence | REVIEW |
| ECRA-1600-D06 | Use Maven, Docker, and GitHub Actions for build/runtime/CI foundations | Provides repeatable build and integration execution without introducing distributed infrastructure | REVIEW |

These decisions are implementation-level proposals. They do not override missing or higher-authority ECRA documents.

## 36. Approval Criteria

ECRA-1600 may move from REVIEW to APPROVED when:

- the implementation technology baseline is accepted;
- no conflict with approved requirements/architecture/design is identified;
- material technology choices are accepted or recorded through the appropriate decision mechanism;
- missing upstream authority is reconciled or its absence is explicitly accepted for the affected implementation scope;
- the VS-J01 implementation path is sufficiently defined;
- persistence, API, serialization, security, testing, and runtime boundaries are considered adequate for Gen1 implementation;
- critical review finds no unresolved material implementation contradiction.

## 37. Status

**REVIEW**

This document is proposed as the ECRA Generation 1 Reference Implementation Baseline. It is not yet an approved implementation authority.
