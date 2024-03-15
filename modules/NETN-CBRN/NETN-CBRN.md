
# NETN-CBRN
|Version| Date| Dependencies|
|---|---|---|
|v2.0|2024-03-10|RPR-Physical, NETN-DIM, NETN-BASE, NETN-ETR|

The NATO Education and Training Network Chemical, Biological, Radiological and Nuclear (NETN-CBRN) provides a standard interface for representing CBRN release, detection, effects, and protective measures in a federated distributed simulation. E.g., the exposure effect on individual humans in a CBRN-contaminated Hazard area where the human is represented in one simulation and the effect is modelled in another federate simulation.

CBRN are Chemical, Biological, Radiological and Nuclear materials that can be delivered intentionally as a weapon using conventional bombs, explosive materials and enhanced blast weapons (e.g., dirty bombs) or unintentionally caused by human error or natural or technological reasons, such as spills, accidental releases or leakages. 

The NETN-CBRN module specifies how to model CBRN-related events in a federated distributed simulation.



## Overview 
 
The NETN-CBRN FOM module covers: 
1.	CBRN Source release modelling 
2.	CBRN Detector modelling 
3.	CBRN Effects modelling 
4.	CBRN Protective measures modelling 
5.	Hazard area modelling 
 
The NETN-METOC module can model weather conditions that may impact the dispersion of CBRN materials and cause dynamic change to hazard areas. 
 
## Contamination 
 
The NETN-CBRN module provides modelling of CBRN contamination related to individual simulated `Platform` entities and `CBRN_Hazard` regions. 
 
```mermaid 
classDiagram 
direction LR 
 
HLAobjectRoot <|-- BaseEntity 
HLAobjectRoot <|-- DIM_HazardRegion 
HLAobjectRoot : UniqueId(NETN-BASE) 
HLAobjectRoot : CreateTime(NETN-BASE) 
BaseEntity <|-- PhysicalEntity 
BaseEntity : EntityIdentifier(RPR-BASE) 
BaseEntity : EntityType(RPR-BASE) 
BaseEntity : Spatial(RPR-BASE) 
PhysicalEntity <|-- Platform 
Platform : Contamination 
DIM_HazardRegion <|-- CBRN_Hazard 
DIM_HazardRegion : Area(NETN-DIM) 
CBRN_Hazard : AgentType 
CBRN_Hazard : Contours 
CBRN_Hazard : ExposureType 
CBRN_Hazard : HazardType 
PhysicalEntity <|-- Lifeform 
Lifeform <|-- Human 
Human : Exposures 
 
``` 
 
A `CBRN_Release` event triggers the start of a CBRN-related event and indicates parameters used to initiate the modelling of a `CBRN_Hazard`. As contamination spreads in the environment, the `CBRN_Hazard` objects are updated, simulated platforms located in CBRN-affected regions are contaminated, and lifeforms are exposed. 
 
```mermaid 
classDiagram 
direction LR 
HLAinteractionRoot <|-- SMC_EntityControl 
HLAinteractionRoot <|-- CBRN_Release 
HLAinteractionRoot : SendTime(NETN-BASE) 
HLAinteractionRoot : UniqueId(NETN-BASE) 
SMC_EntityControl <|-- SetPlatformContamination 
SMC_EntityControl : Entity(NETN-SMC) 
SetPlatformContamination : Contamination 
SMC_EntityControl <|-- SetCasualtyEffect 
SetCasualtyEffect : Exposures 
CBRN_Release : Agent 
CBRN_Release : Duration 
CBRN_Release : Location 
CBRN_Release : Mass 
CBRN_Release : ReleaseDynamics 
CBRN_Release : ReleaseSize 
CBRN_Release : ReleaseVelocity 
``` 
 
The platform contamination and lifeform exposure are usually simulated but can also be set explicitly using NETN-SMC entity control interactions. Use the `SetPlatformContamination` interaction to set the `Platform` contamination level. Use `SetCausaltyEffect` to set `Lifeform` exposure levels. 
 
## Protection and Treatment 
Individual `Lifeform` objects are extended with attributes related to CBRN exposure and treatments. Facilities providing protection and treatment are modelled using `DecontamiationStation` or CollectiveProtection `COLPRO` objects. 
 
