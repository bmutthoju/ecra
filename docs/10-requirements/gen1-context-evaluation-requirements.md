# ECRA Generation 1 — Context and Evaluation Requirements

> Status: DRAFT
> Authority: IMPLEMENTATION
> Generation: GEN1
> Scope: Context and evaluation requirements

## 1. Purpose

This document defines the second set of ECRA Generation 1 product requirements for the Context and Evaluation portion of the approved evaluation path.

It establishes requirements for representing evaluation context, applying context to evaluation, performing evaluation, producing evaluation results, preserving evaluation explainability and reproducibility, and maintaining the boundary between evaluation and downstream decisions.

It builds on the Claim and Evidence requirements established by `gen1-claim-evidence-requirements.md` and does not redefine those requirements.

Concrete real-life examples and usage scenarios are intentionally kept outside this normative requirements document. They should be provided by a separate informative examples/scenarios document when needed.

## 2. Authority and Scope

The [approved Gen1 project vision](../00-project/vision.md) and [approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md) establish the product scope and objectives. The [approved Gen1 terminology](../00-project/terminology.md) establishes canonical product-domain terminology.

ECRA-1000 provides the architectural foundation; ECRA-1100 provides the requirements and traceability framework; and the applicable approved Shared Semantic Foundation governs genuinely portfolio-wide semantic concepts. These authorities MUST be used rather than redefined locally.

This document operationalizes those authorities for Gen1. It MUST NOT redefine their domain semantics.

The requirements in this document are product/system requirements. ECRA-1100 remains the authority for how these requirements are identified, versioned, traced, baselined, and verified.

The repository follows a document hierarchy in which higher-level documents establish scope, terminology, and governing constraints, while lower-level documents elaborate them. Detailed references should point to the applicable higher-level authority rather than duplicating or redefining it.

## 3. Relationship to Claim and Evidence Requirements

The requirements in `gen1-claim-evidence-requirements.md` establish the objects and trust properties that form the inputs to the evaluation path. This document establishes what Gen1 MUST do with those inputs when performing contextualized evaluation.

The evaluation requirements assume that applicable claim, evidence, source, acquired artifact, integrity, authenticity, authority, and provenance information is available according to the preceding requirements. They do not repeat those obligations.

## 4. Context Requirements

### ECRA-G1-FUN-0007 — Evaluation context representation

The system MUST represent the contextual information required to interpret and evaluate a claim and its supporting evidence for a particular evaluation.

**Rationale:** The meaning and applicability of evidence can depend on environmental, temporal, organizational, policy, and operational circumstances.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md); ECRA-1000 evidence-context and contextual evaluation semantics.

**Verification criteria:** Demonstrate that an evaluation can be associated with an explicit context containing the information required by the applicable evaluation semantics.

**Verification method:** Contract and integration verification.

### ECRA-G1-SEM-0004 — Context identity and version

Each persisted evaluation context MUST have a stable identity and MUST preserve the applicable version or lineage information needed to distinguish materially different contextual states.

**Rationale:** Evaluation results must remain interpretable against the context under which they were produced.

**Source basis:** Applicable shared semantic identity/version foundation; ECRA-1000 context and lifecycle semantics.

**Verification criteria:** Demonstrate that materially different contextual versions remain distinguishable and that an evaluation record can identify the context used for it.

**Verification method:** Identity and lineage verification.

### ECRA-G1-SEM-0005 — Explicit contextual applicability

The system MUST represent the applicability of contextual information to the evaluation for which it is used rather than relying solely on implicit runtime state.

**Rationale:** Context that affects evaluation must be reconstructable independently of transient execution state.

**Source basis:** ECRA-1000 evidence-context semantics; applicable shared semantic context foundations.

**Verification criteria:** Demonstrate reconstruction of the contextual inputs that materially affected a representative evaluation.

**Verification method:** Context reconstruction verification.

### ECRA-G1-INT-0008 — Context integrity

Where contextual information is subject to an applicable integrity mechanism, the system MUST preserve sufficient information to determine whether the contextual information used for an evaluation has been altered or corrupted.

**Rationale:** An evaluation cannot be reliably reconstructed if materially relevant contextual information can change without detection or representation.

**Source basis:** [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md); [approved Gen1 terminology](../00-project/terminology.md); ECRA-1000 integrity principles.

**Verification criteria:** Demonstrate detection or representation of supported context-integrity failures.

**Verification method:** Integrity verification.

## 5. Evaluation Requirements

### ECRA-G1-EVL-0001 — Evaluation execution

