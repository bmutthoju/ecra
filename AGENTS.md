# ECRA — Agent Instructions

## 1. Purpose

This repository contains the **ECRA Generation 1 reference implementation**.

These instructions define the operating rules for AI coding agents, including:

- OpenAI Codex;
- Claude Code;
- other compatible AI coding agents;
- human developers working with AI assistance.

The repository is intended to be **self-contained**. An implementation agent must be able to understand and implement ECRA from the repository without depending on historical chat conversations.

This file provides the repository-level agent rules. Detailed requirements, architecture, design, implementation, and verification rules belong in the appropriate documents under `docs/`.

---

## 2. Current Project State

The repository is being bootstrapped from the established **ECRA Generation 1 specification baseline**.

The current work proceeds in two stages:

1. establish and approve the canonical Gen1 requirements, architecture, design, and implementation documentation in this repository;
2. implement and verify the Gen1 reference implementation.

Until the applicable Gen1 specification baseline has been established in the repository:

- do not invent missing requirements;
- do not invent architecture;
- do not begin substantive production implementation;
- do not use implementation convenience to resolve specification ambiguity;
- use only explicitly approved project material when resolving missing context.

Production implementation begins only when the relevant specification and design baseline is available in the repository.

---

## 3. Current Objective

The current objective is:

> Build a production-quality, tested, observable, maintainable **ECRA Generation 1 reference implementation** that conforms to the approved Gen1 requirements, architecture, design decisions, contracts, and verification criteria.

Generation 1 is the current implementation boundary.

Do not expand the scope beyond Gen1 unless an explicit approved change promotes additional work into the current scope.

---

## 4. Generation 1 Architecture Is Frozen

The approved Generation 1 architecture is frozen for implementation.

Agents must:

- implement the established architecture;
- preserve approved architectural boundaries;
- preserve approved interfaces and contracts;
- preserve approved domain semantics;
- follow approved architectural decisions;
- avoid introducing alternative architectures merely because they appear simpler, newer, or more convenient.

Implementation convenience is not sufficient justification for architectural change.

### Architectural conflict rule

If an implementation discovers that an approved Gen1 requirement cannot be satisfied by the current architecture:

1. stop the affected implementation work;
2. identify the exact requirement;
3. identify the architectural constraint causing the conflict;
4. identify the relevant architecture, design, and ADR documents;
5. explain the conflict;
6. identify possible alternatives if useful;
7. do not silently redesign the architecture;
8. do not introduce a workaround that violates the specification.

An architectural change requires an explicit decision and must be recorded through the project's decision process before implementation.

---

## 5. Repository Is the Source of Truth

The canonical project specification is contained in this repository.

The following are **not normative by themselves**:

- ChatGPT conversations;
- historical discussions;
- personal notes;
- temporary working notes;
- generated suggestions;
- comments in external systems;
- abandoned proposals.

Information becomes project authority only when deliberately incorporated into the appropriate repository artifact and given the appropriate status and authority.

Do not reconstruct requirements from memory when authoritative repository documents are available.

---

## 6. Normative Documents

Repository documents must clearly distinguish **authority** from **status**.

### Authority

Documents may be classified as:

```text
NORMATIVE
IMPLEMENTATION
INFORMATIONAL
HISTORICAL
DEFERRED
```

### Status

Documents may be classified as:

```text
DRAFT
REVIEW
APPROVED
SUPERSEDED
DEPRECATED
```

Only documents that are explicitly **APPROVED** and have the appropriate authority may govern implementation.

Draft, historical, informational, superseded, deprecated, and deferred material must not be treated as current Gen1 requirements.

The metadata convention for project documents is defined by the documentation structure under `docs/`.

---

## 7. Document Authority Hierarchy

When approved project artifacts conflict, use the following precedence:

1. approved Gen1 requirements;
2. approved Gen1 architecture;
3. approved Architecture Decision Records;
4. approved detailed design specifications;
5. approved executable contracts, schemas, and test vectors;
6. approved verification and acceptance criteria;
7. existing implementation;
8. informational documentation;
9. historical material;
10. deferred/future material.

