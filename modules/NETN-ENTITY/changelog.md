## Changelog NETN-ENTITY

### v1.2 - First version developed by MSG-134 for NETN FOM v2.0. Object classes and datatypes derived from deprecated NETN FOM v 1.0 module AggDeagg.



### v2.0 - Updated version developed by MSG-163 for NETN FOM v3.0 renamed NETN-Physical

* Added attribute `SourceUnit` to all NETN-Physical platform and lifeform object classes. 
* Added attribute `Route` to all NETN-Physical platform, munition and lifeform object classes. 
* Added attribute `Destination` to all NETN-Physical platform, munition and lifeform object classes. 
* Renamed attribute `UniqueID` to `UniqueId` for compliance with naming convensions. 
* Added attribute `SymbolId` to all NETN-Physical platform, lifeform, cultural feature and munition object classes. 
* Renamed object class `SubmersibleVehicle` to `SubmersibleVessel`. 
 
### Changes for v1.2.0 
NETN-MRM FOM Module v1.2.0 was developed by MSG-106 and MSG-134 and released as part of NETN FOM v2.0 in AMSP-04 Ed A. 
 
* Added object classes and datatypes from FOM modules in NETN FOM v1 
* Added object class `NETN_CulturalFeature` 
* Added  object class `NETN_Munition` 
 
* Added attribute Symbol to all object classes 
* Changed from Reliable to BestEffort on some attributes to get a common transport type


### v3.0 - Updated version developed by MSG-191 for NETN FOM v4.0 renamed NETN-ENTITY

* Renamed module NETN-ENTITY 
 
* Removed `NETN_Aircraft` object class 
* Replaced `NETN_Aircraft` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_Aircraft` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_Aircraft` attribute `SourceUnit` with NETN-MRM `BaseEntity` attribute `SourceAggregate` 
* Removed `NETN_Aircraft` attribute `EmbeddedUnitList` 
* Replaced `NETN_Aircraft` attribute `Callsign` with `BaseEntity` attribute `Callsign` 
* Replaced `NETN_Aircraft` attribute `Activity` with NETN-ETR `BaseEntity` attribute `Activity` 
* Replaced `NETN_Aircraft` attribute `Route` with NETN-ETR `BaseEntity` attribute `Route` 
* Replaced `NETN_Aircraft` attribute `Destination` with NETN-ETR `BaseEntity` attribute `Destination` 
* Replaced `NETN_Aircraft` attribute `SymbolId` with `BaseEntity` attribute `SymbolId` 
 
* Removed `NETN_AmphibiousVehicle` object class 
* Replaced `NETN_AmphibiousVehicle` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_AmphibiousVehicle` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_AmphibiousVehicle` attribute `SourceUnit` with NETN-MRM `BaseEntity` attribute `SourceAggregate` 
* Replaced `NETN_AmphibiousVehicle` attribute `EmbeddedUnitList` 
* Replaced `NETN_AmphibiousVehicle` attribute `Callsign` with `BaseEntity` attribute `Callsign` 
* Replaced `NETN_AmphibiousVehicle` attribute `Activity` with NETN-ETR `BaseEntity` attribute `Activity` 
* Replaced `NETN_AmphibiousVehicle` attribute `Route` with NETN-ETR `BaseEntity` attribute `Route` 
* Replaced `NETN_AmphibiousVehicle` attribute `Destination` with NETN-ETR `BaseEntity` attribute `Destination` 
* Replaced `NETN_AmphibiousVehicle` attribute `SymbolId` with `BaseEntity` attribute `SymbolId` 
 
* Removed `NETN_GroundVehicle` object class 
* Replaced `NETN_GroundVehicle` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_GroundVehicle` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_GroundVehicle` attribute `SourceUnit` with NETN-MRM `BaseEntity` attribute `SourceAggregate` 
* Replaced `NETN_GroundVehicle` attribute `EmbeddedUnitList` 
* Replaced `NETN_GroundVehicle` attribute `Callsign` with `BaseEntity` attribute `Callsign` 
* Replaced `NETN_GroundVehicle` attribute `Activity` with NETN-ETR `BaseEntity` attribute `Activity` 
* Replaced `NETN_GroundVehicle` attribute `Route` with NETN-ETR `BaseEntity` attribute `Route` 
* Replaced `NETN_GroundVehicle` attribute `Destination` with NETN-ETR `BaseEntity` attribute `Destination` 
* Replaced `NETN_GroundVehicle` attribute `SymbolId` with `BaseEntity` attribute `SymbolId` 
 