```mermaid 
classDiagram 
direction LR 
 
HLAobjectRoot <|-- BaseEntity 
 
HLAobjectRoot : UniqueId(NETN-BASE) 
BaseEntity <|-- PhysicalEntity 
BaseEntity : EntityIdentifier(RPR-BASE) 
BaseEntity : EntityType(RPR-BASE) 
BaseEntity : Spatial(RPR-BASE) 
PhysicalEntity <|-- Lifeform 
Lifeform <|-- Human 
 
 
PhysicalEntity <|-- CulturalFeature 
 
Human : IPEType 
Human : Treatments 
Human : TriageLevel 
 
 
CulturalFeature <|-- COLPRO 
CulturalFeature <|-- DecontaminationStation 
CulturalFeature : Capacity 
COLPRO : Protection 
DecontaminationStation : DecontaminationPeriod 
DecontaminationStation : Treatments 
 
 
``` 
 
Two NETN-ETR `Task` subclasses related to protection and treatment are defined in the NETN-CBRN module. Use the `ApplyIPE` task to request a `Lifeform` to apply individual protection equipment. Use the `AdministerTreatment` task to request an entity to initiate the treatment of a set of entities. 
 
```mermaid 
classDiagram 
direction LR 
HLAinteractionRoot <|-- SMC_EntityControl 
HLAinteractionRoot : SendTime(NETN-BASE) 
HLAinteractionRoot : UniqueId(NETN-BASE) 
SMC_EntityControl <|-- Task 
 
SMC_EntityControl <|-- SetCasualtyEffect 
 
SetCasualtyEffect : TriageLevel 
SMC_EntityControl : Entity(NETN-SMC) 
Task <|-- ApplyIPE 
Task <|-- AdministerTreatment 
Task : TaskId(NETN-ETR) 
ApplyIPE : TaskParameters 
AdministerTreatment : TaskParameters 
``` 
 
## Detection and Alarm 
 
The NETN-CBRN can represent CBRN sensors and detectors as `Sensor` objects in the federation. These objects define, e.g., the type of `DetectableAgents` and are used to share aspects of the individual equipment to a CBRN simulation that can generate corresponding sensor events. 
 
```mermaid 
classDiagram 
direction LR 
 
HLAobjectRoot <|-- BaseEntity 
HLAobjectRoot : UniqueId(NETN-BASE) 
BaseEntity <|-- PhysicalEntity 
BaseEntity : EntityIdentifier(RPR-BASE) 
BaseEntity : EntityType(RPR-BASE) 
BaseEntity : Spatial(RPR-BASE) 
PhysicalEntity <|-- Sensor 
Sensor <|-- CBRN_Detector 
Sensor <|-- CBRN_Sensor 
CBRN_Detector : Alarm 
CBRN_Detector : AveragingTime 
CBRN_Detector : DetectableAgents 
CBRN_Detector : ProcessingTime 
CBRN_Sensor : AveragingTime 
CBRN_Sensor : DetectableAgents 
CBRN_Sensor : SensorReadings 
CBRN_Sensor : UpdateFrequency 
``` 
 
A CBRN federate can generate a `CBRN_DetectorAlarm` event to indicate a detected agent at a specific location. A CBRN federate can also generate a `CBRN_SensorUpdate` event to indicate the concentration of a specific agent. 
 
 
```mermaid 
classDiagram 
direction LR 
HLAinteractionRoot <|-- ETR_SensorEvent 
HLAinteractionRoot : SendTime(NETN-BASE) 
HLAinteractionRoot : UniqueId(NETN-BASE) 
 
ETR_SensorEvent <|-- CBRN_SensorUpdate 
ETR_SensorEvent <|-- CBRN_DetectorAlarm 
ETR_SensorEvent : ProducingEntity(NETN-ETR) 
CBRN_SensorUpdate : Agent 
CBRN_SensorUpdate : Concentration 
CBRN_DetectorAlarm : Agent 
CBRN_DetectorAlarm : Location 
``` 
 
 
## Prediction 
 
The NETN-CBRN module also supports the `CBRN_Hazard_Prediction` object class to predict CBRN hazard regions. A prediction model can publish instances of this object to indicate a potential CBRN hazard.
 
```mermaid 
classDiagram 
direction LR 
 
HLAobjectRoot <|-- DIM_HazardRegion 
HLAobjectRoot : UniqueId(NETN-BASE) 
HLAobjectRoot : CreateTime(NETN-BASE) 
 
DIM_HazardRegion <|-- CBRN_Hazard_Prediction 
DIM_HazardRegion : Area(NETN-DIM) 
 
CBRN_Hazard_Prediction : ATP45HazardAreaType 
CBRN_Hazard_Prediction : AgentClass 
CBRN_Hazard_Prediction : Duration 
```


