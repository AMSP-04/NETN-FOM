# NETN-SMC


|Version| Date| Dependencies|
|---|---|---|
|1.0|2023-11-20|NETN-BASE|

> [Full Documentation](NETN-SMC.md)

The NATO Education and Training Service Management and Control (NETN-SMC) module provides a standard way to send control actions in a federated simulation. Control actions are interactions targeting the federation, an individual federate, or an individual simulated entity.

In a federated distributed simulation, the participating systems (federates) provide services to model aspects of the synthetic environment. To simulate model change, these services use operator input, data published in the federation, and the passing of scenario time.

The NETN-SMC module provides methods to interact with services using control actions and defines a Request-Response pattern. The control actions described in this module form the basis for subclassing more specific actions in other FOM modules.

## License

Copyright (C) 2020 NATO/OTAN. This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

The work includes the NETN-SMC.xml FOM Module and documentation.

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
|v1.0 - Version developed by MSG-191. Release included in NETN FOM v4.0|

> [Changelog](changelog.md)

