# NETN-ETR


|Version| Date| Dependencies|
|---|---|---|
|3.0 |2023-04-07|NETN-BASE|

> [Full Documentation](NETN-ETR.md)

The NETN-ETR FOM module provides a standard interface for sending tasks to simulated entities represented in a federated distributed simulation. NETN-ETR contains low-level tasks that can easily be interpreted and executed by simulators that model the behaviour of entities. It also defines a set of reports to provide status information, including the status of task execution.

The NATO Education and Training Network (NETN) Entity Tasking and Reports (ETR) Module specifies how to represent simulation task requests provided to participants in a federated distributed simulation and simulator reports sent during the execution of tasks. 
        
The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and supports interoperability in a federated simulation (federation) based on HLA.
        

The NETN-ETR module focuses on tasking simulated entities: 
    
* It enables the transformation of command and control messages into tasks that a simulator can execute. 
* It defines a comprehensive set of tasks and reports that simulators can easily interpret and execute.
* It reflects the capabilities commonly found in COTS Computer Generated Forces (CGF) applications but is independent of a specific CGF, agent framework, or agent modelling paradigm. 
* It is independent of any specific doctrine or tactics. 

A tasked entity can be either a physical entity (e.g. platform or lifeform) or an aggregate entity. The task definition itself does not specify how a simulation models the execution of the task.

## License

Copyright (C) 2020 NATO/OTAN. This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

The work includes the NETN-ETR.xml FOM Module and documentation.

The licence gives you the right to use and redistribute the NETN FOM Module (XML file and Documentation) in its entirety without modification. You are also allowed to develop new FOM Modules (in separate XML files and separate documentation) that build on or extend the NETN module by referencing and including necessary scaffolding classes. You are NOT allowed to modify this FOM Module or its documentation without prior permission from the NATO Modelling and Simulation Group.

## Versions, updates and extensions

All updates and versioning of this work are coordinated by the NATO Modelling and Simulation Coordination Office (MSCO), managed by the NATO Modelling and Simulation Group (NMSG) and performed as NATO Science and Technology Organization (STO) technical activities in support of the NMSG Modelling and Simulation Standards Subgroup (MS3).

Feedback on the use of this work, suggestions for improvements and identified issues are welcome and can be provided using GitHub issue tracking. To engage in the development and update of this FOM Module please contact your national NMSG representative.

Version numbering of this FOM Module and associated documentation is based on the following principles:

* A new official version number is in effect only when a new release is made in the Master branch.
* An update of the major version number is made if the change constitutes a major restructuring, merging, addition or redefinition of semantics that breaks backward compatibility or covers entirely new concepts.
* An update of the minor version number is made if the change constitutes minor additions to existing concepts and editorial changes that do not break backward compatibility but may require updates of software to use new concepts.
* Patches are released to fix minor issues that do not break backward compatibility.

|Version|
|---|
|v1.1 - NETN-LBML. Developed by MSG-106 and MSG-134 for NETN FOM v2.0.|
|v2.0 - Renamed and updated by MSG-163 for NETN FOM v3.0|
|v3.0 - Updated by MSG-191 for NETN FOM v4.0|

> [Changelog](changelog.md)

