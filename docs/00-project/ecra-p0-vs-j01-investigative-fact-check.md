# ECRA Reference Application — VS-J01 Investigative Fact Check

> Status: REVIEW
> Authority: ENGINEERING / INFORMATIVE
> Generation: GEN1
> Scope: Detailed P0 vertical-slice specification for the Investigative Fact Check workflow
> Matrix Basis: Approved ECRA Reference Implementation — Cross-Slice Capability Matrix

## 1. Purpose and Scope

### 1.1 Purpose

VS-J01 demonstrates an end-to-end claim-first evidence-review workflow for journalism and fact checking.

The slice shall allow a journalist or fact checker to provide an article, transcript, or draft containing factual claims; identify material claims; associate relevant evidence from credible sources; assess the relationship between claims and evidence; preserve provenance and traceability; and produce a user-facing fact-check report.

The slice is intended to demonstrate why ECRA's evidence-centric semantic capabilities are useful in a real user workflow. It is not intended to implement a general-purpose journalism platform, search engine, automated fact-checking service, or universal reasoning system.

### 1.2 Scope

The slice covers:

1. source material selection or ingestion;
2. acquired-artifact preservation sufficient for the supported workflow;
3. identification and representation of factual claims;
4. identification and representation of relevant evidence;
5. explicit claim/evidence association;
6. source representation and source-location capture;
7. provenance and traceability;
8. evidence and claim assessment, including support, contradiction, qualification, and unresolved states where applicable;
9. integrity, authenticity, and authority information where supported by the acquisition or assessment mechanism;
10. structured evaluation/result representation to the extent required by the approved Gen1 evaluation requirements;
11. machine representation and semantic round-trip preservation;
12. user inspection through the reference application UI;
13. generation and inspection of a traceable fact-check report.

### 1.3 Non-goals

This slice does not establish or require:

- a general-purpose web crawler;
- unrestricted web or source acquisition;
- a general search engine;
- universal source ranking;
- autonomous fact-checking without reviewable evidence and provenance;
- a universal reasoning or ontology-inference engine;
- a mandatory numerical truth score;
- a domain-independent policy language;
- a generalized workflow/orchestration engine;
- a distributed or microservice deployment architecture;
- an AI-specific semantic model;
- a complete journalism editorial-management system;
- a general content-generation system.

Domain-specific claim extraction, source discovery, retrieval strategies, and report presentation remain application-level concerns unless later cross-slice evidence justifies promotion.

### 1.4 Intended outcome

The primary outcome is a fact-check record in which each selected material claim can be inspected together with:

- the relevant source and acquired artifact;
- the evidence used;
- the semantic relationship between evidence and claim;
- source location(s);
- provenance and integrity information where available;
- the resulting assessment;
- uncertainty and limitations;
- sufficient traceability to reconstruct the basis of the assessment.

The outcome is an evidence-grounded assessment record, not an assertion that the system itself possesses ultimate knowledge of truth.

## 2. Scenario and Preconditions

### 2.1 Primary scenario

A journalist or fact checker has an article, transcript, or draft containing multiple factual statements. The reviewer wants to determine which statements are adequately supported, contradicted, partially supported or qualified by available evidence, and which remain unresolved.

A representative input may contain a mixture of:

- directly verifiable factual statements;
- quantitative claims;
- statements about people, organizations, events, dates, or places;
- claims that combine multiple propositions;
- claims for which evidence is incomplete or conflicting;
- statements that appear factual but are actually opinion, prediction, interpretation, or rhetorical language.

The application shall allow the reviewer to distinguish claims selected for fact checking from content that is outside the factual-evaluation scope of the slice.

### 2.2 Required inputs

The minimum required user input is source material containing one or more candidate factual claims.

The source material shall be representable as an acquired artifact with sufficient source and provenance information for the supported workflow.

The application shall not require that all claims be automatically identified before the workflow can continue. Human identification or correction shall remain possible.

### 2.3 Optional inputs

The workflow may accept, where available:

- source metadata supplied by the user;
- known source URLs or locators;
- publication date or revision information;
- author or publisher information;
- user-specified claims to prioritize;
- candidate evidence sources supplied by the user;
- contextual information relevant to interpreting a claim;
- reviewer comments or notes.

Optional information shall not be represented as established fact merely because it was supplied by a user.

### 2.4 Preconditions

Before evaluation of a claim:

1. the source material must be available to the application;
2. the acquired artifact must have an identifiable representation;
3. the claim must have stable identity and sufficient information for the evaluation boundary;
4. each evidence item used for assessment must be identifiable;
5. source information must be recorded for evidence where available;
6. applicable source locations must be recorded sufficiently to permit reviewer inspection;
7. the evaluation context and applicable evaluation rules or policy must be represented where required by the Gen1 evaluation contract.

### 2.5 Input-quality assumptions

The slice shall explicitly tolerate imperfect inputs. Source material may be incomplete, ambiguous, duplicated, malformed, unavailable, revised, or inaccessible.

The application shall distinguish:

- successful acquisition;
- successful representation;
- incomplete representation;
- unavailable source;
- failed processing;
- unresolved evaluation.

