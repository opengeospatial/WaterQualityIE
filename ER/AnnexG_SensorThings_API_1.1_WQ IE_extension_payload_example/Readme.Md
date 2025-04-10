# SensorThings API 1.1 + WQ IE extension payload example

That example payload was obtained running the following SensorThings API query : https://wqie.internetofwater.app/FROST-Server/v1.1/Datastreams('0442bf6d-35c8-5a40-33ce-ad664e905735')?$expand=ObservedProperty,ObservingProcedure,UltimateFeatureOfInterest,Observations($expand=FeatureOfInterest) 

WQ IE editor note : the only change between this local file and the API response payload is in the update of the ObservingProcedure name from 
```"name": "pH"``` to ```"name": "pH in Water by Electrometric Method"``` as mentionned by the US National Environmental Methods Index (NEMI) for procedure ```"USEPA-150.1"``` (https://www.nemi.gov/methods/method_summary/4685/)


