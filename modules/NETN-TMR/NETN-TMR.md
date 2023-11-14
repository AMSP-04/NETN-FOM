
# NETN-TMR
|Version| Date| Dependencies|
|---|---|---|
|2.1|2023-03-18|NETN-BASE|

The NETN-TMR FOM module provides a standard interface and protocol for conducting negotiated and coordinated transfer of attribute modelling responsibility between federates. It extends the HLA Ownership Management services by providing the means to  
1. Negotiate the transfer of ownership.  
2. Initiate ownership transfer using a Trigger federate.  A transfer of modelling responsibility is performed during runtime, to dynamically change the responsibility to update specific attributes, to a more suitable federate.  
For example:  
- Transfer from a Live to a Virtual or Constructive simulation 
- Transfer between Virtual and Constructive simulations 
- Transfer between hi- and low-fidelity models 
- Transfer to allow backup, maintenance or load-balancing 
- Transfer of certain attributes to functional models such as movement, and damage assessment.

In a federated distributed simulation, the participating systems (federates) collectively model the synthetic environment. Allocation of modelling responsibilities depends on individual federate capabilities, federation design agreements, and initial scenario conditions. The responsibility of updating an attribute for a specific simulated entity is allocated to at most one federate. However, during execution, the modelling responsibility and ownership may change. 

IEEE 1516 High Level Architecture (HLA) provides essential services for the divestiture and acquisition of attribute ownership. A negotiated and coordinated transfer of modelling responsibilities requires agreements between federates before the transfer of attribute ownership. 

The NATO Education and Training Network Transfer of Modelling Responsibilities (NETN-TMR) FOM Module is a specification of how to perform a negotiated and coordinated transfer of attribute modelling responsibility between federates in a distributed simulation. 

The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and is primarily intended to support interoperability in a federated simulation (federation) based on HLA. A Federation Object Model (FOM) Module specifies how data is represented and exchanged in the federation. The NETN-TMR FOM module is available as an XML file for use in HLA-based federations.

NETN-TMR covers the following cases:  

* A negotiated acquisition where a federate requests to receive the modelling responsibility  
* Negotiated divestiture where a federate requests another federate to take modelling responsibility 
* Acquisition without negotiation where a federate receives the modelling responsibility  
* Cancellation of transfer

## Overview 
 
NETN-TMR uses a combination of HLA interactions and HLA Ownership Management services to negotiate and perform a coordinated transfer of attribute ownership. The pattern includes an optional triggering interaction to initiate a transfer, and interactions for requesting, offering, cancelling and sending results of a completed transfer. 
 
* A federate initiating a TMR is called a **Trigger Federate** 
* The federate requesting a TMR is called the **Request Federate** 
* The federate responding to a request for TMR is called the **Response Federate** 
 
 
### Basic Pattern 
 
``` mermaid 
 
sequenceDiagram 
autonumber
 
Trigger ->> Request:InitiateTransfer 
Request ->> Response:RequestTransfer 
Response->>Request:OfferTransfer 
note left of Response: HLA Ownership Transfer 
Request->>Trigger:TransferResults 
``` 
 
1. An `InitiateTransfer` interaction is sent by a **Trigger Federate** to initiate a TMR request. Parameters include information on the participating federates, which object instances and what attributes to include in the transfer.  The **Trigger Federate** generates a unique `EventId` used in all subsequent TMR interactions related to the event. This step is optional. 
2. A `RequestTransfer` interaction is sent by the requesting federate to the responding federate. If the request is the result of an `InitiateTransfer` interaction, the parameters are copied and used in the `RequestTransfer` interaction, including the `EventId`. If the request is not triggered, the **Request Federate** generates a unique `EventId` used in all subsequent TMR interactions related to the event. Three types of transfer can be requested `Acquire`, `Divest` or `AcquireWithoutNegotiating`. 
3. As a reply to a `RequestTransfer`, a **Response Federate** sends an `OfferTransfer` interaction. This interaction indicates if a transfer can be achieved or not. If the transfer can be achieved HLA ownership services are immediately used to complete the transfer of the negotiated attributes. 
 
* Before divesting instance attributes, the federate updates the attributes (HLA service Update Attribute Values) 
* After the acquisition of instance attributes, the attributes shall be updated (HLA service Update Attribute Values). 
* The EventID is encoded and used as the User Supplied Tag in the HLA Ownership services. 
 
Note: When the transfer type is `Divesting`, the delivery order of the interaction `OfferTransfer` and the HLA ownership callback service `requestAttributeOwnershipRelease` at the receiving federate is not determined. Due to this, receiving a `requestAttributeOwnershipRelease` callback should be treated in the same way as receiving an `OfferTransfer` with a positive offer. The user-supplied tag in the callback contains the `EventId` which identifies a specific transfer process. 
 
