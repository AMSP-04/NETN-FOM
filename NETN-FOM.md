// GENERAL DOCUMENTATION FOR AMSP-04 SECTION 2 (TBD)
# NETN FEDERATION ARCHITECTURE AND DESIGN
## CONCEPTS
In the context of distributed simulation, a Federation is a union of essentially independent applications (Federate) interoperating using common infrastructure services accessed through well-defined standard interfaces and governed by common agreements on modelling responsibilities and information exchange. A High-Level Architecture (HLA) Evolved Federation is a federation using the HLA standard (IEEE 1516-2010) to specify available infrastructure services and APIs for accessing them. The HLA standard also specifies how to document information exchange using a Federation Object Model (FOM). Different domains may have different FOMs but can use the same underlying simulation infrastructure standard. A NETN Federation is a HLA Evolved Federation that follows the NETN Federation Architecture and Design described in this chapter.

Federation Architecture is the style of design and method of integration using Simulation Components and common Simulation Infrastructure to create coherent distributed Simulation Systems. A specific Federation Design is developed to meet the requirements of Simulation Solutions to support Simulation Based Events such as Computer Assisted eXercises (CAX).
 
Figure 2-1: Federation Architecture.

The purpose of having a common Federation Architecture is to harmonize design by providing design rules, design guidelines and best practices. Use of common design patterns and standards for interoperability and reuse lower the cost of development and integration.

The NETN FAFD specifies the architecture for NETN Federations and FOM modules specifically identified to support the design of NETN Federations.

## NETWORK INFRASTRUCTURE
A NETN Federation relies on the existence of a network infrastructure providing local and wide-area connectivity based on standard Internet Protocols (IP). Implementation of the network infrastructure may differ for different NETN federations based on performance and security requirements, network availability, and cost considerations. Network infrastructure services providers, such as the Combined Federated Battle-Lab Network (CFBLNet), manage the network and can provide guarantees with respect to quality of service (QoS) and network security. Conversely, an internet connection combined with technologies for encryption may provide an appropriate level of connectivity and security for some cases.

## Network Virtualization
A Virtual Private Network (VPN) is a common technology used for connecting distributed sites and systems with a peer-to-peer encrypted connection between different local area networks (LAN). The result is a virtual network where all systems share the same IP address space and can connect as if the systems were on the same LAN.

Another technology exists to create a virtual overlay network which acts on a protocol and application level. The overlay network connects only some of the systems on the LANs, e.g. the simulation infrastructure, and allows only these systems to interoperate as if they were on a LAN. An overlay network for simulation can hide the complexity of the physical networking infrastructure, simplifying the federation setup and optimizing simulation performance over WAN by providing a simulation-aware software router. In a NETN federation the types of virtual network technology used and in what combinations depends on the requirements of the federation. In a multi-site federation the use of an overlay network technology is recommended for creating persistent Virtual Simulation Networks.

### Site Identification
In NETN federations the unique identification of sites is a vital part of agreements related to the representation of simulated entities and units. A list of site identifiers (IDs) is therefore required to be completed as part of any federation agreement. The unique site identifier is also used as part of the unique identifier for simulated entities in the federation as defined in the RPR-FOM datatype "EntityIdentifier".

Site IDs should be in the range 1 – 65534.

## SIMULATION INFRASTRUCTURE
NATO STANAG 4603 mandates the use of IEEE 1516-2010 standards on High-Level Architecture (HLA Evolved) for new M&S systems. The use of HLA Evolved in NETN federations is a fundamental design rule which impacts most parts of the NETN FAFD. Any NETN federation will be supported by a Run-Time Infrastructure (RTI) implementing the HLA services. On the network the RTI acts as a distributed operating system (OS) providing a standard interface (API) to the federated systems. Internally the RTI uses distributed algorithms and network protocols to implement all HLA services. The NETN FAFD will not make any recommendations with respect to specific RTI implementations but will assume a complete and certified HLA RTI implementation will be part of any NETN federation design.

### Mixed Infrastructure 
In many NETN federations there will be a need to mix different simulation infrastructure implementations and to support other distributed simulation standards, a.k.a. multi-architecture simulation environment. The NETN FAFD allows non-HLA (e.g. DIS) or legacy HLA (e.g. HLA 1.3) federates to participate in federations using appropriate bridging and/or adaptor technologies. Any bridging required in order to integrate federates to HLA Evolved or the selected RTI shall be the responsibility of the integrating federate. In some cases multiple NETN based federations may exist and information between them exchanged using bridges.
 
