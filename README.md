# Jurisdiction profiles for the 3D CSDM (Cadastral Survey Data Model)

This repository defines profiles of the 3D CSDM (Cadastral Survey Data Model) for each jurisdiction participating in the first phase of development and testing.  

_Note that this is a model for **exchange** of survey data for plan submission, not a data storage specification or a cadastral data product. **[Please see the Reviewers Guide](REVIEW_GUIDE.md) for more details about scope.**_


Profile implementations (schemas, examples etc) may be found [here](https://icsm-au.github.io/3d-csdm-profiles/) using the OGC Building Block Register approach.
 - [ICSM common](https://icsm-au.github.io/3d-csdm-profiles/bblock/icsm.profiles.common)
 - [New Zealand](https://icsm-au.github.io/3d-csdm-profiles/bblock/icsm.profiles.nz)
 - [Victoria](https://icsm-au.github.io/3d-csdm-profiles/bblock/icsm.profiles.nz)
 - [Western Australia](https://icsm-au.github.io/3d-csdm-profiles/bblock/icsm.profiles.nz)


Profile documents (showing the underlying model and logical constraints defined by specific and inherited profiles) may be found here
 - [ICSM common](https://icsm-au.github.io/3d-csdm/docs/icsm-profile/)
 - [New Zealand](https://icsm-au.github.io/3d-csdm/docs/nz-profile/)
 - [Victoria](https://icsm-au.github.io/3d-csdm/docs/vic-profile/)
 - [Western Australia](https://icsm-au.github.io/3d-csdm/docs/wa-profile/)


In addition, a series of test cases allow simplified testing of each key aspect of the model, in particular support for different geometry forms. These are described in the [Examples Register](_sources/common/example_register.md).

The [form of these profiles](PROFILES.md) is based on a common platform for specification development and testing of reusable schemas and profiles (OGC Building Blocks). This supports:

- unambiguous (machine readable) constraints on use of the underlying [3D CSDM model](https://github.com/icsm-au/3d-csdm) and [implementation schema](https://github.com/icsm-au/3d-csdm-schema).
- validation of examples
- test cases
- generation of documentation
- alternative machine readable forms if required
- automated regression testing (of all examples and test cases) on any changes

The relationships of these profiles and the underlying  common model is shown below:

![](https://lucid.app/publicSegments/view/f7e6c029-db67-4186-9592-cab6ec3437d0/image.png)

In future it is expected these profiles may be split into separate repositories to facilitate delegation of governance to each jurisdiction.

## Source code

Machine readable sources for the profile overview descriptions (semantic descriptions using the PROF vocabulary used to drive the documentation) may be found here:
 - [ICSM common](https://icsm-au.github.io/3d-csdm-profiles/profiles/icsm-common.ttl)
 - [New Zealand](https://icsm-au.github.io/3d-csdm-profiles/profiles/nz-profile.ttl)
 - [Victoria](https://icsm-au.github.io/3d-csdm-profiles/profiles/vic-profile.ttl)
 - [Western Australia](https://icsm-au.github.io/3d-csdm-profiles/profiles/wa-profile.ttl)

(Note that a future iteration of the processing may generate these profile descriptions automatically, linking related resources.)

## Repository Structure (OGC Building Block template)

The `build/` directory contains the **_compiled specification_** for implementing profiles of the 3DCSM


### Editable components

[_sources](_sources) contains the editable components that are composed into the final specification **and must not be directly used**. (This is because critical inherited information is not present in the source materials, and the [automation tooling](https://github.com/opengeospatial/bblocks-postprocess).

This contains:
- `features/`: schemas for the feature types defined by this bb (which is a "super-bb" containing at least oneOf these defined features)
- `datatypes/`: reusable schemas for (potentially complex) datatypes defined by this bb
- `aspects/`: groups of properties that may be included in feature types (equivalent to attribute groups in XML schema)
- `assets/`: Documentation assets (e.g. images) directory. See [Assets](#assets) below.

[vocabularies](vocabularies) contains CSV files (Comma Separated Variable) files containing the controlled vocabularies used, in the form:

```
preflabel,definition,notation,altlabel,related
Field Record,Field Record,field-record,,
Subdivision,Plan of Subdivsion,subdivision,,
```

Vocabularies are organised using a file naming convention `<jurisdiction>-<vocabulary-role>.csv` under sub-directories reflecting the part of the schema they specialise.

These vocabularies are annotated and compiled with [additional automation](VOCABULARY_MANAGEMENT.md).  (In future these vocabularies may be managed in a dedicated vocabulary management system with wider scope, however they form part of the initial specification design and testing and are hence included directly at this stage.)

NB. The common encoding specification is based on component building blocks using the same structure, without the vocabulary and profile specification elements. [More information on design and usage of OGC Building Blocks](https://github.com/opengeospatial/bblock-template/blob/master/USAGE.md)
