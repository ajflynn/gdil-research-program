

# Scientific Instrument Framing

GARI is a scientific instrument for the investigation of metadata-driven alignment between Goal-bearing FAIR Digital Objects and CBK-bearing FAIR Digital Objects.

GARI is not a knowledge application platform.

GARI does not apply knowledge to achieve operational outcomes.

Instead, GARI provides a controlled environment for investigating, evaluating, comparing, and reproducing alignment behavior produced by Alignment Engines operating on metadata representations.

The primary scientific result produced by GARI is the Alignment Result Graph.

# GARI v1.0 Specification

## GDIL Alignment Run Instrument

Version: GARI v1.0
Status: Release Candidate

---

# Integrated Table of Contents

1. Chapter 1 — Introduction
   1.1 Purpose
   1.2 Scope
   1.3 Audience
   1.4 Specification Organization
   1.5 Chapter Summary

2. Chapter 2 — Principles and Vocabulary Foundations
   2.1 Overview
   2.2 Vocabulary Governance
   2.3 Glossary and Vocabulary Index
   2.4 Principles
   2.5 Chapter Summary

3. Chapter 3 — Concepts and Structural Entities
   3.1 Overview
   3.2 Core Concepts
   3.3 FAIR Digital Object Specifications
   3.4 Layer Specification
   3.5 Chapter Summary

4. Chapter 4 — Runtime Architecture
   4.1 Overview
   4.2 Runtime Architecture Overview
   4.3 Input Package Specification
   4.4 Alignment Engine Specification
   4.5 Output Package Specification
   4.6 Runtime Lifecycle Summary
   4.7 Chapter Summary

5. Chapter 5 — Results and Provenance
   5.1 Overview
   5.2 Results Architecture Overview
   5.3 Alignment Result Graph Specification
   5.4 Provenance Specification
   5.5 State Model Specification
   5.6 Results Lifecycle Summary
   5.7 Chapter Summary

6. Chapter 6 — User Interaction, Persistence, and Future Boundaries
   6.1 Overview
   6.2 User Interface Specification
   6.3 Persistence Architecture Overview
   6.4 Saved Run Package Specification
   6.5 Preservation Lifecycle Summary
   6.6 Future Concepts Log
   6.7 Chapter Summary

Appendix A — Glossary

Appendix B — Principles Traceability Matrix

Appendix C — Conceptual Constructs and Artifact Model

Appendix D — Information Flow and Provenance Model

Appendix E — Specification Provenance and Contributions

---

# Chapter 1: Introduction

## 1.1 Purpose

The purpose of GARI v1.0 is to specify a scientific instrument for conducting investigations into goal-directed computable knowledge alignment.

GARI provides a structured environment in which Goal-bearing FAIR Digital Objects and Computable Biomedical Knowledge-bearing FAIR Digital Objects may be examined for potential alignment relationships through the use of Alignment Engines operating on metadata-only representations.

The instrument is intended to support the study, evaluation, comparison, and reproducibility of alignment activities involving goal-directed computable knowledge resources.

GARI is specified as an alignment investigation instrument rather than a knowledge application platform. The instrument does not execute computable knowledge, perform operational decision support, or apply knowledge to real-world situations. Instead, GARI focuses exclusively on the identification, representation, and analysis of potential alignment relationships between Goals and computable knowledge resources.

The specification establishes the conceptual constructs, structural entities, runtime architecture, result architecture, provenance architecture, persistence architecture, and user interaction architecture necessary to support rigorous and reproducible investigations of goal-directed computable knowledge alignment.

GARI adopts a metadata-driven approach in which Alignment Engines operate on metadata supplied through FAIR Digital Objects. The specification intentionally separates conceptual constructs from their representations, runtime execution from preservation activities, and alignment investigation from knowledge application.

The objective of GARI v1.0 is not to prescribe a particular alignment methodology. Rather, the objective is to provide a stable architectural foundation within which multiple Alignment Engines may be evaluated, compared, and studied as scientific instruments for goal-directed computable knowledge alignment.

## 1.2 Scope

This specification defines the architecture of GARI v1.0, a scientific instrument for investigating goal-directed computable knowledge alignment.

The scope of this specification includes:

* governing principles
* conceptual constructs
* FAIR Digital Object structures recognized by the instrument
* Layer establishment
* Input Package generation
* Alignment Engine integration
* Output Package generation
* Alignment Result Graph representation
* provenance requirements
* persistence requirements
* user interaction requirements

This specification defines how Goal-bearing FAIR Digital Objects and Computable Biomedical Knowledge-bearing FAIR Digital Objects participate in Alignment Runs and how resulting alignment artifacts are represented, preserved, and inspected.

The scope of GARI v1.0 is limited to alignment investigation.

The following are outside the scope of this specification:

* knowledge application
* execution of computable knowledge
* workflow orchestration
* metadata generation
* metadata repair
* metadata enrichment
* operational decision support
* clinical decision support
* artificial intelligence assistant functionality

This specification establishes the architectural foundation for conducting reproducible investigations of goal-directed computable knowledge alignment and does not prescribe specific alignment methodologies or Alignment Engine implementations.

## 1.3 Audience

This specification is intended for two primary audiences.

The first audience consists of computer science, information science, and software engineering professionals interested in implementing GARI as a scientific instrument. For these readers, the specification defines the principles, concepts, architectures, artifacts, interfaces, and requirements necessary to develop conformant GARI implementations and associated Alignment Engines.

The second audience consists of informaticians, knowledge scientists, researchers, and other stakeholders interested in understanding the operation of GARI and interpreting investigations conducted using GARI. For these readers, the specification defines the conceptual foundations, architectural assumptions, result structures, provenance requirements, and preservation mechanisms necessary to understand, evaluate, compare, and reproduce GARI-based investigations.

Readers interested primarily in implementation may focus on the runtime architecture, provenance architecture, state model, and user interface specifications.

Readers interested primarily in scientific use and interpretation may focus on the principles, conceptual model, Alignment Result Graphs, provenance model, and Saved Run Package specifications.

This specification is intended to support both implementation and scientific interpretation while maintaining a clear separation between the architecture of the instrument and the investigations conducted using the instrument.

## 1.4 Specification Organization

This specification is organized into six chapters and five appendices.

Chapter 2 establishes the principles and vocabulary foundations governing GARI.

Chapter 3 defines the conceptual constructs and structural entities recognized by the instrument.

Chapter 4 defines the runtime architecture through which Alignment Runs are conducted.

Chapter 5 defines the result structures, provenance requirements, and state model used to represent and manage Alignment Run outcomes.

Chapter 6 defines user interaction requirements, persistence requirements, and future architectural boundaries.

The appendices provide supporting reference material, including terminology support, principle traceability, conceptual and artifact models, information flow and provenance summaries, and specification provenance.

The chapters of this specification are intended to be read together. Principles defined in Chapter 2 govern all subsequent chapters. Concepts defined in Chapter 3 provide the foundation for the runtime architecture defined in Chapter 4. Results, provenance, and state structures defined in Chapter 5 build upon the runtime architecture. User interaction and persistence specifications defined in Chapter 6 build upon all preceding chapters.

In the event of a conflict between sections of this specification, the more authoritative specification element SHALL govern. Principles govern architectural specifications. Architectural specifications govern explanatory and informational material. The governing principles of GARI are defined in Section 2.4. Appendices are informative and SHALL NOT supersede normative content contained within Chapters 2–6.


## 1.5 Chapter Summary

This chapter introduced GARI v1.0 and established its purpose, scope, audience, and organization.

The chapter defined GARI as a scientific instrument for investigating goal-directed computable knowledge alignment and established the alignment-only and metadata-driven boundaries that govern the remainder of the specification.

The chapter also described the intended audiences for the specification and explained how the document is organized.

Subsequent chapters define the principles, concepts, runtime architecture, result architecture, provenance architecture, persistence architecture, and user interaction architecture of the instrument.


# Chapter 2: Principles and Vocabulary Foundations

## 2.1 Overview

Chapter 2 establishes the conceptual foundation of GARI v1.0.

Specifically, this chapter defines:

* vocabulary governance
* specification terminology
* foundational principles
* architectural principles
* user experience principles

Together these materials establish the conceptual identity of the instrument and the language used throughout the specification.

This chapter does not define runtime architecture.

Chapter 2 establishes the principles and vocabulary foundations that govern all subsequent specifications.

Accordingly:

* Chapter 3 defines the conceptual entities and structural entities recognized by the instrument.
* Chapter 4 defines runtime architecture.
* Chapter 5 defines results, provenance, and state.
* Chapter 6 defines user interaction, persistence, and future boundaries.

