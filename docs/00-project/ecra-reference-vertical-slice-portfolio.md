# ECRA Reference Application — Vertical Slice Portfolio

> Status: REVIEW
> Authority: ENGINEERING / INFORMATIVE
> Generation: GEN1
> Scope: Reference-application use cases and implementation-driving vertical slices

## 1. Purpose

This document establishes the initial portfolio of concrete, end-to-end vertical slices that will be used to drive, exercise, and demonstrate the ECRA reference implementation.

The portfolio is intentionally use-case-driven. The ECRA reference implementation shall not attempt to implement every capability permitted by the ECRA specifications merely because the specifications define it. Capabilities shall be added to the reference implementation when they are demonstrated to be required by one or more selected vertical slices, or when they are necessary enabling infrastructure for such capabilities.

The vertical slices are application workflows, not additional ECRA specifications. They demonstrate how ECRA capabilities can be composed to solve real user problems.

## 2. Guiding Principle

The reference implementation shall follow this principle:

> Implement the smallest coherent ECRA capability set that is sufficient to support the selected vertical slices, while preserving the normative ECRA contracts and clear extension boundaries. Do not implement speculative generality solely for architectural completeness.

The reference implementation may therefore implement a subset of the semantic capabilities defined by the ECRA specifications at any given time.

## 3. Vertical Slice Definition

A vertical slice is a concrete user workflow that is executable end-to-end through the reference application and demonstrable through its user interface.

A completed vertical slice shall exercise, as applicable:

- real or realistically structured source material;
- user-visible input and workflow steps;
- ECRA semantic objects and relationships;
- provenance and traceability;
- evidence discovery and/or assessment;
- applicable validation or verification;
- machine representation and round-trip behavior where relevant;
- generation of a meaningful user-facing result or report.

A vertical slice is complete only when the complete workflow can be demonstrated through the application, not merely when backend components have unit tests.

## 4. Initial Use-Case Families

The initial candidate portfolio spans multiple domains so that the reference implementation is tested against materially different evidence patterns rather than being optimized for a single domain.

### 4.1 Business

#### VS-B01 — Company Due Diligence

**User:** Investor, analyst, or due-diligence reviewer.

**Goal:** Given a company presentation or other business document, identify material claims and determine which claims are supported, contradicted, partially supported, or unresolved by authoritative filings, financial statements, and other relevant sources.

**End-to-end flow:**

```text
Company document
    → identify material claims
    → discover relevant evidence
    → associate evidence with claims
    → assess support / contradiction / uncertainty
    → preserve provenance and traceability
    → generate due-diligence report
```

#### VS-B02 — Vendor Requirement Verification

**User:** Procurement, engineering, or assurance reviewer.

**Goal:** Given organizational requirements and a vendor proposal, determine whether vendor claims are adequately supported by supplied evidence.

**End-to-end flow:**

```text
Requirements + vendor proposal
    → identify vendor claims
    → identify supplied evidence
    → map requirements ↔ claims ↔ evidence
    → identify gaps and exceptions
    → generate compliance / evaluation report
```

### 4.2 Journalism

#### VS-J01 — Investigative Fact Check

**User:** Journalist or fact checker.

**Goal:** Given an article, transcript, or draft containing factual claims, identify relevant evidence and determine whether each claim is supported, contradicted, partially supported, or unresolved.

**End-to-end flow:**

```text
Article / transcript
    → identify factual claims
    → discover credible sources
    → extract relevant evidence
    → associate evidence with claims
    → assess support / contradiction / limitations
    → generate fact-check report
```

### 4.3 Law

#### VS-L01 — Case Evidence Review

**User:** Lawyer, legal researcher, or case reviewer.

**Goal:** Given a collection of case documents, identify material factual claims and determine which evidence in the case materials supports, contradicts, or leaves those claims unresolved.

**End-to-end flow:**

```text
Case documents
    → identify material factual claims
    → identify relevant evidence
    → map claims ↔ evidence
    → preserve document locations and provenance
    → identify supporting / contradictory / missing evidence
    → generate case evidence report
```

#### VS-L02 — Contract Compliance Review

**User:** Legal, procurement, or compliance reviewer.

**Goal:** Given contractual obligations and a supplier's evidence package, determine which obligations have adequate evidence of compliance and which have evidence gaps.

