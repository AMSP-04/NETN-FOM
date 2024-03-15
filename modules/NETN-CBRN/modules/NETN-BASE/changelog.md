## Changelog NETN-BASE

### v1.0 - Initial version developed by MSG-106 and MSG-134. Release included in NETN FOM v2.0

* v1.0.0 - First version in NETN FOM v2 
* v1.0.1 - Added array data type: ArrayOfWorldLocation3 (moved from NETN_Aggregate FOM module) 
* v1.0.2 - Renamed data type, new name: ArrayOfWorldLocationStruct3. Updated References, Dependency 
 
 
Previous history 
Common datatypes were defined in NETN FOM v1.0 modules NETN_AggDeagg_v1.07_2010, NETN_Service_Consumer_Provider_v1.0.3_2010 and NETN_Logistics_v1.1.2_2010.


### v2.0 - Updated version developed by MSG-163. Release included in NETN FOM v3.0

* Changed `modelIdentification` `securityClassification` from `unclassified` to `Not Classified` 
* Changed `modelIdentification` `other` to include license information 
* Changed `modelIdentification` `useHistory` to only include formally released versions 
* Added datatype `AltitudeMeterFloat64` 
* Added datatype `DegreesPerSecondFloat32` 
* Added datatype `DirectionDegreesFloat32` 
* Added datatype `DraughtMeterFloat32` 
* Modified datatype `TimeSecInt64` to `EpochTimeSecInt64` 
* Added datatype `IMOType` 
* Added datatype `LatLongDegreesFloat64` 
* Added datatype `MassConcentrationFloat32` 
* Added datatype `MassDensityFloat32` 
* Added datatype `MIDType` 
* Added datatype `PercentFloat64` 
* Updated datatype `QuantityFloat32` 
* Added datatype `QuantityFloat64` 
* Added datatype `QuantityInt32` 
* Added datatype `ShipTypeType` 
* Added datatype `TimeSecInt32` 
* Added datatype `CancellationReasonEnum32` 
* Added datatype `EchelonEnum32` 
* Added datatype `EchelonEnum32` 
* Added datatype `SymbolStandardEnum32` 
* Added datatype `GeoLocationTypeEnum32` 
* Added datatype `ArrayOfStringType` 
* Added datatype `ArrayOfText64` 
* Added datatype `FederateName` 
* Removed datatype `ArrayOfWorldLocationStruct2` 
* Removed datatype `ArrayOfWorldLocationStruct3` 
* Added datatype `GeodeticPath` 
* Added datatype `GeodeticPolygon` 
* Added datatype `SymbolIdentifier15` 
* Added datatype `SymbolIdentifier30` 
* Added datatype `Text64` 
* Added datatype `TransactionId` 
* Added datatype `UUID` 
* Added datatype `GeocentricCircle` 
* Added datatype `GeodeticCircle` 
* Added datatype `GeodeticLocation` 
* Added datatype `GeodeticQuadrangle` 
* Added datatype `GeodeticPoint` 
* Added datatype `AreaVariantStruct` 
* Added datatype `PathVariantStruct` 
* Added datatype `PointVariantStruct` 
* Added datatype `SymbolVariantStruct`


### v3.0 - Updated version developed by MSG-191. The release is included in NETN FOM v4.0

* Added `HLAobjectRoot` attribute `UniqueId` 

* Added `HLAobjectRoot` attribute `Time` 
* Added `HLAinteractionRoot` attribute `UniqueId` 
* Added `HLAinteractionRoot` attribute `FederateApplication` 
* Added `HLAinteractionRoot` attribute `Time` 
 
* Removed datatype `AreaVariantStruct` 
* Removed datatype `PathVariantStruct` 
* Removed datatype `PointVariantStruct` 
* Removed datatype `PointTypeEnum32` 
* Removed datatype `PathTypeEnum32` 

* Removed datatype `QuantityFloat32` 
 
* Replaced datatype `NETN_SupplyStruct` with `SupplyStatusStruct` 
* Replaced datatype `ArrayOfWorldLocationStruct` with `LocationStructArray` 
* Replaced datatype `NETN_ArrayOfSupplyStruct` with `ArrayOfSupplyStatus` 

* Removed datatype `TransactionId` 
* Removed datatype `UuidArrayOfHLAbyte16` 
* Removed datatype `ArrayOfText64` 
* Removed datatype `GeodeticPath` 
* Removed datatype `TimeSecInt32` 
* Removed datatype `GeoLocationTypeEnum32` 
* Removed datatype `ArrayOfString` 
* Removed datatype `Text64` 
* Replaced datatype `PercentFloat64` with `PercentFloat32` 
* Replaced datatype `EpochTimeSecInt64`  with `ScenarioTime` 
 
* Added datatype `EquipmentSymbolAmplificationStruct` 
* Added datatype `UnitSymbolAmplificationStruct` 
* Added datatype `InstallationSymbolAmplificationStruct` 
* Added datatype `TimeMillisecondIn64` 
* Added datatype `ScenarioTime` 
* Added datatype `HostilityStatusCodeEnum32` moved from NETN-ORG 
* Added datatype `DamageStatusEnum32` 
* Added datatype `LocationStruct` 
* Added datatype `SymbolAmplificationVariant` 

* Added datatype `SymbolStruct` 
 
* Added datatype `TransmitterOperationalStatusEnum8` 
* Added datatype `ResourceStatusStruct` 
* Added datatype `ArrayOfResourceStatus` 
 
* Changed representation of `QuantityInt32` to `HLAinteger32BE` 
 
* Replaced datatype `LatLongDegreesFloat64` with `LatitudeFloat64` and `LongitudeFloat64`

