# GARI v1.0 Reference Data Schemas

Version: GARI v1.0

Status: Publication Candidate

Normative Relative To:
GARI-v1.0-Specification-Release-Candidate-Reconciled.md

Companion To:
GARI-v1.0-Implementation-Specification.md

---

# Document Status

Structural Audit Status: PASS

Traceability Audit Status: PASS WITH MINOR ISSUES RESOLVED

Reference Data Schema Consistency Audit Status:
PASS WITH CORRECTABLE ISSUES RESOLVED

Publication Readiness Audit Status:
PASS AFTER RECONCILIATION

This document has completed:

* Structural Audit
* Traceability Audit
* Reference Data Schema Consistency Audit
* Publication Readiness Audit

This document is the reference artifact companion to the GARI v1.0 Release Candidate and GARI v1.0 Implementation Specification.

The Release Candidate remains the authoritative architectural specification for GARI v1.0.

The Implementation Specification remains the authoritative engineering realization specification for GARI v1.0.

This document provides canonical example artifacts, example runtime objects, example package structures, example manifests, example fixtures, and example data representations intended to support implementation, testing, interoperability evaluation, and future conformance activities.

This document derives exclusively from the Release Candidate and the Implementation Specification.

This document SHALL NOT be interpreted as introducing new architecture, new concepts, new runtime behavior, new Alignment Engine requirements, or new conformance requirements.

If a conflict exists among the three documents, authority SHALL be determined as follows:

```text
GARI-v1.0-Specification-Release-Candidate-Reconciled.md

takes precedence over

GARI-v1.0-Implementation-Specification.md

takes precedence over

GARI-v1.0-Reference-Data-Schemas.md
```

---

# Purpose

The Release Candidate answers:

```text
What is GARI?
```

The Implementation Specification answers:

```text
How should GARI software be built?
```

This document answers:

```text
What should GARI artifacts
look like in practice?
```

Accordingly, this document provides canonical examples of:

* Goal-bearing FAIR Digital Objects;
* CBK-bearing FAIR Digital Objects;
* Layers;
* Layer Images;
* Alignment Engine Profiles;
* Input Packages;
* Alignment Result Graphs;
* Constructed Realizations;
* Provenance Objects;
* Output Packages;
* Saved Run Packages;
* manifests;
* package layouts;
* acceptance-test fixtures.

The examples contained herein are intended to support:

* software developers;
* AI coding systems;
* Codex implementations;
* test engineers;
* interoperability reviewers;
* implementation auditors;
* future conformance programs.

---

# Informative Status

This document is informative.

Normative requirements remain exclusively within:

```text
GARI-v1.0-Specification-Release-Candidate-Reconciled.md
```

and

```text
GARI-v1.0-Implementation-Specification.md
```

The examples contained within this document illustrate one valid realization of GARI artifacts and structures.

Examples SHALL NOT be interpreted as normative requirements unless explicitly specified by the authoritative documents.

Example identifiers, metadata values, timestamps, directory structures, manifests, and package layouts are illustrative unless otherwise specified.

Implementations MAY use equivalent representations provided that they remain conformant with the authoritative specifications.

---

# Scope

The scope of this document includes:

* canonical example schemas;
* canonical JSON examples;
* example runtime objects;
* example package structures;
* example manifests;
* example directory layouts;
* example preservation artifacts;
* example acceptance-test fixtures;
* implementation traceability mappings.

The scope of this document does not include:

* architectural specification;
* runtime specification;
* Alignment Engine algorithm specification;
* implementation technology selection;
* software architecture specification;
* conformance policy specification.

---

# Intended Use

This document is intended to function as:

* a reference artifact catalog;
* a fixture library;
* an implementation aid;
* a Codex onboarding reference;
* an interoperability reference;
* an acceptance-testing companion;
* a future conformance-support resource.

The examples are designed to be:

* machine-readable;
* internally consistent;
* minimally sufficient where possible;
* realistic where beneficial;
* suitable for direct use as implementation templates and testing fixtures.

---

# Relationship to Other GARI Documents

The GARI v1.0 document suite consists of three complementary documents.

### Release Candidate

Defines:

```text
What GARI is.
```

Provides:

* principles;
* concepts;
* structural entities;
* runtime architecture;
* result architecture;
* provenance architecture;
* persistence architecture;
* user interaction architecture.

### Implementation Specification

Defines:

```text
How GARI software should be realized.
```

Provides:

* implementation requirements;
* runtime component requirements;
* state model realization guidance;
* implementation data models;
* validation requirements;
* engine integration guidance;
* testing requirements;
* conformance guidance.

### Reference Data Schemas

Defines:

```text
Illustrative examples of GARI artifacts.
```

Provides:

* example artifact structures;
* example package contents;
* example manifests;
* example runtime objects;
* example fixtures;
* traceability mappings.

Together these three documents provide the architectural, implementation, and artifact-level guidance necessary to realize GARI v1.0 implementations and supporting tooling.

---

# Reading Guidance

Readers interested in architecture SHOULD begin with the Release Candidate.

Readers interested in implementation SHOULD consult the Implementation Specification after reviewing the Release Candidate.

Readers interested in artifact construction, testing, interoperability, fixture generation, or implementation examples SHOULD consult this document after becoming familiar with the authoritative specifications.

This document assumes familiarity with the concepts defined in the Release Candidate and does not restate normative definitions except where necessary to explain example artifacts.

---

# Chapter 1 — Introduction

## 1.1 Purpose

The purpose of this document is to provide canonical reference artifacts, example data structures, example package layouts, example manifests, example runtime objects, and example testing fixtures for GARI v1.0.

The Release Candidate defines the architecture of GARI.

The Implementation Specification defines how that architecture should be realized in software.

This document provides illustrative examples showing how the concepts, structures, and artifacts defined by those documents may be represented in practice.

The examples contained within this document are intended to support implementation, testing, interoperability evaluation, fixture generation, reproducibility activities, and future conformance efforts.

The examples are designed to be machine-readable, internally consistent, and suitable for direct use as implementation references and testing resources.

This document does not introduce new architecture, concepts, runtime behavior, or implementation requirements.

Instead, it provides illustrative realizations of artifacts already defined by the authoritative GARI specifications.

---

## 1.2 Relationship to the Authoritative Specifications

This document is subordinate to the authoritative GARI specifications.

Normative authority remains with:

```text
GARI-v1.0-Specification-Release-Candidate-Reconciled.md
```

and

```text
GARI-v1.0-Implementation-Specification.md
```

The Release Candidate remains the authoritative architectural specification.

The Implementation Specification remains the authoritative engineering realization specification.

This document derives exclusively from those two sources.

Its purpose is to provide examples and reference artifacts that assist implementers in understanding and realizing the structures defined by the authoritative specifications.

If an example contained within this document appears to conflict with an authoritative requirement, the authoritative requirement SHALL govern.

The authority hierarchy for GARI documentation is therefore:

```text
Release Candidate

takes precedence over

Implementation Specification

takes precedence over

Reference Data Schemas
```

This document SHALL NOT be interpreted as modifying or extending the authoritative specifications.

---

## 1.3 Intended Audience

This document is intended for:

* software developers;
* web application developers;
* implementation teams;
* AI coding systems;
* Codex implementations;
* testing engineers;
* interoperability reviewers;
* implementation auditors;
* reproducibility reviewers;
* future conformance program participants.

Readers are expected to be familiar with the concepts defined in the Release Candidate and the implementation guidance defined in the Implementation Specification.

This document assumes familiarity with concepts such as:

* Goal-bearing FAIR Digital Object (GB-FDO);
* CBK-bearing FAIR Digital Object (CBKB-FDO);
* Layer;
* Layer Image;
* Input Package;
* Alignment Engine;
* Alignment Engine Profile;
* Alignment Result Graph;
* Constructed Realization;
* Output Package;
* Saved Run Package.

Normative definitions of these concepts remain within the authoritative specifications.

---

## 1.4 Scope

The scope of this document is limited to illustrative representations of GARI artifacts and structures.

Specifically, this document provides:

* canonical JSON examples;
* example runtime objects;
* example package structures;
* example manifests;
* example directory layouts;
* example preservation artifacts;
* example acceptance-test fixtures;
* implementation traceability mappings.

The examples are intended to demonstrate one valid realization of GARI artifacts while preserving consistency with the authoritative specifications.

The scope of this document does not include:

* architectural specification;
* runtime specification;
* Alignment Engine algorithm specification;
* implementation technology selection;
* software architecture specification;
* conformance policy specification;
* implementation certification requirements.

These topics remain governed by the authoritative specifications or future work outside the scope of this document.

---

## 1.5 Document Organization

This document is organized into fifteen chapters and three appendices.

Chapter 2 establishes conventions governing the interpretation of examples contained within this document.

Chapters 3 through 12 provide reference artifacts and example structures corresponding to the major conceptual and runtime artifacts defined by GARI v1.0.

These chapters include examples of:

* FAIR Digital Objects;
* Layers;
* Layer Images;
* Alignment Engine Profiles;
* Input Packages;
* Alignment Result Graphs;
* Constructed Realizations;
* Provenance Objects;
* Output Packages;
* Saved Run Packages.

Chapters 13 and 14 provide example package layouts and manifest structures suitable for implementation and testing activities.

Chapter 15 provides acceptance-test fixtures derived from the authoritative specifications.

Appendix A provides identifier examples.

Appendix B maps example artifacts to the corresponding sections of the Implementation Specification.

Appendix C provides a Runtime Artifact Relationship Guide illustrating relationships among major GARI runtime artifacts.

The examples throughout this document are intended to function collectively as a reference artifact catalog suitable for implementation, testing, interoperability evaluation, and future conformance activities.

---

## 1.6 Chapter Summary

This chapter introduced the purpose, scope, audience, authority relationships, and organization of the GARI v1.0 Reference Data Schemas document.

The chapter established that this document functions as an informative companion to the Release Candidate and Implementation Specification and provides canonical examples of GARI artifacts and structures.

The chapter also defined the intended audience and described how the document is organized.

Subsequent chapters establish conventions for interpreting examples and then provide reference artifacts corresponding to the major conceptual and runtime structures defined by GARI v1.0.

---

# Chapter 2 — Conventions

## 2.1 Example Interpretation Rules

### 2.1.1 Purpose

This section defines the conventions governing interpretation of all examples contained within this document.

These conventions apply to:

* JSON examples;
* runtime object examples;
* package examples;
* manifest examples;
* directory layout examples;
* fixture examples;
* identifier examples.

The purpose of these conventions is to ensure that examples are interpreted consistently and do not inadvertently create new requirements beyond those established by the authoritative GARI specifications.

---

### 2.1.2 Informative Status of Examples

All examples contained within this document are informative.

The examples illustrate one valid realization of GARI artifacts and structures.

Examples SHALL NOT be interpreted as normative requirements unless the corresponding requirement is explicitly specified within the authoritative specifications.

Normative requirements remain exclusively within:

```text
GARI-v1.0-Specification-Release-Candidate-Reconciled.md
```

and

```text
GARI-v1.0-Implementation-Specification.md
```

---

### 2.1.3 Authority Hierarchy

If a conflict appears to exist among:

* an example in this document;
* the Implementation Specification; or
* the Release Candidate;

authority SHALL be determined according to the following hierarchy:

```text
Release Candidate

takes precedence over

Implementation Specification

takes precedence over

Reference Data Schemas
```

Examples SHALL be interpreted consistently with the authoritative specifications.

---

### 2.1.4 Illustrative Values

Example values appearing within this document are illustrative.

Illustrative values include:

* identifiers;
* timestamps;
* metadata values;
* file names;
* directory names;
* package names;
* example Goal descriptions;
* example CBK descriptions.

Such values are provided solely to improve readability and implementation understanding.

Illustrative values SHALL NOT be interpreted as required formats unless explicitly specified by an authoritative requirement.

---

### 2.1.5 No New Requirements Rule

Examples SHALL NOT introduce:

* new concepts;
* new architecture;
* new runtime behavior;
* new implementation requirements;
* new Alignment Engine requirements;
* new conformance requirements.

Examples exist solely to illustrate structures already defined by the authoritative specifications.

---

## 2.2 JSON Conventions

### 2.2.1 Purpose

This section defines conventions used within JSON examples throughout this document.

These conventions are intended to improve readability and consistency.

---

### 2.2.2 Example Serialization

JSON examples are presented using conventional JSON notation.

The examples are intended to be machine-readable whenever practical.

Minor formatting adjustments MAY be used for readability.

---

### 2.2.3 Placeholder Values

Examples frequently use placeholder values such as:

```json
{
  "id": "string"
}
```

or

```json
{
  "timestamp": "2026-06-19T00:00:00Z"
}
```

Placeholder values indicate expected value types and do not prescribe specific implementation values.

---

### 2.2.4 Example Arrays

Arrays shown within examples are illustrative.

An array containing one element does not imply a maximum cardinality of one unless such cardinality is defined by the authoritative specifications.

---

### 2.2.5 Example Objects

Example objects are intended to demonstrate structure and relationships among fields.

Presence of a field within an example SHALL NOT be interpreted as creating a mandatory requirement unless that field is required by the authoritative specifications.

---

## 2.3 Identifier Conventions

### 2.3.1 Purpose

This section defines conventions used for identifiers throughout this document.

The conventions are intended to improve consistency across examples.

They do not define required identifier formats.

---

### 2.3.2 Example Identifier Categories

Examples within this document may include identifiers for:

* FAIR Digital Objects;
* Goals;
* CBK Artifacts;
* Layers;
* Layer Images;
* Alignment Runs;
* Input Packages;
* Output Packages;
* Alignment Result Graphs;
* Constructed Realizations;
* Saved Run Packages.

---

### 2.3.3 Human-Readable Example Identifiers

Examples generally use human-readable identifiers.

Examples may include values such as:

```text
gbfdo-goal-001
cbkbfdo-001
run-2026-0001
output-2026-0001
```

Such identifiers are illustrative only.

Implementations MAY use any identifier scheme consistent with the authoritative specifications.

---

### 2.3.4 Persistent Identifiers

Where examples illustrate FAIR Digital Objects, example persistent identifiers are intended only to demonstrate identifier placement within artifact structures.

The examples SHALL NOT be interpreted as prescribing a specific PID technology, syntax, or registration authority.

---

## 2.4 Timestamp Conventions

### 2.4.1 Purpose

This section defines timestamp conventions used throughout example artifacts.

---

### 2.4.2 ISO 8601 Representation

Example timestamps generally use ISO 8601 UTC notation.

Example:

```text
2026-06-19T12:00:00Z
```

This convention aligns with recommendations contained within the Implementation Specification.

---

### 2.4.3 Illustrative Nature

Example timestamps are illustrative.

Timestamp values do not represent actual execution events.

Implementations MAY use equivalent timestamp representations consistent with authoritative requirements.

---

### 2.4.4 Temporal Relationships

Where examples contain multiple timestamps, the timestamps are intended to illustrate logical ordering of events such as:

```text
Layer Image Creation

→ Input Package Creation

→ Alignment Run Execution

→ Output Package Creation

→ Saved Run Package Creation
```

These examples SHALL NOT be interpreted as prescribing implementation timing behavior.

---

## 2.5 Examples Versus Requirements

### 2.5.1 Purpose

This section clarifies the distinction between examples and requirements.

---

### 2.5.2 Requirements

Requirements originate from the authoritative specifications.

Requirements define:

* architecture;
* concepts;
* runtime behavior;
* implementation behavior;
* validation behavior;
* conformance behavior.

Requirements use normative language such as:

```text
SHALL
SHALL NOT
SHOULD
SHOULD NOT
MAY
```

when specified by the authoritative documents.

---

### 2.5.3 Examples

Examples illustrate one valid realization of an artifact or structure.

Examples exist to assist:

* implementation;
* testing;
* interoperability evaluation;
* fixture construction;
* documentation;
* training;
* reproducibility activities.

Examples do not create requirements.

---

### 2.5.4 Traceability

Each major artifact example in this document includes traceability information linking the example to:

* the Release Candidate;
* the Implementation Specification.

Traceability information is provided to assist implementers in locating the authoritative source material from which each example is derived.

Traceability references are informative and SHALL NOT supersede the authoritative specifications.

---

## 2.6 Chapter Summary

This chapter established the conventions governing interpretation of all examples contained within this document.

The chapter defined:

* example interpretation rules;
* JSON conventions;
* identifier conventions;
* timestamp conventions;
* distinctions between examples and requirements.

These conventions govern all subsequent artifact examples and ensure that the examples remain informative, consistent, and subordinate to the authoritative GARI specifications.

Subsequent chapters provide canonical examples of the major conceptual, runtime, provenance, and preservation artifacts defined by GARI v1.0.

---

# Chapter 3 — Canonical FDO Examples

## 3.1 Minimal GB-FDO

### 3.1.1 Purpose

