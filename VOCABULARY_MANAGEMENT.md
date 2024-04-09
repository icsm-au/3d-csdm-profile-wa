# VOCABULARY MANAGEMENT

The 3D CSDM specification is designed to allow **Profiles** to be specified, primarily through use of **Controlled Vocabularies** and **profile constraints**.

_This is the most complex part of the specification process since it spans multiple technologies that do not provide good native support for profiling or vocabularies. The process is expected to be further developed and simpler options emerge over time._

Vocabularies are implemented through **unambiguous codes** in the form:

```"surveyType: "nz-survey-type:subdivision"```

where the "magic" qualifier is defined by the profile:

```"nz-survey-type": "https://linked.data.gov.au/def/csdm/nz-survey-type/",```

**_It is assumed that at some point these vocabularies will be published online under the reserved URI address_.**  However, the testing system has been configured to locate the local files for each vocabulary in the interim.

For ease of use these vocabularies are supplied using a common spreadsheet format, in CSV text files.

These are located under the [```vocabularies/```](vocabularies) subdirectory.

## Vocabulary Source Format

This is a simple CSV format:

```
preflabel,definition,notation,altlabel,related
Deposited Plan,"A cadastral survey plan or dataset that has been prepared under the Land Transfer Act and has had new titles created.",dp,,
```

The key field is ```notation``` - this is used to define an identifier that is used in the data.

Another configuration [vocabs-uplift.yml](vocabs-uplift.yml) is used to bind files to namespaces and data types for terms:

```json
"wa-locality.csv": { "uri": "https://linked.data.gov.au/def/csdm/wa-locality", "label": "WA Localities", "type": "termtype:AdminUnit" },
```

These CSVs and extra configuration metadata are processed into a standardised format (SKOS) that can allow further elucidation, description, cross references etc as required in future.

```
<https://linked.data.gov.au/def/csdm/wa-locality/abba-river> a skos:Concept,
        termtype:AdminUnit ;
    skos:inScheme <https://linked.data.gov.au/def/csdm/wa-locality> ;
    skos:notation "abba-river" ;
    skos:prefLabel "Abba River" .

```
The SKOS format is a semantic model, expressed using the Turtle language (.ttl files), and directly processed by the **profile constraints** that are expressed in SHACL (Shapes Constraint Language).

## Binding Vocabularies to model and schema elements 

Summaries of these are provided in the generated documentation - e.g. [NZ Profile#Vocabularies](https://icsm-au.github.io/3d-csdm/docs/nz-profile/#oJcg30JS)


The "machine-readable binding" between the vocabularies and the relevant parts of the schema is done in a number of places:

- JSON-LD contexts for profiles - [e.g.](_sources/nz/context.jsonld)
- SHACL rules for making sure terms are of the right **term type** (defined in the ICSM common profile - other international CSD implementations may not use controlled vocabularies at all!) 
- Profile rules using the RDF-QB (Datacube) model to link properties to specific **ConceptSchemes**
- 'SHACL closures' to join the vocabularies to the model for the purpose of SHACL rule validation
- "uplift" configurations to process the CSV into SKOS using the correct **ConceptScheme** and **term type** metadata
- "profile descriptions" linking the profile to the set of RDF-QB and SHACL resources.
- generated documents joining profile constraints to model elements.

## Vocabulary labelling

Vocabularies are labelled to support better documentation.

Again, for convenience this is done in simple CSV files (profiles/*-vocab-labels.csv) of the form:

```
Scheme,Label
vocabs:icsm-procedure-used,"Survey Procedure"
```
Extra CSV files are processed using the same automation processes to generate the RDF-QB forms of constraints so that profiles do not need to create _any_ RDF directly for profiling the standard schema.


*In future a "profile specification wizard application" could be used to generate all these elements from a single source*

