# ECRA — Agent Instructions

## 1. Purpose

This repository contains the **ECRA Generation 1 reference implementation**.

These instructions define how AI coding agents and automated development assistants must operate within the repository.

The repository is intended to support implementation by:

- OpenAI Codex
- Claude Code
- other compatible AI coding agents
- human developers working manually or collaboratively with AI agents

The repository is designed to be **self-contained**. An implementation agent must not require access to previous ChatGPT conversations to understand or implement the project correctly.

---

## 2. Current Objective

The current objective is:

> Build a production-quality, tested, observable, maintainable **ECRA Generation 1 reference implementation** that conforms to the approved Gen1 requirements, architecture, design decisions, and implementation contracts.

Generation 1 is the current implementation boundary.

Do not expand the scope beyond Generation 1 unless an explicit approved change requires it.

---

## 3. Generation 1 Is Frozen

The Generation 1 architecture has been established and is considered frozen.

Agents must:

- implement the existing architecture;
- preserve established architectural boundaries;
- preserve approved interfaces and contracts;
- preserve approved domain semantics;
- follow approved architectural decisions;
- avoid introducing alternative architectures merely because they appear simpler or more modern.

Implementation convenience is not sufficient justification for architectural change.

### Architectural conflict rule

If an implementation discovers that an approved Gen1 requirement cannot be satisfied by the current architecture:

1. Stop the affected implementation work.
2. Identify the exact requirement.
3. Identify the architectural constraint causing the conflict.
4. Identify the relevant architecture/design/ADR documents.
5. Explain the conflict.
6. Do not silently redesign the architecture.
7. Do not encode a workaround that violates the specification merely to make the implementation compile.

An architectural change requires an explicit decision and must be recorded through the project's decision process.

---

## 4. Repository Is the Source of Truth

The canonical project specification is contained in this repository.

Chat conversations, personal notes, temporary discussions, generated suggestions, and historical project discussions are not normative unless their content has been deliberately incorporated into the repository.

When information conflicts, use the repository authority hierarchy defined below.

Do not reconstruct requirements from memory when the authoritative repository documents are available.

---

## 5. Document Authority Hierarchy

When resolving conflicts, use the following order of authority:

1. **Approved Gen1 requirements**
2. **Approved Gen1 architecture**
3. **Approved Architecture Decision Records (ADRs)**
4. **Approved detailed design specifications**
5. **Executable contracts, schemas, and test vectors**
6. **Verification and acceptance criteria**
7. **Existing implementation**
8. **Informational documentation**
9. **Historical material**
10. **Deferred/future material**

Higher-authority material takes precedence over lower-authority material.

Existing code does not override a normative requirement merely because the code already exists.

Tests are evidence of intended or required behavior, but tests must themselves remain consistent with the authoritative specification.

---

## 6. Required Reading Before Implementation

Before making a substantive implementation change, an agent must inspect the relevant repository context.

At minimum:

1. `README.md`
2. this `AGENTS.md`
3. the applicable project scope documents
4. relevant requirements
5. relevant architecture documents
6. applicable ADRs
7. relevant design documents
8. relevant contracts/schemas
9. existing implementation
10. existing tests

Do not make broad implementation changes based only on a single requirement or source file.

For a narrowly scoped change, read the smallest complete set of authoritative documents necessary to understand the affected behavior.

---

## 7. Repository Navigation

The repository is organized by responsibility.

```text
docs/
    00-project/        Project identity, scope, terminology, principles
    10-requirements/   Gen1 requirements
    20-architecture/   Gen1 architecture
    30-design/         Detailed design
    40-decisions/      Architecture and design decisions
    50-implementation/ Implementation guidance and execution state
    60-verification/   Verification and release criteria
    90-deferred/       Future work and explicitly deferred material

specs/
    contracts/         Machine-readable and precise contracts
    schemas/           Schemas
    examples/          Canonical examples
    test-vectors/      Verification inputs and expected results

src/                   Production implementation

tests/
    unit/              Unit tests
    component/         Component-level tests
    integration/       Integration tests
    contract/          Contract tests
    e2e/               End-to-end tests

deploy/                Deployment and runtime artifacts

scripts/               Development and operational scripts

.github/               CI/CD and GitHub project configuration
```