This section provides a canonical example of a minimal Goal-bearing FAIR Digital Object (GB-FDO).

The example illustrates the minimum structural elements required for a GB-FDO recognized by GARI v1.0.

The example is informative and intended to support implementation, testing, interoperability evaluation, and fixture generation.

---

### 3.1.2 Traceability

Derived From:

Release Candidate

* Section 3.2.9 — Goal-bearing FAIR Digital Object
* Section 3.3.2 — Minimal FDO Specification
* Section 3.3.8 — Goal-Bearing FDO Profile
* Section 3.3.9 — Goal Interpretation Rule

Implementation Specification

* Section 7.3 — FDO Reference Model

---

### 3.1.3 Minimal Example

```json
{
  "pid": "gbfdo-goal-001",
  "type": "GB-FDO",
  "profileReference": "goal-profile-v1",
  "metadata": {
    "goalRepresentations": [
      {
        "representationType": "text",
        "value": "Estimate risk of 30-day hospital readmission."
      }
    ]
  },
  "bitstreamReference": "goal-representation.json"
}
```

---

### 3.1.4 Rich Example

```json
{
  "pid": "gbfdo-goal-001",
  "type": "GB-FDO",
  "profileReference": "goal-profile-v1",
  "metadata": {
    "title": "Thirty-Day Readmission Risk Goal",
    "description": "Representations of a computational goal concerning readmission risk estimation.",
    "goalRepresentations": [
      {
        "representationType": "text",
        "value": "Estimate risk of 30-day hospital readmission."
      }
    ]
  },
  "bitstreamReference": "goal-representation.json"
}
```

---

### 3.1.5 Notes

This example demonstrates:

* one GB-FDO;
* one Goal;
* one Goal Representation.

The example does not imply that a GB-FDO is limited to a single Goal Representation.

The Release Candidate requires that a GB-FDO represent exactly one Goal.

Multiple Goal Representations MAY exist provided they represent the same Goal.

The example metadata is illustrative only.

---

## 3.2 Minimal CBKB-FDO

### 3.2.1 Purpose

This section provides a canonical example of a minimal CBK-bearing FAIR Digital Object (CBKB-FDO).

The example illustrates the minimum structural elements required for a CBKB-FDO recognized by GARI v1.0.

---

### 3.2.2 Traceability

Derived From:

Release Candidate

* Section 3.2.10 — CBK-bearing FAIR Digital Object
* Section 3.3.2 — Minimal FDO Specification
* Section 3.3.10 — CBK-Bearing FDO Profile

Implementation Specification

* Section 7.3 — FDO Reference Model

---

### 3.2.3 Minimal Example

```json
{
  "pid": "cbkbfdo-001",
  "type": "CBKB-FDO",
  "profileReference": "cbk-profile-v1",
  "metadata": {
    "artifactName": "Readmission Risk Model"
  },
  "bitstreamReference": "model-artifact.bin"
}
```

---

### 3.2.4 Rich Example

```json
{
  "pid": "cbkbfdo-001",
  "type": "CBKB-FDO",
  "profileReference": "cbk-profile-v1",
  "metadata": {
    "artifactName": "Readmission Risk Model",
    "description": "A computable artifact intended to estimate patient readmission risk.",
    "knowledgeApplicationMethods": [
      {
        "name": "Readmission Risk Estimation",
        "inputs": [
          {
            "item": "Patient Data"
          }
        ],
        "outputs": [
          {
            "item": "Risk Estimate"
          }
        ]
      }
    ]
  },
  "bitstreamReference": "model-artifact.bin"
}
```

---

### 3.2.5 Notes

This example demonstrates:

* one CBKB-FDO;
* one CBK Artifact;
* optional Knowledge Application Method structures.

The Release Candidate requires that one CBKB-FDO represent exactly one CBK Artifact.

The example does not prescribe how CBK Artifacts are implemented or executed.

GARI does not execute CBK Artifacts.

---

## 3.3 Multi-Representation Goal Example

### 3.3.1 Purpose

This section illustrates how multiple Goal Representations may exist within a single GB-FDO while preserving the requirement that the GB-FDO represent exactly one Goal.

This example is intended to support implementation of Goal Representation handling and validation logic.

---

### 3.3.2 Traceability

Derived From:

Release Candidate

* Section 3.2.2 — Goal
* Section 3.2.3 — Goal Representation
* Section 3.2.9 — Goal-bearing FAIR Digital Object
* Section 3.3.9 — Goal Interpretation Rule

Implementation Specification

* Section 7.3 — FDO Reference Model

---

### 3.3.3 Example

```json
{
  "pid": "gbfdo-goal-002",
  "type": "GB-FDO",
  "profileReference": "goal-profile-v1",
  "metadata": {
    "goalRepresentations": [
      {
        "representationType": "text",
        "value": "Estimate risk of 30-day hospital readmission."
      },
      {
        "representationType": "structured",
        "value": {
          "goalType": "risk-estimation",
          "subject": "hospital-readmission",
          "timeHorizon": "30-days"
        }
      },
      {
        "representationType": "dfsk",
        "value": {
          "goal": "EstimateReadmissionRisk",
          "parameters": {
            "window": "30-days"
          }
        }
      }
    ]
  },
  "bitstreamReference": "goal-representations.json"
}
```

---

### 3.3.4 Notes

This example demonstrates:

* one GB-FDO;
* one Goal;
* multiple Goal Representations.

The Release Candidate requires that all Goal Representations contained within a GB-FDO be interpreted as alternative representations of the same Goal.

The example SHALL NOT be interpreted as introducing a required Goal Representation vocabulary or serialization format.

The representation types shown are illustrative only.

Implementations MAY support additional representation forms consistent with the governing FDO profile.

---

## 3.4 Chapter Summary

This chapter provided canonical examples of Goal-bearing and CBK-bearing FAIR Digital Objects recognized by GARI v1.0.

The chapter illustrated:

* minimal GB-FDO structures;
* minimal CBKB-FDO structures;
* richer example FDO structures;
* multi-representation Goal examples.

These examples demonstrate how the FAIR Digital Object concepts defined by the Release Candidate may be represented within implementation artifacts while remaining consistent with the authoritative specifications.

Subsequent chapters build upon these examples to demonstrate Layers, Layer Images, Input Packages, and other runtime artifacts derived from collections of FAIR Digital Objects.

---

# Chapter 4 — Layer Examples

## 4.1 Minimal Layer

### 4.1.1 Purpose

This section provides a canonical example of a minimal valid Layer.

The Release Candidate defines a Layer as a conceptual construct representing the active collection of GB-FDOs and CBKB-FDOs available for a specific Alignment Run.

A valid Layer requires:

* one or more GB-FDOs; and
* one or more CBKB-FDOs.

This example illustrates the smallest Layer capable of supporting an Alignment Run.

---

### 4.1.2 Traceability

Derived From:

Release Candidate

* Section 3.2.11 — Layer
* Section 3.4.2 — Definition
* Section 3.4.4 — Minimum Valid Layer
* Section 3.4.6 — Layer Establishment
* Section 3.4.12 — Relationship to Alignment Runs

Implementation Specification

* Section 7.4 — Layer State Model

---

### 4.1.3 Minimal Example

```json
{
  "gbFdos": [
    {
      "pid": "gbfdo-goal-001",
      "type": "GB-FDO"
    }
  ],
  "cbkbFdos": [
    {
      "pid": "cbkbfdo-001",
      "type": "CBKB-FDO"
    }
  ],
  "isEstablished": true
}
```

---

### 4.1.4 Rich Example

```json
{
  "gbFdos": [
    {
      "pid": "gbfdo-goal-001",
      "type": "GB-FDO",
      "profileReference": "goal-profile-v1"
    }
  ],
  "cbkbFdos": [
    {
      "pid": "cbkbfdo-001",
      "type": "CBKB-FDO",
      "profileReference": "cbk-profile-v1"
    }
  ],
  "isEstablished": true,
  "establishedAt": "2026-06-19T12:00:00Z",
  "validation": {
    "errors": [],
    "warnings": []
  }
}
```

---

### 4.1.5 Notes

This example demonstrates:

* one GB-FDO;
* one CBKB-FDO;
* a valid established Layer.

The Layer itself does not possess an independent persistent identity.

The identifiers shown belong to participating FDOs rather than to the Layer itself.

The example SHALL NOT be interpreted as introducing a Layer identifier.

---

## 4.2 Multi-Goal Layer

### 4.2.1 Purpose

This section illustrates a Layer containing multiple Goals and multiple CBK Artifacts.

Such Layers allow Alignment Engines to evaluate relationships among multiple Goal-bearing and CBK-bearing FAIR Digital Objects during a single Alignment Run.

---

### 4.2.2 Traceability

Derived From:

Release Candidate

* Section 3.2.11 — Layer
* Section 3.4.4 — Minimum Valid Layer
* Section 3.4.5 — Layer Assembly
* Section 3.4.6 — Layer Establishment
* Section 3.4.7 — Fixed Layer Rule

Implementation Specification

* Section 7.4 — Layer State Model

---

### 4.2.3 Example

```json
{
  "gbFdos": [
    {
      "pid": "gbfdo-goal-001",
      "type": "GB-FDO"
    },
    {
      "pid": "gbfdo-goal-002",
      "type": "GB-FDO"
    },
    {
      "pid": "gbfdo-goal-003",
      "type": "GB-FDO"
    }
  ],
  "cbkbFdos": [
    {
      "pid": "cbkbfdo-001",
      "type": "CBKB-FDO"
    },
    {
      "pid": "cbkbfdo-002",
      "type": "CBKB-FDO"
    },
    {
      "pid": "cbkbfdo-003",
      "type": "CBKB-FDO"
    }
  ],
  "isEstablished": true,
  "establishedAt": "2026-06-19T12:00:00Z",
  "validation": {
    "errors": [],
    "warnings": []
  }
}
```

---

### 4.2.4 Notes

This example demonstrates:

* multiple Goals;
* multiple CBK Artifacts;
* one established Layer.

The example does not imply any relationship among the participating FDOs.

Relationships are determined only through Alignment Engine execution.

The Layer functions as the active collection of available FDOs for an Alignment Run.

The Layer itself does not assert alignment.

---

## 4.3 Layer Assembly Example

### 4.3.1 Purpose

This section illustrates how a Layer may be assembled incrementally through multiple user actions.

The Release Candidate explicitly permits Layer assembly through one or more user actions.

---

### 4.3.2 Traceability

Derived From:

Release Candidate

* Section 3.4.5 — Layer Assembly
* Section 3.4.6 — Layer Establishment

Implementation Specification

* Section 4.5 — Layer Manager
* Section 7.4 — Layer State Model

---

### 4.3.3 Example Progression

#### Step 1 — Initial State

```json
{
  "gbFdos": [],
  "cbkbFdos": [],
  "isEstablished": false
}
```

#### Step 2 — Goal Loaded

```json
{
  "gbFdos": [
    {
      "pid": "gbfdo-goal-001",
      "type": "GB-FDO"
    }
  ],
  "cbkbFdos": [],
  "isEstablished": false
}
```

#### Step 3 — CBK Artifact Loaded

```json
{
  "gbFdos": [
    {
      "pid": "gbfdo-goal-001",
      "type": "GB-FDO"
    }
  ],
  "cbkbFdos": [
    {
      "pid": "cbkbfdo-001",
      "type": "CBKB-FDO"
    }
  ],
  "isEstablished": true
}
```

---

### 4.3.4 Notes

This example illustrates the transition from:

```text
No Layer

→ Partial Layer

→ Established Layer
```

Layer establishment occurs when at least:

* one GB-FDO; and
* one CBKB-FDO

are present.

This example is intended to support implementation and testing of Layer establishment logic.

---

## 4.4 Chapter Summary

This chapter provided canonical examples of Layer structures recognized by GARI v1.0.

The chapter illustrated:

* a minimal valid Layer;
* a multi-goal Layer;
* Layer assembly through multiple user actions.

These examples demonstrate how collections of Goal-bearing and CBK-bearing FAIR Digital Objects may participate in Alignment Runs while preserving the conceptual and non-persistent nature of Layers defined by the Release Candidate.

The Layer examples established in this chapter provide the foundation for the Layer Image examples presented in the following chapter.

---

# Chapter 5 — Layer Image Examples

## 5.1 Minimal Layer Image

### 5.1.1 Purpose

This section provides a canonical example of a minimal Layer Image.

The Release Candidate defines a Layer Image as a representation of an established Layer.

Layer Images serve as the representational bridge between:

* established Layers;
* Input Packages;
* Output Packages;
* Saved Run Packages.

The examples in this chapter illustrate how an established Layer may be represented without introducing metadata beyond that contained within the participating FAIR Digital Objects.

---

### 5.1.2 Traceability

Derived From:

Release Candidate

* Section 3.2.12 — Layer Image
* Section 3.4.10 — Relationship to Input Packages
* Section 4.3.3 — Relationship to Layers
* Section 4.5.6.2 — Layer Image
* Section 5.4.7 — Layer Image Provenance
* Section 6.4.7.2 — Layer Image

Implementation Specification

* Section 7.5 — Layer Image Model

---

### 5.1.3 Minimal Example

```json
{
  "layerImageId": "layer-image-0001",
  "createdAt": "2026-06-19T12:00:00Z",
  "gbFdoReferences": [
    {
      "pid": "gbfdo-goal-001",
      "type": "GB-FDO"
    }
  ],
  "cbkbFdoReferences": [
    {
      "pid": "cbkbfdo-001",
      "type": "CBKB-FDO"
    }
  ]
}
```

---

### 5.1.4 Rich Example

```json
{
  "layerImageId": "layer-image-0001",
  "createdAt": "2026-06-19T12:00:00Z",
  "gbFdoReferences": [
    {
      "pid": "gbfdo-goal-001",
      "type": "GB-FDO",
      "profileReference": "goal-profile-v1",
      "metadata": {
        "goalRepresentations": [
          {
            "representationType": "dfsk",
            "value": {
              "desiredOutputs": [
                "readmission-risk-score"
              ]
            }
          }
        ]
      }
    }
  ],
  "cbkbFdoReferences": [
    {
      "pid": "cbkbfdo-001",
      "type": "CBKB-FDO",
      "profileReference": "cbk-profile-v1",
      "metadata": {
        "producedOutputs": [
          "readmission-risk-score"
        ]
      }
    }
  ]
}
```

---

### 5.1.5 Notes

This example demonstrates:

* one established Layer;
* one Layer Image;
* one GB-FDO reference;
* one CBKB-FDO reference;
* metadata potentially available for alignment.

The Layer Image is not the Layer itself.

The Layer Image is a representation of the Layer.

The Layer Image SHALL NOT be interpreted as introducing an independent Layer identity.

---

## 5.2 Alignment-Oriented Layer Image Example

### 5.2.1 Purpose

This section illustrates the role of the Layer Image as the metadata universe available to an Alignment Engine during an Alignment Run.

The Release Candidate defines GARI as a metadata-driven alignment instrument.

Accordingly, Alignment Engines operate upon metadata represented within the Layer Image.

This section demonstrates the types of metadata that may be visible to an Alignment Engine without prescribing any specific alignment algorithm.

The examples are illustrative only.

They are intended to make the concept of metadata-driven alignment easier to understand.

---

### 5.2.2 Traceability

Derived From:

Release Candidate

* Section 3.2.12 — Layer Image
* Section 4.3.3 — Relationship to Layers
* Section 4.4 — Input Package
* Section 4.5 — Alignment Engine
* Principle: Metadata-Driven Alignment

Implementation Specification

* Section 7.5 — Layer Image Model
* Section 7.6 — Input Package Model

---

### 5.2.3 Metadata Visibility Concept

A Layer Image represents the metadata available for alignment during a run.

Conceptually:

```text
Goal-bearing FDO Metadata
    Desired Inputs
    Desired Outputs

                ↓

          Layer Image

                ↑

CBK-bearing FDO Metadata
    Accepted Inputs
    Produced Outputs
```

Alignment Engines operate upon metadata visible through the Layer Image.

The Layer Image does not perform alignment.

The Layer Image exposes metadata that may be evaluated by an Alignment Engine.

---

### 5.2.4 Example — Potential Positive Alignment

#### Goal-bearing FDO Metadata

```json
{
  "pid": "gbfdo-goal-001",
  "type": "GB-FDO",
  "metadata": {
    "goalRepresentations": [
      {
        "representationType": "dfsk",
        "value": {
          "desiredInputs": [
            "patient-age",
            "diagnosis-history"
          ],
          "desiredOutputs": [
            "readmission-risk-score"
          ]
        }
      }
    ]
  }
}
```

#### CBK-bearing FDO Metadata

```json
{
  "pid": "cbkbfdo-001",
  "type": "CBKB-FDO",
  "metadata": {
    "artifactType": "prediction-model",
    "acceptedInputs": [
      "patient-age",
      "diagnosis-history"
    ],
    "producedOutputs": [
      "readmission-risk-score"
    ]
  }
}
```