Chapter 2 establishes how the specification is governed.

Chapter 3 establishes what entities the specification recognizes.

Together Chapters 2 and 3 define the conceptual foundation of GARI v1.0.

All subsequent chapters inherit the principles established in this chapter and rely upon the conceptual model established in Chapter 3.

Authoritative definitions of conceptual entities are provided in Chapter 3.

The Glossary and Vocabulary Index in this chapter serves as a navigation and terminology aid and SHALL NOT supersede normative definitions provided elsewhere in the specification.

## 2.2 Vocabulary Governance

Definitions appearing throughout the GARI v1.0 Specification SHALL remain consistent with their authoritative definitions.

When conflicts arise:

1. Core Concepts (Chapter 3) SHALL govern conceptual definitions.
2. Specialized specification sections SHALL govern operational details.
3. Informative sections and appendices SHALL NOT supersede normative definitions.

## 2.3 Glossary and Vocabulary Index

The integrated specification retains the package-wide vocabulary index for navigation, terminology consistency, and concept discovery.

Authoritative definitions SHALL be obtained from the normative specification chapters.

Key indexed concepts include:

* Active Result
* Alignment Engine
* Alignment Engine Profile
* Alignment Result Graph
* Alignment Run
* CBK Artifact
* CBKB-FDO
* Clear Result
* Computable Biomedical Knowledge (CBK)
* Constructed Realization
* FAIR Digital Object (FDO)
* GB-FDO
* Goal
* Goal Representation
* Input Package
* Item
* Knowledge Application Method (KAM)
* Layer
* Layer Image
* Output Package
* Preservation Provenance
* Profile Reference
* Reproducibility Information
* Run Metadata
* Save Run
* Saved Run Metadata
* Saved Run Package

## 2.4 Principles

### 2.4.1 Tier 1 — Foundational Principles

#### 2.4.1.1 Scientific Instrument Principle

GARI SHALL be a scientific instrument for conducting investigations into goal-directed computable knowledge alignment.

GARI SHALL NOT function as a knowledge application platform.

#### 2.4.1.2 Alignment-Only Principle

GARI SHALL investigate alignment between Goal-bearing and CBK-bearing FAIR Digital Objects.

GARI SHALL NOT perform knowledge application.

GARI SHALL NOT execute CBK Artifacts.

#### 2.4.1.3 Metadata-Driven Alignment Principle

Alignment activities SHALL be based upon pre-existing metadata contained within FAIR Digital Objects.

Alignment Engines SHALL operate on metadata supplied through Input Packages.

Alignment within GARI SHALL be based upon metadata represented by the Layer Image.

Metadata used for alignment within GARI SHALL be limited to metadata represented by the Layer Image.

#### 2.4.1.4 No Metadata Generation Principle

Metadata used for alignment SHALL NOT be generated, repaired, enriched, or modified by GARI.

#### 2.4.1.5 Concept–Representation Separation Principle

GARI SHALL distinguish conceptual entities from their representations.

#### 2.4.1.6 Payload–Metadata Separation Principle

Metadata and payloads SHALL be treated as distinct entities.

### 2.4.2 Tier 2 — Architectural Principles

#### 2.4.2.1 One Engine per Run Principle

Each Alignment Run SHALL use exactly one Alignment Engine.

#### 2.4.2.2 Black-Box Engine Principle

Alignment Engines SHALL be treated as black-box computational components.

#### 2.4.2.3 Fixed Layer During Execution Principle

Layers SHALL be fixed when an Alignment Run begins.

#### 2.4.2.4 Ephemeral-by-Default Principle

Alignment Runs SHALL be transient unless explicitly saved by the user.

#### 2.4.2.5 User-Controlled Persistence Principle

Persistence SHALL occur only through explicit user action.

#### 2.4.2.6 Unsaved Run Protection Principle

GARI SHALL provide mechanisms that protect users from accidental loss of unsaved Alignment Run results.

#### 2.4.2.7 Negative Results Principle

Negative outcomes SHALL be considered valid scientific results.

#### 2.4.2.8 Authoritative Result Graph Principle

Every Output Package SHALL contain exactly one Alignment Result Graph.

#### 2.4.2.9 Engine Notes Separation Principle

Engine Notes SHALL NOT be part of Alignment Result Graphs.

#### 2.4.2.10 Saved Run Package Augmentation Principle

Saved Run Packages MAY add reproducibility-supporting information without altering Output Packages.

#### 2.4.2.11 Provenance Preservation Principle

GARI SHALL preserve sufficient provenance to support interpretation, inspection, comparison, and reproducibility.

#### 2.4.2.12 Layer Non-Persistence Principle

Layers SHALL be treated as conceptual constructs and SHALL NOT possess independent persistent identity.

### 2.4.3 Tier 3 — User Experience Principles

#### 2.4.3.1 Concept-Revealing UI Principle

The user interface SHALL expose GARI concepts directly.

#### 2.4.3.2 Scientific Instrument UI Principle

The user interface SHALL present GARI as a scientific instrument.

#### 2.4.3.3 Simplicity and Restraint Principle

The user interface SHALL emphasize simplicity, clarity, reliability, and restraint.

### 2.4.4 Principle Hierarchy

Tier 1 principles establish identity.

Tier 2 principles establish architecture.

Tier 3 principles establish presentation.

Conflicts SHALL be resolved in favor of the higher-tier principle.


## 2.5 Chapter Summary

This chapter established the principles and vocabulary foundations governing GARI v1.0.

The chapter defined vocabulary governance rules and introduced the foundational, architectural, and user experience principles that shape the identity and operation of the instrument.

These principles establish GARI as a scientific instrument for metadata-driven alignment investigation and define the architectural constraints that govern all subsequent specifications.

All subsequent chapters SHALL be interpreted consistently with the principles established in this chapter.


# Chapter 3: Concepts and Structural Entities

## 3.1 Overview

Chapter 3 defines the conceptual constructs and structural entities recognized by GARI v1.0.

Specifically, this chapter defines:

* Core Concepts
* FAIR Digital Object Specifications
* Layer Specifications

Together these specifications establish the conceptual model of the instrument.

This chapter defines what entities exist within the world of GARI.

This chapter does not define runtime execution.

This chapter does not define scientific results.

This chapter does not define persistence mechanisms.

Instead, this chapter defines the entities that participate in those activities.

Accordingly:

* Chapter 2 establishes governing principles and vocabulary foundations.
* Chapter 3 establishes conceptual and structural entities.
* Chapter 4 defines runtime architecture.
* Chapter 5 defines results, provenance, and state.
* Chapter 6 defines user interaction, persistence, and future boundaries.

## 3.2 Core Concepts

### 3.2.1 Purpose

This section defines the core concepts used throughout GARI v1.0.

These concepts provide the normative vocabulary of the specification.

All subsequent specification chapters SHALL use these definitions.

### 3.2.2 Goal

A Goal is a conceptual construct representing a desire for a computation to be performed.

### 3.2.3 Goal Representation

A Goal Representation is a representation of a Goal.

### 3.2.4 Computable Biomedical Knowledge (CBK)

Computable Biomedical Knowledge (CBK) is intentionally undefined by GARI.

### 3.2.5 CBK Artifact

A CBK Artifact is a representation of computable biomedical knowledge.

### 3.2.6 Knowledge Application Method (KAM)

A Knowledge Application Method is a method by which a CBK Artifact may be computationally applied.

### 3.2.7 Item

An Item is a data object that may serve as an input to, or output from, a Knowledge Application Method.

### 3.2.8 FAIR Digital Object (FDO)

A FAIR Digital Object is a digital object represented according to a declared FDO profile.

### 3.2.9 Goal-bearing FAIR Digital Object (GB-FDO)

A Goal-bearing FAIR Digital Object is an FDO representing exactly one Goal.

### 3.2.10 CBK-bearing FAIR Digital Object (CBKB-FDO)

A CBK-bearing FAIR Digital Object is an FDO representing exactly one CBK Artifact.

### 3.2.11 Layer

A Layer is a conceptual construct representing the active collection of GB-FDOs and CBKB-FDOs available for a specific Alignment Run.

Layer membership is composed of Goal-bearing FAIR Digital Objects (GB-FDOs) and CBK-bearing FAIR Digital Objects (CBKB-FDOs) as defined in Section 3.3.

### 3.2.12 Layer Image

A Layer Image is a representation of an established Layer.

Additional Layer Image requirements are specified in:

- Section 4.5 Output Package Specification
- Section 5.4 Provenance Specification
- Section 6.4 Saved Run Package Specification

