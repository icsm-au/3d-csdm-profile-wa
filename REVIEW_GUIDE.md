# REVIEWERS GUIDE for 3D Cadastral Data Exchange Model

This document provides additional guidance to support review of the provided data models and encodings, reflecting the scope of the deliverables and the current state of testing.

# Overview

The 3D Cadastral Data Exchange Model Encoding Specification has the following components:

1. A common modular JSON schema for data exchange, with the following sub-modules:
   1. CSDM specific module
      1. [CSD](https://icsm-au.github.io/3d-csdm-schema/build/generateddocs/slate-build/csdm/features/CSD/) (Container and Parcels) - see note on [future separation of parcels component](https://github.com/icsm-au/3d-csdm-schema/blob/main/docs/future_alignments.md#ladm-parcels-model) 
      2. [Survey Features](https://icsm-au.github.io/3d-csdm-schema/build/generateddocs/slate-build/csdm/features/SurveyFeatures/) (Points, Vectors, Monuments)
      3. [Survey Observations](https://icsm-au.github.io/3d-csdm-schema/build/generateddocs/slate-build/csdm/features/SurveyFeatures/)
      4. [Compound Names](https://icsm-au.github.io/3d-csdm-schema/build/generateddocs/slate-build/csdm/datatypes/compoundName/) (appelation patterns)
      5. [Generalised annotations](https://icsm-au.github.io/3d-csdm-schema/build/generateddocs/slate-build/csdm/datatypes/annotation/)
   2. [Topological Features](https://ogcincubator.github.io/topo-feature/) - 3D extensible model of topology by reference to features
   3. [Observations and Measurements](https://github.com/opengeospatial/ogcapi-sosa) - JSON schema for SOSA ontology implementation of ISO 19156
   4. [PROV-SCHEMA](https://github.com/ogcincubator/bblock-prov-schema) - JSON schema for W3C PROV-O (provenance) standard
   5. [OGC BuildingBlocks](https://opengeospatial.github.io/bblocks/register.html) - meta-models for Features, links etc defined by OGC standards
2. A common binding of **_schema elements_** to the **[CSDM Conceptual Model](https://icsm-au.github.io/3d-csdm-design/2022/spec.html)**
   1. [JSON-LD "master"](https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/features/CSD/context.jsonld) compiled from component module bindings
   2. [JSON schema _annotations_](https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/features/CSD/schema.json) (for use by a possible future tool capability)
3. Profiles for NZ, Vic and WA jurisdictions  ([diagram](https://lucid.app/publicSegments/view/f7e6c029-db67-4186-9592-cab6ec3437d0/image.png)) comprising:
   1. Machine readable [Profile description](./profiles/icsm-common.ttl) describing profile hierarchies and identifying the set of machine readable components.
   2. [Controlled vocabularies](VOCABULARY_MANAGEMENT.md) defining allowable code values in the data
   3. "[Machine-readable bindings](./profiles/icsm-vocab-bindings.csv)" of vocabularies to the common schema
   4. Jurisdictional specific constraints
      1. individual "SHACL" files with [sets of rules] for specific aspects  
      2. A "closure" defining the [set of SHACL rules files](./profiles/icsm-profile-shacl.ttl) for each profile
   5. [Examples](_sources/nz/examples.yaml) and [test cases](_sources/nz/tests/) based on jurisdictional co-design input
4. Test cases and examples at all levels of reusable component, including the final profile specification
   1. with [validation reports](https://icsm-au.github.io/3d-csdm-profiles/build/tests/report.html) for each test case
5. An open source parser utility ([PanCadastre](https://github.com/OpenWork-NZ/pancadastre)) offering:
   1. Demonstration that the specified format can be easily read
   2. "Smoke test" creation of GeoJSON - converted from source CRS and topology relations to simplified geometeries in WGS84 and directly viewable in github preview
   3. Extended data validation including geometry integrity.
   4. Summary reports of file contents
6. Documentation (generated from machine readable sources) in multiple forms for different audiences:
   1. [Semantic Model and Profile](https://icsm-au.github.io/3d-csdm/docs/nz-profile/) - provides descriptions of the meaning of the underlying components, and the profile requirements **_independent of the encoding_**
   2. [Building Block](https://icsm-au.github.io/3d-csdm-profiles/) view of each module, exposing the technical implementation elements
   3. [Validation report](https://icsm-au.github.io/3d-csdm-profiles/build/tests/report.html) showing the application of testing and results per example and test case.
7. Custom documentation describing project specific matters, such as:
   1. [Register of examples](example_register.md)
   2. [Road Map Recommendations](https://github.com/icsm-au/3d-csdm-schema/blob/main/docs/ROAD_MAP.md)
   3. Description of how [2D-](https://github.com/icsm-au/3d-csdm-schema/blob/main/docs/csdm_2d_geometries.md) and [3-D geometries](https://github.com/icsm-au/3d-csdm-schema/blob/main/docs/3d_csdm_geometries.md) are implemented
   4. [Relationship to LADM](https://github.com/icsm-au/3d-csdm-schema/blob/main/docs/csdm-ladm.md)
   5. [Alignments](https://github.com/icsm-au/3d-csdm-schema/blob/main/docs/future_alignments.md) to other standards relevant to supporting wider vendor uptake.
8. Supporting documentation describing the structure of the specification and implementation and [testing procedures](https://github.com/icsm-au/3d-csdm-schema/blob/main/docs/testing.md).

Note that a common ICSM profile is used as a base for each ICSM Jurisdictional Profile, making it clear which elements are common.

# Providing feedback

Feedback may be provided in several ways - ideally in a form that can be tracked and responded to. A document or spreadsheet is fine for example.  Where possible feedback should clearly reference the artefacts associated with the issue with a URL (web link). 

Specific updates may take the form of a git "Pull request". 

Where some requirement is either not covered or unclear where and how it is implemented, examples should be pared down to the absolute minimum detail to describe the issue - referring to a complex paper plan is not going to support future understanding and uptake by implementing systems.  

# Key Principles to bear in mind

1. JSON is *permissive* - i.e. it is possible to **add** any properties to any object to extend it if required.
2. Extensions should be managed by defining restrictions
3. The JSON schema is complex to restrict
   1. we have chosen [version compatible with OGC APIs]() (via an automated "down-scaling" mechanism from a restricted profile of the most recent version of JSON schema)
   2. recent versions offer more elegant options but are not supported by tools yet
4. To understand and test these specifications it should be sufficient to read the profile documentation and examples provided, without detailed understanding of JSON schema, JSON-LD, SHACL, RDF Datacube and SKOS standards that underpin the machine-readable forms. 
5. Additional sub-profiles can be defined to apply specific extensions, rules, vocabularies for particular circumstances, such as:
   1. legacy data, with different content (e.g. terminology) and/or less stringent requirements 
   2. desired "future state" with more stringent requirements
   3. specific applications requiring extensions
6. Test cases are "best effort" based on feedback within timeframe - the test case capture process was extended to the end of the project as new requirements keep emerging.
7. Additional test cases can be added to the repository at any time to extend testing according to ICSM governance arrangements.
8. Documentation generation is an evolving art for this new type of specification, and other projects will re-use and provide improvements that can be incorporated as required. 
   1. _Please provide ideas as to how documentation can be improved, but keep in mind that sustainability depends on solutions being applicable to any such specification process._
9. Git delivery mechanism provides powerful options to clone and "fork" to perform experiments
10. The "compile and test" post-processing capabilities can be run on local copies - _care should be taken to leave shared repositories in working order_.
11. Much of the power of the solution to handle variations is in relatively complex standardised sub-modules based on proven semantic models:
    1. these will be tested in other project contexts
    2. the reusability patterns will be further tested and improved by the wider OGC community

# Test Scope

Testing occurs at a "module level" within the framework, to ensure the schema and business rule definitions work as expected. This means individual patterns can be understood and tested independently, then the tests combined to test a full CSD example.  From a **reviewer's perspective**  however only the tests in this repository need be assessed to confirm jurisdictional requirements are met. Tests are simply example encodings (JSON files) with a minimal implementation of mandatory elements and detail for the component and pattern being tested.

Each test is automatically validated against the underlying schema and the profile constraints. [more technical details](https://github.com/icsm-au/3d-csdm-schema/blob/main/docs/testing.md)

To review the constraints themselves it is possible to directly run the rules against the examples using external tools such as a [SHACL Validator](https://shacl-play.sparna.fr/play/validate) or [JSON Schema Validator](https://www.jsonschemavalidator.net/). Given these are run automatically however the most relevant strategy would be to deliberately break (invalidate) an example and run the rule.  A collection of such "expected to fail" examples have been created to assist rule testing and reside in the base schema repository - e.g. [https://github.com/icsm-au/3d-csdm-schema/tree/main/_sources/csdm/features/CSD/tests](https://github.com/icsm-au/3d-csdm-schema/tree/main/_sources/csdm/features/CSD/tests)

Profile specific rules are attached to each profile, such as generic ICSM rules regarding use of controlled vocabularies at [_sources/common/tests](_sources/common/tests)

# Profile descriptions

The profile description consists of a number of "moving parts" that are combined from different viewpoints:

1. A "machine readable" profile description using a standard semantic model (PROF) that describes each resource comprising the profile
2. A "human readable" description of the constraints imposed on the underlying logical model
3. A "developer friendly" web page linking to the various elements and examples.

The human-readable resources are generated from the machine-readable source to ensure consistency.

_It is expected that improvements in the form of the human readable format will be available from time to time, and a specification maintenance regime is required to decide if and when to apply such improvements._

# Implementation Concerns

A number of implementation concerns are out of scope for this phase since they relate to information managed in other systems that may not be present or require an additional layer to support effective integration. 

### Contextual content references
Typically such information will define the _content_ to be used in an implementation, such as references to previous surveys, documents, equipment registers etc.  The strategy used here is to define **_namespaces_** (i.e. unique Web address prefixes) for resources to allow unambiguous references. Namespaces allow short-form identifiers to be used instead of a static URL, and interpreted against the targets by the consuming system according to the current state of reference data provision. (For more detail [see technical details on namespaces](#namespaces)).   

The assumption is that implementations need only conform to policies around identifiers for both objects (surveys, documents, equipment etc) - the 3D CSDM model encoding enforces that these are in the form that can be converted to an unambiguous identifier.

### Occupation Features

The model is _agnostic_ regarding how "occupation features" can be embedded in CSDs.

Examples are provided using GeoJSON, however it is possible these could include:

- Unique ID references to stable spatial data infrastructure content
- API references to services
- Photographs, LIDAR or other sensor ouputs
- BIM models (or elements)
- tamper-proof "signed" evidence - e.g. using hash signatures or Blockchain  

### Descriptions of agents and processes

Further requirements analysis and co-design is required to determine appropriate sub-modules for describing surveyors and other agents.  

# Creating new profiles 

Creating a new profile may be required for at least two reasons:

1. Defining a new jurisdictional profile
2. Defining additional rules and or metadata requirements for a subset of jurisdictional data - for example making optional elements mandatory after a regulation came into force.

A new profile may be defined in either:

1. a new repository, by cloning and modifying the existing one and using schema references the same way the ICMS common profile references the master schema:

```json

 "allOf": [
    {
      "$ref": "https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/features/CSD/schema.json"
    }
  ]
```

2. A new subdirectory under the ```_sources/``` directory, with the same elements as an existing profile.

In each case its likely that the key requirement will be defining the set of *vocabularies* required. The process of defining these is further described in the document [VOCABULARY_MANAGEMENT](VOCABULARY_MANAGEMENT.md).  _This document is separate as it is expected that future tools to support this process more elegantly can be developed, such as some form of profiling application that prompts for all required information and puts it in the correct locations._

Additional *business rules* can be defined per profile, further described in the document [SHACL Validation](SHACL.md).  _This document is also separate as it is expected that future tools to support this process more elegantly can be developed, such as some form of profiling application that prompts for all required information and creates rules in the correct syntax._

If a profile needs to constrain or add new properties to the schema this can be done, however is somewhat dependent on familiarity with JSON schema (and its versions and tooling which is explained further [here](https://github.com/opengeospatial/bblock-template/blob/master/JSONSCHEMA-PROFILING.md).

# Technical details

Typically profiles of standards have been described in human-readable documents - leading to a range of challenges, such as consistency, alternative ways of achieving the same things and identifying commonality between profiles.

In order to support machine-readable, validatable profiles and avoid generating any project specific description languages a number of existing technologies have been combined in a sophisticated modular framework.

Deep understanding of all aspects of this framework is unnecessary however some notes are provided here to aid technical evaluation and planning for maintenance.

## Namespaces

Namespaces are "bound" to the data using the JSON-LD technology.

The simplest means of doing this is to define a **unique prefix** for each set of objects required by the profile.  This is done in the _sources/{profile}/context.jsonld file - e.g. [ICSM context](_sources/common/context.jsonld).

for example the lines:

```json
"icsm": "https://linked.data.gov.au/def/csdm/",
...
"icsm-angle-type": "icsm:icsm-angle-type/",
```
means that the value of a data element such as 

```json
"angleType": "icsm-angle-type:bearing",
```
is interpreted as:
```
"https://linked.data.gov.au/def/csdm/icsm-angle-type/bearing"
```

## JSON Schema "Future-proofing"

The underlying JSON syntax is stable, and sufficient for robust implementations without further dependency on any other component.

Likewise, JSON-LD and SHACL provide a stable mechanism to identify the semantics of each element and implement additional business rules regarding content.

JSON Schema, describing the *structure* of the JSON, is used to define the encoding patterns. Many versions of JSON Schema have been released in recent years, and it may be subject to further evolution. That said, the specification methodology has been to use the most elegant recent version, (https://json-schema.org/draft/2020-12/schema) but to use implementation patterns supported by the most commonly implemented previous versions.  

_Note - some of the underlying component modules have been placed into repositories managed by the OGC and may undergo further refinement - however the chosen methodology supports generation of multiple schema versions from an authoritative source, and the potential future use of more powerful patterns will require changes to this specification. 

Maintenance of this specification to align with future standardisation of component modules should be considered as an activity that requires consultation with implementers. This alignment may improve adoption, or require adaptation of existing implementations, such as provision of converters between versions, or multiple profiles for different baselines.

Note that the profile description framework allows for multiple versions to co-exist and share common elements if required.