Higher-authority material takes precedence over lower-authority material.

Existing code does not override an approved requirement merely because the code already exists.

Tests are evidence of required or intended behavior, but tests must themselves remain consistent with the authoritative specification.

---

## 8. Never Change the Specification to Make Code Pass

Agents must never modify a requirement, architecture document, ADR, contract, or approved design merely to make an implementation compile or a test pass.

If implementation conflicts with an approved specification:

1. investigate the implementation first;
2. determine whether the implementation is incorrect;
3. determine whether the specification is genuinely incomplete or incorrect;
4. if the specification is defective, stop and follow the applicable decision/change process.

The preferred behavior is:

```text
Specification
    ↓
Implementation
    ↓
Verification
```

not:

```text
Implementation
    ↓
Failure
    ↓
Change specification
    ↓
Pass
```

---

## 9. Required Reading Before Implementation

Before making a substantive implementation change, inspect the smallest complete set of repository context necessary to understand the change.

Depending on the task, this normally includes:

1. `README.md`;
2. `AGENTS.md`;
3. applicable project scope documents;
4. relevant requirements;
5. relevant architecture documents;
6. applicable ADRs;
7. relevant design documents;
8. relevant contracts or schemas;
9. existing implementation;
10. relevant tests;
11. applicable implementation and verification guidance.

Do not make broad implementation changes based only on a task description or a single source file.

---

## 10. Repository Navigation

The repository is organized by responsibility:

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
    contracts/         Precise and machine-readable contracts
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

.github/               GitHub and CI/CD configuration
```

The exact source-language and package/module structure is defined by the approved architecture and implementation documentation.

Do not invent an alternative source hierarchy without justification.

---

## 11. Requirements Before Code

Implementation must be requirement-driven.

Before implementing a meaningful capability, determine:

- which requirement it satisfies;
- which architectural component owns it;
- which design specification governs it;
- which contracts apply;
- what externally observable behavior is required;
- what failure behavior is required;
- what observability behavior is required;
- how the behavior will be verified.

The desired traceability is:

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

## 12. Do Not Invent Requirements

Agents must not introduce behavior simply because it appears useful.

Do not independently invent:

- APIs;
- domain concepts;
- persistence models;
- configuration options;
- extension points;
- plugins;
- integration mechanisms;
- architectural layers;
- infrastructure dependencies;
- product features.

When behavior is genuinely unspecified and materially affects implementation, identify the ambiguity and stop for clarification or an explicit project decision.

A local implementation choice is acceptable when it:

- does not change an approved contract;
- does not change an architectural boundary;
- does not change externally observable behavior;
- does not introduce a new requirement;
- does not create future architectural constraints.

---

## 13. Scope Control

Generation 1 work belongs to one of three categories:

```text
GEN1-IMPLEMENT
GEN1-FIX
FUTURE
```

### GEN1-IMPLEMENT

Work required to implement the approved Generation 1 system.

### GEN1-FIX

Defects preventing conformance to Gen1 requirements, architecture, design, contracts, or production-quality criteria.

### FUTURE

Useful work that is not required for Gen1.

Future work must not be pulled into the current implementation merely because it appears beneficial.

Future and explicitly deferred material belongs under:

```text
docs/90-deferred/
```

unless it is formally promoted into Gen1.

---

## 14. Vertical Slice First

Gen1 implementation begins with the approved vertical slice.

The vertical slice must exercise the actual Gen1 architecture rather than becoming a disconnected prototype or replacement architecture.

The implementation sequence is governed by:

```text
docs/50-implementation/vertical-slice.md
```

The general objective is:

```text
Foundation
    ↓
Domain / Contracts
    ↓
Application behavior
    ↓
Runtime execution
    ↓
Required persistence / infrastructure
    ↓
Observability
    ↓
API / integration boundary
    ↓
