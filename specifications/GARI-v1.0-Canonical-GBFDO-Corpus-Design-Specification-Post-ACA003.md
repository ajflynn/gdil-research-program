# GARI v1.0 Canonical GB-FDO Corpus Design Specification

Version: GARI v1.0  
Status: Corpus Design Specification — Post-ACA003 Draft  
Date: 2026-06-20  

Authoritative Context:

* GARI-v1.0-Specification-Release-Candidate-Reconciled.md
* GARI-v1.0-Implementation-Specification-Publication-Candidate.md
* GARI-v1.0-Reference-Data-Schemas-Publication-Candidate.md

---

# Document Status

This document specifies the design of a canonical Goal-bearing FAIR Digital Object corpus for GARI v1.0.

This Post-PR004 Draft incorporates accepted stress-test findings WT-001 through WT-010 and accepted Publication Readiness findings PR-001 through PR-004 concerning Metadata Representation Condition operationalization, fixture variant integrity, runtime identifier neutrality, computational-function category grounding, domain scope clarification, corpus-evaluation separation, realistic Goal variability, abstraction-boundary control, and publication-state provenance clarity.

This document does not modify GARI v1.0.

This document does not modify the Release Candidate.

This document does not modify the Implementation Specification.

This document does not modify the Reference Data Schemas.

This document does not define Alignment Engine algorithms.

This document does not define a new GARI runtime artifact.

Instead, this document defines a reusable scientific corpus of Goal-bearing FAIR Digital Objects intended to support implementation testing, reproducibility studies, interoperability studies, future conformance activities, and research on metadata-driven alignment.

If this document appears to conflict with the authoritative GARI v1.0 documents, the authoritative GARI v1.0 documents govern.

---

# 1. Purpose

## 1.1 Purpose of the Corpus

The purpose of the canonical GB-FDO corpus is to provide a stable, reusable, scientifically meaningful set of Goal-bearing FAIR Digital Objects for use in GARI v1.0 investigations.

The corpus SHALL support:

* GARI implementation testing;
* reproducibility studies;
* interoperability studies;
* future conformance activities;
* metadata-driven alignment research.

The corpus SHALL function as a first-class scientific asset.

The corpus SHALL be sufficiently realistic to resemble real-world Goal-bearing FDO conditions while remaining sufficiently structured to support controlled scientific investigation.

## 1.2 Non-Purposes

The corpus SHALL NOT be used to determine whether computational goals can actually be achieved.

The corpus SHALL NOT be used to evaluate the operational effectiveness of CBK Artifacts.

The corpus SHALL NOT be used to evaluate real-world clinical, biomedical, public health, scientific, educational, financial, logistics, or operational outcomes.

The corpus SHALL NOT define Alignment Engine behavior.

The corpus SHALL NOT prescribe how an Alignment Engine should internally identify alignments.

The corpus SHALL NOT define evaluation methodologies, scoring systems, benchmark truth models, adjudication procedures, or experimental protocols.

The corpus SHALL NOT introduce metadata generation, metadata repair, metadata enrichment, or metadata modification into GARI.

The corpus SHALL NOT create a new GARI architectural concept.

---

# 2. Scientific Framing

## 2.1 GARI as Scientific Instrument

GARI v1.0 is a scientific instrument for investigating metadata-driven alignment between Goal-bearing FAIR Digital Objects and CBK-bearing FAIR Digital Objects.

The canonical GB-FDO corpus is therefore not merely sample data.

It is part of the scientific apparatus required to conduct reproducible investigations of alignment behavior.

## 2.2 Primary Scientific Focus

The primary scientific focus of the corpus is alignment behavior under different Metadata Representation Conditions.

The corpus is intended to support the question:

```text
How does alignment behavior change
across Metadata Representation Conditions
applied to computational Goals expressed
at a controlled abstraction level?
```

Accordingly, the primary corpus-design variable is:

```text
Metadata Representation Condition (MRC)
```

Metadata Representation Condition replaces the earlier, less precise term:

```text
Metadata Expressiveness
```

for the primary condition dimension of this corpus.

## 2.3 Scientific Boundary

The corpus supports investigation of metadata-driven alignment behavior.

It does not support investigation of knowledge application success.

The corpus supports study of whether Alignment Engines identify, represent, compare, and reason about potential alignment relationships using metadata representations of Goals.

It does not support study of whether those alignments lead to correct decisions, accurate predictions, effective interventions, successful workflow execution, or improved real-world outcomes.

## 2.4 Corpus-Evaluation Separation

The corpus defines conditions.

Experiments produce results.

Evaluation interprets results.

These activities SHALL remain separate.

The corpus specification governs the construction of GB-FDO fixtures and their metadata representation conditions.

It does not define expected alignments, alignment correctness, alignment plausibility, benchmark truth, scoring methods, evaluation protocols, or adjudication procedures.

## 2.5 Metadata Representation Condition Operationalization

Metadata Representation Condition (MRC) is the primary corpus-design variable used by the canonical corpus.

Metadata Representation Systems are the representational mechanisms through which Metadata Representation Conditions are instantiated.

The corpus varies Metadata Representation Conditions in order to investigate alignment behavior across different Metadata Representation Systems.

The scientific object of study is not simply “more metadata.”

The scientific object of study is whether different Metadata Representation Systems influence metadata-driven alignment behavior.

## 2.6 Metadata Representation Systems Principle

Metadata representations are unified representational artifacts whose structure, meaning, and machine-processable characteristics are inseparable aspects of the same representation.

These characteristics may be discussed separately for analytical purposes, but they do not exist independently.

Accordingly, each Metadata Representation Condition is treated as an instantiation of a Metadata Representation System rather than as a collection of independently varying metadata characteristics.

## 2.7 Abstraction Boundary

The canonical corpus SHALL vary Metadata Representation Conditions while minimizing narrow domain-specific semantic variation.

The corpus operates at the level of computational functions rather than biomedical specialties.

The canonical computational-function set for the initial corpus SHALL be:

* Prediction;
* Classification;
* Recommendation;
* Calculation.

These categories provide the primary semantic abstraction boundary for the canonical GARI v1.0 GB-FDO corpus.

For purposes of this corpus, Prediction refers specifically to future-oriented estimation of a future state, future event, future condition, or future outcome.

The corpus intentionally retains this future-oriented interpretation of Prediction in order to distinguish Prediction from Calculation, Classification, and Recommendation.

The corpus does not use increased Metadata Representation Condition as a license to introduce narrow biomedical subspecialty semantics.

## 2.8 Extensibility of Metadata Representation Conditions

The Metadata Representation Conditions defined in this specification represent the initial operational conditions adopted for the canonical GARI v1.0 GB-FDO corpus.

The initial conditions are:

* MRC-1 — Parameter Item Metadata;
* MRC-2 — FHIR Resource Metadata;
* MRC-3 — FHIR RDF Metadata.

These conditions support controlled investigation of alignment behavior across progressively more structured and machine-actionable metadata environments.

The Metadata Representation Condition framework is extensible.

Future corpus versions, research initiatives, or evaluation frameworks MAY introduce additional Metadata Representation Conditions when justified by scientific objectives, emerging representation technologies, or future study requirements.

MRC-1 through MRC-3 SHALL NOT be interpreted as exhaustively defining the space of metadata representation.

They represent an initial experimental framework rather than a theoretical upper bound.


## 2.9 Item Space

