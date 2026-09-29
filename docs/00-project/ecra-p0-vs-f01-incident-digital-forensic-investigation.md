# ECRA Reference Application — VS-F01 Incident / Digital Forensic Investigation

> Status: REVIEW
> Authority: ENGINEERING / INFORMATIVE
> Generation: GEN1
> Scope: Detailed P0 vertical-slice specification for Incident / Digital Forensic Investigation
> Matrix Basis: Current ECRA Reference Implementation — Cross-Slice Capability Matrix
> Portfolio Basis: Approved ECRA Reference Application — Vertical Slice Portfolio

## 1. Purpose and Scope

### 1.1 Purpose

VS-F01 defines an evidence-first investigation workflow for digital incidents. Given logs, reports, communications, system artifacts, acquired forensic artifacts, and other authorized investigative material, the workflow identifies observations and candidate investigative claims or hypotheses, associates relevant evidence, preserves provenance and artifact integrity information, correlates material events where applicable, evaluates competing hypotheses, and produces an auditable investigation report.

The slice demonstrates that the ECRA reference implementation can support an evidence-first workflow in which evidence precedes or drives claim/hypothesis formulation. It exercises the same domain-neutral claim/evidence/provenance/assessment capabilities used by the earlier P0 slices while introducing forensic requirements around artifact acquisition, integrity, source state, temporal correlation, evidence handling, and reconstruction.

### 1.2 Intended Users

Primary users include:

- digital forensic analysts;
- incident responders;
- security investigators;
- incident investigation leads;
- authorized security or assurance analysts;
- technical investigators working with authorized forensic material.

The slice does not prescribe a particular forensic methodology, incident-response standard, jurisdictional evidentiary rule, or professional certification framework.

### 1.3 Workflow Boundary

The workflow begins with an authorized incident context and one or more forensic artifacts, reports, communications, logs, or acquisition inputs. It ends with:

- identified observations and candidate claims/hypotheses;
- explicit evidence associations;
- artifact/source locations;
- integrity and acquisition information where available;
- provenance and handling history;
- temporal relationships and investigation timeline information where applicable;
- support, contradiction, qualification, or unresolved assessments;
- competing hypotheses and evidence gaps;
- an auditable investigation report.

### 1.4 Investigation Neutrality

The application shall distinguish:

1. what an artifact or source contains;
2. what was observed or derived from that material;
3. which claim or hypothesis the observation/evidence bears upon;
4. what assessment follows within the declared investigation scope; and
5. any downstream operational, disciplinary, legal, or attribution decision.

Integrity, authenticity, source authority, tool output, temporal proximity, or artifact type shall not automatically establish the truth of an investigative claim.

### 1.5 Non-Goals

VS-F01 does not establish:

- legal conclusions;
- criminal or civil liability determinations;
- identification of a person as legally responsible;
- autonomous attacker attribution;
- autonomous incident-response actions;
- autonomous containment, eradication, or recovery;
- a general-purpose SIEM;
- a universal log-management platform;
- a malware reverse-engineering engine;
- a sandbox execution platform;
- a universal threat-intelligence platform;
- a general-purpose search engine;
- unrestricted collection or crawling;
- a generalized digital-forensics ontology;
- a new ECRA semantic root type for Incident, Case, Device, Host, User, Account, Process, Malware, Indicator, Attack, Tactic, Technique, or Finding;
- a mandatory numeric evidence-strength or confidence score;
- a generalized workflow/orchestration engine;
- distributed microservice architecture;
- implementation of every ECRA semantic capability.

Forensic-domain concepts not owned by an applicable ECRA specification remain application-level classifications, references, or views over the shared semantic model.

### 1.6 Assumptions and Known Limitations

Forensic material may be:

- incomplete;
- duplicated;
- corrupted;
- partially acquired;
- unavailable;
- encrypted;
- redacted;
- time-skewed;
- overwritten;
- collected using different tools;
- derived through multiple transformations;
- missing expected telemetry;
- supplied without independent verification.

The workflow shall represent such limitations explicitly. It shall not silently infer missing events, normalize conflicting timestamps without recording the transformation, or treat absent telemetry as proof that an event did not occur.

---

## 2. Scenario and Preconditions

### 2.1 Primary Scenario

An authorized investigator receives a collection of forensic artifacts and supporting material following a suspected digital incident.

The application:

1. establishes the investigation context and scope;
2. registers sources and acquired artifacts;
3. records acquisition and integrity information where available;
4. identifies observations and candidate claims/hypotheses;
5. records precise artifact or document locations;
6. associates evidence with claims or hypotheses;
7. correlates evidence across artifacts and time where appropriate;
8. preserves competing explanations;
9. assesses support, contradiction, qualification, or unresolved state;
10. records provenance, handling, versions, and reviewer actions;
11. generates an auditable investigation report.

### 2.2 Example Investigation Questions

The application may support questions such as:

- What material observations are present in the acquired artifacts?
- Which observations support or contradict each investigative hypothesis?
- What evidence indicates that a particular event occurred?
- What evidence is consistent with multiple competing explanations?
- Which artifacts corroborate an observed event?
- Which evidence depends on a transformation, parser, extraction tool, or derived artifact?
- What artifact versions and acquisition states were actually reviewed?
- What is the reconstructed temporal sequence within the available evidence?
- Which expected telemetry is missing or unavailable?
- Which hypotheses remain unresolved?
- What provenance and integrity information underlies each assessment?

These are evidence-review questions, not legal or attribution conclusions.

### 2.3 Required Inputs

The minimum workflow input is:

- an authorized investigation context;
- a defined investigation scope;
- one or more forensic artifacts, source records, reports, communications, or supported acquisition inputs.

The exact representation of an incident remains application-specific unless an applicable ECRA specification establishes a canonical representation.

### 2.4 Optional Inputs

Optional inputs may include:

- incident identifier;
- investigation identifier;
- affected-system identifiers;
- source identifiers;
- artifact identifiers;
- acquisition metadata;
- acquisition timestamps;
- collection method metadata;
- artifact hashes or other integrity metadata;
- tool and tool-version metadata;
- analyst questions;
- candidate hypotheses;
- existing observations;
- expected event windows;
- timezone information;
- known clock-offset information;
- communications or reports;
- selected artifact locations;
- external reference material;
- prior investigation results;
- reviewer notes.

Optional metadata does not become evidence merely because it was supplied.

### 2.5 Initial System and Access Preconditions

Before evidence processing begins:

- the investigator shall have appropriate authorization;
- the review scope shall be established;
- accessible sources and unavailable sources shall be distinguishable;
- acquired artifacts shall retain their acquisition identity where available;
- applicable integrity information shall be preserved;
- processing shall not silently overwrite the original acquired representation.

Where a source cannot be accessed or an artifact cannot be acquired, the system shall represent the limitation rather than claiming that the source was inspected.

### 2.6 Artifact Availability States

A forensic artifact may be:

- available;
- partially available;
- inaccessible;
- corrupted;
- encrypted;
- redacted;
- superseded;
- duplicated;
- historical;
- deleted or otherwise unavailable;
- acquired but not independently verified;
- acquired with integrity metadata;
- acquired without applicable integrity metadata.

The state shall remain distinguishable from the substantive assessment of any claim.

---

## 3. End-to-End Workflow

