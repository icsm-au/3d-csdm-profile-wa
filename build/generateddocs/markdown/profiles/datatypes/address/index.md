
# ICSM Address (Placeholder) (Schema)

`icsm.profiles.datatypes.address` *v0.1*

A simple implementation of ICSM address model. Can be mapped to or replaced by a standard ICSM schema when available.

[*Status*](http://www.opengis.net/def/status): Under development

## Examples

### Example Address With Street
A simple address with street number
#### json
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

#### jsonld
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

#### ttl
```ttl
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


### Example Address with PO Box
A simple address with PO box
#### json
```json
{
      "postOfficeBoxNumber": "4334",
      "locality": "Maidstone",
      "state": "VIC",
      "postCode": "3012",
      "country": "Australia"
}

```

#### jsonld
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

#### ttl
```ttl
@prefix sdo: <https://schema.org/> .

[] sdo:addressCountry "Australia" ;
    sdo:addressLocality "Maidstone" ;
    sdo:addressRegion "VIC" ;
    sdo:postOfficeBoxNumber "4334" ;
    sdo:postalCode "3012" .


```

## Schema

```yaml
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

Links to the schema:

* YAML version: [schema.yaml](https://icsm-au.github.io/3d-csdm-profiles/build/annotated/profiles/datatypes/address/schema.json)
* JSON version: [schema.json](https://icsm-au.github.io/3d-csdm-profiles/build/annotated/profiles/datatypes/address/schema.yaml)


# JSON-LD Context

```jsonld
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

You can find the full JSON-LD context here:
[context.jsonld](https://icsm-au.github.io/3d-csdm-profiles/build/annotated/profiles/datatypes/address/context.jsonld)

## Sources

* [CSDM model](https://github.com/icsm-au/3d-csdm)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/icsm-au/3d-csdm-profiles](https://github.com/icsm-au/3d-csdm-profiles)
* Path: `_sources/datatypes/address`

