# AMSP-04 NETN FAFD Ed B

AMSP-04 NETN Ed A is currently being updated to Ed B by NATO Research Task Group MSG-163.

## Proposed Changes
* Merging of Logistics and SCP FOM Modules
* Renaming and updating LLBML (to ETR) for Entity Tasking and Reporting.
* New module NETN-ORBAT for representation of Task Organizations, Holdings, Org. relationships and initial allocation of modelling responsibilities.
* New module NETN-METOC (in collaboration with MSG-156) for representation of Weather and weather effects.
* New module NETN-AIS for representation of AIS tracks in simulation.

## Schedule
- Q1 2019 Drafting NETN-ETR Module
- Q2 2019 Pre-release NETN-ETR Module
- Q3 2019 Drafting NETN-ORBAT Module, NETN-LOG module & NETN-METOC Module
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

<img src="images/dependencies.svg"/>

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
}
-->