## Object Classes

```mermaid
classDiagram 
direction LR

HLAobjectRoot <|-- BaseEntity
HLAobjectRoot <|-- DIM_HazardRegion
HLAobjectRoot : CreateTime(NETN-BASE)
HLAobjectRoot : UniqueId(NETN-BASE)
BaseEntity <|-- PhysicalEntity
BaseEntity : EntityIdentifier(RPR-BASE)
BaseEntity : EntityType(RPR-BASE)
BaseEntity : Spatial(RPR-BASE)
PhysicalEntity <|-- Lifeform
PhysicalEntity <|-- Sensor
PhysicalEntity <|-- Platform
PhysicalEntity <|-- CulturalFeature
Lifeform <|-- Human
Human : Exposures
Human : IPEType
Human : Treatments
Human : TriageLevel
Sensor <|-- CBRN_Detector
Sensor <|-- CBRN_Sensor
CBRN_Detector : Alarm
CBRN_Detector : AveragingTime
CBRN_Detector : DetectableAgents
CBRN_Detector : ProcessingTime
CBRN_Sensor : AveragingTime
CBRN_Sensor : DetectableAgents
CBRN_Sensor : SensorReadings
CBRN_Sensor : UpdateFrequency
Platform : Contamination
CulturalFeature <|-- COLPRO
CulturalFeature <|-- DecontaminationStation
CulturalFeature : Capacity
COLPRO : Protection
DecontaminationStation : DecontaminationPeriod
DecontaminationStation : Treatments
DIM_HazardRegion <|-- CBRN_Hazard
DIM_HazardRegion <|-- CBRN_Hazard_Prediction
DIM_HazardRegion : Area(NETN-DIM)
CBRN_Hazard : AgentType
CBRN_Hazard : Contours
CBRN_Hazard : ExposureType
CBRN_Hazard : HazardType
CBRN_Hazard_Prediction : ATP45HazardAreaType
CBRN_Hazard_Prediction : AgentClass
CBRN_Hazard_Prediction : Duration
```

### Human

A human lifeform.

|Attribute|Datatype|Semantics|
|---|---|---|
|Exposures|ArrayOfCBRNExposureStruct|Array of agents to which this entity has been exposed to. Defaults to an empty array.|
|IPEType|IPETypeEnum8|Type of IPE that the entity is using. Defaults to None.|
|Treatments|ArrayOfTreatmentStruct|The types of treatment that this entity has used. Defaults to an empty array.|
|TriageLevel|CBRNDamageEnum8|Triage level of this entity. Defaults to Uninjured.|
|CreateTime<br/>(NETN-BASE)|EpochTime|Optional: The time in the scenario when the object is created.| 
|EntityIdentifier<br/>(RPR-BASE)|EntityIdentifierStruct|The unique identifier for the entity instance.| 
|EntityType<br/>(RPR-BASE)|EntityTypeStruct|The category of the entity.| 
|Spatial<br/>(RPR-BASE)|SpatialVariantStruct|Spatial state stored in one variant record attribute.| 
|UniqueId<br/>(NETN-BASE)|UUID|Required. A unique identifier for the object. The Universally Unique Identifier (UUID) is generated or pre-defined.| 

### CBRN_Detector

Represents a CBRN detector. This object is used to pass information to a CBRN federate, which will model the detector internally and publish a CBRN_DetectorAlarm.

|Attribute|Datatype|Semantics|
|---|---|---|
|Alarm|CBRNAlarmStruct|Data representing the alarm of this detector. Defaults to no alarm if the attribute is not set.|
|AveragingTime|TimeSecondInteger32|Duration the detector will collect samples.|
|DetectableAgents|ArrayOfAgentConcentrationStruct|Array of detectable agents and their thresholds.|
|ProcessingTime|TimeSecondInteger32|Duration between the detector being exposed to a concentration of agent above its threshold and the detector raising an alarm.|
|CreateTime<br/>(NETN-BASE)|EpochTime|Optional: The time in the scenario when the object is created.| 
|EntityIdentifier<br/>(RPR-BASE)|EntityIdentifierStruct|The unique identifier for the entity instance.| 
|EntityType<br/>(RPR-BASE)|EntityTypeStruct|The category of the entity.| 
|Spatial<br/>(RPR-BASE)|SpatialVariantStruct|Spatial state stored in one variant record attribute.| 
|UniqueId<br/>(NETN-BASE)|UUID|Required. A unique identifier for the object. The Universally Unique Identifier (UUID) is generated or pre-defined.| 

