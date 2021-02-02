# Feature references

**Purpose**: Verify that referenced features can be retrieved.

**Prerequisites**

**Test method**

* Verify that any feature reference in an association role is publicly accessible via HTTP, i.e. inspect all relevant properties. If a reference (@xlink:href) has a value that starts with "#", verify that an element with a `gml:id` attribute with the referenced identifier exists in the same document. If the reference starts with "http", verify that a HTTP GET request to the URI retrieves an XML document. Otherwise report [brokenLink](#brokenLink).

This data theme currently has the following association role:

* [SeaArea.subArea](#subArea): SeaArea
* [MarineContour.sourceObservations](#sourceObservations): ObservationSet
* [MarineLayer.subLayer](#subLayer): MarineLayer 

**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (2)

**Test type**: Automated

**Notes**

## Messages

Identifier  |  Message text (parameters start with '$')
---------------------------------------------------------- | -------------------------------------------------------------------------
brokenLink <a name="brokenLink"/>  |  XML document '$filename', $featureType '$gmlid': The property '$propertyName' has a value '$value' that cannot be retrieved using HTTP. Every code list value must be made available in an online registry. 

## Contextual XPath references

The namespace prefixes used as described in [README](./README.md#namespaces).

Abbreviation                         |  XPath expression    | Multiplicity    | Voidable
------------------------------------ | ---------------------|-----------------|------------
SeaArea.subArea <a name ="subArea"></a>	| //schema-element(sr:SeaArea)/sr:subArea/@xlink:href <br> //schema-element(sr:Sea)/sr:subArea/@xlink:href <br> //schema-element(sr:MarineCirculationZone)/sr:subArea/@xlink:href | 0..\* | No
MarineContour.sourceObservations <a name ="sourceObservations"></a>	| //schema-element(sr:MarineContour)/sr:sourceObservations/@xlink:href | 0..\* | No
MarineLayer.subLayer <a name ="subLayer"></a>	| //schema-element(sr:SeaBedArea)/sr:subLayer/@xlink:href <br> //schema-element(sr:SeaSurfaceArea)/sr:subLayer/@xlink:href | 0..\* | No