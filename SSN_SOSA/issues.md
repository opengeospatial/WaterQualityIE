## Observing Capability limation with SSN/SOSA
In the examples of the exsitu observation (SSN_SOSA/Aligned_NEW_SW_DO_pH_Observation.ttl), the observing capability are not directly transformable into the SOSA SystemCapabilty.
In fact, the system capability require the presence of a System (Actuator, Sensor, or Sampler). From OMS point view this is not necessary. This makes the mapping to SSN/SOSA not always fully covered
The insitu example (SSN_SOSA/aligned_NEW_GW_InSitu_QualityObservation.ttl) shows that the presnece of a system (a sampler in this case) constitute the element that would glue togther the Capability with the rest of the resources  
