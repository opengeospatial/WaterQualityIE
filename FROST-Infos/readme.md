# FROST Infos

# Batch Upload
When populating a FROST instance from an existing database, the batch upload functionality is most valuable. 
This allows one to provide all data to be imported to FROST in one file, using placeholders for object identifiers. 
These placeholders are used during the batch upload process to create all necessary foreign key relationships between objects within the FROST database.

The batch upload functionality defines a JSON request structure in which to package the STA classes to be uploaded. This request structure consists of the following attributes:
- "id": object identifier placeholder. Subsequent requests in the same group can now use the value of this property, prefixed with a $
- "atomicityGroup": Defines individual transactions if required
- "method": For adding data "post", more generally supports
  - "get": get an object
  - "post": create an object
  - "patch": modify/update an object
  - "delete": delete an object
- "url": The class on which the request operates, e.g. "Things", "Sensors", "Datastreams"...
- "body": JSON representation of a new Thing

The batch upload JSON object consists of a `request` element containing an array of such individual requests.
The following example first creates a Sensor with the id "sensor1", then creates a Datastream linked to this Sensor, as well as to an ObservedProperty already existing within the STA Server with the "@iot.id": 12.

```
{
  "requests": [
    {
      "id": "sensor1",
      "atomicityGroup": "group1",
      "method": "post",
      "url": "Sensors",
      "body": {
		  "name": "DS18B20",
		  "description": "DS18B20 is an air temperature sensor",
		  "encodingType": "application/pdf",
		  "metadata": "http://datasheets.maxim-ic.com/en/ds/DS18B20.pdf"
		}
    },
    {
      "id": "2",
      "atomicityGroup": "group1",
      "method": "post",
      "url": "Things(5)/Datastreams",
      "body": {
		  "name": "Temperature Thing 5",
		  "description": "The temperature of thing 5",
		  "ObservedProperty": {"@iot.id": 12},
		  "Sensor": {"@iot.id": "$sensor1"}
		}
    }
  ]
}
```


## Batch Upload file for WQ IE STA
An [example of a batch upload file](https://github.com/opengeospatial/WaterQualityIE/blob/master/FROST-Infos/BatchSTA-WQ-IE.json) for the WQ IE STA is available. This file can be used as a template for generating batch upload files from existing datasources for upload into FROST via the batch upload functionality.
