# GARI v1.0 Implementation Specification

Version: GARI v1.0  
Status: Implementation Publication Candidate  
Normative Relative To: GARI-v1.0-Specification-Release-Candidate-Reconciled.md

---

# Document Status

This document is the implementation companion to the GARI v1.0 Release Candidate.

The Release Candidate remains the authoritative architectural specification for GARI v1.0.

This Implementation Specification translates the approved GARI architecture into software-engineering requirements suitable for implementation by human developers, AI-assisted coding systems, Codex, and future engineering teams.

If a conflict exists between this document and the Release Candidate, the Release Candidate SHALL take precedence.

This document SHALL NOT be interpreted as redefining GARI concepts, principles, runtime behavior, scientific scope, or architectural intent.

---

# Implementation Specification Table of Contents

1. Introduction  
2. Relationship to the Release Candidate  
3. Implementation Architecture  
4. Runtime Components  
5. User Interface Architecture  
6. State Model Realization  
7. Data Models  
8. Validation Rules  
9. Alignment Engine Integration  
10. Saved Run Package Realization  
11. Error Handling and Logging  
12. Testing Requirements  
13. Reference Implementation Guidance  
14. Conformance Requirements  
Appendix A — Suggested Repository Structure  
Appendix B — Suggested API Interfaces  
Appendix C — Example Runtime Workflows  

---

# 1. Introduction

## 1.1 Purpose

The purpose of this document is to specify how software should be constructed to faithfully realize GARI v1.0.

The Release Candidate answers what GARI is.

This Implementation Specification answers how a conformant GARI v1.0 web application should be engineered.

The Implementation Specification is intended to reduce ambiguity for implementers while preserving the architectural flexibility intentionally retained by the Release Candidate.

## 1.2 Implementation Goal

A conformant GARI v1.0 implementation SHALL provide a web application capable of:

1. loading or registering one Alignment Engine;
2. loading Goal-bearing FAIR Digital Objects and CBK-bearing FAIR Digital Objects;
3. establishing a valid Layer;
4. generating a metadata-only Input Package from the established Layer;
5. executing one Alignment Engine against one Input Package;
6. receiving one Output Package produced by an Alignment Engine for the completed Alignment Run;
7. exposing the Alignment Result Graph as the authoritative result object;
8. preserving provenance sufficient for inspection, comparison, interpretation, and reproducibility;
9. allowing the user to explicitly save a completed run as a Saved Run Package;
10. allowing the user to clear active results from the runtime environment.

## 1.3 Implementation Non-Goals

A GARI v1.0 implementation SHALL NOT implement functionality outside the approved GARI scope.

In particular, a GARI implementation SHALL NOT:

1. execute CBK Artifacts as knowledge-application tools;
2. apply knowledge to operational or real-world outcomes;
3. generate, repair, enrich, or modify FDO metadata for alignment use;
4. implement clinical decision support;
5. implement workflow orchestration;
6. define Alignment Engine algorithms;
7. prescribe how an Alignment Engine internally identifies alignments;
8. require backend infrastructure unless selected by an implementation team;
9. require a database unless selected by an implementation team;
10. require cloud deployment unless selected by an implementation team.

## 1.4 Intended Implementers

This document is written for:

* software engineers;
* web application developers;
* AI coding agents;
* Codex-style implementation systems;
* future maintainers;
* implementation auditors;
* reproducibility reviewers.

The audience is assumed to be familiar with the Release Candidate.

This document therefore avoids restating large portions of the Release Candidate and instead expresses implementation requirements derived from it.

## 1.5 Requirement Language

The terms SHALL, SHALL NOT, SHOULD, SHOULD NOT, and MAY are used as follows:

* SHALL indicates a mandatory implementation requirement derived from the Release Candidate.
* SHALL NOT indicates prohibited implementation behavior.
* SHOULD indicates recommended implementation behavior that supports faithful realization but may vary across conformant implementations.
* MAY indicates permitted implementation flexibility.
* Informative indicates guidance that is useful but not required for conformance.

---

# 2. Relationship to the Release Candidate

## 2.1 Authority Rule

The Release Candidate is the authoritative architectural specification for GARI v1.0.

This Implementation Specification is normative only as an engineering baseline relative to that architecture.

If this document appears to redefine a concept, cardinality, principle, runtime behavior, package relationship, or user-interaction requirement, the Release Candidate SHALL govern.

## 2.2 Derivation Rule

Every mandatory implementation requirement in this document SHALL be traceable to one or more architectural requirements in the Release Candidate.

Implementation requirements MAY add engineering specificity when the Release Candidate defines an architectural requirement but does not prescribe a software realization.

Implementation requirements SHALL NOT add scientific functionality.

## 2.3 Distinction Between Architecture and Realization

The Release Candidate defines GARI concepts such as Layer, Layer Image, Alignment Run, Input Package, Output Package, Alignment Result Graph, and Saved Run Package.

This document defines software representations of those concepts and artifacts.

Software representations SHALL NOT replace the normative definitions in the Release Candidate.

For example:

* an implementation object named `LayerState` may represent the current runtime Layer;
* an implementation object named `LayerImage` may serialize a representation of an established Layer;
* an implementation object named `SavedRunArchive` may implement a downloadable archive.

These implementation artifacts exist to realize the architecture and SHALL NOT be treated as new GARI concepts.

## 2.4 Technology Neutrality

The implementation architecture defined in this document is technology-neutral.

A conformant implementation MAY use React, TypeScript, Vite, Zustand, JSZip, Zod, Playwright, Vitest, or other technologies.

No specific technology stack is required for conformance unless explicitly selected by an implementation project.

Technology recommendations in this document are informative.

## 2.5 Preservation of Architectural Boundaries

A GARI implementation SHALL preserve the following architectural boundaries:

1. GARI is a scientific instrument, not a knowledge application platform.
2. GARI investigates alignment only.
3. GARI operates on pre-existing metadata.
4. GARI does not generate, repair, enrich, or modify metadata for alignment use.
5. Alignment Engines are black-box computational components.
6. Each Alignment Run uses exactly one Alignment Engine.
7. Each Alignment Run operates against exactly one Layer.
8. Each Output Package contains exactly one Alignment Result Graph.
9. Save Run occurs only through explicit user action.
10. Clear Result removes active result artifacts from the runtime environment.

---

# 3. Implementation Architecture

## 3.1 Architectural Style

A GARI v1.0 implementation SHOULD be organized as a modular web application with clear separation among:

1. user interface components;
2. runtime state management;
3. FDO loading and parsing;
4. Layer management;
5. Input Package generation;
6. Alignment Engine integration;
7. run orchestration;
8. result inspection;
9. Saved Run Package generation;
10. validation;
11. logging and diagnostics.

This separation supports auditability, testability, and future replacement of implementation technologies.

## 3.2 Required Software Boundaries

A conformant implementation SHALL distinguish at least the following software responsibility areas.

### 3.2.1 User Interface Boundary

The user interface boundary SHALL present GARI concepts directly to the user.

The interface SHOULD use concept-revealing labels such as:

* Load Alignment Engine;
* Load Layer;
* Layer Established;
* Run Alignment;
* Alignment Result Graph;
* Save Run;
* Clear Result.

The interface SHALL NOT present GARI primarily as a knowledge execution system, decision-support tool, or AI assistant.

### 3.2.2 Runtime State Boundary