#### Example Layer Image

```json
{
  "layerImageId": "layer-image-0003",
  "createdAt": "2026-06-19T12:00:00Z",
  "gbFdoReferences": [
    {
      "pid": "gbfdo-goal-001",
      "metadata": {
        "goalRepresentations": [
          {
            "representationType": "dfsk",
            "value": {
              "desiredInputs": [
                "patient-age",
                "diagnosis-history"
              ],
              "desiredOutputs": [
                "readmission-risk-score"
              ]
            }
          }
        ]
      }
    }
  ],
  "cbkbFdoReferences": [
    {
      "pid": "cbkbfdo-001",
      "metadata": {
        "acceptedInputs": [
          "patient-age",
          "diagnosis-history"
        ],
        "producedOutputs": [
          "readmission-risk-score"
        ]
      }
    }
  ]
}
```

#### Notes

This example illustrates metadata that may support a positive alignment determination.

The example does not prescribe how an Alignment Engine evaluates the metadata.

The example merely illustrates metadata visibility.

---

### 5.2.5 Example — Potential Negative Alignment

#### Goal Metadata

```json
{
  "desiredOutputs": [
    "30-day-readmission-risk"
  ]
}
```

#### CBK Metadata

```json
{
  "producedOutputs": [
    "medication-adherence-score"
  ]
}
```

#### Notes

This example illustrates metadata that may support a determination that no alignment relationship exists.

The determination itself remains the responsibility of the Alignment Engine.

---

### 5.2.6 Example — Multiple Candidate CBK Artifacts

#### Goal Metadata

```json
{
  "desiredOutputs": [
    "readmission-risk-score"
  ]
}
```

#### Candidate CBK Metadata

```json
[
  {
    "pid": "cbkbfdo-001",
    "producedOutputs": [
      "readmission-risk-score"
    ]
  },
  {
    "pid": "cbkbfdo-002",
    "producedOutputs": [
      "mortality-risk-score"
    ]
  },
  {
    "pid": "cbkbfdo-003",
    "producedOutputs": [
      "readmission-risk-score"
    ]
  }
]
```

#### Notes

This example illustrates metadata that may expose multiple potentially relevant CBK-bearing FDOs.

Selection, ranking, scoring, or evaluation of candidates remains entirely under Alignment Engine control.

The Layer Image merely exposes metadata that may be considered during alignment.

---

### 5.2.7 Key Observation

The Layer Image is not simply a list of participating FAIR Digital Objects.

For alignment purposes, the Layer Image represents the metadata available to an Alignment Engine during a run.

Accordingly, the Layer Image may be understood as:

```text
The metadata universe available
for alignment evaluation
during an Alignment Run.
```

This interpretation is intended to aid understanding of metadata-driven alignment and does not introduce additional runtime behavior.

---

## 5.3 Multi-Object Layer Image

### 5.3.1 Purpose

This section illustrates a Layer Image representing a Layer containing multiple Goal-bearing and CBK-bearing FAIR Digital Objects.

---

### 5.3.2 Traceability

Derived From:

Release Candidate

* Section 3.2.12 — Layer Image
* Section 4.3.3 — Relationship to Layers

Implementation Specification

* Section 7.5 — Layer Image Model

---

### 5.3.3 Example

```json
{
  "layerImageId": "layer-image-0002",
  "gbFdoReferences": [
    {
      "pid": "gbfdo-goal-001",
      "metadata": {
        "goalRepresentations": [
          {
            "representationType": "dfsk",
            "value": {
              "desiredOutputs": [
                "readmission-risk-score"
              ]
            }
          }
        ]
      }
    },
    {
      "pid": "gbfdo-goal-002",
      "metadata": {
        "goalRepresentations": [
          {
            "representationType": "dfsk",
            "value": {
              "desiredOutputs": [
                "mortality-risk-score"
              ]
            }
          }
        ]
      }
    }
  ],
  "cbkbFdoReferences": [
    {
      "pid": "cbkbfdo-001",
      "metadata": {
        "producedOutputs": [
          "readmission-risk-score"
        ]
      }
    },
    {
      "pid": "cbkbfdo-002",
      "metadata": {
        "producedOutputs": [
          "mortality-risk-score"
        ]
      }
    }
  ]
}
```

### 5.3.4 Notes

This example demonstrates how multiple Goals and multiple CBK Artifacts may contribute metadata to a single Layer Image.

The Layer Image records metadata visibility.

The Layer Image does not itself perform alignment.

---

## 5.4 Layer-to-Layer Image Transformation Example

### 5.4.1 Traceability

Derived From:

Release Candidate

* Section 3.2.12 — Layer Image
* Section 4.3.3 — Relationship to Layers

Implementation Specification

* Section 7.5 — Layer Image Model

---

### 5.4.2 Example

```text
Layer

↓

Metadata visible to alignment

↓

Layer Image
```

The Layer Image represents the metadata derived from the established Layer and made available for alignment evaluation.

---

## 5.5 Layer Image Preservation Example

### 5.5.1 Traceability

Derived From:

Release Candidate

* Section 5.4.7 — Layer Image Provenance
* Section 6.4.7.2 — Layer Image

Implementation Specification

* Section 7.5 — Layer Image Model
* Section 7.8 — Output Package Model

---

### 5.5.2 Example

```text
Established Layer

↓

Layer Image A

↓

Input Package

↓

Output Package
   contains Layer Image A

↓

Saved Run Package
   contains Layer Image A
```

### 5.5.3 Notes

The Layer Image preserved within a Saved Run Package is intended to be the same Layer Image associated with the corresponding Output Package.

This continuity supports:

* inspection;
* interpretation;
* comparison;
* reproducibility.

---

## 5.6 Chapter Summary

This chapter provided canonical examples of Layer Images recognized by GARI v1.0.

The chapter illustrated:

* minimal Layer Images;
* metadata visibility for alignment;
* potential positive and negative alignment scenarios;
* multiple candidate CBK artifacts;
* multi-object Layer Images;
* transformation from Layer to Layer Image;
* preservation of Layer Images across runtime and preservation artifacts.

Most importantly, the chapter illustrated that a Layer Image functions as the metadata universe available to an Alignment Engine during an Alignment Run.

The examples demonstrate how metadata represented within Layer Images may support alignment evaluation without prescribing any Alignment Engine algorithm.

The Layer Image therefore serves as both:

* a representation of an established Layer; and
* the metadata available for alignment during a run.

Subsequent chapters build upon this foundation through Alignment Engine Profile examples and Input Package examples.

# Chapter 6 — Alignment Engine Profile Examples

## 6.1 Minimal Engine Profile

### 6.1.1 Purpose

This section provides a canonical example of a minimal Alignment Engine Profile.

The Release Candidate requires that Alignment Engines expose profile information describing the engine and its integration characteristics.

Engine Profiles enable GARI implementations to:

* identify available Alignment Engines;
* communicate supported capabilities;
* support integration;
* support reproducibility;
* support inspection of Alignment Run results.

The examples in this chapter are illustrative only.

---

### 6.1.2 Traceability

Derived From:

Release Candidate

* Section 3.2.15 — Alignment Engine
* Section 4.5 — Alignment Engine
* Section 4.5.3 — Engine Profile
* Section 4.5.4 — Engine Registration

Implementation Specification

* Section 7.7 — Alignment Engine Profile Model

---

### 6.1.3 Minimal Example

```json id="rhv4ti"
{
  "engineName": "Example Alignment Engine",
  "engineVersion": "1.0.0"
}
```

---

### 6.1.4 Notes

This example illustrates the minimum information necessary to identify an Alignment Engine.

The example does not imply that this information alone is sufficient for operational integration.

More complete Engine Profiles are illustrated in subsequent sections.

---

## 6.2 Rich Engine Profile

### 6.2.1 Purpose

This section illustrates a richer Alignment Engine Profile suitable for implementation and integration scenarios.

The example demonstrates the types of metadata that may be communicated through an Engine Profile.

---

### 6.2.2 Traceability

Derived From:

Release Candidate

* Section 4.5.3 — Engine Profile
* Section 4.5.5 — Engine Configuration Metadata
* Section 4.5.7 — Alignment Engine Selection

Implementation Specification

* Section 7.7 — Alignment Engine Profile Model

---

### 6.2.3 Example

```json id="5m6rzv"
{
  "engineName": "DFSK Alignment Engine",
  "engineVersion": "1.0.0",
  "engineDescription": "Example metadata-driven alignment engine.",
  "supportedGoalRepresentationTypes": [
    "dfsk"
  ],
  "supportedFdoTypes": [
    "GB-FDO",
    "CBKB-FDO"
  ],
  "configurationSchemaVersion": "1.0",
  "profileVersion": "1.0"
}
```

---

### 6.2.4 Notes

This example demonstrates:

* engine identification metadata;
* supported Goal Representation metadata;
* supported FDO type metadata;
* profile version metadata.

The example SHALL NOT be interpreted as prescribing a specific Engine Profile schema.

Implementations MAY expose additional metadata consistent with the authoritative specifications.

---

## 6.3 Engine Capability Declaration Example

### 6.3.1 Purpose

This section illustrates how an Alignment Engine Profile may communicate capabilities relevant to engine selection and run preparation.

The example is intended to support understanding of how Engine Profiles help establish expectations regarding engine behavior.

The example does not prescribe how an engine performs alignment.

---

### 6.3.2 Traceability

Derived From:

Release Candidate

* Section 4.5.3 — Engine Profile
* Section 4.5.7 — Alignment Engine Selection

Implementation Specification

* Section 7.7 — Alignment Engine Profile Model

---

### 6.3.3 Capability Declaration Example

```json id="g4s6x9"
{
  "engineName": "DFSK Alignment Engine",
  "engineVersion": "1.0.0",
  "supportedGoalRepresentationTypes": [
    "dfsk"
  ],
  "supportedMetadataPatterns": [
    "desiredInputs",
    "desiredOutputs",
    "acceptedInputs",
    "producedOutputs"
  ],
  "supportedFdoTypes": [
    "GB-FDO",
    "CBKB-FDO"
  ],
  "supportsConstructedRealizations": true,
  "supportsMultipleCandidateResults": true
}
```

---

### 6.3.4 Example Interpretation

Conceptually:

```text id="tcezfa"
Layer Image

↓

Visible Metadata

↓

Engine Capability Declaration

↓

Potential Alignment Evaluation
```

An Engine Profile may communicate the categories of metadata that an engine is capable of evaluating.

For example, an engine may indicate support for metadata such as:

```text id="lgjlwm"
desiredInputs
desiredOutputs
acceptedInputs
producedOutputs
```

The profile does not prescribe how the metadata is evaluated.

The profile merely communicates capability.

---

### 6.3.5 Notes

This example is particularly useful in the context of metadata-driven alignment.

The example demonstrates that Engine Profiles may communicate:

* what metadata patterns an engine understands;
* what representation types an engine supports;
* what artifact types an engine supports.

The example SHALL NOT be interpreted as prescribing a standard metadata vocabulary.

---

## 6.4 Engine Configuration Metadata Example

### 6.4.1 Purpose

This section illustrates example configuration metadata associated with an Alignment Engine.

Configuration metadata supports interpretation, reproducibility, and inspection of Alignment Run results.

The example is illustrative only.

---

### 6.4.2 Traceability

Derived From:

Release Candidate

* Section 4.5.5 — Engine Configuration Metadata
* Section 5.4.5 — Output Package Engine Metadata

Implementation Specification

* Section 7.7 — Alignment Engine Profile Model
* Section 7.8 — Output Package Model

---

### 6.4.3 Example

```json id="r1a8t2"
{
  "engineName": "DFSK Alignment Engine",
  "engineVersion": "1.0.0",
  "configuration": {
    "matchingMode": "default",
    "candidateLimit": 10
  }
}
```

---

### 6.4.4 Notes

The configuration values shown are illustrative.

The example demonstrates the concept of configuration metadata rather than any required configuration structure.

The authoritative specifications intentionally permit Alignment Engines to manage internal behavior independently.

---

## 6.5 Chapter Summary

This chapter provided canonical examples of Alignment Engine Profiles recognized by GARI v1.0.

The chapter illustrated:

* minimal Engine Profiles;
* rich Engine Profiles;
* capability declarations;
* configuration metadata.

The examples demonstrate how Engine Profiles communicate information about Alignment Engines without exposing internal alignment algorithms.

Most importantly, the chapter illustrates how Engine Profiles help establish expectations regarding:

* supported Goal Representation types;
* supported artifact types;
* supported metadata categories;
* configuration metadata.

These examples provide the foundation for the Input Package examples presented in the following chapter, where Layer Images and Engine Profiles are combined to prepare Alignment Runs.


# Chapter 7 — Input Package Examples

## 7.1 Minimal Input Package

### 7.1.1 Purpose

This section provides a canonical example of a minimal Input Package.

The Release Candidate defines the Input Package as the artifact supplied to an Alignment Engine for execution of an Alignment Run.

Input Packages communicate:

* the Layer Image;
* Alignment Engine information;
* run metadata;
* package metadata.

Input Packages are metadata-only artifacts.

They do not contain Goal bitstreams, CBK bitstreams, or executable artifacts.

---

### 7.1.2 Traceability

Derived From:

Release Candidate

* Section 3.2.13 — Input Package
* Section 4.4 — Input Package
* Section 4.4.4 — Metadata-Only Rule
* Section 4.4.5 — Input Package Contents

Implementation Specification

* Section 7.6 — Input Package Model

---

### 7.1.3 Minimal Example

```json id="dlf1yw"
{
  "runId": "run-2026-0001",
  "engineProfileReference": "engine-profile-001",
  "layerImageReference": "layer-image-0001"
}
```

---

### 7.1.4 Notes

This example illustrates the minimum information required to identify:

* the Alignment Run;
* the Alignment Engine;
* the Layer Image.

The example is intentionally minimal and omits additional metadata frequently useful for implementation and reproducibility.

---

## 7.2 Rich Input Package

### 7.2.1 Purpose

This section illustrates a richer Input Package suitable for implementation, testing, and reproducibility activities.

The example demonstrates how Layer Image metadata, engine information, and run metadata may be combined within a single package.

---

### 7.2.2 Traceability

Derived From:

Release Candidate

* Section 4.4 — Input Package
* Section 4.4.5 — Input Package Contents
* Section 4.4.6 — Engine Reference
* Section 4.4.7 — Layer Image Reference

Implementation Specification

* Section 7.6 — Input Package Model

---

### 7.2.3 Example

```json id="b15rte"
{
  "runId": "run-2026-0001",
  "createdAt": "2026-06-19T12:00:00Z",
  "engineProfile": {
    "engineName": "DFSK Alignment Engine",
    "engineVersion": "1.0.0"
  },
  "layerImage": {
    "layerImageId": "layer-image-0003",
    "gbFdoReferences": [
      {
        "pid": "gbfdo-goal-001",
        "metadata": {
          "goalRepresentations": [
            {
              "representationType": "dfsk",
              "value": {
                "desiredInputs": [
                  "patient-age",
                  "diagnosis-history"
                ],
                "desiredOutputs": [
                  "readmission-risk-score"
                ]
              }
            }
          ]
        }
      }
    ],
    "cbkbFdoReferences": [
      {
        "pid": "cbkbfdo-001",
        "metadata": {
          "acceptedInputs": [
            "patient-age",
            "diagnosis-history"
          ],
          "producedOutputs": [
            "readmission-risk-score"
          ]
        }
      }
    ]
  }
}
```

---

### 7.2.4 Notes

This example demonstrates:

* Alignment Run metadata;
* Engine Profile metadata;
* Layer Image metadata;
* alignment-visible metadata.

The Input Package does not perform alignment.

The Input Package provides metadata to an Alignment Engine.

---

## 7.3 Input Package Generation Example

### 7.3.1 Purpose

This section illustrates how an Input Package may be generated from an established Layer and an Engine Profile.

The example demonstrates the relationship among previously introduced artifacts.

---

### 7.3.2 Traceability

Derived From:

Release Candidate

* Section 4.4 — Input Package
* Section 4.4.5 — Input Package Contents
* Section 4.4.6 — Engine Reference
* Section 4.4.7 — Layer Image Reference

Implementation Specification

* Section 7.5 — Layer Image Model
* Section 7.6 — Input Package Model
* Section 7.7 — Alignment Engine Profile Model

---

### 7.3.3 Generation Flow

Conceptually:

```text id="c3l8xv"
Established Layer

↓

Layer Image

+

Engine Profile

+

Run Metadata

↓

Input Package
```

---

### 7.3.4 Example

#### Layer Image

