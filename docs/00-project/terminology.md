# ECRA — Terminology

> Status: DRAFT
> Authority: NORMATIVE
> Generation: GEN1

## 1. Purpose

This document defines the canonical terminology used throughout the ECRA
Generation 1 documentation and implementation.

The terms defined here have specific meanings within ECRA. Requirements,
architecture, design, implementation, and verification documents should use
these meanings consistently.

A document may introduce additional domain-specific terminology when
necessary, but it must not redefine a term established here without an
explicit, approved decision.

---

## 2. Claim

A **claim** is a proposition presented as information that can be evaluated
against evidence.

A claim may be expressed explicitly or represented in a structured form.

A claim is the primary subject of an ECRA evaluation.

A claim is not necessarily true merely because it is stated, cited, repeated,
or attributed to a source or person.

---

## 3. Assertion

An **assertion** is a statement or proposition put forward as being true or
otherwise valid.

Within ECRA, an assertion may be treated as a claim when it is subject to
evaluation.

The term "claim" should be preferred when referring specifically to an object
being evaluated by ECRA.

---

## 4. Evidence

**Evidence** is information considered relevant to determining whether or to
what extent a claim is established.

Evidence may:

- support a claim;
- contradict a claim;
- qualify a claim;
- provide context relevant to a claim; or
- fail to establish the claim.

The existence of evidence does not by itself establish the claim.

Evidence must be evaluated according to the applicable Gen1 requirements.

---

## 5. Source

A **source** is an identifiable origin, publication, repository, provider, or
other entity from which information or source material is obtained or to which
it is attributed.

A source may be, for example:

- a document or publication;
- a record or dataset;
- a statement or communication;
- a repository or digital resource;
- an institution or individual;
- or another identifiable origin of information.

A source and the information obtained from or attributed to that source are
distinct concepts.

ECRA does not inherently control the continued availability, integrity,
authenticity, or future state of an external source.

Obtaining source material does not, by itself, establish that the obtained
material is the original or authentic representation of the source.

Where source material is acquired by ECRA, the system should preserve
sufficient acquisition and provenance information to establish what ECRA
obtained, when it obtained it, and, where applicable, how the acquired
material
can be verified against other available evidence.

The existence, authenticity, integrity, or authority of a source must therefore
be treated as distinct properties that require appropriate evidence and
verification.

---

## 6. Source Material

**Source material** is information attributed to or represented as originating
from a source and used as material for an evaluation.

Source material may include, for example:

- text;
- quotations;
- data;
- images;
- recordings;
- structured records; or
- other information contained in or attributed to the source.

Source material should remain distinguishable from the representation acquired
by ECRA, interpretations derived from it, and claims made about it.

The fact that information is attributed to a source does not by itself
establish that the information is authentic, complete, unchanged, or
accurately represented.

---

## 7. Acquired Artifact

An **acquired artifact** is a specific representation of source material
obtained by ECRA at a particular point in time.

An acquired artifact may be, for example:

- a downloaded document;
- an archived web resource;
- an image;
- an audio or video recording;
- a dataset;
- a structured record; or
- another digitally or physically acquired representation.

An acquired artifact represents what ECRA actually obtained. It must be
distinguished from the external source and from claims about the authenticity
or completeness of that source.

Where applicable, ECRA should preserve sufficient acquisition metadata and
provenance to establish what artifact was obtained and when it was obtained.

---

## 8. Artifact Integrity

**Artifact integrity** is the property that an acquired artifact remains
unchanged relative to a specified integrity reference.

An integrity reference may include mechanisms such as:

- a cryptographic hash;
- a digital signature;
- an independently maintained archival record; or
- another appropriate integrity mechanism.

Artifact integrity establishes that the acquired representation has not
changed relative to the applicable integrity reference.

Artifact integrity does not, by itself, establish that the artifact is
authentic, original, authoritative, complete, or truthful.

---

## 9. Source Authenticity

**Source authenticity** concerns whether a source, source material, or
representation of source material is genuine and corresponds to what it
purports to represent.

