# GARI v1.0 Experimental Item Space Design Specification

**Document:** GARI-v1.0-Experimental-Item-Space-Design-Specification.md

**Status:** Publication Candidate

---

# Chapter 1 — Introduction

## 1.1 Purpose

This specification defines the Experimental Item Space used to support metadata-enabled goal-directed alignment between formalized computational goals and computable knowledge capabilities within GARI-based experiment families.

The Experimental Item Space is a deliberately constructed population of Canonical Items that serves as the shared reference substrate over which experimental GB-FDO and CBKB-FDO corpora are constructed.

## 1.2 Scope

This specification defines:

- Experimental Item Space purpose
- Experimental Item Space architecture
- Relationship to Canonical Item Space
- Relationship to GB-FDO corpora
- Relationship to CBKB-FDO corpora
- Experimental Item population governance
- Experimental Item Space design principles

## 1.3 Relationship to the Canonical Item Specification

The Canonical Item Specification defines what a valid Canonical Item is.

This specification defines which Canonical Items are intentionally established for a family of goal–knowledge alignment experiments.

## 1.4 Scientific Context

The Experimental Item Space exists to support metadata-enabled alignment and application of computable knowledge toward realization of desired future states of knowledge.

Within GARI, these activities are investigated through Alignment Result Graphs and Constructed Realizations produced by Alignment Engines operating on Layer Images.

## 1.5 Out of Scope

This specification does not define:

- Item representations;
- FDO representations;
- corpus specifications;
- Layer construction procedures;
- Alignment Engine behavior.


---

# Chapter 2 — Foundational Architecture

## 2.1 Architectural Position

Canonical Item Specification

↓

Experimental Item Space

↓

GB-FDO Corpus / CBKB-FDO Corpus

↓

Layer Construction

↓

Layer Image

↓

Input Package

↓

Alignment Engine

↓

Alignment Result Graph + Constructed Realizations

## 2.2 Experimental Item Population

An Experimental Item Space consists of a deliberately constructed population of Canonical Items intended to support one or more experiment families.

## 2.3 Shared Reference Substrate

The Experimental Item Space serves as a shared reference substrate through which goal–knowledge alignment opportunities may be represented within participating FDO metadata.

---

# Chapter 3 — Core Principles

## EIS-P001 — Shared Design Object Principle

The Experimental Item Space SHALL be treated as a shared scientific design object for the experimental family supported by the Canonical GB-FDO Corpus and Canonical CBKB-FDO Corpus.

The Experimental Item Space SHALL be defined prior to, and independently from, the detailed construction of either corpus.

The GB-FDO Corpus and CBKB-FDO Corpus SHALL be constructed as reference patterns over the Experimental Item Space rather than as independent creators of Item populations.

## EIS-P002 — Derived Population Principle

The size of an Experimental Item Space SHALL be derived from the goal–knowledge alignment landscape required by the experiment family.

Experimental Item Space design SHALL first define:

- goal-participation patterns;
- knowledge-participation patterns;
- alignment-opportunity structures;
- overlap structures;
- Item reuse structures;
- realization-opportunity structures;

before establishing the final Item count.

Item count SHALL be treated as a derived design parameter rather than a primary design objective.

Experimental Item Space design SHALL support construction of multiple distinct Layers whose participating GB-FDOs and CBKB-FDOs exhibit meaningful variation in Item-reference patterns.

The Experimental Item Space SHALL support evaluation of whether Alignment Result Graphs and Constructed Realizations remain stable across Layer constructions exhibiting differing Item-reference configurations.


## EIS-P003 — Latent Item Dependency-Aware Assignment Principle

The Experimental Item Space SHALL be constructed with consideration of latent computational dependencies among Items.

Such dependencies SHALL be treated as Item-level design knowledge and SHALL NOT be represented as explicit Item-to-Item relationships within the Experimental Item Space.

Subsequent assignment of Items to GB-FDOs and CBKB-FDOs SHOULD be informed by latent computational dependency knowledge sufficient to support investigation of:

- single-item Constructed Realizations;
- multi-item Constructed Realizations;
- partial goal fulfillment;
- complete goal fulfillment;
- realization failures.

The Experimental Item Space SHALL support such investigations across Item-ID-visible and Item-ID-blinded experimental conditions.

Items included within the Experimental Item Space SHALL have an intended participation role within one or more experimental corpora. Items lacking intended participation in experimental FDOs SHOULD NOT be included.


## EIS-P004 — Experimental Abstraction Principle

The Experimental Item Space SHALL be constructed at a level of abstraction appropriate to the experimental objectives.

Experimental Items SHALL be sufficiently abstract to support investigation of alignment and realization phenomena without requiring acceptance of domain-specific computational relationships.

Experimental Item design SHOULD avoid unnecessary domain-specific semantics that could introduce external plausibility judgments unrelated to the phenomena under investigation.

The primary purpose of the Experimental Item Space is to support investigation of goal–knowledge alignment and realization behavior rather than representation of a specific scientific domain.


---

# Chapter 4 — Relationship to Experimental Corpora

## 4.1 Corpus Dependency

Experimental corpora depend upon the Experimental Item Space.

## 4.2 GB-FDO Corpus Relationship

The Canonical GB-FDO Corpus SHALL be constructed as a reference pattern over the Experimental Item Space.

## 4.3 CBKB-FDO Corpus Relationship

The Canonical CBKB-FDO Corpus SHALL be constructed as a reference pattern over the Experimental Item Space.

## 4.4 Shared Experimental Landscape

Both corpora inhabit the same Experimental Item Space.

---

# Chapter 5 — Experimental Item Space Governance

## 5.1 Design Authority

The Experimental Item Space SHALL be intentionally designed.

## 5.2 Item Population Ownership

The Experimental Item Space owns the Item population used by the experiment family.

## 5.3 Versioning

Distinct Experimental Item Space versions SHOULD be treated as distinct experimental conditions.

---

# Appendix A — Accepted Findings

- EIS-001 Experimental Item Space Must Be Treated as a Shared Design Object for Both FDO Corpora
- EIS-002 Experimental Item Space Size Should Be Derived From Goal–Knowledge Alignment Landscape Design Rather Than Raw Item Counts
- EIS-003 Experimental Item Space Design SHALL Employ Latent Item Dependency-Aware Assignment
- EIS-004 Experimental Item Space Shall Operate at an Appropriate Level of Abstraction

---

# Appendix B — Future Findings

- EIS-005
- EIS-006
