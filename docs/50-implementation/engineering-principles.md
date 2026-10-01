# ECRA Generation 1 Reference Implementation — Engineering Principles and Practices

> Status: APPROVED
> Authority: IMPLEMENTATION
> Generation: GEN1
> Scope: Reusable engineering principles, practices, patterns, and review criteria for implementing approved Generation 1 vertical slices

## 1. Purpose

This document defines the engineering practices to apply consistently across ECRA Generation 1 vertical slices. It complements `docs/50-implementation/vertical-slice.md` and `docs/50-implementation/testing-strategy.md`.

It does not authorize capabilities beyond approved requirements, slice acceptance criteria, or qualified enabling capabilities.

> Apply strong software engineering practices to realize the approved ECRA design; do not use engineering sophistication as a reason to expand ECRA semantics or Gen1 scope.

## 2. Engineering Decision Hierarchy

Engineering choices are subordinate to:

1. Approved ECRA requirements and semantic ownership.
2. Approved Gen1 architecture.
3. Approved ADRs and material architectural decisions.
4. Approved detailed design.
5. Approved contracts, schemas, examples, and test vectors.
6. Approved vertical-slice requirements and acceptance criteria.
7. Approved implementation and verification guidance.
8. Local implementation decisions that do not materially affect the above.

When approved material is materially insufficient, stop and follow the project's clarification or decision process rather than guessing.

## 3. Core Engineering Principles

Implementation should emphasize:

- correctness and specification conformance;
- explicit behavior and clear contracts;
- high cohesion and low coupling;
- SOLID principles applied pragmatically;
- dependency inversion and replaceable infrastructure;
- deterministic behavior where required;
- immutability where it simplifies correctness;
- explicit lifecycle and state transitions;
- testability and reproducibility;
- observability and operational safety;
- security and least privilege;
- appropriate performance rather than premature optimization;
- simplicity and maintainability;
- incremental, evidence-driven evolution.

Use the smallest complete design that satisfies the applicable requirements. Avoid abstraction for its own sake.

## 4. DSA — Data Structures and Algorithms

For meaningful data-processing paths:

1. identify the data shape and access pattern;
2. select an appropriate data structure;
3. analyze time and space complexity;
4. identify material worst-case behavior;
5. consider memory growth and resource bounds;
6. test representative and boundary inputs;
7. optimize only when evidence justifies additional complexity.

Typical choices include maps/indexes for identity lookup, sets for uniqueness, ordered structures for deterministic ordering, queues for bounded sequential processing, trees for genuine hierarchy, graphs only where the approved semantic model requires traversal, and streaming/iterators for large artifacts where demonstrated necessary.

Do not introduce specialized algorithms merely because they are sophisticated.

## 5. LLD — Low-Level Design

Each substantive component should have clear:

- responsibility;
- inputs and outputs;
- invariants;
- dependencies;
- error behavior;
- lifecycle behavior;
- test seam.

Apply SOLID pragmatically:

- **Single Responsibility:** one coherent reason to change.
- **Open/Closed:** introduce extension points only for approved or demonstrated variation.
- **Liskov Substitution:** implementations preserve the approved behavioral contract.
- **Interface Segregation:** prefer focused interfaces.
- **Dependency Inversion:** depend on stable abstractions where replaceability is required.

Use patterns only for real design problems. Appropriate examples include Strategy, Adapter, Factory, Repository, Specification, and Decorator. A pattern is not itself a requirement.

## 6. DDD — Domain-Driven Design

Use DDD to preserve ECRA semantic boundaries and make behavior explicit.

Apply, where justified:

- ubiquitous language from approved ECRA terminology;
- bounded contexts;
- entities for independently identifiable concepts;
- value objects for descriptive immutable values;
- aggregates for actual consistency boundaries;
- domain services for behavior not naturally owned by an entity/value object;
- repositories at appropriate persistence boundaries;
- domain events only when an approved or demonstrated use case requires them.

Do not introduce new ECRA root concepts through implementation convenience.

A domain class, DTO, database table, or UI model does not automatically establish a new ECRA semantic type.

## 7. Clean / Hexagonal Architecture

Where compatible with the approved architecture, protect core semantics from infrastructure concerns.

A typical logical dependency direction is:

    Presentation / External Interfaces
                  ↓
    Application / Use Cases
                  ↓
    Domain / Semantic Model
                  ↓
    Ports / Stable Contracts
                  ↓
    Infrastructure Adapters

The exact module/package structure remains governed by approved architecture and implementation documentation.

Infrastructure should be replaceable without redefining ECRA semantics. Examples include persistence, source/artifact, external-service, serialization, UI, and API adapters.

Do not force every component into a framework merely to satisfy a theoretical pattern.

## 8. HLD — High-Level Design

For each slice, consider:

- component responsibilities;
- dependency direction;
- data flow;
- state ownership;
- consistency requirements;
- failure boundaries;
- security boundaries;
- persistence boundaries;
- external dependency boundaries;
- scalability characteristics;
- observability;
- deployment implications.

