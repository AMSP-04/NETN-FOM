
# NETN-TMR
|Version| Date| Dependencies|
|---|---|---|
|3.0|2024-03-10|NETN-BASE, NETN-ORG, NETN-SMC|

The NATO Education and Training Network Transfer of Modelling Responsibilities (NETN-TMR) module provides a standard interface and pattern for transferring modelling responsibility between federates. It extends the HLA Ownership Management services by providing the means to trigger modelling responsibility transfer and publish the assigned modelling responsibilities of object instances.
        
For example:
            
* Transfer modelling responsibility between virtual and constructive simulation systems.  
* Transfer modelling responsibility between high- and low-fidelity models.
* Transfer modelling responsibility to allow backup, maintenance or load-balancing.

In a federated distributed simulation, the participating systems (federates) provide services that model the synthetic environment. Allocation of modelling responsibilities depends on individual federate capabilities, federation design agreements, and initial scenario conditions. The primary responsibility for modelling a simulated entity is allocated to, at most, one federate. However, during execution, the modelling responsibility and ownership of individual attributes may change.

NETN-TMR covers the following cases:            
* Initialization with assigned modelling responsibilities for objects. 
* Explicit request to acquire modelling responsibility.
* Triggering modelling responsibility transfer by updating the allocation of responsibility attribute.

## Overview 
 
 
NETN-TMR extends the HLA concept of object instance attribute ownership by associating primary modelling responsibility to objects in the federation. Only one federate has the primary modelling responsibility, but the responsibility can be transferred. Primary responsibility does not require ownership (HLA ownership) of all attributes of an object. 
 
The federate with a primary responsibility shall respond to all NETN-SMC `SMC_EntityControl` actions directed to the entity. This also implies that the same federate normally publishes the `BaseEntity` attribute `SupportedActions`.

## Modelling Responsibility

The NETN-TMR modules extend the `HLAobjectRoot` object class with the attribute `AllocatedFederate`. 

```mermaid
classDiagram 
direction LR

HLAobjectRoot : AllocatedFederate
HLAobjectRoot : UniqueId(NETN-BASE)
```
 
The owner (HLA ownership) of the `AllocatedFederate` attribute is the federate with primary modelling responsibility for the object. An update of this attribute triggers the referenced federate to initiate a transfer to acquire primary modelling responsibility. 

Sending an `AcquireModellingResponsibility` interaction triggers the referenced federate to initiate a transfer. If successful, the acquiring federate owns (HLA ownership) the `AllocatedFederate` attribute and updates its value to the federate name. 


```mermaid
classDiagram 
direction LR

HLAinteractionRoot <|-- SMC_FederateControl
HLAinteractionRoot : UniqueId(NETN-BASE)
SMC_FederateControl <|-- AcquireModellingResponsibility
SMC_FederateControl : Federate(NETN-SMC)
AcquireModellingResponsibility : Entity
```

Transfer of primary modelling responsibility is impossible if no owner of the `AllocatedFederate` attribute exists. 
 
## Attribute triggered Transfer
 
An update of the `AllocatedFederate` attribute triggers the referenced federate to acquire the primary modelling responsibility. E.g. during scenario initialization, a federate may register all objects and then update the `AllocatedFederate` attributes to trigger a change in modelling responsibility. 
 
 
``` mermaid 
 
sequenceDiagram 
autonumber
Federation->>Federate 1:Update entity.AllocatedFederate = federate 1 
Federate 1->>Federation:Attribute Ownership Acquisition(entity.attributes) 
Federation->>Federate 2:Request Attribute Ownership Release(entity.attributes) 
Federate 2->>Federation:Attribute Ownership Divestiture If Wanted(entity.attributes) or <br> Attribute Ownership Release Denied(entity.attributes) 
Federation->>Federate 1:Attribute Ownership Acquisition Notification(entity.attributes) or <br> Attribute Ownership Unavailable(entity.attributes) 
 
Federate 1-->>Federation:Attribute Ownership Acquisition(entity.AllocatedFederate) 
``` 
 
1. The `AllocatedFederate` attribute update triggers the referenced federate (Federate 1) to start the acquisition of primary modelling responsibility. 
2. Use the HLA service `Attribute Ownership Acquisition` to request ownership of relevant attributes. 
3. The federate currently owning a requested attribute (Federate 2) receives a `Request Attribute Ownership Release` callback. 
4. Release the attribute using the `Attribute Ownership Divestiture If Wanted` HLA service, or if unable to release, use the `HLA Attribute Ownership Release Denied`. 
5. The HLA callback `Attribute Ownership Acquisition Notification` indicates a successful attribute ownership transfer, and the `Attribute Ownership Unavailable` callback indicates an unsuccessful transfer. 
6. Acquire the ownership of the `AllocatedFederate` attribute to complete the transfer of modelling responsibility. 
 
 
## Request Transfer
 