Figure 2-2: A Federation with Applications Using Different Standards and APIs.

An adaptor is used to modify the way an individual system interacts with the simulation infrastructure. The adaptor can be implemented as:
a.	An integrated and configurable part of a system (e.g. a plugin "HLA" module of a simulation system).
b.	A separate component but tightly coupled through interfaces with the system (e.g. an HLA Wrapper).
c.	A part of the simulation infrastructure providing an alternate API for system integration (e.g. HLA 1.3 and HLA 1516-2000 APIs provided by an HLA Evolved RTI implementation).

A bridge (also commonly referred to as gateway) is used to integrate multiple federations or federations running different versions of HLA, DIS or other simulation architectures. The difference between an adaptor and a bridge is that the latter allows multiple systems to use the same integration component.

NETN federations use HLA Evolved as the core simulation architecture. However, in the design of a federation, requirements may motivate the use of hierarchical federations, and integration of other simulation architectures. Some of these reasons are listed below:
a.	Possibility of making code change, relinking, etc. (e.g. availability of source code to make adjustments).
b.	Use of different RTI implementations or versions (e.g. no/minimal change of already verified federations).
c.	Need to filter data (e.g. reduce load on a set of systems).
5.	Need to translate data (e.g. using different FOMs).
6.	Most adaptor and bridging solutions modify/reduce the services provided by HLA Evolved. This may have little or no impact on the overall interoperability of the system, but the fundamental design guideline of the NETN FAFD is to allow systems to integrate using as many of the HLA Evolved services and FAFD design patterns as possible. Designs with bridges and adaptors that limit the use of HLA Evolved services and FAFD design patterns should be avoided.

### Federate Compliance Verification and Certification 
Tests to verify compliance with HLA and NETN Federation design should be performed by each federate before integration. NATO nations provide HLA certification and some tools exist to test compliance with NETN design patterns. NATO MSG-134 "NATO Distributed Simulation Architecture & Design, Compliance Testing and Certification" is tasked with developing tool support for compliance testing and certification.

## NETN FOM
The NETN FOM is an identified set of HLA Evolved FOM Modules. To support NETN federation design, the NETN FOM modules are recommended for use when implementing NETN FAFD agreements in a distributed simulation. These modules include both references to standard FOMs and FOM modules as well as NETN modules developed and refined in MSG-068, MSG-085 [8] and MSG-106. The Low-Level BML FOM module was originally developed in ANNC CP-27 (Anglo Netherlands Norwegian Cooperation Programme 27) by TNO (NLD) and FFI (NOR), and is reused in MSG-106. 

The modules have inter-dependencies and have been designed to maximize re-use and interoperability with legacy systems using existing standards, and those having requirements for new patterns of simulation interoperability. The NETN FOM is the complete set of NETN modules and all other modules they depend on (e.g. RPR-FOM modules). A NETN Federation defines the modules that are relevant and each simulation system only loads those modules it requires.
 
Figure 2-3: The NETN FOM Modules.

All FOM modules are provided as HLA IEEE-1516-2010 OMT Data Interchange Format files. Textual representations of the modules are provided in Annex A – NETN FAFD FOM Modules.

The modular concept allows federates to load only those modules necessary for the federation instance. In addition, the modules can be extended with more detailed representation by creating new modules and sub-classing or using information from other modules.

NETN Federations may extend the reference FOM with additional FOM Modules when appropriate. These FOM modules can be used in combination and extended to support NETN federation design. A specific federation may choose to include additional FOM modules, extend the NETN modules and/or select to use only a subset of the provided modules depending on the needs and requirements of the federation. The basic FOM Module rules as defined in HLA Evolved shall be applied. When extending the FOM with additional modules, the naming of classes, datatypes and other identifiers must be de-conflicted.

Registered objects and interactions are always discovered/received at the most specific subscribed class level. Extending a FOM Module with additional subclasses provides the possibility to add extra attributes/parameters at the more specific class level. Exchange of information using this more specific level can take place between federates publishing and subscribing to this level. However, to become compatible with and receive information from federates only publishing on the more general level, the receiving federate must subscribe to both class levels. Subscribers of the more general class will receive information from publishers of the more specific class level.