```json id="n6a0hg"
{
  "layerImageId": "layer-image-0003",
  "gbFdoReferences": [
    {
      "pid": "gbfdo-goal-001"
    }
  ],
  "cbkbFdoReferences": [
    {
      "pid": "cbkbfdo-001"
    }
  ]
}
```

#### Engine Profile

```json id="ok5jzd"
{
  "engineName": "DFSK Alignment Engine",
  "engineVersion": "1.0.0"
}
```

#### Generated Input Package

```json id="rf1jzm"
{
  "runId": "run-2026-0001",
  "engineProfile": {
    "engineName": "DFSK Alignment Engine",
    "engineVersion": "1.0.0"
  },
  "layerImageReference": "layer-image-0003"
}
```

---

### 7.3.5 Notes

This example illustrates the construction of an Input Package from previously established runtime artifacts.

The example does not prescribe implementation mechanics.

It demonstrates conceptual artifact relationships.

---

## 7.4 Input Package Validation Example

### 7.4.1 Purpose

This section illustrates validation concepts associated with Input Package preparation.

The examples are intended to support testing and implementation.

They do not prescribe validation algorithms.

---

### 7.4.2 Traceability

Derived From:

Release Candidate

* Section 4.4 — Input Package
* Section 4.4.5 — Input Package Contents

Implementation Specification

* Section 8 — Validation Requirements

---

### 7.4.3 Example — Valid Input Package

```json id="0d5kza"
{
  "runId": "run-2026-0001",
  "engineProfileReference": "engine-profile-001",
  "layerImageReference": "layer-image-0001"
}
```

Validation Outcome:

```text id="7qv5nm"
Valid
```

---

### 7.4.4 Example — Missing Engine Reference

```json id="3ftm9n"
{
  "runId": "run-2026-0001",
  "layerImageReference": "layer-image-0001"
}
```

Validation Outcome:

```text id="v8u8cg"
Invalid
```

Illustrative Reason:

```text id="7vqkpz"
Missing Engine Profile Reference
```

---

### 7.4.5 Example — Missing Layer Image Reference

```json id="7l3txd"
{
  "runId": "run-2026-0001",
  "engineProfileReference": "engine-profile-001"
}
```

Validation Outcome:

```text id="7rknpq"
Invalid
```

Illustrative Reason:

```text id="m0ud0k"
Missing Layer Image Reference
```

---

### 7.4.6 Notes

The examples illustrate validation outcomes rather than validation procedures.

Implementations MAY realize validation using different mechanisms provided they remain consistent with the authoritative specifications.

---

## 7.5 Chapter Summary

This chapter provided canonical examples of Input Packages recognized by GARI v1.0.

The chapter illustrated:

* minimal Input Packages;
* rich Input Packages;
* Input Package generation;
* Input Package validation.

Most importantly, the chapter demonstrated how:

```text id="my2xpo"
Layer Image

+

Engine Profile

+

Run Metadata

↓

Input Package
```

The examples reinforce the role of the Input Package as the metadata artifact supplied to an Alignment Engine for execution of an Alignment Run.

The Input Package does not perform alignment.

Rather, it provides the metadata context upon which Alignment Engines operate.

Subsequent chapters build upon this foundation by illustrating Alignment Result Graphs and Constructed Realizations generated from Alignment Runs.


# Chapter 8 — Alignment Result Graph Examples

## 8.1 Positive Alignment Example

### 8.1.1 Purpose

This section provides a canonical example of a positive Alignment Result Graph.

The example illustrates a case in which an Alignment Engine reports that one or more CBK-bearing FAIR Digital Objects are aligned with a Goal-bearing FAIR Digital Object.

The example is illustrative only.

The example does not prescribe how the alignment determination was made.

---

### 8.1.2 Traceability

Derived From:

Release Candidate

* Section 3.2.17 — Alignment Result Graph
* Section 5.3 — Alignment Results
* Section 5.5 — Constructed Realizations

Implementation Specification

* Section 7.8 — Output Package Model
* Section 7.9 — Alignment Result Graph Model

---

### 8.1.3 Example

```json
{
  "goalId": "gbfdo-goal-001",
  "alignedCbkIds": [
    "cbkbfdo-001"
  ],
  "alignmentStatus": true,
  "constructedRealizations": [
    {
      "realizationId": "cr-0001"
    }
  ],
  "engineNotes": "Potential alignment identified."
}
```

---

### 8.1.4 Notes

This example illustrates:

* one Goal;
* one aligned CBK Artifact;
* positive alignment status;
* one Constructed Realization reference.

A positive alignment determination indicates that the Alignment Engine identified one or more Constructed Realizations associated with the Goal.

The aligned CBK-bearing FAIR Digital Objects participate in those Constructed Realizations.

The example does not imply knowledge application.

The example reports an Alignment Engine determination.

---

## 8.2 Negative Alignment Example

### 8.2.1 Purpose

This section illustrates a negative Alignment Result Graph.

The example demonstrates a case in which an Alignment Engine reports that no alignment relationship was identified.

---

### 8.2.2 Traceability

Derived From:

Release Candidate

* Section 5.3 — Alignment Results

Implementation Specification

* Section 7.9 — Alignment Result Graph Model

---

### 8.2.3 Example

```json
{
  "goalId": "gbfdo-goal-002",
  "alignedCbkIds": [],
  "alignmentStatus": false,
  "constructedRealizations": [],
  "engineNotes": "No alignment identified."
}
```

---

### 8.2.4 Notes

This example illustrates:

* one Goal;
* no aligned CBK Artifacts;
* negative alignment status;
* no Constructed Realizations.

The example does not imply that suitable knowledge does not exist.

The example reports only the determination of the Alignment Engine used during the run.

---

## 8.3 Multiple Goal Example

### 8.3.1 Purpose

This section illustrates an Alignment Result Graph containing results for multiple Goals.

The example demonstrates how multiple Goals may be represented within a single Alignment Run.

---

### 8.3.2 Traceability

Derived From:

Release Candidate

* Section 5.3 — Alignment Results

Implementation Specification

* Section 7.9 — Alignment Result Graph Model

---

### 8.3.3 Example

```json
{
  "results": [
    {
      "goalId": "gbfdo-goal-001",
      "alignmentStatus": true,
      "alignedCbkIds": [
        "cbkbfdo-001"
      ],
      "constructedRealizations": [
        {
          "realizationId": "cr-0001"
        }
      ]
    },
    {
      "goalId": "gbfdo-goal-002",
      "alignmentStatus": false,
      "alignedCbkIds": [],
      "constructedRealizations": []
    }
  ]
}
```

---

### 8.3.4 Notes

This example demonstrates that alignment results are reported independently for each Goal.

Alignment for one Goal does not imply alignment for another Goal.

Constructed Realizations are likewise reported independently for each Goal.

---

## 8.4 Multiple CBK Example

### 8.4.1 Purpose

This section illustrates a result in which multiple CBK-bearing FAIR Digital Objects are reported as aligned with a single Goal.

The example demonstrates that an Alignment Engine may identify multiple candidate alignments.

---

### 8.4.2 Traceability

Derived From:

Release Candidate

* Section 5.3 — Alignment Results
* Section 5.5 — Constructed Realizations

Implementation Specification

* Section 7.9 — Alignment Result Graph Model

---

### 8.4.3 Example

```json
{
  "goalId": "gbfdo-goal-001",
  "alignedCbkIds": [
    "cbkbfdo-001",
    "cbkbfdo-003",
    "cbkbfdo-005"
  ],
  "alignmentStatus": true,
  "constructedRealizations": [
    {
      "realizationId": "cr-0001"
    },
    {
      "realizationId": "cr-0002"
    }
  ]
}
```

---

### 8.4.4 Notes

This example illustrates:

* one Goal;
* multiple aligned CBK Artifacts;
* multiple Constructed Realizations.

Multiple aligned CBK-bearing FAIR Digital Objects may participate in a single Constructed Realization or in multiple Constructed Realizations.

The Alignment Result Graph reports the outcome of the Alignment Engine determination rather than the internal alignment procedure.

The example does not prescribe ranking, ordering, scoring, or preference.

Those determinations remain under Alignment Engine control.

---

## 8.5 Constructed Realization Relationship Example

### 8.5.1 Purpose

This section clarifies the relationship between Alignment Results and Constructed Realizations.

The examples in this section are intended to support interpretation of positive alignment determinations.

A positive alignment determination indicates that the Alignment Engine identified one or more Constructed Realizations associated with the Goal.

Constructed Realizations provide the realization structures through which one or more CBK-bearing FAIR Digital Objects may be engaged to realize a computational goal.

---

### 8.5.2 Traceability

Derived From:

Release Candidate

* Section 3.2.18 — Constructed Realization
* Section 5.3 — Alignment Results
* Section 5.5 — Constructed Realizations

Implementation Specification

* Section 7.9 — Alignment Result Graph Model
* Section 7.10 — Constructed Realization Model

---

### 8.5.3 Conceptual Relationship

Conceptually:

```text
Goal

↓

Alignment Engine

↓

Constructed Realization

↓

CBKB-FDO Sequence
```

A positive alignment determination indicates that one or more Constructed Realizations were identified.

---

### 8.5.4 Single-Step Constructed Realization

Example:

```text
Goal:
Estimate 30-Day Readmission Risk

↓

CBKB-FDO-001

↓

Readmission Risk Score
```

Illustrative Alignment Result:

```json
{
  "goalId": "gbfdo-goal-001",
  "alignmentStatus": true,
  "constructedRealizations": [
    {
      "realizationId": "cr-0001"
    }
  ]
}
```

#### Notes

This example illustrates a Constructed Realization consisting of a single CBK-bearing FAIR Digital Object.

---

### 8.5.5 Multi-Step Constructed Realization

Example:

```text
Goal:
Estimate Personalized Treatment Risk

↓

CBKB-FDO-001
(Patient Feature Extraction)

↓

Intermediate Computational Output

↓

CBKB-FDO-002
(Risk Estimation)

↓

Treatment Risk Score
```

Illustrative Alignment Result:

```json
{
  "goalId": "gbfdo-goal-002",
  "alignmentStatus": true,
  "constructedRealizations": [
    {
      "realizationId": "cr-0002"
    }
  ]
}
```

#### Notes

This example illustrates a Constructed Realization consisting of multiple CBK-bearing FAIR Digital Objects arranged in a fixed computational sequence.

---

### 8.5.6 GARI v1.0 Representation Scope

The examples in GARI v1.0 represent Constructed Realizations as fixed computational sequences.

Conceptually:

```text
CBKB-FDO-A

↓

CBKB-FDO-B

↓

CBKB-FDO-C
```

The examples do not include:

* branching logic;
* conditional execution;
* workflow orchestration;
* runtime decision structures.

Such constructs are outside the scope of the examples presented in this document.

---

### 8.5.7 Key Interpretation

A positive alignment determination may be interpreted as answering the question:

```text
Is there a sequence of one or more
CBK-bearing FAIR Digital Objects
that can be engaged to realize
the computational goal?
```

Constructed Realizations represent the identified sequences.

The examples do not prescribe how Alignment Engines identify those sequences.

---

## 8.6 Alignment Result Interpretation Example

### 8.6.1 Purpose

This section clarifies interpretation of Alignment Result Graphs.

The distinction between alignment and knowledge application is one of the most important conceptual boundaries within GARI.

This example is intended to support correct interpretation of Alignment Run outputs.

---

### 8.6.2 Traceability

Derived From:

Release Candidate

* Section 5.3 — Alignment Results
* Alignment-Only Scope Principle

Implementation Specification

* Section 7.9 — Alignment Result Graph Model

---

### 8.6.3 Example Alignment Result

```json
{
  "goalId": "gbfdo-goal-001",
  "alignedCbkIds": [
    "cbkbfdo-001"
  ],
  "alignmentStatus": true
}
```

---

### 8.6.4 Correct Interpretation

The result above may be interpreted as:

```text
The Alignment Engine determined
that one or more Constructed
Realizations exist that may be
engaged to realize the Goal.
```

---

### 8.6.5 Incorrect Interpretation

The result above SHALL NOT be interpreted as:

```text
The Goal has been achieved.
```

or:

```text
The CBK has been applied.
```

or:

```text
The Alignment Engine executed
the CBK Artifact.
```

or:

```text
A real-world outcome occurred.
```

---

### 8.6.6 Conceptual Boundary

Conceptually:

```text
Goal

↓

Constructed Realization Identified

↓

Alignment Result Graph
```

GARI stops here.

GARI does not perform:

```text
Knowledge Application

↓

Execution

↓

Real-World Outcome
```

Those activities occur outside the scope of GARI.

---

### 8.6.7 Notes

This distinction is essential for correct interpretation of Alignment Result Graphs.

The Alignment Result Graph reports the determination of an Alignment Engine.

It does not report execution, application, intervention, prediction, or outcome realization.

---

## 8.7 Alignment Result Provenance Example

### 8.7.1 Purpose

This section illustrates the relationship between Alignment Results and Alignment Engine provenance.

The example supports interpretation and reproducibility.

---

### 8.7.2 Traceability

Derived From:

Release Candidate

* Section 5.3 — Alignment Results
* Section 5.4 — Provenance

Implementation Specification

* Section 7.8 — Output Package Model
* Section 7.9 — Alignment Result Graph Model

---

### 8.7.3 Example

```json
{
  "goalId": "gbfdo-goal-001",
  "alignmentStatus": true,
  "alignedCbkIds": [
    "cbkbfdo-001"
  ],
  "provenance": {
    "runId": "run-2026-0001",
    "engineName": "DFSK Alignment Engine",
    "engineVersion": "1.0.0"
  }
}
```

---

### 8.7.4 Notes

This example demonstrates that alignment results may be interpreted in the context of:

* a specific Alignment Run;
* a specific Alignment Engine;
* a specific engine version.

This supports inspection and reproducibility.

---

## 8.8 Chapter Summary

This chapter provided canonical examples of Alignment Result Graphs recognized by GARI v1.0.

The chapter illustrated:

* positive alignment results;
* negative alignment results;
* multiple Goal results;
* multiple CBK results;
* Constructed Realization relationships;
* result interpretation;
* result provenance.

Most importantly, the chapter established the distinction between:

```text
Alignment Determination
```

and:

```text
Knowledge Application
```

The chapter further established that positive alignment determinations are associated with one or more Constructed Realizations.

For purposes of the examples in GARI v1.0, Constructed Realizations are represented as fixed computational sequences consisting of one or more CBK-bearing FAIR Digital Objects.

A positive alignment determination may therefore be understood as indicating that the Alignment Engine identified one or more sequences through which the computational goal could potentially be realized.

Alignment Result Graphs report the determinations of Alignment Engines.

They do not report execution, intervention, prediction, treatment, or real-world outcomes.

This distinction preserves the Alignment-Only Scope of GARI and ensures correct interpretation of Alignment Run outputs.

Subsequent chapters build upon these examples through detailed Constructed Realization examples.


# Chapter 9 — Constructed Realization Examples

## 9.1 Single-Step Constructed Realization

### 9.1.1 Purpose

This section provides a canonical example of a single-step Constructed Realization.

The example illustrates the simplest realization structure recognized by GARI v1.0.

A single-step Constructed Realization consists of one CBK-bearing FAIR Digital Object that may be engaged to realize a computational goal.

---

### 9.1.2 Traceability

Derived From:

Release Candidate

* Section 3.2.18 — Constructed Realization
* Section 5.5 — Constructed Realizations

Implementation Specification

* Section 7.10 — Constructed Realization Model

---

### 9.1.3 Conceptual Example

```text id="hy4n97"
Goal:
Estimate 30-Day Readmission Risk

↓

CBKB-FDO-001

↓

Readmission Risk Score
```

---

### 9.1.4 Example Representation

```json id="dtv2lr"
{
  "realizationId": "cr-0001",
  "goalId": "gbfdo-goal-001",
  "sequence": [
    {
      "step": 1,
      "cbkbFdoId": "cbkbfdo-001"
    }
  ]
}
```

---

### 9.1.5 Notes

This example illustrates:

* one Goal;
* one CBK-bearing FAIR Digital Object;
* one realization step.

The example represents a fixed computational sequence.

The example does not imply execution.

The example identifies a realization structure.

---

## 9.2 Multi-Step Constructed Realization

### 9.2.1 Purpose

This section illustrates a Constructed Realization containing multiple CBK-bearing FAIR Digital Objects.

The example demonstrates how realization structures may consist of more than one computational step.

---

### 9.2.2 Traceability

Derived From:

Release Candidate

* Section 5.5 — Constructed Realizations

Implementation Specification

* Section 7.10 — Constructed Realization Model

---

### 9.2.3 Conceptual Example

```text id="4i4ezp"
Goal:
Estimate Personalized Treatment Risk

↓

CBKB-FDO-001
(Patient Feature Extraction)

↓

Intermediate Computational Output

↓

CBKB-FDO-002
(Risk Estimation)

↓

Treatment Risk Score
```

---