Failure to obtain evidence shall not be silently represented as evidence that a claim is false or true.

## 3. End-to-End Workflow

### 3.1 Workflow overview

```text
Article / Transcript / Draft
        ↓
Source selection / ingestion
        ↓
Acquire and register artifact
        ↓
Identify candidate factual claims
        ↓
Review / correct selected claims
        ↓
Identify relevant evidence
        ↓
Register evidence and sources
        ↓
Associate evidence ↔ claims
        ↓
Capture locations and provenance
        ↓
Assess support / contradiction / qualification / unresolved state
        ↓
Record uncertainty and limitations
        ↓
Preserve evaluation basis
        ↓
Generate fact-check report
        ↓
Inspect / trace / revise as permitted
```

### 3.2 Step 1 — Provide source material

The user provides or selects an article, transcript, or draft.

The application records the source material as an acquired artifact when the material is acquired by ECRA. The artifact retains sufficient identity, provenance, and integrity information for subsequent processing.

The application shall distinguish the source as the origin or attribution context from the acquired artifact as the concrete representation obtained for processing.

### 3.3 Step 2 — Register source and artifact

The system creates or resolves:

- source identity;
- acquired artifact identity;
- source location or locator where available;
- source version/revision state where available;
- acquisition/provenance information;
- applicable integrity information.

Source authenticity and source authority shall be represented separately when such information is available.

### 3.4 Step 3 — Identify candidate claims

Candidate factual claims may be identified by an application-level extraction capability or by a human reviewer.

Claim extraction is not itself an ECRA semantic capability. The resulting claim is represented using the applicable ECRA claim semantics.

The reviewer shall be able to inspect the extracted claim and correct its text, boundaries, or selection before evaluation.

Where a source sentence contains multiple materially distinct propositions, the application should permit separate claim representations where doing so improves evidence traceability and assessment clarity.

### 3.5 Step 4 — Determine evaluation eligibility

Each selected claim is checked for the minimum information required to enter the evaluation path.

A claim that does not satisfy the evaluation boundary shall be rejected or marked incomplete with an explicit user-visible reason.

The system shall not treat an incomplete claim as successfully evaluated.

### 3.6 Step 5 — Identify relevant evidence

The application may support user-provided evidence, application-assisted discovery, or another replaceable evidence-discovery mechanism.

The discovery mechanism is not part of the ECRA semantic core. The output of discovery is one or more identifiable evidence items that can be associated explicitly with a claim.

Evidence selection shall preserve the distinction between:

- evidence relevance;
- source authority;
- source authenticity;
- artifact integrity;
- the substantive assessment of the claim.

### 3.7 Step 6 — Register evidence and sources

For each selected evidence item, the system records, as applicable:

- stable evidence identity;
- source identity;
- acquired artifact identity;
- version/revision or lineage information;
- source location;
- integrity information;
- authenticity information;
- authority information;
- acquisition and transformation provenance.

### 3.8 Step 7 — Associate evidence with claims

The system creates an explicit typed association between each evidence item and each claim for which the evidence is materially relevant.

The relationship shall be independently traversable from claim to evidence and, where supported by canonical inverse rules, from evidence to claim.

The relationship shall not be inferred solely from co-location, search results, or storage structure.

### 3.9 Step 8 — Assess evidence relationship

The reviewer or applicable evaluation mechanism determines how the evidence bears on the claim.

The slice shall support the approved assessment distinctions needed by the workflow, including:

- support;
- contradiction;
- qualification / partial support where applicable;
- unresolved / insufficient basis.

An evidence item may qualify rather than fully support a claim. Multiple evidence items may have different or conflicting relationships to the same claim.

The application shall preserve evidence properties separately from the resulting assessment.

### 3.10 Step 9 — Preserve provenance and traceability

The system preserves the origin and processing history of:

- source material;
- acquired artifacts;
- claims;
- evidence;
- claim/evidence relationships;
- assessment results;
- evaluation context and applicable rules or policy where required.

Traceability shall use stable semantic identities rather than relying solely on mutable storage locations.

### 3.11 Step 10 — Record uncertainty and limitations

Where evidence is incomplete, conflicting, ambiguous, unavailable, or otherwise insufficient for a determinate assessment, the system shall represent the uncertainty or limitation explicitly.

The absence of evidence shall not be silently converted into contradiction.

Likewise, the presence of an apparently authoritative source shall not be silently converted into proof of the claim.

### 3.12 Step 11 — Produce evaluation result

Where the approved Gen1 evaluation path is used, the system produces an explicit evaluation result associated with the claim, evidence, context, and applicable evaluation rules or policy.

The result shall preserve sufficient evaluation basis to explain and reproduce the material result under the applicable contract.

Where the detailed evaluation-policy or uncertainty semantics remain outside currently approved implementation scope, the slice shall use the smallest supported representation and shall not invent additional normative semantics.

### 3.13 Step 12 — Generate report

The application generates a fact-check report containing, at minimum:

- the fact-check subject/source;
- selected claims;
- claim text and source location;
- evidence items and source information;
- claim/evidence relationship(s);
- assessment result;
- uncertainty and limitations;
- relevant provenance and integrity information;
- traceability references sufficient for inspection.

