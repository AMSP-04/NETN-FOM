# Change Proposal

## Identification information
### CPR identifier
NETN-FOM-CPR-1

### Title
NETN FOM update to v3.0.

### Initiator
Bjorn Lofstrand (Sweden)|

### Version
|Version|Date|Comment|
|----|----|----|
|v1|2019-07-02|Draft proposal and schedule for implementation.|

## Proposed change / detected problem
* Merge NETN-SCP-Base, NETN-Repair, NETN-Transport, NETN-Supply and NETN-Storage
* Rename and update NETN-LLBML
* Add module NETN-ORG for representation of Task Organizations, Holdings, Org. relationships and initial allocation of modelling responsibilities
* Add module NETN-METOC (in collaboration with MSG-156) for representation of Weather and weather effects
* Add module NETN-AIS for representation of AIS tracks in simulation
* Update all other modules

## Reason for change / cause of problem
General update of all modules based on community feedback.
Additional modules based on identified needs and requirements from real use of NETN-FOM in exercises.

## Consequences of not processing change
Less interoperability.

## Trade-offs and alternatives

## Evaluation considerations

## Proposed changes details
New modules NETN-METOC, NETN-LOG (replaces NETN-SCP-BASE, NETN-Supply, NETN-Storage, NETN-Repair, NETN-Transport), NETN-ORG, NETN-ETR (replaces NETN-LLBML), NETN-AIS. Updates of all other modules.

Change details covered in separate CPRs for each module.

### Schedule
- Q1 2019 Drafting NETN-ETR Module
- Q2 2019 Pre-release NETN-ETR Module
- Q3 2019 Drafting NETN-ORG Module, NETN-LOG module & NETN-METOC Module
- Q4 2019 Pre-release of NETN-ORG Module, NETN-LOG Module & NETN-METOC Module
- Q1 2020 Drafting of NETN-AIS Module
- Q2 2020 Pre-release of NETN-AIS Module
- Q3 2020 Drafting of AMSP-04 Ed b
- Q4 2020 NMSG MS3 approval of final draft of AMSP-04 Ed B. Submit AMSP-04 to NSO for publication and update of STANREC 4800 to cover the updated standard.
- 2021 Expect AMSP-04 Ed B officially published.
