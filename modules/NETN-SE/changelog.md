## Changelog NETN-SE

### v1.0 - Developed by MSG-163 for NETN FOM v3.0



### v2.0 - Developed by MSG-191 for NETN FOM v4.0

* Replaced object class `SE_GeoObject` with `EnvironmentObject` 
* Replaced object class `Location` with `PointObject` 
* Replaced object class `Path` with `LinearObject` 
* Replaced object class `Region` with `ArealObject` 
* Moved `SE_Facility` attributes `Name`, `SymbolId`, `DamageState`, `Comment` and `Status` moved to `EnvironmentObject` 
* Removed object class `SE_Facility` 
* Replaced object class `CheckPoint` with `Checkpoint` as subclass to `PointObject` 
* Added `PointObject` attribute `Radius` 
* Added `LinearObject` attribute `Points` 
* Added `EnvironmentObject` attribute `HostObject` 
* Added object class `ArealBreach` 
 
 
* Added interaction class `CreateBreach` 
* Added interaction class `EstablishCheckpoint` 
* Added interaction class `LayMinefield` 
* Added interaction class `CreateObstacle` 
* Added interaction class `ClearEngineering` 
 
* Removed datatype `GeoLocationReferenceVariant` 
* Added datatype `EntityControlActionEnum` 
* Added datatype `EngineeringTaskStruct` 
* Added datatype `LayMinefieldTaskStruct` 
* Added datatype `ClearEngineeringTaskStruct` 
* Added datatype `CreateBreachTaskStruct` 
* Added datatype `EstablishCheckpointTaskStruct` 
* Added datatype `CreateObstacleTaskStruct` 
* Added datatype `TaskDefinitionVariantStruct` 
* Added datatype `TaskProgressVariantStruct`