The canonical GB-FDO corpus is organized around three primary scientific constructs:

```text
Goal Space
Item Space
Metadata Representation Condition Space
```

Goal Space defines the computational transformations represented by corpus Goals.

Metadata Representation Condition Space defines the metadata representation systems through which those Goals are expressed.

Item Space defines the Items that participate in those computational transformations.

### 2.9.1 Item as Fundamental Abstraction

For purposes of this corpus, an Item is the fundamental abstract entity that participates in a computational transformation.

The corpus does not treat inputs and outputs as distinct conceptual classes.

Instead:

```text
Input
and
Output
```

are roles that may be played by Items within a computational transformation.

Accordingly, a Goal may be viewed abstractly as:

```text
Item Set
    →
Computational Function
    →
Item Set
```

where the participating Items may assume input roles, output roles, or both.

### 2.9.2 Item Space as a Corpus Design Construct

Item Space is an intentional and curated aspect of the canonical corpus design.

The corpus does not treat Item characteristics as arbitrary.

The corpus intentionally constrains the Item Space represented within Metadata Representation Conditions in order to support controlled investigation of metadata-driven alignment behavior.

The purpose of these constraints is not to model the full diversity of real-world digital objects.

The purpose is to create a scientifically useful Item environment within which Metadata Representation Conditions may be investigated.

### 2.9.3 Item Identity Principle

The canonical corpus adopts the working hypothesis that metadata-driven alignment is principally concerned with:

* Goal representations;
* Item identities;
* Item relationships;
* Metadata representations;

rather than with media-specific characteristics of Items.

Accordingly, the corpus treats Item identity as a more fundamental alignment construct than Item media form.

This principle does not assert that Item typing, Item semantics, or Item structure are universally unimportant.

Rather, the canonical corpus intentionally limits variation in those characteristics in order to support investigation of Metadata Representation Conditions.

### 2.9.4 Item Space Across Metadata Representation Conditions

The canonical corpus defines Item Space differently across Metadata Representation Conditions.

For MRC-1:

* Items SHALL be represented as abstract identifiable Items;
* Items SHALL possess unique identifiers;
* Item typing SHALL NOT be required;
* rich domain semantics SHALL NOT be required.

For MRC-2:

* Items SHALL be represented through constrained FHIR resource structures or profile-constrained collections of FHIR resources;
* Item identity SHALL remain explicit.

For MRC-3:

* Items SHALL be represented through constrained FHIR RDF resource structures or profile-constrained RDF graph representations derived from FHIR resources;
* Item identity SHALL remain explicit.

These conditions provide alternative metadata representation environments while preserving the underlying conceptual Goal.

### 2.9.5 Excluded Item Forms

The canonical corpus is not intended to represent every possible Item form.

The corpus intentionally excludes rich media-oriented Item classes as primary corpus-design elements.

Examples include:

* image-centric Items;
* audio-centric Items;
* video-centric Items;
* document-centric Items;
* arbitrary multimedia artifacts.

Such Item forms MAY be investigated in future corpus families.

They are outside the scope of the canonical GARI v1.0 GB-FDO corpus.

### 2.9.6 Scientific Purpose

The Item Space defined by this corpus is intended to support controlled investigation of metadata-driven alignment behavior across Metadata Representation Conditions.

The canonical corpus does not attempt to determine whether Item type, Item media form, or domain-specific Item semantics are primary determinants of alignment behavior.

Those questions remain appropriate subjects for future investigation.

The canonical corpus instead provides a constrained Item Space suitable for reproducible investigation of Metadata Representation Conditions within the broader GARI scientific framework.


---

# 3. Governing Design Principles

## 3.1 Authoritative Specification Alignment

The corpus SHALL remain consistent with GARI v1.0.

Each GB-FDO in the corpus SHALL represent exactly one Goal.

Each GB-FDO SHALL contain the minimum FDO elements recognized by GARI:

1. PID;
2. Type;
3. Profile Reference;
4. Metadata;
5. Bitstream.

All Goal Representations contained within a GB-FDO SHALL be interpreted as alternative representations of the same Goal.

## 3.2 Metadata-Only Alignment Compatibility

The corpus SHALL be designed so that Alignment Engines can operate on metadata represented in Layer Images and Input Packages.

The corpus SHALL NOT require payload bitstreams to be included in Input Packages.

The corpus MAY include Goal Representation bitstreams as part of GB-FDOs, but those bitstreams SHALL remain distinct from metadata and SHALL NOT be required in metadata-only Input Packages unless represented by reference.

## 3.3 Concept-Representation Separation

The corpus SHALL distinguish:

* the conceptual Goal;
* representations of that Goal;
* metadata describing the GB-FDO;
* the bitstream associated with the GB-FDO;
* corpus governance metadata;
* external evaluation materials.

Corpus-level governance annotations SHALL NOT be confused with Goal metadata available to Alignment Engines.

## 3.4 No Hidden Evaluation Information in Runtime Metadata

Evaluation materials, answer keys, expected outputs, scoring rubrics, or adjudication files SHALL NOT be included in GB-FDO metadata supplied to GARI Alignment Runs.

Alignment Engines SHALL NOT receive evaluation answer keys through Input Packages.

## 3.5 Metadata Representation Condition Separation

Metadata Representation Conditions SHALL be represented as separate corpus fixture variants.

A single GB-FDO fixture SHALL NOT contain multiple alternative metadata representation states.

Each GB-FDO fixture SHALL contain one metadata condition.

## 3.6 Experimental Control

For this canonical GB-FDO corpus, Metadata Representation Condition is the condition intentionally varied across fixture variants.

The following SHALL be treated as controlled variables for all MRC variants of a given conceptual Goal:

* conceptual Goal;
* Goal Representation Type;
* Goal Representation content.

The canonical corpus SHALL use DFSK as the Goal Representation Type for all GB-FDO fixtures.

For a given conceptual Goal, the DFSK Goal Representation content SHALL remain fixed across MRC-1, MRC-2, and MRC-3 fixture variants.

Only Metadata Representation Condition SHALL vary across those fixture variants.

This control is necessary to support scientific investigation of metadata representation without confounding that investigation with Goal Representation Type, Goal Representation method, or Goal Representation content.

## 3.7 Goal Representation Extensibility

Goal Representation Type and Goal Representation content are extensible within the broader GARI architecture.

The canonical GB-FDO corpus does not attempt to evaluate alternative Goal Representation Types or alternative Goal Representation methods.

The decision to use DFSK for all corpus fixtures is an intentional corpus-design control and SHALL NOT be interpreted as a limitation of GARI itself.

Future corpora or scientific investigations MAY vary Goal Representation Type, Goal Representation method, or Goal Representation content when such variation is the subject of study.

## 3.8 Scientific Fixture Library Principle

The corpus SHALL function as a scientific fixture library.

The corpus SHALL NOT prescribe experimental design.

Investigators MAY assemble Layers using any scientifically justified combination of GB-FDO fixtures, including homogeneous Metadata Representation Condition selections, mixed Metadata Representation Condition selections, or other investigator-defined configurations.

Metadata Representation Conditions SHALL be understood as properties of GB-FDO fixtures and corpus governance records.

Metadata Representation Conditions SHALL NOT be interpreted as properties of Layers, Layer Images, Input Packages, Alignment Runs, Alignment Engines, or GARI runtime behavior.

## 3.9 Runtime Identifier Neutrality

