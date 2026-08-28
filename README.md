# NETN FOM
NATO Education and Training Network (NETN) Federation Object Model (FOM)

 
## Executive Summary


Efficient and effective use of NATO and national Modelling & Simulation (M&S) capabilities to support training requires standards for connecting and integrating M&S components across the training system enterprise.

The NATO Education and Training Network Federation Object Model (NETN-FOM) provides a common information exchange data model for developing interoperable distributed simulation systems.

The NETN-FOM focuses on technical interoperability issues in distributed simulation and provides patterns for scenario initialization, transfer of modelling responsibilities, simulation entity tasking, and managing dynamic changes of the model resolution.

The AMSP-04 document provides a summary of all NETN-FOM modules, key design patterns and main concepts. Full online documentation and all related data models and files are provided through http://www.github.org/AMSP-04.



## Licence

Copyright (C) 2020 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md). 

The work includes all the NETN FOM Modules and related [documentation](NETN-FOM.md).

The above licence gives you the right to use and redistribute the NETN FOM (XML files and Documentation) in its entirety without modification. You are also allowed to develop new FOM Modules (in separate XML files and separate documentation) that build on/extend the NETN FOM by reference, including necessary scaffolding classes. You are NOT allowed to modify the NETN FOM or its documentation without prior permission by the NATO Modelling and Simulation Group. 

## Versions, Updates and Extensions

All updates and versioning of this work is coordinated by the NATO Modelling and Simulation Coordination Office (MSCO), managed by the NATO Modelling and Simulation Group (NMSG) and performed as NATO Science and Technology Organization (STO) technical activities in support of the NMSG Modelling and Simulation Standards Subgroup (MS3).

Feedback on the use of this work, suggestions for improvements and identified issues are welcome and can be provided using GitHub issue tracking. To engage in the development and update of the NETN FOM, please contact your national NMSG representative.

Version numbering of the NETN FOM and associated documentation is based on the following principles:

* A new official version number is assigned and in effect only when a new release is made in the `master` branch.
* Updates in the `develop` branch will not change the version number.
* An update of the major version number is made if the change constitutes a major restructuring, merging, addition or redefinition of semantics that breaks backward compatibility or covers entirely new concepts.
* An update of the minor version number is made if the change constitutes minor additions to existing concepts and editorial changes that do not break backward compatibility, but that may require updates of software to use new concepts.
* Patches are released to fix minor issues that do not break backward compatibility.

|Version|Description|
|---|---|
|v1.0|Initial release of NETN FOM as developed by MSG-068 |
|v2.0|Release of NETN FOM included in AMSP-04 Ed A|
|v3.0|Release of NETN FOM included in AMSP-04 Ed B|
|v4.0|Release of NETN FOM included in AMSP-04 Ed C|

[Changelog](changelog.md)

## Repository Structure
* [Modules](modules/) contains each module in its subfolder. These subfolders contain the module's FOM file, documentation and any related files.
* [FomFiles_HLA4](FomFiles_HLA4/) contains only the FOM files in HLA 4 format. Same FOM files as in the _Modules_ folder but no documentation, subfolders or extra files.
* [FomFiles_Merged_HLA_Evolved](FomFiles_Merged_HLA_Evolved/) contains a merged version of the entire NETN 4 and all RPR modules in HLA Evolved format.

## Maintenance on GitHub
* The `master` branch of the NETN FOM repository contains the official public releases of the FOM.
* The `develop` branch of the NETN FOM repository contains the intermediate baseline releases of the FOM and the lasest build/merge of other feature branches/forks used by members of the maintenance team to update the FOM.

[Workflow](flow.md)

[Naming Conventions](NamingConventions.md)

## Documentation

[Full Documentation](NETN-FOM.md)