The runtime state boundary SHALL maintain current application state, including:

* loaded engine profile;
* loaded GB-FDO references;
* loaded CBKB-FDO references;
* Layer establishment status;
* active Input Package during execution;
* active Output Package after run completion;
* active Alignment Result Graph;
* unsaved result status;
* saved state status;
* runtime errors.

### 3.2.3 FDO Boundary

The FDO boundary SHALL be responsible for loading, parsing, and minimally validating FDO structures recognized by GARI.

The FDO boundary SHALL NOT modify FDO metadata for alignment use.

### 3.2.4 Layer Boundary

The Layer boundary SHALL determine whether the currently loaded GB-FDOs and CBKB-FDOs establish a valid Layer.

The Layer boundary SHALL preserve the architectural rule that Layers are conceptual constructs and do not possess independent persistent identity.

### 3.2.5 Engine Boundary

The engine boundary SHALL integrate the selected Alignment Engine as a black-box component.

The engine boundary SHALL validate the presence of an Alignment Engine Profile and SHALL pass an Input Package to the engine for execution.

The engine boundary SHALL NOT inspect, constrain, or redefine the internal alignment algorithm of the engine.

### 3.2.6 Packaging Boundary

The packaging boundary SHALL represent, minimally validate, preserve, package, and present engine-produced Output Packages and Saved Run Packages.

The packaging boundary SHALL NOT construct Alignment Engine result content.

The packaging boundary SHALL preserve the Output Package when creating a Saved Run Package.

Saved Run Package augmentation SHALL NOT modify the preserved Output Package.

## 3.3 Recommended Module Responsibilities

A practical implementation SHOULD include modules corresponding to the following responsibilities:

| Module | Primary Responsibility |
|---|---|
| `fdo-loader` | Load files, folders, or archives containing FDOs. |
| `fdo-validator` | Perform minimum GARI validation. |
| `layer-manager` | Track GB-FDO and CBKB-FDO membership and establishment status. |
| `layer-image-builder` | Generate a Layer Image from the established Layer. |
| `input-package-builder` | Generate Input Packages from Layer Images. |
| `engine-registry` | Load and replace Alignment Engine profiles. |
| `engine-adapter` | Execute an Alignment Engine through a stable implementation interface. |
| `run-orchestrator` | Enforce one-engine, one-layer, one-run execution. |
| `result-manager` | Store active Output Package and Alignment Result Graph after completion. |
| `saved-run-builder` | Generate Saved Run Packages from completed runs. |
| `state-machine` | Enforce state transitions and control enablement. |
| `logger` | Capture implementation diagnostics without violating engine black-box boundaries. |

Module names are informative.

The responsibilities are implementation requirements.

## 3.4 Deployment Architecture

A GARI v1.0 implementation MAY be entirely browser-based.

A GARI v1.0 implementation MAY use a backend service if desired.

Use of a backend service SHALL NOT change GARI architectural behavior.

If a backend service is used, the implementation SHALL preserve:

* user-controlled persistence;
* metadata-only Input Packages;
* payload exclusion from Input Packages;
* black-box engine treatment;
* explicit Save Run behavior;
* Clear Result behavior.

---

# 4. Runtime Components

## 4.1 Component Overview

A conformant implementation SHALL realize the following runtime components:

1. Application Shell;
2. Alignment Engine Manager;
3. FDO Loader;
4. Layer Manager;
5. Input Package Builder;
6. Alignment Run Orchestrator;
7. Output Package Manager;
8. Result Inspector;
9. Saved Run Package Builder;
10. Error and Logging Service.

These components MAY be implemented as separate modules, services, classes, functions, stores, or equivalent architectural units.

## 4.2 Application Shell

The Application Shell SHALL coordinate the user-visible workflow.

The Application Shell SHALL expose the current state of the instrument.

The Application Shell SHALL not contain Alignment Engine algorithm logic.

## 4.3 Alignment Engine Manager

The Alignment Engine Manager SHALL support loading one Alignment Engine Profile.

Loading a new Alignment Engine SHALL replace any previously loaded Alignment Engine.

The Alignment Engine Manager SHALL expose:

* engine identity;
* engine version;
* supported input types if declared;
* engine configuration metadata if supplied;
* engine readiness status;
* profile validation status.

## 4.4 FDO Loader

The FDO Loader SHALL allow users to load FDOs into the runtime environment.

An implementation MAY support:

* individual file upload;
* folder upload;
* drag-and-drop upload;
* archive upload;
* sample data loading.

The FDO Loader SHALL preserve the distinction between metadata and payload bitstreams.

The FDO Loader SHALL NOT use payload bitstreams to construct Input Package metadata.

## 4.5 Layer Manager

The Layer Manager SHALL maintain the active collection of GB-FDOs and CBKB-FDOs.

The Layer Manager SHALL determine whether a valid Layer has been established.

A Layer SHALL be considered established when at least one GB-FDO and at least one CBKB-FDO are present.

When an Alignment Run begins, the implementation SHALL create a Layer Image representing the established Layer used for that run.

The Layer Image SHALL remain associated with the Alignment Run for its duration.

## 4.6 Input Package Builder

The Input Package Builder SHALL generate an Input Package from the Layer Image associated with an established Layer.

The Input Package Builder SHALL include metadata and references required for Alignment Engine execution.

The Input Package Builder SHALL exclude payload bitstreams.

The Input Package Builder SHALL associate each Input Package with exactly one Layer Image.

## 4.7 Alignment Run Orchestrator

The Alignment Run Orchestrator SHALL enforce run execution rules.

It SHALL ensure that:

1. exactly one Alignment Engine is selected for a run;
2. exactly one established Layer is used for a run;
3. exactly one Input Package is supplied to the engine;
4. Layer membership remains fixed during execution;
5. the selected Alignment Engine produces exactly one Output Package upon successful completion;
6. the resulting Output Package contains exactly one Alignment Result Graph.

The Run Orchestrator SHALL prevent concurrent mutation of the active Layer during execution.

## 4.8 Output Package Manager

Alignment Engines produce Output Packages.

GARI receives, minimally validates, preserves, packages, and presents Output Packages.

GARI SHALL NOT construct Alignment Engine result content.

The Output Package Manager SHALL store the active Output Package after successful run completion.

The Output Package Manager SHALL make the Alignment Result Graph available to the Result Inspector.

The Output Package Manager SHALL preserve Engine Notes separately from the Alignment Result Graph.

The Output Package Manager SHALL support negative alignment results as valid results.

## 4.9 Result Inspector

The Result Inspector SHALL provide user-visible inspection of the active Output Package.

At minimum, the Result Inspector SHALL expose:

* Alignment Result Graph presence;
* per-goal alignment outcomes where represented;
* CBKB-FDO references where represented;
* Constructed Realizations where represented;
* provenance metadata;
* Layer Image;
* optional Engine Notes if provided.

The Result Inspector SHALL NOT treat Engine Notes as authoritative result graph content.

## 4.10 Saved Run Package Builder

The Saved Run Package Builder SHALL create a Saved Run Package only after successful Alignment Run completion.

Save Run SHALL only be available when an Output Package exists for the current Alignment Run.

The Saved Run Package Builder SHALL derive each Saved Run Package from exactly one Output Package.

The Saved Run Package Builder SHALL preserve the same Layer Image contained in the corresponding Output Package.

