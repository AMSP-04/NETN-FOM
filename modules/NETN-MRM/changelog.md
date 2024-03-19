## Changelog NETN-MRM

### v1.1 - Initial version of NETN-MRM FOM Module released as part of NETN FOM v2.0.

NETN-MRM FOM Module v1.1.1 was developed by MSG-106 and released 2014-05-15.


### v2.0 - Updated version by MSG-163 to be part of NETN FOM v3.0.

* Changed Filename to NETN-MRM.xml 
* Changed `modelIdentification` `securityClassification` from `unclassified` to `Not Classified` 
* Changed `modelIdentification` `other` to include license information 
* Changed `modelIdentification` `reference` to only refer to directly dependent FOM Modules 
* Added `modelIdentification` `useLimitation` to reflect Scope of FOM Module 
* Added `modelIdentification` `glyph` 
* Updated `modelIdentification` `purpose` to reflect Purpose of FOM Module 
* Updated `modelIdentification` `description` to reflect Introduction of FOM Module 
* Updated `modelIdentification` `name` to NATO Education and Training Network (NETN) Multi-Resolution Modelling (MRM) Module 
* Updated `modelIdentification` `poc` to include Release authority, Primary authors and Contributors 
* Updated `modelIdentification` `applicationDomain` to empty. 
* Removed NETN-MRM dependency on NETN-TMR. 
* Merged NETN-Aggregate to NETN-MRM. 
* Removed InteractionClass `MRM_Object` 
* Removed InteractionClass `MRM_TriggerResponse` 
* Removed InteractionClass `MRM_Trigger` 
* Renamed InteractionClass `MRM_DisaggregationRequest` 
* Renamed InteractionClass `MRM_AggregationRequest` 
* Removed InteractionClass `MRM_DisaggregationResponse` 
* Removed InteractionClass `MRM_AggregationResponse` 
* Removed InteractionClass `MRM_CancelRequest` 
* Removed InteractionClass `MRM_ActionComplete` 
* Added InteractionClass `MRM_Interaction` 
* Added InteractionClass `Request` 
* Added InteractionClass `Aggregate` 
* Added InteractionClass `Disaggregate` 
* Added InteractionClass `Divide` 
* Added InteractionClass `Merge` 
* Added InteractionClass `Inactivate` 
* Added InteractionClass `Activate` 
* Added InteractionClass `QuerySupportedCapabilities` 
* Added InteractionClass `CapabilitiesSupported` 
* Added InteractionClass `Response` 
* Removed datatype `AggregateStateEnum32` 
* Removed datatype `EntityListVariableLengthStruct` 
* Removed datatype `UpdateTypeEnum32` 
* Removed datatype `SupportRelationshipStruct` 
* Removed datatype `FacingDegreesFloat32` 
* Removed datatype `CoverStatusStruct` 
* Removed datatype `CoverEnum8` 
* Removed datatype `CombatValueFloat64` 
* Removed datatype `SupportRelationshipEnum8` 
* Removed datatype `EchelonEnum8` 
* Removed datatype `PercentageUint32` 
* Renamed datatype `NonComplianceReasonEnum` to `MRM_ResponseStatusEnumType` 
* Replaced datatype `PercentageUint32` with `PercentUnsignedInteger32` 
* Replaced datatype `FacingDegreesFloat32` with `DirectionDegreesFloat32` 
* Replaced datatype `TimeSecInt64` with `EpochTimeSecInt64` 
* Moved datatype `QuantityFloat64` to NETN-BASE 
* Changed datatype of `NETN_Aggregate.Mounted` to `PercentFloat64` 
* Changed datatype of `NETN_Aggregate.SourceUnit` to `UuidArrayOfHLAbyte16` 
* Changed datatype of `NETN_Aggregate.Symbol` to `SymbolIdentifier` 
* Changed datatype of `NETN_Aggregate.Footprint` to `GeocentricPolygon ` 
* Added attribute `Route` for  object class `NETN_Aggregate` 
* Added attribute `Destination` for  object class `NETN_Aggregate` 
* Updated semantics of attribute `NETN_Aggregate.UniqueId` 
* Renamed attribute `NETN_Aggregate.UniqueID` to `NETN_Aggregate.UniqueId` 
* Renamed attribute `Symbol` of `NETN_Aggregate` to `SymbolId` 
* Renamed attribute `UnitEquipment`  of `NETN_Aggregate` to `EquipmentStatus` 
* Renamed attribute `UnitPersonnel`  of `NETN_Aggregate` to `PersonnelStatus` 
* Renamed attribute `UnitSupplies`  of `NETN_Aggregate` to `Supplies` 
* Removed attribute `Footprint`of `NETN_Aggregate` object class 
* Removed attribute `SupportUnit` of `NETN_Aggregate` object class 
* Added field `ResourceType` to datatype `ResourceStatusNumberStruct` 
* Changed datatype of attribute `CoverStatus` of `NETN_Aggregate` to `PercentFloat64` 
* Changed datatype of attribute `CombatValue` of `NETN_Aggregate` to `PercentFloat64` 
* Changed datatype of attribute `EntityList` of `NETN_Aggregate` to `ArrayOfEntityStruct` 
* Changed datatype of attribute `Echelon` of `NETN_Aggregate` to `EchelonEnum32` 
* Added field `UnitAllocation` to datatype `EntityStruct`


