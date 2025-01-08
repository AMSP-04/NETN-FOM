# NETN-TMR


|Version| Date| Dependencies|
|---|---|---|
|3.0|2024-03-10|NETN-BASE, NETN-ORG, NETN-SMC|

> [Full Documentation](NETN-TMR.md)

The NATO Education and Training Network Transfer of Modelling Responsibilities (NETN-TMR) module provides a standard interface and pattern for transferring modelling responsibility between federates. It extends the HLA Ownership Management services by providing the means to trigger modelling responsibility transfer and publish the assigned modelling responsibilities of object instances.
        
For example:
            
* Transfer modelling responsibility between virtual and constructive simulation systems.  
* Transfer modelling responsibility between high- and low-fidelity models.
* Transfer modelling responsibility to allow backup, maintenance or load-balancing.

In a federated distributed simulation, the participating systems (federates) provide services that model the synthetic environment. Allocation of modelling responsibilities depends on individual federate capabilities, federation design agreements, and initial scenario conditions. The primary responsibility for modelling a simulated entity is allocated to, at most, one federate. However, during execution, the modelling responsibility and ownership of individual attributes may change.

NETN-TMR covers the following cases:            
* Initialization with assigned modelling responsibilities for objects. 
* Explicit request to acquire modelling responsibility.
* Triggering modelling responsibility transfer by updating the allocation of responsibility attribute.

## License

Copyright (C) 2020 NATO/OTAN. This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

The work includes the NETN-TMR.xml FOM Module and documentation.

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
|v1.1 - Released version part of NETN FOM v2.0 in AMSP-04 Ed A.|
|v2.0 - Released version part of NETN FOM v3.0 in AMSP-04 Ed B.|
|v3.0 - Released version part of NETN FOM v4.0 in AMSP-04 Ed C.|

> [Changelog](changelog.md)