The exact source-language/package structure is defined by the approved implementation documentation and architecture. Do not invent an alternative source hierarchy without justification.

---

## 8. Requirements Before Code

Implementation must be requirement-driven.

Before implementing a capability, determine:

- which requirement(s) it satisfies;
- which architectural component owns it;
- which design specification governs it;
- which contracts apply;
- which failure behavior is required;
- which observability behavior is required;
- how it will be verified.

A useful implementation trace is:

```text
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
```

If a meaningful implementation change cannot be associated with an approved requirement, defect, or necessary implementation task, treat it as potentially out of scope.

---

## 9. Do Not Invent Requirements

Agents must not introduce behavior simply because it appears useful.

Do not independently invent:

- new APIs;
- new domain concepts;
- new persistence models;
- new configuration options;
- new extension points;
- new plugins;
- new integration mechanisms;
- new architectural layers;
- new infrastructure dependencies;
- new product features.

If behavior is genuinely unspecified and necessary to proceed, identify the ambiguity and request or record a decision rather than silently choosing behavior that could become de facto architecture.

Reasonable local implementation choices are allowed when they do not alter an approved contract, architectural boundary, or externally observable requirement.

---

## 10. Scope Control

Generation 1 has a deliberately bounded scope.

Work belongs to one of these categories:

```text
GEN1-IMPLEMENT
GEN1-FIX
FUTURE
```

### GEN1-IMPLEMENT

Required work needed to implement the approved Generation 1 system.

### GEN1-FIX

Defects that prevent the implementation from conforming to Gen1 requirements, architecture, design, contracts, or production-quality criteria.

### FUTURE

Useful ideas that are not required for Gen1.

Future work must not be pulled into the current implementation merely because it appears beneficial.

Material that belongs to future generations or later initiatives should remain under:

```text
docs/90-deferred/
```

unless explicitly promoted into Gen1.

---

## 11. Vertical Slice First

The implementation begins with the approved Gen1 vertical slice.

The vertical slice must demonstrate the real architectural execution path rather than a disconnected prototype.

The implementation sequence should generally be:

```text
Foundation
    ↓
Domain / Contracts
    ↓
Application behavior
    ↓
Runtime execution
    ↓
Persistence / required infrastructure
    ↓
Observability
    ↓
API / integration boundary
    ↓
End-to-end verification
```

The exact sequence is governed by:

```text
docs/50-implementation/vertical-slice.md
```

Do not replace the approved vertical slice with a simplified architecture solely to obtain an earlier demo.

---

## 12. Implementation Quality

Production code must prioritize:

1. correctness;
2. specification conformance;
3. explicit behavior;
4. maintainability;
5. testability;
6. deterministic behavior;
7. observability;
8. operational safety;
9. appropriate performance;
10. simplicity.

Avoid unnecessary abstraction.

Do not introduce abstractions merely because they might be useful in a hypothetical future version.

Prefer a small, explicit implementation over a generalized framework when both satisfy the approved design.

---

## 13. Architectural Boundaries

Respect the responsibilities and dependencies defined by the architecture.

Do not:

- bypass domain boundaries;
- introduce hidden dependencies;
- couple unrelated components;
- leak infrastructure concerns into domain logic without authorization;
- expose internal persistence structures as public contracts;
- bypass application/runtime orchestration;
- duplicate business rules in multiple architectural layers.

If an architectural boundary appears inconvenient, verify the architecture and design documents before changing the implementation.

---

## 14. Contracts Are Deliberate

Public and cross-component contracts must be treated as stable design artifacts.

Do not casually change:

- API structures;
- request/response models;
- error contracts;
- domain contracts;
- persistence contracts;
- serialization formats;
- event/message contracts;
- configuration contracts.

If a contract change is genuinely required, determine whether it is:

- an implementation defect;
- a missing requirement;
- a design clarification;
- an architectural decision.

Do not silently change a contract to make an implementation easier.