### v3.0 - Updated version by MSG-191 to be part of NETN FOM v4.0

* Removed `NETN_Aggregate` object class 
* Replaced `NETN_Aggregate` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_Aggregate` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_Aggregate` attribute `SubunitList` with NETN-MRM `AggregateEntity` attribute `DisaggregatedEntities` 
* Replaced `NETN_Aggregate` attribute `ParentUnit` with NETN-MRM `BaseEntity` attribute `ParentAggregate` 
* Replaced `NETN_Aggregate` attribute `DividedUnitList` with NETN-MRM `AggregateEntity` attribute `DividedEntities` 
* Replaced `NETN_Aggregate` attribute `SourceUnit` with NETN-MRM `BaseEntity` attribute `SourceAggregate` 
* Removed `NETN_Aggregate` attribute `EmbeddedUnitList` 
* Replaced `NETN_Aggregate` attribute `HigherHeadquarters` with NETN-ORG `Unit` attribute `HigherHeadquarters` 
* Replaced `NETN_Aggregate` attribute `Mounted` with NETN-ENTITY `BaseEntity` attribute `HostEntitiy` and NETN-Physical `AggregateEntity` attribute `MountProgress` 
* Replaced `NETN_Aggregate` attribute `SymbolId` with NETN-ENTITY `BaseEntity` attribute `Symbol` 
* Replaced `NETN_Aggregate` attribute `Callsign` with NETN-ENTITY `BaseEntity` attribute `Callsign` 
* Replaced `NETN_Aggregate` attribute `Echelon` with NETN-ENTITY `AggregateEntity` attribute `Echelon` 
* Removed `NETN_Aggregate` attribute `EntityList` 
* Replaced `NETN_Aggregate` attribute `SuppliesStatus` with NETN-LOG `AggregateEntity` attribute `SuppliesStatus` 
* Replaced `NETN_Aggregate` attribute `EquipmentStatus` with NETN-LOG `AggregateEntity` attribute `EquipmentStatus` 
* Replaced `NETN_Aggregate` attribute `PersonnelStatus` with NETN-LOG `AggregateEntity` attribute `PersonnelStatus` 
* Replaced `NETN_Aggregate` attribute `VisualSignature` with NETN-ENTITY `BaseEntity` attribute `Signatures` 
* Replaced `NETN_Aggregate` attribute `HUMINTSignature` with NETN-ENTITY `BaseEntity` attribute `Signatures` 
* Replaced `NETN_Aggregate` attribute `ElectronicSignature` with NETN-ENTITY `BaseEntity` attribute `Signatures`  `ElectronicSignature` 
* Replaced `NETN_Aggregate` attribute `CombatValue` with NETN-ENTITY `AggregateEntity` attribute `CombatValue` 
* Replaced `NETN_Aggregate` attribute `CoverStatus` with NETN-ENTITY `BaseEntity` attribute `Protection` 
* Replaced `NETN_Aggregate` attribute `CaptureStatus` with NETN-ETR `BaseEntity` attribute `CaptureStatus` 
* Removed `NETN_Aggregate` attribute `Mission` 
* Replaced `NETN_Aggregate` attribute `Activity` with NETN-ETR `BaseEntity` attribute `Activity` 
* Replaced `NETN_Aggregate` attribute `Route` with NETN-ETR `BaseEntity` attribute `Route` 
* Replaced `NETN_Aggregate` attribute `Destination` with NETN-ETR `BaseEntity` attribute `Destination` 
* Replaced `NETN_Aggregate` attribute `WeaponsControlOrder` with NETN-ENTITY `AggregateEntity` attribute `WeaponsControlOrder` 
* Removed `MRM_Interaction` interaction class 
* Replaced `MRM_Interaction` parameter `EventId` with NETN-BASE `HLAinteractionRoot` attribute `UniqueId` 
* Removed `CapabilitiesSupported` interaction class 
* Replaced `CapabilitiesSupported` parameter `CapabilityNames` with `AggregateEntity` attribute `SupportedAggregationActions` 
* Removed `Request` interaction class 
* Removed `Request` parameter `Federate` 
* Replaced `Request` parameter `AggregateUnit` with NETN-ETR `ETR_SimCon` parameter `SimulatedEntity` 
* Replaced `Response` interaction class with NETN-ETR `Response` interaction class 
* Removed `Activate` interaction class 
* Removed `Deactivate` interaction class 
* Removed `QuerySupportedCapabilities` interaction class 
* Removed `Aggregate` parameter `RemoveSubunits` 
* Renamed `Merge` parameter `Subunits` to `DividedEntities` 
 
 
* Removed datatype `MissionStruct` 
* Removed datatype `EntityStruct` 
* Removed datatype `ArrayOfEntityStruct` 
* Removed datatype `ConcealmentEnum32` 
* Removed datatype `EntityCategoryEnum32` 
* Moved all the rest of datatype to NETN-Physical 
* Added datatype `AggregationActionEnum` 
* Added datatype `AggregationActionArray` 
 
* Replaced all use of Array datatype `NETN_ArrayOfSupplyStruct` with `SupplyStructArray` 
* Replaced all use of `PercentUnsignedInteger32` with `PercentFloat32` 
* Replaced all use of `PercentFloat64` with `PercentFloat32`