The system MUST evaluate a claim using the applicable evidence and evaluation context according to the applicable evaluation rules or policy, where one is required by the evaluation semantics.

**Rationale:** Evaluation is the central Gen1 capability and must operate on explicit inputs rather than implicit application state.

**Source basis:** [Approved Gen1 vision](../00-project/vision.md); [approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md); ECRA-1000 policy-driven evaluation semantics.

**Verification criteria:** Demonstrate execution of an evaluation with explicit claim, evidence, and context inputs and, where required by the evaluation semantics, an applicable evaluation policy or rule set.

**Verification method:** End-to-end functional verification.

### ECRA-G1-EVL-0002 — Evaluation result representation

The system MUST produce an explicit evaluation result that records the outcome of evaluating the claim under the applicable evidence and context.

**Rationale:** Evaluation must produce a durable, interpretable result rather than only an ephemeral execution outcome.

**Source basis:** [Approved Gen1 vision](../00-project/vision.md); [approved Gen1 terminology](../00-project/terminology.md).

**Verification criteria:** Demonstrate creation and retrieval of an evaluation result associated with its evaluation inputs.

**Verification method:** Contract and integration verification.

### ECRA-G1-EVL-0003 — Evaluation result identity

Each persisted evaluation result MUST have a stable identity that distinguishes it from other evaluation results.

**Rationale:** Results must be independently addressable and traceable throughout their lifecycle.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md); ECRA-1100 identity and traceability principles.

**Verification criteria:** Demonstrate stable result identity across supported storage and representation changes.

**Verification method:** Identity and persistence verification.

### ECRA-G1-EVL-0004 — Evaluation basis preservation

The system MUST preserve sufficient information to reconstruct the material inputs, context, applicable evaluation rules or policy, and relevant evidence relationships used to produce an evaluation result.

**Rationale:** An evaluation result that cannot be related to its material basis is not independently explainable or reproducible.

**Source basis:** ECRA-1000 provenance, policy-driven evaluation, and reproducible reasoning principles; ECRA-1100 traceability principles.

**Verification criteria:** Demonstrate reconstruction of the material evaluation basis for a representative persisted result.

**Verification method:** End-to-end replay and traceability verification.

### ECRA-G1-EVL-0005 — Deterministic evaluation

For repeated evaluation of the same materially relevant inputs, contextual state, applicable evaluation rules or policy, and execution conditions, the system MUST produce reproducible evaluation results, except where an explicitly represented nondeterministic factor is part of the evaluation semantics.

**Rationale:** Deterministic behavior is required for reproducibility, independent verification, and dispute resolution.

**Source basis:** [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md); ECRA-1000 reproducible reasoning and policy-driven evaluation principles.

**Verification criteria:** Demonstrate reproducible results for repeated evaluation of the same materially relevant inputs under equivalent execution conditions, and demonstrate explicit representation of any supported nondeterministic factor.

**Verification method:** Repeatability and replay verification.

### ECRA-G1-EVL-0006 — Evaluation explainability

The system MUST provide sufficient traceable information to explain how the material claim, evidence, context, and applicable evaluation rules or policy contributed to the evaluation result.

**Rationale:** Gen1 results must be explainable rather than opaque outcomes.

**Source basis:** [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md); ECRA-1000 explainability, provenance, and traceability principles.

**Verification criteria:** Demonstrate that a representative evaluation result can be explained using its preserved evaluation basis and traceability relationships.

**Verification method:** End-to-end traceability and independent-review verification.

### ECRA-G1-EVL-0007 — Explicit uncertainty

Where the applicable evaluation semantics produce uncertainty, the system MUST represent that uncertainty explicitly and MUST NOT silently convert uncertainty into certainty.

**Rationale:** Evidence-centric evaluation must distinguish incomplete or uncertain support from established conclusions.

**Source basis:** [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md); ECRA-1000 trust, reasoning, and uncertainty principles.

**Verification criteria:** Demonstrate that supported uncertain evaluation conditions produce an explicit uncertainty representation rather than an unconditional positive or negative result.

**Verification method:** Boundary and negative verification.

## 6. Evaluation Result and Decision Boundary

### ECRA-G1-EVL-0008 — Evaluation result shall not imply downstream authority

The system MUST NOT represent an evaluation result as itself constituting an authorization or operational decision unless a separately applicable decision or governance rule explicitly establishes that semantic relationship.

**Rationale:** Evaluation establishes an evidential assessment; it does not by itself establish authority to act.

**Source basis:** [Approved Gen1 terminology](../00-project/terminology.md); ECRA-1000 separation of evaluation, governance, trust, and decision concerns.

