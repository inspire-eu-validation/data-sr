# Code lists

**Purpose**: Verify that code lists extensions can be accessed.

**Prerequisites**

**Test method**

* Verify that any code list extensions are publicly accessible via HTTP, i.e. inspect extensible code list values property elements. If a reference (@xlink:href) has a value that does not start with http://inspire.ec.europa.eu/codelist/, verify that a HTTP GET request to the URI retrieves a document. Otherwise report [brokenLink](#brokenLink).

This data theme currently has the following empty codelists:

* [SeaAreaTypeClassificationValue](#SeaAreaTypeClassificationValue): http://inspire.ec.europa.eu/codelist/SeaAreaTypeClassificationValue
* [SeaBedCoverValue](#SeaBedCoverValue): http://inspire.ec.europa.eu/codelist/SeaBedCoverValue
* [SeaSurfaceClassificationValue](#SeaSurfaceClassificationValue): http://inspire.ec.europa.eu/codelist/SeaSurfaceClassificationValue
* [ShoreStabilityValue](#ShoreStabilityValue): http://inspire.ec.europa.eu/codelist/ShoreStabilityValue
* [ShoreTypeClassificationValue](#ShoreTypeClassificationValue): http://inspire.ec.europa.eu/codelist/ShoreTypeClassificationValue
* [ZoneTypeValue](#ZoneTypeValue): http://inspire.ec.europa.eu/codelist/ZoneTypeValue


**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 6 (3)
* [TG DS-SR ](./README.md#ref_TG_DS_SR) Annex C

**Test type**: Automated

**Notes**

Annex C of the [TG DS-SR ](./README.md#ref_TG_DS_SR) includes recommended values that may be used by data providers. They are published in the INSPIRE Registry. Before creating new terms, please check if one of them can be used.

## Messages

Identifier  |  Message text (parameters start with '$')
---------------------------------------------------------- | -------------------------------------------------------------------------
brokenLink <a name="brokenLink"/>  |  XML document '$filename', $featureType '$gmlid': The property '$propertyName' has a value '$value' that cannot be retrieved using HTTP. Every code list value must be made available in an online registry. 

## Contextual XPath references

The namespace prefixes used as described in [README](./README.md#namespaces).

Abbreviation                                               |  XPath expression      |Multiplicity   |Voidable
---------------------------------------------------------- | -----------------------|---------------|---------------------------------
SeaAreaTypeClassificationValue <a name ="SeaAreaTypeClassificationValue"></a> | //schema-element(sr:SeaArea)/sr:seaAreaType/@xlink:href <br> //schema-element(sr:Sea)/sr:seaAreaType/@xlink:href <br> //schema-element(sr:MarineCirculationZone)/sr:seaAreaType/@xlink:href | 0..1 | No
SeaBedCoverValue <a name ="SeaBedCoverValue"></a> | //schema-element(sr:SeaBedArea)/sr:surfaceType/@xlink:href | 1..\* | No
SeaSurfaceClassificationValue <a name ="SeaSurfaceClassificationValue"></a> | //schema-element(sr:SeaSurfaceArea)/sr:surfaceType/@xlink:href | 1 | No
ShoreStabilityValue <a name ="ShoreStabilityValue"></a> | //schema-element(sr:Coastline)/sr:segment/sr:ShoreSegment/sr:shoreStability/@xlink:href <br>//schema-element(sr:Shoreline)/sr:segment/sr:ShoreSegment/sr:shoreStability/@xlink:href  | 0..1 | Yes
ShoreTypeClassificationValue <a name ="ShoreTypeClassificationValue"></a> | //schema-element(sr:Coastline)/sr:segment/sr:ShoreSegment/sr:shoreClassification/@xlink:href <br>//schema-element(sr:Shoreline)/sr:segment/sr:ShoreSegment/sr:shoreClassification/@xlink:href  | 0..1 | Yes
ZoneTypeValue <a name ="ZoneTypeValue"></a> | //schema-element(sr:MarineCirculationZone)/sr:zoneType/@xlink:href  | 1 | No