End-to-end verification
```

Do not replace the approved vertical slice with a simplified implementation merely to obtain an earlier demonstration.

---

## 15. Implementation Principles

Production implementation must prioritize:

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

Implement the **smallest complete change** that satisfies the approved requirements and design.

Avoid:

- speculative abstractions;
- unnecessary frameworks;
- premature optimization;
- unrelated refactoring;
- architectural generalization;
- infrastructure added for hypothetical future needs.

Prefer explicit, understandable implementation over unnecessary indirection.

---

## 16. Architectural Boundaries

Respect the responsibilities and dependencies defined by the approved architecture.

Do not:

- bypass domain boundaries;
- introduce hidden dependencies;
- couple unrelated components;
- leak infrastructure concerns into domain logic without authorization;
- expose internal persistence structures as public contracts;
- bypass application/runtime orchestration;
- duplicate business rules across architectural layers.

If an architectural boundary appears inconvenient, inspect the applicable architecture and design documents before changing the implementation.

---

## 17. Contracts Are Deliberate

Treat public and cross-component contracts as controlled design artifacts.

Do not casually change:

- APIs;
- request/response structures;
- error contracts;
- domain contracts;
- persistence contracts;
- serialization formats;
- event/message contracts;
- configuration contracts.

Before changing a contract, determine whether the change represents:

- an implementation defect;
- a missing requirement;
- a design clarification;
- an approved architectural decision.

Do not change contracts merely to make implementation easier.

---

## 18. Local Implementation Decisions vs Material Decisions

Agents may make local implementation decisions when they do not materially affect the system contract.

Agents must stop and request a decision when a change affects:

- domain semantics;
- public APIs;
- persistence semantics;
- architectural boundaries;
- security behavior;
- lifecycle semantics;
- externally observable behavior;
- cross-component contracts;
- required infrastructure;
- major operational behavior.

When uncertain whether a decision is material, treat it as material.

---

## 19. Testing and Verification

Production behavior must be supported by appropriate automated verification.

Follow:

```text
docs/50-implementation/testing-strategy.md
```

and:

```text
docs/60-verification/
```

A meaningful capability is not considered implemented merely because source code exists.

The applicable verification should establish, as appropriate:

- normal behavior;
- boundary behavior;
- invalid input;
- failure behavior;
- state transitions;
- contract behavior;
- integration behavior;
- persistence behavior;
- observability behavior;
- end-to-end behavior.

Do not weaken production behavior merely to simplify tests.

Do not delete or weaken a valid test merely to make an implementation pass.

---

## 20. Observability, Security, and Configuration

Observability, security, and configuration are implementation concerns governed by the approved architecture and design.

Follow the applicable documents under:

```text
docs/20-architecture/
docs/30-design/
docs/50-implementation/
```

Do not:

- add undocumented configuration;
- introduce hidden runtime switches;
- disable required security controls for convenience;
- commit credentials or secrets;
- log sensitive information;
- add arbitrary telemetry;
- introduce operational dependencies without justification.

Detailed rules belong in the applicable architecture and implementation documents rather than being duplicated here.

---

## 21. Dependencies

Prefer existing project dependencies and platform capabilities when they satisfy the approved design.

Do not add a dependency merely because:

- it is popular;
- an AI-generated solution commonly uses it;
- it makes a small implementation shorter;
- it is fashionable;
- it might be useful in a future generation.

Before adding a dependency, consider:

- architectural fit;
- licensing;
- security;
- maintenance;
- operational impact;
- transitive dependencies;
- testability;
- whether it is actually required.

---

## 22. Changes Must Be Narrowly Scoped

When implementing a task:

- change only what is necessary;
- avoid unrelated refactoring;
- avoid opportunistic architecture changes;
- avoid mass formatting changes;
- avoid unrelated renaming;
- avoid speculative infrastructure.

A small task should produce a small, understandable change.

If unrelated technical debt is discovered, record it separately unless it blocks correctness or verification of the current task.

---

## 23. Preserve Existing Correct Behavior

Before modifying existing implementation:

1. understand why it exists;
2. identify the requirement or design governing it;
3. inspect relevant tests;
4. determine whether it is correct;
5. change it only when the specification or a verified defect requires the change.

Do not rewrite working implementation merely to match an agent's preferred style.

---

## 24. Architecture Change Protocol

Architecture changes are exceptional during Gen1 implementation.

Before proposing an architecture change, establish:

1. the exact Gen1 requirement involved;
2. why the current architecture cannot satisfy it;
3. why the problem cannot be solved within the current design;
4. alternatives considered;
5. the smallest viable architectural change;
6. consequences for implementation and tests;
7. affected documents.

Do not implement an architectural change until it has been explicitly approved and recorded through the appropriate ADR/design process.

---

## 25. Documentation Changes

Normative requirements, architecture, contracts, and approved design must not be changed merely to match an incorrect implementation.

When implementation exposes a genuine specification problem:

1. identify the problem;
2. stop the affected implementation;
3. follow the applicable decision/change process;
4. update the authoritative documentation only after approval;
5. update implementation and verification accordingly.

Implementation guidance may evolve without changing architecture or requirements, provided the change remains consistent with the authoritative specification.

---

## 26. Agent Instruction Hierarchy

Instruction sources have the following relationship:

```text
Repository requirements / architecture / approved design
                    ↓
             AGENTS.md
                    ↓
       Agent-specific instructions
                    ↓
       Task-specific implementation
