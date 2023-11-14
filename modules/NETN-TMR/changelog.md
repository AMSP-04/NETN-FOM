## Changelog NETN-TMR

### v1.1 - Released version part of NETN-FOM v2.0 in AMSP-04 Ed A.

v1.0.1 XML Schema Reference Changed 
v1.0.2 - Spelling correction at enumerations 
v1.0.3 - Adding AttributeValues 
v1.0.3r3 - Adding reason 
v1.0.3r4 - Added parameter Respondent at interaction TMR_OfferTransferModellingResponsibility and enumeration value NoofferReasonEnum32.OwnershipStateNotApplicableWithRequest 
v1.0.3r5 - Added enumeration value NoofferReasonEnum32.EntityNotKnown 
V1.0.3r6 - Change definition of data type TransactionId, a counter and the federate handle 
v1.1.0r1 - Added interactions TMR_CancelRequest and TMR_Status 
v1.1.0 - Removed "r1" from module name 
v1.1.1 - Update of Dependency table 
v1.1.2 - Rename of enumeration values (AttributeSetTooRestricted, AttributeSetTooExtensive). 
v1.1.3 - Rename of enumeration value (FederateTooBusy).


### v2.0 - Released version part of NETN-FOM v3.0 in AMSP-04 Ed B.

* Added `modelIdentification` `useLimitation` to reflect Scope of FOM Module 
* Added `modelIdentification` `glyph` 
* Added parameter `ResponseFederate` to interaction class `TMR_RequestTransferModellingResponsibility` 
 
* Moved parameter `RequestFederate` from interaction class `TMR` to `TMR_InitiateTransferModellingResponsibility` 
* Moved parameter `ResponseFederate` from interaction class `TMR` to `TMR_InitiateTransferModellingResponsibility` 
* Moved datatype `FederateName` to NETN-BASE. 
* Moved datatype `CancellationReasonEnum32` to NETN-BASE. 
* Moved datatype `TransactionId` to NETN-Base 
 
* Updated `modelIdentification` `securityClassification` from `unclassified` to `Not Classified` 
* Updated `modelIdentification` `other` to include license information 
* Updated `modelIdentification` `reference` to only refer to directly dependent FOM Modules 
* Updated `modelIdentification` `purpose` to reflect Purpose of FOM Module 
* Updated `modelIdentification` `description` to reflect Introduction of FOM Module 
* Updated InteractionClass `TMR` to `TMR_Interaction` and renamed parameter `TransactionID` to `EventId` 
* Updated InteractionClass `TMR_OfferTransferModellingResponsibility` to `OfferTransfer` 
* Updated InteractionClass `TMR_RequestTransferModellingResponsibility` to `RequestTransfer` 
* Updated InteractionClass `TMR_CancelRequest` to `CancelRequest` 
* Updated InteractionClass `TMR_TransferResult` to `TransferResult` and parameter `TransferOk` to `IsCompleted` 
* Updated InteractionClass `TMR_InitiateTransferModellingResponsibility` to `InitiateTransfer` 
* Updated EnumerateDatatype name `TransferTypeEnum32` to `TransferEnumType` 
* Updated EnumerateDatatype name `NoOfferReasonEnum32` to `NoOfferReasonEnumType` 
* Updated EnumeratedDatatype name `NoofferReasonEnum32` to `NoOfferReasonEnum32` and enumeration `OwnershipStateNotApplicableWithRequest` to `OwnershipStateNotCompatibleWithRequest` 
* Updated ArrayDatatype name `ArrayOfAttributes` to `AttributeNamesType` 
* Updated Paramter `isOffering` of InteractionClass `TMR_OfferTransferOfModellingResponsibility` to `IsOffering` 
 
* Removed Parameter `CapabilityType` from InteractionClass `TMR_RequestTransferModellingResponsibility` 
* Removed Parameter `CapabilityType` from InteractionClass `TMR_InitiateTransferModellingResponsibility` 
* Removed Parameter `Respondent` from InteractionClass `TMR_OfferTransferModellingResponsibility` 
* Removed Parameter `Initiating` of interaction class `TMR_InitiateTransferModellingResponsibility` 
* Removed Parameter `InstanceAttributeValues` from InteractionClass `TMR_RequestTransferModellingResponsibility` 
* Removed Parameter `InstanceAttributeValues` from InteractionClass `TMR_InitiateTransferModellingResponsibility` 
* Removed EnumeratedDatatype `CapabilityTypeEnum32` 
* Removed ArrayDatatype `ArrayOfInstanceAttributeValues` 
* Removed ArrayDatatype `ArrayOfAttributeValues` 
* Removed ArrayDatatype `ArrayOfBytes` 
* Removed FixedRecordDatatype `InstanceAttributeValuesStruct` 
* Removed FixedRecordDatatype `AttributeValueStruct`


### v2.1 - Released version part of NATO-FOM v4.0 in AMSP-04 Ed C.

* Changed datatype `TransactionId` to `UUID`

