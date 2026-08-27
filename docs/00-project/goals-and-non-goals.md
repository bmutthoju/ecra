# ECRA — Goals and Non-Goals

> Status: IN REVIEW
> Authority: NORMATIVE
> Generation: GEN1

## 1. Purpose

This document defines the scope boundary for the ECRA Generation 1 reference
implementation.

It establishes what Generation 1 is intended to accomplish and, equally
importantly, what it is explicitly not intended to accomplish.

The purpose is to provide a stable scope boundary for architecture,
implementation, verification, and AI-assisted development.

A capability that is not required by an approved Gen1 requirement and is not
necessary to implement an approved Gen1 requirement must not be added to
Generation 1 merely because it appears useful or desirable.

---

## 2. Generation 1 Objective

The primary objective of Generation 1 is:

> Build a production-quality reference implementation that demonstrates the
> approved ECRA architecture and provides a reliable, traceable, and
> verifiable mechanism for evaluating claims against evidence, sources, and
> relevant context.

Generation 1 must establish a complete vertical path through the approved
architecture rather than a collection of isolated components or a conceptual
prototype.

The implementation must be sufficiently complete to demonstrate that the
approved requirements and architecture can operate together as a coherent
system.

---

## 3. Goals

### 3.1 Claim Evaluation

Generation 1 shall provide the foundation required to evaluate claims against
associated evidence.

The system must be capable of representing and evaluating the relationship
between a claim and evidence that may:

- support the claim;
- contradict the claim;
- qualify the claim; or
- fail to establish the claim.

The evaluation must produce a structured result according to the approved
Gen1 requirements and design.

---

### 3.2 Evidence Integrity

Generation 1 shall treat evidence as an explicit and inspectable part of the
evaluation process.

The implementation shall provide the mechanisms required by the Gen1
specification to determine whether evidence actually establishes the
proposition for which it is presented.

The system must not equate the existence of a citation with evidentiary
support.

---

### 3.3 Source Authenticity and Authority

Generation 1 shall account for the authenticity and authority of sources
where required by the applicable requirements and design.

The implementation must distinguish, where applicable, between:

- the existence of a source;
- the authenticity of the source;
- the authority or suitability of the source for the claim; and
- what the source actually establishes.

An authentic source must not automatically be treated as evidence supporting a
claim.

---

### 3.4 Contextual Integrity

Generation 1 shall preserve and evaluate relevant context required to
determine whether evidence has been represented faithfully.

The implementation must support the Gen1 requirements concerning situations
such as:

- omitted material context;
- selective quotation;
- misleading presentation;
- interpretation beyond what the source establishes;
- combining evidence in a way that yields an unsupported conclusion.

Detailed rules for determining contextual adequacy belong to the requirements
and design specifications.

---

### 3.5 Provenance and Traceability

Generation 1 shall maintain sufficient provenance to trace an evaluation back
to the claim, evidence, and relevant source information.

A result should make it possible to determine:

- what was evaluated;
- what evidence was considered;
- where the evidence originated;
- what source information was associated with it; and
- how the result relates to the available evidence and context.

Traceability is a core Gen1 capability rather than an optional diagnostic
feature.

---

### 3.6 Explicit and Deterministic Behavior

Generation 1 shall provide explicit, deterministic, and testable behavior
where required by the approved architecture and design.

The system should not depend on undocumented behavior or application-specific
conventions to produce a valid evaluation.

Important behavior must be represented through explicit contracts, models, and
verification.

---

### 3.7 Production-Quality Reference Implementation

Generation 1 shall be implemented as a production-quality reference
implementation.

This includes, as required by the approved specifications:

- clear architectural boundaries;
- explicit contracts;
- appropriate validation;
- appropriate error handling;
- persistence and state management where required;
- observability;
- security controls;
- automated testing;
- integration verification;
- reproducible execution.

"Reference implementation" does not mean "toy implementation" or "proof of
concept."

---

### 3.8 AI-Assisted Implementability