### CBRN_Sensor

Represents a CBRN sensor. This object is used to pass information to a CBRN federate, which will return sensor readings by publishing CBRN_SensorUpdate interactions.

|Attribute|Datatype|Semantics|
|---|---|---|
|AveragingTime|TimeSecondInteger32|Duration the sensor will collect samples.|
|DetectableAgents|ArrayOfAgentTypeEnum|Array of agents that this sensor wishes to detect.|
|SensorReadings|ArrayOfCBRNSensorReadingStruct|Latest sensor readings. Defaults to no readings if this attribute is not set.|
|UpdateFrequency|TimeSecondInteger32|Duration that this sensor would like between updated readings.|
|CreateTime<br/>(NETN-BASE)|EpochTime|Optional: The time in the scenario when the object is created.| 
|EntityIdentifier<br/>(RPR-BASE)|EntityIdentifierStruct|The unique identifier for the entity instance.| 
|EntityType<br/>(RPR-BASE)|EntityTypeStruct|The category of the entity.| 
|Spatial<br/>(RPR-BASE)|SpatialVariantStruct|Spatial state stored in one variant record attribute.| 
|UniqueId<br/>(NETN-BASE)|UUID|Required. A unique identifier for the object. The Universally Unique Identifier (UUID) is generated or pre-defined.| 

### Platform

A physical object under the control of armed forces upon which sensor, communication, or weapon systems may be mounted.

|Attribute|Datatype|Semantics|
|---|---|---|
|Contamination|ArrayOfAgentMassStruct|CBRN hazardous agent inside vehicle due to embedded units.|
|CreateTime<br/>(NETN-BASE)|EpochTime|Optional: The time in the scenario when the object is created.| 
|EntityIdentifier<br/>(RPR-BASE)|EntityIdentifierStruct|The unique identifier for the entity instance.| 
|EntityType<br/>(RPR-BASE)|EntityTypeStruct|The category of the entity.| 
|Spatial<br/>(RPR-BASE)|SpatialVariantStruct|Spatial state stored in one variant record attribute.| 
|UniqueId<br/>(NETN-BASE)|UUID|Required. A unique identifier for the object. The Universally Unique Identifier (UUID) is generated or pre-defined.| 

### CulturalFeature

Engineering and natural effects such as craters, bridges, vehicle tracks, etc.

|Attribute|Datatype|Semantics|
|---|---|---|
|Capacity|QuantityInt32|Required: The number of entities that this cultural feature can handle.|
|CreateTime<br/>(NETN-BASE)|EpochTime|Optional: The time in the scenario when the object is created.| 
|EntityIdentifier<br/>(RPR-BASE)|EntityIdentifierStruct|The unique identifier for the entity instance.| 
|EntityType<br/>(RPR-BASE)|EntityTypeStruct|The category of the entity.| 
|Spatial<br/>(RPR-BASE)|SpatialVariantStruct|Spatial state stored in one variant record attribute.| 
|UniqueId<br/>(NETN-BASE)|UUID|Required. A unique identifier for the object. The Universally Unique Identifier (UUID) is generated or pre-defined.| 

### COLPRO

Represents a feature that provides Collective Protection (COLPRO) against a CBRN threat.

|Attribute|Datatype|Semantics|
|---|---|---|
|Capacity|QuantityInt32|Required: The number of entities that this cultural feature can handle.|
|Protection|ArrayOfProtectionEffectivenessStruct|The effectiveness that this COLPRO offers for each agent.|
|CreateTime<br/>(NETN-BASE)|EpochTime|Optional: The time in the scenario when the object is created.| 
|EntityIdentifier<br/>(RPR-BASE)|EntityIdentifierStruct|The unique identifier for the entity instance.| 
|EntityType<br/>(RPR-BASE)|EntityTypeStruct|The category of the entity.| 
|Spatial<br/>(RPR-BASE)|SpatialVariantStruct|Spatial state stored in one variant record attribute.| 
|UniqueId<br/>(NETN-BASE)|UUID|Required. A unique identifier for the object. The Universally Unique Identifier (UUID) is generated or pre-defined.| 

### DecontaminationStation

Represents a feature that provides treatment for CBRN exposure.

