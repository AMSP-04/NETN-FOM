# NETN-CBRN
NATO Education and Training Network (NETN) Chemical, Biological, Radiological, Nuclear (CBRN) Module

Copyright (C) 2020 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

## Introduction

CBRN is Chemical, Biological, Radiological and Nuclear materials that can be delivered intentionally as a weapon using conventional bombs, explosive materials and enhanced blast weapons (e.g., dirty bombs) or unintentionally caused by human error or natural or technological reasons, such as spills, accidental releases or leakages. 

The NATO Education and Training Network CBRN Module (NETN-CBRN) is a specification of how to model CBRN related concepts in a federated distributed simulation. 

The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and primarily intended to support interoperability in a federated simulation (federation) based on HLA. A Federation Object Model (FOM) Module is used to specify how data is represented and exchanged in the federation. The NETN-CBRN FOM module is available as an XML file for use in HLA based federations.

### Purpose

NETN-CBRN provides a standard interface for the representation of CBRN release, detection, effects, and protective measures in a federated distributed simulation. E.g. the exposure effect on individual humans in a CBRN contaminated Hazard area where the humans are represented in one simulation, and the effect is modelled in another.

### Scope

The NETN-CBRN FOM module covers:

1.  CBRN Source release modelling
2.  CBRN Detector modelling
3.  CBRN Effects modelling
4.  CBRN Protective measures modelling
5.  Hazard area modelling

Meteorological conditions and CBRN material properties for modelling the dispersion of CBRN material are not explicitly represented in the NETN-CBRN FOM Module. NETN-METOC FOM module can be used to model weather conditions that may impact the dispersion of CBRN materials and cause dynamic change to hazard areas.

### Overview

Considerations have been made as to how the CBRN FOM module can be used by legacy systems that cannot be updated to implement the CBRN FOM module. These considerations have resulted in the CBRN FOM module, including interactions that mirror the changes that can be made to objects. These interactions allow for a translation federate to sit between the CBRN and simulation federate to translate the CBRN data into data that the simulation federate can understand.

<img src="./images/interactions.png" width="800px"/>

**Figure: CBRN Interaction Classes**


## CBRN Source Release Modelling

### CBRN Release


The `CBRN_Release` interaction includes all of the CBRN source release information required for a CBRN federate to model a CBRN source release.

<img src="./images/cbrn_release.png" width="350px"/>



### CBRN Warheads on Conventional Munitions

Ideally, the `CBRN_Release` interaction would be sent from a simulation federate to the CBRN federate to inform it that a release had occurred, allowing the CBRN federate to model the release. However, if a legacy simulation federate that can’t be updated to use the CBRN FOM module is being used, then the `MunitionDetonation` from the RPR FOM can be used instead. In this situation an additional federate will be created that can subscribe to the `MunitionDetonation` interactions and use the `WarheadType` parameter to check that the `MunitionDetonation` is a CBRN release. If it is a CBRN release then the additional federate will create a `CBRN_Release` using the `WarheadType` parameter, and publish the `CBRN_Release` interaction allowing the CBRN federate to start its CBRN modelling.

The `CBRN_Release` interaction acts as a trigger for starting the simulation of a CBRN release event.

<img src="./images/release.svg" width="1000px"/>

**Figure: Triggering a CBRN Release**
<!--
participant CBRN Mediation
participant CGF
participant CBRN
autonumber 1
alt CBRN aware CGF
CGF->CBRN:CBRN_Release(UniqueID, Agent, Location, Mass, \nDuration, ReleaseSize, ReleaseDynamics, ReleaseVelocity)
else legacy RPR CGF
CGF->CBRN Mediation:RPR-Warfare::MunitionDetonation(WarheadType, ...)
CBRN Mediation->CBRN:CBRN_Release(UniqueID, Agent, Location, Mass, Duration, ReleaseSize, ReleaseDynamics, ReleaseVelocity)
end
autonumber off
-->

1. The `CBRN_Release` interaction can be sent directly from a CBRN aware CGF to inform a CBRN federate that a release has occurred. 

However, in some federations, an intermediate step is required to support the generation of the `CBRN_Release` interaction. 

2. A legacy RPR based CGF, not aware of NETN-CBRN concepts, can generate an RPR-Warfare `MunitionDetonation` interaction. 
3. A CBRN Mediation federate receives the `MunitionDetonation`. If the `WarheadType` parameter indicates that it is a CBRN release, then the CBRN Mediation federate sends the `CBRN_Release` interaction.


## Detector Modelling

There are two use cases for a detector in an HLA simulation:
1.  The first is for detector properties to be created and published by a simulation federate. A detector model within a CBRN federate would calculate the detector readings and publish the alarm status. This process would use the CBRN_Detector object and CBRN_DetectorAlarm interaction.
2.  The second would have a complete detector model in a federate; this would request concentration readings from a CBRN federate and calculate its alarm status. This would use the CBRN_Sensor object and CBRN_SensorUpdate interaction.

<img src="./images/detectorobjects.png" width="800px"/>

Figure: CBRN Detector Objects.