Sending an `AcquireModellingResponsibility` requests the referenced federate to start acquiring modelling responsibility. 

 
``` mermaid 
 
sequenceDiagram 
autonumber
 
Federation ->>Federate 1:AcquireModellingResponsibility(requestId, entity, federate 1) 
Federate 1->>Federation:HLA Attribute Ownership Acquisition(entity.attributes) 
Federation->>Federate 2:HLA Request Attribute Ownership Release(entity.attributes) 
Federate 2->>Federation:HLA Ownership Release(entity.attributes) 
Federate 2->>Federation:HLA Attribute Ownership Divestiture If Wanted(entity.attributes) 
Federation->>Federate 1:HLA Attribute Ownership Acquisition Notification(entity.attributes) 
Federate 1->>Federation:Update entity.FederateApplication 
Federate 1->>Federation:SMC_Response(requestId, TRUE) 
 
``` 
 
1. Send an `AcquireModellingResponsibility` interaction with references to the entity and the acquiring federate (Federate 1). 
2. If required, use the HLA service `Attribute Ownership Acquisition` to request ownership of relevant attributes for the referenced entities. 
3. The federate currently owning a requested attribute (Federate 2) receives a `Request Attribute Ownership Release` callback. 
4.  Release the attribute using the `Attribute Ownership Divestiture If Wanted` HLA service. 
5. The HLA callback `Attribute Ownership Acquisition Notification` indicates a successful attribute ownership transfer. 
6. After a successful transfer, update the `FederateApplication` attribute of the transferred entities to reference the new federate application that received the modelling responsibility. 
7. Send an `SMC_Response` interaction indicating the successful completion of the entity action. 
 
## Unsuccessful Transfer 
 
If an ownership release of a required attribute is denied, the transfer is cancelled, and the acquiring federate shall update the `AllocatedFederate` attribute to represent the federate with primary modelling responsibility. 
 
``` mermaid 
sequenceDiagram
autonumber

participant Federation 
participant Federate 1 
participant Federate 2 
 
Federate 1->>Federation:HLA Attribute Ownership Acquisition(entity.attributes) 
Federation->>Federate 2:HLA Request Attribute Ownership Release(entity.attributes) 
Federate 2->>Federation:HLA Attribute Ownership Release Denied(entity.attributes) 
Federation->>Federate 1:HLA Attribute Ownership Unavailable(entity.attributes) 
Federate 1->>Federation:Update(entity.AllocatedFederate) 
Federate 1->>Federation:SMC_Response(False) 
 
 
``` 
 
 
1. Use the HLA service `Attribute Ownership Acquisition` to request ownership of relevant attributes for the referenced entities. 
3. The federate currently owning a requested attribute (Federate 2) receives a `Request Attribute Ownership Release` callback. 
4. Deny the attribute release using the `Attribute Ownership Release Denied` HLA service. 
5. The HLA callback `Attribute Ownership Release Denied` indicates an unsuccessful attribute ownership transfer. 
6. Cancel the transfer and update the `AllocatedFederate` attribute. 
7. Send an `SMC_Response` interaction indicating the unsuccessful completion of the entity action.


## Object Classes

```mermaid
classDiagram 
direction LR

HLAobjectRoot : AllocatedFederate
HLAobjectRoot : UniqueId(NETN-BASE)
```

### HLAobjectRoot



|Attribute|Datatype|Semantics|
|---|---|---|
|AllocatedFederate|FederateName|Optional. Reference to the federate application with the assigned primary responsibility for modelling the object behaviour.|
|UniqueId<br/>(NETN-BASE)|UUID|Required. A unique identifier for the object. The Universally Unique Identifier (UUID) is generated or pre-defined.| 

## Interaction Classes

```mermaid
classDiagram 
direction LR
HLAinteractionRoot <|-- SMC_FederateControl
HLAinteractionRoot : UniqueId(NETN-BASE)
SMC_FederateControl <|-- AcquireModellingResponsibility
SMC_FederateControl : Federate(NETN-SMC)
AcquireModellingResponsibility : Entity
```

### AcquireModellingResponsibility

Trigger the specified federate to initiate a transfer of modelling responsibility for the specified entity.

|Parameter|Datatype|Semantics|
|---|---|---|
|Entity|UUID|Required: Reference to the object which is to be transferred.|

## Datatypes

Note that only datatypes defined in this FOM Module are listed below. Please refer to FOM Modules on which this module depends for other referenced datatypes.

### Overview
|Name|Semantics|
|---|---|
|FederateControlActionEnum|Enumeration of Federate Control Actions. The datatype is expected to be extended in specific modules defining additional actions.|
        
### Enumerated Datatypes
|Name|Representation|Semantics|
|---|---|---|
|FederateControlActionEnum|HLAinteger32BE|Enumeration of Federate Control Actions. The datatype is expected to be extended in specific modules defining additional actions.|
    