## Changelog NETN-FOM

### Changes in v 3.0
Version 3.0 of the NETN-FOM is included in AMSP-04 Ed B v1.0 and is based on updates made by MSG-163.



#### NETN-FOM#14 Add NETN FOM Module for representing MSDL information
* Added FOM Module NETN-ORG for representation of Organization

#### NETN-FOM#15 add NETN FOM Module to extend RPR SE
* Added representation of CheckPoint to NETN-Physical FOM Module. No NETN-SE Module added.

#### NETN-FOM#17 Add NETN FOM Module for METOC
* Added NETN-METOC FOM Module

#### NETN-FOM#20 dd support for AIS information #20
* Added FOM Module NETN-AIS for representation of Vessel Traffic Information and Data

#### NETN-FOM#21 Merge Logistics FOM Modules
* Added NETN-LOG FOM Module
* Merged NETN-SCP-Base, NETN-Repair, NETN-Transport, NETN-Supply, NETN-Storage into NETN-LOG
* Removed NETN-SCP-Base - included in NETN-LOG
* Removed NETN-Repair - included in NETN-LOG
* Removed NETN-Transport - included in NETN-LOG
* Removed NETN-Supply - included in NETN-LOG
* Removed NETN-Storage - included in NETN-LOG

#### NETN-FOM#22 Rename LBML Module
* LBML module renamed to NETN-ETR (Entity Tasking and Reporting)




### Changes in v 2.0 
Version 2.0 of the NETN-FOM is included in AMSP-04 Ed A v1.0 and is based on updates made by MSG-106 and MSG-134.

New Modules
* NETN-Base (NETN-Base_v1.0.2.xml)
* NETN-Physical (NETN-Physical_v1.1.2.xml) - extends RPR-FOM v2.0
* NETN-CBRN (CBRN_v1.1.9.xml)
* NETN-MRM (MRM_v1.1.1.xml)
* NETN-TMR (TMR_v1.1.3.xml)
* NETN-HCBML (NETN-HCBML_v1.1.1.xml)
* NETN-LLBML (NETN-LBML_v1.1.0.xml)

Updated/Restructured Modules
* NETN-Aggregate (NETN-Aggregate_v1.0.4.xml) - updated and based on NETN-Base - extends RPR-FOM v2.0
* NETN-SCP-Base (NETN-SCP-Base_v1.1.3.xml) - updated
* NETN-Repair (NETN-Repair_v1.2.1.xml) - from NETN Logistics FOM Module
* NETN-Storage (NETN-Storage_v1.2.2.xml) - from NETN Logistics FOM Module
* NETN-Supply (NETN-Supply_v1.1.2.xml) - from NETN Logistics FOM Module
* NETN-Transport (NETN-Transport_v1.1.2.xml) - from NETN Logistics FOM Module

### Version 1.0
Version 1.0 of the NETN-FOM was developed by MSG-068.

Referenced/extended modules

* RPR‐FOM v2.0 D17 (r2) 
* Link 16 FOM Module v1.0 D2 (r2)

New Modules

* NETN Service Consumer‐Provider FOM Module v1.0
* NETN Logistics FOM Module v1.0
* NETN Aggregate FOM Module v1.0