|Attribute|Datatype|Semantics|
|---|---|---|
|Capacity|QuantityInt32|Required: The number of entities that this cultural feature can handle.|
|DecontaminationPeriod|TimeSecondInteger32|Required: Duration it takes to decontaminate an entity.|
|Treatments|ArrayOfTreatmentStruct|Required: The types of treatment that this decontamination station currently offers.|
|CreateTime<br/>(NETN-BASE)|EpochTime|Optional: The time in the scenario when the object is created.| 
|EntityIdentifier<br/>(RPR-BASE)|EntityIdentifierStruct|The unique identifier for the entity instance.| 
|EntityType<br/>(RPR-BASE)|EntityTypeStruct|The category of the entity.| 
|Spatial<br/>(RPR-BASE)|SpatialVariantStruct|Spatial state stored in one variant record attribute.| 
|UniqueId<br/>(NETN-BASE)|UUID|Required. A unique identifier for the object. The Universally Unique Identifier (UUID) is generated or pre-defined.| 

### CBRN_Hazard

A generic representation of a CBRN Hazard.

|Attribute|Datatype|Semantics|
|---|---|---|
|AgentType|AgentTypeEnum16|Requierd: Agent reflected in this contour.|
|Contours|ArrayOfContourStruct|Optional: Array of contours. These should be ordered in a sequence of ascending PercentProbabilityLevel.|
|ExposureType|ExposureTypeEnum8|Optional: The type of exposure.|
|HazardType|HazardTypeEnum8|Type of hazard.|
|Area<br/>(NETN-DIM)|GeodeticPolygon|Required: Geographical boundary of the HazardRegion.| 
|CreateTime<br/>(NETN-BASE)|EpochTime|Optional: The time in the scenario when the object is created.| 
|UniqueId<br/>(NETN-BASE)|UUID|Required. A unique identifier for the object. The Universally Unique Identifier (UUID) is generated or pre-defined.| 

### CBRN_Hazard_Prediction

Represents the footprint generated by a CBRN warning and reporting simulation. This follows the NATO ATP-45 doctrine to generate a hazard area.

|Attribute|Datatype|Semantics|
|---|---|---|
|ATP45HazardAreaType|ATP45HazardAreaTypeEnum8|This hazard area's type|
|AgentClass|AgentClassEnum8|The agent class|
|Duration|TimeSecondInteger32|Duration  that this hazard prediction is valid.|
|Area<br/>(NETN-DIM)|GeodeticPolygon|Required: Geographical boundary of the HazardRegion.| 
|CreateTime<br/>(NETN-BASE)|EpochTime|Optional: The time in the scenario when the object is created.| 
|UniqueId<br/>(NETN-BASE)|UUID|Required. A unique identifier for the object. The Universally Unique Identifier (UUID) is generated or pre-defined.| 

## Interaction Classes

```mermaid
classDiagram 
direction LR
HLAinteractionRoot <|-- SMC_EntityControl
HLAinteractionRoot <|-- CBRN_Release
HLAinteractionRoot <|-- ETR_SensorEvent
HLAinteractionRoot : SendTime(NETN-BASE)
HLAinteractionRoot : UniqueId(NETN-BASE)
SMC_EntityControl <|-- Task
SMC_EntityControl <|-- SetPlatformContamination
SMC_EntityControl <|-- SetCasualtyEffect
SMC_EntityControl : Entity(NETN-SMC)
Task <|-- ApplyIPE
Task <|-- AdministerTreatment
Task : TaskId(NETN-ETR)
ApplyIPE : TaskParameters
AdministerTreatment : TaskParameters
SetPlatformContamination : Contamination
SetCasualtyEffect : Exposures
SetCasualtyEffect : TriageLevel
CBRN_Release : Agent
CBRN_Release : Duration
CBRN_Release : Location
CBRN_Release : Mass
CBRN_Release : ReleaseDynamics
CBRN_Release : ReleaseSize
CBRN_Release : ReleaseVelocity
ETR_SensorEvent <|-- CBRN_SensorUpdate
ETR_SensorEvent <|-- CBRN_DetectorAlarm
ETR_SensorEvent : ProducingEntity(NETN-ETR)
CBRN_SensorUpdate : Agent
CBRN_SensorUpdate : Concentration
CBRN_DetectorAlarm : Agent
CBRN_DetectorAlarm : Location
```

### ApplyIPE