### 9.2.4 Example Representation

```json id="x19cw4"
{
  "realizationId": "cr-0002",
  "goalId": "gbfdo-goal-002",
  "sequence": [
    {
      "step": 1,
      "cbkbFdoId": "cbkbfdo-001"
    },
    {
      "step": 2,
      "cbkbFdoId": "cbkbfdo-002"
    }
  ]
}
```

---

### 9.2.5 Notes

This example illustrates:

* one Goal;
* multiple CBK-bearing FAIR Digital Objects;
* a fixed computational sequence.

The example does not prescribe how intermediate computational outputs are represented internally by an Alignment Engine.

The example illustrates realization structure only.

---

## 9.3 Multiple Constructed Realizations for a Single Goal

### 9.3.1 Purpose

This section illustrates a situation in which an Alignment Engine identifies more than one Constructed Realization associated with a Goal.

The example demonstrates that multiple realization structures may exist for the same Goal.

---

### 9.3.2 Traceability

Derived From:

Release Candidate

* Section 5.5 — Constructed Realizations

Implementation Specification

* Section 7.10 — Constructed Realization Model

---

### 9.3.3 Conceptual Example

Constructed Realization A:

```text id="1r7ttq"
Goal

↓

CBKB-FDO-001

↓

Desired Output
```

Constructed Realization B:

```text id="2x7sgu"
Goal

↓

CBKB-FDO-003

↓

Desired Output
```

---

### 9.3.4 Example Representation

```json id="3x9bbm"
{
  "goalId": "gbfdo-goal-001",
  "constructedRealizations": [
    {
      "realizationId": "cr-0001",
      "sequence": [
        {
          "step": 1,
          "cbkbFdoId": "cbkbfdo-001"
        }
      ]
    },
    {
      "realizationId": "cr-0003",
      "sequence": [
        {
          "step": 1,
          "cbkbFdoId": "cbkbfdo-003"
        }
      ]
    }
  ]
}
```

---

### 9.3.5 Notes

This example illustrates:

* one Goal;
* multiple realization structures;
* multiple candidate computational sequences.

The example does not imply preference, ranking, or superiority among realizations.

Those determinations remain under Alignment Engine control.

---

## 9.4 Constructed Realization as a Computational Sequence

### 9.4.1 Purpose

This section clarifies the interpretation of Constructed Realizations used throughout the examples in this document.

The examples presented in GARI v1.0 represent Constructed Realizations as fixed computational sequences.

---

### 9.4.2 Conceptual Representation

```text id="brrx2w"
CBKB-FDO-A

↓

CBKB-FDO-B

↓

CBKB-FDO-C
```

Each step represents a CBK-bearing FAIR Digital Object participating in the realization structure.

---

### 9.4.3 Example Representation

```json id="mvw6cq"
{
  "realizationId": "cr-0004",
  "sequence": [
    {
      "step": 1,
      "cbkbFdoId": "cbkbfdo-A"
    },
    {
      "step": 2,
      "cbkbFdoId": "cbkbfdo-B"
    },
    {
      "step": 3,
      "cbkbFdoId": "cbkbfdo-C"
    }
  ]
}
```

---

### 9.4.4 Notes

For purposes of the examples in GARI v1.0, Constructed Realizations are represented as fixed computational sequences.

The examples do not include:

* branching logic;
* conditional execution;
* workflow orchestration;
* runtime decision structures.

The examples are intentionally limited to sequential realization structures.

---

## 9.5 Constructed Realization Interpretation Example

### 9.5.1 Purpose

This section clarifies how Constructed Realizations should be interpreted.

The examples are intended to reinforce the distinction between realization identification and realization execution.

---

### 9.5.2 Example

```json id="0h4vx5"
{
  "realizationId": "cr-0002",
  "goalId": "gbfdo-goal-002",
  "sequence": [
    {
      "step": 1,
      "cbkbFdoId": "cbkbfdo-001"
    },
    {
      "step": 2,
      "cbkbFdoId": "cbkbfdo-002"
    }
  ]
}
```

---

### 9.5.3 Correct Interpretation

The example above may be interpreted as:

```text id="lk0v4w"
A computational sequence was
identified through which the Goal
could potentially be realized.
```

---

### 9.5.4 Incorrect Interpretation

The example above SHALL NOT be interpreted as:

```text id="tcl9r8"
The sequence was executed.
```

or:

```text id="fxjnzv"
The Goal was achieved.
```

or:

```text id="fbgv3g"
A real-world outcome occurred.
```

---

### 9.5.5 Notes

Constructed Realizations are alignment outputs.

They are not execution records.

They are not workflow execution traces.

They are not outcome reports.

---

## 9.6 Constructed Realization and Alignment Relationship

### 9.6.1 Purpose

This section summarizes the relationship between Alignment Results and Constructed Realizations.

---

### 9.6.2 Conceptual Relationship

Conceptually:

```text id="ys20of"
Goal

↓

Alignment Engine

↓

Constructed Realizations Identified

↓

Alignment Result Graph
```

A positive alignment determination indicates that one or more Constructed Realizations were identified.

---

### 9.6.3 Key Question

A positive alignment determination may be interpreted as answering:

```text id="43q1gf"
Is there a sequence of one or more
CBK-bearing FAIR Digital Objects
that can be engaged to realize
the computational goal?
```

Constructed Realizations represent the identified sequences.

---

## 9.7 Chapter Summary

This chapter provided canonical examples of Constructed Realizations recognized by GARI v1.0.

The chapter illustrated:

* single-step Constructed Realizations;
* multi-step Constructed Realizations;
* multiple Constructed Realizations for a single Goal;
* realization sequences;
* realization interpretation;
* relationships between alignment and realization structures.

Most importantly, the chapter established that Constructed Realizations are represented in GARI v1.0 examples as fixed computational sequences consisting of one or more CBK-bearing FAIR Digital Objects.

The examples further reinforce that Constructed Realizations are identified by Alignment Engines but are not executed by GARI.

Constructed Realizations therefore represent potential realization structures through which computational goals could be realized rather than records of execution or outcome achievement.


# Chapter 10 — Provenance Examples

## 10.1 Minimal Provenance Object

### 10.1.1 Purpose

This section provides a canonical example of a minimal provenance object.

The Release Candidate requires provenance sufficient to support interpretation, inspection, and reproducibility of Alignment Runs.

The examples in this chapter are illustrative only.

---

### 10.1.2 Traceability

Derived From:

Release Candidate

* Section 5.4.6 — Provenance
* Section 6.4.6 — Provenance
* Principle: Scientific Instrument

Implementation Specification

* Section 7.12 — Provenance Model

---

### 10.1.3 Minimal Example

```json
{
  "runId": "run-2026-0001",
  "timestamp": "2026-06-19T12:00:00Z",
  "engineVersion": "1.0.0"
}
```

---

### 10.1.4 Notes

This example illustrates the minimum provenance information required to associate an artifact with:

* a specific Alignment Run;
* a specific execution time;
* a specific Alignment Engine version.

The example is intentionally minimal.

---

## 10.2 Alignment Run Provenance Example

### 10.2.1 Purpose

This section illustrates provenance associated with an Alignment Run.

The example demonstrates how run context may be represented for interpretation and reproducibility purposes.

---

### 10.2.2 Traceability

Derived From:

Release Candidate

* Section 3.2.16 — Alignment Run
* Section 5.4.6 — Provenance

Implementation Specification

* Section 7.12 — Provenance Model

---

### 10.2.3 Example

```json
{
  "runId": "run-2026-0001",
  "timestamp": "2026-06-19T12:00:00Z",
  "userAgent": "user",
  "engineName": "DFSK Alignment Engine",
  "engineVersion": "1.0.0",
  "layerImageId": "layer-image-0003"
}
```

---

### 10.2.4 Notes

This example illustrates provenance linking:

* a run;
* an engine;
* a Layer Image;
* a timestamp.

The example does not prescribe any particular provenance technology.

---

## 10.3 Alignment Result Provenance Example

### 10.3.1 Purpose

This section illustrates provenance associated with Alignment Results.

The example demonstrates how Alignment Results may be associated with the Alignment Run that produced them.

---

### 10.3.2 Traceability

Derived From:

Release Candidate

* Section 5.3 — Alignment Results
* Section 5.4.6 — Provenance

Implementation Specification

* Section 7.9 — Alignment Result Graph Model
* Section 7.12 — Provenance Model

---

### 10.3.3 Example

```json
{
  "goalId": "gbfdo-goal-001",
  "alignmentStatus": true,
  "alignedCbkIds": [
    "cbkbfdo-001"
  ],
  "provenance": {
    "runId": "run-2026-0001",
    "timestamp": "2026-06-19T12:00:00Z",
    "engineName": "DFSK Alignment Engine",
    "engineVersion": "1.0.0"
  }
}
```

---

### 10.3.4 Notes

This example illustrates how an Alignment Result may be traced to:

* a specific Alignment Run;
* a specific Alignment Engine;
* a specific engine version.

This supports inspection and reproducibility.

---

## 10.4 Constructed Realization Provenance Example

### 10.4.1 Purpose

This section illustrates provenance associated with Constructed Realizations.

Because Constructed Realizations are identified by Alignment Engines, provenance is important for interpretation and reproducibility.

---

### 10.4.2 Traceability

Derived From:

Release Candidate

* Section 5.5 — Constructed Realizations
* Section 5.4.6 — Provenance

Implementation Specification

* Section 7.10 — Constructed Realization Model
* Section 7.12 — Provenance Model

---

### 10.4.3 Example

```json
{
  "realizationId": "cr-0002",
  "goalId": "gbfdo-goal-002",
  "sequence": [
    {
      "step": 1,
      "cbkbFdoId": "cbkbfdo-001"
    },
    {
      "step": 2,
      "cbkbFdoId": "cbkbfdo-002"
    }
  ],
  "provenance": {
    "runId": "run-2026-0001",
    "engineName": "DFSK Alignment Engine",
    "engineVersion": "1.0.0",
    "timestamp": "2026-06-19T12:00:00Z"
  }
}
```

---

### 10.4.4 Notes

This example illustrates provenance associated with an identified Constructed Realization.

The provenance identifies:

* the run during which the realization was identified;
* the Alignment Engine that identified the realization;
* the engine version used.

The example does not imply execution of the realization.

---

## 10.5 Provenance Continuity Example

### 10.5.1 Purpose

This section illustrates provenance continuity across major GARI runtime artifacts.

The example demonstrates how provenance supports traceability from Alignment Run initiation through result generation and preservation.

---

### 10.5.2 Traceability

Derived From:

Release Candidate

* Section 5.4.6 — Provenance
* Section 6.4.6 — Provenance

Implementation Specification

* Section 7.12 — Provenance Model

---

### 10.5.3 Conceptual Example

```text
Alignment Run

↓

Input Package

↓

Alignment Result Graph

↓

Constructed Realization

↓

Output Package

↓

Saved Run Package
```

---

### 10.5.4 Provenance Continuity Example

```json
{
  "runId": "run-2026-0001",
  "engineVersion": "1.0.0",
  "timestamp": "2026-06-19T12:00:00Z",
  "referencedArtifacts": [
    "input-package-0001",
    "alignment-result-0001",
    "cr-0002",
    "output-package-0001",
    "saved-run-0001"
  ]
}
```

---

### 10.5.5 Notes

This example illustrates continuity of provenance across multiple runtime artifacts.

The example is intended to support:

* inspection;
* traceability;
* reproducibility;
* interpretation.

The example does not prescribe a provenance implementation technology.

---

## 10.6 Chapter Summary

This chapter provided canonical provenance examples recognized by GARI v1.0.

The chapter illustrated:

* minimal provenance objects;
* Alignment Run provenance;
* Alignment Result provenance;
* Constructed Realization provenance;
* provenance continuity across runtime artifacts.

Most importantly, the chapter demonstrated how provenance supports interpretation and reproducibility without exposing Alignment Engine internals.

The examples further illustrate that provenance may be associated with:

* runs;
* results;
* Constructed Realizations;
* Output Packages;
* Saved Run Packages.

Provenance therefore functions as the traceability mechanism connecting GARI runtime artifacts to the Alignment Runs that produced them.

# Chapter 11 — Output Package Examples

## 11.1 Minimal Output Package

### 11.1.1 Purpose

This section provides a canonical example of a minimal Output Package.

The Release Candidate defines the Output Package as the primary output artifact produced by an Alignment Engine during an Alignment Run.

Output Packages communicate the results of Alignment Engine execution and preserve the runtime artifacts necessary for interpretation.

---

### 11.1.2 Traceability

Derived From:

Release Candidate

* Section 3.2.17 — Output Package
* Section 4.5 — Output Package

Implementation Specification

* Section 7.8 — Output Package Model

---

### 11.1.3 Minimal Example

```json
{
  "runId": "run-2026-0001",
  "alignmentResults": [],
  "provenance": {
    "runId": "run-2026-0001",
    "timestamp": "2026-06-19T12:00:00Z"
  }
}
```

---

### 11.1.4 Notes

This example illustrates the minimum structure of an Output Package.

The example is intentionally minimal and omits many runtime artifacts commonly present in richer Output Packages.

Output Packages originate from Alignment Engines.

---

## 11.2 Rich Output Package

### 11.2.1 Purpose

This section illustrates a richer Alignment Engine-produced Output Package suitable for implementation, inspection, and reproducibility activities.

The example demonstrates the major runtime artifacts commonly associated with an Alignment Run.

---

### 11.2.2 Traceability

Derived From:

Release Candidate

* Section 4.5 — Output Package
* Section 4.5.6.1 — Alignment Result Graph
* Section 4.5.6.2 — Layer Image
* Section 4.5.6.3 — Provenance Metadata
* Section 4.5.6.4 — Engine Configuration Metadata

Implementation Specification

* Section 7.8 — Output Package Model

---

### 11.2.3 Example

```json
{
  "runId": "run-2026-0001",
  "layerImageId": "layer-image-0003",
  "alignmentResults": [
    {
      "goalId": "gbfdo-goal-001",
      "alignmentStatus": true
    }
  ],
  "constructedRealizations": [
    {
      "realizationId": "cr-0001"
    }
  ],
  "engineMetadata": {
    "engineName": "DFSK Alignment Engine",
    "engineVersion": "1.0.0"
  },
  "provenance": {
    "timestamp": "2026-06-19T12:00:00Z"
  }
}
```

---

### 11.2.4 Notes

This example illustrates:

* Layer Image preservation;
* Alignment Result Graph content;
* Constructed Realization references;
* Engine metadata;
* provenance.

The example is intended to demonstrate artifact relationships rather than implementation mechanics.

The Output Package is produced by the Alignment Engine.

---

## 11.3 Positive Alignment Output Package Example

### 11.3.1 Purpose

This section illustrates an Output Package produced from a positive alignment determination.

The example demonstrates the relationship between Alignment Results and Constructed Realizations.

The Output Package shown below is produced by the Alignment Engine that executed the Alignment Run.

---

### 11.3.2 Traceability

Derived From:

Release Candidate

* Section 5.3 — Alignment Result Graph
* Section 4.5 — Output Package
* Section 3.2.19 — Constructed Realization

Implementation Specification

* Section 7.8 — Output Package Model
* Section 7.9 — Alignment Result Graph Model
* Section 7.10 — Constructed Realization Model

---

### 11.3.3 Example

```json
{
  "runId": "run-2026-0001",
  "alignmentResults": [
    {
      "goalId": "gbfdo-goal-001",
      "alignmentStatus": true,
      "alignedCbkIds": [
        "cbkbfdo-001"
      ],
      "constructedRealizations": [
        {
          "realizationId": "cr-0001"
        }
      ]
    }
  ],
  "constructedRealizations": [
    {
      "realizationId": "cr-0001",
      "sequence": [
        {
          "step": 1,
          "cbkbFdoId": "cbkbfdo-001"
        }
      ]
    }
  ]
}
```

---

### 11.3.4 Notes

This example illustrates:

* a positive alignment determination;
* one Constructed Realization;
* a realization sequence associated with the Goal.

The Output Package records the determination of the Alignment Engine.

The Output Package does not imply execution of the realization.

---

## 11.4 Negative Alignment Output Package Example

### 11.4.1 Purpose

This section illustrates an Output Package produced from a negative alignment determination.

The example demonstrates how no-alignment outcomes are represented.

Negative-result Output Packages are produced by Alignment Engines and constitute valid scientific outputs of GARI.

---

### 11.4.2 Traceability

Derived From:

Release Candidate

* Section 5.3 — Alignment Result Graph
* Section 4.5 — Output Package

Implementation Specification

* Section 7.8 — Output Package Model
* Section 7.9 — Alignment Result Graph Model

---

### 11.4.3 Example

```json
{
  "runId": "run-2026-0002",
  "alignmentResults": [
    {
      "goalId": "gbfdo-goal-002",
      "alignmentStatus": false,
      "alignedCbkIds": [],
      "constructedRealizations": []
    }
  ],
  "constructedRealizations": []
}
```

