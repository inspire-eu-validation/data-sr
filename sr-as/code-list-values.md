# Code list values

**Purpose**: Verify whether all attributes whose value type is a code list take the values set out therein

**Prerequisites**

**Test method**

When an attribute has a code list as its type, verify that the values comply with the definitions and include the values set out in Annex II, III and IV of the Implementing Rule. To pass this test verify that any instance of an attribute:

* takes only values explicitly specified in the INSPIRE code list register when the code list‘s extensibility is 'none'.
* takes only a value explicitly specified in the INSPIRE code list register or shall take a value that is narrower (i.e. more specific) than those explicitly specified in the application schema when the code list‘s extensibility is 'narrower'.
* takes values explicitly specified in the INSPIRE code list register when the code list‘s extensibility is 'open' or if a value is not one of the values listed in the code list register check that any extensions do not overlap with the code lists that are defined in Annexes II, III and IV of the Implementing Rule and that all extensions conform to the requirements (This last check is a manual test).

The following checks are performed for every feature in the dataset, for the not extensible codelists:

* Check that all the [waterLevel](#waterLevel), [highWaterLevel](#highWaterLevel) and [lowWaterLevel](#lowWaterLevel) elements has a xlink:href attribute pointing to a [valid value](#validValue1). If the check fails report [disallowedCodeListValue](#disallowedCodeListValue).

* Check that all the [composition](#composition) elements has a xlink:href attribute pointing to a [valid value](#validValue2). If the check fails report [disallowedCodeListValue](#disallowedCodeListValue).


| <a name="validValue1"></a> Valid values for xlink:href attribute of [waterLevel](#waterLevel), [highWaterLevel](#highWaterLevel) and [lowWaterLevel](#lowWaterLevel) elements are available in the INSPIRE Registry. | 
| ---- | 
| WaterLevelValue: http://inspire.ec.europa.eu/codelist/WaterLevelValue |

| <a name="validValue2"></a> Valid values for xlink:href attribute of [composition](#composition) element are available in the INSPIRE Registry| 
| ---- | 
| ShoreTypeValue: http://inspire.ec.europa.eu/codelist/ShoreTypeValue | 


**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (1)
* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (3)
* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 6 (1)
* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 6 (2)
* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 6 (3)
* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 6 (4)

**Test type**: Automated

**Notes**

The WaterLevelValue and the ShoreTypeValue codelists are defined and managed in the Hydrodraphy theme.

## Messages

Identifier  |  Message text (parameters start with '$')
---------------------------------------------------------- | -------------------------------------------------------------------------
disallowedCodeListValue <a name="disallowedCodeListValue"/> | XML document '$filename', $featureType '$gmlid': The property '$propertyName' has a value '$value' that is not one of the allowed values listed at $codelist. Please note that the URIs of all code list values from the INSPIRE Registry shall be referenced using the http protocol. 

## Contextual XPath references

The namespace prefixes used as described in [README](./README.md#namespaces).

Abbreviation                                               |  XPath expression				|Multiplicity       |Voidable
---------------------------------------------------------- | -------------------------------|-------------------|---------
waterLevel <a name="waterLevel"></a> | //schema-element(sr:Coastline)/sr:waterLevel/@xlink:href <br> //schema-element(sr:Shoreline)/sr:waterLevel/@xlink:href | 1  | Yes
waterLevel <a name="waterLevel"></a> | //schema-element(sr:MarineCirculationZone)/sr:extent/sr:MarineExtent/sr:waterLevel/@xlink:href <br> //schema-element(sr:Sea)/sr:extent/sr:MarineExtent/sr:waterLevel/@xlink:href <br< //schema-element(sr:SeaArea)/sr:extent/sr:MarineExtent/sr:waterLevel/@xlink:href  | 0..1  | No
highWaterLevel <a name="highWaterLevel"></a> | //schema-element(sr:InterTidalArea)/sr:highWaterLevel/@xlink:href | 1 | No
lowWaterLevel <a name="lowWaterLevel"></a> | //schema-element(sr:InterTidalArea)/sr:lowWaterLevel/@xlink:href | 1 | No
composition <a name="composition"></a> | //schema-element(sr:InterTidalArea)/hy-p:composition/@xlink:href | 1 | Yes