Represents an task for the specified entities to use individual protective equipment.

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|ApplyIPETaskStruct|Required: Task parameters.|
|Entity<br/>(NETN-SMC)|UUID|Required: Reference to a simulation entity for which the control action is intended.| 
|SendTime<br/>(NETN-BASE)|EpochTime|Optional: Scenario time when the interaction was sent. Default is interpreted as the receivers scenario time when the interaction is received. Required for all CBRN related interactions.| 
|TaskId<br/>(NETN-ETR)|UUID|Required. Unique identifier for the task.| 
|UniqueId<br/>(NETN-BASE)|UUID|Optional: A unique identifier for the interaction. Required for all CBRN related interactions.| 

### AdministerTreatment

Represents an order for the specified entities to receive the list of treatments.

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|AdministerTreatmentTaskStruct|Required: Task parameters.|
|Entity<br/>(NETN-SMC)|UUID|Required: Reference to a simulation entity for which the control action is intended.| 
|SendTime<br/>(NETN-BASE)|EpochTime|Optional: Scenario time when the interaction was sent. Default is interpreted as the receivers scenario time when the interaction is received. Required for all CBRN related interactions.| 
|TaskId<br/>(NETN-ETR)|UUID|Required. Unique identifier for the task.| 
|UniqueId<br/>(NETN-BASE)|UUID|Optional: A unique identifier for the interaction. Required for all CBRN related interactions.| 

### SetPlatformContamination

Represents an update to the contaminating mass inside a vehicle due to embedded entities.

|Parameter|Datatype|Semantics|
|---|---|---|
|Contamination|ArrayOfAgentMassStruct|New state of CBRN hazardous agent inside vehicle due to embedded units.|
|Entity<br/>(NETN-SMC)|UUID|Required: Reference to a simulation entity for which the control action is intended.| 
|SendTime<br/>(NETN-BASE)|EpochTime|Optional: Scenario time when the interaction was sent. Default is interpreted as the receivers scenario time when the interaction is received. Required for all CBRN related interactions.| 
|UniqueId<br/>(NETN-BASE)|UUID|Optional: A unique identifier for the interaction. Required for all CBRN related interactions.| 

### SetCasualtyEffect

Informs the federate representing the entity of the casualty effects of exposure.

|Parameter|Datatype|Semantics|
|---|---|---|
|Exposures|ArrayOfCBRNExposureStruct|Optional: Array of agents to which this unit has been exposed.|
|TriageLevel|CBRNDamageEnum8|Required: Triage level of this entity.|
|Entity<br/>(NETN-SMC)|UUID|Required: Reference to a simulation entity for which the control action is intended.| 
|SendTime<br/>(NETN-BASE)|EpochTime|Optional: Scenario time when the interaction was sent. Default is interpreted as the receivers scenario time when the interaction is received. Required for all CBRN related interactions.| 
|UniqueId<br/>(NETN-BASE)|UUID|Optional: A unique identifier for the interaction. Required for all CBRN related interactions.| 

### CBRN_Release

Communicates information associated with the release of hazardous agent.

|Parameter|Datatype|Semantics|
|---|---|---|
|Agent|AgentTypeEnum16|The type of released CBRN hazardous agent.|
|Duration|TimeSecondInteger32|Duration the release takes place.|
|Location|LocationStruct|Initial location of the release in the geocentric location system.|
|Mass|MassKilogramFloat32|Total released agent mass in kg.|
|ReleaseDynamics|ReleaseDynamicsStruct|Temperature differance and density ratio of released material relative to the atmosphere.|
|ReleaseSize|ReleaseSizeStruct|The initial size of the release including initial Gaussian sigmas of the released puff and mean & variance of released particles.|
|ReleaseVelocity|VelocityVectorStruct|Velocity of the source term.|
|SendTime<br/>(NETN-BASE)|EpochTime|Optional: Scenario time when the interaction was sent. Default is interpreted as the receivers scenario time when the interaction is received. Required for all CBRN related interactions.| 
|UniqueId<br/>(NETN-BASE)|UUID|Optional: A unique identifier for the interaction. Required for all CBRN related interactions.| 

### CBRN_SensorUpdate

Sends information about the current state of a previously registered CBRN sensor.