```text
Authorized incident context + investigation scope
    ↓
Source / artifact intake and registration
    ↓
Acquire or register forensic artifacts
    ↓
Preserve artifact identity, integrity, and acquisition provenance
    ↓
Identify observations / candidate claims / hypotheses
    ↓
Locate observations and evidence in artifacts
    ↓
Associate evidence with claims / hypotheses
    ↓
Correlate evidence across artifacts and time
    ↓
Compare competing hypotheses and evidence
    ↓
Assess support / contradiction / qualification / unresolved state
    ↓
Record provenance, handling, versions, transformations, and limitations
    ↓
Construct investigation timeline / finding set
    ↓
Generate auditable investigation report
    ↓
Investigator inspection and follow-up
```

### 3.1 Investigation Scope

The investigator establishes:

- incident context;
- investigation purpose;
- artifact corpus;
- time window where applicable;
- systems or environments in scope;
- investigation questions;
- processing constraints;
- applicable review criteria.

Scope is contextual information and does not automatically become an investigative claim.

### 3.2 Source and Artifact Registration

Each material source or acquired artifact shall preserve applicable:

- stable identity;
- source identity;
- artifact identity;
- acquisition state;
- acquisition timestamp;
- version/revision or lineage;
- location;
- provenance;
- integrity information;
- authenticity information where applicable;
- authority/context information where applicable.

An original acquired artifact shall remain distinguishable from transformed, parsed, extracted, normalized, or derived representations.

### 3.3 Acquisition and Preservation

Where the application receives an acquired artifact, it shall preserve the acquired representation sufficiently to support later integrity, provenance, traceability, and reconstruction.

Acquisition metadata may include:

- acquisition source;
- acquisition timestamp;
- acquisition method;
- collection scope;
- acquisition tool and version;
- integrity or fingerprint information;
- acquisition status;
- operator identity where available;
- transformation history after acquisition.

Concrete acquisition technology is outside this slice specification.

### 3.4 Observation Identification

The application may derive or receive observations from:

- system logs;
- authentication records;
- network records;
- endpoint telemetry;
- file-system artifacts;
- configuration snapshots;
- application logs;
- cloud or service records;
- communications;
- reports;
- memory or process artifacts;
- other authorized forensic material.

A forensic observation is an application-level representation of information extracted or identified from evidence. It does not establish a new ECRA semantic root type.

Observations shall preserve:

- stable identity;
- originating artifact/source;
- precise location where available;
- extraction/transformation provenance;
- relevant timestamp information;
- applicable version state;
- processing context.

### 3.5 Candidate Claims and Hypotheses

An investigative hypothesis is represented as an identifiable claim/proposition subject to evidence evaluation.

Examples include:

- a particular event occurred within the declared scope;
- a sequence of observed events is consistent with a proposed explanation;
- an artifact indicates a particular system state;
- one of several competing explanations is supported by the available evidence.

Hypotheses remain propositions under evaluation. The application shall not establish a new semantic root type for Hypothesis.

### 3.6 Evidence Identification and Registration

Relevant evidence may include:

- original or acquired artifacts;
- artifact portions;
- logs and log records;
- communications;
- endpoint records;
- network records;
- system-state records;
- configuration records;
- reports;
- derived artifacts;
- corroborating observations;
- evidence obtained through explicit evidence chains.

Evidence shall remain explicitly associated with the claims or hypotheses for which it is relevant.

### 3.7 Evidence Location

The application shall support precise or sufficiently precise locations such as:

- file path;
- artifact identifier;
- byte or record offset;
- log record;
- event identifier;
- timestamp;
- packet or flow reference;
- database record;
- message identifier;
- document page or text span;
- other supported source-specific location.

A location identifies where information occurs; it does not replace the semantic identity of the source or artifact.

### 3.8 Evidence Correlation

Evidence may be correlated across:

- multiple artifacts;
- multiple sources;
- multiple observations;
- time ranges;
- related versions;
- acquisition states;
- explicit evidence chains.

Correlation shall remain traceable to the underlying evidence. Similar timestamps, matching keywords, or co-location alone shall not silently establish a substantive relationship.

### 3.9 Temporal Correlation

Where temporal reasoning is material, the application shall preserve:

- source timestamp;
- timestamp semantics where known;
- timezone or offset;
- clock-offset information where available;
- normalized/display timestamp where a transformation is applied;
- transformation provenance;
- source/version context.

Normalization shall not overwrite the original temporal representation.

Conflicting timestamps shall remain visible and traceable.

### 3.10 Assessment

The assessment representation shall support:

- supported;
- contradicted;
- partially supported or qualified;
- unresolved;
- insufficient evidence.

An assessment is relative to the declared investigation scope and evidence available at the relevant time.

It is not a legal conclusion, attribution determination, or operational command.

### 3.11 Evidence-Strength Characterization

Where the investigation model characterizes evidentiary strength, the characterization shall be explicit, criteria-based, and traceable.

Forensic evidence that may warrant stronger characterization can include, depending on the declared criteria:

- independently verified artifact-integrity information;
- authenticated source material;
- corroboration across independently acquired sources;
- reproducible derivation from recorded source material;
- logically derived conclusions supported by valid proof or transformation steps.

A log line, analyst statement, or eyewitness account shall not be treated as strong evidence merely because it exists or is attributed. Conversely, no evidence type shall be assigned an absolute strength independent of context, provenance, integrity, relevance, and the applicable evaluation criteria.

The report shall expose the evidence basis, verification or derivation, provenance, relevant limitations, and applicable criteria whenever evidentiary strength is characterized.

### 3.12 Competing Hypotheses

The application shall preserve multiple hypotheses where the evidence permits more than one explanation.

For each material hypothesis, the report should identify:

- hypothesis statement;
- supporting evidence;
- contradicting evidence;
- qualifying evidence;
- unresolved evidence;
- temporal implications;
- provenance;
- limitations;
- current assessment state.

The application shall not silently select one hypothesis merely because it is displayed first, generated first, or associated with a preferred source.

### 3.13 Human Review and Correction

Investigators may:

- correct observations;
- add observations;
- add or revise hypotheses;
- change evidence associations;
- identify missing artifacts;
- correct artifact locations;
- revise temporal interpretations;
- revise assessments;
- add review notes.

A material reviewer correction or justification shall be represented as a reviewer-originated claim/assertion with explicit provenance rather than as an unqualified state change.

Where the correction or justification makes a substantive proposition, that proposition shall be assessable against supporting evidence where applicable.

Material changes shall preserve:

- reviewer identity where available;
- timestamp;
- prior state;
- revised state;
- justification;
- supporting evidence where applicable;
- assessment state where applicable;
- provenance.

Reviewer-generated claims and corrections shall remain distinguishable from source-originated claims and shall not automatically override them.

### 3.14 Transformation and Derived Evidence

Processing may transform source material into derived representations, such as:

- parsed log records;
- extracted text;
- normalized timestamps;
- decoded records;
- generated indexes;
- correlated observations;
- derived evidence records.

Every material transformation shall preserve sufficient provenance to identify:

- input artifact(s);
- transformation operation or processing stage;
- processing tool/version where available;
- processing timestamp where material;
- output artifact/observation identity;
- relevant configuration or parameters where reproducibility requires them.

Derived evidence shall not be represented as though it were the original acquired artifact.

### 3.15 Investigation Timeline / Finding Set

