---
title: ICSM Address (Placeholder) (Schema)

language_tabs:
  - json: JSON
  - jsonld: JSON-LD
  - turtle: RDF/Turtle

toc_footers:
  - Version 0.1
  - <a href='#'>ICSM Address (Placeholder)</a>
  - <a href='https://blocks.ogc.org/register.html'>Building Blocks register</a>

search: true

code_clipboard: true

meta:
  - name: ICSM Address (Placeholder) (Schema)
---


# ICSM Address (Placeholder) `icsm.profiles.datatypes.address`

A simple implementation of ICSM address model. Can be mapped to or replaced by a standard ICSM schema when available.

<p class="status">
    <span data-rainbow-uri="http://www.opengis.net/def/status">Status</span>:
    <a href="http://www.opengis.net/def/status/under-development" target="_blank" data-rainbow-uri>Under development</a>
</p>

<aside class="success">
This building block is <strong><a href="https://github.com/icsm-au/3d-csdm-profiles/blob/main/build/tests/profiles/datatypes/address/" target="_blank">valid</a></strong>
</aside>

# Examples

## Example Address With Street



```json
{
      "propertyNumber": "4",
      "streetName": "Clarendon",
      "streetType": "St",
      "locality": "Maidstone",
      "state": "VIC",
      "postCode": "3012",
      "country": "Australia"
}

```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-profiles/build/tests/profiles/datatypes/address/example_1_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-profiles%2Fbuild%2Ftests%2Fprofiles%2Fdatatypes%2Faddress%2Fexample_1_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "propertyNumber": "4",
  "streetName": "Clarendon",
  "streetType": "St",
  "locality": "Maidstone",
  "state": "VIC",
  "postCode": "3012",
  "country": "Australia",
  "@context": "https://icsm-au.github.io/3d-csdm-profiles/build/annotated/profiles/datatypes/address/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-profiles/build/tests/profiles/datatypes/address/example_1_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-profiles%2Fbuild%2Ftests%2Fprofiles%2Fdatatypes%2Faddress%2Fexample_1_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix ns1: <ad:> .
@prefix sdo: <https://schema.org/> .

[] ns1:propertyNumber "4" ;
    ns1:streetName "Clarendon" ;
    ns1:streetType "St" ;
    sdo:addressCountry "Australia" ;
    sdo:addressLocality "Maidstone" ;
    sdo:addressRegion "VIC" ;
    sdo:postalCode "3012" .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-profiles/build/tests/profiles/datatypes/address/example_1_1.ttl">Open in new window</a>
</blockquote>


A simple address with street number


## Example Address with PO Box



```json
{
      "postOfficeBoxNumber": "4334",
      "locality": "Maidstone",
      "state": "VIC",
      "postCode": "3012",
      "country": "Australia"
}

```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-profiles/build/tests/profiles/datatypes/address/example_2_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-profiles%2Fbuild%2Ftests%2Fprofiles%2Fdatatypes%2Faddress%2Fexample_2_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "postOfficeBoxNumber": "4334",
  "locality": "Maidstone",
  "state": "VIC",
  "postCode": "3012",
  "country": "Australia",
  "@context": "https://icsm-au.github.io/3d-csdm-profiles/build/annotated/profiles/datatypes/address/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-profiles/build/tests/profiles/datatypes/address/example_2_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-profiles%2Fbuild%2Ftests%2Fprofiles%2Fdatatypes%2Faddress%2Fexample_2_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix sdo: <https://schema.org/> .

[] sdo:addressCountry "Australia" ;
    sdo:addressLocality "Maidstone" ;
    sdo:addressRegion "VIC" ;
    sdo:postOfficeBoxNumber "4334" ;
    sdo:postalCode "3012" .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-profiles/build/tests/profiles/datatypes/address/example_2_1.ttl">Open in new window</a>
</blockquote>


A simple address with PO box


# JSON Schema

```yaml--schema
$schema: https://json-schema.org/draft/2020-12/schema
$defs:
  icsm-address:
    allOf:
    - additionalProperties: false
      properties:
        propertyNumber:
          type: string
          x-jsonld-id: ad:propertyNumber
        unitNumber:
          type: string
        streetName:
          type: string
          x-jsonld-id: ad:streetName
        streetType:
          type: string
          x-jsonld-id: ad:streetType
        locality:
          type: string
          x-jsonld-id: https://schema.org/addressLocality
        state:
          type: string
          x-jsonld-id: https://schema.org/addressRegion
        postOfficeBoxNumber:
          type: string
          x-jsonld-id: https://schema.org/postOfficeBoxNumber
        postCode:
          type: string
          x-jsonld-id: https://schema.org/postalCode
        country:
          type: string
          x-jsonld-id: https://schema.org/addressCountry
      required:
      - postCode
      - state
    - anyOf:
      - required:
        - streetName
        - locality
      - required:
        - postOfficeBoxNumber
        - state
  streetAddress:
    allOf:
    - $ref: '#$defs/icsm-address'
    - required:
      - streetName
allOf:
- $ref: '#/$defs/icsm-address'
x-jsonld-extra-terms:
  address: https://schema.org/address
x-jsonld-prefixes:
  sdo: https://schema.org/
  ads: https:/icsm.org.au/placeholder/address/

```

> <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=yaml&amp;dataUrl=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-profiles%2Fbuild%2Fannotated%2Fprofiles%2Fdatatypes%2Faddress%2Fschema.yaml&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on YAML Viewer</a>

Links to the schema:

* YAML version: <a href="https://icsm-au.github.io/3d-csdm-profiles/build/annotated/profiles/datatypes/address/schema.yaml" target="_blank">https://icsm-au.github.io/3d-csdm-profiles/build/annotated/profiles/datatypes/address/schema.yaml</a>
* JSON version: <a href="https://icsm-au.github.io/3d-csdm-profiles/build/annotated/profiles/datatypes/address/schema.json" target="_blank">https://icsm-au.github.io/3d-csdm-profiles/build/annotated/profiles/datatypes/address/schema.json</a>


# JSON-LD Context

```json--ldContext
{
  "@context": {
    "propertyNumber": "ad:propertyNumber",
    "streetName": "ad:streetName",
    "streetType": "ad:streetType",
    "locality": "sdo:addressLocality",
    "state": "sdo:addressRegion",
    "postOfficeBoxNumber": "sdo:postOfficeBoxNumber",
    "postCode": "sdo:postalCode",
    "country": "sdo:addressCountry",
    "address": "sdo:address",
    "sdo": "https://schema.org/",
    "ads": "https:/icsm.org.au/placeholder/address/",
    "@version": 1.1
  }
}
```

> <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-profiles%2Fbuild%2Fannotated%2Fprofiles%2Fdatatypes%2Faddress%2Fcontext.jsonld">View on JSON-LD Playground</a>

You can find the full JSON-LD context here:
<a href="https://icsm-au.github.io/3d-csdm-profiles/build/annotated/profiles/datatypes/address/context.jsonld" target="_blank">https://icsm-au.github.io/3d-csdm-profiles/build/annotated/profiles/datatypes/address/context.jsonld</a>

# References

* [CSDM model](https://github.com/icsm-au/3d-csdm)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: <a href="https://github.com/icsm-au/3d-csdm-profiles" target="_blank">https://github.com/icsm-au/3d-csdm-profiles</a>
* Path:
<code><a href="https://github.com/icsm-au/3d-csdm-profiles/blob/HEAD/_sources/datatypes/address" target="_blank">_sources/datatypes/address</a></code>

