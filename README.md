# NETN FOM
NATO Education and Training Network (NETN) Federation Object Model (FOM)

## Introduction

The NETN FOM is an identified set of HLA FOM Modules. The modules are recommended for use when implementing NATO AMSP-04 NETN FAFD compliant distributed simulation. 

The modules have inter-dependencies and have been designed to maximize re-use and interoperability with legacy systems using existing standards, and those having requirements for new patterns of simulation interoperability. The NETN FOM is the complete set of NETN modules and all other modules they depend on, e.g. the SISO RPR-FOM.

### Purpose
The NETN FOM provides a standard interfaces for the representation of simulated entities, events, and other models of real-world objects, processes and phenomenon. It also provide standard interfaces and patterns for simulation interplay between systems in a federated distributed simulation to allow multi-resolution modelling, transfer of modelling responsibilities, tasking and simulation control.

## Licence

Copyright (C) 2020 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md). 

The work includes all the NETN FOM Modules and related [documentation](NETN-FOM.md).

Above licence gives you the right to use and redistribute the NETN FOM (XML files and Documentation) in its entirety without modification. You are also allowed to develop new FOM Modules (in separate XML files and separate documentation) that build-on/extends the NETN FOM by reference and including necessary scaffolding classes. You are NOT allowed to modify the NETN FOM or its documentation without prior permission by the NATO Modelling and Simulation Group. 

## Versions, updates and extensions

All updates and versioning of this work is coordinated by the NATO Modelling and Simulation Coordination Office (MSCO), managed by the NATO Modelling and Simulation Group (NMSG) and performed as NATO Science and Technology Organization (STO) technical activities in support of the NMSG Modelling and Simulation Standards Subgroup (MS3).

Feedback on the use of this work, suggestions for improvements and identified issues are welcome and can be provided using GitHub issue tracking. To engage in the development and update of NETN FOM, please contact your national NMSG representative.

Version numbering of the NETN FOM and associated documentation is based on the following principles:

* New official version number is assigned and in effect only when a new release is made in the Master branch.
* Updates in the Develop branch will not change the version number.
* Update of the major version number is made if the change constitutes a major restructuring, merging, addition or redefinition of semantics that breaks backward compatibility or cover entirely new concepts.
* Update of the minor version number is made if the change constitutes minor additions to existing concepts and editorial changes that do not break backward compatibility but may require updates of software to use new concepts.
* Patches are released to fix minor issues that do not break backward compatibility.

|Version|Description|
|---|---|
|v1.0|Initial release of NETN FOM as developed by MSG-068 |
|v2.0|Release of NETN FOM included in AMSP-04 Ed A|
|v3.0|Release of NETN FOM included in AMSP-04 Ed B|

[Changelog](changelog.md)

## Maintenance on GitHub
* The master branch of each NETN FOM Module repository contains the official public releases of the module.
* The develop branch of each NETN FOM Module repository contains the intermediate baseline releases of the module and the lasest build/merge of other feature branches/forks used by members of the maintenance team to update the module.

[Work Flow](flow.md)

[Naming Conventions](NamingConventions.md)

## Documentation

[Full Documentation](NETN-FOM.md)

