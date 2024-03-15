# NETN-LOG


|Version| Date| Dependencies|
|---|---|---|
|2.1|2023-03-25|NETN-BASE|

> [Full Documentation](NETN-LOG.md)

The NATO Education and Training Network (NETN) Logistics (LOG) Module provides a common standard interface for negotiation, delivery and acceptance of logistics services where service providers and consumers are represented in different systems in a federated distributed simulation.

Military logistics is the discipline of planning and carrying out the movement and maintenance of military forces including storage, distribution, maintenance and transportation of materiel.

The NATO Education and Training Network Logistics Module (NETN-LOG) is a specification of how to model logistics services in a federated distributed simulation. 
The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and is primarily intended to support interoperability in a federated simulation (federation) based on HLA. A Federation Object Model (FOM) Module is used to specify how data is represented and exchanged in the federation. The NETN-LOG FOM module is available as an XML file for use in HLA-based federations.

The NETN Logistics module covers the following services:    
* Supply Service   
* Transport Service  
* Repair service     
        
Examples of use:    
* Refuelling of aircraft at an airbase or in the air   
* Transport of supplies between facilities   
* Repair of damaged platforms in a facility or by unit  
* Transport of units, platforms, and humans by train, ship, or aircraft   
* Embarkment and disembarkment of units on platforms

## License

Copyright (C) 2020 NATO/OTAN. This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

The work includes the NETN-LOG.xml FOM Module and documentation.

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
|v1.1 - Initial version developed by MSG-068 for NETN-FOM v1.0. |
|v2.0 - Re-merged version of NETN-LOG FOM Module updated by MSG-163 for NETN-FOM v3.0. Includes NETN-SCP, NETN-Supply, NETN-Storage, NETN-Repair and NETN-Transport.|
|v2.1 - Updated version developed by MSG-191. Release included in NATO-FOM v4.0|

> [Changelog](changelog.md)