---

### 11.4.4 Notes

This example illustrates:

* a negative alignment determination;
* no aligned CBK-bearing FAIR Digital Objects;
* no Constructed Realizations.

The example does not imply that suitable knowledge does not exist.

The example reports only the determination of the Alignment Engine used during the run.

---

## 11.5 Output Package Artifact Relationship Example

### 11.5.1 Purpose

This section illustrates the relationships among the major artifacts preserved within an Output Package.

The example is intended to support implementation and inspection activities.

---

### 11.5.2 Traceability

Derived From:

Release Candidate

* Section 4.5 — Output Package

Implementation Specification

* Section 7.8 — Output Package Model

---

### 11.5.3 Output Package Production Model

#### Purpose

This section clarifies the origin of Output Packages and the respective responsibilities of Alignment Engines and GARI.

Output Package ownership is an important architectural boundary within GARI v1.0.

---

#### Conceptual Relationship

```text
Established Layer

↓

Layer Image

↓

Input Package

↓

Alignment Engine

↓

Alignment Result Graph
Constructed Realizations
Engine Notes
Engine Metadata
Provenance

↓

Output Package

↓

GARI

(receives)

(validates)

(displays)

(preserves)
```

---

#### Architectural Responsibility Boundary

For purposes of GARI v1.0:

```text
Alignment Engines
produce Output Packages.
```

GARI:

```text
receives Output Packages;
validates Output Package structure;
displays Output Package contents;
preserves Output Packages;
packages Output Packages into Saved Run Packages.
```

GARI does not generate:

* Alignment Result Graphs;
* Constructed Realizations;
* Engine Notes;
* Alignment Engine result content.

Those artifacts originate from the Alignment Engine.

---

#### Notes

This distinction preserves:

* the Black-Box Engine Principle;
* Alignment Engine Independence;
* Output Package ownership by Alignment Engines.

GARI functions as the orchestration, inspection, and preservation environment surrounding Alignment Engine execution.

---

### 11.5.4 Conceptual Relationship

Conceptually:

```text
Layer Image

+

Alignment Result Graph

+

Constructed Realizations

+

Provenance

+

Engine Metadata

↓

Output Package
```

---

### 11.5.5 Expanded Example

```json
{
  "runId": "run-2026-0001",
  "layerImage": {
    "layerImageId": "layer-image-0003"
  },
  "alignmentResults": [
    {
      "goalId": "gbfdo-goal-001",
      "alignmentStatus": true
    }
  ],
  "constructedRealizations": [
    {
      "realizationId": "cr-0001"
    }
  ],
  "engineMetadata": {
    "engineName": "DFSK Alignment Engine",
    "engineVersion": "1.0.0"
  },
  "provenance": {
    "runId": "run-2026-0001",
    "timestamp": "2026-06-19T12:00:00Z"
  }
}
```

---

### 11.5.6 Notes

This example illustrates how multiple runtime artifacts are preserved together within an Alignment Engine-produced Output Package.

The Output Package functions as the principal runtime output artifact of an Alignment Run.

The Output Package provides the context necessary for interpretation of Alignment Results and Constructed Realizations.

---

## 11.6 Chapter Summary

This chapter provided canonical Output Package examples recognized by GARI v1.0.

The chapter illustrated:

* minimal Output Packages;
* rich Output Packages;
* positive alignment Output Packages;
* negative alignment Output Packages;
* Output Package artifact relationships.

Most importantly, the chapter demonstrated how Output Packages aggregate the principal runtime artifacts produced by an Alignment Engine during an Alignment Run.

Conceptually:

```text
Layer Image

+

Alignment Result Graph

+

Constructed Realizations

+

Engine Metadata

+

Provenance

↓

Output Package
```

Output Packages originate from Alignment Engines.

GARI receives, validates, displays, preserves, and packages Output Packages but does not generate Alignment Result Graphs, Constructed Realizations, Engine Notes, or other Alignment Engine result content.

This responsibility boundary preserves the Black-Box Engine Principle and maintains Alignment Engine ownership of alignment outputs.

The Output Package therefore functions as the primary runtime artifact through which Alignment Results and Constructed Realizations are communicated, interpreted, and preserved.

The Output Package does not execute Constructed Realizations.

The Output Package records the determinations of the Alignment Engine and the realization structures identified during the Alignment Run.

# Chapter 12 — Saved Run Package Examples

## 12.1 Minimal Saved Run Package

### 12.1.1 Purpose

This section provides a canonical example of a minimal Saved Run Package.

The Release Candidate defines the Saved Run Package as the preservation artifact produced by GARI from the results of a completed Alignment Run.

Saved Run Packages support:

* preservation;
* inspection;
* sharing;
* reproducibility;
* re-execution.

---

### 12.1.2 Traceability

Derived From:

Release Candidate

* Section 3.2.20 — Saved Run Package
* Section 6 — Saved Run Package

Implementation Specification

* Section 7.11 — Saved Run Package Model

---

### 12.1.3 Minimal Example

```json
{
  "savedRunId": "saved-run-0001",
  "runId": "run-2026-0001",
  "outputPackageId": "output-package-0001"
}
```

---

### 12.1.4 Notes

This example illustrates the minimum information necessary to associate a Saved Run Package with:

* a completed Alignment Run;
* an Output Package;
* a preserved run artifact.

Saved Run Packages are produced by GARI.

---

## 12.2 Rich Saved Run Package

### 12.2.1 Purpose

This section illustrates a richer Saved Run Package suitable for preservation, inspection, and reproducibility activities.

The example demonstrates the major artifacts commonly preserved by GARI.

---

### 12.2.2 Traceability

Derived From:

Release Candidate

* Section 6 — Saved Run Package
* Section 6.4.7 — Layer Image
* Section 6.4.8 — Reproducibility Information

Implementation Specification

* Section 7.11 — Saved Run Package Model

---

### 12.2.3 Example

```json
{
  "savedRunId": "saved-run-0001",
  "runId": "run-2026-0001",
  "outputPackage": {
    "outputPackageId": "output-package-0001"
  },
  "layerImage": {
    "layerImageId": "layer-image-0003"
  },
  "reproducibilityInformation": {
    "engineName": "DFSK Alignment Engine",
    "engineVersion": "1.0.0"
  },
  "savedAt": "2026-06-19T12:15:00Z"
}
```

---

### 12.2.4 Notes

This example illustrates preservation of:

* Output Package information;
* Layer Image information;
* reproducibility information;
* save metadata.

The Saved Run Package is generated by GARI after receiving an Output Package from an Alignment Engine.

---

## 12.3 Output Package to Saved Run Package Transformation Example

### 12.3.1 Purpose

This section illustrates the relationship between Alignment Engine-produced Output Packages and GARI-produced Saved Run Packages.

This distinction is an important architectural boundary within GARI v1.0.

---

### 12.3.2 Traceability

Derived From:

Release Candidate

* Section 5 — Output Package
* Section 6 — Saved Run Package

Implementation Specification

* Section 7.8 — Output Package Model
* Section 7.11 — Saved Run Package Model

---

### 12.3.3 Conceptual Relationship

```text
Alignment Engine

↓

Output Package

↓

GARI

↓

Saved Run Package
```

---

### 12.3.4 Responsibility Boundary

```text
Alignment Engine
    produces Output Package

GARI
    receives Output Package
    validates Output Package
    preserves Output Package
    packages Saved Run Package
```

GARI does not generate Alignment Results or Constructed Realizations during Save Run operations.

Those artifacts originate from the Alignment Engine and are preserved by GARI.

---

### 12.3.5 Notes

The Saved Run Package is a preservation artifact.

The Saved Run Package is not an Alignment Engine output.

---

## 12.4 Positive Alignment Saved Run Package Example

### 12.4.1 Purpose

This section illustrates a Saved Run Package derived from a positive alignment result.

---

### 12.4.2 Example

```json
{
  "savedRunId": "saved-run-0001",
  "runId": "run-2026-0001",
  "outputPackage": {
    "alignmentResults": [
      {
        "goalId": "gbfdo-goal-001",
        "alignmentStatus": true
      }
    ]
  },
  "constructedRealizations": [
    {
      "realizationId": "cr-0001"
    }
  ]
}
```

---

### 12.4.3 Notes

This example illustrates preservation of:

* positive alignment results;
* Constructed Realizations;
* Alignment Engine outputs.

The Saved Run Package preserves these artifacts but does not create them.

---

## 12.5 Negative Alignment Saved Run Package Example

### 12.5.1 Purpose

This section illustrates a Saved Run Package derived from a negative alignment result.

---

### 12.5.2 Example

```json
{
  "savedRunId": "saved-run-0002",
  "runId": "run-2026-0002",
  "outputPackage": {
    "alignmentResults": [
      {
        "goalId": "gbfdo-goal-002",
        "alignmentStatus": false
      }
    ]
  },
  "constructedRealizations": []
}
```

---

### 12.5.3 Notes

Negative-result Saved Run Packages are valid preservation artifacts.

A Saved Run Package may preserve a completed run regardless of alignment outcome.

---

## 12.6 Reproducibility Information Example

### 12.6.1 Purpose

This section illustrates reproducibility information preserved within a Saved Run Package.

The purpose of reproducibility information is to support future inspection and re-execution of Alignment Runs.

---

### 12.6.2 Example

```json
{
  "runId": "run-2026-0001",
  "engineName": "DFSK Alignment Engine",
  "engineVersion": "1.0.0",
  "layerImageId": "layer-image-0003",
  "savedAt": "2026-06-19T12:15:00Z"
}
```

---

### 12.6.3 Notes

This example illustrates metadata useful for:

* reproducibility;
* re-execution;
* inspection;
* provenance interpretation.

---

## 12.7 Saved Run Package Artifact Relationship Example

### 12.7.1 Purpose

This section illustrates the major artifacts preserved within a Saved Run Package.

---

### 12.7.2 Conceptual Relationship

```text
Output Package

+

Layer Image

+

Provenance

+

Reproducibility Information

↓

Saved Run Package
```

---

### 12.7.3 Expanded Example

```json
{
  "savedRunId": "saved-run-0001",
  "runId": "run-2026-0001",
  "outputPackage": {
    "outputPackageId": "output-package-0001"
  },
  "layerImage": {
    "layerImageId": "layer-image-0003"
  },
  "provenance": {
    "runId": "run-2026-0001"
  },
  "reproducibilityInformation": {
    "engineVersion": "1.0.0"
  }
}
```

---

### 12.7.4 Notes

This example illustrates how GARI aggregates preservation-oriented artifacts into a single Saved Run Package.

The Saved Run Package serves as the principal preservation artifact of GARI.

---

## 12.8 Chapter Summary

This chapter provided canonical Saved Run Package examples recognized by GARI v1.0.

The chapter illustrated:

* minimal Saved Run Packages;
* rich Saved Run Packages;
* Output Package to Saved Run Package transformation;
* positive-result preservation;
* negative-result preservation;
* reproducibility information;
* Saved Run Package artifact relationships.

Most importantly, the chapter established the architectural distinction between:

```text
Alignment Engine Output
```

and:

```text
GARI Preservation Artifact
```

Conceptually:

```text
Alignment Engine

↓

Output Package

↓

GARI

↓

Saved Run Package
```

Output Packages originate from Alignment Engines.

Saved Run Packages originate from GARI.

Saved Run Packages preserve Alignment Engine outputs and the information necessary to interpret, inspect, share, and reproduce completed Alignment Runs.

```
```

# Chapter 13 — Package Layout Examples

## 13.1 Purpose

This chapter provides canonical package layout examples for GARI v1.0 runtime artifacts.

The examples are intended to support:

* implementation;
* interoperability testing;
* fixture generation;
* acceptance testing;
* conformance evaluation.

The examples illustrate physical package organization only.

The examples do not introduce new architecture or runtime behavior.

---

## 13.2 Conventions

The directory structures presented in this chapter are illustrative.

Implementations MAY organize internal files differently provided they remain consistent with the authoritative specifications.

The examples are intended to demonstrate artifact relationships and package contents.

---

## 13.3 Output Package Layout Example

### 13.3.1 Purpose

This section illustrates a canonical Output Package layout.

Output Packages are produced by Alignment Engines.

---

### 13.3.2 Traceability

Derived From:

Release Candidate

* Section 5 — Output Package

Implementation Specification

* Section 7.8 — Output Package Model

---

### 13.3.3 Example Layout

```text
output-package/

├── output-package.json

├── alignment-results.json

├── constructed-realizations.json

├── layer-image.json

├── provenance.json

└── engine-metadata.json
```

---

### 13.3.4 Notes

This example illustrates separation of major Output Package artifacts.

Implementations MAY consolidate artifacts into fewer files provided the logical contents remain equivalent.

---

## 13.4 Rich Output Package Layout Example

### 13.4.1 Purpose

This section illustrates a richer Output Package layout containing additional Alignment Engine artifacts.

---

### 13.4.2 Example Layout

```text
output-package/

├── output-package.json

├── alignment-results.json

├── constructed-realizations.json

├── layer-image.json

├── provenance.json

├── engine-metadata.json

├── engine-notes.md

└── logs/

    ├── execution-log.txt

    └── diagnostics.json
```

---

### 13.4.3 Notes

The additional artifacts shown in this example are illustrative.

The Release Candidate does not require diagnostic logs.

---

## 13.5 Saved Run Package Layout Example

### 13.5.1 Purpose

This section illustrates a canonical Saved Run Package layout.

Saved Run Packages are produced by GARI following receipt of an Output Package.

---

### 13.5.2 Traceability

Derived From:

Release Candidate

* Section 6 — Saved Run Package

Implementation Specification

* Section 7.11 — Saved Run Package Model

---

### 13.5.3 Example Layout

```text
saved-run/

├── saved-run-package.json

├── output-package/

│   ├── output-package.json
│   ├── alignment-results.json
│   ├── constructed-realizations.json
│   ├── layer-image.json
│   ├── provenance.json
│   └── engine-metadata.json

└── reproducibility-information.json
```

---

### 13.5.4 Notes

This example demonstrates preservation of the Alignment Engine-produced Output Package within the Saved Run Package.

The Saved Run Package does not recreate Alignment Results or Constructed Realizations.

The Saved Run Package preserves them.

---

## 13.6 Rich Saved Run Package Layout Example

### 13.6.1 Purpose

This section illustrates a richer Saved Run Package containing additional preservation-oriented artifacts.

---

### 13.6.2 Example Layout

```text
saved-run/

├── saved-run-package.json

├── output-package/

│   ├── output-package.json
│   ├── alignment-results.json
│   ├── constructed-realizations.json
│   ├── layer-image.json
│   ├── provenance.json
│   ├── engine-metadata.json
│   └── engine-notes.md

├── reproducibility-information.json

├── manifests/

│   └── manifest.json

└── metadata/

    └── save-metadata.json
```

---

### 13.6.3 Notes

The additional artifacts shown are illustrative examples intended to support inspection and reproducibility activities.

---

## 13.7 Saved Run ZIP Example

### 13.7.1 Purpose

This section illustrates the canonical archive structure produced by a Save Run operation.

---

### 13.7.2 Conceptual Relationship

```text
Alignment Engine

↓

Output Package

↓

GARI

↓

Saved Run Package

↓

ZIP Archive
```

---

### 13.7.3 Example Archive Layout

```text
saved-run-0001.zip

└── saved-run/

    ├── saved-run-package.json

    ├── output-package/

    │   ├── output-package.json
    │   ├── alignment-results.json
    │   ├── constructed-realizations.json
    │   ├── layer-image.json
    │   ├── provenance.json
    │   └── engine-metadata.json

    └── reproducibility-information.json
```

---

### 13.7.4 Notes

This example illustrates one possible archive representation.

The archive structure is intended to preserve all information necessary for interpretation and reproducibility.

---

## 13.8 Package Ownership Example

### 13.8.1 Purpose

This section summarizes package ownership responsibilities within GARI v1.0.

---

### 13.8.2 Ownership Relationship

Conceptually:

```text
Alignment Engine

    owns

        Output Package
        Alignment Results
        Constructed Realizations
        Engine Metadata
        Engine Notes

↓

GARI

    owns

        Saved Run Package
        Preservation Metadata
        Reproducibility Metadata
        ZIP Packaging
```

---

### 13.8.3 Notes

This ownership model preserves:

* Alignment Engine independence;
* Output Package ownership;
* Black-box execution boundaries;
* reproducibility requirements.

---

## 13.9 Chapter Summary

This chapter provided canonical package layout examples recognized by GARI v1.0.

The chapter illustrated:

* Output Package layouts;
* Saved Run Package layouts;
* ZIP archive layouts;
* package ownership relationships.

Most importantly, the chapter demonstrated the physical organization of runtime artifacts and preservation artifacts.

