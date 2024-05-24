# FROST Infos

# Batch Upload
When populating a FROST instance from an existing database, the batch upload functionality is most valuable. 
This allows one to provide all data to be imported to FROST in one file, using placeholders for object identifiers. 
These placeholders are used during the batch upload process to create all necessary foreign key relationships between objects within the FROST database.

The batch upload functionality defines a JSON request structure in which to package the STA classes to be uploaded. This request structure consists of the following attributes:
- "id": object identifier placeholder
- "atomicityGroup": Defines individual transactions if required
- "method": For adding data "post", more generally supports
  - "get": get an object
  - "post": create an object
  - "patch": modify/update an object
  - "delete": delete an object
- "url": The class on which the request operates, e.g. "Things", "Sensors", "Datastreams"...
- "body": JSON representation of a new Thing

The batch upload JSON object consists of a `request` element containing an array of such individual requests as follows.





## Batch Upload file for WQ IE STA
We have provided an [example of a batch upload file](https://github.com/opengeospatial/WaterQualityIE/blob/master/FROST-Infos/BatchSTA-WQ-IE.json) for the WQ IE STA. This file can be used as a template for generating dumps from datasources.
