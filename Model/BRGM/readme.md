# Mapping nécessaire à l'alimentation de ST API à partir des topics Pub/Sub
## TODO
- nos GeoJSON dans le Pub/Sub utilisent le pattern href/title pour les URI vers d'autres Features et les codeList. 
 
  en JSON-LD on utilise le pattern @id/name pour faire de même

  Discussion en cours communauté INSPIRE Observation href/title VS id/name dans les JSON en sortie de STAPI (https://docs.google.com/spreadsheets/d/1CFcoAtXQes2yUfSjx0MECC-7AUc8pnGD7-BYOpTbW9c/edit#gid=0)
- unité des mesure (uom)
  - pour l'instant le lien propriété observé - méthode -> uom n'est pas fourni par le topic mais par un paramétrage externe
  - à améliorer

## Documents de référence
- ST API 
  - 1.0 spec : http://docs.opengeospatial.org/is/15-078r6/15-078r6.html
  - note : FROST anticipant la V 1.1 de ST API chaque classe du modèle est maintenant possède un attribut properties (JSON_Object). Nous l'utiliserons.

## Topics nécessaires
- Piezo (TODO EL : ajout nom topic)
- Observation (TODO EL : ajout nom topic)

## Note : 
-   les fichiers CSV poussés par les capteurs terrain nous donnent seulement un identifiant (normalement) à savoir l'ID du forage/point d'eau. Du point de vue de l'observation ce n'est pas l'ultimateFeatureOfInterest (qui serait l'aquifère) mais plutôt un proximateFeatureOfInterest. Idéalement on préférerait que ce soit l'identifiant externe stable et unique du piezometre (un Environmental Monitoring Facility)

-   Statut/qualification des observations : pour l'instant on pointe vers les nomenclatures Sandre. La demande est faire en interne pour avoir nos registres sur le sujet

-  uom
	-  GroundWater depth : https://data.geoscience.fr/ncl/uom/504
	-  Water Temperature : https://data.geoscience.fr/ncl/uom/607
	-  Battery voltage in the data communication module: https://data.geoscience.fr/ncl/uom/589
	-  Battery voltage in the sensor : https://data.geoscience.fr/ncl/uom/589
	-  Conductivity at 25°C : https://data.geoscience.fr/ncl/uom/463


## Mapping topics
### Piezo
- Alimentation du Thing, Location, Sensor, ObservedProperty, Datastream, FoI