### 3.2.13 Input Package

An Input Package is the execution-time metadata-only representation of the Layer Image associated with an established Layer presented to an Alignment Engine.

### 3.2.13A Alignment

Alignment is a relationship identified by an Alignment Engine between a Goal Representation and one or more CBKB-FDOs.

### 3.2.14 Alignment Engine

An Alignment Engine is a computational component that consumes an Input Package and produces an Output Package.

### 3.2.15 Alignment Engine Profile

An Alignment Engine Profile is metadata describing an Alignment Engine.

### 3.2.16 Alignment Run

An Alignment Run is a single execution of one Alignment Engine against one Layer.

### 3.2.17 Output Package

An Output Package is the complete output produced by one Alignment Engine for one Alignment Run.

### 3.2.18 Alignment Result Graph

An Alignment Result Graph is the authoritative scientific result object produced by an Alignment Run.

### 3.2.19 Constructed Realization

A Constructed Realization is an Alignment Engine-produced representation of a claimed alignment realization involving one or more CBKB-FDOs and a Goal Representation.

### 3.2.20 Saved Run Package

A Saved Run Package is a package that may be generated from a completed Alignment Run and saved by the user.

## 3.3 FAIR Digital Object Specifications

### 3.3.1 Purpose

This section defines the FAIR Digital Object structures recognized by GARI v1.0.

### 3.3.2 Minimal FDO Specification

Every FAIR Digital Object recognized by GARI SHALL contain:

1. PID
2. Type
3. Profile Reference
4. Metadata
5. Bitstream

### 3.3.3 PID

A persistent identifier uniquely identifying the FAIR Digital Object.

### 3.3.4 Type

A declared type identifying the FAIR Digital Object category.

### 3.3.5 Profile Reference

A reference to the profile governing interpretation of the FAIR Digital Object.

### 3.3.6 Metadata

Structured information describing the FAIR Digital Object.

### 3.3.7 Bitstream

A bitstream is the bytes of information comprising the payload bitstream of an FDO.

### 3.3.8 Goal-Bearing FDO Profile

One GB-FDO SHALL represent exactly one Goal.

### 3.3.9 Goal Interpretation Rule

All Goal Representations contained within a GB-FDO SHALL be interpreted as alternative representations of the same Goal.

### 3.3.10 CBK-Bearing FDO Profile

One CBKB-FDO SHALL represent exactly one CBK Artifact.

### 3.3.11 Knowledge Application Method Structure

Each Knowledge Application Method MAY contain input and output item structures.

### 3.3.12 Item Association Rule

Items SHALL belong to Knowledge Application Methods.

### 3.3.13 Payload Usage

Payload bitstreams SHALL NOT be included in Input Packages.

### 3.3.14 Extensibility

Future FDO profiles MAY be introduced.

## 3.4 Layer Specification

### 3.4.1 Purpose

This section defines the Layer concept used by GARI v1.0.

### 3.4.2 Definition

A Layer is a conceptual construct representing the active collection of GB-FDOs and CBKB-FDOs available for a specific Alignment Run.

### 3.4.3 Layer Characteristics

Layers are conceptual constructs and do not possess independent persistent identity.

### 3.4.4 Minimum Valid Layer

A valid Layer SHALL contain one or more GB-FDOs and one or more CBKB-FDOs.

### 3.4.5 Layer Assembly

Layers MAY be assembled through one or more user actions.

### 3.4.6 Layer Establishment

A Layer SHALL be considered established when at least one GB-FDO and one CBKB-FDO are present.

### 3.4.7 Fixed Layer Rule

Layer membership SHALL remain fixed during execution of an Alignment Run.

### 3.4.8 Layer Dynamics

Layer dynamics occur before Alignment Run execution.

### 3.4.9 Layer Persistence

Layers SHALL NOT possess independent persistent identity.

### 3.4.10 Relationship to Input Packages

Input Packages SHALL be generated from the Layer Image associated with an established Layer.

Each Input Package SHALL be associated with exactly one Layer Image.

### 3.4.11 Relationship to Alignment Engines

An Alignment Run requires both an established Layer and an Alignment Engine.

### 3.4.12 Relationship to Alignment Runs

Each Alignment Run SHALL operate against exactly one Layer.

## 3.5 Chapter Summary

This chapter establishes the conceptual constructs and structural entities recognized by GARI v1.0.

These concepts provide the foundation for the runtime architecture defined in Chapter 4.

Subsequent chapters rely upon the concepts defined here and SHALL interpret them consistently with the definitions provided in this chapter.


# Chapter 4: Runtime Architecture

## 4.1 Overview

Chapter 4 defines the runtime architecture of GARI v1.0.

Specifically, this chapter defines:

* Input Packages
* Alignment Engines
* Output Packages

Together these specifications define how Alignment Runs are conducted.

The overall runtime flow is:

Layer

→ Input Package

→ Alignment Engine

→ Output Package

The runtime architecture adopts a metadata-driven approach and treats Alignment Engines as black-box computational components.

## 4.2 Runtime Architecture Overview

### 4.2.1 Purpose

This section defines the runtime architecture of GARI v1.0.

### 4.2.2 Architectural Scope

The runtime architecture governs Alignment Run execution.

### 4.2.3 Runtime Participants

#### 4.2.3.1 Layer

A Layer provides the conceptual collection of GB-FDOs and CBKB-FDOs available for an Alignment Run.

#### 4.2.3.2 Input Package

The Input Package represents the execution-time metadata representation of a Layer.

#### 4.2.3.3 Alignment Engine

The Alignment Engine performs alignment processing.

#### 4.2.3.4 Output Package

The Output Package records Alignment Run outputs.

### 4.2.4 Runtime Information Flow

Information flows from Layer to Input Package, from Input Package to Alignment Engine, and from Alignment Engine to Output Package.

### 4.2.5 Runtime Constraints

Runtime execution SHALL conform to the principles established in Chapter 2.

### 4.2.6 One Engine per Run Rule

Each Alignment Run SHALL use exactly one Alignment Engine.

### 4.2.7 Fixed Layer Rule

Layer membership SHALL remain fixed during execution.

### 4.2.8 Metadata-Driven Runtime Rule

Alignment Engines SHALL operate on metadata supplied through Input Packages.

## 4.3 Input Package Specification

### 4.3.1 Purpose

This section defines Input Packages.

### 4.3.2 Definition

An Input Package is the execution-time metadata-only representation of the Layer Image associated with an established Layer.

### 4.3.3 Relationship to Layers

Input Packages SHALL be generated from the Layer Image associated with an established Layer.

Each Input Package SHALL be associated with exactly one Layer Image.

A Layer Image SHALL NOT introduce metadata used for alignment that is not derived from the established Layer.

### 4.3.4 Relationship to Alignment Runs

Each Alignment Run SHALL consume exactly one Input Package.

### 4.3.5 Input Package Structure

Input Packages contain run metadata and references required for Alignment Engine execution.

### 4.3.6 Required Elements

#### 4.3.6.1 Run Identifier

A unique identifier for the Alignment Run.

#### 4.3.6.2 Layer References

References to GB-FDOs and CBKB-FDOs participating in the Layer.

#### 4.3.6.3 Engine References

References to the Alignment Engine selected for execution.

#### 4.3.6.4 Run Metadata

Metadata associated with runtime execution.

### 4.3.7 Payload Exclusion Rule

Payload bitstreams SHALL NOT be included within Input Packages.

### 4.3.8 Input Package Generation

Input Packages SHALL be generated after Layer establishment and before Alignment Engine execution.

### 4.3.9 Input Package Lifecycle

Input Packages exist only for the purpose of Alignment Run execution.

## 4.4 Alignment Engine Specification

### 4.4.1 Purpose

This section defines Alignment Engines.

### 4.4.2 Definition

An Alignment Engine is a computational component that consumes an Input Package and produces an Output Package.

### 4.4.3 Alignment Engine Responsibilities

Alignment Engines evaluate potential alignment relationships between Goal Representations and CBKB-FDOs.

### 4.4.4 Alignment Engine Boundaries

Internal engine implementation remains outside the scope of GARI.

### 4.4.5 Black-Box Engine Rule

Alignment Engines SHALL be treated as black-box computational components.

### 4.4.6 Engine Profile Requirements

Alignment Engines SHALL provide an Alignment Engine Profile.

### 4.4.7 Supported Input Types

Alignment Engines SHALL declare supported input types through their profiles.

### 4.4.8 Engine Configuration Metadata

Engine configuration metadata SHALL be recorded within Output Packages.

### 4.4.9 Engine Execution

