# NETN-AIS


|Version| Date| Dependencies|
|---|---|---|
|2.0|2024-03-10|NETN-BASE, RPR-Communication, NETN-ETR, NETN-ORG, NETN-SMC|

> [Full Documentation](NETN-AIS.md)

The purpose of the NATO Education and Training Network Automatic Identification System Module (NETN-AIS) is to:     
        
* represent vessel traffic in a simulation using AIS messages to, for example, communicate position status reports of vessels.   
* enable the exchange of AIS messages between HLA Federate Applications in real-time and non-real-time platform-level simulation.   
* allow HLA Federate Applications to use regular HLA interaction classes and parameters to represent vessel information and leave any translations to physical message formats to dedicated gateways.


AIS is a worldwide automated tracking system used for sharing vessel identification and location information by propagating messages between nearby vessels and Vessel Traffic Services stations.

The NETN-AIS module is a simulation-oriented representation of AIS messages. It does not focus on the physical message format defined by the AIS standard ITU-R M.1371-5. However, the module is aligned with this standard to enable easy mapping to and from live message formats.

## License

Copyright (C) 2020 NATO/OTAN. This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

The work includes the NETN-AIS.xml FOM Module and documentation.

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
|v1.0 - Developed by MSG-163 for NETN FOM v3.0|
|v2.0 - Developed by MSG-191 for NETN FOM v4.0|

> [Changelog](changelog.md)