4. A `TransferResult` interaction is sent by the **Request Federate** to indicate the successful or unsuccessful completion of the transfer. 
 
A `CancelRequest` interaction can be sent by the **Request Federate** to cancel a request at any point before HLA ownership transfer is completed. 
 
 
### HLA Ownership Management Services 
 
The HLA Ownership Management services used in TMR (callbacks marked with †) are: 
 
* Attribute Ownership Acquisition (when negotiation) 
* Attribute Ownership Acquisition If Available (without negotiation) 
* Attribute Ownership Divesture If Wanted 
* Cancel Attribute Ownership Acquisition 
* Request Attribute Ownership Release † 
* Attribute Ownership Acquisition Notification † 
* Confirm Attribute Ownership Acquisition Cancellation † 
* Attribute OwnershipUnavailable †

## Use Cases 
 
### Negotiated Acquisition 
 
The requesting federate initiates the transfer to acquire instance attributes. The transfer completes successfully. 
 
``` mermaid 
 
sequenceDiagram 
autonumber
 
Request ->> Response:RequestTransfer(TransferType=Acquire) 
Response->>Request:OfferTransfer 
 
Request->> RTI:attributeOwnershipAcquisition 
RTI->>Response:requestAttributeOwnershipRelease 
Response->>RTI:updateAttributeValues 
RTI->>Request:reflectAttributeValues 
Response->>RTI:attributeOwnershipDivestitureIfWanted 
RTI->>Request:attributeOwnershipAcquisitionNotification 
 
``` 
 
1. The **Request Federate** sends a `RequestTransfer` interaction to the **Response Federate**. Set the `TransferType` parameter to `Acquire` to indicate that attribute ownership is requested to change from the **Response Federate** to the **Request Federate**. Included in the request are references to all instances and associated attributes involved in the transfer. 
2. The **Response Federate** replies to the request by sending an `OfferTransfer` interaction. If the `IsOffering` parameter is True, the **Response Federate** is offering to release ownership of the attributes. 
3. The **Request Federate** starts the attribute ownership transfer using HLA Ownership Services by calling the RTI service `attributeOwnershipAcquisition`. 
4. The **Response Federate** receives a `requestAttributeOwnershipRelease` callback from the RTI. 
5. Before releasing attribute ownership, the **Response Federate** sends a final `updateAttributeValues` for all attributes involved in the transfer. 
6. The attribute update is reflected in the **Request Federate** by the RTI using the `reflectAttributeValues` callback. 
7. The **Response Federate** divests its ownership of the attributes by calling the RTI service `attributeOwnershipDivestitureIfWanted`. 
8. The RTI informs the **Request Federate** and the **Response federate** of the changed ownership using the `attributeOwnershipAcquisitionNotiication` callback. 
 
 
### Negotiated Divestiture 
The requesting federate initiates the transfer for divesting instance attributes. 
 
``` mermaid 
 
sequenceDiagram 
autonumber
 
Request ->> Response:RequestTransfer(TransferType=Divest) 
Response->>Request:OfferTransfer 
 
Response->> RTI:attributeOwnershipAcquisition 
RTI->>Request:requestAttributeOwnershipRelease 
Request->>RTI:updateAttributeValues 
RTI->>Response:reflectAttributeValues 
Request->>RTI:attributeOwnershipDivestitureIfWanted 
RTI->>Response:attributeOwnershipAcquisitionNotification 
 
``` 
 
1. The **Request Federate** sends a `RequestTransfer` interaction to the **Response Federate**. Set the `TransferType` parameter to `Divest` to indicate that attribute ownership transfers from the **Request Federate** to the **Response Federate**. Included in the request are references to all instances and associated attributes involved in the transfer. 
2. The **Response Federate** replies to the request by sending an `OfferTransfer` interaction. If the `IsOffering` parameter is True, the **Response Federate** is offering to acquire ownership of the attributes. 
3. The **Response Federate** starts the attribute ownership transfer using HLA Ownership Services by calling the RTI service `attributeOwnershipAcquisition`. 
4. The **Request Federate** receives a `requestAttributeOwnershipRelease` callback from the RTI. 
5. Before releasing attribute ownership, the **Request Federate** sends a final `updateAttributeValues` for all attributes involved in the transfer. 
6. The attribute update is reflected in the **Response Federate** by the RTI using the `reflectAttributeValues` callback. 
7. The **Request Federate** divest its ownership of the attributes by calling the RTI service `attributeOwnershipDivestitureIfWanted`. 
8. The RTI informs the **Response Federate** (and the Request federate) of the changed ownership using the `attributeOwnershipAcquisitionNotiication` callback. 
 
