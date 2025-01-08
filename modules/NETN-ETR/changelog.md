## Changelog NETN-ETR

### v1.1 - NETN-LBML. Developed by MSG-106 and MSG-134 for NETN FOM v2.0.

The NETN-ETR FOM Module is based on the previously released NETN-LLBML FOM module developed by MSG-068, updated by MSG-106 and prepared for release by MSG-134. 
 
The version of LLBML used in AMSP-04 Ed. A. NATO Education and Training Network Federation Architecture and FOM Design (NETN FAFD) is: 
* NETN-LBML_v1.1.0.xml


### v2.0 - Renamed and updated by MSG-163 for NETN FOM v3.0

* Added a new attribute to ETR_Task: CommunicationNetworkIdentifiers 
* Added new Task: DisruptCommunicaction 
* Added new Task: Observe 
* Added SetTransmitterStatus 
* Added MagicMove 
* Added MagicResource* Added QuerySupportedCapabilities interaction 
* Added CapabilitiesSupported interaction 
* Added EstablishCheckPoint 
* Added OperateCheckPoint 
* Added RemoveCheckPoint 
* Added StopAtSideOfRoad 
* Added CreateObstacle 
* Added CreateMinefield 
* Added ClearObstacle 
* Added AddPassage 
* Added RemovePassage 
* Added Patrol 
* Added PatrolRepeating 
 
* Removed FollowRoute 
 
* Renamed MoveToUnit to MoveToEntity 
* Renamed FollowUnit to FollowEntity 
* Renamed VehicleMount to Mount 
* Renamed VehicleDismount to Dismount 
* Renamed FireIndirectWM to FireAtLocationWM 
* Renamed FireAtUnit to FireAtEntity 
* Renamed FireDirectWM to FireAtEntityWM 
* Renamed ChangeOrderedSpeed to SetOrderedSpeed 
* Renamed ChangeOrderedAltitude to SetOrderedAltitude 
* Renamed Parameter SensorReport.SpottedEnities to SpottedEntities. 
* Renamed Parameter MOUNT.EntiityId to EntityId


### v3.0 - Updated by MSG-191 for NETN FOM v4.0

* Added `BaseEntity` attribute `SupportedTasks` 
* Added `BaseEntity` attribute `TaskProgress` 
* Added `BaseEntity` attribute `CurrentTasks` 
* Added `BaseEntity` attribute `PlannedTasks` 
* Added `BaseEntity` attribute `PreviousTasks` 
 
 
* Added object Class `ETR_DelegatedTask` 
 
* Removed interaction class `ETR_Root` 
* Removed interaction class `ETR_SimCon` 
* Removed interaction class `ETR_TaskManagement` 
* Moved interaction class `ETR_Task` as subclass of `SMC_EntityControl` and renamed to `Task` 
* Moved interaction class `ETR_Report` as subclass of `HLAinteractionRoot` 
 
* Merged `CancelAllTasks` and `CancelSpecifiedTasks` to `RequestCancelTask` 
* Moved and renamed interaction class `TaskStatusReport` as `ETR_Report` subclass `TaskStatusUpdate` 
* Moved all `ETR_Task` subclasses to `Task` subclasses 
* Replaced all task interaction parameters with `TaskParameters` with different datatypes for each task type. 
 
* Removed `QueryCapabilitiesSupported` interaction class 
* Removed `CapabilitiesSupported` interaction class 
 
* Moved and renamed `MagicResource` interaction class to NETN-LOG `RequestTask` subclass `SetResourceStatus` 
* Moved `MagicMove` interaction class as `RequestTask` subclass 
* Changed `MagicMove` parameter `Heading` datatype to `DirectionDegreesFloat32` 
* Changed `MagicMove` parameter `Location` datatype to `LocationStruct` 
* Removed `MagicMove` parameter `LocationUuid` 
 
