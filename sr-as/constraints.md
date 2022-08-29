# Constraints

**Purpose**: Verify that the features provided in the dataset adhere to the constraints specified in the INSPIRE application schema.

**Prerequisites**

**Test method**

The following checks are performed for every feature in the dataset.

* Check that the [waterLevel](#waterLevelSea) element of the spatial object type "Sea" is 'meanHighWater' (i.e. http://inspire.ec.europa.eu/codelist/WaterLevelValue/meanHighWater) (OCL: " inv: self.extent.waterLevel = 'meanHighWater' "). Sea is defined at Mean High Water, but this constraint can be relaxed if there is not significant tidal variation in water level. If the constraint is violated a manual check is required and the message will be [noTidalVariationCheck](#noTidalVariationCheck).

* Check that the [waterLevel](#waterLevelCoastline) element of the spatial object type "Coastline" is 'meanHighWater' (i.e. http://inspire.ec.europa.eu/codelist/WaterLevelValue/meanHighWater). Coastline is a special case of shoreline at Mean High Water Level (MHW). Coastline is the boundary between land and sea to be used for viewing, discovery and general purpose applications where a land/marine boundary is required. Where there is no significant variation in water level, Mean Sea Level (MSL) (i.e. http://inspire.ec.europa.eu/codelist/WaterLevelValue/meanSeaLevel) can be used as a substitute for MHW.

* Check that the [geometry](#geometry) of the spatial object types "SeaSurfaceArea" and "SeaBedArea" is a surface or a point. A Marine Layer (SeaSurfaceArea or SeaBedArea) can be represented as either a surface or a point. The point type geometry reflects the reality that many Marine Layers are identified by point observations. (OCL: " inv:self.geometry.oclIsKindOf(GM_Point) OR self.geometry.oclIsKindOf(GM_Surface) ").

* Check that the [extent](#extent) element of the spatial object types "Sea" and "MarineCirculationZone" has multiplicity 1.


**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (2)
* [TG DS-SR](./README.md#ref_TG_DS_SR) 5.3.2.1.1.; 5.3.2.1.5.; 5.3.2.1.6.
* [TG DS-SR-corr](./README.md#ref_TG_DS_SR_corr) Change: 2

**Test type**: Automated + Manual test (if required)

**Notes** 

GM_Surface is implemented in GML by: gml:Surface, gml:Polygon, gml:PolyhedralSurface and gml:TriangulatedSurface. GM_Point is implemented in GML by gml:Point.

Verify that the OCL constraints that are specified in the UML model of the application schema are met, i.e. validate features against the constraints. For unmet constraints report [constraintViolation](#constraintViolation).

## Messages

Identifier  |  Message text (parameters start with '$')
---------------------------------------------------------- | -------------------------------------------------------------------------
constraintViolation <a name="constraintViolation"/>  |  XML document '$filename', $featureType '$gmlid': The constraint '$constraint' is violated.
noTidalVariationCheck <a name="noTidalVariationCheck"/>  |  XML document '{filename}', {featureType} '{gmlid}': The property '{property}' has a value '{value}' that is not equal to meanHighWater value, please verify if there is not significant tidal variation in water level.

## Contextual XPath references

The namespace prefixes used as described in [README](./README.md#namespaces).

Abbreviation                   |  XPath expression                 |Multiplicity       |Voidable
------------------------------ | --------------------------------- | ------------------|----------
waterLevel <a name="waterLevelSea"></a> | //schema-element(sr:Sea)/sr:extent/sr:MarineExtent/sr:waterLevel/@xlink:href="http://inspire.ec.europa.eu/codelist/WaterLevelValue/meanHighWater" | 0..1 | No
waterLevel <a name="waterLevelCoastline"></a> | //schema-element(sr:Coastline)/sr:waterLevel/@xlink:href="http://inspire.ec.europa.eu/codelist/WaterLevelValue/meanHighWater"  OR //schema-element(sr:Coastline)/sr:waterLevel/@xlink:href="http://inspire.ec.europa.eu/codelist/WaterLevelValue/meanSeaLevel" | 1 | Yes
geometry <a name="geometry"></a> | //schema-element(sr:SeaBedArea)/sr:geometry/gml:Surface <br> //schema-element(sr:SeaBedArea)/sr:geometry/gml:Polygon <br> //schema-element(sr:SeaBedArea)/sr:geometry/gml:PolyhedralSurface <br> //schema-element(sr:SeaBedArea)/sr:geometry/gml:TriangulatedSurface OR //schema-element(sr:SeaBedArea)/sr:geometry/gml:Point <br> //schema-element(sr:SeaSurfaceArea)/sr:geometry/gml:Surface <br> //schema-element(sr:SeaSurfaceArea)/sr:geometry/gml:Polygon <br> //schema-element(sr:SeaSurfaceArea)/sr:geometry/gml:PolyhedralSurface <br> //schema-element(sr:SeaSurfaceArea)/sr:geometry/gml:TriangulatedSurface OR //schema-element(sr:SeaSurfaceArea)/sr:geometry/gml:Point | 0..1 | No
extent <a name="extent"></a> | //schema-element(sr:MarineCirculationZone)/sr:extent <br> //schema-element(sr:Sea)/sr:extent | 1..\*  | No