The canonical corpus SHOULD use runtime-visible identifiers that avoid encoding:

* Metadata Representation Conditions;
* conceptual-goal relationships;
* evaluation classifications;
* corpus-governance assignments;
* experimental-condition assignments;

when practical neutral alternatives exist.

Mappings between runtime identifiers and corpus-governance information SHOULD be maintained in:

* corpus manifests;
* goal records;
* governance metadata;
* corpus-management artifacts.

This recommendation applies only to the canonical corpus and SHALL NOT be interpreted as a GARI architectural requirement or a restriction on arbitrary investigator-created GB-FDOs.

## 3.10 Realistic Goal Variability

The corpus SHOULD preserve realistic variation in Goal formulation where scientifically useful.

The corpus does not assume that computationally equivalent Goals must be represented identically.

The corpus does not attempt to create a canonical ontology of Goals.

The corpus MAY contain:

* near-equivalent Goals;
* overlapping Goals;
* alternative phrasings;
* alternative framings;
* Goals expressing similar computational intentions;

when such fixtures improve realism and scientific utility.

Conceptual Goal identity within the corpus is a corpus-governance construct used for fixture organization, provenance management, Metadata Representation Condition control, and corpus maintenance.

It SHALL NOT be interpreted as a claim regarding universal Goal identity.

The corpus makes no normative assumptions regarding how Goals originate.

Goals may be produced by humans, organizations, software systems, workflows, agents, future AI systems, or other Goal-producing entities.

GARI itself assumes only that a Goal has been represented in a GB-FDO capable of participating in a Layer, Layer Image, Input Package, and Alignment Engine workflow.

## 3.11 Computational Abstraction Boundary

The corpus SHALL operate at the level of abstract computational functions.

The initial computational-function abstraction layer SHALL be limited to:

* Prediction;
* Classification;
* Recommendation;
* Calculation.

Other computational activities MAY be represented in future corpora.

The canonical GARI v1.0 GB-FDO corpus intentionally limits its primary computational-function scope to these four categories in order to support a controlled investigation of Metadata Representation Conditions.

## 3.12 Domain-Semantics Control

The canonical corpus SHALL avoid using narrow biomedical field semantics as the primary source of variation.

Examples of narrow biomedical field semantics that SHALL NOT define the corpus include:

* oncology;
* cardiology;
* dentistry;
* sepsis;
* readmission;
* medication dosing;
* specific disease areas;
* specific therapeutic areas.

Such concepts MAY appear in future corpora.

They SHALL NOT define the primary semantic variation strategy of the canonical GARI v1.0 corpus.


## 3.13 Item Space Principle

The canonical GARI v1.0 GB-FDO corpus SHALL treat Item Space as a first-class corpus-design construct.

Item Space SHALL be governed independently from Goal Space and independently from Metadata Representation Condition Space.

The corpus SHALL recognize that computational Goals operate upon Items and that Item characteristics may influence metadata-driven alignment behavior.

Accordingly, Item Space SHALL be intentionally designed, curated, and constrained as part of corpus construction.

### 3.13.1 Item Abstraction Principle

For purposes of the canonical corpus, Item SHALL be treated as the fundamental abstraction participating in computational transformations.

Inputs and outputs SHALL NOT be treated as separate conceptual classes.

Instead, input and output SHALL be treated as roles that may be assumed by Items within a computational transformation.

The corpus SHALL organize Item representations according to the Item abstraction rather than according to separate input and output taxonomies.

### 3.13.2 Item Identity Control

The canonical corpus SHALL preserve stable Item identity within Metadata Representation Conditions and across Metadata Representation Condition variants when representing the same conceptual Goal.

Item identity SHALL be treated as a primary Item-level construct for corpus design.

The corpus SHALL NOT require Item typing as a prerequisite for Item representation.

The corpus SHALL NOT require rich domain-specific semantics as a prerequisite for Item representation.

### 3.13.3 MRC-1 Item Constraint

MRC-1 SHALL represent Items as abstract identifiable Items.

MRC-1 Items SHALL possess unique identifiers.

MRC-1 SHALL NOT require Item type declarations.

MRC-1 SHALL NOT require domain-specific ontological classifications.

MRC-1 SHALL support metadata-driven alignment under intentionally sparse Item representation conditions.

### 3.13.4 MRC-2 Item Constraint

MRC-2 SHALL represent Items through constrained FHIR resource structures or profile-constrained collections of FHIR resources.

The purpose of MRC-2 Item representations is to introduce structured resource-based metadata while preserving the underlying conceptual Goal.

MRC-2 SHALL NOT introduce narrow biomedical specialty semantics as the primary source of corpus variation.

### 3.13.5 MRC-3 Item Constraint

MRC-3 SHALL represent Items through constrained FHIR RDF resource structures or profile-constrained RDF graph representations derived from FHIR resources.

The purpose of MRC-3 Item representations is to introduce graph-oriented metadata representation while preserving the underlying conceptual Goal.

MRC-3 SHALL remain comparable in semantic scope to MRC-2.

The principal distinction between MRC-2 and MRC-3 SHALL be representation form rather than domain-semantic expansion.

### 3.13.6 Canonical Item Space Boundary

The canonical corpus SHALL intentionally limit the Item Space represented within the corpus.

The corpus SHALL NOT attempt to represent the full diversity of possible digital-object forms.

The canonical corpus SHALL exclude rich media-oriented Item classes as primary corpus-design elements, including:

* image-centric Items;
* audio-centric Items;
* video-centric Items;
* document-centric Items;
* arbitrary multimedia artifacts.

Such Item forms MAY be investigated in future corpus families.

They are outside the scope of the canonical GARI v1.0 GB-FDO corpus.

### 3.13.7 Scientific Control Principle

The canonical corpus SHALL treat Item Space as a controlled corpus-design construct.

The corpus SHALL intentionally constrain Item variation in order to support controlled investigation of Metadata Representation Conditions.

The corpus SHALL NOT treat unrestricted Item diversity as a primary scientific objective of the canonical corpus.

Future corpora MAY vary Item Space, Item representation approaches, Item typing strategies, Item semantic richness, or Item media forms when such variation becomes the subject of investigation.

Such studies SHALL be considered distinct from the primary Metadata Representation Condition investigations supported by the canonical GARI v1.0 GB-FDO corpus.


---

# 4. Corpus Architecture

## 4.1 Recommended Corpus Model

The canonical corpus SHOULD use the following model:

```text
Conceptual Goal
  → GB-FDO Fixture Variant at MRC-1
  → GB-FDO Fixture Variant at MRC-2
  → GB-FDO Fixture Variant at MRC-3
```

This is the recommended design.

It preserves the same underlying conceptual Goal and the same DFSK Goal Representation while varying Metadata Representation Condition.

This design supports within-goal comparison across metadata representation conditions without requiring a single GB-FDO to contain multiple metadata states.

## 4.2 Fixture Variant Integrity Rule

For each conceptual Goal, MRC-1, MRC-2, and MRC-3 SHALL be represented as separate GB-FDO fixture variants.

A single GB-FDO SHALL NOT contain multiple alternative metadata representation states.

Each GB-FDO fixture SHALL contain:

* one Goal;
* one fixed DFSK Goal Representation for that Goal;
* one Metadata Representation Condition;
* one Metadata Representation Condition assignment recorded in corpus governance metadata.

