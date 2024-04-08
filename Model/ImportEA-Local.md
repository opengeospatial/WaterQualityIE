# Importing in EA

Sequence of action to do in an EA project using the 'Reusable Asset Service' approach
## Adding ISO 'Observations, Measurements & Samples'

Supporting documentation from ISO : <https://github.com/ISO-TC211/HMMG/wiki#reusable-assets>

1. Clic on 'Publish/Reusable Assets' (circled red on the image below), then enter the ISO configuration (circled purple on the image below)
> Name: iso_in_the_cloud 
> Protocol:http 
> Server:104.130.217.178 
> Port:804 
> Model Name: iso

![RAS_1](./IMG/RAS_1.PNG)

2. Scroll the Storage down to 'ISO 19156 Observations & measurements'

![RAS_2](./IMG/RAS_2.PNG)

3. Take the latest version

and clic import (no need to add dependancies)

![RAS_3](./IMG/RAS_3.PNG)

4. Package import complete and ok looks like this

![RAS_4](./IMG/RAS_4.PNG)

## Adding OGC  'Water Quality IE modelling work'

That's exactly the same logic.
Just add on another 'root node'

1. Clic on 'Publish/Reusable Assets' (circled red on the image below), then enter the OGC  configuration (circled purple on the image below)
> Name: OGC
> Protocol:https 
> Server:umltool.ogc.org
> Port:1805 
> Model Name: IEs2023

![RAS_5](./IMG/RAS_5.PNG)

For ReadOnly access, use this
- User : readonly
- Password : OGC.model

2. Pick WaterQuality_IE

![RAS_6](./IMG/RAS_6.PNG)

and clic import (no need to add dependancies)

3. Package import complete and ok looks like this

![RAS_7](./IMG/RAS_7.PNG)

## Adding OGC 'HY_Features' model

Follow exactly the same logic.
Note : so far, in the WQ IE, we only use one package of the OGC HY_Features standard. It will be shared more properly at some point (so this may move at some point, then we'll update this How to).

1. Clic on 'Publish/Reusable Assets' (circled red on the image below), then enter the OGC  configuration (circled purple on the image below)
> Name: OGC
> Protocol:https 
> Server:umltool.ogc.org
> Port:1805 
> Model Name: IEs2023

2. Pick HY_SurfaceHydroFeature

and clic import (no need to add dependancies)

![RAS_8](./IMG/RAS_8.PNG)



## Final imported model should look like this

![image](https://user-images.githubusercontent.com/16756304/218700843-4de3c2ac-882e-4009-b579-e475fd8ab77d.png)
