
# NETN-ETR
|Version| Date| Dependencies|
|---|---|---|
|3.0 |2023-04-07|NETN-Physical|

The NETN-ETR FOM module provides a standard interface for sending tasks to simulated entities represented in a federated distributed simulation. NETN-ETR contains low-level tasks that can easily be interpreted and executed by simulators that model the behaviour of entities. It also defines a set of reports to provide status information, including the status of task execution.

The NATO Education and Training Network (NETN) Entity Tasking and Reports (ETR) Module specifies how to represent simulation task requests provided to participants in a federated distributed simulation and simulator reports sent during the execution of tasks. 
        
The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and supports interoperability in a federated simulation (federation) based on HLA.
        

The NETN-ETR module focuses on tasking simulated entities: 
    
* It enables the transformation of command and control messages into tasks that a simulator can execute. 
* It defines a comprehensive set of tasks and reports that simulators can easily interpret and execute.
* It reflects the capabilities commonly found in COTS Computer Generated Forces (CGF) applications but is independent of a specific CGF, agent framework, or agent modelling paradigm. 
* It is independent of any specific doctrine or tactics. 

A tasked entity can be either a physical entity (e.g. platform or lifeform) or an aggregate entity. The task definition itself does not specify how a simulation models the execution of the task.

## Overview 
The NETN-ETR module defines extensions of the RPR-FOM object classes `BaseEntity`, `AggregateEntity`, `Lifeform`, and `Platform` to represent the planned, current and previous tasks assigned to simulated entities. 
 
Tasking, reporting and simulation control use the following base interaction classes: 
 
* `ETR_Task` is a base class for tasking 
* `ETR_Report` is a base class for reports 
* `ETR_SimCon`  is a base class for simulation control 
 
### Tasks 
 
In a standard pattern for tasking a simulation entity, a tasking federate sends a `RequestTask` subclass interaction with the appropriate task parameters, which includes a reference to the simulation entity intended to execute the task. The application responsible for modelling the entity responds with a `TaskStatusUpdate` notification to indicate task status and performs the task when appropriate. 
 
The `TaskStatusUpdate` interaction provides the following notifications regarding the task: 
 
* Accepted: the task is received and scheduled for execution 
* Refused: the task is not accepted for execution 
* Waiting: the task is waiting for execution 
* Executing: the task is running 
* Completed: the task has been executed successfully 
* Cancelled: the task execution has been explicitly terminated 
* Error: the task execution has been terminated due to a modelling error 
 