The application may present a timeline or finding set composed from the evidence and assessments.

A timeline entry or finding is a presentation/application-level result unless an applicable ECRA specification establishes otherwise.

Each material timeline entry shall remain traceable to the source observations/evidence from which it was derived.

The timeline shall distinguish:

- observed event information;
- inferred or derived event information;
- uncertain timing;
- conflicting timing;
- missing expected events.

### 3.16 Report Generation

The report shall show, as applicable:

- investigation scope;
- source and artifact inventory;
- acquisition and integrity information;
- material observations;
- candidate claims/hypotheses;
- evidence and precise locations;
- evidence relationships;
- competing hypotheses;
- assessments;
- investigation timeline or finding set;
- provenance and transformation history;
- limitations and evidence gaps;
- reviewer actions and corrections;
- unresolved questions;
- report generation/provenance information.

The report shall not present legal conclusions, criminal attribution, guilt, innocence, liability, or operational commands as if they were established by the evidence-review workflow.

---

## 4. Semantic Object Requirements

### 4.1 Investigation Context

Represents the application-level incident/investigation scope, purpose, corpus, temporal scope, reviewer context, and evaluation criteria.

It reuses applicable ECRA context semantics and is not a new portfolio-wide root type.

### 4.2 Source

Represents an identifiable origin from which information or forensic material is obtained or attributed.

It preserves stable identity and applicable source metadata, provenance, authenticity, authority/context, and source-state information.

### 4.3 Acquired Artifact

Represents material actually acquired or received by the system.

It preserves:

- stable identity;
- acquisition provenance;
- version/revision or lineage;
- integrity information where available;
- relationship to source;
- acquisition state.

The acquired artifact is distinct from an abstract source and from derived representations.

### 4.4 Forensic Artifact

A forensic artifact is an application-level contextual classification of an acquired artifact or source material relevant to the investigation.

Examples include:

- log files;
- event records;
- disk images;
- memory captures;
- configuration snapshots;
- network records;
- endpoint telemetry;
- application records;
- communications.

It does not establish a new ECRA semantic root type.

### 4.5 Observation

An observation is an application-level representation of information identified in or derived from evidence.

It shall preserve:

- stable identity;
- source/artifact origin;
- location;
- extraction/transformation provenance;
- applicable temporal information;
- version/lineage where applicable.

An observation is not automatically a claim about why the observed information exists.

### 4.6 Claim / Hypothesis

Represents an identifiable proposition submitted for investigation.

A hypothesis is a contextual classification of a claim. It does not establish a separate ECRA semantic root type.

The claim/hypothesis preserves:

- stable identity;
- proposition content;
- origin/provenance;
- applicable source locations;
- evidence relationships;
- assessment state;
- version/lineage where applicable.

### 4.7 Evidence

Represents information relevant to determining whether, or to what extent, a claim or hypothesis is established within the declared investigation scope.

It preserves:

- stable identity;
- source/artifact;
- location;
- version/lineage where applicable;
- provenance;
- integrity/authenticity/authority information where applicable.

### 4.8 Evidence Relationship

Represents an explicit association between evidence and the claim/hypothesis for which it is relevant.

Concrete relationship names and detailed domain/range rules shall be taken from authoritative ECRA relationship semantics.

### 4.9 Assessment / Evaluation Result

Represents the assessment of a claim/hypothesis relative to available evidence and the declared investigation context.

It remains distinct from:

- artifact integrity;
- source authenticity;
- source authority;
- provenance completeness;
- analyst identity;
- tool identity;
- temporal normalization;
- operational response;
- legal conclusion;
- attacker attribution.

### 4.10 Artifact Location

Identifies where evidence occurs within an artifact or source.

It may identify a file path, record, offset, event identifier, packet/flow reference, timestamp, message identifier, or other supported location.

A location is a reference into an artifact/source and does not replace artifact identity.

### 4.11 Acquisition / Handling Provenance

Represents provenance of acquisition, registration, transformation, handling, and material reviewer actions.

Where applicable it shall support a chain-of-custody-style history without creating a new ECRA semantic root type.

The implementation shall preserve the distinction between:

- original/acquired material;
- derived material;
- handling metadata;
- reviewer assertions.

### 4.12 Integrity, Authenticity, and Authority

The Gen1 boundaries shall remain distinct:

- integrity concerns whether acquired information has been altered or corrupted under the applicable mechanism;
- authenticity concerns whether source/artifact identity or attribution is genuine under the applicable mechanism;
- authority concerns the basis for considering a source appropriate for the relevant evaluation.

None of these properties alone establishes the truth of a hypothesis.

### 4.13 Processing / Transformation Record

A transformation record identifies material processing that changes or derives information from an artifact.

It is an application-level provenance construct unless an applicable ECRA specification establishes otherwise.

It should preserve input identity, output identity, processing operation, tool/version where available, processing time where material, and relevant parameters needed for reconstruction.

---

## 5. Relationship Requirements

### 5.1 Required Relationship Families

The workflow requires relationships corresponding to:

- investigation-context association with source/artifact material;
- artifact origin from source;
- observation origin from artifact/source;
- claim/hypothesis origin;
- evidence origin from source/artifact;
- evidence bearing on claim/hypothesis;
- observation supporting or qualifying a claim where applicable;
- claim derivation where applicable;
- provenance/handling association;
- transformation lineage;
- version/lineage;
- assessment association;
- artifact-location association;
- temporal association where applicable.

Concrete relationship names shall be taken from authoritative ECRA relationship semantics.

### 5.2 Relationship Identity

Every material relationship shall have identifiable semantic endpoints.

Filenames, hostnames, timestamps, event identifiers, hashes, database rows, textual similarity, or UI labels shall not substitute for semantic identity.

### 5.3 Multiplicity

The slice supports:

- multiple artifacts per investigation;
- multiple observations per artifact;
- multiple evidence items per claim/hypothesis;
- one evidence item relevant to multiple claims/hypotheses;
- multiple hypotheses for the same observation set;
- multiple artifacts corroborating one hypothesis;
- multiple artifact versions;
- multiple assessments across investigation revisions.

### 5.4 Competing Hypotheses

Competing hypotheses shall remain independently identifiable.

Evidence may support one hypothesis while contradicting another.

The system shall not collapse competing hypotheses merely because they refer to the same incident, event window, or artifact.

### 5.5 Evidence Chains

An evidence chain may be:

```text
Hypothesis A
  → Observation B
  → Acquired Artifact C
  → Source D
```

or:

```text
Hypothesis A
  → Derived Evidence B
  → Transformation C
  → Acquired Artifact D
```

The chain remains traversable.

Evidence reached through a chain does not automatically establish every intermediate proposition.

### 5.6 Temporal Relationships

Where material, claims, evidence, observations, and artifacts shall preserve:

- source timestamps;
- time ranges;
- timezone/offset;
- clock-offset metadata where available;
- normalized representations;
- temporal transformation provenance.

Temporal correlation shall preserve original values and shall not silently normalize conflicts.

### 5.7 Version and Lineage Relationships

When an artifact, observation, or derived evidence representation changes:

- prior versions remain identifiable where retention permits;
- the new representation has distinct version/lineage information;
- prior assessments remain associated with the source state on which they were based;
- affected claims/hypotheses may be reassessed.

### 5.8 Acquisition and Handling Traceability

