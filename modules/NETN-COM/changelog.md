## Changelog NETN-COM

### 1.0 - Initial version developed by MSG-164 and MSG-163 for NETN FOM v3.0



### 2.0 - Version developed by MSG-191 for NETN FOM v4.0

* Replaced all `WorldLocationStruct` with `LocationStruct` 
* Replaced all use of datatype `PercentFloat64` with `PercentFloat32` 
* Replaced all `ArrayOfWorldLocationStruct` with `LocationStructArray` 
* Moved attribute `UniqueId` of object class `METOC_Root` to object class `HLAobjectRoot` defined in `NETN-BASE` FOM module 
* Renamed field `Bandwith`in Fixed Record `ConnectionReceiverStruct`to `Bandwidth` 
* Added interaction class `DisruptCommunication` 
* Change datatype `CommunicationNetworkArray` element to `UUID` 
* Added `Task` parameter `CommunicationNetworks` 
* Added datatype `EntityControlActionEnum` 
* Added datatype `TaskDefinitionVariantRecord` 
* Renamed Connection attribute CommunicationNetworkName to CommunicationNetwork 
* Changed datatype of Connection attribute CommunicationNetwork to UUID 
* Renamed Connection attribute SenderEntityId to SenderEntity 
* Renamed CommunicationNode attribute EntityId to HostEntity 
* Renamed DisruptionEffect attribute AffectedNetworks to Networks 
* Renamed DisruptionEffect attribute AffectedArea to Area 
* Changed datatype of DisruptionEffect attribute Networks to ArrayOfUuid 
* Changed datatype of DisruptionEffect attribute Area to LocationStructArray 
* Added `Unit` attribute `CommunicationNetworks` 
* Added `Equipment` attribute `CommunicationNetworks`