Authenticity does not necessarily mean that an acquired artifact is the
original physical or digital artifact. An authentic representation may be a
faithful copy, reproduction, transcription, or other representation of an
original source.

Authenticity is distinct from:

- artifact integrity;
- originality;
- authority;
- relevance;
- accuracy;
- reliability; and
- evidentiary support.

Obtaining an artifact does not, by itself, establish its authenticity,
originality, or completeness.

Authenticity should therefore be established, where possible, using
appropriate evidence and provenance rather than being inferred solely from
the existence of an acquired artifact.

Where authenticity cannot be established, that limitation should remain
explicit rather than being represented as established fact.

---

## 10. Source Authority

**Source authority** is the degree or basis to which a source is recognized,
designated, or regarded as authoritative or suitable for a particular purpose,
domain, or context.

Authority is not an inherent universal property assigned by ECRA.

Where an authority claim is relevant, ECRA should represent the basis for that
claim, including its attribution, applicable context, criteria, standard,
policy, or other supporting information where available.

An authority claim is itself information that may require evaluation.

---

## 11. Context

**Context** is information or circumstances relevant to correctly interpreting
a claim, evidence, source material, or evaluation.

Context may include, depending on the subject:

- surrounding statements;
- temporal circumstances;
- geographic circumstances;
- intended audience;
- domain;
- definitions;
- qualifications;
- limitations;
- preceding or subsequent material;
- conditions under which a statement applies; or
- other information necessary to avoid a materially misleading interpretation.

Context is relevant when its absence or alteration could materially affect the
meaning or evaluation of a claim or evidence.

---

## 12. Contextual Integrity

**Contextual integrity** is the preservation and faithful representation of
context necessary for an accurate interpretation or evaluation.

Contextual integrity may be compromised by, among other things:

- selective quotation;
- omission of material context;
- misleading presentation;
- removal of relevant qualifications;
- interpretation beyond what the source establishes; or
- combining information in a way that produces an unsupported conclusion.

The precise criteria for contextual adequacy are defined by the applicable Gen1
requirements and design.

---

## 13. Provenance

**Provenance** is information describing the origin, history, derivation, or
transformation of an information object.

For ECRA, provenance may establish relationships such as:

    Claim
      |
      v
    Evidence
      |
      v
    Source
      |
      v
    Source Material

It may also record transformations or interpretations applied to information.

Provenance exists to support traceability and independent examination of the
basis for an evaluation.

---

## 14. Traceability

**Traceability** is the ability to follow an evaluation, result, or
information object back through its relevant claims, evidence, sources,
context, transformations, and other recorded relationships.

Traceability should allow an interested party to understand the basis of an
evaluation and, where applicable, identify where an error or unsupported
inference occurred.

---

## 15. Interpretation

An **interpretation** is an explanation, inference, or understanding derived
from source material, evidence, context, or other information.

An interpretation is distinct from the underlying source material.

An interpretation must not be presented as though it were the original source
material.

Where an interpretation is generated or transformed by an AI system, its
AI-generated nature and relevant provenance should be represented according to
the applicable requirements.

---

## 16. AI-Generated Interpretation

An **AI-generated interpretation** is an interpretation produced or materially
transformed by an artificial intelligence system.

An AI-generated interpretation should remain distinguishable from:

- the original source material;
- human-authored content;
- the evidence on which it is based; and
- the evaluation result to which it contributes.

Where applicable, provenance should identify the AI system or model and other
relevant information required by the Gen1 specification.

---

## 17. Evaluation

An **evaluation** is the systematic assessment of a claim using relevant
evidence, source information, context, and applicable evaluation criteria.

An evaluation is an explicit process governed by approved requirements and
design.

An evaluation should not be inferred solely from the existence of a citation,
source, or assertion.

---

## 18. Evaluation Result

An **evaluation result** is the structured outcome produced by an ECRA
evaluation.

The result represents the conclusion of the evaluation according to the
applicable Gen1 evaluation model.

The precise result categories, semantics, and confidence or uncertainty
representation, if any, are defined by the approved Gen1 requirements and
design.

---

## 19. Decision

A **decision** is a determination or action taken by a person or system based
on an evaluation, evidence, policy, criteria, or other relevant information.