The purpose of separate fixture variants is to preserve real-world fidelity while enabling controlled scientific manipulation of metadata representation.

## 4.3 Rejected Alternatives

The corpus SHOULD NOT use distinct conceptual Goals at each Metadata Representation Condition as the primary canonical design.

That design would confound metadata representation with goal content.

It would be difficult to determine whether differences in alignment behavior were caused by metadata representation or by differences among the Goals themselves.

Distinct goals at each representation condition MAY be used in later exploratory corpora, but not in the canonical GARI v1.0 GB-FDO corpus.

The corpus also SHOULD NOT encode multiple metadata representation states inside a single GB-FDO fixture.

That design would reduce real-world fidelity and blur the distinction between a GB-FDO metadata state and corpus-level experimental fixture management.

## 4.4 Corpus Unit

The primary corpus unit is the conceptual Goal.

Each conceptual Goal SHALL have:

* a stable conceptual Goal identifier;
* a human-readable goal statement;
* a computational-function category;
* three GB-FDO variants corresponding to MRC-1, MRC-2, and MRC-3;
* corpus governance metadata.

## 4.5 GB-FDO Variant Unit

Each GB-FDO variant SHALL have:

* a PID;
* type value indicating GB-FDO;
* profile reference;
* metadata appropriate to the Metadata Representation Condition;
* bitstream reference;
* fixture path;
* checksum;
* version;
* provenance metadata.

## 4.6 Recommended Identifier Pattern

The corpus SHOULD use stable identifiers for fixture development and corpus governance.

Runtime-visible fixture identifiers SHOULD avoid encoding MRC assignments or conceptual-goal relationships where practical.

Recommended conceptual Goal identifier pattern for governance records:

```text
gari-gb-goal-0001
```

Recommended neutral GB-FDO fixture identifier pattern for runtime-visible artifacts:

```text
urn:gari:v1:gbfdo:k3f7q
urn:gari:v1:gbfdo:t9m2x
urn:gari:v1:gbfdo:a6r4v
```

These are examples only.

The mapping between fixture identifiers and Metadata Representation Conditions SHALL be maintained in corpus governance metadata and corpus manifests.

GB-FDO runtime metadata SHOULD NOT require MRC-specific profile references.

These identifier patterns are recommended for fixture stability and runtime neutrality.

They do not prescribe a required external PID technology.

---

# 5. Metadata Representation Conditions

## 5.1 Overview

The corpus SHALL be organized around three Metadata Representation Conditions.

The conditions are:

* MRC-1 — Parameter Item Metadata;
* MRC-2 — FHIR Resource Metadata;
* MRC-3 — FHIR RDF Metadata.

The conditions are intended to support controlled investigation of how alignment behavior changes across different metadata representation environments.

The conditions represent distinct metadata representation systems.

They SHALL NOT be interpreted as a simple hierarchy of “better” metadata.

## 5.2 MRC-1 — Parameter Item Metadata

### 5.2.1 Purpose

MRC-1 represents the minimum viable metadata condition.

It is intended to expose a sparse and abstract metadata representation of a GB-FDO.

MRC-1 establishes a baseline condition for alignment behavior under minimal metadata representation.

### 5.2.2 Metadata Characteristics

An MRC-1 GB-FDO SHALL contain the minimum elements required for GARI-recognized FDOs.

MRC-1 metadata SHOULD include only:

* PID;
* type;
* profile reference;
* minimal title or label;
* goal representation reference;
* parameter item metadata sufficient for fixture interpretation.

MRC-1 metadata SHOULD NOT include detailed structured metadata describing domain-specific subject matter.

MRC-1 metadata SHOULD preserve the computational-function abstraction boundary.

### 5.2.3 Example Metadata Pattern

```json
{
  "pid": "urn:gari:v1:gbfdo:k3f7q",
  "type": "GB-FDO",
  "profileReference": "gari-gb-fdo-profile-v1",
  "metadata": {
    "label": "Goal Item",
    "computationalFunction": "prediction",
    "goalRepresentations": [
      {
        "representationType": "dfsk-reference",
        "value": "goal-representation.json"
      }
    ]
  },
  "bitstreamReference": "goal-representation.json"
}
```

### 5.2.4 Scientific Use

MRC-1 supports:

* sparse metadata alignment testing;
* baseline condition testing;
* lower-structure metadata evaluation;
* evaluation of alignment behavior when metadata is minimally represented.

## 5.3 MRC-2 — FHIR Resource Metadata

### 5.3.1 Purpose

MRC-2 represents a structured resource metadata condition.

It uses a FHIR-oriented resource representation and a GB-FDO-specific FHIR profile as the structural model for GB-FDO metadata.

MRC-2 increases structural constraint, metadata organization, and machine-actionability relative to MRC-1.

### 5.3.2 Metadata Characteristics

MRC-2 metadata SHOULD include:

* FHIR-oriented resource structure;
* GB-FDO-specific FHIR profile reference;
* computational-function category;
* abstract input class;
* abstract output class;
* parameter structure where applicable;
* constraint structure where applicable;
* DFSK Goal Representation reference.

MRC-2 MAY include more semantic information than MRC-1.

However, that semantic information SHOULD remain at the level of computational function, input class, output class, parameter structure, data object structure, and profile constraints.

MRC-2 SHALL NOT use narrow biomedical subspecialty semantics as the primary source of variation.

### 5.3.3 Example Metadata Pattern

```json
{
  "resourceType": "GBFDOGoal",
  "id": "t9m2x",
  "meta": {
    "profile": [
      "http://example.org/fhir/StructureDefinition/gari-gb-fdo-goal"
    ]
  },
  "identifier": [
    {
      "system": "urn:gari:v1:gbfdo",
      "value": "t9m2x"
    }
  ],
  "computationalFunction": "prediction",
  "inputClass": "structured-input-set",
  "outputClass": "future-state-estimate",
  "goalRepresentation": {
    "representationType": "dfsk-reference",
    "reference": "goal-representation.json"
  }
}
```

### 5.3.4 Scientific Use

MRC-2 supports:

* evaluation of structured metadata representation;
* profile-constrained metadata testing;
* analysis of alignment behavior under higher metadata organization;
* comparison with parameter item representation.

## 5.4 MRC-3 — FHIR RDF Metadata

### 5.4.1 Purpose

MRC-3 represents a graph-oriented metadata condition.

It uses a FHIR RDF-oriented representation and a GB-FDO-specific FHIR RDF profile or profile-constrained RDF representation as the structural model for GB-FDO metadata.

MRC-3 is intended to be comparable in semantic scope to MRC-2 while changing the representation into an RDF graph form.

### 5.4.2 Metadata Characteristics

MRC-3 metadata SHOULD include:

* RDF graph representation;
* FHIR RDF-oriented structure;
* GB-FDO-specific RDF profile or profile-constrained representation;
* computational-function category;
* abstract input class;
* abstract output class;
* parameter structure where applicable;
* constraint structure where applicable;
* DFSK Goal Representation reference.

MRC-3 MAY include semantic information comparable to MRC-2.

The principal difference between MRC-2 and MRC-3 SHOULD be graph-oriented representation and RDF-based machine-actionability, not a major increase in narrow domain-specific semantic content.

### 5.4.3 Example Metadata Pattern