```

Agent-specific instructions may refine operational workflow but must not override:

- approved requirements;
- approved architecture;
- approved contracts;
- approved ADRs;
- approved security constraints;
- approved verification criteria.

`AGENTS.md` is itself a repository control document.

Agents must not modify `AGENTS.md` as part of ordinary implementation work.

Changes to `AGENTS.md` must be intentional, narrowly scoped, and reviewed because they alter the operating rules for future agents.

---

## 27. Repository Hygiene

Do not commit:

- credentials or secrets;
- local environment files containing secrets;
- build output;
- temporary files;
- debug dumps;
- abandoned prototypes;
- IDE-specific artifacts unless intentionally tracked;
- generated artifacts unless explicitly required.

Keep implementation branches and commits focused on the task being performed.

---

## 28. Build and Verification Before Completion

A substantive implementation change is not complete until the applicable verification has been executed.

Depending on the change, this may include:

- formatting;
- static analysis;
- compilation/build;
- unit tests;
- component tests;
- integration tests;
- contract tests;
- end-to-end tests.

If a verification step cannot yet be executed, document why.

Never claim verification that was not actually performed.

---

## 29. When to Stop

An agent must stop and request clarification or a project decision when:

- requirements conflict;
- architecture conflicts with requirements;
- two approved normative documents conflict;
- required behavior is materially unspecified;
- implementation requires an architectural change;
- a security-sensitive decision is ambiguous;
- a public contract requires an unapproved change;
- the requested work appears outside Gen1 scope;
- a local implementation decision would create significant future constraints.

Do not resolve material ambiguity by guessing.

---

## 30. Preferred Implementation Workflow

For a normal implementation task:

```text
1. Identify the task.
2. Identify the applicable requirement.
3. Read the relevant architecture.
4. Read applicable ADRs.
5. Read the relevant design.
6. Inspect the existing implementation.
7. Inspect relevant tests.
8. Identify the smallest complete implementation change.
9. Implement it.
10. Add or update tests.
11. Run applicable verification.
12. Review the implementation against the specification.
13. Update implementation status where applicable.
14. Report implementation, verification, and remaining work.
```

Do not skip directly from a task description to code.

---

## 31. Agent Output Expectations

When completing implementation work, report:

### Implemented

What changed.

### Specification

Which requirements, architecture, design documents, contracts, or ADRs govern the change.

### Tests

Which tests were added or modified.

### Verification

Which build, test, and verification commands were executed and their results.

### Remaining

Any unresolved issue, limitation, or blocked work.

### Scope

Any discovered work that belongs outside the current task or Gen1.

---

## 32. Final Principle

The objective is not to produce the largest, most sophisticated, or most generalized implementation.

The objective is to produce the:

> **smallest complete, correct, production-quality implementation that faithfully realizes the approved ECRA Generation 1 requirements and architecture.**

When in doubt:

> **Prefer the specification over assumption, approved design over convenience, explicit behavior over hidden behavior, evidence over claims, and bounded implementation over speculative expansion.**
