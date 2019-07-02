# NETN FOM
 
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
 


<img src="images/dependencies.png"/>

<!--
# Vis-js.com

digraph G {

	"RPR-Base" -> "RPR-Foundation";
	"NETN-BASE" -> "RPR-Foundation"
	"NETN-LOG" -> "RPR-Base"
	"NETN-LOG" -> "NETN-BASE"
	"RPR-Physical" -> "RPR-Base"
		"RPR-Aggregate" -> "RPR-Base"
	"NETN-Physical" -> "RPR-Physical"
	"NETN-AGG" -> "RPR-Aggregate"
	"NETN-METOC" -> "NETN-BASE"
	"NETN-MRM" -> "NETN-TMR"
	"NETN-TMR" -> "NETN-BASE"
	"NETN-CBRN" -> "NETN-Physical"
	"NETN-ETR" -> "NETN-BASE"
}
-->

Figure: The NETN FOM


|NETN FOM Module|Dependency|Description|
|---|---|---|
|NETN-Base|RPR-FOM Base|NETN common concepts and datatypes.|
|NETN-Physical||Physical platform and entities state.|
|NETN-Aggregate||Simulated Unit state.|
|NETN-ORG||Representation of task organization relationships and status.|
|NETN-LOG||Modelling of Logistics Services across federates.|
|NETN-ETR||Tasking of simulation entities and simulation task reporting.|
|NETN-CBRN||Representation of CBRN triggers, release and events.|
|NETN-METOC||Representation of weather and effects of weather.|
|NETN-AIS||Representation of simulated ship AIS data.|
|NETN-MRM||Multi-Resolution modelling including aggregation and disaggregation patterns.|
|NETN-TMR||Coordinated transfer of modelling responsibilities between federates.|

## License

Copyright (C) 2019 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENSE.md). 

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


## History

[History](history.md)

## Documentation

[Full Documentation](NETN-FOM.md)