Example: A national extension to the NETN FOM Modules subclasses existing NETN object classes and defines additional attributes. National models aware of this extension can publish and subscribe to the more specific level defined in the national FOM module extensions. Other existing federates not aware of the extension can still discover the object and receive updates but only on the level they subscribe to. In order for the national federates to discover and receive information from other federates they need to subscribe to the NETN class level as well as the national extension level. Note that the discovered object and attribute updates will be on the NETN level.

## NETN FEDERATION DESIGN

### Initialization

In a NETN federation the responsibility of modelling and simulation is allocated to participating federates. Optimally, each federate is selected to participate in the federation because it has intrinsic capabilities to represent certain aspects of entities, events and other phenomena in the simulated environment necessary to accomplish the purpose for which the federation exists. The federation design and development process allocates, describes, and documents the roles and responsibilities of all federates. The responsibility of modelling certain aspects can only be assigned to a federate with a capability that meets specified requirements. Agreements on how to define the initial and dynamic transfer of modelling responsibilities are important for all NETN federation design.

NETN federations are advised to use Military Scenario Definition Language (MSDL) [SISO-STD-007-2008] and NETN extensions of MSDL to provide federates with initial scenario settings including ORBAT. Shared folders and/or web services can be used for distribution of MSDL and/or other common data. However, a single common distribution mechanism is currently not included in the recommendations. Chapter Initialization details the NETN proposed extensions to MSDL and proposed updates of the MSDL Schema is provided in Annex B.

### Transfer of Modelling Responsibility

In advanced distributed simulation the modelling and simulation responsibilities may change during the execution of the federation. The NETN FAFD provides a recommended design pattern for dynamic transfer of modelling responsibilities (TMR), which is described in detail in chapter Transfer of Modelling Responsibility. The TMR pattern is a general purpose pattern that supports multiple federation designs to handle situations where dynamic change of modelling responsibility is required or requested. TMR works at the attribute level and can include all or a subset of attributes for a simulated entity.

TMR is recommended, amongst other things, to support the following situations:
a.	Transfer of modelling responsibility from a high fidelity federate to a low fidelity federate or vice versa.
b.	Transfer of modelling responsibility from a Live simulation to a Constructive or Virtual simulation.
c.	Transfer of modelling responsibility from a Constructive to a Virtual simulation.
d.	Transfer of modelling responsibility from a Virtual to a Constructive simulation.
e.	Transfer of modelling responsibility to a fail-over federate in case of federate loss.
f.	Load balancing by transferring modelling responsibility to a less loaded federate.
g.	Transfer of modelling responsibility to a federate located geographically closer to another federate to reduce latency between them.
h.	Aggregation/Disaggregation using the NETN FAFD MRM pattern.

### Representation of Aggregate and Physical Entities 

The NETN FAFD representation of aggregate entities such as military units and physical entities such as platforms is based on the RPR-FOM v2.0 standard. The NETN FOM Module extends the RPR-FOM with NETN-Aggregate and NETN-Physical which include additional attributes for unique identification of simulated entities. The unique identification has been included to provide better support for initialization, TMR and other advanced design patterns requiring unique pre-defined identifiers for simulated entities. NETN federations still allow pure RPR-FOM based federates in the federation but with limited ability to interoperate in some NETN design aspects. Chapter Aggregate and Physical Entity Representation describes the extensions to RPR-FOM BaseEntity object class.

It is recommended that NETN federates support NETN extensions of Aggregate and Physical Entities. For compatibility reasons NETN federates that implement NETN extensions of Aggregate and/or Physical Entities are also required to support RPR-FOM v2.0.

### Multi-Resolution Modelling 

The NETN FAFD supports multi-resolution modelling (MRM) by providing an MRM pattern for aggregation and disaggregation of simulated aggregate units and physical entities. The MRM pattern as described in chapter Multi Resolution Modelling (MRM) requires the use of NETN FAFD Transfer of Modelling Responsibilities pattern.

It is recommended that NETN federations that require models of varying levels of resolution apply the NETN FAFD MRM design pattern.

### Simulation-C2 System Interoperability 