Conceptually:

```text
Alignment Engine

↓

Output Package

↓

GARI

↓

Saved Run Package

↓

ZIP Archive
```

The examples support implementation, interoperability testing, fixture generation, and future conformance activities while preserving the architectural boundaries established by the Release Candidate and Implementation Specification.


# Chapter 14 — Manifest Examples

## 14.1 Purpose

This chapter provides canonical manifest examples for GARI v1.0 runtime and preservation artifacts.

Manifest examples support:

* package inspection;
* artifact enumeration;
* traceability;
* fixture generation;
* interoperability testing;
* conformance evaluation.

The examples presented in this chapter are illustrative.

They do not introduce new architecture or runtime behavior.

---

## 14.2 Conventions

The examples in this chapter use:

```text
manifest.json
```

as the illustrative manifest filename.

Implementations MAY use different manifest filenames provided the contents remain logically equivalent.

Manifest examples are informative.

Normative requirements remain within the Release Candidate and Implementation Specification.

---

## 14.3 Minimal Manifest Example

### 14.3.1 Purpose

This section illustrates a minimal manifest suitable for simple package inventory purposes.

---

### 14.3.2 Example

```json
{
  "manifestId": "manifest-0001",
  "artifacts": [
    "output-package.json"
  ]
}
```

---

### 14.3.3 Notes

This example illustrates:

* manifest identity;
* artifact enumeration.

The example is intentionally minimal.

---

## 14.4 Output Package Manifest Example

### 14.4.1 Purpose

This section illustrates a manifest associated with an Alignment Engine-produced Output Package.

---

### 14.4.2 Traceability

Derived From:

Release Candidate

* Section 5 — Output Package

Implementation Specification

* Section 7.8 — Output Package Model

---

### 14.4.3 Example

```json
{
  "manifestId": "manifest-output-0001",
  "packageType": "output-package",
  "artifacts": [
    {
      "name": "output-package.json",
      "type": "output-package"
    },
    {
      "name": "alignment-results.json",
      "type": "alignment-results"
    },
    {
      "name": "constructed-realizations.json",
      "type": "constructed-realizations"
    },
    {
      "name": "layer-image.json",
      "type": "layer-image"
    },
    {
      "name": "provenance.json",
      "type": "provenance"
    },
    {
      "name": "engine-metadata.json",
      "type": "engine-metadata"
    }
  ]
}
```

---

### 14.4.4 Notes

This example illustrates inventory of the principal artifacts contained within an Output Package.

The manifest does not generate or modify package contents.

The manifest describes package contents.

---

## 14.5 Saved Run Package Manifest Example

### 14.5.1 Purpose

This section illustrates a manifest associated with a GARI-produced Saved Run Package.

---

### 14.5.2 Traceability

Derived From:

Release Candidate

* Section 6 — Saved Run Package

Implementation Specification

* Section 7.11 — Saved Run Package Model

---

### 14.5.3 Example

```json
{
  "manifestId": "manifest-saved-run-0001",
  "packageType": "saved-run-package",
  "artifacts": [
    {
      "name": "saved-run-package.json",
      "type": "saved-run-package"
    },
    {
      "name": "output-package/",
      "type": "preserved-output-package"
    },
    {
      "name": "reproducibility-information.json",
      "type": "reproducibility-information"
    }
  ]
}
```

---

### 14.5.4 Notes

This example illustrates inventory of the major artifacts preserved within a Saved Run Package.

The Saved Run Package manifest describes preserved content.

The manifest does not recreate Alignment Engine outputs.

---

## 14.6 Rich Manifest Example

### 14.6.1 Purpose

This section illustrates a richer manifest suitable for inspection and testing activities.

---

### 14.6.2 Example

```json
{
  "manifestId": "manifest-0002",
  "packageType": "saved-run-package",
  "generatedAt": "2026-06-19T12:15:00Z",
  "artifacts": [
    {
      "name": "saved-run-package.json",
      "type": "saved-run-package"
    },
    {
      "name": "output-package/",
      "type": "preserved-output-package"
    },
    {
      "name": "reproducibility-information.json",
      "type": "reproducibility-information"
    },
    {
      "name": "manifests/manifest.json",
      "type": "manifest"
    }
  ]
}
```

---

### 14.6.3 Notes

This example demonstrates additional metadata that may support package inspection and traceability.

The example is illustrative only.

---

## 14.7 Manifest Traceability Example

### 14.7.1 Purpose

This section illustrates the relationship between manifests and package artifacts.

---

### 14.7.2 Conceptual Relationship

```text id="m4v7sz"
Manifest

↓

Artifact Inventory

↓

Package Inspection

↓

Traceability
```

---

### 14.7.3 Example

```json
{
  "manifestId": "manifest-output-0001",
  "references": [
    "alignment-results.json",
    "constructed-realizations.json",
    "layer-image.json",
    "provenance.json"
  ]
}
```

---

### 14.7.4 Notes

This example illustrates how manifests may support artifact discovery and inspection activities.

---

## 14.8 Manifest and Ownership Example

### 14.8.1 Purpose

This section reinforces the ownership model established throughout the document.

---

### 14.8.2 Conceptual Relationship

```text id="2xq0q7"
Alignment Engine

↓

Output Package

↓

Output Package Manifest

↓

GARI

↓

Saved Run Package

↓

Saved Run Package Manifest
```

---

### 14.8.3 Notes

Output Package manifests describe Alignment Engine-produced artifacts.

Saved Run Package manifests describe GARI-produced preservation artifacts.

The manifest reflects package ownership but does not alter package ownership.

---

## 14.9 Chapter Summary

This chapter provided canonical manifest examples recognized by GARI v1.0.

The chapter illustrated:

* minimal manifests;
* Output Package manifests;
* Saved Run Package manifests;
* rich manifests;
* manifest traceability relationships;
* manifest ownership relationships.

Most importantly, the chapter demonstrated how manifests support package inventory, inspection, traceability, interoperability testing, and conformance activities.

Conceptually:

```text id="xwkk8x"
Manifest

↓

Artifact Inventory

↓

Inspection

↓

Traceability
```

The examples in this chapter are intended to support implementation and testing activities while preserving the ownership and architectural boundaries established elsewhere in the GARI v1.0 specification suite.


# Chapter 15 — Acceptance-Test Fixtures

## 15.1 Purpose

This chapter provides canonical acceptance-test fixtures for GARI v1.0.

The fixtures are intended to support:

* software testing;
* implementation verification;
* interoperability testing;
* fixture generation;
* conformance evaluation.

The examples are illustrative.

Normative requirements remain within the Release Candidate and Implementation Specification.

---

## 15.2 Fixture Conventions

The fixtures presented in this chapter are:

* machine-readable;
* self-contained;
* minimal where possible;
* internally consistent.

Fixture identifiers are illustrative.

Implementations MAY use different identifiers while preserving logical equivalence.

---

## 15.3 Fixture 1 — Minimal Valid GB-FDO

### Purpose

Verify successful handling of a minimal Goal-bearing FAIR Digital Object.

### Fixture

```json id="vj8mr3"
{
  "pid": "gbfdo-goal-001",
  "type": "GB-FDO",
  "profileReference": "goal-profile-v1",
  "metadata": {
    "goalRepresentations": [
      {
        "representationType": "dfsk",
        "value": {
          "desiredOutputs": [
            "readmission-risk-score"
          ]
        }
      }
    ]
  },
  "bitstreamReference": "goal-representation.json"
}
```

### Expected Outcome

```text id="9nb5l2"
Valid GB-FDO
```

---

## 15.4 Fixture 2 — Minimal Valid CBKB-FDO

### Purpose

Verify successful handling of a minimal CBKB-bearing FAIR Digital Object.

### Fixture

```json id="m49xk7"
{
  "pid": "cbkbfdo-001",
  "type": "CBKB-FDO",
  "profileReference": "cbk-profile-v1",
  "metadata": {
    "producedOutputs": [
      "readmission-risk-score"
    ]
  },
  "bitstreamReference": "cbk-artifact.bin"
}
```

### Expected Outcome

```text id="4v4kj5"
Valid CBKB-FDO
```

---

## 15.5 Fixture 3 — Minimal Valid Layer

### Purpose

Verify successful Layer establishment.

### Fixture

```json id="ly4r7x"
{
  "gbFdos": [
    "gbfdo-goal-001"
  ],
  "cbkbFdos": [
    "cbkbfdo-001"
  ]
}
```

### Expected Outcome

```text id="f7cp7q"
Valid Layer
```

---

## 15.6 Fixture 4 — Minimal Valid Engine Profile

### Purpose

Verify successful handling of an Alignment Engine Profile.

### Fixture

```json id="n3x4da"
{
  "engineName": "DFSK Alignment Engine",
  "engineVersion": "1.0.0"
}
```

### Expected Outcome

```text id="9z9a5j"
Valid Engine Profile
```

---

## 15.7 Fixture 5 — Minimal Valid Input Package

### Purpose

Verify successful Input Package construction.

### Fixture

```json id="s9u5wt"
{
  "runId": "run-2026-0001",
  "engineProfileReference": "engine-profile-001",
  "layerImageReference": "layer-image-0001"
}
```

### Expected Outcome

```text id="0yszpy"
Valid Input Package
```

---

## 15.8 Fixture 6 — Positive Alignment Output Package

### Purpose

Verify successful handling of a positive Alignment Engine output.

### Fixture

```json id="j8p3d2"
{
  "runId": "run-2026-0001",
  "alignmentResults": [
    {
      "goalId": "gbfdo-goal-001",
      "alignmentStatus": true,
      "alignedCbkIds": [
        "cbkbfdo-001"
      ]
    }
  ],
  "constructedRealizations": [
    {
      "realizationId": "cr-0001"
    }
  ]
}
```

### Expected Outcome

```text id="whf2gc"
Valid Output Package

Positive Alignment Result

One Constructed Realization
```

---

## 15.9 Fixture 7 — Negative Alignment Output Package

### Purpose

Verify successful handling of a negative Alignment Engine output.

### Fixture

```json id="zddqzz"
{
  "runId": "run-2026-0002",
  "alignmentResults": [
    {
      "goalId": "gbfdo-goal-002",
      "alignmentStatus": false,
      "alignedCbkIds": [],
      "constructedRealizations": []
    }
  ]
}
```

### Expected Outcome

```text id="qv2tk0"
Valid Output Package

Negative Alignment Result

No Constructed Realizations
```

---

## 15.10 Fixture 8 — Minimal Valid Saved Run Package

### Purpose

Verify successful preservation of a completed Alignment Run.

### Fixture

```json id="2ztzzk"
{
  "savedRunId": "saved-run-0001",
  "runId": "run-2026-0001",
  "outputPackageId": "output-package-0001"
}
```

### Expected Outcome

```text id="tq1dxf"
Valid Saved Run Package
```

---

## 15.11 Composite Fixture Example

### Purpose

Verify successful handling of a complete minimal Alignment Run lifecycle.

---

### Fixture Set

```text id="mh1g5u"
Fixture 1
+
Fixture 2
+
Fixture 3
+
Fixture 4
+
Fixture 5
+
Fixture 6
+
Fixture 8
```

---

### Expected Outcome

```text id="hh5iq4"
Successful End-to-End Run

Valid Output Package

Valid Saved Run Package
```

---

## 15.12 Negative Validation Fixture Examples

### Purpose

Verify failure handling for invalid artifacts.

---

### Example A

Missing Engine Profile Reference

```json id="vngjlwm"
{
  "runId": "run-2026-0001",
  "layerImageReference": "layer-image-0001"
}
```

Expected Outcome:

```text id="nsjlwm"
Invalid Input Package
```

---

### Example B

Missing Layer Image Reference

```json id="m0x94v"
{
  "runId": "run-2026-0001",
  "engineProfileReference": "engine-profile-001"
}
```

Expected Outcome:

```text id="l0n8gm"
Invalid Input Package
```

---

### Example C

Invalid FDO Type

```json id="0rfh86"
{
  "pid": "object-001",
  "type": "UNKNOWN"
}
```

Expected Outcome:

```text id="9h7mxr"
Invalid FDO
```

---

## 15.13 Fixture Traceability Matrix

### Purpose

Illustrate fixture coverage across major runtime artifacts.

---

### Example

```text id="7p3s2m"
Fixture 1 → GB-FDO

Fixture 2 → CBKB-FDO

Fixture 3 → Layer

Fixture 4 → Engine Profile

Fixture 5 → Input Package

Fixture 6 → Positive Output Package

Fixture 7 → Negative Output Package

Fixture 8 → Saved Run Package
```

---

## 15.14 Chapter Summary

This chapter provided canonical acceptance-test fixtures for GARI v1.0.

The chapter illustrated:

* valid artifact fixtures;
* invalid artifact fixtures;
* positive alignment fixtures;
* negative alignment fixtures;
* end-to-end fixture composition;
* fixture traceability.

Most importantly, the chapter provides a baseline fixture library suitable for:

* implementation testing;
* interoperability testing;
* AI-assisted development;
* conformance evaluation.

Conceptually:

```text id="pjlwm9"
Reference Artifact

↓

Fixture

↓

Implementation Test

↓

Conformance Evidence
```

The fixtures in this chapter are intended to serve as reusable implementation assets supporting the practical realization of GARI v1.0.


# Appendix A — Identifier Examples

## Status

Normative: Informative

---

## Purpose

This appendix provides canonical identifier examples for major GARI v1.0 artifacts.

The examples are intended to support:

* implementation;
* fixture generation;
* interoperability testing;
* acceptance testing;
* conformance evaluation.

The examples are illustrative only.

The examples do not prescribe identifier generation methods.

Normative requirements remain within the Release Candidate and Implementation Specification.

---

# A.1 Identifier Conventions

The examples in this appendix use human-readable identifier formats.

Implementations MAY use:

* UUIDs;
* URIs;
* FAIR Digital Object identifiers;
* repository-specific identifiers;
* locally generated identifiers.

The examples are intended to illustrate identifier usage rather than identifier generation.

---

# A.2 Goal-Bearing FAIR Digital Object Identifiers

## Example

```text id="aqe96r"
gbfdo-goal-001
```

Additional Examples:

```text id="jlwmcw"
gbfdo-goal-002

gbfdo-goal-003

gbfdo-goal-004
```

### Notes

The examples illustrate identifiers associated with Goal-bearing FAIR Digital Objects.

The examples do not imply any required naming convention.

---

# A.3 CBK-bearing FAIR Digital Object Identifiers

## Example

```text id="d6p2xz"
cbkbfdo-001
```

Additional Examples:

```text id="sh1p8d"
cbkbfdo-002

cbkbfdo-003

cbkbfdo-004
```

### Notes

The examples illustrate identifiers associated with CBKB-bearing FAIR Digital Objects.

---

# A.4 Layer Image Identifiers


## Example

```text id="jq5z8s"
layer-image-0001
```

Additional Examples:

```text id="e9d0nx"
layer-image-0002

layer-image-0003

layer-image-0004
```

### Notes

The examples illustrate identifiers associated with Layer Images.

---

# A.6 Alignment Engine Profile Identifiers

## Example

```text id="lq8n0k"
engine-profile-001
```

Additional Examples:

```text id="q9g5vr"
engine-profile-002

engine-profile-003
```

### Notes

The examples illustrate identifiers associated with Alignment Engine Profiles.

---

# A.7 Alignment Run Identifiers

## Example

```text id="z4xw39"
run-2026-0001
```

Additional Examples:

```text id="t1cpow"
run-2026-0002

run-2026-0003

run-2026-0004
```

### Notes

The examples illustrate identifiers associated with Alignment Runs.

The year component is illustrative only.

---

# A.8 Input Package Identifiers

## Example

```text id="0n2u9e"
input-package-0001
```

Additional Examples:

```text id="8fgx6j"
input-package-0002

input-package-0003
```

### Notes

The examples illustrate identifiers associated with Input Packages.

---

# A.9 Alignment Result Identifiers

## Example

```text id="p4d2ec"
alignment-result-0001
```

Additional Examples:

```text id="m2vh8k"
alignment-result-0002

alignment-result-0003
```

### Notes

The examples illustrate identifiers associated with Alignment Results.

---

# A.10 Constructed Realization Identifiers

## Example

```text id="c6d4zv"
cr-0001
```

Additional Examples:

```text id="t8j0m5"
cr-0002

cr-0003

cr-0004
```

### Notes

The examples illustrate identifiers associated with Constructed Realizations.

---

# A.11 Output Package Identifiers

## Example

```text id="h1r4ga"
output-package-0001
```

Additional Examples:

```text id="z5v0xn"
output-package-0002

output-package-0003
```

### Notes

The examples illustrate identifiers associated with Alignment Engine-produced Output Packages.

---

# A.12 Saved Run Package Identifiers

## Example

```text id="i8z2cr"
saved-run-0001
```