## 4.11 Error and Logging Service

The Error and Logging Service SHALL capture implementation-level events relevant to debugging and audit.

Logging SHALL NOT expose or redefine internal Alignment Engine reasoning unless the engine explicitly returns such information as Engine Notes or supporting artifacts.

---

# 5. User Interface Architecture

## 5.1 User Interface Philosophy

The user interface SHALL present GARI as a scientific instrument.

The interface SHALL emphasize inspection, evaluation, comparison, reproducibility, clarity, and restraint.

The interface SHALL NOT present GARI as a general-purpose AI assistant, workflow executor, clinical tool, or knowledge-application platform.

## 5.2 Required Interface Regions

A conformant implementation SHALL provide interface facilities for:

1. Alignment Engine Management;
2. Layer Management;
3. Alignment Run Controls;
4. Result Inspection;
5. Save Run Controls;
6. Clear Result Controls;
7. Status and Diagnostics.

These facilities MAY be organized as panels, cards, tabs, pages, or other user interface structures.

## 5.3 Alignment Engine Management Interface

The Alignment Engine Management interface SHALL allow the user to load or select an Alignment Engine.

The interface SHALL display at least:

* engine loaded/not loaded status;
* engine name if available;
* engine version if available;
* profile validation status;
* replacement behavior when a new engine is loaded.

The interface SHOULD make clear that only one Alignment Engine can be active for a run.

## 5.4 Layer Management Interface

The Layer Management interface SHALL allow the user to load GB-FDOs and CBKB-FDOs.

The interface SHALL display:

* number of loaded GB-FDOs;
* number of loaded CBKB-FDOs;
* Layer establishment status;
* validation warnings or errors;
* clear distinction between metadata and payload availability where relevant.

The interface SHOULD label the valid condition as Layer Established.

## 5.5 Alignment Run Controls

The Run control SHALL only be enabled when:

1. one Alignment Engine is loaded and ready;
2. a Layer is established;
3. no Alignment Run is currently executing;
4. state constraints allow a new run.

During execution, Run SHALL be disabled.

The implementation MAY allow a new Alignment Run after completion of a previous Alignment Run if state constraints and unsaved result protection are satisfied.

## 5.6 Result Inspection Interface

After run completion, the interface SHALL expose the active Output Package and the Alignment Result Graph.

The interface SHALL identify the Alignment Result Graph as the authoritative scientific result object.

The interface SHALL allow negative results to be viewed as valid results.

The interface SHALL distinguish Engine Notes from Alignment Result Graph content.

## 5.7 Save Run Interface

Save Run SHALL only be available when an Output Package exists for the current Alignment Run.

Save Run SHALL create a Saved Run Package through explicit user action.

The interface SHALL NOT automatically save Alignment Run outputs as a substitute for user-controlled persistence.

The interface SHOULD provide feedback after successful package creation.

## 5.8 Clear Result Interface

Clear Result SHALL only be available when an Output Package exists for the current Alignment Run.

Clear Result SHALL remove active result artifacts from the runtime environment.

Clear Result SHALL NOT delete previously created Saved Run Packages.

Implementations SHOULD warn users before clearing unsaved Alignment Run results.

## 5.9 Status and Diagnostics Interface

The interface SHOULD display concise implementation status messages, including:

* engine loading status;
* Layer establishment status;
* validation failures;
* run execution status;
* run completion status;
* save completion status;
* clear result status.

Diagnostics SHOULD support user understanding without exposing unnecessary implementation complexity.

---

# 6. State Model Realization

## 6.1 Purpose

This chapter translates the Release Candidate state model into software states, transitions, guards, control enablement rules, and error-handling requirements.

## 6.2 Required Runtime States

A conformant implementation SHALL realize the following user-visible states or equivalent internal states:

| State ID | State Name | Definition |
|---|---|---|
| S0 | Landed | Initial application state. No valid Layer is established and no active result exists. |
| S1 | Engine Loaded | One Alignment Engine has been loaded, but a valid Layer may not yet be established. |
| S2 | Layer Established | At least one GB-FDO and one CBKB-FDO are present. |
| S3 | Ready To Run | One Alignment Engine is loaded and a valid Layer is established. |
| S4 | Run Executing | One Alignment Engine is executing against one Input Package generated from one established Layer. |
| S5 | Run Complete | The Output Package has been produced for the current Alignment Run. |
| S6 | Saved | A Saved Run Package has been created from the active Output Package. |
| S7 | Result Cleared | Active result artifacts have been removed from the runtime environment. |
| SE | Error | A recoverable or non-recoverable runtime error has occurred. |

Implementations MAY combine S1, S2, and S3 in the user interface if control enablement remains correct.

## 6.3 State Transition Table

| From | User or System Action | Guard Condition | To |
|---|---|---|---|
| S0 | Load Engine | Engine profile parse succeeds | S1 |
| S0 | Load FDOs | Valid minimum Layer exists | S2 |
| S1 | Load FDOs | Valid minimum Layer exists | S3 |
| S2 | Load Engine | Engine profile parse succeeds | S3 |
| S3 | Run Alignment | Engine ready and Layer established | S4 |
| S4 | Run succeeds | Output Package produced | S5 |
| S4 | Run fails | Error captured | SE |
| S5 | Save Run | Output Package exists | S6 |
| S5 | Clear Result | Output Package exists and user confirms if unsaved | S7 |
| S6 | Clear Result | Output Package exists | S7 |
| S7 | Load or retain Engine and Layer | Engine and Layer available | S3 |
| SE | Recover | Error resolved according to implementation rules | Prior valid state or S0 |

## 6.4 Control Enablement Rules

### 6.4.1 Load Engine

Load Engine SHALL be available in S0, S1, S2, S3, S5, S6, and S7.

Loading a new Alignment Engine SHALL replace any previously loaded Alignment Engine.

If an active unsaved result exists, implementations SHOULD warn before engine replacement if replacement would make the active result context confusing or unrecoverable.

### 6.4.2 Load FDOs

Load FDO controls SHALL be available before run execution.

Load FDO controls SHALL be disabled or constrained during S4 Run Executing.

An implementation MAY allow additional FDO loading after S5 or S6, but SHALL protect unsaved results if the action would clear, obscure, or supersede active results.

### 6.4.3 Run Alignment

Run Alignment SHALL be enabled only in S3 Ready To Run or equivalent state.

Run Alignment SHALL be disabled when:

* no Alignment Engine is loaded;
* no valid Layer is established;
* an Alignment Run is currently executing;
* required minimum validation has failed;
* unsaved result protection requires user decision before proceeding.

### 6.4.4 Save Run

Save Run SHALL be enabled only when an Output Package exists for the current Alignment Run.

Save Run SHALL be disabled in S0, S1, S2, S3, S4, and SE unless the implementation can safely preserve a completed Output Package.

### 6.4.5 Clear Result

Clear Result SHALL be enabled only when an Output Package exists for the current Alignment Run.

Clear Result SHALL remove active result artifacts from runtime state.

Clear Result SHALL NOT remove loaded FDOs or loaded Alignment Engine unless the implementation explicitly provides a broader reset action distinct from Clear Result.

## 6.5 Unsaved Result Protection

A completed run whose Output Package has not been saved SHALL be treated as an unsaved result.

Before clearing or superseding an unsaved result, the implementation SHOULD warn the user.

The warning SHOULD identify the consequence clearly:

* the active Output Package will be removed from the runtime environment;
* previously created Saved Run Packages will not be affected;
* unsaved run results may be lost if not saved.

## 6.6 Error State Realization

Errors SHALL be represented without violating GARI architectural boundaries.

For example:

* invalid FDO metadata is a loading or validation error;
* missing engine profile is an engine loading error;
* engine execution failure is a run execution error;
* malformed Output Package is a run completion error;
* failed archive creation is a Save Run error.

An error SHALL NOT be represented as a negative alignment result unless the Alignment Engine successfully produced a valid Alignment Result Graph containing a negative outcome.

---

# 7. Data Models

## 7.1 Purpose

This chapter defines implementation-level data models for constructing conformant software.

These models are implementation artifacts.

They do not replace normative definitions in the Release Candidate.

The examples use JSON-like structures for clarity.

## 7.2 Common Conventions

Implementations SHOULD use stable identifiers for runtime artifacts.

Identifiers SHOULD be represented as strings.

Timestamps SHOULD use ISO 8601 format.

References to FDOs SHOULD preserve original PIDs when available.

Internal runtime identifiers MAY be generated for UI or processing purposes but SHALL NOT be confused with FDO PIDs.

## 7.3 FDO Reference Model

```json
{
  "pid": "string",
  "type": "GB-FDO | CBKB-FDO | string",
  "profileReference": "string",
  "metadata": {},
  "bitstreamReference": "string | null",
  "source": {
    "kind": "file | folder | archive | sample | remote",
    "name": "string"
  },
  "validation": {
    "isRecognized": true,
    "errors": [],
    "warnings": []
  }
}
```

Implementation requirements:

1. `pid` SHALL represent the FDO persistent identifier when available.
2. `type` SHALL represent the declared FDO category.
3. `profileReference` SHALL represent the governing FDO profile reference.
4. `metadata` SHALL contain structured metadata supplied by the FDO.
5. `bitstreamReference` MAY identify payload location, but payload bytes SHALL NOT be included in Input Packages.

## 7.4 Layer State Model

```json
{
  "gbFdos": [],
  "cbkbFdos": [],
  "isEstablished": true,
  "establishedAt": "2026-06-19T00:00:00Z",
  "validation": {
    "errors": [],
    "warnings": []
  }
}
```

Implementation requirements:

1. `gbFdos` SHALL contain one or more GB-FDO references for an established Layer.
2. `cbkbFdos` SHALL contain one or more CBKB-FDO references for an established Layer.
3. `isEstablished` SHALL be true only when at least one GB-FDO and one CBKB-FDO are present.
4. Layer state SHALL NOT be treated as an independently persistent Layer identity.

## 7.5 Layer Image Model

```json
{
  "layerImageId": "string",
  "createdAt": "2026-06-19T00:00:00Z",
  "gbFdoReferences": [
    {
      "pid": "string",
      "type": "GB-FDO",
      "profileReference": "string",
      "metadata": {}
    }
  ],
  "cbkbFdoReferences": [
    {
      "pid": "string",
      "type": "CBKB-FDO",
      "profileReference": "string",
      "metadata": {}
    }
  ]
}
```

Implementation requirements:

1. A Layer Image SHALL represent an established Layer.
2. A Layer Image SHALL include metadata and references derived from loaded FDOs.
3. A Layer Image SHALL NOT introduce metadata used for alignment that is not derived from the established Layer.
4. The Layer Image preserved in the Saved Run Package SHALL be identical to the Layer Image contained in the corresponding Output Package.

## 7.6 Input Package Model

```json
{
  "inputPackageId": "string",
  "runId": "string",
  "createdAt": "2026-06-19T00:00:00Z",
  "engineReference": {
    "name": "string",
    "version": "string",
    "profileReference": "string"
  },
  "layerImage": {},
  "runMetadata": {}
}
```

Implementation requirements:

1. Each Input Package SHALL be associated with exactly one Layer Image.
2. Each Alignment Run SHALL consume exactly one Input Package.
3. Input Packages SHALL exclude payload bitstreams.
4. Input Packages SHALL be generated after Layer establishment and before Alignment Engine execution.

## 7.7 Alignment Engine Profile Model

```json
{
  "engineId": "string",
  "name": "string",
  "version": "string",
  "profileVersion": "string",
  "supportedInputTypes": [],
  "configurationSchema": {},
  "executionInterface": {
    "kind": "local | web-worker | http | custom",
    "entrypoint": "string"
  },
  "metadata": {}
}
```

Implementation requirements:

1. An Alignment Engine SHALL provide an Alignment Engine Profile.
2. The implementation SHALL record engine identity and version in run metadata or provenance.
3. Supported input types SHALL be honored when declared.
4. The profile SHALL NOT be interpreted as revealing engine internal algorithms.

## 7.8 Output Package Model

```json
{
  "outputPackageId": "string",
  "runId": "string",
  "createdAt": "2026-06-19T00:00:00Z",
  "alignmentResultGraph": {},
  "layerImage": {},
  "provenance": {},
  "engineConfigurationMetadata": {},
  "engineNotes": null,
  "supportingArtifacts": []
}
```

Implementation requirements:

1. Each completed Alignment Run SHALL result in exactly one Output Package produced by the selected Alignment Engine.
2. Each Output Package SHALL contain exactly one Alignment Result Graph.
3. Each Output Package SHALL contain a Layer Image.
4. Each Output Package SHALL contain provenance metadata.
5. Engine Notes SHALL be represented separately from the Alignment Result Graph.

## 7.9 Alignment Result Graph Model

```json
{
  "graphId": "string",
  "runId": "string",
  "results": [
    {
      "goalId": "string",
      "alignmentStatus": true,
      "cbkReferences": ["string"],
      "constructedRealizations": [],
      "engineNotesReferences": []
    }
  ],
  "additionalResultMetadata": {}
}
```

Implementation requirements:

1. The Alignment Result Graph SHALL be the authoritative scientific result object.
2. The graph SHALL represent alignment outcomes generated by an Alignment Engine.
3. Negative alignment outcomes SHALL be valid graph content.
4. Supporting artifacts SHALL NOT supersede graph contents.

## 7.10 Provenance Record Model

```json
{
  "runId": "string",
  "executionTimestamp": "2026-06-19T00:00:00Z",
  "engine": {
    "name": "string",
    "version": "string",
    "profileReference": "string"
  },
  "inputPackageId": "string",
  "outputPackageId": "string",
  "layerImageId": "string",
  "generatedArtifacts": []
}
```

Implementation requirements:

1. Provenance SHALL identify the Alignment Run.
2. Provenance SHALL identify the execution timestamp.
3. Provenance SHALL identify the Alignment Engine version.
4. Provenance SHALL associate generated artifacts with the Alignment Run.
5. Provenance SHALL be sufficient to support inspection, comparison, interpretation, and reproducibility.

## 7.11 Saved Run Package Metadata Model

```json
{
  "savedRunPackageId": "string",
  "createdAt": "2026-06-19T00:00:00Z",
  "sourceOutputPackageId": "string",
  "sourceRunId": "string",
  "reproducibilityInformation": {},
  "savedBy": "user"
}
```

Implementation requirements:

1. Each Saved Run Package SHALL be derived from exactly one Output Package.
2. Saved Run Metadata SHALL identify the circumstances of package creation.
3. Reproducibility Information SHALL support reconstruction of the Alignment Run represented by the package.
4. Saved Run Package augmentation SHALL NOT modify the preserved Output Package.

---

# 8. Validation Rules

## 8.1 Purpose

This chapter defines implementation validation behavior.

It distinguishes normative validation required for architectural conformance from implementation convenience validation intended to improve user experience.

## 8.2 Normative Validation

Normative validation SHALL enforce requirements necessary for GARI v1.0 conformance.

Normative validation SHALL include:

1. FDO recognition validation;
2. minimum Layer validation;
3. Alignment Engine Profile validation;
4. Input Package payload exclusion validation;
5. one-engine-per-run validation;
6. fixed Layer during execution validation;
7. Output Package structure validation;
8. Alignment Result Graph presence validation;
9. Save Run precondition validation;
10. Clear Result precondition validation.

## 8.3 Implementation Convenience Validation

Implementation convenience validation MAY be used to improve user experience.

Examples include:

* friendly file type warnings;
* duplicate upload warnings;
* unsupported profile warnings;
* malformed optional field warnings;
* missing display-label warnings;
* archive size warnings;
* browser compatibility warnings.

Convenience validation SHALL NOT become profile policing beyond the requirements of GARI v1.0.

Convenience validation SHALL NOT modify FDO metadata for alignment use.

## 8.4 FDO Loading Validation

When loading an FDO, the implementation SHALL validate the presence or parseability of:

1. PID;
2. Type;
3. Profile Reference;
4. Metadata;
5. Bitstream reference or payload indication.

The implementation SHALL classify recognized FDOs as GB-FDO or CBKB-FDO when the declared type supports such classification.

The implementation SHALL reject or quarantine objects that cannot be recognized as usable GARI FDOs.

## 8.5 Layer Establishment Validation

A Layer SHALL be established only when:

1. at least one GB-FDO is present;
2. at least one CBKB-FDO is present.

The implementation SHALL not require engine-specific validation for Layer establishment.

The implementation MAY display engine compatibility warnings separately from Layer establishment status.

## 8.6 Alignment Engine Loading Validation

The implementation SHALL validate that an Alignment Engine Profile is present and parseable.

The implementation SHOULD validate that required profile fields are available, including:

* engine name;
* engine version;
* execution interface or adapter information;
* supported input types if required by the implementation.

Loading a new Alignment Engine SHALL replace the currently loaded Alignment Engine.

## 8.7 Run Execution Validation

Before run execution, the implementation SHALL validate that:

1. exactly one Alignment Engine is loaded;
2. a Layer is established;
3. an Input Package can be generated;
4. the Input Package excludes payload bitstreams;
5. no run is already executing;
6. state-machine guards allow execution.

## 8.8 Output Package Validation

After engine execution, the implementation SHALL validate that one Output Package exists.

The Output Package SHALL include:

1. exactly one Alignment Result Graph;
2. a Layer Image;
3. provenance metadata;
4. engine configuration metadata.

If the engine returns malformed output, the implementation SHALL report a run completion error rather than silently treating the output as a valid scientific result.

## 8.9 Save Run Validation

Save Run SHALL only proceed when an Output Package exists for the current Alignment Run.

The implementation SHALL validate that the Saved Run Package can include:

1. Alignment Result Graph;
2. Layer Image;
3. Provenance Metadata;
4. Reproducibility Information;
5. Saved Run Metadata.

The implementation SHALL preserve FDOs by reference rather than by payload duplication.

## 8.10 Clear Result Validation

Clear Result SHALL only proceed when an Output Package exists for the current Alignment Run.

If the active result is unsaved, the implementation SHOULD require confirmation before clearing.

Clear Result SHALL remove active result artifacts from the runtime environment.

---

# 9. Alignment Engine Integration

## 9.1 Purpose

This chapter defines how a GARI implementation should integrate Alignment Engines while preserving the black-box engine principle.

## 9.2 Engine Black-Box Boundary

An Alignment Engine SHALL be treated as a black-box computational component.

The implementation SHALL provide an Input Package to the engine and receive an Output Package from the engine.

The implementation SHALL NOT define, inspect, or constrain the internal alignment algorithm beyond interface and package requirements.

## 9.3 Engine Profile Requirement

Each engine SHALL provide an Alignment Engine Profile.

The profile SHOULD include:

* engine identifier;
* engine name;
* engine version;
* profile version;
* supported input types;
* configuration schema if configurable;
* execution interface;
* optional documentation reference.

## 9.4 Engine Replacement Rule

Only one Alignment Engine SHALL be active for a run.

Loading a new Alignment Engine SHALL replace the previously loaded engine.

The interface SHOULD display the active engine clearly.

## 9.5 Engine Adapter Interface

An implementation SHOULD isolate engine invocation behind an adapter interface.

A minimal adapter SHOULD support:

```text
loadProfile(profile)
validateProfile(profile)
execute(inputPackage, configuration)
normalizeOutput(engineOutput)
```

This interface is informative but strongly recommended for maintainability and testability.

## 9.6 Engine Execution Contract

During execution:

1. the implementation SHALL generate one Input Package;
2. the implementation SHALL pass that Input Package to exactly one Alignment Engine;
3. the engine SHALL produce one Output Package;
4. the implementation SHALL receive and validate the Output Package structure;
5. the implementation SHALL enter Run Complete State only after successful Output Package creation.

## 9.7 Engine Configuration Metadata

If an engine is configurable, the configuration used for execution SHALL be recorded as engine configuration metadata within the Output Package.

Configuration metadata SHALL support interpretation and reproducibility.

Configuration metadata SHALL NOT be included in the Input Package unless required by the engine interface and consistent with the Release Candidate.

## 9.8 Engine Notes

Alignment Engines MAY produce Engine Notes.

Engine Notes SHALL be stored separately from the Alignment Result Graph.

The implementation MAY display Engine Notes as explanatory material.

Engine Notes SHALL NOT supersede the Alignment Result Graph.

## 9.9 Engine Failure Handling

If engine execution fails, the implementation SHALL report a run execution error.

An engine failure SHALL NOT be converted into a negative alignment result.

Negative results are valid only when represented in a successfully produced Alignment Result Graph.

---

# 10. Saved Run Package Realization

## 10.1 Purpose

This chapter defines implementation requirements for creating Saved Run Packages.

## 10.2 Save Run Precondition

Save Run SHALL only be available when an Output Package exists for the current Alignment Run.

The implementation SHALL prevent Save Run before successful run completion.

## 10.3 Archive Format

A Saved Run Package SHOULD be implemented as a downloadable archive.

ZIP is recommended for browser-based implementations.

The archive format is informative unless selected by a specific implementation project.

## 10.4 Required Archive Contents

A Saved Run Package archive SHALL contain the following logical contents:

```text
saved-run-package/
  manifest.json
  saved-run-metadata.json
  reproducibility-information.json
  output-package/
    output-manifest.json
    alignment-result-graph.json
    layer-image.json
    provenance.json
    engine-configuration-metadata.json
    engine-notes.json              optional
    supporting-artifacts/          optional
```

File names are recommended implementation names.

The logical contents are required.

## 10.5 Manifest Requirements

The Saved Run Package manifest SHALL identify:

* package identifier;
* source run identifier;
* source Output Package identifier;
* creation timestamp;
* included files;
* required elements;
* optional elements if present.