* Removed `NETN_MultiDomainPlatform` object class 
* Replaced `NETN_MultiDomainPlatform` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_MultiDomainPlatform` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_MultiDomainPlatform` attribute `SourceUnit` with NETN-MRM `BaseEntity` attribute `SourceAggregate` 
* Replaced `NETN_MultiDomainPlatform` attribute `EmbeddedUnitList` 
* Replaced `NETN_MultiDomainPlatform` attribute `Callsign` with `BaseEntity` attribute `Callsign` 
* Replaced `NETN_MultiDomainPlatform` attribute `Activity` with NETN-ETR `BaseEntity` attribute `Activity` 
* Replaced `NETN_MultiDomainPlatform` attribute `Route` with NETN-ETR `BaseEntity` attribute `Route` 
* Replaced `NETN_MultiDomainPlatform` attribute `Destination` with NETN-ETR `BaseEntity` attribute `Destination` 
* Replaced `NETN_MultiDomainPlatform` attribute `SymbolId` with `BaseEntity` attribute `SymbolId` 
 
* Removed `NETN_Spacecraft` object class 
* Replaced `NETN_Spacecraft` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_Spacecraft` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_Spacecraft` attribute `SourceUnit` with NETN-MRM `BaseEntity` attribute `SourceAggregate` 
* Replaced `NETN_Spacecraft` attribute `EmbeddedUnitList` 
* Replaced `NETN_Spacecraft` attribute `Callsign` with `BaseEntity` attribute `Callsign` 
* Replaced `NETN_Spacecraft` attribute `Activity` with NETN-ETR `BaseEntity` attribute `Activity` 
* Replaced `NETN_Spacecraft` attribute `Route` with NETN-ETR `BaseEntity` attribute `Route` 
* Replaced `NETN_Spacecraft` attribute `Destination` with NETN-ETR `BaseEntity` attribute `Destination` 
* Replaced `NETN_Spacecraft` attribute `SymbolId` with `BaseEntity` attribute `SymbolId` 
 
* Removed `NETN_SubmersibleVessel` object class 
* Replaced `NETN_SubmersibleVessel` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_SubmersibleVessel` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_SubmersibleVessel` attribute `SourceUnit` with NETN-MRM `BaseEntity` attribute `SourceAggregate` 
* Replaced `NETN_SubmersibleVessel` attribute `EmbeddedUnitList` 
* Replaced `NETN_SubmersibleVessel` attribute `Callsign` with `BaseEntity` attribute `Callsign` 
* Replaced `NETN_SubmersibleVessel` attribute `Activity` with NETN-ETR `BaseEntity` attribute `Activity` 
* Replaced `NETN_SubmersibleVessel` attribute `Route` with NETN-ETR `BaseEntity` attribute `Route` 
* Replaced `NETN_SubmersibleVessel` attribute `Destination` with NETN-ETR `BaseEntity` attribute `Destination` 
* Replaced `NETN_SubmersibleVessel` attribute `SymbolId` with `BaseEntity` attribute `SymbolId` 
 
* Removed `NETN_SurfaceVessel` object class 
* Replaced `NETN_SurfaceVessel` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_SurfaceVessel` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_SurfaceVessel` attribute `SourceUnit` with NETN-MRM `BaseEntity` attribute `SourceAggregate` 
* Replaced `NETN_SurfaceVessel` attribute `EmbeddedUnitList` 
* Replaced `NETN_SurfaceVessel` attribute `Callsign` with `BaseEntity` attribute `Callsign` 
* Replaced `NETN_SurfaceVessel` attribute `Activity` with NETN-ETR `BaseEntity` attribute `Activity` 
* Replaced `NETN_SurfaceVessel` attribute `Route` with NETN-ETR `BaseEntity` attribute `Route` 
* Replaced `NETN_SurfaceVessel` attribute `Destination` with NETN-ETR `BaseEntity` attribute `Destination` 
* Replaced `NETN_SurfaceVessel` attribute `SymbolId` with `BaseEntity` attribute `SymbolId` 
 