---

## 15. Error Handling

Failure behavior is part of the system contract.

For each meaningful failure path, consider:

- validation failure;
- domain failure;
- application failure;
- infrastructure failure;
- persistence failure;
- configuration failure;
- external dependency failure;
- unexpected failure.

Errors must be:

- deterministic where possible;
- appropriately classified;
- observable;
- testable;
- propagated according to the approved error model.

Do not hide failures merely to make a test or execution path succeed.

Do not expose internal implementation details through public error contracts unless explicitly required.

---

## 16. Observability

Observability is part of the implementation, not an optional post-processing step.

Where required by the architecture and observability specification, implementation must provide appropriate:

- metrics;
- structured logs;
- correlation/context information;
- health information;
- diagnostic information;
- tracing signals.

Do not add arbitrary telemetry that creates unnecessary operational complexity.

Follow the canonical observability design.

---

## 17. Testing Requirements

Production behavior must be accompanied by appropriate tests.

Use the test layers defined by:

```text
docs/50-implementation/testing-strategy.md
```

and:

```text
docs/60-verification/
```

Tests should cover, as applicable:

- normal behavior;
- boundary conditions;
- invalid input;
- failure paths;
- state transitions;
- contract behavior;
- integration behavior;
- persistence behavior;
- observability behavior;
- end-to-end behavior.

Do not weaken production behavior merely to simplify tests.

Do not delete or weaken a test to make an implementation pass unless the test itself is demonstrably incorrect according to the authoritative specification.

---

## 18. Test Evidence

A requirement is not considered implemented merely because the code exists.

For significant behavior, the implementation should eventually provide traceability:

```text
Requirement ID
    ↓
Implementation component
    ↓
Test
    ↓
Verification result
```

Use:

```text
docs/10-requirements/requirements-traceability.md
```

for the canonical traceability model.

---

## 19. Dependencies

Prefer existing project dependencies and platform capabilities when they satisfy the approved design.

Do not introduce a dependency merely because:

- it is popular;
- an AI-generated solution commonly uses it;
- it makes a small implementation shorter;
- it is fashionable;
- it may be useful in a future version.

Before adding a dependency, consider:

- architectural fit;
- licensing;
- security;
- maintenance;
- operational impact;
- transitive dependencies;
- testability;
- whether the dependency is actually required.

---

## 20. Configuration

Configuration must follow the approved configuration model.

Do not introduce undocumented configuration switches.

Configuration should be:

- explicit;
- validated;
- observable where appropriate;
- safely defaulted where defaults are permitted;
- documented.

Do not use environment variables or configuration values as hidden mechanisms for changing architectural behavior.

---

## 21. Security

Security requirements are mandatory requirements, not optional hardening work.

Follow:

```text
docs/20-architecture/security.md
```

and the relevant requirements/design documents.

Do not:

- disable security controls merely to simplify development;
- commit credentials or secrets;
- add insecure defaults;
- bypass authentication/authorization where required;
- log sensitive information;
- introduce unsafe diagnostic behavior.

Development-only shortcuts must never silently become production defaults.

---

## 22. Changes Must Be Narrowly Scoped

When implementing a task:

- change only what is necessary;
- avoid unrelated refactoring;
- avoid opportunistic architecture changes;
- avoid mass formatting changes;
- avoid renaming unrelated components;
- avoid introducing speculative infrastructure.

A small task should produce a small, understandable change.

If implementation reveals unrelated technical debt, record it separately rather than expanding the current task unless it blocks correctness.

---

## 23. Preserve Existing Correct Behavior

Before modifying existing code:

1. understand why it exists;
2. identify the requirement or design governing it;
3. inspect relevant tests;
4. determine whether it is correct;
5. change it only when the specification or defect requires the change.

Do not rewrite working code simply to match an agent's preferred style.

---

## 24. Build and Test Before Completion

A substantive implementation change is not complete until the applicable:

- build;
- static checks;
- unit tests;
- component tests;
- integration tests;
- contract tests;
- end-to-end tests

have been executed, or a documented reason explains why a particular verification step cannot yet run.