**End-to-end flow:**

```text
Contract obligations
    + supplier evidence
    → represent requirements / obligations
    → identify compliance claims
    → map claims ↔ evidence
    → assess coverage and gaps
    → generate compliance report
```

### 4.4 Forensics

#### VS-F01 — Incident / Digital Forensic Investigation

**User:** Investigator, forensic analyst, or incident responder.

**Goal:** Given logs, reports, communications, and other forensic artifacts, identify evidence relevant to competing investigative claims or hypotheses and produce an auditable investigation report.

**End-to-end flow:**

```text
Forensic artifacts
    → observations / candidate claims / hypotheses
    → evidence association
    → provenance and source-location tracking
    → support / contradiction / uncertainty assessment
    → investigation timeline or finding set
    → generate investigation report
```

### 4.5 Engineering

#### VS-E01 — Engineering Design Evidence Review

**User:** Systems engineer, architect, or design reviewer.

**Goal:** Given engineering requirements, an architecture/design, design decisions, analyses, and test results, determine whether important design claims and decisions are adequately supported by requirements and evidence.

**End-to-end flow:**

```text
Requirements
    + architecture / design
    + analyses / test results
    → identify design claims and decisions
    → establish traceability
    → associate supporting evidence
    → identify gaps / conflicts
    → generate design review report
```

#### VS-E02 — Engineering Failure Investigation

**User:** Reliability engineer or failure-analysis team.

**Goal:** Given failure reports, telemetry, test results, and engineering records, evaluate evidence supporting competing root-cause hypotheses.

**End-to-end flow:**

```text
Failure artifacts
    → observations / hypotheses
    → evidence discovery and association
    → provenance tracking
    → competing-evidence assessment
    → unresolved questions
    → generate failure-analysis report
```

### 4.6 Scientific / Research

#### VS-S01 — Research Claim Verification

**User:** Researcher, reviewer, or research analyst.

**Goal:** Given a research paper or study, identify important claims and determine whether the reported experimental or observational evidence supports those claims.

**End-to-end flow:**

```text
Research paper
    → identify important claims
    → identify reported evidence
    → associate evidence with claims
    → distinguish result from interpretation
    → assess support / limitation / contradiction
    → generate evidence review
```

#### VS-S02 — Literature Evidence Review

**User:** Researcher or evidence-review analyst.

**Goal:** Given a research question and a document corpus, identify relevant evidence across sources and synthesize what the corpus establishes, disputes, or leaves unresolved.

### 4.7 Religion / Historical and Religious Texts

#### VS-R01 — Lecture or Sermon Claim Review

**User:** Reader, researcher, educator, or reviewer.

**Goal:** Given a transcript of a lecture, sermon, or religious talk, identify substantive claims and identify evidence that supports, contradicts, qualifies, or leaves those claims unresolved, then generate a traceable report.

**End-to-end flow:**

```text
Lecture / sermon transcript
    → identify substantive claims
    → classify claims where useful
    → identify relevant primary / secondary sources
    → extract relevant evidence
    → associate evidence with claims
    → distinguish support / contradiction / interpretation / uncertainty
    → preserve source provenance and locations
    → generate evidence report
```

The application shall not treat the evidence-review workflow as a mechanism for determining theological truth. The purpose of the slice is to represent claims, sources, evidence, relationships, assessments, and uncertainty in a transparent and auditable manner.

This slice is intentionally included to test whether the ECRA approach remains domain-neutral when claims can be factual, historical, interpretive, or theological in character.

### 4.8 Compliance / Audit

#### VS-C01 — Regulatory Compliance Evidence Review

**User:** Compliance officer, auditor, or assurance reviewer.

**Goal:** Given requirements and an organization's evidence package, determine which requirements have adequate evidence and which have gaps or exceptions.

**End-to-end flow:**

```text
Requirements / obligations
    + organization evidence
    → claims of compliance
    → evidence association
    → traceability
    → coverage / exception assessment
    → generate audit report
```

### 4.9 Public Policy

#### VS-P01 — Policy Evidence Review

**User:** Policy analyst, researcher, or reviewer.

**Goal:** Given a proposed policy and the evidence cited in support of it, determine whether material policy claims are supported, contradicted, qualified, or unresolved.