The purpose of SIM-C2 interoperability is to automate the process of interaction between C2 systems and simulations. The NETN SIM-C2 concept as described in Chapter Simulation-C2 Interoperability is based on the Coalition Battle Management Language (C-BML) standard. A common design pattern is the use of a C-BML server to connect and exchange C-BML information between C2 systems and simulations. To interact with a NETN federation, a C-BML-HLA Gateway is used to transfer C-BML data between C-BML Server and the NETN federation. The NETN federation uses a C-BML FOM module as data exchange model within the federation. For a further break-down of the C-BML information, the NETN FAFD provides a Low-Level BML (LBML) FOM module. The LBML FOM module was originally developed in ANNC 
CP-27 (Anglo Netherlands Norwegian Cooperation Programme 27) by FFI and TNO, and is further refined in MSG-106.
 
Figure 2-4: SIM-C2 Architecture as Proposed in 13S-SIW-032.

NETN Federations in Simulation Solutions that include C2 systems are recommended to make use of the NETN FAFD SIM-C2 design to automate Simulation-C2 interaction for orders and reports. A C-BML-HLA Gateway should be procured/implemented.

NETN Federations with CGFs that require low level BML instructions are recommended to procure/implement C2 Agent Federates using the NETN LBML FOM Module and/or extensions to support specific CGF interoperability.

### Service Oriented Modelling and Simulation 

The NETN FAFD includes a design pattern for allowing a federate to provide or request modelling and simulation services to or from other federates. This is not a transfer of responsibility between federates but rather a service provided by one federate and consumed by another. The NETN Service-Consumer FOM Module is a base module that allows federates to request, provide and consume services. This design pattern is also used in the NETN Logistics FOM module for logistics related services. Chapter Service Consumer-Provider Pattern describes this pattern in detail.

NETN Federation designs requiring inter-federate service negotiation before the simulation of the delivery of a service are advised to use the NETN FAFD Service Consumer-Provider Pattern.
 
Figure 2-5: NETN Service Consumer-Provider 
Pattern Interaction Sequence Diagram.

### Logistics 

The NETN Logistics services are based on the NETN Service Consumer-Provider Pattern. The pattern is described in Chapter Logistics and implemented as extensions to the base FOM module (NETN-SCP-Base). The NETN Logistics covers the following services:
a.	Supply service is provided by a facility, a unit or entity with consumable materials supply capability. Resources are transferred from the providing unit to the consuming unit.
b.	Storage service is provided by a facility, a unit or entity with consumable materials storage capability. Resources are transferred from the consuming unit to the providing unit.
c.	Repair service can be performed on equipment (i.e. non-consumables items such as platforms) by facilities or units capable of performing requested repairs. Modelling responsibility is by default not transferred for the consuming unit (e.g. a damaged platform) to the application with modelling responsibility for the providing unit (i.e. repairing facility). Modelling responsibility can be transferred by introducing the Transfer of Modelling Responsibility (TMR) pattern.
d.	Transport service is provided by a facility, a unit or entity with transportation capability of non-consumable materials (units). Transported units are embarked, transported and disembarked. Modelling responsibility is by default not transferred for the consuming unit (transported unit) to the application with modelling responsible for the providing unit (transporter). Modelling responsibility can be transferred by introducing the Transfer of Modelling Responsibility pattern.

NETN Logistics is recommended to replace RPR-FOM v2.0 logistics modules and can be used, amongst others, in the following situations:
a.	Supply of fixed wing aircraft in airports or during aerial refuelling.
b.	Supply of helicopters in assembly areas.
c.	Repair of damaged platforms by a maintenance unit without changing the platform's location.
d.	Maintenance of damaged platforms previously deposited in a facility.
e.	Transport of units, platforms, and humans by train, ship, or aircraft.
f.	Embarkment and disembarkment of units.

### CBRN
The NETN FAFD includes a FOM Module designed to add specific support for CBRN modelling and simulation. The module is described in detail in Chapter Chemical, Biological, Radiological and Nuclear (CBRN). NETN Federations modelling CBRN events and effects are recommended to make use of the NETN FAFD CBRN design.

### Maritime Task
The German Maritime FOM (GMF) provides enhanced/extended support for modelling and simulation of Maritime Tasks. Although the NETN FAFD does not include specific design recommendations or FOM modules for modelling and simulation of maritime tasks, the Chapter NETN and GMF Compatibility provides key information regarding the use of GMF in NETN Federations.