Report failures accurately.

Never claim that an implementation is verified when the relevant verification has not actually been performed.

---

## 25. Repository Hygiene

Do not commit:

- generated temporary files;
- credentials;
- local environment files containing secrets;
- IDE-specific artifacts unless intentionally tracked;
- build output;
- debug dumps;
- temporary experiments;
- abandoned prototypes.

Generated artifacts should be committed only when explicitly required by the repository design.

---

## 26. Documentation Changes

When implementation changes a documented behavior, update the relevant documentation when the change is authoritative and approved.

Do not modify normative architecture or requirements merely to make them match an implementation that was incorrectly written.

The preferred sequence is:

```text
Specification
    ↓
Implementation
    ↓
Verification
    ↓
Documentation alignment
```

If the specification itself is wrong or incomplete, stop and handle that as a specification/design decision rather than silently rewriting it.

---

## 27. Architecture Change Protocol

An architecture change is exceptional during Gen1 implementation.

Before proposing one, establish:

1. The exact Gen1 requirement involved.
2. Why the existing architecture cannot satisfy it.
3. Why the issue cannot be resolved within the current design.
4. What alternatives were considered.
5. The smallest architectural change that would resolve the issue.
6. The consequences for existing implementation and tests.
7. The affected documents.

Do not implement the architectural change until it has been explicitly approved and recorded in the appropriate ADR/design documents.

---

## 28. Deferred Work

Future ideas must not silently enter the Gen1 implementation.

Use:

```text
docs/90-deferred/
```

for:

- future generations;
- speculative improvements;
- optional integrations;
- broader ecosystem capabilities;
- long-term product ideas;
- architectural extensions not required by Gen1.

A future idea may be recorded without being implemented.

---

## 29. Completion Criteria

A capability is considered complete only when it satisfies the applicable Definition of Done.

At minimum:

- required behavior is implemented;
- contracts are correct;
- failure behavior is implemented;
- tests are present and passing;
- integration behavior is verified where applicable;
- observability requirements are satisfied;
- security requirements are satisfied;
- documentation is aligned;
- no known Gen1 specification violation remains.

The authoritative completion criteria are defined under:

```text
docs/60-verification/
```

---

## 30. When to Stop

An agent must stop and request clarification or a project decision when:

- requirements conflict;
- architecture conflicts with requirements;
- two normative documents conflict;
- required behavior is genuinely unspecified;
- an implementation requires an architectural change;
- a security-sensitive decision is ambiguous;
- a public contract requires an unapproved change;
- the requested work appears outside Gen1 scope.

Do not resolve material ambiguity by guessing.

A clearly documented, local implementation choice is acceptable only when it does not materially affect requirements, architecture, contracts, or externally observable behavior.

---

## 31. Preferred Implementation Workflow

For a normal implementation task:

```text
1. Identify the task.
2. Identify the applicable requirement.
3. Read the relevant architecture.
4. Read applicable ADRs.
5. Read the relevant design.
6. Inspect the existing implementation.
7. Inspect relevant tests.
8. Identify the smallest implementation change.
9. Implement it.
10. Add/update tests.
11. Run applicable verification.
12. Review the change against the specification.
13. Update implementation status.
14. Report what changed and what was verified.
```

Do not skip directly from task description to code.

---

## 32. Agent Output Expectations

When completing implementation work, report:

### Implemented

What was changed.

### Specification

Which requirements/design/architecture documents govern the change.

### Tests

Which tests were added or modified.

### Verification

Which build/test/verification commands were executed and their results.

### Remaining

Any unresolved issue, limitation, or blocked work.

### Scope

Explicitly identify anything discovered that belongs outside the current task or Gen1.

---

## 33. Final Principle

The objective is not to produce the largest or most sophisticated implementation.

The objective is to produce the **smallest complete, correct, production-quality implementation that faithfully realizes the approved ECRA Generation 1 architecture and requirements**.

When in doubt:

> Prefer the specification over assumption, explicit behavior over hidden behavior, evidence over claims, and bounded implementation over speculative expansion.