HLD should answer: What owns this behavior? What does it depend on? What crosses a boundary? What happens when a dependency fails? What state must be durable? What must remain reproducible? What can evolve independently?

Do not introduce distributed architecture merely because it could theoretically support future scale.

## 9. Microservices and Distributed-System Patterns

Microservices patterns are engineering tools, not a Gen1 deployment requirement.

Use principles selectively to preserve future evolvability:

- cohesive boundaries;
- explicit contracts;
- dependency inversion;
- isolated external integrations;
- explicit failure handling;
- idempotency where repeated requests are possible;
- correlation/context propagation;
- clear persistent-state ownership.

Potential patterns include timeout, bounded retry/backoff, circuit breaker, bulkhead, idempotency key, outbox/inbox, saga, and asynchronous messaging.

Introduce them only when the selected slice has the corresponding problem.

Do not introduce Kafka, service meshes, distributed transactions, event sourcing, or microservice deployment solely to demonstrate architectural sophistication.

Target evolution:

    Cohesive Modular Implementation
              ↓
    Evidence of Boundary / Scale Need
              ↓
    Selected Module Separation
              ↓
    Distributed Service Where Justified

## 10. API and Contract Engineering

Where a slice requires an API or cross-component contract:

- define explicit inputs and outputs;
- validate inputs at the appropriate boundary;
- define error semantics;
- preserve stable identifiers;
- preserve provenance/version information where required;
- define idempotency where applicable;
- avoid leaking persistence structures;
- preserve approved compatibility requirements;
- test contract behavior independently of implementation details.

Contracts derive from approved semantics and requirements. Do not expose an internal method merely because it could be an API.

## 11. Persistence Engineering

Persistence is an implementation mechanism, not the source of ECRA semantics.

When required:

- model stable identity explicitly;
- preserve version/lineage;
- preserve provenance and source locations;
- preserve relationships;
- preserve assessment state;
- preserve required historical state;
- define transaction/consistency boundaries;
- isolate storage-specific behavior;
- consider concurrency and failure behavior.

Do not define persistence contracts merely to suit a convenient storage engine.

Do not select storage because it is fashionable or because a data structure maps conveniently to it. Storage remains subordinate to approved semantic and behavioral requirements.

## 12. Serialization and Semantic Round-Trip

Where round-trip behavior applies:

    Logical Model
         ↓
    Machine Representation
         ↓
    Reconstructed Logical Model

Verify preservation of applicable:

- semantic identity;
- membership/reference;
- relationships;
- provenance;
- source locations;
- assessments;
- versions/lineage;
- limitations and relevant metadata.

Byte-for-byte equality is not required unless an approved contract explicitly requires it. Concrete serialization must not redefine semantic ownership.

## 13. Testing and Verification Engineering

Apply the approved testing strategy at appropriate levels:

- unit tests for local deterministic behavior;
- component tests for cohesive modules;
- contract tests for externally visible/cross-component contracts;
- integration tests for real component interactions;
- E2E tests for complete user-visible slice behavior.

Include normal, invalid, boundary, failure, partial-processing, version-change, provenance, conflict, authorization, and external-dependency cases where applicable.

Do not weaken tests to accommodate an incorrect implementation.

## 14. Security Engineering

Security is part of production quality. Apply where relevant:

- least privilege;
- authentication and authorization;
- input validation;
- safe output handling;
- secure secret handling;
- sensitive-data minimization;
- protected logging;
- integrity verification;
- provenance preservation;
- auditability;
- safe error handling;
- dependency/supply-chain review.

Treat untrusted documents, scripts, models, binaries, macros, and other artifacts as data unless controlled execution is explicitly authorized. Do not execute untrusted content merely to simplify processing.

## 15. Reliability and Failure Handling

For each external or failure-prone dependency, identify applicable:

- timeouts;
- retry limits and backoff;
- idempotency;
- partial-failure behavior;
- fallback/degradation;
- error propagation;
- resource limits;
- recovery behavior.

Do not hide failures by silently substituting data or results. Historical results must not be silently rewritten because a later dependency changed.

## 16. Observability and Operational Investigation

Material behavior should be diagnosable through appropriate:

- structured logs;
- metrics;
- traces;
- correlation identifiers;
- audit records;
- provenance records;
- health/readiness signals.

Respect security/privacy boundaries and avoid arbitrary telemetry.

Observability should help establish what happened, when, which operation caused it, which artifact/version was involved, which dependency was used, whether the result was complete, and how it can be reproduced.

Where applicable, observability reports and related operational artifacts may serve as authorized investigative inputs to **VS-F01 — Incident / Digital Forensic Investigation**. The VS-F01 reference application may therefore be used to investigate application or system issues using such evidence where the investigation falls within the approved VS-F01 workflow and applicable authorization boundaries.