* Moved `AddPassage` interaction class to NETN-SE `CreateBreach` 
* Moved `ClearObstacle` interaction class to NETN-SE `ClearEngineering` 
* Moved `CreateObstacle` interaction class to NETN-SE `CreateObstacle` 
* Moved `CreateMinefield` interaction class to NETN-SE `LayMinefield` 
* Moved `EstablishCheckPoint` interaction class to NETN-SE `EstablishCheckpoint` 
* Moved `RemoveCheckPoint` interaction class to NETN-SE `ClearEngineering` 
* Moved `RemovePassage` interaction class to NETN-SE `ClearEngineering` 
* Moved `DisruptCommunication` interaction class to NETN-COM `DisruptCommunication` 
* Moved `SetTransmitterStatus` interaction class to NETN-COM `SetTransmitterStatus` 
* Removed `TurnToOrientation` interaction class 
* Merged `PatrolRepeating` and `Patrol` interaction classes to `Patrol` 
* Merged `FireAtEntity` and `FireAtEntityWM` interaction classes to `DirectFire` 
* Merged `FireAtLocation` and `FireAtLocationWM` interaction classes to `IndirectFire` 
* Renamed `Move` interaction class to `MoveInDirection` 
* Added `MoveByRoute` interaction class 
* Added `OperateObservationPost` interaction class 
* Renamed `OperateCheckPoint` interaction class to `OperateCheckpoint` 
* Removed `MoveToEntity` interaction class 
* Renamed `SetOrderedAltitude` interaction class to `ChangeAltitude` 
* Renamed `SetOrderedSpeed` interaction class to `ChangeSpeed` 
* Renamed `TurnToHeading` interaction class to `ChangeHeading` 
 
* Added `RequestTaskStatus` interaction class 
* Added `RequestTaskDelegation` interaction class 
* Added `RequestReport` interaction class 
* Added `Response` interaction class 
 
* Added `ETR_Report` parameter `ReportingEntity` 
* Changed `ETR_Report` parameter `ReportId` datatype to `UUID` 
* Replaced `ETR_Report` parameter `When` with NETN-BASE `HLAinteractionRoot` parameter `Time` 
* Moved `ETR_Report` parameter `CommunicationNetworkIds` to NETN-COM `ETR_Report 
* Replaced `InWeaponRange` parameter `Observer` with `ETR_Report` parameter `ReportingEntity` 
* Replaced `SpotReport` parameter `Observer` with `ETR_Report` parameter `ReportingEntity` 
* Added `SpotReport` parameter `SensorType` 
* Renamed `SensorReport` interaction class to `ETR_SensorEvent` and move as subclass to `HLAinteractionClass` 
* Replaced `StatusReport` parameter `EntityId` with `ETR_Report` parameter `ReportingEntity` 
* Added `EntitySensorUpdate` interaction class 
* Removed `StatusReport` interaction class 
 
* Changed `PositionStatusReport` parameter `Position` datatype to `LocationStruct` 
* Changed `PositionStatusReport` parameter `Heading` datatype to `DirectionDegreesFloat32` 
* Changed `ResourceStatusReport` parameter `Resource` datatype to `SupplyStruct` 
* Changed `UnderAttackStatusReport` parameter `FromDirection` datatype to `DirectionDegreesFloat32` 
 
 
* Changed `TaskStatusReport` parameter `TaskId` datatype to `UUID` 
* Renamed `TaskStatusReport` parameter `TaskId` to `Task` 
* Replaced `TaskStatusReport` parameter `When` with NETN-BASE `HLAinteractionRoot` parameter `Time` 
 
 
* Removed datatype `MineCountEnum32` 
* Removed datatype `Datetime18` 
* Removed datatype `ArrayOfTaskIds` 
* Removed datatype `ArrayOfNames` 
* Removed datatype `MineCountVariantStruct` 
 
* Added datatype `EntityControlActionEnum` 
* Added datatype `CaptureStatusEnum` 
 
* Added datatype `ArrayOfTaskTypes` 
* Added datatype `ArrayOfTaskDefinitions` 
* Added datatype `ArrayOfTaskProgress` 
* Added datatype `ArrayOfWaypoints` 
 
* Added struct datatypes for each task type with task parameters 
* Added struct datatypes for task progress (various) 
 
* Added datatype `RoundStruct` 
* Added datatype `TaskDefinition` 
* Added datatype `TaskProgress` 
* Added datatype `Waypoint` 
 
* Added datatype `TaskDefinitionVariantRecord` 
* Added datatype `TaskProgressVariantRecord` 
 
* Changed datatype `SpottedEntity` field `Orientation` to `Heading` 
 
* Renamed `Mount` interaction class to `Attach` 
* Renamed `Dismount` interaction class to `Detach`