Where handling history is material, the traceability path shall permit reconstruction of:

```text
Source
  → Acquisition
  → Acquired Artifact
  → Integrity / Authenticity Information
  → Transformation / Handling
  → Derived Observation / Evidence
  → Claim / Hypothesis
  → Assessment
```

The implementation need not use a specific chain-of-custody product or repository.

### 5.9 Independence and Corroboration

Where the investigation characterizes evidence as corroborating or independent, the basis for that characterization shall be recorded.

Shared upstream provenance, duplicated acquisition, or a common source shall not be silently represented as independent corroboration.

---

## 6. Evidence and Assessment Requirements

### 6.1 Evidence Sources

Evidence may originate from:

- acquired system artifacts;
- logs;
- endpoint records;
- network records;
- communications;
- reports;
- configuration state;
- memory or process artifacts;
- cloud/service records;
- derived artifacts;
- reviewer-supplied material.

Evidence source type remains descriptive context.

### 6.2 Artifact Integrity

Where an applicable integrity mechanism exists, the system shall preserve the information necessary to reproduce or assess the artifact-integrity determination.

Examples may include hashes, signatures, or equivalent integrity metadata when supplied or generated by an applicable mechanism.

Integrity success shall not be converted automatically into a positive hypothesis assessment.

### 6.3 Source Authenticity

Where supported, source authenticity assessment shall be preserved with its basis.

Authenticity shall remain distinct from authority and substantive truth.

### 6.4 Source Authority

Authority information shall identify the basis on which a source is considered appropriate for the relevant investigation or evaluation.

Source authority shall not be inferred merely from source availability or artifact integrity.

### 6.5 Evidence Relevance

Evidence relevance shall be represented explicitly.

The system shall not infer relevance solely from:

- common host;
- common timestamp;
- keyword match;
- filename;
- physical co-location;
- similar text;
- identical labels.

### 6.6 Support

Evidence supports a claim/hypothesis when, within the declared criteria and scope, it materially bears in favor of the proposition.

The report shall identify the evidence and relevant locations.

### 6.7 Contradiction

Contradiction requires materially incompatible relevant evidence.

It shall not be inferred merely because:

- an expected artifact is absent;
- telemetry is unavailable;
- timestamps differ without semantic comparison;
- a source has lower authority;
- an analyst prefers another explanation;
- a hypothesis is unpopular or unexpected.

### 6.8 Qualification / Partial Support

Evidence may support only part of a hypothesis or establish a narrower proposition.

The application shall allow:

- supported portions;
- unsupported portions;
- qualifying conditions;
- evidence;
- locations;
- temporal limitations.

### 6.9 Unresolved / Insufficient Evidence

A hypothesis may remain unresolved because:

- evidence is insufficient;
- artifacts are unavailable;
- relevant telemetry is missing;
- evidence conflicts;
- timestamps cannot be reconciled;
- source authenticity remains unresolved;
- acquisition integrity cannot be established;
- the investigation scope is insufficient.

Absence of evidence shall not automatically become contradiction.

### 6.10 Evidence Gaps

The report shall distinguish:

- evidence found;
- evidence not found;
- evidence expected but unavailable;
- evidence known to exist but inaccessible;
- evidence excluded from scope;
- evidence lost or overwritten;
- evidence whose integrity cannot be established.

Evidence gaps shall remain explicit rather than being converted into unsupported conclusions.

### 6.11 Derived Evidence

Derived evidence shall preserve transformation provenance and remain distinguishable from source/acquired material.

The application shall permit the investigator to trace derived evidence back to its inputs and processing steps.

### 6.12 Corroboration and Independence

Where evidence is characterized as corroborating or independent, the report shall identify the underlying sources and the basis for that characterization.

Corroboration shall not be inferred merely because two records contain similar content if they derive from the same upstream source or transformation.

### 6.13 Temporal Evidence

Temporal evidence shall preserve original source time information.

Where timestamps are normalized, the report shall expose:

- original timestamp;
- normalized timestamp;
- normalization rule or transformation;
- timezone/offset;
- clock-offset assumption where applicable;
- provenance.

### 6.14 Evidence Strength

Evidence strength, when used, shall be a transparent assessment property rather than an intrinsic property of an artifact category.

The report shall identify the criteria and evidence basis.

Evidence with independently verifiable integrity, authentic source material, independent corroboration, or reproducible derivation may receive a stronger characterization when the declared criteria justify it.

No evidence type shall receive an absolute strength solely because of its category.

### 6.15 Human Assessment and Correction

Human assessments and corrections shall preserve:

- reviewer identity where available;
- timestamp;
- prior state;
- revised state;
- justification;
- supporting evidence where applicable;
- assessment provenance.

A material correction or justification that contains a substantive proposition shall be represented as a reviewer-originated claim/assertion and may itself be assessed.

### 6.16 Tool Output

Tool-generated observations or extracted records shall remain distinguishable from source material.

The report shall preserve applicable:

- tool identity;
- tool version;
- processing timestamp;
- transformation provenance;
- configuration or parameters where required for reconstruction.

Tool output does not become authoritative merely because it was produced by a forensic tool.

### 6.17 Analyst Notes

Analyst notes may contain observations, claims, interpretations, or review actions.

They shall be classified appropriately and shall not automatically become evidence merely because an analyst entered them.

### 6.18 Downstream Decision Boundary

The evidence-review workflow shall not silently convert an assessment into:

- containment authorization;
- remediation command;
- disciplinary action;
- legal conclusion;
- criminal attribution;
- definitive attacker identity.

Such downstream decisions remain outside this slice.

---

## 7. Provenance and Traceability

### 7.1 Required Provenance

The workflow shall preserve provenance for:

- investigation context;
- source registration;
- artifact acquisition;
- artifact version;
- integrity assessment;
- authenticity assessment where applicable;
- observation extraction;
- evidence association;
- claim/hypothesis creation;
- transformation;
- temporal normalization;
- reviewer corrections;
- assessments;
- report generation.

### 7.2 Investigation Traceability Path

A representative traceability path is:

```text
Investigation Scope
    ↓
Source
    ↓
Acquired Artifact
    ↓
Artifact Location
    ↓
Observation / Evidence
    ↓
Claim / Hypothesis
    ↓
Assessment
    ↓
Report
```

Where transformation occurs:

```text
Source
    ↓
Acquired Artifact
    ↓
Transformation
    ↓
Derived Artifact / Observation / Evidence
    ↓
Claim / Hypothesis
    ↓
Assessment
```

### 7.3 Acquisition Provenance

Acquisition provenance shall identify, where available:

- source;
- acquisition time;
- acquisition method;
- collection scope;
- operator;
- acquisition tool/version;
- integrity information;
- acquisition status.

### 7.4 Transformation Provenance

Material transformations shall identify:

- input;
- output;
- transformation;
- processing component/tool;
- version;
- time;
- relevant configuration/parameters where needed.

### 7.5 Handling History

Where material to the investigation, handling history shall preserve enough information to establish which artifact representation was processed and when.

The implementation shall not silently replace an acquired artifact with a transformed representation.

### 7.6 Temporal Reconstruction

Temporal reconstruction shall preserve the original evidence and the derivation of any normalized timeline.

A displayed timeline is a derived representation and shall remain traceable to source timestamps.

### 7.7 Historical Reconstruction