Alignment Engines execute against one Input Package during one Alignment Run.

### 4.4.10 Engine Outputs

Alignment Engines SHALL produce one Output Package.

### 4.4.11 Engine Notes

Alignment Engines MAY produce Engine Notes.

### 4.4.12 Negative Results

Negative alignment results SHALL be treated as valid scientific results.

### 4.4.13 Alignment Engine Independence

Alignment Engines remain independent of the GARI runtime architecture.

## 4.5 Output Package Specification

### 4.5.1 Purpose

This section defines Output Packages.

### 4.5.2 Definition

An Output Package is the complete runtime output produced by an Alignment Engine.

### 4.5.3 Relationship to Alignment Runs

Each completed Alignment Run SHALL produce exactly one Output Package.

### 4.5.4 Relationship to Alignment Engines

Output Packages are produced by Alignment Engines.

### 4.5.5 Output Package Structure

Output Packages contain required and optional runtime artifacts.

### 4.5.6 Required Elements

#### 4.5.6.1 Alignment Result Graph

The authoritative scientific result object.

#### 4.5.6.2 Layer Image

A representation of the Layer used during execution.

#### 4.5.6.3 Provenance Metadata

Provenance associated with the Alignment Run.

#### 4.5.6.4 Engine Configuration Metadata

Metadata describing the engine configuration used during execution.

### 4.5.7 Optional Elements

#### 4.5.7.1 Engine Notes

Optional explanatory information produced by the Alignment Engine.

#### 4.5.7.2 Additional Supporting Artifacts

Optional supporting artifacts.

### 4.5.8 Authoritative Result Rule

The Alignment Result Graph SHALL be the authoritative scientific result object.

### 4.5.9 Output Package Lifecycle

Output Packages persist after Alignment Run completion and may be incorporated into Saved Run Packages.

## 4.6 Runtime Lifecycle Summary

### 4.6.1 Layer Establishment

A Layer is established through assembly of GB-FDOs and CBKB-FDOs.

### 4.6.2 Input Package Creation

An Input Package is generated from the established Layer.

### 4.6.3 Alignment Engine Execution

The Alignment Engine consumes the Input Package and performs alignment processing.

### 4.6.4 Output Package Creation

Execution produces an Output Package.

### 4.6.5 Runtime Completion

The Alignment Run concludes upon successful Output Package creation.

## 4.7 Chapter Summary

This chapter defines the runtime architecture of GARI v1.0.

The chapter establishes how Alignment Runs are conducted and how runtime artifacts are produced.

The resulting runtime outputs provide the foundation for the result, provenance, and state specifications defined in Chapter 5.


# Chapter 5: Results and Provenance

## 5.1 Overview

Chapter 5 defines the result structures, provenance structures, and state structures produced by GARI v1.0.

Specifically, this chapter defines:

* Alignment Result Graphs
* Provenance Metadata
* Runtime State Models

Together these specifications define how Alignment Run outcomes are represented, interpreted, and managed.

The result architecture is centered on the Alignment Result Graph, which serves as the authoritative scientific result object produced by an Alignment Run.

## 5.2 Results Architecture Overview

### 5.2.1 Purpose

This section defines the result architecture of GARI v1.0.

### 5.2.2 Architectural Scope

The result architecture governs representation of Alignment Run outcomes.

### 5.2.3 Result Artifacts

#### 5.2.3.1 Alignment Result Graph

The authoritative scientific result object.

#### 5.2.3.2 Layer Image

A representation of the established Layer used during execution.

#### 5.2.3.3 Provenance Metadata

Information describing the origin and context of runtime artifacts.

#### 5.2.3.4 Engine Notes

Optional explanatory information supplied by an Alignment Engine.

### 5.2.4 Result Information Flow

Results originate from Alignment Runs and are represented within Output Packages.

### 5.2.5 Result Authority Rule

The Alignment Result Graph SHALL be the authoritative scientific result object.

### 5.2.6 Relationship to Output Packages

Output Packages contain Alignment Result Graphs and related result artifacts.

### 5.2.7 Relationship to Saved Run Packages

Saved Run Packages preserve result artifacts for future inspection and reproducibility.

## 5.3 Alignment Result Graph Specification

### 5.3.1 Purpose

This section defines Alignment Result Graphs.

### 5.3.2 Definition

An Alignment Result Graph is the authoritative scientific result object produced by an Alignment Run.

### 5.3.3 Authority

No supporting artifact supersedes Alignment Result Graph contents.

### 5.3.4 Relationship to Alignment Runs

Each Alignment Run SHALL produce exactly one Alignment Result Graph.

### 5.3.5 Relationship to Output Packages

Each Output Package SHALL contain exactly one Alignment Result Graph.

### 5.3.6 Graph Structure

Alignment Result Graphs represent alignment outcomes generated by an Alignment Engine.

### 5.3.7 Required Elements

#### 5.3.7.1 Goal Identifier

Identifier of the Goal being evaluated.

#### 5.3.7.2 Alignment Status

The engine-produced alignment outcome.

#### 5.3.7.3 CBK References

References to participating CBKB-FDOs.

#### 5.3.7.4 Constructed Realizations

Engine-produced Constructed Realizations.

### 5.3.8 Optional Elements

#### 5.3.8.1 Engine Notes References

Optional references to Engine Notes.

#### 5.3.8.2 Additional Result Metadata

Additional metadata supporting interpretation.

### 5.3.9 Negative Result Representation

Negative alignment outcomes SHALL be represented as valid scientific results.

### 5.3.10 Interpretation Constraints

Interpretation SHALL be based upon Alignment Result Graph contents.

## 5.4 Provenance Specification

### 5.4.1 Purpose

This section defines provenance requirements.

### 5.4.2 Provenance Scope

Provenance records relationships among Alignment Runs, Output Packages, and generated artifacts.

### 5.4.3 Provenance Principles

Provenance SHALL support inspection, comparison, interpretation, and reproducibility.

### 5.4.4 Alignment Run Provenance

#### 5.4.4.1 Run Identifier

Unique identifier of an Alignment Run.

#### 5.4.4.2 Execution Timestamp

Timestamp of Alignment Run execution.

#### 5.4.4.3 Alignment Engine Version

Version identifier of the Alignment Engine used.

### 5.4.5 Output Package Provenance

Provenance associated with Output Package creation.

### 5.4.6 Alignment Result Graph Provenance

Provenance associated with Alignment Result Graph generation.

### 5.4.7 Layer Image Provenance

Provenance associated with Layer Image representation.

### 5.4.8 Provenance Preservation Requirements

Provenance SHALL be preserved in a manner sufficient to support reproducibility objectives.

### 5.4.9 Provenance Minimalism

GARI adopts a minimal provenance model sufficient to support scientific interpretation and reproducibility.

## 5.5 State Model Specification

### 5.5.1 Purpose

This section defines the runtime state model of GARI.

### 5.5.2 Scope

The state model governs user-visible transitions among major runtime states.

### 5.5.3 State Model Overview

The state model supports Alignment Run execution and result management.

### 5.5.4 Landed State

The initial state of the instrument.

### 5.5.5 Layer Established State

The state in which a valid Layer has been established.

### 5.5.6 Run Complete State

The state reached after successful Alignment Run completion.

A Run enters the Run Complete State when the Output Package has been produced.

Save Run SHALL only be available when an Output Package exists for the current Alignment Run.

Clear Result SHALL only be available when an Output Package exists for the current Alignment Run.

A new Alignment Run MAY be initiated after completion of a previous Alignment Run.

### 5.5.7 Saved State

The state reached after successful Save Run completion.

### 5.5.8 Clear Result State Transition

The transition used to remove active result artifacts from the runtime environment.

### 5.5.9 Unsaved Result Protection

Users SHALL be protected from accidental loss of unsaved results.

Implementations SHOULD provide a warning before clearing unsaved Alignment Run results.

### 5.5.10 State Constraints

State transitions SHALL conform to the state model specification.

## 5.6 Results Lifecycle Summary

### 5.6.1 Alignment Run Completion

Completion of an Alignment Run produces an Output Package.

### 5.6.2 Output Package Availability

Output Packages become available for inspection after successful completion.

### 5.6.3 Result Inspection

Users may inspect Alignment Run results.

### 5.6.4 Save Run Decision

Users may elect to save results.

### 5.6.5 Result Clearing

Users may clear active results after inspection or saving.

### 5.6.6 Lifecycle Completion

The results lifecycle concludes when active result artifacts are cleared.

## 5.7 Chapter Summary

This chapter defines the result architecture, provenance architecture, and state architecture of GARI v1.0.

