# Physical Model

The physical model was created as a draft for the current work in updating STA to V2.0.

The observational aspects of the physical model are very close to the STA 1.1 model, with the following additions:
- OMS:Deployment - indicates when a Sensor was deployed on a Thing
- OMS:ObservingProcedure - the procedure used by the Sensor when creating the Observation
- STA1.1:FeatureOfInterest renamed to Feature
- UltimateFeatureOfInterest association from Datastream to Feature

![Unbenannt](https://github.com/opengeospatial/WaterQualityIE/assets/11915304/3ddf5eb0-e7c7-4946-bace-1222769fecf9)

The classes defined under OMS for Sampling have all been added to the physical model.

![Unbenannt-1](https://github.com/opengeospatial/WaterQualityIE/assets/11915304/368f7c71-0734-486a-8548-f5928a85794a)

In addition, relations mimicking OMS:relatedObservation and OMS:relatedSample have been added to the following classes:
- Thing -> RelatedThing
- Datastream -> RelatedDatastream
- Observation -> RelatedObservation
- Feature -> RelatedFeature

Each relation can have a RelationRole, whereby these roles can be reused across relation types.

![Unbenannt](https://github.com/opengeospatial/WaterQualityIE/assets/11915304/2c5b5954-1292-4c54-9588-37e2b5be6e57)

The following diagram gives a complete overview of the physical model.

![Unbenannt](https://github.com/opengeospatial/WaterQualityIE/assets/11915304/929ca764-74d1-4d7e-9bce-7be9e7526f9b)

In addition, the following diagram shows the derivation of the physical model from the logical OMS based model.

![Unbenannt-1](https://github.com/opengeospatial/WaterQualityIE/assets/11915304/b4041d12-fed0-49b9-82c3-5afff4abb98f)