```turtle
@prefix gari: <http://example.org/gari/> .
@prefix fhir: <http://hl7.org/fhir/> .

gari:a6r4v
  a gari:GBFDOGoal ;
  gari:computationalFunction "prediction" ;
  gari:inputClass "structured-input-set" ;
  gari:outputClass "future-state-estimate" ;
  gari:goalRepresentation "goal-representation.json" .
```

### 5.4.4 Scientific Use

MRC-3 supports:

* evaluation of graph-oriented metadata representation;
* semantic-web-compatible metadata testing;
* analysis of alignment behavior under RDF representation;
* comparison between structured resource metadata and RDF graph metadata.

---

# 6. Computational Functions as the Basis for Goal Categories

## 6.1 Conceptual Foundation

The Goal category system used by the canonical GB-FDO corpus is a Computational Function Category Framework.

The framework is grounded in procedural knowledge, generic-task reasoning, computational functions, and computable knowledge.

A computational function is a class of procedural capability that transforms inputs into outputs according to a specified computational method.

Goals express desired computational functions.

CBK-bearing artifacts may embody capabilities capable of realizing those functions.

This distinction provides part of the conceptual foundation for metadata-driven alignment.

## 6.1A Scientific Foundation for the Computational Function Framework

The canonical computational-function framework is grounded in three complementary traditions:

* Procedural Knowledge (Anderson, 1983);
* Generic Tasks and Reasoning Tasks (Clancey, 1985; Chandrasekaran, 1986; Chandrasekaran et al., 1992);
* Computable Knowledge and Learning Health System traditions (Friedman et al., 2015 and related literature).

The categories Prediction, Classification, Recommendation, and Calculation are scientifically grounded corpus-design constructs adopted to support investigation of Metadata Representation Conditions as instantiated through Metadata Representation Systems.

They are not asserted to constitute a complete taxonomy of computational functions.

They are not asserted to define a normative ontology of computational functions.

## 6.2 Canonical Computational Functions

The canonical GARI v1.0 GB-FDO corpus SHALL use four primary computational-function categories:

| Category | Definition |
|---|---|
| Prediction | Future-oriented estimation of a future state, event, condition, or outcome. |
| Classification | Assignment of one or more categories to an entity, object, state, or case. |
| Recommendation | Suggestion of one or more candidate actions, options, or choices. |
| Calculation | Computation of a value from specified inputs using a defined procedure. |

These categories define the initial abstraction layer for the canonical corpus.

Future corpora MAY introduce additional computational-function categories when scientifically justified. Such additions do not invalidate the canonical four-category framework adopted for the GARI v1.0 corpus.

## 6.3 Prediction Boundary

For this corpus, Prediction SHALL retain future orientation.

Prediction SHALL NOT be used merely as a synonym for producing any model output.

This definition intentionally differs from usages in which “prediction” is generalized to mean any output produced by a model.

The corpus retains the future-oriented meaning of Prediction to preserve a useful distinction from Calculation, Classification, and Recommendation.

## 6.4 Category Purpose

Computational Function Categories support:

* corpus construction;
* corpus balancing;
* metadata design;
* alignment analysis;
* controlled investigation of Metadata Representation Conditions.

Categories SHALL NOT be interpreted as mutually exclusive ontological classes.

## 6.5 Primary and Secondary Categories

Each conceptual Goal SHALL have one Primary Category representing its principal computational function.

A conceptual Goal MAY have one or more Secondary Categories representing additional computational-function relationships.

Secondary categories SHALL be used cautiously so that the four-category abstraction boundary remains clear.

## 6.6 Vocabulary Considerations

If Computational Function Categories are exposed through GB-FDO metadata, they SHOULD be drawn from a corpus value set.

Future corpus versions MAY map category values to external vocabularies, terminologies, or ontologies.

Such mappings are not required for the canonical GARI v1.0 corpus.

---

# 7. Goal Category Design

## 7.1 Recommended Category Set

The canonical corpus SHALL include computational Goals from the following primary categories:

| Category | Description | Rationale |
|---|---|---|
| Prediction | Estimate future states, future events, future conditions, or future outcomes. | Retains a future-oriented computational function distinct from generic model output. |
| Classification | Assign entities, cases, objects, or states to one or more categories. | Provides a highly general computational function occurring across domains. |
| Recommendation | Suggest one or more candidate actions, options, or choices. | Represents action- or option-oriented computational support. |
| Calculation | Compute a value from specified inputs using a defined procedure. | Captures calculators, scores, formulas, and parameterized computable procedures. |

## 7.2 Category Balance

The canonical corpus SHOULD avoid overconcentration in a single category.

A medium corpus of 120 conceptual Goals SHOULD allocate approximately:

| Category | Recommended Count |
|---|---:|
| Prediction | 30 |
| Classification | 30 |
| Recommendation | 30 |
| Calculation | 30 |
| Total | 120 |

These counts are recommended starting targets.

They MAY be adjusted during corpus construction if needed to preserve scientific utility.

## 7.3 Category Assignment Rules

Each conceptual Goal SHALL have one primary computational-function category.

Each conceptual Goal MAY have one or more secondary categories.

Primary category SHALL support corpus organization and balance.

Secondary categories MAY support exploratory analysis.

Category assignments are corpus-governance assignments and SHALL NOT be interpreted as universal claims regarding Goal identity.

---

# 8. Corpus Size Recommendation

## 8.1 Recommended Size

The canonical GARI v1.0 GB-FDO corpus SHOULD contain:

```text
120 conceptual Goals
```

Each conceptual Goal SHOULD have three Metadata Representation Condition variants.

Therefore, the canonical corpus SHOULD contain:

```text
360 GB-FDO fixtures
```

## 8.2 Rationale

A corpus of 120 conceptual Goals is large enough to support meaningful category coverage, representation-condition comparison, implementation testing, reproducibility studies, and publication-quality analysis.

It is small enough to support careful curation, manual review, provenance tracking, version control, fixture maintenance, and practical use in implementation test suites.


## 8.2A Layer Variability Rationale

The canonical GB-FDO corpus exists not only as a collection of Goal-bearing FAIR Digital Object fixtures but also as a source population from which Layers may be constructed.

Because GARI operates on Layers rather than isolated GB-FDOs, corpus scale SHALL be evaluated in part according to its ability to support meaningful variability among possible Layer realizations.

The corpus SHOULD be sufficiently large to support:

* repeated random Layer construction;
* constrained Layer construction;
* Metadata Representation Condition-specific Layer construction;
* mixed-Metadata Representation Condition Layer construction;
* category-balanced Layer construction;
* category-specific Layer construction;
* future investigator-defined Layer construction strategies.

The scientific objective of the corpus is not limited to analysis of individual alignment outcomes.

The corpus SHOULD support investigation of distributions of alignment outcomes arising from many distinct Layer realizations constructed from the corpus.

Accordingly, corpus scale SHOULD be evaluated partly in terms of:

* Layer diversity;
* Layer composition variability;
* Layer Image variability;
* Input Package variability;
* Alignment Run variability;
* reproducibility of Layer-based investigations.

A corpus that is too small may produce excessive reuse of the same Goals across Layer constructions and may limit the diversity of achievable Layer configurations.

A corpus that is sufficiently large supports a broader space of possible Layer realizations and more closely reflects the variability expected in real-world Goal-bearing environments.

For purposes of the canonical corpus, support for meaningful Layer variability SHALL be considered a primary scientific criterion when evaluating corpus scale recommendations.


## 8.3 Expansion Path

The canonical corpus SHOULD be developed in phases:

| Phase | Conceptual Goals | GB-FDO Fixtures | Purpose |
|---|---:|---:|---|
| Pilot | 12 | 36 | Validate design, schemas, identifiers, and fixture structure. |
| Alpha | 30 | 90 | Support initial implementation testing and mock engine development. |
| Beta | 60 | 180 | Support early comparison of alignment behavior under MRC variation. |
| v1.0 Canonical | 120 | 360 | Support publication-quality investigation and stable corpus release. |
| Extended | 250+ | 750+ | Support broader category and condition expansion. |

The Pilot phase SHOULD be completed before full corpus expansion.

The v1.0 Canonical phase SHOULD be treated as the first stable corpus release.

---

# 9. Domain Scope

## 9.1 GARI Domain Neutrality

GARI is domain-neutral.

The GARI architecture is not restricted to healthcare, public health, biomedical research, learning health systems, or any other specific domain.

## 9.2 Corpus Abstraction Scope

The canonical GARI v1.0 GB-FDO corpus is domain-neutral in semantic abstraction.

The corpus may be biomedical in provenance or historical motivation, but its canonical Goal space SHALL be expressed at the level of abstract computational functions.

The corpus SHALL NOT organize its primary Goal set around narrow biomedical domains, specialties, diseases, interventions, or data environments.

## 9.3 Rationale

This abstraction-first scope is recommended because:

* the scientific focus is metadata-driven alignment, not biomedical subspecialty reasoning;
* computational functions can be expressed across domains;
* narrow domain semantics could become a confounding source of variation;
* Metadata Representation Conditions can be studied more cleanly when Goal semantics are controlled at an abstract level;
* the corpus should support GARI and GDIL investigations without collapsing into a domain-specific biomedical benchmark.

## 9.4 Future Domain-Specific Extensions

Future corpus extensions MAY introduce domain-specific Goals.

Such extensions MAY include clinical care, public health, biomedical research, learning health systems, finance, logistics, education, environmental science, general computing, and scientific workflows.

These extensions SHOULD be versioned separately so that the canonical GARI v1.0 abstraction-first corpus remains stable.

---

# 10. Goal Construction Rules

## 10.1 Goal Statement Rule

Each conceptual Goal SHALL have a concise human-readable goal statement.

The goal statement SHOULD begin with a verb that expresses the desired computation.

Examples:

* Predict a future state from specified inputs.
* Classify an item into one or more categories.
* Recommend one or more candidate actions.
* Calculate a value from specified parameters.

## 10.2 Single-Goal Rule

Each conceptual Goal SHALL represent one computational desire.

Compound Goals SHOULD be decomposed unless the compound structure is itself the object of study.

Poor example:

```text
Predict a future outcome and recommend an action.
```

Preferred decomposition:

```text
Predict a future outcome.
```

and

```text
Recommend an action based on specified inputs.
```

## 10.3 Operational Neutrality Rule

Goal statements SHOULD describe computational goals without asserting that the computation will be correct, appropriate, useful, or outcome-improving.

Preferred:

```text
Predict a future event probability.
```

Avoid:

```text
Prevent future adverse events.
```

The latter implies real-world intervention success and exceeds the alignment-only scope.

## 10.4 Metadata Representation Condition Rule

The same conceptual Goal SHALL be represented differently across MRC variants.

The conceptual Goal SHALL remain stable.

Only Metadata Representation Condition SHALL change.

## 10.5 Ambiguity Rule

The corpus MAY include controlled ambiguity where scientifically useful.

Ambiguity may include under-specified inputs, vague output form, broad computational-function phrasing, or overlapping computational-function interpretation.

Ambiguity SHOULD be documented as a corpus-governance matter.

## 10.6 Goal Variability Rule

The corpus SHOULD preserve realistic variation in Goal formulation where scientifically useful.

Near-equivalent Goals, overlapping Goals, alternative phrasings, and alternative framings MAY coexist within the corpus when they reflect realistic Goal-producing environments.

The corpus curates Goals.

The corpus does not normalize reality.

## 10.7 Abstraction Boundary Rule

Canonical corpus Goals SHALL remain at the abstract computational-function level.

Goal statements SHALL avoid narrow biomedical specialty semantics as defining content.

Examples of avoided canonical Goal forms include:

```text
Predict sepsis onset.
Classify oncology treatment eligibility.
Calculate pediatric chemotherapy dose.
Recommend cardiology follow-up.
```

Preferred abstraction-level forms include:

```text
Predict a future event from specified inputs.
Classify an item into one or more categories.
Calculate a value from specified parameters.
Recommend one or more candidate actions.
```

---

# 11. Fixture Organization

## 11.1 Recommended Repository Structure

The corpus SHOULD be organized as follows:

```text
gari-v1-canonical-gbfdo-corpus/
  README.md
  VERSION.md
  LICENSE.md
  CHANGELOG.md
  corpus-manifest.json
  governance/
    contribution-rules.md
    review-rules.md
    versioning-policy.md
    identifier-policy.md
    mrc-policy.md
    abstraction-boundary-policy.md
  goals/
    gari-gb-goal-0001/
      goal-record.json
      mrc1/
        gbfdo.json
        metadata.json
        goal-representation.json
        checksum.txt
      mrc2/
        gbfdo.json
        metadata.json
        goal-representation.json
        checksum.txt
      mrc3/
        gbfdo.json
        metadata.json
        goal-representation.json
        checksum.txt
    gari-gb-goal-0002/
      ...
  profiles/
    gari-gb-fdo-profile-v1.json
    fhir/
      gari-gb-fdo-fhir-profile.json
    fhir-rdf/
      gari-gb-fdo-fhir-rdf-profile.ttl
  examples/
    minimal-layer-examples/
    input-package-examples/
    mock-engine-examples/
  validation/
    schemas/
    validation-report.json
  docs/
    design-notes.md
    curation-notes.md
    mrc-notes.md
```

## 11.2 Runtime Fixture Boundary

The `goals/` directory SHALL contain runtime-loadable GB-FDO fixtures.

The `governance/` directory SHALL contain corpus management rules.

The `profiles/` directory SHALL contain profile references used by corpus fixtures.

The `validation/` directory SHALL contain corpus validation resources.

Evaluation artifacts SHALL NOT be part of the corpus runtime fixture boundary.

## 11.3 Goal Record

Each conceptual Goal SHOULD include a `goal-record.json` file containing corpus-level information.

This file is not necessarily part of the GB-FDO metadata supplied to GARI.

Recommended fields:

```json
{
  "conceptualGoalId": "gari-gb-goal-0001",
  "canonicalGoalStatement": "Predict a future event from specified inputs.",
  "primaryCategory": "prediction",
  "secondaryCategories": [],
  "abstractionLevel": "computational-function",
  "metadataRepresentationConditions": ["MRC-1", "MRC-2", "MRC-3"],
  "goalRepresentationType": "DFSK",
  "goalRepresentationContentRule": "fixed across MRC variants",
  "curationStatus": "reviewed",
  "version": "1.0.0",
  "createdBy": "corpus-curation-team",
  "createdAt": "2026-06-20T00:00:00Z",
  "reviewedAt": "2026-06-20T00:00:00Z"
}
```

## 11.4 Corpus Manifest

The corpus SHALL include a `corpus-manifest.json` file.