The chapter establishes how Alignment Run outcomes are represented, traced, managed, and preserved.

These structures provide the foundation for the user interaction and persistence specifications defined in Chapter 6.


# Chapter 6: User Interaction, Persistence, and Future Boundaries

## 6.1 Overview

Chapter 6 defines the user interaction architecture, persistence architecture, and future architectural boundaries of GARI v1.0.

Specifically, this chapter defines:

* User Interface requirements
* Saved Run Packages
* Future Concepts Log

Together these specifications define how users interact with GARI, how Alignment Run outputs may be preserved, and which topics remain outside the scope of the current specification.

This chapter builds upon the concepts defined in Chapter 3, the runtime architecture defined in Chapter 4, and the result architecture defined in Chapter 5.

## 6.2 User Interface Specification

### 6.2.1 Purpose

This section defines user interface requirements for GARI v1.0.

### 6.2.2 User Interface Philosophy

The user interface SHALL present GARI as a scientific instrument.

### 6.2.3 Scientific Instrument Presentation

The user interface SHALL emphasize inspection, evaluation, and reproducibility.

### 6.2.4 Concept-Revealing Interface Requirements

User interface elements SHALL expose GARI concepts directly.

### 6.2.5 Simplicity and Restraint Requirements

The user interface SHALL emphasize clarity, simplicity, and restraint.

### 6.2.6 Major User Interface Elements

#### 6.2.6.1 Layer Management

Facilities for loading and establishing Layers.

#### 6.2.6.2 Alignment Engine Management

Facilities for selecting Alignment Engines.

Loading a new Alignment Engine SHALL replace any previously loaded Alignment Engine.

#### 6.2.6.3 Alignment Run Controls

Facilities for initiating Alignment Runs.

#### 6.2.6.4 Result Inspection

Facilities for viewing Alignment Run outputs.

#### 6.2.6.5 Save Run Controls

Facilities for creating Saved Run Packages.

### 6.2.7 User Interface States

#### 6.2.7.1 Landed State

Initial application state.

#### 6.2.7.2 Layer Established State

Layer has been successfully established.

#### 6.2.7.3 Run Complete State

An Alignment Run has completed successfully.

#### 6.2.7.4 Saved State

A Saved Run Package has been created.

### 6.2.8 Unsaved Result Protection

Users SHALL be protected from accidental loss of unsaved results.

### 6.2.9 Clear Result Behavior

Clear Result SHALL remove active result artifacts from the runtime environment.

### 6.2.10 User Interface Constraints

User interface behavior SHALL conform to the GARI state model.

## 6.3 Persistence Architecture Overview

### 6.3.1 Purpose

This section defines persistence architecture concepts.

### 6.3.2 Persistence Scope

Persistence governs preservation of Alignment Run outputs.

### 6.3.3 User-Controlled Persistence Principle

Persistence SHALL occur only through explicit user action.

### 6.3.4 Relationship to Output Packages

Saved Run Packages are derived from Output Packages.

### 6.3.5 Relationship to Reproducibility

Persistence supports reproducibility objectives.

### 6.3.6 Persistence Information Flow

Output Package

→

Saved Run Package

## 6.4 Saved Run Package Specification

### 6.4.1 Purpose

This section defines Saved Run Packages.

### 6.4.2 Definition

A Saved Run Package is a preservation-oriented package derived from a completed Alignment Run.

### 6.4.3 Relationship to Alignment Runs

Saved Run Packages originate from completed Alignment Runs.

### 6.4.4 Relationship to Output Packages

Saved Run Packages preserve Output Package information.

### 6.4.5 Relationship to Reproducibility

The reproducibility objective of a Saved Run Package SHALL be reproduction of the Alignment Run that produced the preserved Alignment Result Graph.

Saved Run Packages support reproducibility and inspection.

A Saved Run Package SHALL contain the Reproducibility Information required to reconstruct the Alignment Run represented by the package.

Reproducibility is supported through preservation of Alignment Run outputs together with associated provenance and reproducibility information.

Provenance requirements supporting reproducibility are specified in Section 5.4 Provenance Specification.

### 6.4.6 Saved Run Package Structure

Saved Run Packages contain required and optional preservation artifacts.

### 6.4.7 Required Elements

#### 6.4.7.1 Alignment Result Graph

#### 6.4.7.2 Layer Image

#### 6.4.7.3 Provenance Metadata

#### 6.4.7.4 Reproducibility Information

#### 6.4.7.5 Saved Run Metadata

### 6.4.8 Optional Elements

#### 6.4.8.1 Augmented Information

#### 6.4.8.2 Additional Supporting Artifacts

### 6.4.9 Saved Run Package Augmentation Rule

Saved Run Packages MAY augment preserved information without modifying Output Packages.

### 6.4.10 Preservation by Reference

FDOs SHALL be preserved by reference rather than by payload duplication.

The Layer Image preserved within a Saved Run Package SHALL be identical to the Layer Image contained within the corresponding Output Package.

Each Saved Run Package SHALL be derived from exactly one Output Package.

### 6.4.11 Saved Run Package Lifecycle

Saved Run Packages are created after successful Save Run invocation.

## 6.5 Preservation Lifecycle Summary

### 6.5.1 Alignment Run Completion

An Alignment Run completes successfully.

### 6.5.2 Output Package Availability

The Output Package becomes available for inspection.

### 6.5.3 Save Run Invocation

The user elects to create a Saved Run Package.

### 6.5.4 Saved Run Package Creation

A Saved Run Package is generated.

### 6.5.5 Preservation Completion

The preservation lifecycle concludes after package creation.

## 6.6 Future Concepts Log

### 6.6.1 Purpose

This section records future concepts that are intentionally outside the scope of GARI v1.0.

### 6.6.2 Informative Status

This section is informative and non-normative.

### 6.6.3 Candidate Future Topics

#### 6.6.3.1 Multi-Engine Architectures

#### 6.6.3.2 Alternative Provenance Models

#### 6.6.3.3 Alternative Preservation Models

#### 6.6.3.4 Additional FDO Profiles

#### 6.6.3.5 Additional Alignment Models

### 6.6.4 Non-Normative Status

Nothing in this section introduces requirements for GARI v1.0.

## 6.7 Chapter Summary

This chapter defines how users interact with GARI, how Alignment Run outputs may be preserved, and which topics remain outside the scope of GARI v1.0.

Together with the preceding chapters, this chapter completes the normative specification of GARI v1.0.


# Appendix A — Glossary

## Document Status

Version: GARI v1.0

Status: Publication Candidate

Normative: No

---

# Purpose

This appendix provides a consolidated glossary of terminology used throughout the GARI v1.0 Specification Package.

The glossary is descriptive rather than normative.

Authoritative definitions remain in Chapters 2–6. Where conflicts arise, Chapters 2–6 take precedence.

---

# Audit A — Terminology and Consistency Review

Result: Pass

Observations:

1. "Alignment Engine Profile" and "Engine Profile" are used interchangeably in the specification. The glossary standardizes on **Alignment Engine Profile** while noting that "Engine Profile" is a shortened form.
2. "Preservation Provenance" is retained as the Saved Run Package term and remains distinct from Alignment Run provenance.
3. "Layer Image" is consistently treated as a representational artifact rather than a conceptual construct.
4. "Saved Run Package Augmentation" is preserved as the approved augmentation concept from Chapter 6.
5. Concept–representation distinctions are maintained throughout.

---

# Audit B — Cross-Part Conformance Review

Result: Pass

Findings:

1. All conceptual entities align with Chapter 3 Core Concepts.
2. Runtime entities align with Chapter 4 Runtime Architecture specifications.
3. Result and provenance terminology aligns with Chapter 5.
4. Persistence terminology aligns with Chapter 6.
5. No glossary entry supersedes normative specification language.

---

# Glossary

## Active Result
**Category:** Operational Artifact

The Alignment Result currently present in the user interface following completion of an Alignment Run. An Active Result remains available until removed through Clear Result.

---

## Alignment Engine
**Category:** Operational Artifact

A computational component that consumes an Input Package and produces an Output Package.

---

## Alignment Engine Profile
**Category:** Representational Artifact

Metadata describing an Alignment Engine, including its identity, version, and implementation characteristics.

---

## Alignment Result Graph
**Category:** Representational Artifact

The authoritative scientific result object produced by an Alignment Run.

---

## Alignment Run
**Category:** Operational Artifact

A single execution of one Alignment Engine against one Layer.

---

## Bitstream
**Category:** Representational Artifact

The payload bytes of a FAIR Digital Object. Bitstreams are distinct from metadata and are excluded from Input Packages.

