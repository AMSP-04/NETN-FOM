
The NETN FOM is an identified set of HLA FOM Modules. The modules are recommended for use when implementing NATO AMSP-04 NETN FAFD compliant distributed simulation. It provides a standard interfaces for the representation of simulated entities, events, and other models of real-world objects, processes and phenomenon. It also provide standard interfaces and patterns for simulation interplay between systems in a federated distributed simulation to allow multi-resolution modelling, transfer of modelling responsibilities, tasking and simulation control. 

The modules have inter-dependencies and have been designed to maximize re-use and interoperability with legacy systems using existing standards, and those having requirements for new patterns of simulation interoperability. The NETN FOM is the complete set of NETN modules and all other modules they depend on, e.g. the SISO RPR-FOM v2.0.

The NETN FOM v3.0 consists of the following modules:

|Module|Description|
|---|---|
|NETN&#8209;BASE| Common definitions of datatypes and extends the RPR-BASE FOM Module.|
|NETN&#8209;Physical|Representation of Physical Entities in a federated distributed simulation. |
|NETN&#8209;MRM| Aggregate level entity simulation, aggregation and disaggregation of units. Division and merging of unit resources. |
|NETN&#8209;COM| Representation of Communication Networks and the status of communication links.|
|NETN&#8209;METOC| Representation of weather conditions and primary effects of weather on terrain, on water surfaces, in the atmosphere and subsurface water conditions. |
|NETN&#8209;CBRN| Representation of CBRN release, detection, effects, and protective measures in a federated distributed simulation.|
|NETN&#8209;LOG| Negotiation, delivery, and acceptance of logistics services between federates modelling different entities involved in the service transaction. |
|NETN&#8209;TMR| Negotiated and coordinated transfer of attribute modelling responsibility between federates. |
|NETN&#8209;SE| Representation of persistent abstract geographical objects that can be (re-)used and referenced for specifying locations, paths, etc. The module also includes the representation of facilities with a function or capability to perform activities. |
|NETN&#8209;ETR| Interface for sending simulation tasks to entities represented in a federated distributed simulation.|
|NETN&#8209;ORG| Representation of the state of units including command structure and relationship between organizations. |
|NETN&#8209;AIS|Represent vessel traffic in a simulation using AIS messages.