The manifest SHOULD include corpus name, corpus version, release date, number of conceptual Goals, number of GB-FDO fixtures, MRC counts, category counts, profile references, checksums, license, and provenance summary.

---

# 12. Corpus Usage Support

The corpus MAY support implementation testing, reproducibility studies, interoperability studies, and Alignment Engine comparison activities.

The corpus specification does not define evaluation methodologies, scoring frameworks, benchmark truth models, adjudication procedures, or experimental protocols.

---

# 13. Governance Model

## 13.1 Versioning

The corpus SHALL use semantic versioning.

Recommended version pattern:

```text
MAJOR.MINOR.PATCH
```

Major version changes SHOULD indicate changes that affect corpus comparability.

Minor version changes SHOULD indicate backward-compatible corpus expansion or added metadata.

Patch version changes SHOULD indicate corrections that do not alter corpus interpretation.

## 13.2 Stable Corpus Releases

The corpus SHOULD distinguish working drafts, pilot releases, alpha releases, beta releases, and stable corpus releases.

Stable corpus releases SHALL be immutable after publication except for clearly documented errata.

## 13.3 Identifier Stability

Once released in a stable corpus version, conceptual Goal identifiers SHALL NOT be reassigned.

GB-FDO variant identifiers SHALL NOT be reassigned.

Deprecated Goals SHALL remain in the corpus history and SHALL NOT be silently replaced.

## 13.4 Provenance

Each corpus release SHALL include provenance metadata documenting release date, curators, reviewers, Goal construction method, review method, changes from prior version, and known limitations.

## 13.5 Contribution Rules

New Goal contributions SHOULD include:

* proposed goal statement;
* primary computational-function category;
* rationale for inclusion;
* MRC-1, MRC-2, and MRC-3 GB-FDO fixture variants;
* confirmation that Goal Representation Type and Goal Representation content are fixed across variants;
* confirmation that the Goal remains within the abstraction boundary;
* review notes.

Contributions SHOULD be reviewed for one-goal-per-GB-FDO compliance, MRC separation, fixture variant integrity, fixed DFSK Goal Representation across MRC variants, scientific usefulness, abstraction-boundary compliance, category balance, absence of evaluation answer keys in runtime metadata, and consistency with GARI scope.

## 13.6 Expansion Rules

Corpus expansion SHOULD preserve corpus stability.

New Goals SHOULD be added in new minor versions unless they materially alter corpus interpretation.

Corrections to existing Goals SHOULD be documented in changelogs.

Corrections that alter corpus interpretation SHOULD trigger a new major or minor version, not a silent patch.

## 13.7 Review Roles

Corpus governance SHOULD include at least the following review roles:

| Role | Responsibility |
|---|---|
| Corpus Curator | Drafts and maintains Goal fixtures. |
| Metadata Reviewer | Assesses MRC separation and metadata quality. |
| Abstraction Boundary Reviewer | Assesses compliance with the computational-function abstraction boundary. |
| GARI Conformance Reviewer | Assesses consistency with GARI specifications. |

A single person MAY serve multiple roles during early pilot work.

Stable releases SHOULD include independent review where practical.

---

# 14. Canonical Pilot Corpus Recommendation

## 14.1 Pilot Size

The first construction step SHOULD be a pilot corpus of:

```text
12 conceptual Goals
36 GB-FDO fixtures
```

The pilot corpus should validate the corpus architecture before full-scale construction.

## 14.2 Pilot Category Coverage

The pilot SHOULD include representative Goals from:

1. Prediction;
2. Classification;
3. Recommendation;
4. Calculation.

A balanced 12-Goal pilot SHOULD include approximately three conceptual Goals per category.

## 14.3 Pilot Goal Candidate Pattern

The pilot corpus SHOULD construct abstract computational-function Goals rather than domain-specific biomedical Goals.

Candidate patterns include:

| ID | Category | Abstract Goal Statement |
|---|---|---|
| gari-gb-goal-0001 | Prediction | Predict a future event from specified inputs. |
| gari-gb-goal-0002 | Prediction | Predict a future state value from specified inputs. |
| gari-gb-goal-0003 | Prediction | Predict whether a future condition will occur. |
| gari-gb-goal-0004 | Classification | Classify an item into one of several categories. |
| gari-gb-goal-0005 | Classification | Classify an entity as satisfying or not satisfying a condition. |
| gari-gb-goal-0006 | Classification | Classify an observation pattern into a predefined class. |
| gari-gb-goal-0007 | Recommendation | Recommend one or more candidate actions from specified inputs. |
| gari-gb-goal-0008 | Recommendation | Recommend a preferred option from available alternatives. |
| gari-gb-goal-0009 | Recommendation | Recommend a next step in a structured process. |
| gari-gb-goal-0010 | Calculation | Calculate a numeric value from specified parameters. |
| gari-gb-goal-0011 | Calculation | Calculate a score from a defined input set. |
| gari-gb-goal-0012 | Calculation | Calculate a derived quantity from structured inputs. |

These are candidate patterns for corpus construction.

They should be reviewed before being locked.

---

# 15. Acceptance Criteria for the Corpus

## 15.1 Structural Acceptance Criteria

The corpus SHALL pass structural validation confirming that:

* each conceptual Goal has exactly three MRC variants;
* each GB-FDO variant has a PID;
* each GB-FDO variant has type `GB-FDO` or equivalent declared type recognized by the profile;
* each GB-FDO variant has a profile reference;
* each GB-FDO variant has metadata;
* each GB-FDO variant has a bitstream reference;
* each conceptual Goal is represented consistently across MRC variants;
* each MRC variant is represented as a separate GB-FDO fixture;
* each MRC variant contains the same DFSK Goal Representation content for the same conceptual Goal;
* all checksums are present;
* all manifest entries resolve to existing files.

## 15.2 Scientific Acceptance Criteria

The corpus SHOULD pass scientific review confirming that:

* Goals are realistic at the computational-function abstraction level;
* category assignments are plausible;
* MRC differences represent distinct metadata representation systems while preserving the same conceptual Goal and the same DFSK Goal Representation;
* the corpus avoids narrow biomedical field semantics as the primary source of variation;
* controlled Goal variability is intentionally represented where useful;
* evaluation materials are separated from runtime metadata;
* corpus design supports reproducible comparison.

## 15.3 GARI Compatibility Acceptance Criteria

The corpus SHALL pass compatibility review confirming that:

* each GB-FDO represents exactly one Goal;
* Goal Representation Type and Goal Representation content remain fixed across MRC fixture variants for the same conceptual Goal;
* metadata and bitstreams are distinct;
* payloads are not required in Input Packages;
* corpus fixtures can participate in Layers with CBKB-FDO fixtures;
* corpus fixtures can be loaded by GARI implementations for testing;
* the corpus does not require GARI to generate, repair, enrich, or modify metadata.

---

# 16. Future Extensibility

## 16.1 CBKB-FDO Corpus Pairing

The GB-FDO corpus SHOULD eventually be paired with a canonical CBKB-FDO corpus.

The paired corpora should support controlled alignment investigations involving MRC sensitivity, engine comparison, reproducibility studies, interoperability studies, and Layer fixture construction.

Any evaluation of Alignment Engine outputs SHALL be specified outside this GB-FDO corpus design specification.

## 16.2 Layer Fixtures

Future work SHOULD define canonical Layer fixtures combining GB-FDO and CBKB-FDO corpora.

Layer fixtures SHOULD support small implementation tests, medium corpus runs, stress tests, and reproducibility studies.

