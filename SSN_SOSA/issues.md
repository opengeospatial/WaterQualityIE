## Observing Capability limation with SSN/SOSA
  In fact, the system capability require the presence of a System (Actuator, Sensor, or Sampler). From OMS point view this is not necessary. This makes the mapping to SSN/SOSA not always fully covered

## Reflaction around the uniq nature of ObservingCapability
 Observing Capability is more of a theoritical indication of what can be observed, using what method, on what  (proximate and ultimate ) feature of interest, at what Host. Although it can point to a host, it doesn't mean that realted observations are performed directly at the host, but that it originate from there. It can omit any necessary intermediate steps steps like Sampling.
 
  The initial assumption that ssn-sytem:SystemCapability is able to cover the oms:ObservingCapability is clearly wrong. The system capability can tell in a way the technical specs of sensor for exmaple, about what it can observe, whith what method, nder what condition, etc. but it doesn't allow link to what FoI and were are we doing we CAN do the observation.

 In contrast to that, sosa:Deployment, as it is in the name, is the actual deployment of an asset/system, not just theoritical. So it can very well convey the info about the info about the capability, but not in all cases. This could be clearly seen in the differences between the inSitu and exSitu examples of surface Water quality.

## The case of ExSitu obervation
 the insitu example (diagrams/NEW SW_DO_pH_Observation.png and aligned_NEW_GW_InSitu_QualityObservation.ttl in Surfacewater/SW_InSitu_QualityObservation) shows that already a deployment and a sensor are explicitly montionned. In this case we have the actual implementation that can convey the capability info. The observing capability  (link to propety, method, FoIs and  host)  is concretly accessible through the Deployement and the sensor.

## The case of ExSitu observation
  The existu example (diagrams/NEW SW_DO_pH_Observation.png and Aligned_NEW_SW_DO_pH_Observation_complete.ttl in Surfacewater/SW_ExSitu_QualityObservation) shows that there  is  no easy way to convey the observing capabilities, since no deployement and sensor are mentionned. In addition the acts of sampling and sub-sampling  ads a layer of indirect relation between the observation and the host of the Observing Capabilities. We know the Capability is indicating the host being the water quality station (Platform) but we know for a fact that the observation is not done there. As you can see in the Aligned_NEW_SW_DO_pH_Observation_complete.ttl , there is a try of adding a dummy sosa:Deployement as replacement of the oms:ObservingCapability. This however is factually not correct, since the sytem doing the obervation (the dummy sensor) is not really deployed in the host (Plateform), but it should be somewhere else (the Lab perhaps). The tutrle should be revised to depict the real original info.
  
  In addtional, there's a need to rethink the relation between the Observation and the Host in this case. The host indectly linked to the observation, since it's only the place where the sampling is happening. This may give a wrong indication about the conditions in which the oberving act happended.