* Removed `NETN_Human` object class 
* Replaced `NETN_Human` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_Human` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_Human` attribute `SourceUnit` with NETN-MRM `BaseEntity` attribute `SourceAggregate` 
* Replaced `NETN_Human` attribute `Callsign` with `BaseEntity` attribute `Callsign` 
* Replaced `NETN_Human` attribute `Activity` with NETN-ETR `BaseEntity` attribute `Activity` 
* Replaced `NETN_Human` attribute `Route` with NETN-ETR `BaseEntity` attribute `Route` 
* Replaced `NETN_Human` attribute `Destination` with NETN-ETR `BaseEntity` attribute `Destination` 
* Replaced `NETN_Human` attribute `SymbolId` with `BaseEntity` attribute `SymbolId` 
 
* Removed `NETN_NonHuman` object class 
* Replaced `NETN_NonHuman` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_NonHuman` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_NonHuman` attribute `SourceUnit` with NETN-MRM `BaseEntity` attribute `SourceAggregate` 
* Replaced `NETN_NonHuman` attribute `Callsign` with `BaseEntity` attribute `Callsign` 
* Replaced `NETN_NonHuman` attribute `Activity` with NETN-ETR `BaseEntity` attribute `Activity` 
* Replaced `NETN_NonHuman` attribute `Route` with NETN-ETR `BaseEntity` attribute `Route` 
* Replaced `NETN_NonHuman` attribute `Destination` with NETN-ETR `BaseEntity` attribute `Destination` 
* Replaced `NETN_NonHuman` attribute `SymbolId` with `BaseEntity` attribute `SymbolId` 
 
* Removed `NETN_CulturalFeature` object class 
* Replaced `NETN_CulturalFeature` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_CulturalFeature` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_CulturalFeature` attribute `EmbeddedUnitList` 
* Replaced `NETN_CulturalFeature` attribute `Callsign` with `BaseEntity` attribute `Callsign` 
* Replaced `NETN_CulturalFeature` attribute `Activity` with NETN-ETR `BaseEntity` attribute `Activity` 
* Replaced `NETN_CulturalFeature` attribute `SymbolId` with `BaseEntity` attribute `SymbolId` 
 
* Removed `NETN_Munition` object class 
* Replaced `NETN_Munition` attribute `UniqueId` with NETN-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `NETN_Munition` attribute `Status` with NETN-MRM `BaseEntity` attribute `Status` 
* Replaced `NETN_Munition` attribute `Route` with NETN-ETR `BaseEntity` attribute `Route` 
* Replaced `NETN_Munition` attribute `Destination` with NETN-ETR `BaseEntity` attribute `Destination` 
* Replaced `NETN_Munition` attribute `SymbolId` with `BaseEntity` attribute `SymbolId` 
 
* Added `AggregateEntity` object class (from NETN_Aggregate in NETN-MRM) 
* Added `BaseEntity` attribute `HostEntitiy` 
* Added `BaseEntity` attribute `Symbol` 
* Added `BaseEntity` attribute `Callsign` 
* Added `AggregateEntity` attribute `Echelon` 
* Added `BaseEntity` attribute `Signatures` 
* Added `AggregateEntity` attribute `CombatValue` 
* Added `BaseEntity` attribute `Protection` 
* Added `AggregateEntity` attribute `WeaponsControlOrder` 
 

* Added datatype `RangeFloat32` 
* Added datatype `WeaponControlOrderEnum8` 
* Added datatype `SensorStateEnum32` 
* Added datatype `ArrayOfSensorStruct` 
* Added datatype `VisualSignatureStruct` 
* Added datatype `HUMINTSignatureStruct` 
* Added datatype `ElectronicSignatureStruct` 
* Added datatype `SensorStateStruct` 
 
* Changed datatype of FixedRecord SensorStruct field SensorID to UUID

