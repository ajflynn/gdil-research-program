# GARI v1.0 Canonical Item Specification

**Document:** GARI-v1.0-Canonical-Item-Specification.md

**Status:** Publication Candidate

---

# Chapter 1 — Introduction

## 1.1 Purpose

This specification defines Canonical Item Space, Canonical Items, and the requirements governing their use in metadata-driven computability discovery experiments.

## 1.2 Scope

This specification defines:

- Canonical Items
- Canonical Item Spaces
- Item identity requirements
- Item record requirements
- Item Space construction requirements
- Conformance requirements

This specification does not define:

- GARI runtime behavior
- Layers
- Layer Images
- Packages
- Metadata transport mechanisms
- Alignment Engine behavior
- Corpus governance

## 1.3 Relationship to GARI v1.0

The Canonical Item Specification is intended to support metadata-driven computability discovery experiments conducted using GARI and related scientific instruments.

## 1.4 Scientific Context

Canonical Item Space serves as a shared reference substrate supporting metadata-driven discovery of computational capabilities.

## 1.5 Conformance Philosophy

### 1.5.1 Experimental Scope Principle

This specification SHALL specify only those requirements necessary to support reproducible metadata-driven alignment experiments.

Requirements that are not necessary for reproducible experimentation SHOULD be considered out of scope unless justified by future experimental needs.

---

# Chapter 2 — Foundational Concepts

## 2.1 Canonical Item Space = Shared Reference Substrate

Canonical Item Space is a shared reference space used for metadata-driven computability discovery.

## 2.2 Item Definition

An Item is a referenceable specification of a computationally meaningful data resource that may be required, consumed, produced, or transformed by computational capabilities.

## 2.3 Canonical Item

A Canonical Item is the uniquely identified Item record maintained within Canonical Item Space.

## 2.4 Architectural Ownership Model

- Canonical Item Space owns Item definitions.
- FDO metadata may contain Item references.
- Alignment Engines may interpret Item references.

---

# Chapter 3 — Canonical Item Space Requirements

## CIS-R001 Item Collection

A Canonical Item Space SHALL consist of a collection of Canonical Items.

## CIS-R002 Identifier Integrity

A Canonical Item Space SHALL maintain Item identifier integrity.

- One identifier → one Item
- One Item → one identifier

## CIS-R003 Authoritative Definition Ownership

The Canonical Item Space SHALL be the authoritative source of Item definitions.

## CIS-R004 Shared Reference Support

A Canonical Item Space SHALL permit multiple metadata records to reference the same Item identifier.

## CIS-R005 Item Independence

Items SHALL NOT require relationships to other Items in order to be valid.

## CIS-R006 Reference Stability

The meaning of an Item identifier SHALL remain stable for the lifetime of the Item Space version in which it appears.

## CIS-R007 Minimal Structural Assumption

The specification SHALL NOT require graphs, ontologies, workflows, taxonomies, or semantic networks within Canonical Item Space.

---

# Chapter 4 — Item Identity

## 4.1 Item Identifier Integrity

Every Canonical Item SHALL possess exactly one Item identifier within its Canonical Item Space.

Each Item identifier SHALL identify one and only one Item within its Canonical Item Space.

The same Item identifier SHALL always refer to the same Item within its Canonical Item Space.

Different Item identifiers SHALL refer to different Items within the same Canonical Item Space.

## 4.2 Identity Locality

Identity is local to Canonical Item Space and does not imply global semantic identity.

## 4.3 Item-Space Uniqueness

Item identifiers SHALL be unique within a Canonical Item Space.

## 4.4 Identifier Immutability

Once assigned within a Canonical Item Space, an Item identifier SHALL NOT change.

## 4.5 Identifier Non-Reuse

Once assigned within a Canonical Item Space, an Item identifier SHALL NOT be reassigned to a different Item.

---

# Chapter 5 — Canonical Item Records

## 5.1 Canonical Item Record Principle