The Gen1 repository shall contain sufficient approved requirements,
architecture, design, contracts, and verification information for competent
developers and AI coding agents to implement the system without relying on
historical conversations.

Codex, Claude, and human developers should be able to derive implementation
work from the repository specification.

---

### 3.9 Verifiable Results

Generation 1 shall make evaluation behavior and results sufficiently explicit
to support automated verification.

The implementation must allow the correctness of important behavior to be
demonstrated through appropriate tests and verification evidence.

Claims about correctness must be supported by executable verification wherever
practical.

---

## 4. Non-Goals

The following are explicitly outside the Generation 1 scope unless a later
approved requirement explicitly promotes them into Gen1.

### 4.1 General-Purpose Fact-Checking Platform

Generation 1 is not intended to implement every capability associated with a
general-purpose fact-checking platform.

Only capabilities required by the approved Gen1 specification are in scope.

---

### 4.2 Autonomous General Intelligence

ECRA Gen1 is not intended to determine truth through unrestricted autonomous
reasoning or general intelligence.

It provides a defined evaluation system governed by explicit requirements,
contracts, evidence, sources, context, and verification.

---

### 4.3 Replacement for Human Judgment

Generation 1 is not intended to eliminate the need for human judgment in
situations where human judgment is necessary.

However, human judgment should itself be evidence-based, transparent, and
traceable wherever practical.

ECRA should, where applicable, support decision processes in which the
evidence considered, relevant sources and context, evaluation basis, and
resulting judgment can be understood by others.

The exact mechanisms by which human judgments are captured, represented, or
audited are defined by the approved Gen1 requirements and design.

This transparency is important not only for establishing confidence in a
decision, but also for identifying, reviewing, and learning from human errors
when they occur.

ECRA therefore does not treat human judgment as inherently correct or
inherently superior to automated evaluation. Human judgments remain subject to
the same need for evidence, appropriate context, sound reasoning, and
traceability.

---

### 4.4 Unrestricted Web or Information Crawling

Generation 1 is not a general-purpose web crawler, search engine, or
unrestricted information acquisition platform.

Only source acquisition and integrations explicitly required by the Gen1
architecture and requirements are in scope.

---

### 4.5 Universal Source Authority Registry

Generation 1 is not intended to establish a universal authority ranking or
intrinsic authority score for all sources, publishers, institutions, or
information domains.

Where source authority is relevant, ECRA should represent factual,
provenance-aware information about the source and the basis on which its
authority or suitability is asserted.

For example, if a source is identified or declared as authoritative, the
system should, where such information is available, make it possible to
identify:

- who or what recognizes the source as authoritative;
- the context or domain in which that recognition applies;
- the criteria, standard, policy, or other basis for the recognition;
- when the recognition was established or is applicable; and
- the relevant supporting evidence or reference.

ECRA should present such information transparently rather than treating
authority as an unexplained property of the source.

Authority is therefore contextual and attributable rather than an inherent
property assigned universally by ECRA.

An authority claim represented by ECRA is itself information to be evaluated
or reported according to the applicable Gen1 requirements; it is not
automatically accepted as true merely because it has an identified
attribution.

---

### 4.6 Domain-Specific Truth Systems

Generation 1 is not intended to encode comprehensive truth models for every
domain such as:

- religion;
- medicine;
- law;
- politics;
- science;
- history;
- finance; or
- other specialized domains.

ECRA provides a general evaluation foundation. Domain-specific rules belong
in explicit specifications or future extensions where applicable.

---

### 4.7 Content Generation

Generating persuasive articles, social-media posts, summaries, opinions, or
other content is not itself a Gen1 objective.

ECRA may evaluate information supplied by another system, but content
generation is not a core Gen1 responsibility unless explicitly specified.

---

### 4.8 Replacing or Concealing Source Material

Generation 1 is not intended to replace authoritative source material with an
AI-generated interpretation in a way that obscures the underlying source or
prevents users from independently examining the evidence.

ECRA may generate, present, or annotate AI-generated interpretations where
such behavior is required by the approved Gen1 specification.

