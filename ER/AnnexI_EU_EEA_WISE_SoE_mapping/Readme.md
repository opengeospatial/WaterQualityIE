# EEA WISE SoE mapping to WQ IE mapping notes

2024-11-12 version

## Tables

FK between S_WISE6_SpatialObject_DerivedData (Site with context) and T_WISE6_DisaggregatedData (the actual data) is monitoringSiteIdentifier

If monitoringSiteIdentifier is provided, it is the same as thematicIdIdentifier	```Select * from S_WISE6_SpatialObject_DerivedData where not (monitoringSiteIdentifier ISNULL) and not (thematicIdIdentifier like monitoringSiteIdentifier) limit 10;```

For 1717 sites there is no monitoringSiteIdentifier, thus no link to data	

If no coordinates, ignore	

## Data Quality

Missing location in S_WISE6_SpatialObject_DerivedData, for AT 6% missing location, but in the wider dataset 20%!!! (14357 sites of 71843 total)	

## FoI

"New FoI if there is a value for:
* sampleIdentifier
* parameterSampleDepth
* parameterSedimentDepthSampled
* parameterSpecies"	

FoI	Information on water spatial objects 	https://water.discomap.eea.europa.eu/arcgis/rest/services/WISE_WFD 
Reporting	Reporting data (same structure as DisaggregatedData)	https://reportnet.europa.eu/public/dataflow/799