In the above example, the HLA callback `requestAttributeOwnershipRelease`, with a `TransferId` as UserSuppliedTag, may be delivered to the **Request Federate** before the `OfferTransfer` is received. In such circumstances, the `requestAttributeOwnershipRelease` is considered a positive offer and the **Request Federate** shall ignore any `OfferTransfer` received later for the same `EventId`. 
 
 
### Acquisition without Negotiation 
 
``` mermaid 
 
sequenceDiagram 
autonumber
 
Trigger ->> Request:InitiateTransfer(TransferType=AcquireWithoutNegotiation) 
Request->>RTI:attributeOwnershipAcquisitionIfAvailable 
RTI->>Request:attributeOwnershipAcquisitionNotification 
Request->>Trigger:TransferResults 
``` 
 
 
1. An `InitiateTransfer` with `TransferType` set to `AcquireWithoutNegotiation` is sent from a **Trigger Federate** to the **Request Federate**. 
2. The **Request Federate** uses the HLA Ownership Management Service `attributeOwnershipAcquisitionIfAvailable` to request ownership of attributes without negotiation of its release. 
3. The HLA Ownership Management Service `attributeOwnershipAcquisitionNotification` informs the **Request Federate** of ownership transfer completion. 
4. The **Request Federate** informs the **Trigger Federate** of the result of the transfer by sending a `TransferResults` interaction. 
 
 
### Cancellation of Transfer

#### A. Cancel Acquisition Request 
 
``` mermaid 
 
sequenceDiagram 
autonumber
 
Request ->> Response:RequestTransfer(TransferType=Acquire) 
Response->>Request:OfferTransfer 
Request ->> Response:CancelRequest 
``` 
 
1. The **Request Federate** initiates an acquisition transfer with a `RequestTransfer` interaction. 
2. The **Response Federate** provides a positive offer by sending an `OfferTransfer` interaction. 
3. The **Request Federate** sends a `CancelRequest` interaction to cancel the request either after or before receiving the positive offer. The **Request Federate** does not send an `attributeOwnershipAcquisition`. 
 
#### B. Cancel Divestiture Request 
 
``` mermaid 
 
sequenceDiagram 
autonumber
 
Request ->> Response:RequestTransfer(TransferType=Divest) 
Response->>Request:OfferTransfer 
Response->>RTI:attributeOwnershipAcquisition 
RTI->>Request: requestAttributeOwnershipRelease 
Request ->> Response:CancelRequest 
Response->>RTI:cancelAttributeOwnershipAcquisition 
RTI->>Response:confirmAttributeOwnershipCancellation 
 
``` 
 
1. The **Request Federate** initiates a divestiture transfer with a `RequestTransfer` interaction. 
5. The **Response Federate** provides a positive offer by sending an `OfferTransfer` interaction. 
6. The **Response Federate** immediately sends an `attributeOwnershipAcquisition`. 
7. The **Request Federate** will receive the `OfferTransfer` interaction and `requestAttributeOwnershipRelease` callback in an undetermined order. 
8. The **Request Federate** sends a `CancelRequest` interaction to cancel the request. The cancel is sent any time after making the request but before responding to the `requestAttributeOwnershipRelease` callback. 
9. The **Response Federate** calls `cancelAttributeOwnershipAcquisition` to abort the ongoing HLA attribute ownership transfer. 
10. On HLA attribute ownership transfer cancellation, the **Response Federate** receives a `confirmAttributeOwnershipCancellation` callback.


## Interaction Classes

Note that inherited and dependency parameters are not included in the description of interaction classes.

```mermaid
graph RL
TMR_Interaction-->HLAinteractionRoot
InitiateTransfer-->TMR_Interaction
RequestTransfer-->TMR_Interaction
OfferTransfer-->TMR_Interaction
CancelRequest-->TMR_Interaction
TransferResult-->TMR_Interaction
```

### TMR_Interaction

The `TMR_Interaction` interaction class is the base for all Transfer of Modelling Responsibility interactions. It provides a single parameter used in all TMR interactions to uniquely identify TMR transactions between participating federates.

|Parameter|Datatype|Semantics|
|---|---|---|
|EventId|UUID|Required. The `EventId` is a unique reference to a specific execution of a TMR pattern. It consists of two values, a Counter and a Federate Handle. The value of this parameter is also encoded and used as the User Supplied Tag in the HLA Ownership services to allow a correlation between the TMR interactions and HLA Ownership services. The `EventId` is generated by a trigger federate or, if no trigger federate is used, directly by the requesting federate. The value of this parameter should match all related TMR pattern interactions belonging to the same Transfer of Modelling Responsibilities event.|

### InitiateTransfer

An `InitiateTransfer` interaction is sent by a **Trigger Federate** to initiate a TMR request. Parameters include information on the participating federates, which object instances and what attributes are included in the transfer.  The **Trigger Federate** shall generate a unique `EventId` to be used in all subsequent TMR interactions related to the event.