```mermaid 

sequenceDiagram 

autonumber
Tasking Federate->>Entity Simulation:RequestTask(TaskParameters) 
Note left of Entity Simulation: Task Received 
Entity Simulation->>Tasking Federate:TaskStatusUpdate(Accepted) 
Note left of Entity Simulation: Task Waiting 
Entity Simulation->>Tasking Federate:TaskStatusUpdate(Waiting) 
Entity Simulation->>Tasking Federate:TaskStatusUpdate(Executing) 
Note left of Entity Simulation: Task Executing 
Entity Simulation->>Tasking Federate:TaskStatusUpdate(Completed) 
Note left of Entity Simulation: Task Completed 
```` 
1. A tasking federate sends one of the `RequestTask` subclass interactions 
2. The federate responsible for simulating the entity responds with a `TaskStatusUpdate` indicating that the task is accepted. If the task is not supported, send a `TaskStatusUpdate` indicating `Refused`. 
3. If there is a delay until the execution, the entity simulation sends a `TaskStatusUpdate` indicating that the task is waiting. 
4. A `TaskStatusUpdate` indicates that the task started executing. 
5. A `TaskStatusUpdate` indicates successful completion of task execution. 
 
A task can execute concurrently with other tasks or sequentially. The `RequestTask` task parameters indicate the expected mode of task execution. The receiving federate application determines if it can fulfil the concurrent or non-concurrent task mode request and accept the task. Tasks are scheduled based on their start time and task execution mode. 
 
The execution of a task can start if: 
 
* For a non-concurrent task 
* No other non-concurrent task is executing 
* The task has the earliest `StartTime` parameter of all planned non-concurrent tasks 
* The task parameter `StartTime` is less than or equal to the current `ScenarioTime`. 
* For a concurrent task 
* The task parameter `StartTime` is less than or equal to the current `ScenarioTime`. 
 
Scheduled tasks are published using the `PlannedTasks` attribute of the simulated entity. 
 
Currently executing tasks and their execution progress are published using the simulated entity's `CurrentTasks` and `TaskProgress` attributes. 
 
Completed tasks are published using the `PreviousTasks` attribute of the simulated entity. 
 
Use the `SupportedTasks` attribute available for all simulated `Platform`, `Lifeform` and `AggregatedEntity` entities to indicate which tasks are supported. Normally, a tasking federate check supported tasks before sending a `TaskRequest` to avoid unnecessary `TaskStatusUpdate` with refusal to accept the task. 
 
 
#### Task Delegation 
 
A federate application may need to delegate the execution of some tasks to some other federate. Use `RequestTaskDelegation` to request a `FederateApplication` to execute a task based on a `TaskDefinition`. The progress of the task execution is published using a corresponding `DelegatedTask` object. Once execution is complete, remove the `DelegatedTask` object instance from the federation.


## Object Classes

Note that inherited and dependency attributes are not included in the description of object classes.

```mermaid
graph RL
BaseEntity-->HLAobjectRoot
DelegatedTask-->HLAobjectRoot
```

### BaseEntity

A base class of aggregate and discrete scenario domain participants. The BaseEntity class is characterized by being located at a particular location in space and independently movable, if capable of movement at all. It specifically excludes elements normally considered to be a component of another element. The BaseEntity class is intended to be a container for common attributes for entities of this type. Since it lacks sufficient class specific attributes that are required for simulation purposes, federates cannot publish objects of this class. Certain simulation management federates, e.g. viewers, may subscribe to this class. Simulation federates will normally subscribe to one of the subclasses, to gain the extra information required to properly simulate the entity.

|Attribute|Datatype|Semantics|
|---|---|---|
|SupportedTasks|ArrayOfTaskTypes|Optional: Tasks supported by this entity.|
|TaskProgress|ArrayOfTaskProgress|Optional. An array of progress for current tasks.|
|CurrentTasks|ArrayOfTaskDefinitions|Optional. An array of currently executing tasks.|
|PlannedTasks|ArrayOfTaskDefinitions|Optional. An array of all planned tasks.|
|PreviousTasks|ArrayOfTaskDefinitions|Optional. An array of completed or cancelled tasks.|
|Activity|AggregateMissionEnum16|Optional: Current activity performed by the entity.|
|Destination|LocationStruct|Optional. The current destination of movement.|
|Route|LocationStructArray|Optional. The current path of movement.|

### DelegatedTask

Object to represent a task and its execution progress when delegated to a federate application other than the one responsible for the tasked entity.

|Attribute|Datatype|Semantics|
|---|---|---|
|TaskDefinition|TaskDefinition|Required. Definition description of the task represented.|
|TaskProgress|TaskProgress|Required. Progress description of the task represented.|

## Interaction Classes

Note that inherited and dependency parameters are not included in the description of interaction classes.

```mermaid
graph RL
ETR_SimCon-->HLAinteractionRoot
ETR_Task-->HLAinteractionRoot
ETR_Report-->HLAinteractionRoot
MagicMove-->ETR_SimCon
UpdateResource-->ETR_SimCon
RequestCurrentSensorDetections-->ETR_SimCon
SetRulesOfEngagement-->ETR_SimCon
RequestTask-->ETR_Task
RequestCancelTask-->ETR_Task
RequestTaskStatus-->ETR_Task
RequestTaskDelegation-->ETR_Task
TaskStatusUpdate-->ETR_Task
Wait-->RequestTask
DirectFire-->RequestTask
IndirectFire-->RequestTask
OperateCheckpoint-->RequestTask
Observe-->RequestTask
MoveToLocation-->RequestTask
MoveIntoFormation-->RequestTask
MoveInDirection-->RequestTask
FollowEntity-->RequestTask
Mount-->RequestTask
Dismount-->RequestTask
MoveByRoute-->RequestTask
ChangeSpeed-->RequestTask
ChangeAltitude-->RequestTask
ChangeHeading-->RequestTask
Patrol-->RequestTask
StopAtSideOfRoad-->RequestTask
OperateObservationPost-->RequestTask
SpotReport-->ETR_Report
PositionStatusReport-->ETR_Report
DamageStatusReport-->ETR_Report
ResourceStatusReport-->ETR_Report
UnderAttackStatusReport-->ETR_Report
InWeaponRangeReport-->ETR_Report
```

### ETR_SimCon

Simulation control interactions instruct a simulation model to change a specific state directly. Although the simulation control interactions are not tasks performed by the simulation model, they are a direct change of model state if accepted by a federate application.

|Parameter|Datatype|Semantics|
|---|---|---|
|SimulatedEntity|UUID|Required. Reference to the entity that is the subject of simulation control.|

### MagicMove

Instructs the simulation entity to immediately change location to the specified position and heading.

|Parameter|Datatype|Semantics|
|---|---|---|
|Location|LocationStruct|Required. Location of the entity.|
|Heading|DirectionDegreesFloat32|Optional. Heading of the entity. Default = 0. True North.|

### UpdateResource

Instructs the simulation entity to set the amount of available resources immediately.

|Parameter|Datatype|Semantics|
|---|---|---|
|Resource|SupplyStruct|Required. Defines the resource type that will get a new quantity value.|

### RequestCurrentSensorDetections

Requests the resending of all current `SensorReports`.


### SetRulesOfEngagement

Instructs the simulation entity to change its rules of engagement immediately.

|Parameter|Datatype|Semantics|
|---|---|---|
|RulesOfEngagement|RulesOfEngagementEnum8|Required. The rules of engagement for an entity.|

### ETR_Task

Base interaction class related to the tasking of simulated entities and task management.

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskedEntity|UUID|Required. Reference to the entity that should execute the task.|

### RequestTask

Requests a simulated entity to perform some task based on a task description. If accepted, the federate application modelling the behaviour will execute the task per task parameters and scheduling. A request task is acknowledged using a `TaskStatusUpdate` response interaction. Resending a `RequestTask` with the same `TaskId` as a previously sent interaction is equivalent to cancelling and sending a new task.

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskId|UUID|Required. Unique identifier for the task.|
|StartTime|ScenarioTime|Optional. The default value is the current `ScenarioTime`.|
|Activity|AggregateMissionEnum16|Optional. Specifies the activity for the entity that will execute the task. The default value is zero (0).|
|Annotation|HLAunicodeString|Optional. A general text describing information about this task. The annotation may, e.g. include the reason for the task and text describing the names of referenced entities.|
|MainTask|UUID|Optional. Provided to indicate that this task is a subtask related to a main task.|
|PreviousTask|UUID|Optional. Provided to indicate that the task will execute after the referenced task.|
|NextTask|UUID|Optional. Provided to indicate that the task will execute before the referenced task.|
|Tasker|Callsign|Optional. Callsign of the commander of the task. If missing, the commander is undefined.|
|TaskMode|TaskModeEnum8|Optional. Determines the task mode. Default NonConcurrentMode|

### Wait

Tasking of an entity to wait for a duration of time. TaskTypeEnum=42

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|WaitTaskStruct|Required: Task parameters.|

### DirectFire

Tasking an entity to fire directed at a specified target entity. TaskTypeEnum = 20

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|DirectFireTaskStruct|Required: Task parameters|

### IndirectFire

Tasking an entity to fire directed at an area. TaskTypeEnum=22

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|IndirectFireTaskStruct|Required: Task parameters|

### OperateCheckpoint

Request an entity to operate a checkpoint. The tasked entity should be within the radius of the checkpoint object. If not, a separate move task should be issued first. The tasked entity activates an inactive checkpoint and operates the checkpoint for the specified duration. TaskTypeEnum=32

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|OperateCheckpointTaskStruct|Required: Task parameters|

### OperateObservationPost

Requests an entity to operate an observation post. The tasked unit should be within in a given radius from the observation post. If not, a separate move task should be issued first. The tasked unit activates an inactive observation post and operates it for the specified duration. TaskTypeEnum=34
|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|OperateObservationPostTaskStruct|Required: Task parameters|

### Observe

Tasking of an entity to observe an area. TaskTypeEnum=31

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|ObserveTaskStruct|Required: Task parameters|

### MoveToLocation

Request a simulated entity to move to a specified destination location. The entity aligns with the path from its current position to the nearest position or waypoint on the path. The entity leaves the path at a position or waypoint on the path closest to the destination. TaskTypeEnum=28

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|MoveToLocationTaskStruct|Required: Task parameters.|

### MoveIntoFormation

Tasking a simulated entity to move into the given formation on the given location with the given heading. TaskTypeEnum=26

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|MoveIntoFormationTaskStruct|Required: Task parameters.|

### MoveInDirection

Tasking of an entity to move in a specified direction for a duration. TaskTypeEnum=25

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|MoveInDirectionTaskStruct|Required: Task parameters.|

### FollowEntity

Tasking of an entity to follow another entity at a specified distance. TaskTypeEnum=24

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|FollowEntityTaskStruct|Required: Task parameters.|

### Mount

Requesting a simulated entity to mount the specified entity. The tasked entity should be within a certain distance (tolerance specified in the federation agreements) of the entity's location to mount. TaskTypeEnum=30

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|MountTaskStruct|Required: Task parameters|

### Dismount

Requesting a simulated entity to dismount from a mounted position. TaskTypeEnum=18


### MoveByRoute

Requesting a simulated entity to move given the specified route with a given speed for reaching each waypoint. The entity should align with the path from its current position to the first waypoint on the path using the speed set for the first waypoint in the route. When reaching the last waypoint, the speed is zero (0), and movement stops.

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|MoveByRouteTaskStruct|Required: Task parameters.|

### ChangeSpeed

Tasking of an entity to change speed. TaskTypeEnum=36

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|ChangeSpeedTaskStruct|Required: Task parameters.|

### ChangeAltitude

Tasking of an entity to set move to a specified altitude. TaskTypeEnum=35

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|ChangeAltitudeTaskStruct|Required: Task parameters.|

### ChangeHeading

Tasking of an entity to change heading. TaskTypeEnum=40

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|ChangeHeadingTaskStruct|Required: Task parameters.|

### Patrol

Requesting a simulated entity to perform a patrol task. The tasked entity moves from its current position to the start of the patrol route and then moves according to the patrol route from its start point in the path through all waypoints. TaskTypeEnum=33

|Parameter|Datatype|Semantics|
|---|---|---|
|TaskParameters|PatrolTaskStruct|Required: Task parameters|

### StopAtSideOfRoad

Requesting a simulated entity to stop at the side of the road. This task is only relevant for an entity moving along a road. The current move task is cancelled, and a new move task executes to a position at the side of the road (the simulator has to calculate this location). TaskTypeEnum=39


### RequestCancelTask

Request to cancel all one or more tasks.

|Parameter|Datatype|Semantics|
|---|---|---|
|Tasks|ArrayOfUuid|Required. Tasks to cancel. If no specific tasks are indicated, the default is to cancel all scheduled and ongoing tasks for the simulation entity.|

### RequestTaskStatus

Requests the federate application modelling the tasked entity to send a `TaskStatusUpdate` interaction for the specified tasks.

|Parameter|Datatype|Semantics|
|---|---|---|
|Tasks|ArrayOfUuid|Optional. Tasks for which status reports are requested. The default, if not provided or if the list of tasks is empty, the request refers to all tasks for the tasked entity.|

### RequestTaskDelegation

Request a specific federate application to execute a task. If the delegated task is accepted, a `DelegatedTask` object is created in the federation to track the progress of task execution.

|Parameter|Datatype|Semantics|
|---|---|---|
|RequestedFederateApplication|UUID|Required. Reference to the target federate application.|
|TaskDefinition|TaskDefinition|Required. Definition of the task.|

### TaskStatusUpdate

A management task report regarding the status of a specific task assigned to an entity. The inherited parameter `Time is required.`

|Parameter|Datatype|Semantics|
|---|---|---|
|Task|UUID|Required. Reference to the task associated with the report.|
|TaskStatus|TaskStatusEnum32|Required. The status of the task.|
|Comments|HLAunicodeString|Optional. Any additional comments, e.g. reason for cancelling, errors.|

### ETR_Report

A base interaction class for more specialized report interaction classes. The inherited parameter `Time is required.`

|Parameter|Datatype|Semantics|
|---|---|---|
|ReportId|UUID|Required: Unique identifier for the report.|
|ReportingEntity|UUID|The entity sending the report.|
|Comments|HLAunicodeString|Optional. Any additional comments associated with the report.|

### SpotReport

Report on a unit's awareness of spotted entities.

|Parameter|Datatype|Semantics|
|---|---|---|
|IdentificationLevel|IdentificationLevelEnum8|Required. The identification level of spotted entities.|
|SpottedEntities|ArrayOfSpottedEntities|Required. Spotted entities at the time of the report.|
|SensorType|EntityTypeStruct|Optional: The type of sensor that is the primary source of the report.|

### PositionStatusReport

Report on a unit's position, speed, and heading.

|Parameter|Datatype|Semantics|
|---|---|---|
|Position|LocationStruct|Required. Position of the entity at the specified time.|
|Heading|DirectionDegreesFloat32|Required. Heading of the entity.|
|Speed|VelocityMeterPerSecondFloat32|Required. Speed of the entity.|

### DamageStatusReport

Report on a unit's damage status.

|Parameter|Datatype|Semantics|
|---|---|---|
|DamageType|DamageStatusEnhancedEnum32|Required. Damage state of the reported entity.|

### ResourceStatusReport

Report on a unit's remaining amount of resources.

|Parameter|Datatype|Semantics|
|---|---|---|
|Resource|SupplyStruct|Required. The type of resource and remaining quantity.|

### UnderAttackStatusReport

Report from a unit that it is under attack.

|Parameter|Datatype|Semantics|
|---|---|---|
|FromDirection|DirectionDegreesFloat32|Required. The direction of the attack.|
|Severeness|AttackTypeEnum32|Required. Severeness of the attack upon the reporting entity.|

### InWeaponRangeReport

Report on a unit's ability to reach specific targets with its weapon systems.

|Parameter|Datatype|Semantics|
|---|---|---|
|WeaponType|EntityTypeStruct|Required. The type of weapon that is in range.|
|EntitiesInWeaponRange|ArrayOfUuid|Required. Reference to entities in weapon range.|

## Datatypes

Note that only datatypes defined in this FOM Module are listed below. Please refer to FOM Modules on which this module depends for other referenced datatypes.

### Overview
|Name|Semantics|
|---|---|
|ArrayOfSpottedEntities|The spotted entities at a specific time|
|ArrayOfSpottedEquipment|An array with spotted equipment at the spotted entity.|
|ArrayOfTaskDefinitions|Array containing task definitions.|
|ArrayOfTaskProgress|Array of task progress types.|
|ArrayOfTaskTypes|A set of types of tasks.|
|ArrayOfWaypoints|Array of waypoints with location and the speed to the waypoint.|
|AttackTypeEnum32|The kind of attack by the enemy.|
|ChangeAltitudeTaskStruct|Task-specific data for ChangeAltitude|
|ChangeHeadingTaskStruct|Task-specific data to turn to the specified heading.|
|ChangeSpeedTaskStruct|Task-specific data for ChangeSpeedTask task.|
|DirectFireTaskStruct|Task-specific data for direct fire.|
|ElapsedTimeProgress|Progress definition for tasks only needing elapsed time.|
|EmptyTaskStruct|No task parameters.|
|FireTaskProgress|Task progress data for Fire tasks.|
|FollowEntityTaskStruct|Task-specific data for FollowEntity|
|IdentificationLevelEnum8|The identification level of an object.|
|IndirectFireTaskStruct|Task-specific data for IndirectFire task.|
|MountTaskStruct|Task-specific data for Mount task.|
|MoveByRouteTaskStruct|Task-specific data for MoveByRoute.|
|MoveInDirectionTaskStruct|Tasking of an entity to move in a specified direction for a given duration.|
|MoveIntoFormationTaskStruct|Initial movement speed.|
|MoveTaskProgress|Task progress data for all move tasks with a path. If the next waypoint index < the last waypoint index, it indicates the reverse movement along a route.|
|MoveToEntityTaskStruct|Task-specific data for MoveToEntity.|
|MoveToLocationTaskStruct|Task-specific data for MoveToLocation task.|
|MoveTypeEnum32|CrossCountry: move directly to the destination without considering the roads. OnlyRoads: stay on the roads to get to the closest point to the destination that is still on the road; if there is no road very near to the start (within around 10 meters), there will be no movement. RoadsAndCrossCountry: move to the destination by considering the roads; it is allowed to go off the road.|
|ObserveTaskStruct|Task-specific data for Observe task.|
|OperateCheckpointTaskStruct|Task-specific data for OperateCheckpoint task.|
|OperateObservationPostTaskStruct|Task-specific data for OperateObservationPost task.|
|PatrolMoveTypeEnum32|Defines the movement during the execution of the patrol.|
|PatrolTaskProgress|Task progress data for PatrolRepeating tasks.|
|PatrolTaskStruct|Task-specific data for a Patrol task.|
|PatrolTypeEnum32|Other - The behaviour is federate application specific (e.g. wait for the next command). Circle - At the end of the route, move to the start point of the patrol route (the federate application determines the route). Reverse - Follow the patrol route in reverse order.|
|RoundStruct|Details of munition fired.|
|RulesOfEngagementEnum8|Rules of engagement for a simulated entity.|
|SpottedEntity|Descripton of the observed entity. The symbol contains information about the spotted entity's relation to the spotter and details about the type and echelon of the spotted entity.|
|SpottedEquipment|Equipment at the spotted entity.|
|TaskDefinition|Fixed record to describe the definition of a task.|
|TaskDefinitionVariantRecord|Variant record for task definition data.|
|TaskModeEnum8|Specifies if task execution is in non-concurrent or concurrent mode.|
|TaskProgress|Fixed record to describe the progress of an executing task.|
|TaskProgressVariantRecord|Variant record for task progress data.|
|TaskStatusEnum32|The status of a task.|
|TaskTypeEnum|Task types.|
|WaitTaskStruct|Task-specific data for Wait task.|
|Waypoint|A location and the speed to reach that location.|
        
### Enumerated Datatypes
|Name|Representation|Semantics|
|---|---|---|
|AttackTypeEnum32|HLAinteger32BE|The kind of attack by the enemy.|
|IdentificationLevelEnum8|HLAoctet|The identification level of an object.|
|MoveTypeEnum32|HLAinteger32BE|CrossCountry: move directly to the destination without considering the roads. OnlyRoads: stay on the roads to get to the closest point to the destination that is still on the road; if there is no road very near to the start (within around 10 meters), there will be no movement. RoadsAndCrossCountry: move to the destination by considering the roads; it is allowed to go off the road.|
|PatrolMoveTypeEnum32|HLAinteger32BE|Defines the movement during the execution of the patrol.|
|PatrolTypeEnum32|HLAinteger32BE|Other - The behaviour is federate application specific (e.g. wait for the next command). Circle - At the end of the route, move to the start point of the patrol route (the federate application determines the route). Reverse - Follow the patrol route in reverse order.|
|RulesOfEngagementEnum8|HLAoctet|Rules of engagement for a simulated entity.|
|TaskModeEnum8|HLAoctet|Specifies if task execution is in non-concurrent or concurrent mode.|
|TaskStatusEnum32|HLAinteger32BE|The status of a task.|
|TaskTypeEnum|HLAinteger32BE|Task types.|
        
### Array Datatypes
|Name|Element Datatype|Semantics|
|---|---|---|
|ArrayOfSpottedEntities|SpottedEntity|The spotted entities at a specific time|
|ArrayOfSpottedEquipment|SpottedEquipment|An array with spotted equipment at the spotted entity.|
|ArrayOfTaskDefinitions|TaskDefinition|Array containing task definitions.|
|ArrayOfTaskProgress|TaskProgress|Array of task progress types.|
|ArrayOfTaskTypes|TaskTypeEnum|A set of types of tasks.|
|ArrayOfWaypoints|Waypoint|Array of waypoints with location and the speed to the waypoint.|
        
### Fixed Record Datatypes
|Name|Fields|Semantics|
|---|---|---|
|ChangeAltitudeTaskStruct|Altitude|Task-specific data for ChangeAltitude|
|ChangeHeadingTaskStruct|Heading|Task-specific data to turn to the specified heading.|
|ChangeSpeedTaskStruct|Speed|Task-specific data for ChangeSpeedTask task.|
|DirectFireTaskStruct|Target, Duration, Round|Task-specific data for direct fire.|
|ElapsedTimeProgress|ElapsedTime|Progress definition for tasks only needing elapsed time.|
|EmptyTaskStruct||No task parameters.|
|FireTaskProgress|ElapsedTime, MunitionUsed|Task progress data for Fire tasks.|
|FollowEntityTaskStruct|FollowedEntity, Behind, Right, Above, Duration|Task-specific data for FollowEntity|
|IndirectFireTaskStruct|Area, Duration, Round|Task-specific data for IndirectFire task.|
|MountTaskStruct|EntityId|Task-specific data for Mount task.|
|MoveByRouteTaskStruct|Route, MoveType|Task-specific data for MoveByRoute.|
|MoveInDirectionTaskStruct|Direction, Speed, Duration|Tasking of an entity to move in a specified direction for a given duration.|
|MoveIntoFormationTaskStruct|Formation, Location, Distance, Heading, Speed|Initial movement speed.|
|MoveTaskProgress|LastPassedWaypointIndex, NextWaypointIndex|Task progress data for all move tasks with a path. If the next waypoint index < the last waypoint index, it indicates the reverse movement along a route.|
|MoveToEntityTaskStruct|Entity, Path, MoveType|Task-specific data for MoveToEntity.|
|MoveToLocationTaskStruct|Location, Path, MoveType, Speed|Task-specific data for MoveToLocation task.|
|ObserveTaskStruct|ObservationArea|Task-specific data for Observe task.|
|OperateCheckpointTaskStruct|CheckpointId, Duration, DelayTime|Task-specific data for OperateCheckpoint task.|
|OperateObservationPostTaskStruct|ObserveTask, Duration, ObservationPostId|Task-specific data for OperateObservationPost task.|
|PatrolTaskProgress|PathProgress, ElapsedTime, IntervalElapsedTime|Task progress data for PatrolRepeating tasks.|
|PatrolTaskStruct|Path, PatrolType, MoveType, Duration, IntervalTime|Task-specific data for a Patrol task.|
|RoundStruct|WeaponType, MunitionType, QuantityFired, RateOfFire|Details of munition fired.|
|SpottedEntity|SpottedEntity, Location, Orientation, Speed, Equipment, Activity, Symbol|Descripton of the observed entity. The symbol contains information about the spotted entity's relation to the spotter and details about the type and echelon of the spotted entity.|
|SpottedEquipment|Type, NumberOfEquipment|Equipment at the spotted entity.|
|TaskDefinition|TaskId, TaskedEntity, Tasker, StartTime, Annotation, TaskMode, Activity, Status, TaskParameters, MainTask, PreviousTask, NextTask|Fixed record to describe the definition of a task.|
|TaskProgress|TaskId, LastUpdated, ExecutingFederateId, ETC, ProgressData|Fixed record to describe the progress of an executing task.|
|WaitTaskStruct|Duration|Task-specific data for Wait task.|
|Waypoint|Location, Speed|A location and the speed to reach that location.|
        
### Variant Record Datatypes
|Name|Discriminant (Datatype)|Alternatives|Semantics|
|---|---|---|---|
|TaskDefinitionVariantRecord|TaskType (TaskTypeEnum)|NoTaskParameters, DirectFire, IndirectFire, FollowEntity, MoveInDirection, MoveIntoFormation, MoveToEntity, MoveToLocation, Mount, Observe, OperateCheckpoint, OperateObservationPost, Patrol, ChangeAltitude, ChangeSpeed, ChangeHeading, Wait|Variant record for task definition data.|
|TaskProgressVariantRecord|TaskType (TaskTypeEnum)|ElapsedTime, FireTask, MoveOnPath, Patrol|Variant record for task progress data.|
    