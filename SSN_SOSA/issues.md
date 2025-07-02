## Observing Capability limitation with SSN/SOSA
  In fact, the system capability require the presence of a System (Actuator, Sensor, or Sampler). From OMS point view this is not necessary. This makes the mapping to SSN/SOSA not always fully covered

## Reflection around the unique nature of ObservingCapability
 Observing Capability describes a potential Observation, using what method, on what  (proximate and ultimate ) feature of interest, at what Host. Although it can point to a host, it doesn't mean that related observations are performed directly at the host, but that it originate from there. It can omit any necessary intermediate steps steps like Sampling.
 
  The initial assumption that ssn-sytem:SystemCapability is able to cover the oms:ObservingCapability is clearly wrong. The system capability can tell in a way the technical specs of sensor for example, about what it can observe, with what method, under what condition, etc. but it doesn't allow link to what FoI and were are we doing we CAN do the observation.

## Use of sosa:Deployment

 In contrast to that, sosa:Deployment, as it is in the name, is the actual deployment of an asset/system, not just theoritical. So it can very well convey the info about the info about the capability, but not in all cases. This could be clearly seen in the differences between the inSitu and exSitu examples of surface Water quality.

### The case of _in situ_ obervation
 The _in situ_ example (diagrams/NEW SW_DO_pH_Observation.png and aligned_NEW_GW_InSitu_QualityObservation.ttl in Surfacewater/SW_InSitu_QualityObservation) shows that already a deployment and a sensor are explicitly montioned. In this case we have the actual implementation that can convey the capability info. The observing capability  (link to propety, method, FoIs and  host)  is concretly accessible through the Deployment and the Sensor.

### The case of _ex situ_ observation
  The _ex situ_ example (diagrams/NEW SW_DO_pH_Observation.png and Aligned_NEW_SW_DO_pH_Observation_complete.ttl in Surfacewater/SW_ExSitu_QualityObservation) shows that there  is  no easy way to convey the observing capabilities, since no deployement and sensor are defined. In addition, the acts of sampling and sub-sampling adds a layer of indirect relation between the observation and the host of the Observing Capabilities. We know the Capability is indicating the host being the water quality station (Platform) but we know for a fact that the observation is not done there. As you can see in the Aligned_NEW_SW_DO_pH_Observation_complete.ttl , there is a try of adding a dummy sosa:Deployment as replacement of the oms:ObservingCapability. This however is factually not correct, since the sytem doing the obervation (the dummy sensor) is not really deployed in the Host (Platform), but it should be somewhere else (the Lab perhaps). The turtle should be revised to depict the real original info.
  
  In addtional, there's a need to rethink the relation between the Observation and the Host in this case. The host is indirectly linked to the observation, since it's only the place where the sampling is happening. This may give a wrong indication about the conditions in which the oberving act happended.

## Use of sosa:ObservationCollection
A further attempt ([SW_DO_pH_Collection_KS.ttl](https://github.com/opengeospatial/WaterQualityIE/blob/master/SSN_SOSA/Surfacewater/SW_ExSitu_QualityObservation/SW_DO_pH_Collection_KS.ttl)) was made using sosa:ObservationCollection as a replacement for oms:ObservingCapability. However, this runs into similar issues as the sosa:Deployment approach described above, as there is no way to link to the sosa:Platform. The only way to model this is by creating both a virtual Sensor and Deployment.