The report is a user-facing application artifact. Its presentation format is not itself an ECRA semantic requirement.

## 4. Semantic Object Requirements

### 4.1 Required semantic objects

| Object | Role in VS-J01 | Required? | Authority / basis |
|---|---|---:|---|
| Source | Identifies origin/attribution of source material or evidence | Yes | Gen1 Claim and Evidence Requirements; ECRA-1000 |
| Acquired Artifact | Represents concrete source material acquired for processing | Yes where acquired | Gen1 Claim and Evidence Requirements |
| Claim | Represents factual proposition selected for evaluation | Yes | ECRA-G1-FUN-0001; ECRA-G1-SEM-0001 |
| Evidence | Represents information relevant to determining whether/how far a claim is established | Yes | ECRA-G1-FUN-0003 |
| Claim–Evidence relationship | Explicitly represents evidence relevance/bearing on a claim | Yes | ECRA-G1-FUN-0004; ECRA-G1-TRC-0001 |
| Provenance | Represents origin, acquisition, transformation, and association history | Yes | ECRA-G1-INT-0005; ECRA-G1-SEM-0003 |
| Source location | Identifies the relevant location within source/artifact | Yes for traceable review | P0 UI/traceability requirements; portfolio workflow |
| Integrity information | Preserves supported artifact/evidence integrity determination | Yes where mechanism applies | ECRA-G1-INT-0001; ECRA-G1-INT-0004 |
| Source authenticity | Preserves supported authenticity result separately | Where applicable | ECRA-G1-INT-0002 |
| Source authority | Represents basis for source authority separately from authenticity | Yes where applicable | ECRA-G1-INT-0003 |
| Evaluation Context | Represents contextual information required for contextual evaluation | Where evaluation semantics require | ECRA-G1-FUN-0007 onward |
| Evaluation Result | Durable result of evaluating claim under evidence/context | Where Gen1 evaluation path is used | ECRA-G1-EVL-0002 onward |
| Assessment / uncertainty information | Records structured assessment and limitations | Yes | P0 capability matrix; ECRA-G1-EVL-0007 |

### 4.2 Claim requirements

Each selected claim shall:

- have stable identity;
- contain sufficient proposition content for evaluation;
- retain origin information sufficient to locate the claim in the source artifact;
- remain independent of storage location and serialization format;
- be distinguishable from reviewer comments, evidence, and evaluation results.

### 4.3 Evidence requirements

Each evidence item shall:

- have stable identity;
- retain applicable version or lineage information;
- identify its source where available;
- retain its relevant source location;
- retain applicable integrity, authenticity, and authority information separately;
- remain traceable to the claim(s) for which it was used.

### 4.4 Reviewer input

Reviewer comments, corrections, and observations are application-level inputs. Where a reviewer statement materially participates in the evidence analysis, the application may represent it using applicable claim/assertion semantics rather than creating a new ECRA root type.

A reviewer comment shall not become authoritative merely because it was entered into the application.

## 5. Relationship Requirements

### 5.1 Relationship set

The initial VS-J01 relationship set shall be limited to relationships demonstrated by the workflow and authoritative requirements.

| Relationship | Source | Target | Direction | Purpose |
|---|---|---|---|---|
| Evidence relevance / bearing on claim | Evidence | Claim | Explicit | Establishes why evidence is considered in evaluating a claim |
| Claim origin | Claim | Source/Artifact | Explicit traceability association | Locates the claim in originating material |
| Evidence origin | Evidence | Source/Artifact | Explicit traceability association | Locates evidence in originating material |
| Provenance association | Provenance record | Affected entity | Explicit | Preserves origin/acquisition/transformation history |
| Evaluation basis | Evaluation Result | Claim/Evidence/Context/Policy as applicable | Explicit traceability | Preserves material basis of result |

The exact canonical names of relationship types shall follow the applicable authoritative relationship semantics when those names are established. This slice shall not invent competing portfolio-wide relationship names.

### 5.2 Directionality

Where a relationship has directional semantics, its direction shall be explicit. Diagram position, UI ordering, or storage order shall not determine semantic direction.

### 5.3 Multiplicity

The workflow shall support:

- one claim associated with zero or more evidence items;
- one evidence item associated with zero or more claims;
- multiple evidence items bearing different relationships to the same claim;
- a claim with no currently identified evidence;
- an evaluation result associated with the material inputs used for that result.

Detailed normative multiplicities shall defer to the applicable ECRA relationship authority.

### 5.4 Relationship provenance

Material relationship creation, modification, or assessment shall retain sufficient provenance to identify its origin and, where relevant, the reviewer or processing step responsible.

## 6. Evidence and Assessment Requirements

### 6.1 Evidence relevance

Evidence is included because it is relevant to determining whether, or to what extent, the claim is established. Relevance shall be represented explicitly.

### 6.2 Assessment dimensions

The application shall distinguish at least the following user-visible assessment outcomes where applicable:

- Supported;
- Contradicted;
- Partially Supported / Qualified;
- Unresolved / Insufficient Evidence.

These labels are workflow-level manifestations of the approved P0 assessment capability. They shall not be interpreted as a new normative ECRA truth calculus.