|Parameter|Datatype|Semantics|
|---|---|---|
|Agent|AgentTypeEnum16|Required: Type of the agent.|
|Concentration|MassConcentrationFloat32|Required: Mean Concentration in kg m-3.|
|ProducingEntity<br/>(NETN-ETR)|UUID|Optional: Reference to an entity with a sensor producing the sensor event. Default is no specific entity referenced.| 
|SendTime<br/>(NETN-BASE)|EpochTime|Optional: Scenario time when the interaction was sent. Default is interpreted as the receivers scenario time when the interaction is received. Required for all CBRN related interactions.| 
|UniqueId<br/>(NETN-BASE)|UUID|Optional: A unique identifier for the interaction. Required for all CBRN related interactions.| 

### CBRN_DetectorAlarm

Represents the alarm trigger of a previously registered CBRN detector.

|Parameter|Datatype|Semantics|
|---|---|---|
|Agent|AgentTypeEnum16|Enumeration representation of the agent.|
|Location|LocationStruct|Required: Location of the detection (location of Detector)|
|ProducingEntity<br/>(NETN-ETR)|UUID|Optional: Reference to an entity with a sensor producing the sensor event. Default is no specific entity referenced.| 
|SendTime<br/>(NETN-BASE)|EpochTime|Optional: Scenario time when the interaction was sent. Default is interpreted as the receivers scenario time when the interaction is received. Required for all CBRN related interactions.| 
|UniqueId<br/>(NETN-BASE)|UUID|Optional: A unique identifier for the interaction. Required for all CBRN related interactions.| 

## Datatypes

Note that only datatypes defined in this FOM Module are listed below. Please refer to FOM Modules on which this module depends for other referenced datatypes.

### Overview
|Name|Semantics|
|---|---|
|ATP45HazardAreaTypeEnum8|Type of ATP-45 Hazard Area (simple or detailed).|
|AdministerTreatmentTaskStruct|Task-specific data.|
|AgentClassEnum8|Class of Agent for an ATP-45 Hazard Area.|
|AgentConcentrationStruct|Concentration value associated with a specific agent.|
|AgentMassStruct|Mass of contaminant inside a vehicle brought in by an embedded unit.|
|AgentTypeEnum16|Type of CBRN hazardous agent.|
|ApplyIPETaskStruct|Task-specific data.|
|ArrayOfAgentConcentrationStruct|Array of agents and their concentrations.|
|ArrayOfAgentMassStruct|Array of agents and their masses.|
|ArrayOfAgentTypeEnum|Array of agents.|
|ArrayOfCBRNExposureStruct|Array of agents and their dosages.|
|ArrayOfCBRNSensorReadingStruct|Array of sensor readings.|
|ArrayOfContourStruct|A set of contour boundaries defining concentration levels in ascending order.|
|ArrayOfProtectionEffectivenessStruct|Array of the protection’s effectiveness.|
|ArrayOfSigmas6|Size of the initial Gaussian puff sigma values.|
|ArrayOfTreatmentStruct|Array of TreatmentStruct types.|
|CBRNAlarmStruct|Properties of a CBRN alarm.|
|CBRNDamageEnum8|Level of damage due to CBRN exposure.|
|CBRNExposureStruct|Dosage exposure value associated with a specific agent.|
|CBRNSensorReadingStruct|Timed CBRN sensor reading.|
|ContourStruct|Countour description.|
|DensityRatioFloat32|Ratio of density of two materials in range [0, 1].|
|DosageKgSecondPerMeterCubedFloat32|Dosage in SI units.|
|EntityControlActionEnum|Enumeration of Entity Control Actions. The datatype is expected to be extended in specific modules defining additional actions.|
|ExposureFloat32|Data type for exposure.|
|ExposureTypeEnum8|Type of exposure represented in a contour group.|
|HazardTypeEnum8|Type of dispersion output represented in a contour group.|
|IPETypeEnum8|Types of Individual Protective Equipment.|
|MeanMetersFloat32|Mean of a Gaussian distribution, based on SI unit meter, unit symbol m.|
|ProtectionEffectivenessStruct|Protection effectiveness associated with a specific agent.|
|ReleaseDistributionStruct|Mean and variance of the distribution of the particles or droplets in a release.|
|ReleaseDynamicsStruct|Defines the dynamic properties of a release.|
|ReleaseSizeStruct|Defines the properties of the initial size of a release.|
|TaskDefinitionVariantRecord|Variant record for task definition data.|
|TaskProgressVariantRecord|Variant record for task progress data.|
|TreatmentStruct|Defines the properties for a CBRN treatment.|
|VarianceMetersSquaredFloat32|Variance of a Gaussian distribution, based on SI unit meter squared, unit symbol m2.|
        