Both the `CBRN_Detector` and `CBRN_Sensor` objects extend the BaseEntity.PhysicalEntity.Sensor object in the RPR Physical FOM module.
 
### CBRN_Detector

The `CBRN_Detector` object is used when a CGF creates a detector with a CBRN federate performing the modelling of the detector. When the federate controlling the detector calculates a concentration above a threshold, it will issue a `CBRN_DetectorAlarm` interaction.

### CBRN_Sensor

The `CBRN_Sensor` object is used when there is a detector federate performing the modelling of the detector. The `CBRN_Sensor` registers the agents that it is interested in and receives readings in the form of a `CBRN_SensorUpdate` interaction.
 
<img src="./images/detectorinteractions.png" width="600px"/>

Figure: CBRN Detector Interactions.



## CBRN Effects Modelling

Previous systems utilising HLA as the interoperability mechanism have used representations of damage from existing object models for representing kinetic weapons to represent CBRN exposure. The representation of damage from kinetic models does not necessarily map well to represent CBRN exposure.

This section presents the use cases and data types for CBRN casualty modelling.

### Lifeform CBRN Effects Modelling

The `CBRN_Human` object is an extension of the `NETN_Human` object from the NETN Physical FOM module. The CBRN federate will update the appropriate attributes as the casualty state of the entity changes. The TriageLevel uses the NATO representation of triage category scores. The IPEType attribute denotes the level of Individual Protective Equipment (IPE) that the unit is wearing. These levels are those defined by the Nuclear, Biological and Chemical (NBC) dress states.
 
<img src="./images/cbrn_human.png" width="400px%"/>

Figure: CBRN_Human Object.


The `CBRN_Casualty` interaction is provided to give support to legacy systems that do not use the CBRN FOM module. A translation federate can then map the `CBRN_Casualty` interaction into a data type that the legacy system can handle.

<img src="./images/cbrn_casualty.png" width="350px"/>

Figure: CBRN_Casualty Interaction.

The triage levels used in the `CBRNDamageEnum8` enumeration uses the ‘T system’ to denote the priority of treatment for casualties where the levels are defined as:
*   T3 – Delayed priority.
*   T2 – Urgent priority.
*   T1 – Immediate priority.
*   T4 – Expectant priority (treatment would be ineffective).

### CBRN Platforms 

To calculate further contamination and exposure for a platform, extensions are made to seven NETN leaf nodes in the NETN Physical FOM module. These are all extensions of the Platform object from the RPR Physical FOM module. Each extension contains an array of the mass of all materials that are contaminating the vehicle.

<img src="./images/cbrn_platform.png" />

Figure: CBRN Platform Objects.


Using the same pattern as that used for the `CBRN_Human` object, the contaminating mass inside a platform due to embedded units can be updated by an external federate using the `CBRN_PlatformUpdate` interaction.
 
 <img src="./images/cbrn_platformupdate.png" width="350px" />

Figure: CBRN_PlatformUpdate Interaction.

## Protective Measures Modelling

The use case for protective measures covers both the modelling of CBRN treatment and the modelling of CBRN protective equipment. This includes both individual (i.e. a respirator) and collective protection (i.e. Collective Protection (COLPRO)).

The `COLPRO` and `DecontaminationStation` object classes extends the `NETN_CulturalFeature` object class and provides information on how many entities it can contain as well as what agents it provides protection against.
 
<img src="./images/cbrn_protectobjects.png" width="700px" />

Figure: CBRN Protective Measures Objects.

### Protective Measures Interactions

<img src="./images/cbrn_protectinteractions.png" width="800px" />

Figure: CBRN Protective Measures Interactions.

The `CBRN_FacilityUpdate` interactions allows entities to be instructed to enter or leave a CBRN facility.

* The `COLPROUpdate` interaction extends the CBRN_FacilityUpdate and allows entities to be instructed to enter or leave a COLPRO object.
* The `DecontaminationStationUpdate` interaction extends the CBRNFacilityUpdate and allows entities to be instructed to enter or leave a DecontaminationStation object.

The `IPECommand` interaction allows entities to be instructed to don IPE by an external federate.

The `CBRN_TreatmentCommand` can be used for both pre-mission countermeasures and for treatment to be applied post-exposure. The `CBRN_Human` object has an attribute which denotes the treatments that have been applied to the unit.
 
## Hazard Area Modelling

The modelling of hazard areas allows the representation of a contamination area to be sent to a simulation federate in the simplest possible form. This could be in the form of:

* The output from a hazard prediction algorithm (a warning area defined in Allied Tactical Publication (ATP)-45) in response to a detector alarm or observation.
*   Raw output from a dispersion model (contours) during a simulation run.

<img src="./images/cbrn_hazard.png" width="700px" />

Figure: CBRN Hazard Area Objects.

The `ATP45HazardArea` object represents the hazard region as calculated by a warning and reporting model. Currently, only a subset of the ATP-45 definition is used.

The `ProbabilityHazardContourGroup` object provides a representation of the hazard area of the casualty effects of this CBRN hazard, calculated from the properties of the particular material.

The `RawDataHazardContourGroup` object provides a representation of the raw dispersion output, which is purely the quantity of the material calculated by a dispersion model.