Additional Examples:

```text id="j7k1ml"
saved-run-0002

saved-run-0003
```

### Notes

The examples illustrate identifiers associated with Saved Run Packages.

---

# A.13 Manifest Identifiers

## Example

```text id="8x7kqa"
manifest-0001
```

Additional Examples:

```text id="f2v8wp"
manifest-0002

manifest-0003
```

### Notes

The examples illustrate identifiers associated with manifests.

---

# A.14 Provenance Object Identifiers

## Example

```text id="n5s4eo"
prov-0001
```

Additional Examples:

```text id="r4g6kc"
prov-0002

prov-0003
```

### Notes

The examples illustrate identifiers associated with provenance objects.

---

# A.15 Composite Identifier Example

## Purpose

This section illustrates identifier relationships across a complete Alignment Run.

---

## Example

```text id="q7j4fw"
Goal:
gbfdo-goal-001

CBK:
cbkbfdo-001

Layer:
layer-image-0001

Layer Image:
layer-image-0001

Engine Profile:
engine-profile-001

Run:
run-2026-0001

Input Package:
input-package-0001

Alignment Result:
alignment-result-0001

Constructed Realization:
cr-0001

Output Package:
output-package-0001

Saved Run Package:
saved-run-0001
```

---

### Notes

This example demonstrates one possible identifier set associated with a complete Alignment Run lifecycle.

The example is intended to support implementation and testing activities.

---

# A.16 Identifier Relationship Summary

Conceptually:

```text id="7cwzvt"
GB-FDO

↓

Layer

↓

Layer Image

↓

Input Package

↓

Alignment Run

↓

Alignment Result

↓

Constructed Realization

↓

Output Package

↓

Saved Run Package
```

The identifier examples presented in this appendix are intended to provide a reusable reference library for developers, test engineers, AI coding systems, and future conformance programs.

The examples are illustrative and do not prescribe identifier generation methods.

# Appendix B — JSON Schema Mapping Guide

## Status

Normative: Informative

---

## Purpose

This appendix provides a mapping between the example artifacts presented in this document and the corresponding implementation models described in the GARI v1.0 Implementation Specification.

The appendix is intended to support:

* implementation;
* schema development;
* fixture generation;
* interoperability testing;
* conformance evaluation.

The appendix is informative.

The appendix does not define normative JSON Schemas.

Normative requirements remain within:

```text
GARI-v1.0-Specification-Release-Candidate-Reconciled.md
```

and

```text
GARI-v1.0-Implementation-Specification.md
```

---

# B.1 Mapping Conventions

The mappings presented in this appendix associate:

```text id="h0rkvy"
Reference Data Schema Example

↓

Implementation Model
```

The mappings are intended to support traceability.

The mappings do not define validation rules.

---

# B.2 Goal-Bearing FAIR Digital Object Mapping

## Reference Data Schema Section

```text id="gmqln9"
Chapter 3.1

Minimal GB-FDO
```

## Implementation Specification Mapping

```text id="7cwplf"
GB-FDO Model
```

## Purpose

Illustrates the implementation model associated with Goal-bearing FAIR Digital Objects.

---

# B.3 CBKB-Bearing FAIR Digital Object Mapping

## Reference Data Schema Section

```text id="2kx24g"
Chapter 3.2

Minimal CBKB-FDO
```

## Implementation Specification Mapping

```text id="xjlwm0"
CBKB-FDO Model
```

## Purpose

Illustrates the implementation model associated with CBKB-bearing FAIR Digital Objects.

---

# B.4 Layer Mapping

## Reference Data Schema Sections

```text id="mtvtn0"
Chapter 4.1

Minimal Layer

Chapter 4.2

Multi-Goal Layer
```

## Implementation Specification Mapping

```text id="49ntaj"
Layer Model
```

## Purpose

Illustrates the implementation model associated with Layer Images.

---

# B.5 Layer Image Mapping

## Reference Data Schema Sections

```text id="i1tlh5"
Chapter 5

Layer Image Examples
```

## Implementation Specification Mapping

```text id="nmn9m7"
Layer Image Model
```

## Purpose

Illustrates the implementation model associated with Layer Images.

---

# B.6 Alignment Engine Profile Mapping

## Reference Data Schema Sections

```text id="6hjlwm"
Chapter 6

Alignment Engine Profile Examples
```

## Implementation Specification Mapping

```text id="vb9g0r"
Alignment Engine Profile Model
```

## Purpose

Illustrates the implementation model associated with Alignment Engine Profiles.

---

# B.7 Input Package Mapping

## Reference Data Schema Sections

```text id="mjlwm3"
Chapter 7

Input Package Examples
```

## Implementation Specification Mapping

```text id="n4af1o"
Input Package Model
```

## Purpose

Illustrates the implementation model associated with Input Packages.

---

# B.8 Alignment Result Graph Mapping

## Reference Data Schema Sections

```text id="v7c7o5"
Chapter 8

Alignment Result Graph Examples
```

## Implementation Specification Mapping

```text id="p2l4ha"
Alignment Result Graph Model
```

## Purpose

Illustrates the implementation model associated with Alignment Result Graphs.

---

# B.9 Constructed Realization Mapping

## Reference Data Schema Sections

```text id="qf1l2d"
Chapter 9

Constructed Realization Examples
```

## Implementation Specification Mapping

```text id="0j6f1y"
Constructed Realization Model
```

## Purpose

Illustrates the implementation model associated with Constructed Realizations.

---

# B.10 Provenance Mapping

## Reference Data Schema Sections

```text id="dd3kz0"
Chapter 10

Provenance Examples
```

## Implementation Specification Mapping

```text id="3cjlwm"
Provenance Model
```

## Purpose

Illustrates the implementation model associated with provenance objects.

---

# B.11 Output Package Mapping

## Reference Data Schema Sections

```text id="8jlwmn"
Chapter 11

Output Package Examples
```

## Implementation Specification Mapping

```text id="uxh2r5"
Output Package Model
```

## Purpose

Illustrates the implementation model associated with Alignment Engine-produced Output Packages.

---

# B.12 Saved Run Package Mapping

## Reference Data Schema Sections

```text id="fjlwm0"
Chapter 12

Saved Run Package Examples
```

## Implementation Specification Mapping

```text id="s7kn18"
Saved Run Package Model
```

## Purpose

Illustrates the implementation model associated with GARI-produced Saved Run Packages.

---

# B.13 Package Layout Mapping

## Reference Data Schema Sections

```text id="2jlwm8"
Chapter 13

Package Layout Examples
```

## Implementation Specification Mapping

```text id="q5xm0j"
Output Package Layout Model

Saved Run Package Layout Model
```

## Purpose

Illustrates mappings between logical implementation models and physical package structures.

---

# B.14 Manifest Mapping

## Reference Data Schema Sections

```text id="jlwm91"
Chapter 14

Manifest Examples
```

## Implementation Specification Mapping

```text id="v2cp0n"
Manifest Model
```

## Purpose

Illustrates implementation mappings associated with package manifests.

---

# B.15 Acceptance-Test Fixture Mapping

## Reference Data Schema Sections

```text id="qjlwm3"
Chapter 15

Acceptance-Test Fixtures
```

## Implementation Specification Mapping

```text id="n6u0o7"
All Major Runtime Models
```

## Purpose

Illustrates how acceptance-test fixtures correspond to implementation models.

---

# B.16 Consolidated Mapping Matrix

| Reference Data Schema Section | Implementation Model           |
| ----------------------------- | ------------------------------ |
| Chapter 3                     | GB-FDO Model                   |
| Chapter 3                     | CBKB-FDO Model                 |
| Chapter 4                     | Layer Model                    |
| Chapter 5                     | Layer Image Model              |
| Chapter 6                     | Alignment Engine Profile Model |
| Chapter 7                     | Input Package Model            |
| Chapter 8                     | Alignment Result Graph Model   |
| Chapter 9                     | Constructed Realization Model  |
| Chapter 10                    | Provenance Model               |
| Chapter 11                    | Output Package Model           |
| Chapter 12                    | Saved Run Package Model        |
| Chapter 13                    | Package Layout Models          |
| Chapter 14                    | Manifest Model                 |
| Chapter 15                    | Acceptance-Test Fixture Models |

---

# B.17 Traceability Summary

Conceptually:

```text id="gw4qsl"
Release Candidate

↓

Implementation Specification

↓

Reference Data Schemas

↓

Examples

↓

Fixtures

↓

Implementations
```

The mappings presented in this appendix are intended to support traceability between:

* architectural requirements;
* implementation models;
* reference examples;
* testing artifacts.

The appendix does not define normative schemas, validation rules, or implementation requirements.

Its purpose is to support consistent interpretation and realization of the GARI v1.0 architecture.

# Appendix C — Runtime Artifact Relationship Guide

## Status

Normative: Informative

---

## Purpose

This appendix provides a consolidated view of the major runtime artifacts defined and illustrated throughout the GARI v1.0 Reference Data Schemas document.

The appendix is intended to support:

* implementation;
* inspection;
* testing;
* interoperability evaluation;
* conformance evaluation.

The appendix is informative.

The appendix introduces no new architecture, concepts, or runtime behavior.

---

# C.1 Relationship Conventions

The diagrams and examples presented in this appendix are conceptual.

They are intended to illustrate artifact relationships.

They do not prescribe implementation technologies or internal software architectures.

---

# C.2 Core Runtime Relationship

## Purpose

Provide a consolidated view of the primary GARI runtime flow.

---

## Conceptual Relationship

```text id="h1g7vz"
Goal

↓

GB-FDO

+

CBKB-FDO

↓

Layer

↓

Layer Image

↓

Input Package

↓

Alignment Engine

↓

Alignment Result Graph

+

Constructed Realizations

↓

Output Package

↓

GARI

↓

Saved Run Package
```

---

## Notes

This relationship summarizes the primary runtime artifact flow represented throughout the document.

---

# C.3 Layer Relationship Guide

## Purpose

Illustrate relationships among Goals, FDOs, Layers, and Layer Images.

---

## Conceptual Relationship

```text id="5k8v3p"
GB-FDO(s)

+

CBKB-FDO(s)

↓

Layer

↓

Layer Image
```

---

## Notes

The Layer Image represents the metadata available to the Alignment Engine during an Alignment Run.

The Layer Image is derived from the established Layer.

---

# C.4 Input Package Relationship Guide

## Purpose

Illustrate the relationships associated with Input Package construction.

---

## Conceptual Relationship

```text id="c7m4xt"
Layer Image

+

Engine Profile

↓

Input Package
```

---

## Notes

The Input Package is provided to the Alignment Engine.

The Input Package serves as the primary Alignment Engine input artifact.

---

# C.5 Alignment Relationship Guide

## Purpose

Illustrate the relationships among Input Packages, Alignment Engines, Alignment Results, and Constructed Realizations.

---

## Conceptual Relationship

```text id="t4x9zs"
Input Package

↓

Alignment Engine

↓

Alignment Result Graph

+

Constructed Realizations
```

---

## Notes

Alignment Engines determine alignment outcomes and identify Constructed Realizations.

The internal methods used by Alignment Engines are outside the scope of GARI.

---

# C.6 Constructed Realization Relationship Guide

## Purpose

Illustrate the relationship between Goals and Constructed Realizations.

---

## Conceptual Relationship

```text id="j6w1kp"
Goal

↓

Constructed Realization

↓

CBKB-FDO Sequence
```

---

## Example

```text id="a5v3fh"
Goal

↓

CBKB-FDO-001

↓

CBKB-FDO-002

↓

Desired Computational Output
```

---

## Notes

For purposes of GARI v1.0 examples, Constructed Realizations are represented as fixed computational sequences.

---

# C.7 Output Package Relationship Guide

## Purpose

Illustrate the artifact composition of Output Packages.

---

## Conceptual Relationship

```text id="v8g7pc"
Alignment Result Graph

+

Constructed Realizations

+

Layer Image

+

Provenance

+

Engine Metadata

↓

Output Package
```

---

## Notes

Output Packages are produced by Alignment Engines.

Output Packages communicate Alignment Engine determinations.

---

# C.8 Output Package Ownership Guide

## Purpose

Illustrate Output Package ownership responsibilities.

---

## Conceptual Relationship

```text id="w2q9nd"
Alignment Engine

↓

Output Package
```

---

## Notes

Alignment Engines own:

* Alignment Result Graphs;
* Constructed Realizations;
* Engine Metadata;
* Engine Notes;
* Output Packages.

GARI receives and preserves Output Packages.

---

# C.9 Saved Run Package Relationship Guide

## Purpose

Illustrate the relationship between Output Packages and Saved Run Packages.

---

## Conceptual Relationship

```text id="u4m7xt"
Output Package

↓

GARI

↓

Saved Run Package
```

---

## Notes

Saved Run Packages preserve Output Packages and associated reproducibility information.

Saved Run Packages are produced by GARI.

---

# C.10 Saved Run Package Ownership Guide

## Purpose

Illustrate Saved Run Package ownership responsibilities.

---

## Conceptual Relationship

```text id="f9n2kv"
GARI

↓

Saved Run Package
```

---

## Notes

GARI owns:

* Saved Run Packages;
* preservation metadata;
* reproducibility information;
* packaging operations.

GARI does not generate Alignment Results or Constructed Realizations during Save Run operations.

---

# C.11 Provenance Relationship Guide

## Purpose

Illustrate provenance relationships across runtime artifacts.

---

## Conceptual Relationship

```text id="m7x5zw"
Alignment Run

↓

Alignment Result Graph

↓

Constructed Realization

↓

Output Package

↓

Saved Run Package
```

---

## Notes

Provenance supports:

* traceability;
* interpretation;
* reproducibility;
* inspection.

---

# C.12 Package Relationship Guide

## Purpose

Illustrate physical package relationships.

---

## Conceptual Relationship

```text id="q3w7pk"
Output Package

↓

Saved Run Package

↓

ZIP Archive
```

---

## Notes

The ZIP Archive preserves the Saved Run Package produced by GARI.

---

# C.13 Manifest Relationship Guide

## Purpose

Illustrate relationships between manifests and package artifacts.

---

## Conceptual Relationship

```text id="d4r6ym"
Output Package

↓

Output Package Manifest

Saved Run Package

↓

Saved Run Package Manifest
```

---

## Notes

Manifests provide artifact inventory and traceability support.

Manifests do not generate package contents.

---

# C.14 Acceptance-Test Fixture Relationship Guide

## Purpose

Illustrate fixture coverage across major runtime artifacts.

---

## Conceptual Relationship

```text id="r8n5wx"
Reference Artifact

↓

Acceptance-Test Fixture

↓

Implementation Test

↓

Conformance Evidence
```

---

## Notes

Fixtures provide reusable test assets supporting implementation verification.

---

# C.15 Consolidated Ownership Model

## Purpose

Provide a single view of artifact ownership across GARI v1.0.

---

## Conceptual Relationship

```text id="x5v7ct"
Alignment Engine

    owns

        Output Package
        Alignment Result Graph
        Constructed Realizations
        Engine Metadata
        Engine Notes

↓

GARI

    owns

        Saved Run Package
        Preservation Metadata
        Reproducibility Information
        Packaging Operations
```

---

## Notes

This ownership model preserves:

* Alignment Engine independence;
* Black-Box Engine execution;
* Output Package ownership;
* GARI preservation responsibilities.

---

# C.16 End-to-End Runtime Lifecycle

## Purpose

Provide a consolidated view of the complete GARI runtime lifecycle.

---

## Conceptual Relationship

```text id="n6q3yv"
Goal

↓

GB-FDO

+

CBKB-FDO

↓

Layer

↓

Layer Image

↓

Input Package

↓

Alignment Engine

↓

Alignment Result Graph

+

Constructed Realizations

↓

Output Package

↓

GARI

↓

Saved Run Package

↓

ZIP Archive
```

---

## Notes

This lifecycle summarizes the relationships among the major runtime artifacts presented throughout the document.

---

# C.17 Relationship Summary

This appendix provided a consolidated reference guide for the major runtime artifacts represented throughout the GARI v1.0 Reference Data Schemas document.

The appendix illustrated:

* Layer relationships;
* Input Package relationships;
* Alignment relationships;
* Constructed Realization relationships;
* Output Package relationships;
* Saved Run Package relationships;
* provenance relationships;
* package relationships;
* ownership relationships;
* fixture relationships.

Most importantly, the appendix provides a single consolidated view of the runtime artifact ecosystem represented by GARI v1.0.

Conceptually:

```text id="z7m4kf"
Goal

↓

GB-FDO

+

CBKB-FDO

↓

Layer

↓

Layer Image

↓

Input Package

↓

Alignment Engine

↓

Output Package

↓

GARI

↓

Saved Run Package
```

The appendix is intended to serve as a quick-reference implementation aid for developers, AI coding systems, QA engineers, interoperability reviewers, and future conformance programs.