---

## CBK Artifact
**Category:** Representational Artifact

A representation of computable biomedical knowledge.

---

## CBKB-FDO
**Category:** Representational Artifact

A CBK-bearing FAIR Digital Object representing exactly one CBK Artifact.

---

## Clear Result
**Category:** User Interface Function

The user action that removes the Active Result from the interface without altering previously created Saved Run Packages.

---

## Computable Biomedical Knowledge (CBK)
**Category:** Conceptual Construct

An externally supplied knowledge concept intentionally left undefined by GARI.

---

## Constructed Realization
**Category:** Representational Artifact

An Alignment Engine-produced representation of how one or more CBKB-FDOs may support alignment with a Goal Representation.

---

## FAIR Digital Object (FDO)
**Category:** Representational Artifact

A digital object represented according to a declared FDO profile.

---

## GB-FDO
**Category:** Representational Artifact

A Goal-bearing FAIR Digital Object representing exactly one Goal.

---

## Goal
**Category:** Conceptual Construct

A conceptual construct representing a desire for a computation to be performed.

---

## Goal Representation
**Category:** Representational Artifact

A representation of a Goal.

---

## Input Package
**Category:** Representational Artifact

The execution-time metadata-only representation of an established Layer presented to an Alignment Engine.

---

## Item
**Category:** Conceptual Construct

A data object that may serve as an input to, or output from, a Knowledge Application Method.

---

## Knowledge Application Method (KAM)
**Category:** Conceptual Construct

A method by which a CBK Artifact may be computationally applied.

---

## Layer
**Category:** Conceptual Construct

The active collection of GB-FDOs and CBKB-FDOs available for a specific Alignment Run.

---

## Layer Establishment
**Category:** Operational Artifact

The condition in which at least one GB-FDO and at least one CBKB-FDO are present, creating a valid Layer.

---

## Layer Image
**Category:** Representational Artifact

A representation of an established Layer identifying the GB-FDOs and CBKB-FDOs that comprise it.

---

## Metadata
**Category:** Representational Artifact

Structured information describing a FAIR Digital Object or other specification artifact.

---

## Output Package
**Category:** Representational Artifact

The complete output produced by one Alignment Engine for one Alignment Run.

---

## Persistent Identifier (PID)
**Category:** Representational Artifact

A persistent identifier uniquely identifying a FAIR Digital Object.

---

## Preservation Provenance
**Category:** Representational Artifact

Metadata documenting creation of a Saved Run Package.

---

## Profile Reference
**Category:** Representational Artifact

A reference identifying the profile governing interpretation of a FAIR Digital Object.

---

## Provenance
**Category:** Representational Artifact

Metadata describing the circumstances under which Alignment Run results were produced or preserved.

---

## Reproducibility Information
**Category:** Representational Artifact

Information preserved within a Saved Run Package that supports later interpretation, inspection, comparison, and potential reconstruction of an Alignment Run.

---

## Run Metadata
**Category:** Representational Artifact

Metadata identifying an Alignment Run, including execution time and Alignment Engine identity.

---

## Save Run
**Category:** User Interface Function

The explicit user action that creates a Saved Run Package from a completed Alignment Run.

---

## Saved Run Metadata
**Category:** Representational Artifact

Metadata identifying a Saved Run Package and the circumstances of its creation.

---

## Saved Run Package
**Category:** Representational Artifact

A package generated from a completed Alignment Run and saved through explicit user action.

---

## Saved Run Package Augmentation
**Category:** Preservation Concept

Additional preservation-supporting information added to a Saved Run Package without modifying the preserved Output Package.

---

## State Model
**Category:** Operational Artifact

The specification defining runtime states and state transitions within GARI.



# Appendix B — Principles Traceability Matrix

## Document Status

Version: GARI v1.0

Status: Publication Candidate

Normative: No

---

# Purpose

This appendix documents how the principles defined in Chapter 2 are reflected throughout the remainder of the GARI v1.0 Specification Package.

The purpose of this appendix is to support:

* traceability
* architectural verification
* specification maintenance
* navigation

This appendix is descriptive rather than normative.

When conflicts arise, Chapters 2–6 take precedence.

---

# Tier 1 — Foundational Principles

## P1 Scientific Instrument Principle

### Statement

GARI is specified as a scientific instrument for Goal–CBK alignment experimentation.

### Reflected In

* Section 4.2 Runtime Architecture Overview
* Section 5.2 Results Architecture Overview
* Section 6.2 User Interface Specification
* Section 6.4 Saved Run Package Specification

### Notes

These sections consistently frame GARI as an instrument rather than a knowledge application platform.

---

## P2 Alignment-Only Principle

### Statement

GARI investigates alignment and does not perform knowledge application.

### Reflected In

* Section 3.2 Core Concepts
* Section 4.4.4 Alignment Engine Boundaries
* Section 4.4.13 Alignment Engine Independence
* Section 5.3 Alignment Result Graph Specification

---

## P3 Metadata-Driven Alignment Principle

### Statement

Alignment is based upon pre-existing metadata supplied through FAIR Digital Objects.

### Reflected In

* Section 4.2.8 Metadata-Driven Runtime Rule
* Section 4.3.2 Definition
* Section 4.3.7 Payload Exclusion Rule
* Section 4.4.2 Definition

---

## P4 No Metadata Generation Principle

### Statement

GARI does not generate, repair, enrich, or modify metadata.

### Reflected In

* Section 4.2.8 Metadata-Driven Runtime Rule
* Section 4.3.2 Definition
* Section 4.3.7 Payload Exclusion Rule
* Section 4.4.2 Definition

---

## P5 Concept–Representation Separation Principle

### Statement

Conceptual entities are distinct from the representations that describe them.

### Reflected In

* Chapter 3 — Core Concepts
* Chapter 3 — Layer Specification
* Chapter 4 — Input Package Specification
* Chapter 6 — Saved Run Package Specification

---

## P6 Payload–Metadata Separation Principle

### Statement

Metadata and payloads are distinct entities.

### Reflected In

* Chapter 3 — FAIR Digital Object Specifications
* Chapter 4 — Runtime Architecture Overview
* Chapter 4 — Input Package Specification
* Chapter 6 — Saved Run Package Specification

---

# Tier 2 — Architectural Principles

## P7 One Engine per Run Principle

### Reflected In

* Chapter 3 — Core Concepts
* Chapter 4 — Alignment Engine Specification
* Chapter 4 — Output Package Specification

---

## P8 Black-Box Engine Principle

### Reflected In

* Chapter 3 — Core Concepts
* Chapter 4 — Alignment Engine Specification

---

## P9 Fixed Layer During Execution Principle

### Reflected In

* Section 3.4.7 Fixed Layer Rule
* Section 4.2.7 Fixed Layer Rule
* Section 5.5 State Model Specification

---

## P10 Ephemeral-by-Default Principle

### Reflected In

* Chapter 5 — State Model Specification
* Chapter 6 — User Interface Specification
* Chapter 6 — Saved Run Package Specification

---

## P11 User-Controlled Persistence Principle

### Reflected In

* Chapter 3 — Core Concepts
* Chapter 6 — User Interface Specification
* Chapter 6 — Saved Run Package Specification

---

## P12 Unsaved Run Protection Principle

### Reflected In

* Chapter 5 — State Model Specification
* Chapter 6 — User Interface Specification

---

## P13 Negative Results Principle

### Reflected In

* Chapter 4 — Output Package Specification
* Chapter 5 — Alignment Result Graph Specification

---

## P14 Authoritative Result Graph Principle

### Reflected In

* Chapter 3 — Core Concepts
* Chapter 4 — Output Package Specification
* Chapter 5 — Alignment Result Graph Specification

---

## P15 Engine Notes Separation Principle

### Reflected In

* Chapter 4 — Alignment Engine Specification
* Chapter 4 — Output Package Specification
* Chapter 5 — Alignment Result Graph Specification

---

## P16 Saved Run Package Augmentation Principle

### Reflected In

* Chapter 6 — Saved Run Package Specification

---

## P17 Provenance Preservation Principle

### Reflected In

* Chapter 5 — Provenance Specification
* Chapter 6 — Saved Run Package Specification

---

## P18 Layer Non-Persistence Principle

### Reflected In

* Chapter 3 — Core Concepts
* Chapter 3 — Layer Specification
* Chapter 6 — Saved Run Package Specification

---

# Tier 3 — User Experience Principles

## P19 Concept-Revealing UI Principle

### Reflected In

* Chapter 6 — User Interface Specification

---

## P20 Scientific Instrument UI Principle

