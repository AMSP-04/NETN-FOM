# AMSP-04 Ed B v1.0 NETN FAFD 

AMSP-04 NETN Ed A v1.0 is currently being updated to AMSP-04 NETN Ed B v1.0 by NATO Research Task Group MSG-163.

## Proposed Changes
* Merge NETN-SCP-Base, NETN-Repair, NETN-Transport, NETN-Supply and NETN-Storage
* Rename and update NETN-LLBML
* Add module NETN-ORG for representation of Task Organizations, Holdings, Org. relationships and initial allocation of modelling responsibilities
* Add module NETN-METOC (in collaboration with MSG-156) for representation of Weather and weather effects
* Add module NETN-AIS for representation of AIS tracks in simulation
* Update all other modules

## Schedule
- Q1 2019 Drafting NETN-ETR Module
- Q2 2019 Pre-release NETN-ETR Module
- Q3 2019 Drafting NETN-ORG Module, NETN-LOG module & NETN-METOC Module
- Q4 2019 Pre-release of NETN-ORBAT Module, NETN-LOG Module & NETN-METOC Module
- Q1 2020 Drafting of NETN-AIS Module
- Q2 2020 Pre-release of NETN-AIS Module
- Q3 2020 Drafting of AMSP-04 Ed b
- Q4 2020 NMSG MS3 approval of final draft of AMSP-04 Ed B. Submit AMSP-04 to NSO for publication and update of STANREC 4800 to cover the updated standard.
- 2021 Expect AMSP-04 Ed B officially published.

_Changes to the schedule is possible_

## Involvement
Please contact your national NATO Modelling and Simulation Group representative for more information how to join MSG-163 or provide your commets directly through GitHub.

## FOM Module Dependencies

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
	"NETN-PHYS" -> "RPR-Physical"
	"NETN-AGG" -> "RPR-Aggregate"
	"NETN-METOC" -> "NETN-BASE"
	"NETN-MRM" -> "NETN-TMR"
	"NETN-TMR" -> "NETN-BASE"
	"NETN-CBRN" -> "NETN-PHYS"
	"NETN-ETR" -> "NETN-BASE"

}

-->


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

## Documentation

[Full Documentation](NETN-FOM.md)