**Verification criteria:** Demonstrate that an evaluation result alone cannot bypass a separately applicable decision or governance requirement.

**Verification method:** Negative and boundary verification.

### ECRA-G1-EVL-0009 — Historical result preservation

Once an evaluation result is released or baselined, the system MUST preserve the information necessary to reconstruct the result as it was established, even when later revisions exist to the underlying claim, evidence, context, or evaluation policy.

**Rationale:** Historical evaluation results must remain auditable and must not silently change when their inputs evolve.

**Source basis:** ECRA-1000 lifecycle and provenance principles; ECRA-1100 baseline, lineage, and historical reconstruction principles.

**Verification criteria:** Demonstrate reconstruction of a released or baselined result after creation of a later revision to one or more of its material inputs.

**Verification method:** Baseline and replay verification.

## 7. Traceability Requirements

### ECRA-G1-TRC-0003 — Evaluation traceability

The system MUST maintain explicit, typed, and traversable traceability between an evaluation result and the material claim, evidence, source, acquired artifact, provenance, context, and applicable evaluation rules or policy used to produce it.

**Rationale:** Evaluation results must be independently reconstructable and explainable.

**Source basis:** ECRA-1100 traceability framework; ECRA-1000 provenance, context, and evaluation semantics.

**Verification criteria:** Demonstrate traversal from a representative evaluation result to its material inputs and evaluation basis, and reconstruction of the corresponding relationships. Canonical inverse relationships may be derived rather than physically duplicated.

**Verification method:** End-to-end relationship and replay verification.

### ECRA-G1-TRC-0004 — Context and policy traceability preservation

The system MUST preserve traceability to the specific contextual state and applicable evaluation rules or policy associated with each released or baselined evaluation result.

**Rationale:** A result cannot be meaningfully reconstructed if the context or evaluation rules used to produce it are ambiguous or replaced without lineage.

**Source basis:** ECRA-1000 context and policy-driven evaluation principles; ECRA-1100 baseline and traceability principles.

**Verification criteria:** Demonstrate that a historical evaluation result identifies the contextual and policy/rule versions applicable at the time of evaluation.

**Verification method:** Historical reconstruction verification.

## 8. Scope Boundaries

These requirements do not establish:

- a universal reasoning engine;
- a mandatory trust-scoring algorithm;
- a general-purpose policy language;
- a general-purpose decision automation platform;
- autonomous AI reasoning;
- a universal context-management platform;
- a complete verification or conformance methodology;
- Generation 2 reasoning, agent, or federation capabilities.

Such capabilities require separate approved scope or standards and MUST NOT be inferred from these requirements.

## 9. Requirement-to-Source Alignment

The principal source categories for this requirement set are:

| Source | Role |
|---|---|
| [Approved Gen1 project vision](../00-project/vision.md) | Product scope and evaluation objectives |
| [Approved Gen1 goals and non-goals](../00-project/goals-and-non-goals.md) | Gen1 evaluation, integrity, determinism, and scope objectives |
| [Approved Gen1 terminology](../00-project/terminology.md) | Canonical product-domain terminology |
| ECRA-1000 | Context, provenance, policy-driven evaluation, reasoning, trust, and architectural semantics |
| ECRA-1100 | Requirement identity, traceability, lifecycle, baseline, and historical reconstruction |
| Shared Semantic Foundation | Shared identity, relationship, context, provenance, and constraint foundations where approved/applicable |

ECRA-1000, ECRA-1100, and the applicable Shared Semantic Foundation references will be linked to their authoritative repository documents when those documents are incorporated into the repository. Until then, their names are retained as authoritative source references rather than replaced with guessed repository paths.

The document hierarchy is intentional: project-level documents establish scope and terminology; requirements documents define what the system must do; architecture and design documents elaborate how it is structured and behaves; implementation documents provide implementation guidance; and verification documents establish conformance.

## 10. Open Items

The following remain outside this PR and MUST be resolved before the relevant later implementation work:

1. Define the detailed evaluation-policy/rule representation and execution contract at the appropriate architecture/design layer.
2. Define the formal semantics for result equivalence, reproducibility, and supported nondeterministic factors.
3. Define the detailed uncertainty representation and interpretation rules.
4. Define the detailed evaluation-result schema and serialization contract.
5. Define the complete verification/conformance methodology under the applicable ECRA verification framework.
6. Add repository links to ECRA-1000, ECRA-1100, and the applicable Shared Semantic Foundation documents once those authoritative documents are incorporated.