### 6.3 Multiple evidence items

A claim may have multiple evidence items, including evidence that:

- independently supports the claim;
- contradicts part of the claim;
- qualifies the claim's scope or conditions;
- is insufficient to resolve the claim;
- conflicts with other evidence.

The application shall expose the individual evidence relationships rather than collapsing all evidence into a single opaque score.

### 6.4 Evidence properties versus conclusion

The following shall remain separate:

```text
Artifact integrity
Source authenticity
Source authority
Evidence relevance
Evidence relationship
Evaluation result
Downstream editorial decision
```

Successful integrity verification does not establish claim truth. Source authenticity does not establish source authority. Evaluation result does not itself constitute a downstream editorial or publication decision.

### 6.5 Human and automated responsibilities

The slice may use automated processing for:

- candidate claim extraction;
- candidate evidence discovery;
- source metadata extraction;
- location extraction;
- duplicate detection;
- preliminary relationship suggestions.

However, automated suggestions shall remain distinguishable from accepted semantic relationships or assessments. The application shall provide a review/accept/correct path before a result is treated as the authoritative state of the slice record.

No unsupported automated inference shall be presented as established fact.

## 7. Provenance and Traceability

### 7.1 Minimum provenance

The slice shall preserve, as applicable:

- source identity;
- source locator;
- acquired artifact identity;
- acquisition timestamp/state;
- artifact version or revision;
- claim origin and source location;
- evidence origin and source location;
- evidence-to-claim relationship origin;
- assessment origin;
- evaluation context identity/version;
- applicable evaluation rule/policy identity/version;
- processing/transformation history;
- relevant user actions.

### 7.2 Source locations

Source locations shall be sufficiently precise to allow the reviewer to return from a claim or evidence item to the relevant material.

The exact location representation may vary by artifact type. It shall not be assumed that a URL alone is sufficient for all source materials.

Examples of application-level location forms include, as applicable:

- document page and paragraph;
- transcript timestamp;
- section or heading;
- table/row/cell;
- quoted passage boundaries;
- web-resource locator plus retrieved artifact state.

The application shall preserve the location semantics appropriate to the acquired artifact without making these examples universal ECRA types.

### 7.3 Traceability traversal

The UI and underlying implementation shall support traversal at least along:

```text
Claim
  → originating source/artifact
  → evidence
  → evidence source/artifact
  → assessment/evaluation result
  → provenance
```

Where canonical inverse relationships are available, reverse traversal shall also be supported without requiring duplicate semantic relationship storage.

### 7.4 Historical preservation

Once a fact-check result is released or baselined, its material basis shall remain reconstructable even if later revisions occur to source material, evidence, context, or evaluation rules.

The slice does not define a general version-control platform; it demonstrates the minimum preservation required by the approved Gen1 contracts.

## 8. Input / Output Contracts

### 8.1 Input contract

The logical input to the slice is:

```text
FactCheckRequest
├── sourceMaterial
├── optional user-selected claims
├── optional candidate evidence
├── optional source metadata
├── optional evaluation context
└── optional reviewer instructions
```

The exact machine syntax is deferred to the implementation/interchange layer.

### 8.2 Input validation

The application shall deterministically validate the minimum structural conditions required to begin processing.

Examples of invalid input include:

- no source material;
- unreadable or unsupported artifact representation;
- claim with insufficient identifying/propositional content at the evaluation boundary;
- evidence reference that cannot be resolved;
- malformed source location where a location is required;
- invalid relationship endpoint.

The user shall receive an understandable failure or incomplete-state indication.

### 8.3 Output contract

The logical output is:

```text
FactCheckResult
├── source/artifact references
├── selected claims
├── evidence items
├── claim/evidence relationships
├── assessments / evaluation results
├── uncertainty and limitations
├── provenance and traceability
└── report reference/content
```

### 8.4 Incomplete result

The system shall support a result that is explicitly incomplete when one or more material claims remain unresolved, evidence is unavailable, or processing fails for part of the workflow.

An incomplete result is not a failed claim evaluation and shall not be silently converted into a negative assessment.

## 9. UI Demonstration

### 9.1 Minimum screens / interactions

The reference application shall provide a minimal end-to-end UI consisting of the following logical capabilities. These may be implemented as separate screens or combined views.

1. **Source Intake** — select/provide the article, transcript, or draft and inspect acquisition state.
2. **Claim Review** — display candidate claims, permit selection/correction, and show source locations.
3. **Evidence Review** — display evidence items, source information, locations, and integrity/authenticity/authority metadata where available.
4. **Relationship / Assessment View** — show claim-to-evidence relationships and the resulting assessment, including uncertainty and limitations.
5. **Traceability View** — permit traversal from claim to evidence to sources/artifacts and provenance.
6. **Report View** — generate and inspect the final fact-check report.

### 9.2 Claim inspection

The user shall be able to inspect:

- claim identity;
- claim text;
- originating source/artifact;
- source location;
- evaluation status;
- associated evidence;
- assessment and uncertainty.

### 9.3 Evidence inspection

The user shall be able to inspect:

- evidence identity;
- evidence content or representation;
- source;
- source location;
- artifact/version state;
- integrity information where applicable;
- authenticity and authority information where applicable;
- claims for which the evidence is relevant.

### 9.4 Assessment inspection

The user shall be able to distinguish:

- support;
- contradiction;
- qualification/partial support;
- unresolved/insufficient evidence;
- uncertainty;
- limitations.

### 9.5 Report inspection

The report view shall permit the reviewer to move from a reported claim to its supporting material and assessment basis without leaving the reference application workflow.

The report shall identify unresolved claims rather than omitting them.

## 10. Negative and Boundary Cases

| Case | Required behavior |
|---|---|
| No source material | Reject intake with explicit error; do not create a successful fact-check result |
| Unsupported/malformed artifact | Report processing failure; preserve available acquisition/error provenance |
| No claims identified | Permit explicit empty/incomplete review state; do not fabricate claims |
| Candidate claim is opinion/prediction rather than factual proposition | Allow reviewer to exclude or classify outside this slice; do not force factual assessment |
| Claim lacks minimum evaluation information | Mark ineligible/incomplete and provide reason |
| No evidence found | Preserve claim as unresolved/insufficient evidence; do not infer contradiction |
| Evidence source inaccessible | Preserve evidence/reference state as unavailable where supported; do not silently discard the relationship |
| Evidence conflicts with other evidence | Preserve distinct evidence relationships and expose conflict; do not collapse without an explicit assessment basis |
| Evidence duplicates another item | Preserve identity/lineage and allow deduplication handling without losing provenance |
| Source changes after acquisition | Preserve acquired artifact/version state and historical provenance; do not silently rewrite the prior evaluation basis |
| Source authenticity cannot be established | Represent authenticity as unknown/unavailable as supported; do not infer inauthenticity |
| Source is authentic but authority is uncertain | Preserve authenticity and authority separately |
| Integrity check succeeds | Preserve integrity result; do not treat it as proof of claim truth |
| Source location ambiguous | Mark location limitation and retain enough provenance for the reviewer to understand the gap |
| Claim/evidence relationship invalid | Reject or quarantine the invalid relationship; do not use it in a successful assessment |
| Provenance incomplete | Mark the affected result incomplete or limited; do not silently invent provenance |
| Automated claim extraction incorrect | Allow reviewer correction/removal and preserve material processing provenance where applicable |
| Automated evidence suggestion incorrect | Allow reviewer rejection; do not treat suggestion as accepted evidence association |
| Partial processing failure | Preserve successfully processed material and explicitly identify failed portions |
| User changes a claim after assessment | Invalidate or supersede the affected assessment as required by lifecycle semantics; do not silently leave a stale result attached to materially changed claim content |
| Later revision of source/evidence | Preserve historical result and establish lineage to the later revision |
| Machine round-trip | Read-back model shall remain logically equivalent and preserve required identity, relationships, provenance, and traceability |

## 11. Acceptance Criteria

### AC-J01-01 — End-to-end workflow

Given a supported article, transcript, or draft containing factual claims, a reviewer can complete the workflow from source intake through claim review, evidence association, assessment, and report generation through the reference application UI.

### AC-J01-02 — Claim identity

Each selected claim has stable identity independent of storage location and machine representation.

### AC-J01-03 — Claim source location

Each selected claim can be traced back to its originating source artifact and relevant source location.

### AC-J01-04 — Evidence identity

Each evidence item has stable identity and retains applicable version or lineage information.

### AC-J01-05 — Explicit evidence association

A reviewer can inspect the explicit association between a claim and each evidence item used for its evaluation.

### AC-J01-06 — Source distinction

The system distinguishes source identity, acquired artifact identity, source authenticity, and source authority where those properties are available.

### AC-J01-07 — Integrity boundary

Successful artifact/evidence integrity verification cannot by itself produce a positive claim assessment.

### AC-J01-08 — Authenticity/authority boundary

Successful source-authenticity assessment cannot by itself establish source authority.

### AC-J01-09 — Assessment states

The workflow can represent support, contradiction, qualification/partial support, and unresolved/insufficient-evidence outcomes where applicable.

### AC-J01-10 — Conflicting evidence

When evidence items have conflicting relationships to a claim, the system preserves the individual relationships and exposes the conflict rather than silently collapsing it.

### AC-J01-11 — Uncertainty

When the evaluation basis is materially uncertain or incomplete, the result explicitly represents the uncertainty or limitation.

### AC-J01-12 — Provenance

A reviewer can reconstruct the relevant origin, acquisition, transformation where applicable, and association history of representative claims and evidence.

### AC-J01-13 — Traceability

A reviewer can traverse from a claim to its evidence, sources/artifacts, provenance, and assessment/evaluation result.

### AC-J01-14 — Explainability

A representative evaluation result exposes sufficient traceable information to explain the material claim, evidence, context, and applicable evaluation basis used to produce it.

### AC-J01-15 — Reproducibility

Repeated evaluation of the same materially relevant inputs, context, applicable rules/policy, and execution conditions produces reproducible results, except for explicitly represented nondeterministic factors permitted by the applicable evaluation semantics.

### AC-J01-16 — Historical preservation