This does not make VS-F01 a general-purpose observability platform, automatic root-cause engine, or autonomous incident-response system. The investigation must continue to distinguish observations, evidence, claims or hypotheses, assessments, uncertainty, provenance, and downstream decisions.

## 17. Performance Engineering

Performance work is evidence-driven:

1. identify workload;
2. identify metric;
3. establish baseline;
4. identify bottleneck;
5. select smallest appropriate optimization;
6. verify improvement;
7. verify correctness and maintainability.

Consider complexity, memory, I/O, serialization, database access, batching, caching, concurrency, and backpressure.

Do not add caches, indexes, asynchronous processing, or distributed computation without evidence.

## 18. Concurrency and State

When concurrency is required:

- identify shared mutable state;
- define ownership and invariants;
- choose appropriate synchronization;
- avoid unnecessary locks;
- prefer immutable data where practical;
- define ordering guarantees;
- test race-sensitive behavior;
- define idempotency where relevant.

Do not assume concurrency is required merely because future scale might require it.

## 19. Maintainability and Evolution

Prefer cohesive modules, stable interfaces, dependency inversion, explicit contracts, replaceable adapters, minimal infrastructure coupling, clear ownership, small changes, and compatible evolution where required.

A future capability remains deferred until promoted through the established capability lifecycle.

Do not build speculative extension points everywhere.

## 20. Slice-by-Slice Engineering Workflow

For every implementation slice:

    1. Source sufficiency
             ↓
    2. Requirement traceability
             ↓
    3. Semantic / DDD model
             ↓
    4. HLD boundary analysis
             ↓
    5. LLD design
             ↓
    6. DSA / complexity analysis
             ↓
    7. Contract design
             ↓
    8. Implementation
             ↓
    9. Unit / component tests
             ↓
    10. Contract / integration tests
             ↓
    11. E2E workflow
             ↓
    12. Security / observability review
             ↓
    13. Performance review where applicable
             ↓
    14. Traceability / verification evidence
             ↓
    15. Critical PR review

At every stage ask:

> Is this required by the slice, necessary to implement it correctly, or merely something that could be useful later?

Only the first two categories belong in the current implementation.

## 21. Code Review Checklist

### Specification
- Is every meaningful change traceable to an approved requirement, acceptance criterion, defect, or qualified enabling capability?
- Does implementation preserve approved semantics?
- Are material ambiguities identified?

### Architecture
- Are approved boundaries preserved?
- Are dependencies directed appropriately?
- Is hidden coupling avoided?
- Has deployment architecture changed without approval?

### LLD / DDD
- Are responsibilities cohesive?
- Are domain concepts aligned with approved terminology?
- Are entities/value objects/aggregates used appropriately?
- Are abstractions justified?
- Are infrastructure concerns isolated?

### DSA / Performance
- Are data structures appropriate?
- Is complexity acceptable?
- Are resource bounds understood?
- Is optimization evidence-based?

### Contracts
- Are interfaces and errors explicit?
- Is persistence hidden behind the appropriate boundary?
- Are semantic and serialization concerns separated?

### Security / Operations
- Are authorization and sensitive-data boundaries addressed?
- Is untrusted content handled safely?
- Is provenance preserved?
- Is behavior observable and reproducible?
- Can relevant observability artifacts be used as investigative evidence where the approved VS-F01 workflow permits?

### Testing
- Are appropriate test levels applied?
- Are negative and boundary cases covered?
- Is round-trip behavior verified where applicable?
- Are historical/versioning behaviors verified?

### Scope
- Is the change limited to the selected slice?
- Has speculative infrastructure been avoided?
- Has shared capability been promoted only with evidence?

## 22. Definition of Engineering Done

A slice implementation is engineering-complete only when:

1. requirements and acceptance criteria are traceable;
2. approved architecture/design are respected;
3. domain ownership remains correct;
4. responsibilities and dependencies are clear;
5. appropriate algorithms/data structures are used;
6. contracts are explicit and verified;
7. required persistence semantics are preserved;
8. normal, boundary, and failure behavior is tested;
9. security and untrusted-artifact handling are addressed;
10. material behavior is observable;
11. the E2E user workflow works;
12. semantic round-trip is verified where applicable;
13. no speculative capability is introduced;
14. verification evidence is recorded;
15. implementation is understandable and maintainable.

## 23. Relationship to Other Implementation Guidance

Read this together with:

- `docs/50-implementation/vertical-slice.md` — slice sequence and scope;
- `docs/50-implementation/testing-strategy.md` — testing and verification;
- `docs/00-project/ecra-p0-vs-f01-incident-digital-forensic-investigation.md` — approved VS-F01 investigation boundary.

If implementation guidance conflicts with approved requirements, architecture, ADRs, detailed design, contracts, or verification criteria, the higher-authority artifact takes precedence and the conflict must be recorded.

## 24. Status

This engineering-principles guide is **APPROVED** and governs Generation 1 slice implementation.