A decision may incorporate human judgment.

A decision is distinct from an evaluation result: an evaluation may provide
evidence or an assessment that informs a decision, while the decision may
include additional considerations or responsibilities outside the evaluation
itself.

---

## 20. Human Judgment

**Human judgment** is a determination, interpretation, assessment, or decision
made by a person.

ECRA does not treat human judgment as inherently correct or inherently
superior to automated evaluation.

Where practical and applicable, human judgment should be evidence-based,
transparent, and traceable so that others can understand and review the basis
for the judgment.

---

## 21. Authority Claim

An **authority claim** is an assertion that a source, person, institution,
publication, standard, or other entity has authority or suitability for a
specified purpose, domain, or context.

An authority claim should be distinguished from the underlying factual
information about the source.

The authority claim itself may be evaluated or reported according to the
applicable Gen1 requirements.

---

## 22. Unsupported Conclusion

An **unsupported conclusion** is a conclusion that is not adequately
established by the available evidence, applicable context, and evaluation
criteria.

An unsupported conclusion may result from:

- insufficient evidence;
- incorrect interpretation;
- omitted context;
- inappropriate inference;
- combining individually valid pieces of information in an invalid manner; or
- other reasoning that exceeds what the available evidence establishes.

---

## 23. Evidence-Based Judgment

An **evidence-based judgment** is a human or system judgment whose basis is
explicitly related to relevant evidence and applicable context.

Evidence-based does not mean infallible.

An evidence-based judgment may still be incorrect because of incomplete
evidence, incorrect interpretation, omitted context, flawed reasoning, or
other errors.

ECRA should support the ability to examine and, where applicable, challenge an
evidence-based judgment.

An AI system may analyze the evidence, context, reasoning, and basis of a
judgment and identify potential errors, inconsistencies, unsupported
conclusions, or other concerns. Where appropriate, the AI system may express
an analysis, assessment, or opinion that a judgment may be incorrect or
flawed.

Any such AI-generated challenge should itself be clearly identified as
AI-generated and should provide sufficient provenance and supporting
information to allow the challenge to be independently examined.

Where the applicable ECRA workflow supports it, an AI-generated challenge may
be recorded as part of the evaluation or decision record and presented for
human reconsideration.

An AI-generated challenge is not automatically correct. It is itself an
assertion or evaluation that must be assessed according to the applicable
evidence, context, criteria, and review process.

The ability to inspect, challenge, and reconsider the basis of a judgment is
an important aspect of ECRA's traceability and accountability model.

---

## 24. Normative Language

Unless a document explicitly defines otherwise, the following terms are
used as normative language conventions throughout the ECRA specification:

- **MUST / SHALL** — mandatory requirement.
- **MUST NOT / SHALL NOT** — prohibited behavior.
- **SHOULD** — recommended behavior that may be omitted only with an
  appropriate reason.
- **SHOULD NOT** — behavior that is generally discouraged unless there is an
  appropriate reason.
- **MAY** — permitted but optional behavior.

Normative interpretation must remain consistent with the document authority
and precedence rules defined in `AGENTS.md`.

---

## 25. Terminology Governance

New ECRA-specific terms should be added to this document when they become
important to requirements, architecture, design, implementation, or
verification.

A new term should be introduced only when:

1. the concept is materially distinct from an existing term;
2. using an existing term would introduce ambiguity; and
3. the new terminology improves precision or consistency.

Existing terminology must not be casually redefined.

If an existing term must change meaning, the change requires an explicit
approved decision and appropriate updates to affected normative documents.

---

## 26. Relationship to Other Documents

This document establishes canonical terminology for the ECRA project.

It does not define detailed functional requirements, architecture,
implementation behavior, or verification procedures.

Those are defined in:

- `docs/10-requirements/`;
- `docs/20-architecture/`;
- `docs/30-design/`;
- `docs/40-decisions/`;
- `docs/50-implementation/`; and
- `docs/60-verification/`.

Where a detailed specification introduces a more specific term for a
well-defined technical concept, that term should be used consistently within
its scope without redefining the canonical project terminology.
