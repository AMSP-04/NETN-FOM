# NETN-ETR


|Version| Date| Dependencies|
|---|---|---|
|3.0 |2024-03-08|NETN-BASE, NETN-SMC|

> [Full Documentation](NETN-ETR.md)

The NATO Education and Training Network Entity Tasking and Reports Module (NETN-ETR) provides a standard interface for sending tasks to simulated entities represented in a federated distributed simulation. It defines interactions that can be interpreted and executed by simulators that model the behaviour of a tasked entity. The module also defines report interactions sent by simulated entities.

Based on the SMC_EntityControl pattern, the module defines a core set of tasks for simulated entities. Other NETN-FOM modules define additional tasks. The task definitions provided in NETN reflect the capabilities commonly found in Commercial-off-the-Shelf (COTS) Computer-Generated Forces (CGF) applications but are independent of any specific CGF.

A tasked entity can be either a physical entity (e.g., platform or lifeform) or an aggregate entity. A task definition does not specify in detail how a simulation models the execution of the task.

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