A baselined investigation shall remain reconstructable from retained source/artifact versions and recorded processing/provenance information, subject to authorized retention and access.

### 7.8 Changed Evidence After Assessment

If an artifact or evidence representation changes after assessment:

- the prior representation remains identifiable where retention permits;
- the prior assessment remains associated with the prior state;
- the changed state receives distinct lineage;
- reassessment is permitted;
- the report identifies the change and its potential impact.

---

## 8. Input / Output Contracts

### 8.1 Investigation Request

A technology-independent logical request shall contain, as applicable:

```text
InvestigationRequest
+-- investigation context [1]
+-- review scope [1]
+-- source/artifact inputs [1..*]
+-- candidate questions [0..*]
+-- candidate hypotheses [0..*]
+-- temporal scope [0..1]
+-- processing constraints [0..*]
+-- existing claims/observations/evidence [0..*]
```

### 8.2 Artifact Input

An artifact input should support:

- artifact identity where already assigned;
- source identity;
- acquired content/reference;
- acquisition state;
- acquisition time;
- version/lineage;
- integrity information;
- provenance;
- location metadata;
- access state.

### 8.3 Observation Input

An observation input should contain:

- observation identity;
- source/artifact reference;
- location;
- observation content;
- temporal metadata where applicable;
- extraction/transformation provenance;
- classification where applicable.

### 8.4 Claim / Hypothesis Input

A claim/hypothesis input shall contain:

- stable identity;
- proposition;
- origin;
- applicable source location;
- provenance;
- version/lineage;
- review scope;
- existing evidence relationships where supplied.

### 8.5 Evidence Input

An evidence input shall contain:

- stable identity;
- source/artifact reference;
- location;
- evidence content or reference;
- provenance;
- version/lineage where applicable;
- integrity/authenticity/authority information where applicable.

### 8.6 Assessment Input

An assessment input shall contain:

- assessed claim/hypothesis;
- assessment state;
- evidence basis;
- scope/context;
- assessment provenance;
- limitations;
- reviewer information where applicable.

### 8.7 Investigation Result

The logical result shall contain, as applicable:

```text
InvestigationResult
+-- investigation context [1]
+-- source/artifact inventory [1..*]
+-- observations [0..*]
+-- claims/hypotheses [0..*]
+-- evidence [0..*]
+-- relationships [0..*]
+-- assessments [0..*]
+-- timeline/finding presentation [0..*]
+-- provenance [1..*]
+-- limitations [0..*]
+-- unresolved questions [0..*]
```

### 8.8 Partial Result

The system shall support partial results when some sources, artifacts, transformations, or processing stages fail.

A partial result shall identify:

- successfully processed material;
- failed or unavailable material;
- failure reason/state where available;
- affected claims/assessments;
- completeness limitations.

The system shall not discard valid processed material merely because another artifact failed.

### 8.9 Structural Validation

Validation shall deterministically detect, as applicable:

- missing investigation scope;
- missing required identities;
- invalid references;
- invalid relationship endpoints;
- malformed artifact metadata;
- missing required provenance;
- inconsistent version/lineage;
- invalid assessment references.

Structural validity does not imply substantive investigative correctness.

---

## 9. UI Demonstration

### 9.1 Investigation Setup

The UI shall allow the investigator to:

- establish investigation scope;
- select or register sources;
- identify access restrictions;
- define temporal scope;
- record investigation questions.

### 9.2 Artifact Intake

The UI shall show:

- source;
- artifact identity;
- acquisition state;
- version;
- integrity information;
- acquisition provenance;
- access state.

### 9.3 Artifact / Observation Inspection

The investigator shall be able to inspect:

- artifact metadata;
- source location;
- artifact content or authorized representation;
- extracted observations;
- extraction provenance;
- timestamps and temporal metadata.

### 9.4 Hypothesis Workspace

The UI shall display:

- candidate claims/hypotheses;
- hypothesis provenance;
- supporting evidence;
- contradicting evidence;
- qualifying evidence;
- unresolved evidence;
- current assessment;
- limitations.

Multiple competing hypotheses shall remain simultaneously inspectable.

### 9.5 Evidence Inspection

The UI shall permit navigation from an evidence item to:

- source;
- acquired artifact;
- precise artifact location;
- acquisition/integrity information;
- transformation history;
- related claims/hypotheses.

### 9.6 Timeline / Correlation View

Where temporal analysis is applicable, the UI shall show:

- original source timestamps;
- normalized timestamps where used;
- timezone/offset;
- clock-offset assumptions where applicable;
- source/artifact references;
- traceability to observations/evidence;
- conflicts and uncertainty.

The timeline shall not hide source-time discrepancies.

### 9.7 Competing-Hypothesis View

A comparison view should show, for each hypothesis:

| Hypothesis | Supporting evidence | Contradicting evidence | Qualifying evidence | Unresolved gaps | Assessment |
|---|---|---|---|---|---|

The view shall not imply that display order constitutes semantic priority.

### 9.8 Provenance / Handling View

The UI shall permit traversal through:

```text
Source
  → Acquisition
  → Artifact
  → Transformation / Handling
  → Observation / Evidence
  → Claim / Hypothesis
  → Assessment
```

### 9.9 Report View

The report view shall expose:

- investigation scope;
- artifact inventory;
- acquisition and integrity information;
- observations;
- hypotheses;
- evidence;
- evidence locations;
- assessments;
- timeline/finding set;
- provenance;
- limitations;
- unresolved questions;
- reviewer actions.

### 9.10 Authorization and Sensitive Material

The UI shall not expose protected artifact content to unauthorized users.

Unavailable or restricted material shall be represented without claiming that it was inspected.

---

## 10. Negative and Boundary Cases

### 10.1 Missing Investigation Scope

Reject the investigation request deterministically or require scope completion before substantive assessment.

### 10.2 Empty Artifact Corpus

Permit an explicit incomplete investigation state if the application supports it, but do not report substantive findings without evidence.

### 10.3 Malformed Artifact

Preserve the artifact registration and report the processing failure. Do not fabricate observations.

### 10.4 Inaccessible Artifact

Represent the artifact as inaccessible and identify affected claims/hypotheses.

Do not treat inaccessible material as inspected evidence.

### 10.5 Corrupted Artifact

Preserve available integrity information and report corruption.

Do not silently repair or replace the artifact while presenting it as the original.

### 10.6 Integrity Mismatch

If a supported integrity check fails:

- preserve the failure result;
- retain the affected artifact identity;
- identify affected downstream evidence;
- prevent silent conversion into a valid integrity state.

### 10.7 Missing Integrity Metadata

Represent that integrity could not be established under the available mechanism.

Do not convert missing integrity information into either integrity success or substantive contradiction.

### 10.8 Duplicate Artifact

Detect or represent duplication where possible.

Do not count identical copies from the same upstream acquisition as independent corroboration merely because they have different storage locations.

### 10.9 Changed Artifact After Assessment

Preserve prior artifact/version and assessment context, record the changed lineage, and permit reassessment.

### 10.10 Derived Artifact Without Provenance

Reject or mark the derived representation incomplete for evidence-bearing use when required provenance is absent.

Do not represent an unexplained derived result as though it were original evidence.

### 10.11 Conflicting Timestamps

Preserve original timestamps, expose the conflict, and record any normalization or clock-offset assumption.

Do not silently select one timestamp.

