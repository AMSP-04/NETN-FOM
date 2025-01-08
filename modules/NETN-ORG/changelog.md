## Changelog NETN-ORG

### v1.0 - Initial version developed by MSG-163. Release included in NETN FOM v3.0



### v2.0 - Updated version developed by MSG-191. Release included in NETN FOM v4.0

* Replaced `ORG_Root` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
 
* Added `ORG_Root` attribute `Name` 
 
* Added object class `OrganizationElement` 
 
* Replaced `Unit` attribute `Name` with `ORG_Root` attribute `Name` 
* Replaced `Unit` attribute `Force` with `OrganizationElement` attribute `Organization` 
* Replaced `Unit` attribute `EntityType` with `OrganizationElement` attribute `EntityType` 
* Replaced `Unit` attribute `SymbolId` with `OrganizationElement` attribute `Symbol` 
* Replaced `Unit` attribute `Disposition` with `OrganizationElement` attribute `Location` 
* Replaced `Unit` attribute `CommunicationNetworks` with NETN-COM `Unit` attribute `CommunicationNetworks` 
* Replaced `Unit` attribute `EmbarkedIn` with `OrganizationElement` attribute `HostUnit` 
* Replaced `Unit` attribute `SymbolAmplification` with `OrganizationElement` attribute `Symbol` 
* Renamed `Unit` attribute `SuperiorUnit` to `AggregateUnit` 
 
* Added `Unit` attribute `HigherHeadquarters` 
 
* Renamed object class `EquipmentItem` to `Equipment` 
* Replaced `EquipmentItem` attribute `Name` with `ORG_Root` attribute `Name` 
* Replaced `EquipmentItem` attribute `EntityType` with `OrganizationElement` attribute `EntityType` 
* Removed `EquipmentItem` attribute `NatoStockNumber` 
* Replaced `EquipmentItem` attribute `SymbolId` with `OrganizationElement` attribute `Symbol` 
* Replaced `EquipmentItem` attribute `Disposition` with `OrganizationElement` attribute `Location` 
* Replaced `EquipmentItem` attribute `CommunicationNetworks` with NETN-COM `Equipment` attribute `CommunicationNetworks` 
* Removed `EquipmentItem` attribute `Resolution` 
* Replaced `EquipmentItem` attribute `MountedOn` with `OrganizationElement` attribute `HostUnit` 
* Replaced `EquipmentItem` attribute `SymbolAmplification` with `OrganizationElement` attribute `Symbol` 
 
* Replaced `Installation` attribute `Name` with `ORG_Root` attribute `Name` 
* Renamed `Installation` attribute `Owner` to `UnitInCommand` 
* Replaced `Installation` attribute `EntityType` with `OrganizationElement` attribute `EntityType` 
* Replaced `Installation` attribute `SymbolId` with `OrganizationElement` attribute `Symbol` 
* Replaced `Installation` attribute `Location` with `OrganizationElement` attribute `Location` 
* Replaced `Installation` attribute `SymbolAmplification` with `OrganizationElement` attribute `Symbol` 
 
* Renamed `Force` attribute `Relations` to `Relationships` 
* Replaced `Force` attribute `Name` with `ORG_Root` attribute `Name` 
 
* Renamed object class `Force` to `Organization` 
 
* Added `Organization` attribute `ForceIdentifier` 
* Added `Organization` attribute `CountryCode` 
 
 
* Added `BaseEntity` attribute `Organization` 
* Removed object class `FederateApplication` 
 
* Added datatype `ForceIdentifierEnum` 
 
* Removed datatype `Text1` 
* Removed datatype `Text2` 
* Removed datatype `Text3` 
* Removed datatype `Text5` 
* Removed datatype `Text8` 
* Removed datatype `Text9` 
* Removed datatype `Text15` 
* Removed datatype `Text20` 
* Removed datatype `Text21` 
* Removed datatype `Text24` 
* Removed datatype `Text255` 
* Removed datatype `EquipmentSymbolAmplificationStruct` 
* Removed datatype `UnitSymbolAmplificationStruct` 
* Removed datatype `InstallationSymbolAmplificationStruct` 
* Removed datatype `FormationInt32` 
* Removed datatype `FormationPositionStruct` 
* Removed datatype `HostilityStatusCodeEnum32` 
* Removed datatype `ModelResolutionTypeEnum32` 
* Removed datatype `NatoStockNumberArray13` 
* Removed datatype `ArrayOfCommunicationNetworks` 
* Removed datatype `CommunicationNetworkStruct` 
* Removed datatype `CommunicationServiceTypeEnum32` 
* Removed datatype `DispositionStruct`