## 10.6 Output Package Preservation

The Saved Run Package SHALL preserve Output Package information.

Saved Run Package augmentation MAY add reproducibility-supporting information.

Saved Run Package augmentation SHALL NOT modify the preserved Output Package.

## 10.7 Layer Image Preservation

The Layer Image in the Saved Run Package SHALL be identical to the Layer Image contained in the corresponding Output Package.

Creating a Saved Run Package SHALL NOT create a new Layer Image.

## 10.8 Preservation by Reference

FDOs SHALL be preserved by reference rather than by payload duplication.

The Saved Run Package SHOULD include FDO identifiers, profile references, metadata references, and source references sufficient to support reconstruction of the alignment context.

Payload bitstreams SHALL NOT be duplicated into the Saved Run Package unless a future specification explicitly permits or requires it.

## 10.9 Reproducibility Information

Reproducibility Information SHALL support reconstruction of the Alignment Run represented by the package.

It SHOULD include:

* run identifier;
* engine identity and version;
* engine profile reference or embedded profile copy if appropriate;
* engine configuration metadata;
* Layer Image;
* Input Package reference or reconstruction instructions;
* Output Package identifier;
* package creation timestamp;
* implementation version if available.

## 10.10 Download Behavior

The implementation SHOULD provide the user with a downloadable package after successful Save Run.

A successful Save Run SHALL transition the runtime to Saved State or equivalent.

Save Run SHALL not automatically clear the active result.

---

# 11. Error Handling and Logging

## 11.1 Purpose

This chapter defines error handling and implementation logging requirements.

## 11.2 Error Categories

A conformant implementation SHOULD distinguish the following error categories:

1. FDO loading errors;
2. FDO validation errors;
3. Layer establishment errors;
4. Alignment Engine loading errors;
5. Input Package generation errors;
6. Alignment Engine execution errors;
7. Output Package validation errors;
8. Save Run packaging errors;
9. Clear Result errors;
10. unexpected application errors.

## 11.3 User-Facing Error Messages

User-facing error messages SHOULD be concise, concept-revealing, and actionable.

Examples:

* `Layer cannot be established because no CBKB-FDO is loaded.`
* `Run cannot start because no Alignment Engine is loaded.`
* `Save Run is unavailable because no Output Package exists.`
* `The Alignment Engine did not return a valid Output Package.`

Error messages SHALL NOT imply knowledge application or CBK execution.

## 11.4 Internal Diagnostics

The implementation SHOULD maintain internal diagnostic logs for debugging.

Diagnostic logs MAY include:

* timestamps;
* state transitions;
* validation outcomes;
* file loading events;
* engine profile loading events;
* run start and completion events;
* package creation events;
* caught exceptions.

## 11.5 Black-Box Logging Constraint

Implementation logs SHALL preserve the black-box engine boundary.

The implementation MAY log:

* engine invoked;
* input package identifier;
* execution started;
* execution completed;
* execution failed;
* output received;
* output validation status.

The implementation SHALL NOT fabricate or infer engine internal reasoning.

## 11.6 Error Recovery

The implementation SHOULD support recovery from common errors without requiring full application reload.

For example:

* invalid FDOs may be removed;
* malformed engine profiles may be replaced;
* failed runs may return to Ready To Run if engine and Layer remain valid;
* failed Save Run may allow retry if the Output Package remains available.

---

# 12. Testing Requirements

## 12.1 Purpose

Testing SHALL demonstrate that the implementation faithfully realizes the Release Candidate and this Implementation Specification.

Tests SHOULD be automatable.

Acceptance tests SHOULD be written in behavior-oriented form suitable for human developers and AI coding systems.

## 12.2 Unit Testing Expectations

Unit tests SHOULD cover:

* FDO parsing;
* FDO minimum validation;
* Layer establishment logic;
* Layer Image creation;
* Input Package generation;
* payload exclusion;
* engine profile validation;
* state-machine transitions;
* Output Package validation;
* Saved Run Package manifest generation;
* unsaved result detection.

## 12.3 Integration Testing Expectations

Integration tests SHOULD cover:

* loading an engine and Layer in either order;
* running an engine against a valid Layer;
* preserving fixed Layer membership during execution;
* producing and inspecting an Output Package;
* saving a completed run;
* clearing active results;
* replacing an engine;
* handling engine failure;
* handling malformed output.

## 12.4 End-to-End Testing Expectations

End-to-end tests SHOULD verify the full user workflow:

1. user lands in initial state;
2. user loads an Alignment Engine;
3. user loads GB-FDOs and CBKB-FDOs;
4. application establishes a Layer;
5. Run becomes available;
6. user initiates Alignment Run;
7. application receives a valid engine-produced Output Package;
8. application displays Alignment Result Graph;
9. Save Run becomes available;
10. user creates Saved Run Package;
11. Clear Result removes active result artifacts.

## 12.5 Acceptance Tests

### AT-001 — Initial State

Given the application has just loaded,  
Then no Layer SHALL be established,  
And no Output Package SHALL exist,  
And Save Run SHALL be disabled,  
And Clear Result SHALL be disabled.

### AT-002 — Engine Loading

Given no Alignment Engine is loaded,  
When the user loads a valid Alignment Engine Profile,  
Then the engine SHALL become the active Alignment Engine.

### AT-003 — Engine Replacement

Given an Alignment Engine is already loaded,  
When the user loads another valid Alignment Engine Profile,  
Then the new engine SHALL replace the previous engine.

### AT-004 — Layer Establishment

Given at least one GB-FDO is loaded,  
And at least one CBKB-FDO is loaded,  
Then the Layer SHALL be established.

### AT-005 — Invalid Layer

Given only GB-FDOs are loaded,  
Or only CBKB-FDOs are loaded,  
Then the Layer SHALL NOT be established.

### AT-006 — Run Enablement

Given one Alignment Engine is loaded,  
And a Layer is established,  
And no run is executing,  
Then Run Alignment SHALL be enabled.

### AT-007 — Run Disabled Without Engine

Given a Layer is established,  
And no Alignment Engine is loaded,  
Then Run Alignment SHALL be disabled.

### AT-008 — Run Disabled Without Layer

Given an Alignment Engine is loaded,  
And no valid Layer is established,  
Then Run Alignment SHALL be disabled.

### AT-009 — Input Package Payload Exclusion

Given a Layer is established,  
When an Input Package is generated,  
Then payload bitstreams SHALL NOT be included.

### AT-010 — One Engine per Run

Given a run is initiated,  
Then exactly one Alignment Engine SHALL be used for that run.

### AT-011 — Fixed Layer During Execution

Given an Alignment Run is executing,  
Then Layer membership SHALL remain fixed until execution completes or fails.

### AT-012 — Output Package Creation

Given an Alignment Run completes successfully,  
Then exactly one Output Package SHALL exist for the current run.

### AT-013 — Alignment Result Graph Presence

Given an Output Package exists,  
Then it SHALL contain exactly one Alignment Result Graph.

### AT-014 — Save Run Availability

Given no Output Package exists,  
Then Save Run SHALL be disabled.

### AT-015 — Save Run Success

Given an Output Package exists,  
When the user invokes Save Run,  
Then a Saved Run Package SHALL be created.

### AT-016 — Clear Result Availability

Given no Output Package exists,  
Then Clear Result SHALL be disabled.

### AT-017 — Clear Result Behavior