A released or baselined fact-check result remains reconstructable after a later revision to a material source, evidence item, context, or applicable evaluation rule/policy.

### AC-J01-17 — Machine round-trip

A fact-check semantic model written to the supported machine representation and read back produces a logically equivalent model with required identity, relationships, provenance, and traceability preserved.

### AC-J01-18 — Negative cases

The application demonstrates defined behavior for missing sources, insufficient evidence, inaccessible evidence, conflicting evidence, invalid relationships, provenance gaps, partial processing failures, and material user corrections.

### AC-J01-19 — Report completeness

The generated report identifies all selected claims, including unresolved claims, and provides the evidence and assessment basis needed for review.

### AC-J01-20 — UI completeness

All required stages of the workflow are demonstrable through the reference application UI rather than only through backend tests.

## 12. Reference-Core versus Application Responsibilities

| Capability | Placement | Rationale |
|---|---|---|
| Stable identity | Shared ECRA reference core | Reused by all P0 slices |
| Source/artifact representation | Shared ECRA reference core | Common evidence-centric capability |
| Claim representation | Shared ECRA reference core | Directly required across P0 portfolio |
| Evidence representation | Shared ECRA reference core | Directly required across P0 portfolio |
| Typed relationship representation | Shared ECRA reference core | Common semantic requirement |
| Assessment representation | Shared ECRA reference core | Required across P0 slices |
| Provenance/traceability | Shared ECRA reference core | Common auditability requirement |
| Integrity/authenticity/authority metadata boundaries | Shared ECRA reference core | Common trust-property boundary |
| Machine representation / round-trip | Shared ECRA reference core | Explicit P0 capability |
| Evaluation integration contract | Shared core / enabling infrastructure | Required by Gen1 evaluation path without implementing speculative engines |
| Persistence/storage abstraction | Enabling infrastructure | Needed to persist the semantic record while preserving replaceability |
| Claim extraction | VS-J01 application layer / replaceable service | Domain/workflow-specific processing |
| Evidence discovery | VS-J01 application layer / replaceable service | Retrieval strategy is not semantic core |
| Source ranking | VS-J01 application layer | Not justified as a universal core capability |
| Source connectors | Application/integration layer | External dependency and acquisition mechanism are replaceable |
| Source-location extraction | Application/integration layer | Artifact-type-specific behavior |
| Fact-check report presentation | Application layer | Presentation is workflow-specific |
| Reviewer UI workflow | Application layer | User workflow is not semantic core |
| Reviewer comments/corrections | Application layer using core semantics as applicable | User interaction concern, not new root type |

This allocation is an initial slice-derived classification. Promotion into or movement within the shared core shall follow the approved capability-promotion lifecycle.

## 13. Capability Coverage

The following table records the VS-J01 evidence against the current approved capability matrix.

| Capability | J01 classification | Level | Evidence / requirement basis | Initial placement |
|---|:---:|---|---|---|
| Source material registration | D | 1 | Source intake and artifact registration are mandatory workflow steps | Shared core |
| Acquired artifact preservation | D | 1 | Required to preserve the concrete acquired source material | Shared core |
| Source location / citation | D | 1 | Claim/evidence inspection and report require source locations | Shared core + application location handling |
| Stable semantic identity | D | 1 | Claim/evidence identity and traceability requirements | Shared core |
| Claim representation | D | 1 | ECRA-G1-FUN-0001; ECRA-G1-SEM-0001 | Shared core |
| Evidence representation | D | 1 | ECRA-G1-FUN-0003 | Shared core |
| Evidence-to-claim association | D | 1 | ECRA-G1-FUN-0004; ECRA-G1-TRC-0001 | Shared core |
| Typed relationship representation | D | 1 | Explicit claim/evidence relationship | Shared core |
| Support / contradiction / qualification assessment | D | 1 | Approved P0 workflow and capability matrix | Shared core assessment representation; evaluation semantics bounded by authority |
| Unresolved / uncertainty representation | D | 1 | ECRA-G1-EVL-0007 and P0 workflow | Shared core |
| Provenance representation | D | 1 | ECRA-G1-INT-0005; ECRA-G1-SEM-0003 | Shared core |
| Traceability traversal | D | 1 | ECRA-G1-TRC-0001; P0 UI requirement | Shared core + application UI |
| Source version / revision state | D | 1 | Evidence/source lineage and historical preservation | Shared core |
| Artifact integrity information | D | 1 | ECRA-G1-INT-0001; ECRA-G1-INT-0004 | Shared core |
| Source authenticity result | E | 1/2 | ECRA-G1-INT-0002; mechanism may be absent in J01 | Shared core boundary; mechanism replaceable |
| Source authority information | D | 1 | ECRA-G1-INT-0003; credible-source assessment workflow | Shared core representation; application determines relevant authority |
| Transformation provenance | E | 1/2 | May arise from extraction/acquisition processing | Shared provenance contract |
| Machine-readable representation | D | 1 | P0 round-trip requirement | Shared core |
| Semantic round-trip preservation | D | 1 | P0 completion criterion | Shared core |
| Structured assessment result | D | 1 | Evaluation/result workflow | Shared core |
| Report generation | D | 1 | Fact-check report is required user-facing outcome | Application layer |
| UI source selection / ingestion | D | 1 | P0 UI demonstration | Application layer |
| UI claim / observation inspection | D | 1 | P0 UI demonstration | Application layer |
| UI evidence inspection | D | 1 | P0 UI demonstration | Application layer |
| UI relationship inspection | D | 1 | P0 UI demonstration | Application layer |
| UI provenance / location inspection | D | 1 | P0 UI demonstration | Application layer |
| UI assessment / uncertainty inspection | D | 1 | P0 UI demonstration | Application layer |
| UI traceability navigation | D | 1 | P0 UI demonstration | Application layer |
| UI report inspection | D | 1 | P0 UI demonstration | Application layer |
| Validation/conformance integration boundary | E | 2 | Required boundary, not full validation engine | Shared core integration boundary |
| Verification integration boundary | E | 2 | Acceptance/verification evidence must connect to slice | Shared core integration boundary |
| Deterministic validation of required input structure | D | 1/2 | Claim eligibility and input validation | Shared core contract + application validation |
| Reproducible processing record | E | 2 | Required to support reproducibility and replay | Shared enabling infrastructure |
| Generic search engine | — | 3 | Explicitly out of scope | Deferred |
| Universal reasoning engine | — | 3 | Explicitly out of scope | Deferred |
| Generic ontology inference | — | 3 | Explicitly out of scope | Deferred |
| Graph-database dependence | — | 3 | Explicitly out of scope | Deferred |
| Universal query language | — | 3 | Explicitly out of scope | Deferred |
| General workflow engine | — | 3 | Explicitly out of scope | Deferred |
| Distributed microservice architecture | — | 3 | Explicitly out of scope | Deferred |
| AI-specific semantic core | — | 3 | P2/Future boundary | Deferred |