### Simple Datatypes
|Name|Units|Semantics|
|---|---|---|
|DensityRatioFloat32|NA|Ratio of density of two materials in range [0, 1].|
|DosageKgSecondPerMeterCubedFloat32|Kg Second Per Meter Cubed|Dosage in SI units.|
|ExposureFloat32|NA|Data type for exposure.|
|MeanMetersFloat32|meters|Mean of a Gaussian distribution, based on SI unit meter, unit symbol m.|
|VarianceMetersSquaredFloat32|meters squared|Variance of a Gaussian distribution, based on SI unit meter squared, unit symbol m2.|
        
### Enumerated Datatypes
|Name|Representation|Semantics|
|---|---|---|
|ATP45HazardAreaTypeEnum8|HLAoctet|Type of ATP-45 Hazard Area (simple or detailed).|
|AgentClassEnum8|HLAoctet|Class of Agent for an ATP-45 Hazard Area.|
|AgentTypeEnum16|HLAinteger16BE|Type of CBRN hazardous agent.|
|CBRNDamageEnum8|HLAoctet|Level of damage due to CBRN exposure.|
|EntityControlActionEnum|HLAinteger32BE|Enumeration of Entity Control Actions. The datatype is expected to be extended in specific modules defining additional actions.|
|ExposureTypeEnum8|HLAoctet|Type of exposure represented in a contour group.|
|HazardTypeEnum8|HLAoctet|Type of dispersion output represented in a contour group.|
|IPETypeEnum8|HLAoctet|Types of Individual Protective Equipment.|
        
### Array Datatypes
|Name|Element Datatype|Semantics|
|---|---|---|
|ArrayOfAgentConcentrationStruct|AgentConcentrationStruct|Array of agents and their concentrations.|
|ArrayOfAgentMassStruct|AgentMassStruct|Array of agents and their masses.|
|ArrayOfAgentTypeEnum|AgentTypeEnum16|Array of agents.|
|ArrayOfCBRNExposureStruct|CBRNExposureStruct|Array of agents and their dosages.|
|ArrayOfCBRNSensorReadingStruct|CBRNSensorReadingStruct|Array of sensor readings.|
|ArrayOfContourStruct|ContourStruct|A set of contour boundaries defining concentration levels in ascending order.|
|ArrayOfProtectionEffectivenessStruct|ProtectionEffectivenessStruct|Array of the protection’s effectiveness.|
|ArrayOfSigmas6|LengthMeterFloat32|Size of the initial Gaussian puff sigma values.|
|ArrayOfTreatmentStruct|TreatmentStruct|Array of TreatmentStruct types.|
        
### Fixed Record Datatypes
|Name|Fields|Semantics|
|---|---|---|
|AdministerTreatmentTaskStruct|Entities, Treatment, Duration|Task-specific data.|
|AgentConcentrationStruct|MeanConcentration, Agent|Concentration value associated with a specific agent.|
|AgentMassStruct|ContaminatedMass, Agent|Mass of contaminant inside a vehicle brought in by an embedded unit.|
|ApplyIPETaskStruct|IPEType|Task-specific data.|
|CBRNAlarmStruct|Location, Agent|Properties of a CBRN alarm.|
|CBRNExposureStruct|Exposure, Agent|Dosage exposure value associated with a specific agent.|
|CBRNSensorReadingStruct|Time, Reading|Timed CBRN sensor reading.|
|ContourStruct|Boundary, ProbabilityLevel, ConcentrationLevel|Countour description.|
|ProtectionEffectivenessStruct|Effectiveness, Agent|Protection effectiveness associated with a specific agent.|
|ReleaseDistributionStruct|Mean, Variance|Mean and variance of the distribution of the particles or droplets in a release.|
|ReleaseDynamicsStruct|DensityRatio, TemperatureDifference|Defines the dynamic properties of a release.|
|ReleaseSizeStruct|SigmaArray, ReleaseDistribution|Defines the properties of the initial size of a release.|
|TreatmentStruct|Effectiveness, Duration, TreatmentWindow, TreatableAgents|Defines the properties for a CBRN treatment.|
        
### Variant Record Datatypes
|Name|Discriminant (Datatype)|Alternatives|Semantics|
|---|---|---|---|
|TaskDefinitionVariantRecord|TaskType (EntityControlActionEnum)|ApplyIPE, AdministerTreatment|Variant record for task definition data.|
|TaskProgressVariantRecord|TaskType (EntityControlActionEnum)|Treatment|Variant record for task progress data.|
    