Given an Output Package exists,  
When the user invokes Clear Result,  
Then active result artifacts SHALL be removed from the runtime environment.

### AT-018 — Unsaved Result Protection

Given an Output Package exists and has not been saved,  
When the user attempts to clear or supersede the result,  
Then the implementation SHOULD warn the user before proceeding.

### AT-019 — Negative Result Validity

Given an Alignment Engine returns a valid Alignment Result Graph containing negative alignment outcomes,  
Then the implementation SHALL treat those outcomes as valid scientific results.

### AT-020 — Engine Failure Is Not Negative Result

Given an Alignment Engine fails to execute or returns malformed output,  
Then the implementation SHALL report an execution or validation error,  
And SHALL NOT convert the failure into a negative alignment result.

### AT-021 — Saved Run Package Layer Image Identity

Given a Saved Run Package is created,  
Then the Layer Image preserved in the Saved Run Package SHALL be identical to the Layer Image contained in the corresponding Output Package.

### AT-022 — Saved Run Package Augmentation

Given a Saved Run Package is created,  
Then it MAY contain reproducibility-supporting augmentation,  
And SHALL NOT modify the preserved Output Package.

## 12.6 Regression Testing

Regression tests SHOULD be maintained for every accepted conformance behavior.

Future implementation changes SHALL NOT break mandatory requirements without explicit architectural revision.

---

# 13. Reference Implementation Guidance

## 13.1 Informative Status

This chapter is informative.

It recommends one practical technology stack and implementation approach but does not require it for conformance.

## 13.2 Suggested Technology Stack

A browser-based reference implementation MAY use:

* React for user interface composition;
* TypeScript for type-safe implementation;
* Vite for development and build tooling;
* Zustand or equivalent for runtime state management;
* Zod or equivalent for runtime schema validation;
* JSZip or equivalent for Saved Run Package archive creation;
* Vitest for unit and integration tests;
* Playwright for end-to-end tests;
* Web Workers for local engine execution where appropriate.

A conformant implementation MAY use different technologies.

## 13.3 Suggested Application Structure

A practical implementation SHOULD separate:

* domain models;
* validators;
* state machine;
* UI components;
* engine adapters;
* package builders;
* test fixtures;
* acceptance tests.

## 13.4 Suggested Development Sequence

A practical implementation SHOULD proceed in the following order:

1. define TypeScript or equivalent domain types;
2. implement FDO loading and minimum validation;
3. implement Layer establishment;
4. implement engine profile loading;
5. implement state-machine guards;
6. implement Layer Image generation;
7. implement Input Package generation;
8. implement mock Alignment Engine adapter;
9. implement Output Package validation;
10. implement Result Inspector;
11. implement Save Run Package generation;
12. implement Clear Result;
13. implement acceptance tests;
14. replace mock engine with real engine adapters.

## 13.5 Mock Engine Recommendation

A reference implementation SHOULD include a mock Alignment Engine for testing.

The mock engine SHOULD:

* consume a valid Input Package;
* return a valid Output Package;
* include exactly one Alignment Result Graph;
* optionally produce negative results;
* optionally produce Engine Notes.

The mock engine SHALL be clearly identified as a test engine and SHALL NOT be represented as a scientific alignment method.

---

# 14. Conformance Requirements

## 14.1 Purpose

This chapter distinguishes mandatory conformance requirements from recommended implementation practices and areas of implementation freedom.

## 14.2 Conformance Evidence

An implementation claiming conformance to GARI v1.0 SHOULD be able to demonstrate successful execution of the mandatory behaviors defined by this specification.

GARI does not require a specific certification process, accreditation mechanism, testing authority, scoring methodology, or compliance program.

Methods used to demonstrate conformance remain implementation-specific.

## 14.3 Mandatory Requirements

A conformant GARI v1.0 implementation SHALL satisfy all of the following mandatory requirements.

### 14.3.1 Scope of Mandatory Requirements

Mandatory requirements defined throughout this specification contribute to GARI conformance unless explicitly identified as informative, optional, recommended, illustrative, or implementation-specific.

Conformance SHALL be determined by satisfaction of applicable mandatory requirements regardless of the chapter in which those requirements appear.

Chapter 14 summarizes conformance expectations but does not replace, supersede, or limit mandatory requirements defined elsewhere in this specification.

### CR-001 — Scientific Instrument Identity

The implementation SHALL present and operate GARI as a scientific instrument for metadata-driven alignment investigation.

### CR-002 — Alignment-Only Scope

The implementation SHALL NOT perform knowledge application or execute CBK Artifacts.

### CR-003 — Metadata-Only Input Packages

The implementation SHALL ensure Input Packages contain metadata-only representations and exclude payload bitstreams.

### CR-004 — No Metadata Generation

The implementation SHALL NOT generate, repair, enrich, or modify metadata for alignment use.

### CR-005 — One Engine per Run

Each Alignment Run SHALL use exactly one Alignment Engine.

### CR-006 — Black-Box Engine Treatment

The implementation SHALL treat Alignment Engines as black-box computational components.

### CR-007 — Minimum Layer Establishment

The implementation SHALL establish a Layer only when at least one GB-FDO and at least one CBKB-FDO are present.

### CR-008 — Fixed Layer During Execution

Layer membership SHALL remain fixed during Alignment Run execution.

### CR-009 — Input Package Generation

Each Alignment Run SHALL consume exactly one Input Package generated from the Layer Image associated with the established Layer.

### CR-010 — Output Package Production

Each successfully completed Alignment Run SHALL result in exactly one Output Package produced by the selected Alignment Engine.

### CR-011 — Alignment Result Graph Authority

Each Output Package SHALL contain exactly one Alignment Result Graph, and that graph SHALL be treated as the authoritative scientific result object.

### CR-012 — Engine Notes Separation

Engine Notes, if present, SHALL be maintained separately from the Alignment Result Graph.

### CR-013 — Negative Result Validity

Negative alignment outcomes represented in a valid Alignment Result Graph SHALL be treated as valid scientific results.

### CR-014 — Save Run Precondition

Save Run SHALL only be available when an Output Package exists for the current Alignment Run.

### CR-015 — User-Controlled Persistence

Persistence SHALL occur only through explicit user action.

### CR-016 — Saved Run Package Derivation

Each Saved Run Package SHALL be derived from exactly one Output Package.

### CR-017 — Saved Run Package Required Elements

Each Saved Run Package SHALL contain the Alignment Result Graph, Layer Image, Provenance Metadata, Reproducibility Information, and Saved Run Metadata.

### CR-018 — Saved Run Package Augmentation

Saved Run Package augmentation SHALL NOT modify the preserved Output Package.

### CR-019 — Layer Image Identity Across Packages

The Layer Image preserved in a Saved Run Package SHALL be identical to the Layer Image contained in the corresponding Output Package.

### CR-020 — Preservation by Reference

FDOs SHALL be preserved by reference rather than by payload duplication.

### CR-021 — Clear Result Precondition

Clear Result SHALL only be available when an Output Package exists for the current Alignment Run.

### CR-022 — Clear Result Behavior

Clear Result SHALL remove active result artifacts from the runtime environment without altering previously created Saved Run Packages.

### CR-023 — Provenance Preservation

The implementation SHALL preserve provenance sufficient to support inspection, comparison, interpretation, and reproducibility.

