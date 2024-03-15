# NETN-METOC


|Version| Date| Dependencies|
|---|---|---|
|2.0|2023-04-13|NETN-BASE|

> [Full Documentation](NETN-METOC.md)

The purpose of the NATO Education and Training Network (NETN) Meteorological and Oceanographic (METOC) Module is to provide a standard way to exchange data related to weather conditions and the primary effects of weather on terrain and water surfaces in the atmosphere and subsurface water conditions. The main objective is to provide a reference model that represents a common core subset of METOC-related aspects and to allow the extension of the module to incorporate additional detail if required. Therefore, the NETN-METOC module is a reference FOM module where extensions are allowed and encouraged to meet federation-specific requirements fully.

This module specifies how to represent METOC-related data in a federated distributed simulation. The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and supports interoperability in a federated simulation (federation) based on HLA.

Current weather conditions impact simulations such as platforms and sensors on the ground, sea, underwater and in the air. A correlated representation of these conditions is key to meeting interoperability and model requirements in a federated distributed simulation. Different simulations require different fidelity of weather conditions concerning data resolution and accuracy. The NETN-METOC focus on representing weather conditions for related surfaces and layers. The main difference is that a surface condition does not have a volume and only represents the conditions directly related to the surface of a piece of terrain or water. The layer conditions represent a volume of water or air with height/depth from surface and layer thickness. Environmental conditions have explicit locations or positions related to other simulated entities and objects in the synthetic environment.

NETN-METOC covers the most common levels of representation required by a large set of existing simulators.

## License

Copyright (C) 2020 NATO/OTAN. This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

The work includes the NETN-METOC.xml FOM Module and documentation.

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
|v1.0 - Initial version developed by MSG-163. Release included in NETN-FOM v3.0|
|v2.0 - Updates developed by MSG-191 and included in NETN-FOM v4.0|

> [Changelog](changelog.md)