### Reflected In

* Chapter 6 — User Interface Specification

---

## P21 Simplicity and Restraint Principle

### Reflected In

* Chapter 6 — User Interface Specification

---

# Traceability Matrix Summary

Tier 1 principles establish identity.

Tier 2 principles establish architecture.

Tier 3 principles establish presentation.

The specifications contained in Chapters 3–6 collectively reflect the principles established in Chapter 2.


# Appendix C — Conceptual Constructs and Artifact Model

## Document Status

Version: GARI v1.0

Status: Publication Candidate

Normative: No

---

# Purpose

This appendix provides a consolidated overview of the principal conceptual constructs and artifacts recognized within GARI v1.0.

The appendix is intended to:

* clarify the conceptual structure of GARI
* distinguish concepts from their representations
* distinguish concepts from operational artifacts
* aid navigation of the specification

This appendix summarizes concepts and relationships defined elsewhere in the specification.

This appendix does not introduce:

* new concepts
* new artifacts
* new relationships
* new cardinalities
* new architectural requirements

In the event of a conflict between this appendix and a normative specification section, the normative specification section SHALL take precedence.

---

# Overview

GARI recognizes several categories of entities that participate in Alignment Runs and related activities.

For explanatory purposes, these entities are grouped into:

* Abstract Conceptual Constructs
* Operational Artifacts
* Representational Artifacts

These categories are descriptive rather than prescriptive.

They are intended to aid understanding of the specification and do not impose a rigid architectural hierarchy.

Some entities may participate in more than one conceptual role depending on the context in which they are discussed.

Relationships among these categories are defined throughout Chapters 2–6 of the specification.

---

# Abstract Conceptual Constructs

Abstract Conceptual Constructs are conceptual entities recognized by the specification.

They are not operational artifacts.

They are not representations.

Examples include the following.

## Goal

A Goal represents a desired future state whose achievement is being evaluated or pursued.

Goals are conceptual entities independent of any particular representation.

## CBK

A Computable Biomedical Knowledge (CBK) entity represents computable knowledge that may participate in alignment activities.

CBKs are conceptual entities independent of any particular artifact or representation.

## Layer

A Layer is a conceptual aggregation of Goal-bearing and CBK-bearing FDOs established for an Alignment Run.

A Layer is a conceptual construct and is distinct from any representation of that Layer.

---

# Operational Artifacts

Operational Artifacts are entities that participate directly in execution, processing, result generation, persistence, or user interaction.

Examples include the following.

## Goal-Bearing FAIR Digital Object (GB-FDO)

A GB-FDO is an operational artifact that realizes a Goal within the GARI environment.

## CBK-Bearing FAIR Digital Object (CBKB-FDO)

A CBKB-FDO is an operational artifact that realizes a CBK within the GARI environment.

## Input Package

An Input Package is an operational artifact used to provide run inputs to an Alignment Engine.

## Alignment Engine

An Alignment Engine is an operational artifact that performs alignment processing.

## Output Package

An Output Package is an operational artifact produced by a completed Alignment Run.

## Alignment Result Graph

An Alignment Result Graph is an operational artifact that records alignment results produced during a run.

## Saved Run Package

A Saved Run Package is a package that may be generated from a completed Alignment Run and may be saved by the user.

---

# Representational Artifacts

Representational Artifacts represent other entities recognized by the specification.

They are distinct from the entities they represent.

Examples include the following.

## Goal Representation

A Goal Representation represents a Goal.

A Goal Representation is not itself a Goal.

## CBK Artifact

A CBK Artifact represents a CBK.

A CBK Artifact is not itself a CBK.

## Layer Image

A Layer Image represents a Layer.

A Layer Image is not a Layer.

---

# Realization Relationships

The specification defines relationships through which conceptual constructs are realized in operational artifacts.

Examples include the following.

| Conceptual Construct | Operational Realization |
|----------|----------|
| Goal | Goal-Bearing FAIR Digital Object (GB-FDO) |
| CBK | CBK-Bearing FAIR Digital Object (CBKB-FDO) |
| Layer | Established Layer used during an Alignment Run |

These examples are illustrative summaries of relationships defined elsewhere in the specification.

---

# Representation Relationships

The specification also defines relationships through which conceptual constructs are represented by representational artifacts.

Examples include the following.

| Conceptual Construct | Representation |
|----------|----------|
| Goal | Goal Representation |
| CBK | CBK Artifact |
| Layer | Layer Image |

Representation relationships are distinct from realization relationships.

A representation is not the entity being represented.

---

# Appendix Notes

This appendix is intended to support understanding of the conceptual structure of GARI.

The categories and examples presented here are explanatory aids and should not be interpreted as introducing additional architectural constraints.

Authoritative definitions remain in Chapters 2–6 of the specification.

Future revisions of GARI may expand or refine explanatory material in this appendix while preserving consistency with the normative specification.


# Appendix D — Information Flow and Provenance Model

## Document Status

Version: GARI v1.0

Status: Publication Candidate

Normative: No

---

# Purpose

This appendix provides a consolidated overview of information flow and provenance relationships within GARI v1.0.

The appendix summarizes how information moves through the architecture and how provenance relationships are associated with resulting artifacts.

This appendix does not introduce new provenance requirements, new architectural elements, new runtime behavior, or new artifacts.

In the event of a conflict between this appendix and Chapters 2–6 of the specification, Chapters 2–6 SHALL take precedence.

---

# Scope

This appendix describes:

* information flow
* artifact production
* provenance relationships
* Saved Run Package preservation relationships

within GARI.

This appendix is descriptive.

Normative provenance requirements are defined in:

* Chapter 5 — Results and Provenance
* Section 5.4 Provenance Specification

---

# Information Flow Overview

Information within GARI flows through a sequence of established artifacts and generated artifacts.

The overall information flow is:

Established Layer

↓

Input Package

↓

Alignment Engine

↓

Output Package

├── Alignment Result Graph

├── Layer Image

├── Provenance Metadata

└── Optional Engine Notes

↓

Saved Run Package

The Output Package is the primary source of generated information products.

The Saved Run Package preserves selected Output Package content together with associated reproducibility information.

---

# Layer Establishment

A Layer is established prior to Alignment Run execution.

A Layer contains:

* one or more Goal-bearing FDOs
* one or more CBK-bearing FDOs

The Layer serves as the informational basis for Alignment Run execution.

The Layer itself is not generated by the Alignment Engine.

The Layer exists independently of Alignment Run execution.

---

# Input Package Information Flow

The Input Package represents the operational representation of an established Layer for a particular Alignment Run.

The Input Package provides the information supplied to the Alignment Engine.

The Input Package may contain:

* references to Layer contents
* run identifiers
* engine references
* execution metadata

The Input Package does not create new Goal-bearing FDOs or CBK-bearing FDOs.

Instead, it provides a run-specific representation of the established Layer.

---

# Alignment Engine Information Flow

The Alignment Engine consumes information represented within the Input Package.

During execution, the Alignment Engine evaluates relationships between:

* Goal Representations
* CBK-bearing FDOs

The Alignment Engine produces Alignment Run outputs according to its internal implementation.

The internal operation of the Alignment Engine remains outside the scope of GARI.

Only the resulting outputs are represented within GARI artifacts.

---

# Output Package Information Flow

The Output Package captures the informational products generated by a completed Alignment Run.

The Output Package may contain:

* Alignment Result Graph
* Layer Image
* provenance metadata
* Engine Configuration Metadata
* optional engine notes
* run metadata

The Output Package serves as the authoritative representation of Alignment Run results.

## Alignment Result Graph

The Alignment Result Graph represents Alignment Run outcomes.

The graph records information generated by Alignment Engine execution.

The graph serves as the principal structured representation of Alignment Run results.

## Layer Image

The Layer Image represents the established Layer used during Alignment Run execution.

The Layer Image provides a preserved representation of the Layer context associated with the Output Package.

The Layer Image is treated as an information product contained within the Output Package.

The Layer Image does not represent a newly created Layer.

Instead, it represents the established Layer used during execution.

---

# Saved Run Package Information Flow

A Saved Run Package may be generated from a completed Alignment Run and may be saved by the user.

The Saved Run Package provides a preservation-oriented representation of Alignment Run outputs together with associated reproducibility information.

The Saved Run Package may contain:

* Alignment Result Graph
* Layer Image
* provenance metadata
* reproducibility information
* output metadata
* Saved Run Metadata

The Saved Run Package is derived from completed Alignment Run outputs.

## Layer Image Preservation

The Layer Image contained within the Saved Run Package is the same Layer Image contained within the Output Package.