When an AI-generated interpretation is presented, it should be accompanied
by relevant and sufficient provenance and contextual information to allow users
to understand:

- that the interpretation was generated or transformed by an AI system;
- which evidence and source material the interpretation is based on;
- which model or AI system produced the interpretation, where applicable;
- the relevant model or system version, where available;
- the evaluation or processing context, where relevant; and
- the relationship between the interpretation and the underlying evidence.

AI-generated interpretation must not be presented as though it were the
original source material or as an independently established fact when it is
actually an interpretation derived from evidence.

The underlying source material and relevant evidence should remain
identifiable and traceable so that users can independently examine the basis
for the interpretation.

---

### 4.9 Speculative AI Capabilities

Generation 1 does not include speculative AI capabilities merely because they
could improve future versions of ECRA.

Examples include:

- autonomous agent ecosystems;
- unrestricted multi-agent reasoning;
- self-modifying evaluation logic;
- autonomous policy creation;
- speculative model orchestration;
- capabilities not required by the approved Gen1 architecture.

---

### 4.10 Ecosystem Expansion

Generation 1 is not intended to implement a complete ecosystem around ECRA.

Future integrations, plugins, external platforms, developer ecosystems, and
broader adoption mechanisms are deferred unless explicitly required by Gen1.

---

### 4.11 Generation 2 and Future Architecture

Generation 2 capabilities and architectural extensions are outside the
Generation 1 implementation boundary.

Future ideas may be documented under:

    docs/90-deferred/

but must not influence Gen1 implementation unless formally promoted.

---

## 5. Scope-Control Rules

The following rules apply throughout Generation 1 implementation.

### Rule 1 — Requirements Define Scope

A capability is in Gen1 scope only when supported by an approved Gen1
requirement or is necessary to implement such a requirement.

---

### Rule 2 — Architecture Does Not Expand Scope

The existence of an architectural extension point does not imply that every
possible capability using that extension point belongs to Gen1.

---

### Rule 3 — Implementation Convenience Does Not Expand Scope

A developer or AI agent must not add capabilities merely because they are
easy to implement or naturally fit an existing abstraction.

---

### Rule 4 — Future Value Does Not Establish Gen1 Scope

A capability may be valuable without being a Gen1 requirement.

Useful future work should be recorded separately rather than implemented
speculatively.

---

### Rule 5 — Dependencies Do Not Become Features

A library, framework, integration, or infrastructure component required by
another Gen1 capability does not automatically make all of its capabilities
part of ECRA.

Only the required subset is in scope.

---

### Rule 6 — Reference Implementation Means Complete, Not Broad

Gen1 should be complete with respect to its approved scope.

Completeness must not be achieved by continuously expanding that scope.

---

## 6. Scope-Change Rule

During Generation 1 implementation, any proposal that materially expands
scope must identify:

1. the requirement motivating the change;
2. why the capability is necessary for Gen1;
3. the architectural impact;
4. the implementation impact;
5. the verification impact;
6. what existing work, if any, must change;
7. whether the capability should instead be deferred.

No material scope expansion should be implemented without explicit approval.

---

## 7. Relationship to Other Documents

This document establishes the project-level Gen1 scope boundary.

Detailed behavior is defined elsewhere:

- `docs/10-requirements/` defines what the system must do;
- `docs/20-architecture/` defines how the system is structured;
- `docs/30-design/` defines detailed solution behavior;
- `docs/40-decisions/` records approved architectural and design decisions;
- `docs/50-implementation/` defines implementation guidance;
- `docs/60-verification/` defines how conformance is established;
- `docs/90-deferred/` contains explicitly deferred work.

If a conflict exists, follow the repository's document authority hierarchy
defined in `AGENTS.md`.

---

## 8. Gen1 Completion Boundary

Generation 1 is complete when the approved Gen1 requirements have been
implemented, integrated, and verified according to the approved architecture,
design, and verification criteria.

Gen1 is not incomplete merely because additional useful capabilities remain
possible.

Future capability is expected.

Uncontrolled scope expansion is not.
