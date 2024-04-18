# ICSM profile of the 3D CSDM (Cadastral Survey Data Model) JSON schema for data exchange.

This repository defines profiles of the 3D CSDM (Cadastral Survey Data Model) for each jurisdiction participating in the first phase of development and testing.  

_Note that this is a model for **exchange** of survey data for plan submission, not a data storage specification or a cadastral data product. **[Please see the Reviewers Guide](REVIEW_GUIDE.md) for more details about scope.**_


Profile implementations (schemas, examples etc): 
 - [ICSM common](https://icsm-au.github.io/3d-csdm-profile-icsm)
 - [New Zealand](https://icsm-au.github.io/3d-csdm-profile-nz)
 - [Victoria](https://icsm-au.github.io/3d-csdm-profile-vic)
 - [Western Australia](https://icsm-au.github.io/3d-csdm-profile-wa)


Profile documents (showing the underlying model and logical constraints defined by specific and inherited profiles) may be found here
 - [ICSM common](https://icsm-au.github.io/3d-csdm/docs/icsm-profile/)
 - [New Zealand](https://icsm-au.github.io/3d-csdm/docs/nz-profile/)
 - [Victoria](https://icsm-au.github.io/3d-csdm/docs/vic-profile/)
 - [Western Australia](https://icsm-au.github.io/3d-csdm/docs/wa-profile/)


The [form of these profiles](https://ogcincubator.github.io/bblocks-docs/) is based on a common platform for specification development and testing of reusable schemas and profiles (OGC Building Blocks). This supports:

- unambiguous (machine readable) constraints on use of the underlying [3D CSDM model](https://github.com/icsm-au/3d-csdm) and [implementation schema](https://github.com/icsm-au/3d-csdm-common).
- validation of examples
- test cases
- generation of documentation
- alternative machine readable forms if required
- automated regression testing (of all examples and test cases) on any changes

The relationships of the ICSM common and jurisdictional profiles and the underlying  common model is shown below:

![](https://lucid.app/publicSegments/view/f7e6c029-db67-4186-9592-cab6ec3437d0/image.png)



## Repository Structure (OGC Building Block template)

The `build/` directory contains the **_compiled specification_** for implementing profiles of the 3DCSM


### Editable components

[_sources](_sources) contains the editable components that are composed into the final specification **and must not be directly used**. (This is because critical inherited information is not present in the source materials, and the [automation tooling](https://github.com/opengeospatial/bblocks-postprocess).

This contains:
- `features/`: schemas for the feature types defined by this bb (which is a "super-bb" containing at least oneOf these defined features)
- `datatypes/`: reusable schemas for (potentially complex) datatypes defined by this bb
- `aspects/`: groups of properties that may be included in feature types (equivalent to attribute groups in XML schema)
- `assets/`: Documentation assets (e.g. images) directory. See [Assets](#assets) below.

[profiles/](profiles/) contain vocabulary bindings and content validation rules fpr this profile. These are combined with other profiles as required.

NB. The common encoding specification is based on component building blocks using the same structure, without the vocabulary and profile specification elements. [More information on design and usage of OGC Building Blocks](https://ogcincubator.github.io/bblocks-docs/)
