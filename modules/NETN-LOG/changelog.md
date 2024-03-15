## Changelog NETN-LOG

### v1.1 - Initial version developed by MSG-068 for NETN FOM v1.0. 

In NETN FOM v 2.0 this module was replaced with several FOM modules to represent different services. A Base FOM Module was used to represent the basic Service-Consumer Provider (SCP) pattern. 
 
These modules were initially developed by MSG-106 and prepared for release by MSG-134. 
 
Modules in AMSP-04 Ed. A. NATO Education and Training Network Federation Architecture and FOM Design (NETN FAFD) were: 
* NETN-SCP-BASE v1.1.3 
* NETN-Supply v1.1.2 
* NETN-Storage v1.2.2 
* NETN-Repair v 1.2.1 
* NETN-Transport v1.1.2


### v2.0 - Re-merged version of NETN-LOG FOM Module updated by MSG-163 for NETN FOM v3.0. Includes NETN-SCP, NETN-Supply, NETN-Storage, NETN-Repair and NETN-Transport.

* FOM Modules NETN-SCP-BASE v1.1.3, NETN-Supply v1.1.2, NETN-Storage v1.2.2, NETN-Repair v1.2.1 and NETN-Transport v1.1.2 merged into new module NETN-LOG 
* Prefix dropped from all interaction classes except interaction class LOG_Service 
* Added note for `modelIdentification` to provide additional description of FOM module 
* Added glyph 
* Updated `releaseRestriction`, `purpose`, `description` and `useLimitation` 
* Changed `securityClassification` from `Unclassified` to `Not Classified` 
 
* Removed object class `SCP_Facility` 
* Removed interaction class `RequestStorage` 
* Removed interaction class `OfferStorage` 
* Removed interaction class `StorageComplete` 
* Removed interaction class `ReadyToReceiveStorage` 
* Removed interaction class `ReadyToReceiveRepair` 
* Removed interaction class `ReadyToReceiveSupply` 
 
* Removed parameter `LOG_Service.Consumer` 
* Removed parameter `LOG_Service.Provider` 
* Removed parameter `RequestSupply.LoadingDoneByProvider` 
* Removed parameter `OfferSupply.LoadingDoneByProvider` 
* Removed parameter `LOG_Service.ServiceType` 
* Removed parameter `OfferTransport.OfferType` 
* Removed parameter `OfferService.IsOffering` 
* Removed parameter `RequestRepair.Appointment` 
* Removed parameter `RequestSupply.Appointment` 
* Removed parameter `OfferRepair.Appointment` 
* Removed parameter `OfferSupply.Appointment` 
 
* Removed datatype `TransportStruct` 
* Removed datatype `DataTStruct` 
* Removed datatype `DataEDStruct` 
* Removed datatype `TransportTypeEnum32` 
* Removed datatype `ServiceIdentifier` 
* Removed datatype `LOG_ServiceTypeEnum8` 
* Removed datatype `ServiceDescription` 
* Removed datatype `NETN_RepairTypeEnum16` 
 
* Added interaction class `LOG_Interaction.CancelOffer` 
* Renamed interaction class `CancelService` to `CancelRequest` 
* Renamed interaction class `LOG_Service` to `LOG_Interaction` 
 
* Added parameter `RequestService.ConsumerEntity` 
* Added parameter `RequestService.ProviderEntity` 
* Added parameter `OfferService.OfferId` 
* Added parameter `AcceptOffer.OfferId` 
* Added parameter `OfferService.ProviderEntity` 
* Added parameter `OfferService.OfferType` 
* Added parameter `RequestService.StartAppointment` 
* Added parameter `RequestTransport.EndAppointment` 
* Added parameter `OfferService.StartAppointment` 
* Added parameter `OfferTransport.EndAppointment` 
* Added parameter `RequestSupply.TransferDirection` 
 
* Renamed parameter `LOG_Service.TransactionId` to `LOG_Interaction.RequestId` 
* Renamed parameter `OfferService.RequestTimeOut` to `OfferService.OfferTimeOut` 
* Changed parameter datatype for `LOG_Service.ServiceID` to `TransactionId` 
* Changed parameter datatype for `RequestTransport.TransportData` to `ArrayOfUuid`. 
* Changed parameter datatype for `OfferTransport.TransportData` to `ArrayOfUuid`. 
 
* Renamed datatype `NETN_ServiceIdentifier` to `ServiceIdentifier` 
* Renamed datatype field `RepairStruct.MaterialID` to `RepairStruct.MaterielId` 
* Changed datatype for `ArrayOfRepairTypeEnum` from `NETN_RepairTypeEnum16` to `RepairTypeEnum16`


### v3.0 - Updated version developed by MSG-191. Release included in NETN FOM v4.0

* MAJOR UPDATE TO USE NETN-ETR Patterns 
* Add dependency on NETN-ETR 
* Replaced all interaction classes 
* Removed datatype `OfferTypeEnum32` 
* Removed datatype `TransferDirectionEnum32` 
* Removed datatype `RepairStruct` 
* Removed datatype `ArrayOfRepairStruct` 
* Removed datatype `ArrayOfRepairTypeEnumStruct` 
 
* Updated datatype `AppointmentStruct` 
 
* Extended`AggregateEntity` object class 
* Added `AggregateEntity` attribute `Supplies` 
* Added `AggregateEntity` attribute `Equipment` 
* Added `AggregateEntity` attribute `Personnel` 
 
* Extended NETN-ETR `RequestTask` 
* Added `RequestTask` interaction subclass `Resupply` 
* Added `RequestTask` interaction subclass `Repair` 
* Added `RequestTask` interaction subclass `Transport` 
 


* Added `SMC_EntityControl` interaction subclass `SetEquipmentStatus` 
* Added `SMC_EntityControl` interaction subclass `SetPersonnelStatus` 
* Added `SMC_EntityControl` interaction subclass `SetSuppliesStatus` 
 
* Added datatype `RepairTaskStruct` 
* Added datatype `ResupplyTaskStruct` 
* Added datatype `TransportTaskStruct` 
* Added datatype `RepairTypeEnum16` 
* Added enumerators to datatype `EntityControlActionEnum` 
* Added alternatives to NETN-ETR datatype `TaskDefinitionVariantRecord` 
* Added alternatives to NETN-ETR datatype `TaskProgressVariantRecord`