## 16.3 Saved Run Packages

Future work MAY define saved run packages containing Layer Image, Input Package, Output Package, Alignment Result Graph, provenance metadata, reproducibility information, and engine profile.

Evaluation annotations SHALL remain external to the corpus specification.

## 16.4 Domain Extensions

Future corpus extensions MAY introduce domain-specific Goals.

Such extensions SHOULD be separately versioned and SHOULD NOT destabilize the canonical abstraction-first GARI v1.0 corpus.

## 16.5 Profile Extensions

Future work MAY define additional profile references for richer metadata representations or alternative Goal Representation Types.

Profile extensions SHOULD preserve the core GARI requirement that each GB-FDO represent exactly one Goal.

Future corpora MAY vary Goal Representation Type or Goal Representation content, but such corpora would study a different scientific variable than the canonical GARI v1.0 GB-FDO corpus.

---

# 17. Summary of Recommendations

The canonical GARI v1.0 GB-FDO corpus SHOULD adopt the following design decisions:

1. Treat the corpus as a first-class scientific asset.
2. Organize the corpus around conceptual Goals, not isolated GB-FDO files.
3. Represent each conceptual Goal at MRC-1, MRC-2, and MRC-3.
4. Use separate GB-FDO fixture variants for each Metadata Representation Condition.
5. Use Metadata Representation Condition, not Metadata Expressiveness, as the primary corpus-design variable.
6. Use MRC-1 Parameter Item Metadata, MRC-2 FHIR Resource Metadata, and MRC-3 FHIR RDF Metadata as the initial corpus conditions.
7. Use 120 conceptual Goals for the stable v1.0 canonical corpus.
8. Produce 360 GB-FDO fixtures for the stable v1.0 canonical corpus.
9. Begin with a 12-Goal pilot corpus.
10. Use Prediction, Classification, Recommendation, and Calculation as the canonical computational-function categories.
11. Define Prediction specifically as future-oriented estimation.
12. Avoid narrow biomedical field semantics as the primary source of variation.
13. Preserve strict separation between runtime metadata and evaluation materials.
14. Use stable identifiers and semantic versioning.
15. Preserve corpus stability through immutable stable releases.
16. Pair the GB-FDO corpus with a future canonical CBKB-FDO corpus.
17. Use the corpus to study alignment behavior, not knowledge application success.
18. Treat Metadata Representation Condition as a fixture property, not a GARI runtime concept.
19. Hold DFSK Goal Representation Type and Goal Representation content fixed across MRC variants in this canonical corpus.
20. Treat the corpus as a scientific fixture library that does not prescribe investigator experimental designs.
21. Preserve realistic Goal variability where scientifically useful.
22. Recognize that the corpus curates Goals but does not normalize reality.
23. Treat Metadata Representation Condition as the primary corpus-design variable and Metadata Representation Systems as the representational mechanisms through which those conditions are instantiated.

---

# Appendix A — Minimal GB-FDO Variant Checklist

Each GB-FDO variant SHOULD satisfy the following checklist:

```text
[ ] PID present
[ ] Type present
[ ] Profile Reference present
[ ] Metadata present
[ ] Bitstream Reference present
[ ] Exactly one conceptual Goal represented
[ ] DFSK Goal Representation present or referenced
[ ] Goal Representation Type fixed according to corpus design
[ ] MRC assignment recorded in corpus governance metadata
[ ] Conceptual Goal identifier linked
[ ] Corpus version declared
[ ] Checksum available
[ ] Runtime metadata excludes evaluation answer keys
```

---

# Appendix B — Recommended Corpus Manifest Skeleton

```json
{
  "corpusName": "GARI v1.0 Canonical GB-FDO Corpus",
  "corpusVersion": "1.0.0",
  "releaseStatus": "draft",
  "releaseDate": "2026-06-20",
  "gariVersion": "1.0",
  "conceptualGoalCount": 120,
  "gbFdoFixtureCount": 360,
  "metadataRepresentationConditions": [
    "MRC-1",
    "MRC-2",
    "MRC-3"
  ],
  "computationalFunctionCategories": [
    "prediction",
    "classification",
    "recommendation",
    "calculation"
  ],
  "profiles": [
    "gari-gb-fdo-profile-v1",
    "gari-gb-fdo-fhir-profile",
    "gari-gb-fdo-fhir-rdf-profile"
  ],
  "goals": [
    {
      "conceptualGoalId": "gari-gb-goal-0001",
      "canonicalGoalStatement": "Predict a future event from specified inputs.",
      "primaryCategory": "prediction",
      "goalRepresentationType": "DFSK",
      "goalRepresentationContentRule": "fixed across variants",
      "variants": [
        {
          "mrc": "MRC-1",
          "pid": "urn:gari:v1:gbfdo:k3f7q",
          "path": "goals/gari-gb-goal-0001/mrc1/gbfdo.json"
        },
        {
          "mrc": "MRC-2",
          "pid": "urn:gari:v1:gbfdo:t9m2x",
          "path": "goals/gari-gb-goal-0001/mrc2/gbfdo.json"
        },
        {
          "mrc": "MRC-3",
          "pid": "urn:gari:v1:gbfdo:a6r4v",
          "path": "goals/gari-gb-goal-0001/mrc3/gbfdo.json"
        }
      ]
    }
  ]
}
```

---

# Appendix C — First Construction Pass

The next practical construction pass SHOULD produce the pilot corpus.

That pass SHOULD create:

```text
GARI-v1.0-Canonical-GBFDO-Corpus-Pilot/
```

containing:

* 12 conceptual Goal records;
* 36 GB-FDO fixtures;
* 3 MRC profile references;
* one corpus manifest;
* validation schemas;
* README and version files.

The pilot corpus SHOULD then be audited before expansion to the alpha corpus.

---

# Appendix D — WT-008 and WT-009 Reconciliation Summary

WT-008 replaced the prior Metadata Expressiveness framing with Metadata Representation Condition.

WT-009 established that Metadata Representation Conditions are implemented through Metadata Representation Systems.

Metadata representations are unified representational artifacts whose structure, meaning, and machine-processable characteristics are inseparable aspects of the same representation.

The accepted framework treats Metadata Representation Condition (MRC) as the primary corpus-design variable while recognizing Metadata Representation Systems as the representational mechanisms through which those conditions are instantiated.

The accepted WT-008 framework establishes:

* MRC as the primary corpus-design variable;
* MRC-1 as Parameter Item Metadata;
* MRC-2 as FHIR Resource Metadata;
* MRC-3 as FHIR RDF Metadata;
* Prediction, Classification, Recommendation, and Calculation as the canonical computational-function abstraction layer;
* Prediction as future-oriented estimation;
* domain-specific biomedical semantics as outside the primary variation strategy;
* computational-function abstraction as the appropriate semantic level for the initial canonical corpus.

This reconciliation substantially changes the scientific framing of the canonical corpus and supersedes prior language that treated metadata expressiveness as the primary variable.


---

# Appendix E — WT-010 Reconciliation Summary

WT-010 established the Computational Function Framework used by the canonical corpus.

Prediction, Classification, Recommendation, and Calculation are scientifically grounded corpus-design constructs adopted to support investigation of Metadata Representation Conditions as instantiated through Metadata Representation Systems. They are not asserted to constitute a complete taxonomy of computational functions or a normative ontology of computation.
