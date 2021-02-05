# Sea Regions theme-specific requirements - DRAFT

**Purpose**: Verify that the features provided in the dataset adhere to the theme-specific requirements specified in the INSPIRE application schema.

**Prerequisites**

**Test method**

The following check is performed for every feature in the dataset:

* The MarineExtent of a Sea spatial object shall have a [waterLevel](#waterLevelSea) value equal to “MeanHighWater” (i.e. http://inspire.ec.europa.eu/codelist/WaterLevelValue/meanHighWater), unless there is no appreciable change in the Sea extent due to tides, in which case a value of “MeanSeaLevel” may be used. If the requirement is violated a manual check is required and the message will be [noTidalVariationCheck](#noTidalVariationCheck).

The following checks shall be performed manually for all features in the dataset:

* The Sea spatial object type shall be used to describe identified, named areas of sea (or ocean). Artificial reporting units are excluded from this requirement.

* The low water level used to define an IntertidalArea shall be provided as a value of the lowWaterLevel attribute. The level shall be a low water level. --> TO BE VERIFIED WHETHER IT CAN BE AUTOMATIZED

* The code lists defined in the spatial data theme Oceanographic Geographical Features shall be used to identify phenomena represented by MarineContour spatial object types. --> TO BE VERIFIED WHETHER IT CAN BE AUTOMATIZED

* SeaAreas shall be represented as 2-dimensional geometries. --> TO BE VERIFIED WHETHER IT CAN BE AUTOMATIZED


**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (2)
* [TG DS-SR](./README.md#ref_TG_DS_SR) 5.3.1.2.1.; 5.3.1.2.4.; 5.3.1.5.

**Test type**: Manual

**Notes** 

Verify that the theme-specific requirements that are specified in the UML model of the application schema are met, i.e. validate features against the theme-specific requirements. For unmet theme-specific requirements report [constraintViolation](#constraintViolation).

## Messages

Identifier  |  Message text (parameters start with '$')
---------------------------------------------------------- | -------------------------------------------------------------------------
constraintViolation <a name="constraintViolation"/>  |  XML document '$filename', $featureType '$gmlid': The constraint '$constraint' is violated.
noTidalVariationCheck <a name="noTidalVariationCheck"/>  |  XML document '{filename}', {featureType} '{gmlid}': The property '{property}' has a value '{value}' that is not equal to meanHighWater value, please verify if there is not significant tidal variation in water level.

## Contextual XPath references

The namespace prefixes used as described in [README](./README.md#namespaces).

Abbreviation                                               |  XPath expression				|Multiplicity       |Voidable
---------------------------------------------------------- | -------------------------------|-------------------|---------
waterLevel <a name="waterLevelSea"></a> | //schema-element(sr:Sea)/sr:extent/sr:MarineExtent/sr:waterLevel/@xlink:href="http://inspire.ec.europa.eu/codelist/WaterLevelValue/meanHighWater" | 0..1 | No