| Pub/Sub                            |                                                                                                               | ST-Api     |                                    | Constante                                                            | Commentaire                                                                              |
|------------------------------------|---------------------------------------------------------------------------------------------------------------|------------|------------------------------------|----------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| id                               |                                                                                                               | Thing     | properties.identifier              |                                                                      |                                                                                          |
| properties.description             |                                                                                                               |            | description                        |                                                                      |                                                                                          |
| properties.name                    |                                                                                                               |            | name                               |                                                                      |                                                                                          |
| properties.mediaMonitored          |                                                                                                               |            | properties.mediaMonitored          |                                                                      |                                                                                          |
| properties.purpose                 |                                                                                                               |            | properties.purpose                 |                                                                      |                                                                                          |
| properties.measurementRegime       |                                                                                                               |            | properties.measurementRegime       |                                                                      |                                                                                          |
| properties.mobile                  |                                                                                                               |            | properties.mobile                  |                                                                      |                                                                                          |
| properties.resultAcquisitionSource |                                                                                                               |            | properties.resultAcquisitionSource |                                                                      |                                                                                          |
| properties.specialisedEMFType      |                                                                                                               |            | properties.specialisedEMFType      |                                                                      |                                                                                          |
| properties.any                     |                                                                                                               |            | properties                         |                                                                      |                                                                                          |
| properties.name                    |                                                                                                               | Location   | name                               |                                                                      |                                                                                          |
| properties.description             |                                                                                                               |            | description                        |                                                                      |                                                                                          |
| N/A                                |                                                                                                               |            | encodingType                       | application/vnd.geo+json                                             |                                                                                          |
| geometry                           |                                                                                                               |            | location                           |                                                                      |                                                                                          |
| properties.observingCapability     | ultimateFeatureOfInterest                                                                                     | DataStream | properties.related.ultimateFeatureOfInterest                             |                                                                      | Un Datastream par Observing Capability                                                   |
|                                    | proximateFeatureOfInterest                                                                                    |            |     /                               |                                                                      |                                                                                          |
|                                    | procedure                                                                                                     |            | sensor                             |                                                                      |                                                                                          |
|                                    | observedProperty                                                                                              |            | observedProperty                   |                                                                      |                                                                                          |
|                                    | N/A                                                                                                           |            | properties.resultNature            | 'http://inspire.ec.europa.eu/codelist/ResultNatureValue/primary'     |                                                                                          |
|                                    | observingCapability.observedProperty +'at'+ properties.name +'with method'+ observingCapability.procedure     |            | name                               |                                                                      | pattern (ex : https://sensorthings-wq.brgm-rec.fr/FROST-Server/v1.0/Datastreams(1142553) |
|                                    | observingCapability.observedProperty +' at '+ properties.name +' with method '+ observingCapability.procedure |            | description                        |                                                                      | pattern (ex : https://sensorthings-wq.brgm-rec.fr/FROST-Server/v1.0/Datastreams(1142553) |
|                                    | N/A                                                                                                           |            | observationType                    | http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Measurement |                                                                                          |
|                                    | https://data.geoscience.fr/ncl/uom/xxx.skos:prefLabel                                                                                                       |            | unitOfMeasurement.name             |                                                                      | ex : 'Mètre' pour uom 504                                                                                             |
|                                    | https://data.geoscience.fr/ncl/uom/xxx.skos:notation                                                                                                           |            | unitOfMeasurement.symbol           |                                                     | ex : 'm' pour uom 504                                                                                         |
|                                    | https://data.geoscience.fr/ncl/uom/xxx                                                                                                           |            | unitOfMeasurement.definition       |                                | ex  : https://data.geoscience.fr/ncl/uom/504                                                                                          |
|                                    | N/A                                                                                                           |            | observedArea                       |                                                                      |                                                                                          |
|                                    | N/A                                                                                                           |            | phenomenomTime                     |                                                                      | devrait être repris des observations                                                     |
|                                    | N/A                                                                                                           |            | resultTime                         |                                                                      | devrait être repris des observations                                                     |
|                           |                                                                                                                                                                                                        | FeatureOfInterest |                            |
| id                        | 'FoI for Thing'\+id                                                                                                                                                                                    |                   | name                       |
| id                        | 'Generated for Thing'\+id                                                                                                                                                                              |                   | description                |
|                           | 'application/vnd\.geo\+json'                                                                                                                                                                           |                   | encodingType               |
| geometry                  | \{        "type": "Point",         "coordinates": \[…\]         \]       \}                                                                                                                            |                   | feature                    |
| ultimateFeatureOfInterest | "properties": \{     "sampledFeature": \{         "@id": "https://data\.geoscience\.fr/id/HydroGeoUnit/143AE05",         "name": "le nom de l'Entite hydrogeologique 143AE05 if we have it"     \} \} |                   | properties\.sampledFeature |

### Observation
- Retrouver le bon DataStream et alimentation d'Observation

| Pub/Sub                    |       | ST-Api            |                         | Constante                | Commentaire                                                                      |
|----------------------------|-------|-------------------|-------------------------|--------------------------|----------------------------------------------------------------------------------|
| proximateFeatureOfInterest |       | featureOfInterest |                         |                          |                                                                                  |
|                            | href  |                   | properties.id           |                          |                                                                                  |
|                            | title |                   | name                    |                          |                                                                                  |
|                            | N/A   |                   | description             |                          | il faudrait reprendre la description du Thing relié au Datastream correspondant  |
|                            | N/A   |                   | encodingType            | application/vnd.geo+json |                                                                                  |
|                            | N/A   |                   | feature                 |                          | il faut reprendre la location du Thing relié au Datastream correspondant         |
| ultimateFeatureOfInterest  |       |                   | properties.related      |                          |                                                                                  |
|                            | href  |                   | properties.related.id   |                          |                                                                                  |
|                            | title |                   | properties.related.name |                          |                                                                                  |
| procedure                  |       |                   |                         |                          | peut servir de contrôle de cohérence ou d'input pour retrouver le bon datastream |
| observedProperty           |       |                   |                         |                          | peut servir de contrôle de cohérence ou d'input pour retrouver le bon datastream |
|                            |       | Observation       |                         |                          |                                                                                  |
| phenomenonTime             |       |                   | phenomenonTime          |                          |                                                                                  |
| resultTime                 |       |                   | resultTime              |                          |                                                                                  |
| result                     |       |                   | result                  |                          |                                                                                  |
| resultQuality              |       |                   | resultQuality           |                          |                                                                                  |
| parameters                 |       |                   | parameters              |                          |                                                                                  |