### CR-024 — Concept-Revealing Interface

The user interface SHALL expose GARI concepts directly.

### CR-025 — State Model Conformance

Runtime behavior SHALL conform to the state model and guard requirements defined in this document and derived from the Release Candidate.

## 14.4 Recommended Requirements

A conformant implementation SHOULD satisfy the following recommended requirements unless there is a documented reason not to do so.

### RR-001 — Unsaved Result Warning

The implementation SHOULD warn users before clearing or superseding unsaved Alignment Run results.

### RR-002 — Downloadable Saved Run Archive

The implementation SHOULD provide Saved Run Packages as downloadable archives.

### RR-003 — Behavior-Oriented Acceptance Tests

The implementation SHOULD include automated acceptance tests corresponding to Chapter 12.

### RR-004 — Mock Alignment Engine

The implementation SHOULD include a mock Alignment Engine for testing implementation behavior.

### RR-005 — Schema Validation

The implementation SHOULD use runtime schema validation for FDOs, Input Packages, Output Packages, and Saved Run Packages.

### RR-006 — Modular Engine Adapter

The implementation SHOULD isolate engine integration behind an adapter interface.

### RR-007 — Diagnostic Logging

The implementation SHOULD maintain diagnostic logs sufficient for debugging and implementation audit.

## 14.5 Implementation Freedom Areas

Conformant implementations MAY vary in the following areas:

1. programming language;
2. user interface framework;
3. state management library;
4. archive library;
5. test framework;
6. visual design;
7. file upload mechanism;
8. local versus backend execution;
9. engine adapter implementation;
10. internal directory structure;
11. naming of implementation modules;
12. optional convenience validation;
13. optional supporting artifacts;
14. optional developer diagnostics.

Implementation freedom SHALL NOT be used to violate mandatory requirements.

### 14.5.1 Implementation Freedom Clarification

Unless explicitly constrained by a mandatory requirement, implementations MAY differ in their internal design, technology choices, deployment approaches, persistence strategies, diagnostic mechanisms, identifier-generation approaches, serialization formats, user-interface designs, adapter implementations, and other implementation details.

Conformance is determined by externally observable satisfaction of applicable mandatory requirements rather than by internal implementation architecture.

Implementation freedom SHALL NOT be interpreted as permission to violate mandatory GARI requirements.

## 14.6 Non-Conforming Behaviors

An implementation is non-conforming if it:

1. treats GARI as a knowledge application platform;
2. executes CBK Artifacts as part of GARI runtime behavior;
3. generates or repairs metadata for alignment use;
4. includes payload bitstreams in Input Packages;
5. runs multiple engines in a single Alignment Run;
6. permits run execution without an established Layer;
7. permits Save Run without an Output Package;
8. permits Clear Result without an Output Package;
9. modifies the Output Package while creating a Saved Run Package;
10. treats Engine Notes as authoritative result graph content;
11. treats engine failure as a negative alignment result;
12. persists runs automatically as a substitute for explicit Save Run.

---

# Appendix A — Suggested Repository Structure

Informative.

```text
gari-v1-implementation/
  README.md
  package.json
  src/
    app/
      AppShell.*
      routes.*
    components/
      EnginePanel.*
      LayerPanel.*
      RunControls.*
      ResultInspector.*
      SaveRunPanel.*
      DiagnosticsPanel.*
    domain/
      fdo.*
      layer.*
      layer-image.*
      input-package.*
      output-package.*
      alignment-result-graph.*
      provenance.*
      saved-run-package.*
    state/
      state-machine.*
      runtime-store.*
      selectors.*
    services/
      fdo-loader.*
      fdo-validator.*
      layer-manager.*
      input-package-builder.*
      engine-registry.*
      engine-adapter.*
      run-orchestrator.*
      output-package-manager.*
      saved-run-builder.*
      logger.*
    engines/
      mock-engine.*
      adapters/
    schemas/
      fdo.schema.*
      input-package.schema.*
      output-package.schema.*
      saved-run-package.schema.*
    tests/
      unit/
      integration/
      e2e/
  public/
    sample-data/
  docs/
    implementation-notes.md
```

---

# Appendix B — Suggested API Interfaces

Informative.

## B.1 FDO Loader

```text
loadFdos(source): FdoLoadResult
validateFdo(candidate): FdoValidationResult
classifyFdo(fdo): GB-FDO | CBKB-FDO | unsupported
```

## B.2 Layer Manager

```text
addFdo(fdo): LayerState
removeFdo(pid): LayerState
isLayerEstablished(layerState): boolean
createLayerImage(layerState): LayerImage
```

## B.3 Input Package Builder

```text
buildInputPackage(layerImage, engineProfile, runMetadata): InputPackage
validateInputPackage(inputPackage): ValidationResult
```

## B.4 Engine Adapter

```text
loadProfile(profile): EngineProfile
validateProfile(profile): ValidationResult
execute(inputPackage, configuration): OutputPackage
```

## B.5 Run Orchestrator

```text
canRun(runtimeState): boolean
startRun(runtimeState): RunExecutionState
completeRun(outputPackage): RuntimeState
failRun(error): RuntimeState
```

## B.6 Saved Run Builder

```text
canSaveRun(runtimeState): boolean
buildSavedRunPackage(outputPackage, reproducibilityInformation): SavedRunPackage
createArchive(savedRunPackage): ArchiveBlob
```

## B.7 Result Manager

```text
setActiveOutputPackage(outputPackage): RuntimeState
getAlignmentResultGraph(): AlignmentResultGraph
clearResult(): RuntimeState
hasUnsavedResult(): boolean
```

---

# Appendix C — Example Runtime Workflows

Informative.

## C.1 Standard Successful Run

1. User opens GARI.
2. Application enters Landed State.
3. User loads Alignment Engine Profile.
4. Application validates profile.
5. User loads one GB-FDO.
6. User loads one CBKB-FDO.
7. Application establishes Layer.
8. Application enables Run Alignment.
9. User initiates run.
10. Application fixes Layer membership for the duration of execution.
11. Application creates Layer Image.
12. Application creates Input Package.
13. Application invokes Alignment Engine.
14. Engine returns Output Package.
15. Application validates Output Package.
16. Application enters Run Complete State.
17. Application displays Alignment Result Graph.
18. User invokes Save Run.
19. Application creates Saved Run Package.
20. Application enters Saved State.
21. User invokes Clear Result.
22. Application removes active result artifacts.

## C.2 Run Producing Negative Results

1. User loads engine and establishes Layer.
2. User runs alignment.
3. Engine returns a valid Output Package.
4. Alignment Result Graph records negative alignment outcomes.
5. Application treats the outcomes as valid scientific results.
6. Save Run remains available.

## C.3 Engine Failure

1. User loads engine and establishes Layer.
2. User runs alignment.
3. Engine fails or returns malformed output.
4. Application reports execution or output validation error.
5. Application does not create a valid Output Package.
6. Save Run remains disabled.
7. Error can be resolved and run retried if engine and Layer remain valid.

## C.4 Unsaved Result Clearing

1. User completes run.
2. Output Package exists.
3. User has not invoked Save Run.
4. User invokes Clear Result.
5. Application warns that unsaved active result artifacts may be lost.
6. User confirms.
7. Application clears active result artifacts.
8. Previously created Saved Run Packages remain unaffected.

---

# End of GARI v1.0 Implementation Specification
