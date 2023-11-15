# NETN-SE
Copyright (C) 2020 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

## Introduction

The NATO Education and Training Network Synthetic Environment Module (NETN-SE) is a specification of how to represent generic synthetic environment elements such as geographical locations, paths and regions in a federated distributed simulation. It also specifies how to represent facilities that represent some function or capability associated with a geographic location or a specific entity.

The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and primarily intended to support interoperability in a federated simulation (federation) based on HLA. A Federation Object Model (FOM) Module is used to specify how data is represented and exchanged in the federation. The NETN-ORG FOM module is available as an XML file for use in HLA based federations.

### Purpose

The NETN-SE FOM Module provides a common standard interface for representing persistent abstract geographical objects that can be (re-)used and referenced for specifying locations, paths, and regions. The module also includes the representation of facilities with a function or capability to perform activities.

### Scope

The current version of the NETN-SE is limited to:

- Representation of Checkpoint Facilities
- Representation of specific geographical locations, paths and regions

<img src=./images/se-objectclasses.png>

**Figure: GeoObject and Facility**

## Facility

The `SE_Facility` object class is a base class for all types of facilities. In the current version of NETN-SE the only facility represented is a `Checkpoint` facility.

|Attribtue|Description|
|---|---|
|UniqueId|**Required.** Pre-defined or generated unique identifier of the object instance.|
|LocationReference|**Required.** A reference that identifies a geographical location directly or indirectly by reference to a simulated object.|
|Name|**Optional.** Name of the facility.|
|SymbolId|**Optional.** A symbol identifier represented as a string. |
|Status|**Optional.** Specifies if the facility is active (operational) or not. Default value is 1 (Active).|
|ObjectType|**Optional.** Specifying the domain, the kind and the specific identification of the environment object.|
|ForceId|**Optional.** The force that operates the facility. Default is 0 (Other).|
|PercentComplete|**Optional.** Describes a level of completion when establishing/building of the facility. Expressed in percent [0-100]. Default is 100%.|
|DamageState|**Optional.** The damage state on the facility. Default value is 0 (NoDamage).|
|Comment|**Optional.** A descriptive text comment.|

### Checkpoint

A `CheckPoint` defines a location where simulated aggregate and physical entities should stop and wait a specified time before continuing on their route.

If the checkpoint is currently in operation, the status attribute value should be True. A system simulating the movement of a physical or an aggregate entity can either be directly affected by the checkpoint, by subscribing to its state, or indirectly by receiving a NETN-ETR `Wait` task.  

|Attribtue|Description|
|---|---|
|DelayTime|**Required.** The time that an entity shall wait at the checkpoint before passing. The time is a nominal value; federates can use this for modifying delay time for different types of entities, e.g. add or subtract a value or multiply with a type depending factor.|

## GeoObject

The `SE_GeoObject` is a representation of geographically associated locations, paths, and regions with or without a defined name. E.g. a harbour may be represented as a location with a specific name, a commonly used route can be represented as a named path and a region can be represented as a specific geographic area and reused as an object instance in the simulation.

|Attribtue|Description|
|---|---|
|UniqueId|**Required.** Unique identifier for the GeoObject.|
|Name|**Optional.** Name of the GeoObject, e.g. Location name, Road name etc.|


### Location

A location is a geographical point in latitude, longitude and altitude above mean sea level.

|Attribtue|Description|
|---|---|
|Point|**Required.** A geographical point in latitude, longitude, and altitude above mean sea level.|

### Path

A path is defined as a sequence of at least two locations. Each location in the path is defined as geodetic coordinates and altitude above the mean sea level.

|Attribtue|Description|
|---|---|
|Points|**Required.** A path with at least 2 points expressed as GeodeticPoints.|

### Region

A region is an area on the earth's surface defined by a polygon or a circle.

|Attribtue|Description|
|---|---|
|Area|**Required.** Defines the area, either as a geodetic polygon, circle or a quadrangle.|