### 10.12 Missing Expected Telemetry

Represent the telemetry gap explicitly.

Do not infer that the expected event did not occur solely because the telemetry is absent.

### 10.13 Conflicting Evidence

Preserve each evidence item and its provenance.

Do not overwrite or silently rank one source as correct.

### 10.14 Competing Hypotheses

Preserve all material hypotheses.

Do not silently collapse them into a single finding.

### 10.15 Unsupported Hypothesis

Represent the hypothesis as unresolved or insufficiently evidenced.

Do not convert lack of support into proof of falsity.

### 10.16 Partial Support

Represent which portions are supported and which remain unsupported or qualified.

### 10.17 Source Authenticity Unresolved

Preserve the uncertainty.

Do not equate unresolved authenticity with substantive contradiction.

### 10.18 Tool Output Error

Preserve tool identity/version and processing failure.

Do not silently treat failed or partial tool output as authoritative evidence.

### 10.19 Incorrect Automated Observation

Allow human correction with preserved prior observation, revised observation, provenance, and justification.

Where the correction contains a substantive proposition, represent it as a reviewer-originated claim/assertion and assess it against supporting evidence where applicable.

### 10.20 Analyst Note Containing a Claim

Distinguish the note from the underlying source evidence.

If the note contains a substantive claim, represent that claim explicitly rather than treating the note itself as proof.

### 10.21 Identity Ambiguity

Do not silently merge hosts, users, accounts, devices, systems, or other subjects merely because identifiers appear similar.

Identity resolution remains application-level unless an applicable authoritative specification establishes otherwise.

### 10.22 Evidence Chain

Preserve every material chain step.

Do not imply that all intermediate propositions are established.

### 10.23 Transformation Failure

Preserve the input artifact and processing failure.

Do not silently substitute an incomplete derived result.

### 10.24 Partial Processing Failure

Retain successfully processed material and identify failed portions and their effect on completeness.

### 10.25 Round-Trip Failure

Report representation/conformance failure rather than silently dropping artifact, observation, claim, evidence, relationship, provenance, assessment, or limitation information.

### 10.26 Unauthorized Access Request

Enforce the authorization boundary.

Do not bypass repository or artifact access controls merely to improve investigation completeness.

### 10.27 Downstream Decision Request

Preserve the evidence-review task where possible but do not silently transform an evidence assessment into a legal conclusion, attacker attribution, containment command, remediation action, or disciplinary decision.

---

## 11. Acceptance Criteria

| ID | Acceptance criterion |
|---|---|
| AC-F01-01 | An investigator can establish an investigation with a declared scope and authorized artifact corpus. |
| AC-F01-02 | Sources and acquired artifacts can be registered with stable identity and applicable provenance. |
| AC-F01-03 | Artifact acquisition state, version/lineage, and access state can be represented and inspected. |
| AC-F01-04 | Applicable artifact-integrity information can be preserved and assessed independently of substantive claim assessment. |
| AC-F01-05 | Material observations can be identified with source/artifact locations and provenance. |
| AC-F01-06 | Candidate claims/hypotheses can be represented with stable identity, provenance, and scope. |
| AC-F01-07 | Evidence can be registered and explicitly associated with claims/hypotheses. |
| AC-F01-08 | Support, contradiction, qualification/partial support, unresolved, and insufficient states can be represented. |
| AC-F01-09 | Competing hypotheses remain independently identifiable and simultaneously inspectable. |
| AC-F01-10 | Multiple artifacts can corroborate a hypothesis without silently treating duplicate upstream acquisitions as independent evidence. |
| AC-F01-11 | Evidence locations remain navigable from evidence to source/artifact and back to the assessed hypothesis. |
| AC-F01-12 | Temporal metadata preserves original timestamps, normalization information, and relevant timezone/clock-offset context. |
| AC-F01-13 | Conflicting timestamps remain visible and are not silently normalized away. |
| AC-F01-14 | Transformation provenance permits reconstruction from acquired artifact to derived observation/evidence where applicable. |
| AC-F01-15 | Tool identity/version and processing provenance remain associated with material derived output where available. |
| AC-F01-16 | Human corrections preserve prior state, revised state, reviewer provenance, and justification. |
| AC-F01-17 | Material reviewer corrections or justifications containing substantive propositions can be represented as claims/assertions and assessed where applicable. |
| AC-F01-18 | Changed artifacts preserve historical lineage and prior assessment context where permitted. |
| AC-F01-19 | Missing, inaccessible, corrupted, or unavailable evidence is distinguished from contradiction. |
| AC-F01-20 | Evidence gaps and missing telemetry are explicitly visible in the investigation result. |
| AC-F01-21 | Artifact integrity failure cannot automatically produce a substantive hypothesis conclusion. |
| AC-F01-22 | Source authenticity and source authority remain distinct. |
| AC-F01-23 | Competing evidence remains traceable and is not overwritten or silently ranked. |
| AC-F01-24 | The UI exposes investigation scope, artifacts, observations, hypotheses, evidence, relationships, provenance, timeline, assessments, and report output. |
| AC-F01-25 | The UI permits navigation from evidence to its precise source/artifact location and provenance. |
| AC-F01-26 | The timeline, where used, exposes original timestamps and transformations rather than hiding temporal discrepancies. |
| AC-F01-27 | A partial processing failure preserves successfully processed material and identifies affected portions. |
| AC-F01-28 | Machine round-trip preserves identity, artifacts, observations, claims, evidence, relationships, provenance, source/version state, assessments, and limitations. |
| AC-F01-29 | Structural validation deterministically detects invalid identities, references, relationship endpoints, and required provenance. |
| AC-F01-30 | A complete end-to-end investigation workflow can be demonstrated through the UI from artifact intake through report inspection. |
| AC-F01-31 | The report exposes evidence basis, integrity/authenticity information, provenance, assessments, competing hypotheses, limitations, and unresolved questions without converting them into unsupported legal or attribution conclusions. |

---

## 12. Reference-Core versus Application Responsibilities

### 12.1 Shared Reference Core

The shared core shall provide only capabilities demonstrated as reusable and necessary across the P0 portfolio, including:

- stable semantic identity;
- source/artifact representation;
- source/artifact location;
- claim representation;
- evidence representation;
- typed relationship representation;
- assessment representation;
- provenance and traceability;
- source-state/version handling;
- integrity/authenticity/authority metadata boundaries;
- machine representation and semantic round-trip;
- persistence/storage abstractions;
- validation/verification integration boundaries.

VS-F01 does not justify a new forensic-specific semantic root type.

### 12.2 Reusable Enabling Infrastructure

Potential reusable enabling infrastructure includes:

- acquired artifact preservation;
- artifact version/lineage storage;
- source-location handling;
- deterministic structural validation;
- provenance capture;
- transformation provenance;
- report assembly;
- traceability traversal;
- reproducible processing records;
- artifact-integrity metadata handling.

These capabilities remain cohesive and replaceable.

### 12.3 Application Layer

The F01 application owns:

- investigation setup;
- forensic artifact corpus configuration;
- forensic acquisition integration;
- artifact parsing/extraction;
- observation generation;
- hypothesis formulation assistance;
- evidence discovery/correlation;
- temporal normalization and timeline presentation;
- forensic-domain classification;
- competing-hypothesis presentation;
- incident-specific source selection;
- analyst review workflow;
- investigation report presentation.

