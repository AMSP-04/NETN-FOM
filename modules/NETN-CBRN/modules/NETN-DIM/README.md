# NETN-DIM


|Version| Date| Dependencies|
|---|---|---|
|1.0|2023-04-18|RPR-SE, NETN-ETR|

> [Full Documentation](NETN-DIM.md)

The NATO Education and Training Network (NETN) Disaster Module (DIM) provides a standard interface for representing hazards, e.g. flooding and wildfire, in federated distributed simulation environments.

Hazards such as wildfire, flooding, earthquakes and landslides cause different effects in a synthetic environment and to the simulated entities. Furthermore, hazard observation reporting and activities to mitigate the effect of hazards are important aspects of simulations where hazards are part of the scenario.
        
In a federated distributed simulation, the NATO Education and Training Network Disaster Module (NETN-DIM) specifies how to model hazards and control activities to mitigate their effects. 
The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and supports interoperability in a federated simulation (federation) based on HLA.



## License

Copyright (C) 2020 NATO/OTAN. This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

The work includes the NETN-DIM.xml FOM Module and documentation.

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
|v0.9 - Initial version developed by MSG-147 and used in LOE3 experiment.|
|v1.0 - Updated version developed by MSG-191. Release included in NATO-FOM 4.0|

> [Changelog](changelog.md)