### 4.10 Consumer / General User

#### VS-U01 — Product Claim Verification

**User:** Consumer or product researcher.

**Goal:** Given a product page or product document, identify material product claims and compare them with manufacturer documentation and independent evidence.

## 5. Initial Prioritization

The candidate portfolio is intentionally broader than the first implementation scope. The initial reference application should prioritize a small set that maximizes semantic diversity and reuse while remaining practical to demonstrate.

The recommended initial set is:

| Priority | Slice | Primary reason |
|---|---|---|
| P0 | VS-J01 — Investigative Fact Check | Direct realization of the core claim → evidence → report workflow |
| P0 | VS-R01 — Lecture or Sermon Claim Review | Exercises the same core workflow with factual, historical, interpretive, and theological claim contexts |
| P0 | VS-B01 — Company Due Diligence | Exercises authoritative-source comparison and material-claim analysis |
| P0 | VS-L01 — Case Evidence Review | Exercises legal-document provenance, source locations, and competing evidence |
| P0 | VS-F01 — Incident / Digital Forensic Investigation | Exercises evidence-first investigation and strong provenance requirements |
| P0 | VS-E01 — Engineering Design Evidence Review | Exercises requirements, architecture, decisions, evidence, and traceability |
| P1 | VS-C01 — Regulatory Compliance Evidence Review | Exercises requirements/obligations and evidence coverage at scale |

The P0 portfolio should be treated as the initial proving portfolio. P1 and later slices should be added after the first core has demonstrated sufficient capability and after their incremental requirements are understood.

This prioritization is subject to refinement during detailed use-case analysis.

## 6. Workflow Pattern Coverage

The portfolio deliberately includes several workflow orientations.

### Claim-first

```text
Claim → Evidence → Assessment → Report
```

Examples: VS-J01, VS-R01, VS-B01.

### Evidence-first

```text
Evidence corpus → Observations / Claims → Relationships → Assessment → Report
```

Examples: VS-F01, VS-E02.

### Requirement-first

```text
Requirement / Obligation → Claim → Evidence → Coverage / Assessment → Report
```

Examples: VS-B02, VS-L02, VS-C01.

### Architecture/design-first

```text
Architecture / Design → Decision / Claim → Evidence → Traceability → Assessment → Report
```

Examples: VS-E01.

### Corpus synthesis

```text
Question → Document corpus → Claims / Evidence → Cross-source assessment → Synthesis report
```

Examples: VS-S02, VS-P01.

This diversity is important because the reference implementation should not accidentally optimize for only one direction of information flow.

## 7. Common End-to-End Capability Candidates

The following capabilities are candidates for the shared reference core because multiple vertical slices appear to require them:

- artifact/document registration;
- stable identity;
- source location and citation;
- claim representation;
- evidence representation;
- evidence-to-claim relationships;
- support, contradiction, qualification, and unresolved relationships or assessments as justified by the normative specifications;
- provenance;
- traceability;
- source/version state where required;
- structured assessment results;
- uncertainty and limitations;
- machine representation;
- report generation;
- user-visible inspection of claims, evidence, relationships, provenance, and assessment.

These are candidate capabilities, not yet implementation commitments. Their final inclusion shall be determined through detailed analysis of the selected slices and the applicable normative specifications.

## 8. Capabilities That Must Not Be Added Speculatively

Unless a selected vertical slice demonstrates a need, the reference implementation should not introduce generalized infrastructure merely for theoretical completeness, including:

- universal reasoning engines;
- generic ontology inference systems;
- arbitrary workflow engines;
- distributed microservice architecture;
- graph-database dependence;
- universal query languages;
- generalized plugin marketplaces;
- elaborate multi-tenant infrastructure;
- domain-specific features that are not reusable across demonstrated slices;
- AI-specific abstractions that unnecessarily constrain implementation choices.

The implementation shall preserve replaceability and extension boundaries without implementing speculative machinery.

## 9. UI Demonstration Requirement

Every selected vertical slice shall be demonstrable through the reference application UI.

At minimum, the UI should allow a demonstrator to:

1. provide or select the relevant source material;
2. inspect identified claims or observations;
3. inspect identified evidence;
4. inspect claim/evidence relationships;
5. inspect source locations and provenance;
6. inspect assessments and uncertainty;
7. follow traceability links where applicable;
8. generate and inspect the resulting report.