These capabilities shall not be promoted into the semantic core merely because F01 needs them.

### 12.4 External Dependencies

Potential external dependencies include:

- authorized forensic acquisition systems;
- endpoint and network telemetry repositories;
- log-management systems;
- security monitoring platforms;
- storage/repository systems;
- OCR/text extraction;
- forensic parsing tools;
- timeline/correlation tools;
- threat-intelligence providers;
- identity/access-control systems.

No provider, forensic tool, or acquisition technology is prescribed.

---

## 13. Capability Coverage

### 13.1 Required / Demonstrated Capabilities

The current capability matrix identifies the following as directly required or enabling for F01:

| Capability | F01 classification | Placement |
|---|---|---|
| Source material registration | Level 1 / D | Shared core |
| Acquired artifact preservation | Level 1 / D | Shared core |
| Source/artifact location | Level 1 / D | Shared core |
| Stable semantic identity | Level 1 / D | Shared core |
| Claim representation | Level 1 / E | Shared core |
| Evidence representation | Level 1 / D | Shared core |
| Evidence-to-claim association | Level 1 / D | Shared core |
| Typed relationship representation | Level 1 / D | Shared core |
| Support/contradiction/qualification assessment | Level 1 / D | Shared core |
| Unresolved/uncertainty representation | Level 1 / D | Shared core |
| Provenance representation | Level 1 / D | Shared core |
| Traceability traversal | Level 1 / D | Shared core |
| Source version/revision state | Level 1 / D | Shared core |
| Artifact integrity information | Level 1 / D | Shared core |
| Source authenticity result | Level 1/2 / D | Shared core boundary |
| Source authority information | Level 1 / D | Shared core |
| Transformation provenance | Level 1/2 / D | Shared core boundary |
| Machine-readable representation | Level 1 / D | Shared core |
| Semantic round-trip preservation | Level 1 / D | Shared core |
| Structured assessment result | Level 1 / D | Shared core |
| Report generation | Level 1 / D | Application/shared capability as justified |
| UI source selection/ingestion | Level 1 / D | Application |
| UI observation inspection | Level 1 / D | Application |
| UI evidence inspection | Level 1 / D | Application |
| UI relationship inspection | Level 1 / D | Application |
| UI provenance/location inspection | Level 1 / D | Application |
| UI assessment/uncertainty inspection | Level 1 / D | Application |
| UI traceability navigation | Level 1 / D | Application |
| UI report inspection | Level 1 / D | Application |
| Validation/conformance integration boundary | Level 2 / E | Shared boundary |
| Verification integration boundary | Level 2 / E | Shared boundary |
| Deterministic required-input validation | Level 1/2 / D | Shared boundary |
| Reproducible processing record | Level 2 / D | Shared enabling infrastructure |

These classifications are derived from the current capability matrix and the F01 workflow. They do not by themselves constitute a matrix status change or a capability-promotion decision.

### 13.2 Application-Specific Capabilities

The following remain application-level:

- forensic artifact acquisition;
- forensic parsing and extraction;
- observation classification;
- hypothesis-generation assistance;
- timeline correlation;
- forensic-domain event interpretation;
- tool orchestration;
- analyst workflow;
- forensic report formatting;
- incident-specific search and discovery;
- threat-intelligence integration;
- host/account/device contextualization.

### 13.3 Explicitly Deferred / Not Promoted

F01 does not justify promotion of:

- universal search infrastructure;
- universal reasoning engines;
- generic ontology inference;
- arbitrary graph analytics;
- universal forensic knowledge graphs;
- automated attacker attribution;
- malware-analysis engines;
- sandbox execution infrastructure;
- generalized SIEM capabilities;
- universal threat-intelligence platform;
- generalized workflow orchestration;
- distributed microservices;
- generalized multi-tenancy;
- AI-specific semantic core;
- jurisdiction-specific legal semantics;
- mandatory numeric confidence/evidence-strength scoring.

If implementation evidence reveals a missing shared capability, the approved capability-promotion lifecycle shall be used rather than silently changing the matrix.

---

## 14. Security, Privacy, and Operational Considerations

### 14.1 Sensitive Investigative Material

Forensic artifacts may contain:

- credentials;
- personal information;
- confidential communications;
- security-sensitive configuration;
- proprietary source code;
- regulated data;
- malware samples;
- privileged or restricted information.

The implementation shall apply appropriate authorization, retention, access-control, and handling requirements for the deployment context.

### 14.2 Access-Controlled Artifacts

Artifact access state shall be represented.

Unauthorized users shall not receive protected artifact content, and the investigation shall not claim that protected material was inspected when it was inaccessible.

### 14.3 Artifact Integrity

Where supported, artifact-integrity information shall be preserved and auditable.

Integrity failure shall be visible and shall not be silently repaired into a successful integrity state.

### 14.4 Acquisition and Handling Auditability

The system should preserve enough history to determine:

- what artifact was acquired;
- when it was acquired;
- from which source;
- under which acquisition context;
- which transformations occurred;
- which reviewers acted on the result;
- which assessment was based on which artifact state.

### 14.5 Retention and Historical Reconstruction

Retention shall support the agreed investigation reproducibility requirements.

Concrete retention periods and archival technology remain deployment/implementation decisions.

### 14.6 External Dependency Failure

Acquisition, parsing, extraction, repository, search, or correlation failure shall not corrupt successfully registered artifacts.

Resulting incompleteness shall be represented.

### 14.7 Observability

Operational records should diagnose:

- artifact acquisition;
- parsing/extraction;
- integrity checks;
- transformation;
- timestamp normalization;
- observation generation;
- evidence association;
- assessment;
- report generation;
- external dependency failures.

### 14.8 Reproducibility

Baselined investigation results should remain reconstructable from retained artifact versions and recorded processing/provenance state, subject to authorization and retention constraints.

### 14.9 Authorization Boundary

The slice shall not bypass acquisition, repository, endpoint, or artifact authorization controls merely to improve evidence completeness.

### 14.10 Malware and Dangerous Content Boundary

Forensic artifacts may contain malicious or dangerous content.

The reference slice shall treat such material as data and shall not require automatic execution of untrusted code, scripts, binaries, or macros.

Safe handling and analysis mechanisms remain deployment/tooling concerns.

---

## 15. Explicit Exclusions

VS-F01 does not require:

- autonomous incident response;
- automatic containment or remediation;
- automatic attacker attribution;
- legal conclusions;
- criminal or civil liability determinations;
- universal forensic reasoning;
- malware reverse-engineering engines;
- sandbox execution;
- generalized SIEM;
- universal log-management infrastructure;
- universal threat-intelligence infrastructure;
- unrestricted artifact acquisition;
- unrestricted crawling;
- generalized identity resolution;
- universal workflow orchestration;
- distributed microservices;
- generalized multi-tenancy;
- forensic-specific semantic root types;
- mandatory evidence-strength scores;
- implementation of all ECRA semantic constructs.

Specialized forensic services and tools may be used as replaceable application dependencies when needed.

---

## 16. Implementation and Evolution Constraints

### 16.1 Semantic Contract Stability

The semantic model shall remain independent of:

- UI framework;
- persistence technology;
- forensic acquisition technology;
- parsing/extraction engine;
- log-management platform;
- search provider;
- threat-intelligence provider;
- timeline/correlation engine;
- deployment topology.