|Parameter|Datatype|Semantics|
|---|---|---|
|RequestFederate|FederateName|Required. A name specifying the federate requesting the transfer.|
|ResponseFederate|FederateName|Required unless TransferType is AquireWithoutNegotiation: A Federate Name specifying the federate that is the responding federate.|
|Instances|ArrayOfUuid|Required. References (UUID) to NETN Platform, Lifeform or Aggregate instances included in the transfer.|
|Attributes|AttributeNamesType|Required. The common set of attributes for all referenced instances to be included in the transfer. Reference to attributes is by attribute name.|
|TransferType|TransferEnumType|Required. An enumerated value that indicates the direction of the transfer of the ownership and whether there shall be any negotiation: `Acquire` = Requesting Federate acquires instance attribute ownership from the Responding Federate (current owner), `Divest` = Requesting Federate (current owner) releases instance attribute ownership to Responding Federate and `AcquireWithoutNegotiating` = Requesting Federate acquires unowned instance attributes.|

### RequestTransfer

A `RequestTransfer` interaction is sent by the requesting federate to the responding federate. If the request is the result of an `InitiateTransfer` interaction, the parameters from that interaction shall be copied and used in the request including `EventId`. If the request is not triggered the **Request Federate** shall generate a unique `EventId` to be used in all subsequent TMR interactions related to the event.

|Parameter|Datatype|Semantics|
|---|---|---|
|ResponseFederate|FederateName|Required unless TransferType is AquireWithoutNegotiation: A Federate Name specifying the federate that is the responding federate.|
|Instances|ArrayOfUuid|Required. References (UUID) to NETN Platform, Lifeform or Aggregate instances  included in the transfer.|
|Attributes|AttributeNamesType|Required. The common set of attributes for all referenced instances to be included in the transfer. Reference to attributes is by attribute name.|
|TransferType|TransferEnumType|Required. An enumerated value that indicates the direction of the transfer of the ownership and whether there shall be any negotiation: `Acquire` = Requesting Federate acquires instance attribute ownership from the Responding Federate (current owner), `Divest` = Requesting Federate (current owner) releases instance attribute ownership to Responding Federate and `AcquireWithoutNegotiating` = Requesting Federate acquires unowned instance attributes.|

### OfferTransfer

An `OfferTransfer` interaction is sent by a **Response Federate** as a reply to a `RequestTransfer` to indicate if a transfer can be accomplished or not. 
 
**Special Case**: 
When the transfer type is Divesting, the delivery order of the interaction `OfferTransfer` and the HLA ownership callback service `requestAttributeOwnershipRelease` at the receiving federate is not determined. Due to this, receiving a `requestAttributeOwnershipRelease` callback should be treated in the same way as receiving an `OfferTransfer` with a positive offer. The user-supplied tag in the callback contains the `EventId` which identifies a specific transfer process.

|Parameter|Datatype|Semantics|
|---|---|---|
|IsOffering|HLAboolean|Required. True if and only if for all instances all attributes in the request are offered. False if for any instance any attribute in the request is not offered.|
|Reason|NoOfferReasonEnumType|Optional. An enumerated value that shall specify the reason for a negative offer.|

### CancelRequest

A `CancelRequest` interaction can be sent by the **Request Federate** to cancel a request.

|Parameter|Datatype|Semantics|
|---|---|---|
|Reason|CancellationReasonEnum32|Optional. An enumerated value that describes the reason for the cancellation: `Other` = When a Requesting Federate for some reason except time out decides not to complete a transfer. `TimeOut` = When a model's time limit for receiving a TMR offer has passed.|

### TransferResult

A `TransferResult` interaction is sent by the **Request Federate** to indicate the successful or unsuccessful completion of the transfer.

|Parameter|Datatype|Semantics|
|---|---|---|
|IsCompleted|HLAboolean|Required. A Boolean value indicating the result of the transfer. TRUE = Transfer Completed Successfully.|

## Datatypes

Note that only datatypes defined in this FOM Module are listed below. Please refer to FOM Modules on which this module depends for other referenced datatypes.

### Overview
|Name|Semantics|
|---|---|
|AttributeNamesType|Array of attribute names.|
|NoOfferReasonEnumType|Describes the reason why not accepting a TMR request|
|TransferEnumType|Transfer type|
        
### Enumerated Datatypes
|Name|Representation|Semantics|
|---|---|---|
|NoOfferReasonEnumType|HLAinteger32BE|Describes the reason why not accepting a TMR request|
|TransferEnumType|HLAinteger32BE|Transfer type|
        
### Array Datatypes
|Name|Element Datatype|Semantics|
|---|---|---|
|AttributeNamesType|HLAunicodeString|Array of attribute names.|
    