Output Package Layer Image

=

Saved Run Package Layer Image

Creation of a Saved Run Package does not generate a new Layer Image.

Instead, the existing Layer Image is preserved.

The relationship may be summarized as:

Layer

↓

represented by

Layer Image

↓

contained within

Output Package

↓

preserved within

Saved Run Package

---

# Provenance Overview

Provenance information records relationships among:

* Alignment Runs
* generated outputs
* generated artifacts
* preserved artifacts

This appendix describes provenance relationships only.

Normative provenance requirements are defined elsewhere in the specification.

---

# Alignment Run Provenance

Alignment Run provenance associates generated outputs with a particular Alignment Run.

Examples include relationships among:

* Alignment Run identifiers
* execution timestamps
* Alignment Engine versions
* generated outputs

Alignment Run provenance provides traceability between execution activity and generated artifacts.

---

# Output Package Provenance

Output Package provenance records provenance relationships associated with Output Package contents.

These relationships may associate:

* Alignment Result Graphs
* Layer Images
* engine-generated outputs
* execution metadata

with the Alignment Run that produced them.

The Layer Image does not require a separate provenance model.

Its provenance is represented through Output Package provenance relationships and associated provenance metadata.

---

# Saved Run Package Provenance

Saved Run Package provenance records provenance relationships associated with preservation of Alignment Run outputs.

These relationships may associate:

* Saved Run Packages
* preserved Output Package contents
* reproducibility information
* package creation metadata

with the originating Alignment Run.

Saved Run Package provenance supports understanding how preserved artifacts relate to previously generated Alignment Run outputs.

---

# Provenance Relationship Summary

The primary provenance relationships may be summarized as:

Established Layer

↓

represented by

Layer Image

↓

associated with

Alignment Run

↓

produces

Output Package

↓

contains

Alignment Result Graph

Layer Image

Provenance Metadata

↓

may be preserved within

Saved Run Package

The Saved Run Package maintains relationships back to the originating Alignment Run through associated provenance metadata.

---

# Appendix Notes

This appendix is intended as an architectural reference.

It summarizes information movement and provenance relationships across the GARI architecture.

This appendix does not define normative provenance requirements.

Normative provenance requirements are defined in:

* Chapter 5 — Results and Provenance
* Section 5.4 Provenance Specification

If any inconsistency exists between this appendix and the normative specification, the normative specification SHALL take precedence.


# Appendix E — Specification Provenance and Contributions

## Document Status

Version: GARI v1.0

Status: Publication Candidate

Normative: No

---

# Purpose

This appendix documents the provenance of the GARI v1.0 specification and records major architectural decisions, specification evolution, stabilization activities, and contributions that materially influenced the final specification.

This appendix is informative.

This appendix does not introduce new requirements, new principles, new concepts, new artifacts, or new architectural elements.

If a conflict exists between this appendix and Chapters 2–6 of the specification, Chapters 2–6 SHALL take precedence.

---

# Scope

This appendix documents specification provenance.

This appendix does not define runtime provenance requirements.

Normative provenance requirements are defined in Section 5.4 Provenance Specification.

The purpose of this appendix is to explain how the specification evolved and how major architectural decisions became stabilized throughout specification development.

---

# Major Architectural Decisions

The following decisions materially influenced the final GARI v1.0 architecture.

## Alignment-Only Scope

GARI investigates alignment.

GARI does not perform knowledge application.

Knowledge application remains outside the scope of GARI.

This separation establishes GARI as a scientific instrument for alignment investigation rather than a system for operational knowledge execution.

---

## Metadata-Driven Alignment

Alignment Engines operate on metadata supplied through Input Packages.

GARI does not generate metadata.

GARI does not repair metadata.

GARI does not enrich metadata.

GARI does not modify metadata.

This decision preserves separation between metadata production and alignment evaluation.

---

## Layer as Conceptual Construct

Layers are conceptual constructs.

Layers exist as logical collections of Goal-bearing FDOs and CBK-bearing FDOs.

Layers possess no independent persistent identity.

Representations of Layers may exist, but those representations are not Layers themselves.

This distinction became foundational throughout the specification.

---

## Layer Image

Layer Images represent established Layers.

Layer Images support inspection, provenance recording, reproducibility activities, Output Package creation, and Saved Run Package creation.

Layer Images are representational artifacts.

Layer Images are not Layers.

The specification consistently maintains the distinction between conceptual constructs and their representations.

---

## Preservation by Reference

Saved Run Packages preserve references to FDOs rather than FDO payload bitstreams.

The specification therefore preserves sufficient information to reconstruct alignment contexts without requiring duplication of referenced digital objects.

This decision significantly reduced preservation complexity while supporting reproducibility objectives.

---

## Alignment Result Graph Authority

The Alignment Result Graph serves as the authoritative scientific result object produced by an Alignment Run.

Supporting artifacts may supplement interpretation.

No supporting artifact supersedes Alignment Result Graph contents.

This decision established a single authoritative result representation throughout the specification.

---

# Specification Evolution

The final architecture emerged through iterative refinement and stabilization.

Several concepts evolved substantially before reaching their final form.

## Layer Finalization to Layer Establishment

Earlier formulations described Layer Finalization.

Subsequent review determined that establishment more accurately reflected the architectural role of a Layer.

The final specification therefore adopted Layer Establishment.

This terminology better reflects the conceptual nature of Layers and avoids implications of persistence or lifecycle ownership.

---

## Additivity to Saved Run Package Augmentation

Earlier drafts used the term Additivity.

Review activities determined that Augmentation more accurately described the architectural relationship among Saved Run Package components.

The final specification therefore adopted Saved Run Package Augmentation.

---

## Discard Result to Clear Result

Earlier user interaction concepts employed Discard Result terminology.

Subsequent review determined that Clear Result more accurately represented the intended state transition behavior.

The final specification therefore adopted Clear Result.

---

## Preservation Provenance to Saved Run Package Provenance

Earlier drafts referred to Preservation Provenance.

Specification-wide terminology review determined that Saved Run Package Provenance more accurately reflected the architecture.

The final specification therefore adopted Saved Run Package Provenance.

Historical references to Preservation Provenance remain relevant only for understanding specification evolution.

---

## Output Package Layer Image and Saved Run Package Layer Image

Multiple architectural alternatives were evaluated regarding Layer Image creation.

One alternative proposed generation of separate Layer Images for Output Packages and Saved Run Packages.

The final architecture rejected this approach.

The specification instead preserves the same Layer Image across both package types.

This decision improved consistency, reduced duplication, and simplified provenance relationships.

---

## Principle Traceability Terminology

Several formulations were evaluated for documenting relationships between principles and specification sections.

The final specification adopted the phrase:

**Reflected In**

This terminology was selected because it accurately describes architectural correspondence without implying implementation mechanics.

---

# Contributions

The following sections describe categories of contributions that materially influenced development of the final specification.

These categories are descriptive.

They do not constitute ownership claims, governance assertions, or normative attributions.

---

## Author's Architectural Contributions

Architectural contributions reflected throughout the specification include:

- alignment-only scope
- metadata-driven alignment
- Layer establishment
- Layer Image architecture
- preservation by reference
- Alignment Result Graph authority
- Saved Run Package augmentation
- provenance architecture
- reproducibility architecture
- conceptual separation of architecture and implementation responsibilities

---

## Author's Conceptual Precision Contributions

- Goal versus Goal Representation
- CBK versus CBK Artifact
- Layer versus Layer Image
- concept versus representation
- realization versus representation
- save versus preserve
- augmentation versus additivity
- reflected in versus implementation-oriented terminology

---

## Author's Consistency Review Contributions

- terminology harmonization
- cardinality consistency review
- state model refinement
- provenance consistency review
- package-wide architectural coherence review
- cross-part terminology reconciliation
- artifact relationship harmonization
- specification-wide consistency auditing

---

## Collective Contributions

- iterative review
- challenge and critique
- audit cycles
- terminology harmonization
- cross-part reconciliation
- package-wide consistency review
- refinement of conceptual distinctions
- stabilization of architectural boundaries
- resolution of competing formulations
- specification-wide harmonization

---

# Provenance Notes

This appendix documents specification provenance.

It does not define runtime provenance requirements.

Runtime provenance requirements are defined elsewhere within the normative specification.

---

# Appendix Notes

This appendix is informative.

This appendix records how the specification evolved and how major architectural decisions became stabilized.

No content contained within this appendix supersedes the normative specification.

If conflicts are identified in future revisions, the authoritative specification contained within Chapters 2–6 SHALL take precedence.
