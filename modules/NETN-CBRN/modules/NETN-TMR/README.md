# NETN-TMR


|Version| Date| Dependencies|
|---|---|---|
|2.1|2023-03-18|NETN-BASE|

> [Full Documentation](NETN-TMR.md)

The NETN-TMR FOM module provides a standard interface and protocol for conducting negotiated and coordinated transfer of attribute modelling responsibility between federates. It extends the HLA Ownership Management services by providing the means to  
1. Negotiate the transfer of ownership.  
2. Initiate ownership transfer using a Trigger federate.  A transfer of modelling responsibility is performed during runtime, to dynamically change the responsibility to update specific attributes, to a more suitable federate.  
For example:  
- Transfer from a Live to a Virtual or Constructive simulation 
- Transfer between Virtual and Constructive simulations 
- Transfer between hi- and low-fidelity models 
- Transfer to allow backup, maintenance or load-balancing 
- Transfer of certain attributes to functional models such as movement, and damage assessment.

In a federated distributed simulation, the participating systems (federates) collectively model the synthetic environment. Allocation of modelling responsibilities depends on individual federate capabilities, federation design agreements, and initial scenario conditions. The responsibility of updating an attribute for a specific simulated entity is allocated to at most one federate. However, during execution, the modelling responsibility and ownership may change. 

IEEE 1516 High Level Architecture (HLA) provides essential services for the divestiture and acquisition of attribute ownership. A negotiated and coordinated transfer of modelling responsibilities requires agreements between federates before the transfer of attribute ownership. 

The NATO Education and Training Network Transfer of Modelling Responsibilities (NETN-TMR) FOM Module is a specification of how to perform a negotiated and coordinated transfer of attribute modelling responsibility between federates in a distributed simulation. 

The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and is primarily intended to support interoperability in a federated simulation (federation) based on HLA. A Federation Object Model (FOM) Module specifies how data is represented and exchanged in the federation. The NETN-TMR FOM module is available as an XML file for use in HLA-based federations.

NETN-TMR covers the following cases:  * A negotiated acquisition where a federate requests to receive the modelling responsibility  * Negotiated divestiture where a federate requests another federate to take modelling responsibility * Acquisition without negotiation where a federate receives the modelling responsibility  * Cancellation of transfer

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
|v1.1 - Released version part of NETN-FOM v2.0 in AMSP-04 Ed A.|
|v2.0 - Released version part of NETN-FOM v3.0 in AMSP-04 Ed B.|
|v2.1 - Released version part of NATO-FOM v4.0 in AMSP-04 Ed C.|

> [Changelog](changelog.md)

