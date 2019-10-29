# NETN FOM v3.0

## Background
In 2006, NATO Allied Command Transformation (ACT) requested NATO Modelling
and Simulation Group (NMSG) to explore the concepts of a NATO Education and Training Network capability. An exploratory team (ET-025) was set up to analyze the requirement and it proposed a technical activity to develop the NETN concepts. 

In 2007, the NMSG technical activity **MSG-068 NETN** was started. The group was led by NATO Joint Warfare Center (JWC) and with participants from NATO HQ-SACT, NATO Joint Forces Training Center (JFTC), NATO Consultancy, Command and Control Agency (NC3A) and 13 Nations (Australia, Bulgaria, France, Germany, Hungary, Netherlands, Romania, Slovenia, Spain, Sweden, Turkey, UK, USA). MSG-068 assessed the distributed simulation and learning capabilities that could contribute to the development of an NETN capability and drafted standards to better enable reuse and sharing of national Modelling and Simulation systems. The capabilities were demonstrated at I/ITSEC 2010 and the group ended its work in 2011. A NETN Federation Architecture and FOM Design specification (NETN FAFD) was produced which included the **NETN-FOM v1.0** published in February 2012. 

In early 2012, the NMSG technical activity **MSG-106 SPHINX** was started as a follow-on to MSG-068 but with a slightly larger scope. The technical subgroup of MSG-106 continued to work on the NETN FAFD specification and delivered a draft NETN-FOM v2.0 which included several new FOM modules and other improvements. The updated FOM was also included in the draft Allied Modelling and Simulation Publication (AMSP-04) NATO Education and Training Network Federation Architecture and FOM Design (NETN FAFD).

In late 2014, the NMSG technical activity **MSG-134 NATO Distributed Simulation Architecture & Design, Compliance Testing and Certification** was started as a follow-on for continued maintenance of the NETN FAFD and to continue work on establishing the NATO HLA certification process identified in STANAG 4603. The group did not add any new modules to the NETN-FOM but it assisted NMSG in updating the draft AMSP-04 to a final version inclduing an official **NETN-FOM v2.0** release. The group ended its work in late 2017 and the AMSP-04 was later promulgted and published by NATO in March 2018 and is covered by NATO STANREC 4800.

In early 2018, the NMSG technical activity **MSG-163 Evolving NATO Standards for Federated Simulation** started as a follow-on to MSG-134. In late 2020 the group will provide a draft updated AMSP-04 Ed B NETN FAFD document including **NETN-FOM v3.0** that incudes both new modules and several updates based on NATO and national experiences using the NETN-FOM.

## Concepts

A **Federation** is a union of essentially independent applications (**Federates**) interoperating using the common infrastructure services accessed through well-defined standard interfaces and governed by common agreements on modelling responsibilities and information exchange. 

**NATO STANAG 4603** mandates the use of IEEE 1516 standards on High-Level Architecture (**HLA**) for federates and federations. 

The HLA standard specifies how to document information exchange using a Federation Object Model (**FOM**). Different domains may have different FOMs but can use the same underlying simulation infrastructure standard. 

HLA services are provided by a Run-Time Infrastructure (**RTI**). On the network the RTI acts as a distributed operating system providing the standard HLA interfaces to the federates. Internally the RTI uses distributed algorithms and network protocols to implement all HLA services. 

**Federation architecture** is the style of design and method of integration to create coherent distributed simulation systems based on federates and a common service-oriented infrastructure. 

**Federation design** is detailed specification of a federation that meet requirements for a specific simulation solution used to support simulation based events such as a Computer Assisted eXercises (CAX).

The **NETN Federation Architecture** mandates the use of HLA (in accordance with STANAG 4603) and the use of the NETN FOM. 

## NETN FOM Modules

The NETN FOM is defined as the complete set of NETN FOM Modules plus all modules they depend on (e.g. RPR-FOM modules). The modules have inter-dependencies and are designed to maximize re-use and interoperability. All NETN FOM modules are provided as HLA IEEE 1516-2010 OMT Data Interchange Format XML files.
 

## License

Copyright (C) 2019 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md). 

The work includes all the NETN FOM Modules and related [documentation](NETN-FOM.md).

Above license gives you the right to use and redistribute the NETN FOM (XML files<> and Documentation) in its entirety without modification. You are also allowed to develop your own new FOM Modules (in separate XML files and separate documentation) that build-on/extends the NETN FOM by reference and including neccessary scaffolding classes. You are NOT allowed to modify the NETN FOM or its documentation without prior permission by the NATO Modelling and Simulation Group. 

## Versions, updates and extentions

All updates and versioning of this work is coordinated by the NATO Modelleing and Simulation Coordination Office (MSCO), managed by the NATO Modelling and Simulation Group (NMSG) and performed as NATO Science and Technology Organization (STO) technical activities in support of the NMSG Modelling and Simulation Standards Subgroup (MS3).

Feedback on the use of this work, suggestions for improvements and identified issues are welcome and can be provided using GitGub issue tracking. To engage in the development and update of NETN-FOM, please contact your national NMSG representative.

Version numbering of the NETN-FOM and associated documentation is based on the following principles:

* New official version number is assigned and in effect only when new release is made in the Master branch.
* Updates in the Develop branch will not change version number.
* Update of the major version number is made if the change constitute a major restructuring, merging, addition or redefinition of semantics that breaks backward compatibility or cover entirely new concepts.
* Update of the minor version number is made if the change constitute a minor additions to existing concepts and editorial changes that do not break backward compatibility but may require updates of software to use new concepts.
* Patches are released to fix minor issues that do not break backward compatibility.

|Version|Description|
|---|---|
|v1.0|Initial release of NETN FOM as developed by MSG-068 |
|v2.0|Update release of NETN FOM included in AMSP-04 Ed A v1.0. New modules NETN-SCP-BASE, NETN-Supply, NETN-Storage, NETN-Repair, NETN-Transport, NETN-CBRN|
|v3.0|Update release of NETN FOM included in AMSP-04 Ed B v1.0. New modules NETN-METOC, NETN-LOG (replaces NETN-SCP-BASE, NETN-Supply, NETN-Storage, NETN-Repair, NETN-Transport), NETN-ORG, NETN-ETR (replaces NETN-LLBML), NETN-AIS. Updates of all other modules.|

[Changelog](changelog.md)

## Documentation

[Full Documentation](NETN-FOM.md)