A Canonical Item record SHALL contain the information necessary to uniquely specify the computationally meaningful data resource represented by the Item.

## 5.2 Canonical Item Record Minimum

A Canonical Item record SHALL contain:

1. id
2. item_bitstream

Example:

```json
{
  "id": "CIS-000001",
  "item_bitstream": "1"
}
```

## 5.3 Minimal Valid Item Principle

A single item_bitstream containing the value "1" SHALL constitute a valid Item.

## 5.4 Item Existence Principle

Item existence is determined by:

- id
- item_bitstream

Not by:

- label
- description
- ontology mappings
- classifications
- relationships

## CIS-IR-R001 — Minimum Record

No additional fields SHALL be required.

## CIS-IR-R002 — Optional Enrichment

Additional Item-record fields MAY be present.

Such fields SHALL NOT be required for Item validity.

## 5.5 Representation Condition Independence

Differences among MRC-1, MRC-2, and MRC-3 representations SHALL be expressed through the contents of item_bitstream.

The validity and identity of a Canonical Item SHALL NOT depend upon additional required metadata fields introduced solely to support a representation condition.

---

# Chapter 6 — Item Representation Integrity

## CIS-MRC-R001 — Single Definition Principle

Within a Canonical Item Space, a given Item identifier SHALL resolve to exactly one Canonical Item definition.

## CIS-MRC-R002 — Bitstream Uniqueness by Identifier

A Canonical Item identifier SHALL NOT be associated with multiple item_bitstream representations.

## CIS-MRC-R003 — Distinct Representation Principle

If two item_bitstreams differ, they SHALL be treated as different Canonical Items and SHALL possess different Item identifiers.

Implication:

Canonical Item = id + item_bitstream

Different item_bitstream => Different Item => Different Item identifier

---

# Chapter 7 — Item References

## 7.1 Item References

FDO metadata may contain Item references.

Examples include:

- input_item_ids
- output_item_ids

## 7.2 Shared Referencing

Multiple metadata records may reference the same Item.

---

# Chapter 8 — Item Space Construction

## CIS-CON-R001 — Item Space Construction Documentation

A Canonical Item Space SHALL be accompanied by documentation describing how the included Canonical Items were selected and assembled.

Item Space construction methodology is a scientific reporting concern rather than an infrastructure governance concern.

---

# Chapter 9 — Conformance

## 9.1 Canonical Item Conformance

A Canonical Item conforms to this specification if:

1. It possesses exactly one Item identifier.
2. It possesses an item_bitstream.
3. It satisfies the Item Identity requirements of this specification.
4. It satisfies the Canonical Item Record requirements of this specification.
5. It satisfies the Single Definition Principle.

## 9.2 Canonical Item Space Conformance

A Canonical Item Space conforms to this specification if:

1. It consists of Canonical Items.
2. Item identifiers are unique within the Canonical Item Space.
3. It satisfies CIS-R001 through CIS-R007.
4. It satisfies CIS-CON-R001.

## 9.3 Scope of Conformance

This specification defines conformance only for:

- Canonical Items
- Canonical Item Spaces

This specification does not define conformance for:

- Experimental corpora
- GARI
- Layers
- Layer Images
- Packages
- Metadata schemas
- Alignment Engines

## 9.4 Conformance Independence Principle

Conformance to this specification does not imply conformance to any other specification.

Conformance to other specifications SHALL be determined by those specifications.

---

# Appendix A — Resolved Specification Issues

Resolved:

- SI-001 Canonical Item Space Requirements
- SI-002A Item Identity Scope
- SI-002B Identifier Immutability and Non-Reuse
- SI-003 Canonical Item Record Requirements
- SI-004A Item Identity vs Representation
- SI-005 Item Space Construction Methodology
- SI-006 Conformance Requirements

Struck as Out of Scope:

- Item Advertisement Representation
- Canonical Item Corpus Governance
- Relationship Between Item Space and Future Layer Fixtures