### 13.1 Matrix refinement candidates

VS-J01 does not currently provide sufficient evidence to promote any Level 3 capability.

The slice may provide future evidence for more specific reusable capabilities, such as a generic source-location abstraction or a common evidence-discovery interface, but those should not be promoted solely from this slice. Promotion requires evidence under the approved lifecycle.

## 14. Security, Privacy, and Operational Considerations

### 14.1 Source sensitivity

Articles, transcripts, drafts, and evidence may include confidential, embargoed, personal, copyrighted, or otherwise sensitive material. The slice shall treat source handling as controlled application behavior and shall not assume unrestricted public availability.

### 14.2 Access control

Where access restrictions apply, the application shall preserve the distinction between:

- inability to access evidence;
- absence of evidence;
- evidence that was accessed but found insufficient.

These states shall not be conflated in assessment.

### 14.3 Provenance integrity

Material provenance records shall be protected against silent alteration. Released/baselined fact-check records shall retain their historical basis according to applicable lifecycle requirements.

### 14.4 Reproducibility

The application shall preserve sufficient processing and input state to reproduce representative results under equivalent conditions.

### 14.5 External dependencies

Evidence discovery and source acquisition may depend on external services. The slice shall isolate such dependencies behind replaceable interfaces or application-level boundaries and shall preserve the identity/provenance of the resulting material.

No specific external search provider is required by this specification.

### 14.6 Failure isolation and observability

The application shall make partial failures observable and shall avoid allowing an external acquisition or processing failure to silently corrupt an existing semantic record.

Operational implementation details remain outside this slice specification unless demonstrated by the workflow.

## 15. Explicit Exclusions

The following are deliberately excluded from VS-J01:

- implementation of a universal web crawler;
- implementation of a universal search engine;
- autonomous source credibility ranking as an ECRA core capability;
- universal truth scoring;
- generic reasoning or inference engines;
- automated theological, legal, or scientific reasoning;
- generalized multi-tenant infrastructure;
- distributed deployment architecture;
- AI-generated-content semantics;
- generalized editorial workflow management;
- publication approval/governance beyond what is needed to demonstrate the fact-check result;
- a complete ECRA validation/conformance engine;
- a complete ECRA verification/proof engine;
- concrete interchange formats or protocols beyond the minimum implementation contract required to demonstrate semantic round-trip behavior.

## 16. Implementation and Evolution Constraints

### 16.1 Technology independence

The logical contracts in this specification shall not depend on a particular programming language, database, message broker, search provider, or deployment topology.

### 16.2 Replaceability

Claim extraction, evidence discovery, source acquisition, document parsing, and report presentation shall be replaceable without changing the ECRA semantic contracts.

### 16.3 Cohesive responsibilities

The implementation should maintain clear boundaries among:

- semantic representation;
- persistence;
- source acquisition;
- document processing;
- evidence discovery;
- assessment/evaluation;
- UI/report presentation.

### 16.4 Future decomposition

The initial implementation may be a modular application. Its internal contracts should permit future decomposition into separate processes or services without avoidable changes to the ECRA semantic model.

This is a future evolution constraint, not a current microservice requirement.

### 16.5 Determinism

Where the workflow uses deterministic processing, the same materially relevant inputs and processing configuration should produce reproducible results. Nondeterministic factors shall not be hidden when they materially affect interpretation.