### 16.2 Replaceability

Acquisition, extraction, parsing, search, correlation, timeline generation, and reporting components should be replaceable through explicit interfaces.

### 16.3 Cohesive Responsibilities

Maintain clear boundaries between:

- source/artifact management;
- acquisition;
- parsing/extraction;
- observation representation;
- claim/evidence representation;
- provenance;
- assessment;
- temporal correlation;
- investigation workflow;
- report generation;
- UI presentation.

### 16.4 Future Decomposition

The implementation should permit future separation of acquisition, extraction, correlation, assessment, and reporting into separate processes/services without changing stable ECRA semantic contracts where reasonably foreseeable.

No microservice architecture is required for F01.

### 16.5 Determinism and Reproducibility

Structural validation and machine representation operations shall be deterministic.

For processing that depends on mutable external data, the implementation shall preserve sufficient source identity, acquisition time, version, artifact identity, and processing provenance to reproduce the investigation result to the extent reasonably possible.

### 16.6 Forensic-Domain Decoupling

The shared semantic model shall not depend on:

- a particular forensic tool;
- a specific incident-response methodology;
- a particular security product;
- a specific threat-intelligence provider;
- a particular operating system;
- a particular cloud provider;
- a particular incident taxonomy.

Application-level forensic context may be supplied through replaceable domain components.

---

## 17. Design and Implementation Traceability

This specification is derived from and remains traceable to:

1. Approved ECRA Reference Application — Vertical Slice Portfolio.
2. Current ECRA Reference Implementation — Cross-Slice Capability Matrix.
3. Approved ECRA P0 Vertical Slice Specification Framework.
4. Approved Gen1 Claim and Evidence Requirements.
5. Approved Gen1 Context and Evaluation Requirements.
6. Approved Gen1 Traceability and Engineering Requirements.
7. Applicable ECRA-1200 Architecture Description Language boundaries.
8. Applicable ECRA-1200 detailed-design foundation and canonical ADL meta-model.

J01, R01, B01, and L01 are used only as implementation-pattern references for common P0 structure and previously demonstrated claim/evidence/provenance boundaries. They do not override the authoritative sources above.

The capability matrix's current repository status is preserved as-is; this specification does not silently change that status or treat F01 analysis as approval of the matrix.

The specification does not supersede any normative ECRA document.

Where F01 requires a semantic capability not established by these authorities, the gap shall be recorded rather than silently promoted into the normative ECRA model.

---

## 18. Verification Strategy

### 18.1 Contract Tests

Verify:

- investigation request/result structures;
- stable identities;
- valid references;
- relationship endpoints;
- artifact/version consistency;
- incomplete-result handling;
- required provenance.

### 18.2 Artifact Integrity Tests

Verify:

- supported integrity metadata is preserved;
- integrity failure is represented;
- integrity success does not automatically produce a positive hypothesis assessment;
- artifact identity remains stable across representation changes.

### 18.3 Acquisition and Transformation Tests

Verify:

- acquisition metadata is preserved;
- acquired artifact remains distinguishable from derived artifacts;
- transformation inputs and outputs remain traceable;
- tool/version metadata remains associated with material derived output where available.

### 18.4 Semantic Integration Tests

Verify:

- source/artifact;
- observation;
- claim/hypothesis;
- evidence;
- explicit evidence relationships;
- artifact locations;
- assessments;
- provenance;
- traceability;
- version/lineage;
- source-property boundaries.

### 18.5 Competing-Hypothesis Tests

Verify:

- multiple hypotheses can coexist;
- evidence can support one hypothesis and contradict another;
- no hypothesis is silently overwritten;
- display order does not alter semantic state;
- the report preserves the evidence basis for each assessment.

### 18.6 Temporal Tests

Verify:

- original timestamps remain preserved;
- normalized timestamps remain traceable to originals;
- timezone/offset information is preserved;
- clock-offset assumptions are visible where applicable;
- conflicting timestamps remain visible.

### 18.7 Evidence-Chain Tests

Verify:

- derived evidence remains linked to its inputs;
- transformation history is traversable;
- intermediate propositions are not automatically treated as established.

### 18.8 Identity Boundary Tests

Verify that:

- similar hostnames do not cause silent merging;
- similar usernames/accounts do not cause silent merging;
- similar device identifiers do not cause silent merging;
- artifact identity remains stable across representation changes.

### 18.9 Negative Tests

Verify:

- missing scope;
- empty corpus;
- malformed artifact;
- inaccessible artifact;
- corrupted artifact;
- integrity mismatch;
- missing integrity metadata;
- duplicate artifact;
- changed artifact;
- derived artifact without provenance;
- conflicting timestamps;
- missing telemetry;
- conflicting evidence;
- competing hypotheses;
- unsupported hypothesis;
- partial support;
- unresolved authenticity;
- tool-output failure;
- incorrect automated observation;
- analyst note containing a claim;
- identity ambiguity;
- transformation failure;
- partial processing failure;
- unauthorized access;
- downstream decision request.

### 18.10 Reproducibility Tests

Verify reconstruction of a baselined investigation from retained artifact versions and recorded processing/provenance information, subject to permitted retention and access.

### 18.11 Representation Round-Trip

Verify:

```text
Logical VS-F01 semantic state
    → machine representation
    → reconstructed logical state
```

Required identity, artifacts, observations, claims, evidence, relationships, provenance, traceability, source/version state, assessments, and limitations shall be preserved.

Byte-for-byte serialization equality is not required.

### 18.12 UI End-to-End Test

Demonstrate:

```text
Investigation setup
    → artifact intake
    → observation inspection
    → hypothesis workspace
    → evidence inspection
    → competing-hypothesis comparison
    → timeline / correlation
    → provenance / traceability
    → assessment
    → report
```

The UI demonstration is part of slice completion.

---

## 19. Deliverable and Completion Definition

VS-F01 is complete only when:

1. the evidence-first workflow is implemented;
2. required shared-core capabilities are available;
3. application-specific forensic capabilities are implemented;
4. the complete workflow is demonstrable through the UI;
5. acceptance criteria are verified;
6. negative and boundary cases are tested;
7. competing-hypothesis behavior is demonstrated;
8. artifact-location traceability is demonstrated;
9. acquisition/integrity provenance is demonstrated;
10. temporal reconstruction behavior is demonstrated where applicable;
11. machine representation round-trip is verified;
12. provenance and traceability are demonstrated;
13. relevant capability-matrix evidence is recorded;
14. the implementation remains within the approved reference-core boundary.

Implementation completion does not require excluded or deferred capabilities.

---

## 20. Open and Deferred Items

The following remain intentionally open or deferred:

1. concrete forensic acquisition mechanisms and products;
2. detailed forensic artifact-type vocabulary;
3. detailed timestamp normalization and clock-skew algorithms;
4. forensic parsing/extraction engines;
5. timeline/correlation technology;
6. threat-intelligence providers;
7. concrete storage and retention parameters;
8. malware analysis and sandboxing;
9. incident-response orchestration;
10. domain-specific incident taxonomies;
11. concrete UI technology;
12. broader capability promotion based on later P0 implementation evidence.

These shall be resolved only when implementation evidence or an authoritative specification requires them.

---

## 21. Status

This specification is **REVIEW** and is intended to drive VS-F01 reference-application implementation planning and supporting verification once approved.