The UI should expose enough semantic detail to demonstrate ECRA behavior without requiring the user to understand the internal implementation architecture.

## 10. Vertical Slice Completion Criteria

A selected slice shall not be considered complete merely because its individual components pass unit tests.

A slice is complete when:

- the complete user workflow executes successfully;
- the UI supports the workflow end-to-end;
- the required ECRA semantics are represented correctly;
- provenance and source locations are preserved;
- applicable relationships and traceability are preserved;
- the resulting report is reproducible from the recorded inputs and processing state to the extent required by the applicable contract;
- applicable validation/conformance checks pass;
- serialization and round-trip behavior pass where applicable;
- negative and boundary cases are demonstrated;
- important failures are understandable to the user;
- the slice's implementation requirements and lessons learned are recorded.

## 11. Capability Derivation Rule

For each candidate reference-implementation capability, classify it as:

### Level 1 — Demonstrated necessity

Required directly by one or more selected vertical slices.

**Default:** implement.

### Level 2 — Enabling infrastructure

Not directly visible in the user workflow but necessary to implement Level 1 cleanly and consistently.

**Default:** implement when justified.

### Level 3 — Speculative capability

Permitted by an ECRA specification but not currently required by a selected slice and not necessary enabling infrastructure.

**Default:** defer.

This classification shall be maintained in the implementation coverage matrix.

## 12. Reference Implementation Coverage Matrix

A living coverage matrix shall map:

```text
ECRA specification capability
        ↕
Reference implementation capability
        ↕
Vertical slice requirement
        ↕
UI demonstration
        ↕
Test / acceptance criterion
```

The matrix shall identify implemented, partial, deferred, and intentionally excluded capabilities.

## 13. Evolution Through Additional Vertical Slices

The initial P0 portfolio is not a permanent limit.

After the initial slices are operational, additional slices shall be added when they provide meaningful evidence about:

- uncovered semantic capabilities;
- different information-flow patterns;
- new provenance requirements;
- new traceability patterns;
- representation/interoperability behavior;
- scalability or robustness;
- domain neutrality;
- limitations or weaknesses in the current reference core.

New slices should first be analyzed for their incremental requirements. A new capability should be generalized into the core only when there is sufficient evidence that doing so is justified.

## 14. Relationship to ECRA Specifications

Vertical slices shall consume ECRA semantics; they shall not silently redefine them.

Where a vertical slice exposes an ambiguity, missing rule, or inconsistency in an ECRA specification:

1. record the observation;
2. determine whether it is an implementation issue or specification issue;
3. correct the authoritative specification when required;
4. update the implementation contract;
5. update the reference implementation and slice tests.

Implementation behavior shall not become de facto normative semantics merely because it was implemented first.

## 15. Immediate Next Steps

1. Review and approve this initial vertical-slice portfolio.
2. Develop detailed specifications for the P0 slices, beginning with VS-J01 and VS-R01 because they directly instantiate the core claim → evidence → report workflow.
3. Derive the cross-slice capability matrix from the P0 portfolio.
4. Identify the minimum reference-core capability set.
5. Establish the reference application architecture and UI boundary.
6. Continue the ECRA-1200 normative work, including the Normative Relationship Catalog, using the concrete slice requirements as an implementation-relevance input without allowing application concerns to redefine ECRA-1200 ownership.
7. Implement the minimum reference core required for the first end-to-end slice.
8. Build VS-J01 and VS-R01 as fully demonstrable UI-backed slices.
9. Use the results to refine the core before implementing the remaining P0 slices.
10. Maintain the coverage matrix and defer unsupported/speculative capabilities.

## 16. Non-Goals

This document does not:

- define new ECRA semantic ownership;
- define implementation technology choices;
- define concrete serialization schemas;
- define AI models or retrieval algorithms;
- prescribe domain-specific truth judgments;
- require all candidate slices to be implemented immediately;
- require the reference implementation to implement every ECRA specification capability;
- define production deployment architecture.

## 17. Design Status

This document captures the initial engineering portfolio and is intended to be reviewed before being treated as an approved implementation-planning baseline. The candidate portfolio may evolve as concrete slice specifications and capability analysis are developed.