## 17. Design / Implementation Traceability

The VS-J01 specification shall trace to the approved framework and requirements as follows:

| Traceability target | Reference |
|---|---|
| Vertical-slice definition | Approved ECRA Reference Application — Vertical Slice Portfolio, VS-J01 |
| Common specification structure | Approved ECRA Reference Application — P0 Vertical Slice Specification Framework |
| Capability derivation | Approved ECRA Reference Implementation — Cross-Slice Capability Matrix |
| Claim representation | ECRA-G1-FUN-0001; ECRA-G1-SEM-0001 |
| Claim eligibility | ECRA-G1-FUN-0002 |
| Evidence representation | ECRA-G1-FUN-0003 |
| Evidence-to-claim association | ECRA-G1-FUN-0004 |
| Evidence integrity | ECRA-G1-INT-0001; ECRA-G1-INT-0004 |
| Evidence identity/lineage | ECRA-G1-SEM-0002 |
| Source representation | ECRA-G1-FUN-0005 |
| Source authenticity | ECRA-G1-INT-0002 |
| Source authority | ECRA-G1-INT-0003 |
| Provenance | ECRA-G1-INT-0005; ECRA-G1-SEM-0003 |
| Integrity boundary | ECRA-G1-INT-0006 |
| Authenticity/authority boundary | ECRA-G1-INT-0007 |
| Claim/evidence traceability | ECRA-G1-TRC-0001; ECRA-G1-TRC-0002 |
| Evaluation context | ECRA-G1-FUN-0007; ECRA-G1-SEM-0004; ECRA-G1-SEM-0005 |
| Evaluation result | ECRA-G1-EVL-0002; ECRA-G1-EVL-0003 |
| Evaluation basis | ECRA-G1-EVL-0004 |
| Deterministic evaluation | ECRA-G1-EVL-0005 |
| Evaluation explainability | ECRA-G1-EVL-0006 |
| Explicit uncertainty | ECRA-G1-EVL-0007 |
| Historical result preservation | ECRA-G1-EVL-0009 |
| Evaluation traceability | ECRA-G1-TRC-0003; ECRA-G1-TRC-0004 |
| Engineering continuity | ECRA-G1-TRC-0005 onward where applicable |
| ADL semantic preservation boundary | Approved ECRA-1200 ADL architecture/design documents where applicable |

This document elaborates approved requirements for VS-J01. It does not redefine those requirements.

## 18. Verification Strategy

Verification shall be performed at multiple levels.

### 18.1 Contract verification

Verify that the logical input/output contracts, semantic object identities, required relationships, and required states are represented as specified.

### 18.2 Integration verification

Verify that source intake, claim representation, evidence representation, relationship creation, provenance, assessment, and report generation operate together through the reference application.

### 18.3 Negative verification

Verify that integrity does not imply truth, authenticity does not imply authority, missing evidence does not imply contradiction, and incomplete processing does not produce a falsely successful result.

### 18.4 Traceability verification

Verify forward and reverse traversal of representative claim/evidence/source/provenance/result relationships.

### 18.5 Replay / reproducibility verification

Verify repeatability of representative evaluations and reconstruction of released/baselined results after later revisions.

### 18.6 Representation verification

Verify semantic round-trip behavior:

```text
Logical fact-check model
        ↓
Supported machine representation
        ↓
Read-back
        ↓
Logically equivalent fact-check model
```

The comparison shall concern semantic equivalence, including required identities, relationships, provenance, traceability, and assessment information. Byte-for-byte serialization equality is not required.

### 18.7 UI-backed end-to-end verification

At least one representative complete fact-check scenario shall be executed through the reference application UI, including source intake, claim review, evidence review, assessment, traceability inspection, and report generation.

## 19. Deliverable and Completion Definition

VS-J01 is complete only when the following artifacts/evidence exist:

1. an approved detailed slice specification;
2. representative source material and acquired-artifact record;
3. representative selected claims;
4. representative evidence items and source records;
5. explicit claim/evidence relationships;
6. provenance and source-location records;
7. assessment/evaluation results including an unresolved case;
8. negative/boundary-case demonstrations;
9. machine representation round-trip evidence;
10. UI-backed end-to-end demonstration;
11. a generated fact-check report;
12. capability-matrix evidence sufficient to support any justified refinement.

Completion does not require implementation of capabilities classified as Level 3 or otherwise deferred.

## 20. Open / Deferred Items

The following are deliberately not resolved by this slice:

1. final canonical relationship names and inverse rules where the applicable relationship authority remains pending;
2. detailed evaluation-policy/rule representation;
3. complete uncertainty semantics and scoring, if any;
4. concrete machine serialization schema;
5. generalized source-discovery/search architecture;
6. complete verification/conformance methodology;
7. generalized external-source monitoring or change-detection service;
8. domain-specific source credibility/ranking methodology.

Where these items affect the implementation, the slice shall use the approved current contract and record any dependency rather than inventing a competing semantic rule.

## 21. Status

This specification is submitted for review. It defines the detailed implementation-driving requirements and acceptance boundary for VS-J01 — Investigative Fact Check. It does not itself constitute an implementation approval.
