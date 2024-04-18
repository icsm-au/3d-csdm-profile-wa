## Cadastral Survey Data Model - NZ Profile

Rules and default namespace bindings for NZ Jurisdiction Profile of the Cadastral Survey Data Model (CSDM).

A **Profile** is compliant with the underlying standard, and provides additional constraints on the use of generic patterns. Most of these are simple requirements to use specific vocabularies for descriptive codes in different places.

This extends the common ICSM Profile with NZ specific constraints.

The CSDM model assumes **stable references** in the form of URIs are available for things that need to be registered.
(The schema allows for simple strings, however this practice is unsafe in terms of data quality, and validators to check such references should be implemented)

Some points to note:

* uses the **foaf:** namespace for additional schema elements to describe agents
  - this may be either adopted as an icsm standard or modified as required to meet relevant standards. 
* a **registered-surveyors** namespace using an example of "https://example.gov.nz/surveyors/" is defined
  - this should be set to a relevant register


