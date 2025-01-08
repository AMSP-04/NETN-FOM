# NETN-MRM


|Version| Date| Dependencies|
|---|---|---|
|3.0|2024-03-10|NETN-BASE, NETN-SMC, NETN-ORG|

> [Full Documentation](NETN-MRM.md)

The NATO Education and Training Network Multi-Resolution Modelling (NETN-MRM) module supports federations with entities represented at multiple resolution levels.

Models of real-world objects, processes and phenomena are used to create a synthetic representation suitable for the simulation. Entities can be represented as individual objects or as part of an aggregated object. Entity representation can change during the simulation and switch between different levels of aggregation and individual physical entities.  

The NETN-MRM module specifies aggregation, disaggregation, division and merging of aggregate entities.

NETN-MRM covers the following cases: 
* Aggregation of subunits into a representation of their parent unit
* Disaggregation of a unit representation into subunits
* Division of unit into subunits or physical entities
* Merging of previously divided entities into a unit

## License

Copyright (C) 2020 NATO/OTAN. This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

The work includes the NETN-MRM.xml FOM Module and documentation.

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
|v1.1 - Initial version of NETN-MRM FOM Module released as part of NETN FOM v2.0.|
|v2.0 - Updated version by MSG-163 to be part of NETN FOM v3.0.|
|v3.0 - Updated version by MSG-191 to be part of NETN FOM v4.0|

> [Changelog](changelog.md)

