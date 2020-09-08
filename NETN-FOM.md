The NATO Education and Training Network (NETN) Federation Object Model (FOM).

Copyright (C) 2020 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

## Acknowledgements

The following individuals have, in some way, participated in the development of this standard or its earlier versions.

Adam Brook, Allan Gillis, Amy Grom, André Geiger, Andrew Poulter, Andy Bowers, Angel San Jose Martin, Antony Hubervic, Anthony Jones, Bharat Patel, Birol Güvenç, Björn Löfstrand, Brian Gregg, Brian Horn, Cem Kumsal, Ceri Pritchard, Christopher Struselis, Christian Mårtensson, Clive Wood, Craig Pepper, Darren McFarlane, David Desert, Dieter Steinkamp, Duncan E Rogers, Elena Bravo, Elisseos Mavratzotis, Ercan Atalay, Erdal Cayirci, Erich Schmid, Erik Solum, Frank Bertling, Franz Schubert, Fredrik Jonsson, Gareth M. Pugh, Gokay Sursal, Gunnar Öhlund, Gustav Schulz, Göran Bergström, Hannu Outila, Hans Jense, Heliodoro Ruiperez, Henk Hendersen, Herbert Tietje, Horst Behner, Ionel Vlasie, Jacek Sumislawski, Jack Bramhill, James Boulet, Jan Hodicky, Jan van Geest, Jean-Pierre Faye, Jens Kåregren, Jeppe Nyløkke, Jerome Martinet, Jochen Siebeneicher, Johannes Mulder, John Loughhead, Jose Mimbrero, Jose Ruiz, Juan José Ruiz Pérez, Karl-Heinz Neumann, Kjell Magne Fauske, Klaus Greiwe, Konradin Keller, Lars Jansson, Lars Lindberg, Laurent Lesage, Leif Almgren, Lennart Olsson, Lesley Jacobs, Linus Lindholm, Lubomir Chylik, Malcolm Pigott, Magnus Karperyd, Manuel Dogaru, Marco Picollo, Mark Shelford, Martin Adelantado, Martin Eklöf, Martin Jones, Michael Jobson, Michael Mifsud, Miles Patterson, Mimi Nguyen, Morten Ottesen, Nathan Newton, Neil Morris, Neil Smith, Nico de Reus, Nicolas Pitrat, Nils Smedberg, Ola Wall, Oliver Henne, Orlin Nikolov, Osmo Forsten, Patrice Guillou, Patricio Jimenez, Per-Philip Sollin, Petar Savkov Petrov, Peter Lindskog, Peter Meyer zu Drewer, Peter Jackson, Rachid El Abdouni Khayari, Raniero Castrogiovanni, Regis Mauget, Reinhard Herzog, Robert B. Kean, Robert Paledau, Robert Wittman, Roberto Censori, Roger Jansen, Rolf Engsvang, Ron Caprio, Russell Mills, Sam Hall, Sergio Galán, Simon Morris, Stefan Vrieler, Stephane Devaud, Stephen Ballard, Steven Blackstone, Stuart Robin, Søren Larsen, Thomas Orichel, Tobias Kuhn, Tom van den Berg, Torbjörn Hultén, Ulf Björkman, Ulf Jinnestrand, Vladimir Manda, Wim Huiskamp, Xavier Coste, Xavier Cuneo, Yuri Fedulov.

## Executive Summary

Efficient and effective use of NATO and national Modelling & Simulation (M&S) capabilities, to support training, requires standards for connecting and integrating M&S components across the training system enterprise.

The NATO Education and Training Network Federation Architecture and FOM Federation Object Model Design (NETN FAFD) document including the NETN-FOM provide architecture and design guidance for developing distributed simulation and training systems, including support for Computer Assisted Exercises (CAX). The standard applies to NATO CAX, national CAX and distributed modelling and simulation in general.

The NETN-FOM focuses on technical interoperability issues in distributed simulation and provides architecture and design patterns and proposed solutions. However, it is not a complete guide on how to design a distributed simulation system. It includes architecture and design guidelines on network infrastructure, simulation infrastructure, simulation data exchange models and how to create a robust, scalable, interoperable and high performing federation of distributed simulation to support CAX. 


## Introduction

### Purpose

The NATO Education and Training Network Federation Architecture and FOM Federation Object Model Design (NETN FAFD) document provide architecture and design guidance for developing distributed simulation and training systems, including support for Computer Assisted Exercises (CAX). The guidance has been developed to support the NETN vision and applies to NATO CAX, national CAX and distributed modelling and simulation in general.

> “To deliver to NATO and Partners a persistent, distributed combined joint training capability able to support training from the operational to the tactical level across the full spectrum of operations, through leveraging existing national expertise and capabilities.” - NATO ACT NETN Vision

The NETN FAFD focuses mainly on technical interoperability issues in distributed simulation. It is not a complete guide on how to design a distributed simulation to support CAX but provide key architecture and design patterns and proposed solutions.

As a reference document, the NETN FAFD does not replace design and agreements documents authored to support each particular instance of federation development and use.

The NETN-FOM is an identified set of HLA Evolved FOM Modules. The NETN FOM modules are recommended for use when implementing NATO AMSP-04 NETN FAFD compliant distributed simulation. 

The modules have inter-dependencies, and their design maximizes re-use of- and interoperability with legacy systems. The NETN-FOM is the complete set of NETN modules and all other modules on which they depend.

The NETN-FOM provides standard interfaces for the representation of simulated entities, events, and other models of real-world objects, processes and phenomenon. It also provides standard interfaces and patterns for simulation interplay between systems in a federated distributed simulation to allow multi-resolution modelling, transfer of modelling responsibilities, tasking and simulation control.

### Scope

<img src="./images/NETN FOM v3.0 Draft.png"/>

|Module|Version|Dependency|Description|
|---|---|---|---|
|NETN-BASE| v2.0 |RPR-Base | Common definitions of datatypes and extends the RPR-BASE FOM Module.|
|NETN-Physical| v2.0 |NETN-BASE, RPR-Physical|Representation of Physical Entities in a federated distributed simulation. |
|NETN-MRM| v2.0 |NETN-BASE, RPR-Aggregate | Aggregate level entity simulation, aggregation and disaggregation of units. Division and merging of unit resources. |
|NETN-COM| v1.0 |NETN-BASE, RPR-Communication| Representation of Communication Networks and the status of communication links.|
|NETN-METOC| v1.0 |NETN-BASE| Representation of weather conditions and primary effects of weather on terrain, on water surfaces, in the atmosphere and subsurface water conditions. |
|NETN-CBRN| v1.2 |NETN-Physical| Representation of CBRN release, detection, effects, and protective measures in a federated distributed simulation.|
|NETN-LOG| v2.0 |NETN-BASE| Negotiation, delivery, and acceptance of logistics services between federates modelling different entities involved in the service transaction. |
|NETN-TMR| v2.0 |NETN-BASE| Negotiated and coordinated transfer of attribute modelling responsibility between federates. |
|NETN-SE| v2.0 |NETN-BASE, RPR-SE| Representation of persistent abstract geographical objects that can be (re-)used and referenced for specifying locations, paths, etc. The module also includes the representation of facilities with a function or capability to perform activities. |
|NETN-ETR|v2.0 |NETN-BASE | Interface for sending simulation tasks to entities represented in a federated distributed simulation.|
|NETN-ORG|v1.0 |NETN-BASE | Representation of the state of units including command structure and relationship between organizations. |
|NETN-AIS|v1.0 |NETN-BASE, NETN-ETR, NETN-ORG RPR-Communication| Represent vessel traffic in a simulation using AIS messages.|

### History
In 2006, NATO Allied Command Transformation (ACT) requested NATO Modelling and Simulation Group (NMSG) to explore the concepts of a NATO Education and Training Network capability. An exploratory team (ET-025) analyzed the requirement, and it proposed a technical activity to develop NETN concepts. 

In 2007, the NMSG technical activity **MSG-068 NETN** started led by NATO Joint Warfare Center (JWC) and with participants from NATO HQ-SACT, NATO Joint Forces Training Center (JFTC), NATO Consultancy, Command and Control Agency (NC3A) and 13 Nations (Australia, Bulgaria, France, Germany, Hungary, Netherlands, Romania, Slovenia, Spain, Sweden, Turkey, UK, USA). MSG-068 assessed the distributed simulation and learning capabilities that could contribute to the development of a NETN capability and drafted standards to enable better re-use and sharing of national Modelling and Simulation systems. The capabilities were demonstrated at I/ITSEC 2010, and the group ended its work in 2011. A NETN Federation Architecture and FOM Design specification (NETN FAFD) was produced which included the **NETN-FOM v1.0** published in February 2012. 

In early 2012, the NMSG technical activity **MSG-106 SPHINX**  started as a follow-on to MSG-068 but with a slightly broader scope. The technical subgroup of MSG-106 continued to work on the NETN FAFD specification and delivered a draft NETN-FOM v2.0 which included several new FOM modules and other improvements. The updated NETN-FOM was included in the draft Allied Modelling and Simulation Publication (AMSP-04) NATO Education and Training Network Federation Architecture and FOM Design (NETN FAFD).

In late 2014, the NMSG technical activity **MSG-134 NATO Distributed Simulation Architecture & Design, Compliance Testing and Certification** started as a follow-on to MSG-106 to continue maintenance of the NETN FAFD and to work on establishing the NATO HLA certification process as identified in NATO STANAG 4603. The group did not add any new modules to the NETN-FOM, but it assisted in updating the draft AMSP-04 to a final version including an official **NETN-FOM v2.0** release. The group ended its work in late 2017, and the AMSP-04 was later promulgated and published by NATO in March 2018 and is covered by NATO STANREC 4800.

In early 2018, the NMSG technical activity **MSG-163 Evolving NATO Standards for Federated Simulation** started as a follow-on to MSG-134. In late 2020 the group delivered a draft updated AMSP-04 Ed B NETN FAFD document including **NETN-FOM v3.0** with new modules and several updates based on NATO and national experiences using the NETN-FOM.

### Summary of changes

* Changes in v 3.0
  * New FOM Module NETN-ORG for the representation of Organizations
  * New FOM Module NETN-SE to extend RPR-SE
  *	New FOM Module NETN-METOC for the representation of Weather
  * New FOM Module NETN-AIS for the representation of Vessel Traffic Information and Data
  * New FOM Module NETN-LOG that Merge and remove Logistics FOM Modules NETN-SCP-Base, NETN-Repair, NETN-Transport, NETN-Supply, and NETN-Storage
  * Renamed LBML module to NETN-ETR (Entity Tasking and Reporting)
  * Major update of NETN-MRM to simplify aggregation, disaggregation, divide and merge of units.
  * Exclude FOM Module NETN-HCBML for high-level C-BML Sim-C2 interactions (in anticipation of SISO C2SIM standard).
* Changes in v 2.0
  * New FOM Module NETN-Base for standard datatypes
  * New FOM Module NETN-Physical extends RPR-Physical
  * New FOM Module NETN-CBRN for the representation of CBRN events and effects
  * New FOM Module NETN-MRM for aggregation and disaggregation of units
  * New FOM Module NETN-TMR for transfer of modelling responsibilities
  * New FOM Module NETN-HCBML for high-level C-BML Sim-C2 interactions
  * New FOM Module NETN-LLBML for low-level entity tasking and reporting
  * Renamed NETN Service Consumer-Provider FOM Module to NETN-SCP-Base
  * Replaced NETN Logistics FOM Module with NETN-Repair, NETN-Storage, NETN-Supply and NETN-Transport
* Original modules in v1.0
  * NETN Service Consumer-Provider FOM Module v1.0
  * NETN Logistics FOM Module v1.0
  * NETN Aggregate FOM Module v1.0

### References

While this document is sufficiently complete to be stand-alone, it cannot fully explain all the concepts and foundational work accomplished by the many individuals and organizations whose efforts preceded ours. Please refer to the documents referenced below for more details. In the case of differences between this document and the references, this document is primary as changes have the intent to support evolving NETN requirements.

* NATO STANAG 4603.
* IEEE 1516-2010 - IEEE Standard for Modeling and Simulation (M&S) High Level Architecture (HLA)-- Framework and Rules
* IEEE 1516.1-2010 - IEEE Standard for Modeling and Simulation (M&S) High Level Architecture (HLA)-- Federate Interface Specification
* IEEE 1516.2-2010 - IEEE Standard for Modeling and Simulation (M&S) High Level Architecture (HLA)-- Object Model Template (OMT) Specification
* SISO-REF-010 Reference for Enumerations for Simulation Interoperability.
* SISO-STD-007-2008: Military Scenario Definition Language (MSDL).
* IEEE 1278.1-2012 - IEEE Standard for Distributed Interactive Simulation--Application Protocols
* SISO-STD-001-2015: Standard for Guidance, Rationale, and Interoperability Modalities (GRIM) for the Real-time Platform Reference Federation Object Model (RPR FOM), Version 2.0 (10 Aug 2015).
* SISO-STD-001.1-2015: Standard for Real-time Platform Reference Federation Object Model (RPR FOM), Version 2.0 (10 Aug 2015).


## NETN Federation Architecture and Design

### Federation Concepts

In the context of distributed simulation, a Federation is a union of independent applications (Federate) interoperating using standard infrastructure services accessed through well-defined standard interfaces and governed by common agreements on modelling responsibilities and information exchange. A High-Level Architecture (HLA) Evolved Federation is a federation using the HLA standard (IEEE 1516-2010) to specify available infrastructure services and APIs for accessing them. The HLA standard also specifies how to document information exchange using a Federation Object Model (FOM). Different domains may have different FOMs but can use the same underlying simulation infrastructure standard. A NETN Federation is an HLA Evolved Federation that follows the NETN Federation Architecture and Design described in this chapter.

Federation Architecture is the style of design and method of integration using Simulation Components and common Simulation Infrastructure to create coherent distributed Simulation Systems. A specific Federation Design meets the requirements of Simulation Solutions to support Simulation-Based Events such as Computer Assisted eXercises (CAX).

The purpose of having a standard Federation Architecture is to harmonize design by providing design rules, design guidelines and best practices. Use of common design patterns and standards for interoperability and reuse, lower the cost of development and integration.

The NETN FAFD specifies the architecture for NETN Federations and FOM modules specifically identified to support the design of NETN Federations.

### Network Infrastructure

A NETN Federation relies on the existence of a network infrastructure providing local and wide-area connectivity based on standard Internet Protocols (IP). Implementation of the network infrastructure may differ for different NETN federations based on performance and security requirements, network availability, and cost considerations. Network infrastructure services providers, such as the Combined Federated Battle-Lab Network (CFBLNet), manage the network and can provide guarantees for the quality of service (QoS) and network security. Conversely, an internet connection combined with technologies for encryption may provide an appropriate level of connectivity and security for some cases.

### Simulation Infrastructure

NATO STANAG 4603 mandates the use of IEEE 1516-2010 standards on High-Level Architecture (HLA Evolved) for new M&S systems. The use of HLA in NETN federations is a fundamental design rule which impacts most parts of the NETN FAFD. A NETN federation includes a Run-Time Infrastructure (RTI) implementing the HLA services. On the network, the RTI acts as a distributed operating system, providing a standard interface (API) to the federated systems. Internally the RTI uses distributed algorithms and network protocols to implement all HLA services. The NETN FAFD makes no recommendations concerning specific RTI implementations but requires complete and certified HLA RTI implementation.

In many NETN federations, there is a need to mix different simulation infrastructure implementations and to support other distributed simulation standards, a.k.a. a multi-architecture simulation environment. The NETN FAFD allows non-HLA (e.g. DIS) or legacy HLA (e.g. HLA 1.3) federates to participate in federations using appropriate bridging or adaptor technologies. Any bridging required to integrate federates to HLA, or the selected RTI shall be the responsibility of the integrating federate. In some cases, multiple NETN based federations may exist, and information between them exchanged using bridges.

NETN federations use HLA Evolved as the core simulation architecture. However, in the design of a federation, requirements may motivate the use of hierarchical federations and integration of other simulation architectures. Some of these reasons are listed below:

* Possibility of making a code change, e.g. availability of source code to make adjustments.
* Use of different RTI implementations or versions, e.g. no/minimal change of already verified federations.
* Need to filter data, e.g. reduce the load on a set of systems.
* Need to translate data, e.g. using different FOMs.

Most adaptor and bridging solutions modify or reduce the services provided by HLA Evolved. These solutions may have little or no impact on the overall interoperability of the system. However, the fundamental design guideline of the NETN FAFD is to allow systems to integrate using as many of the HLA Evolved services and FAFD design patterns as possible.

Tests to verify compliance with HLA and NETN Federation design should be performed by each federate before integration. NATO provide HLA certification and tools exist to test compliance with HLA and some NETN design patterns. 


## Federation Design

A NETN Federation may extend the reference FOM with additional FOM Modules when appropriate. These FOM modules can be used in combination and to extend NETN federation design. A specific federation may choose to include additional FOM modules, extend the NETN modules or select to use only a subset of the provided modules depending on the needs and requirements of the federation. 

The basic FOM Module rules, as defined in HLA, shall be applied. When extending the FOM with additional modules, the naming of classes, datatypes and other unique identifiers must be de-conflicted.

The modular concept allows, federates, to load only those modules necessary for the federation instance. It also allows the extension of other FOM modules by sub-classing or re-use of information from other modules.

Registered objects and interactions are always discovered/received at the most specific subscribed class level. Extending a FOM Module with additional subclasses provides the possibility to add extra attributes/parameters at the more specific class level. Exchange of information using this more specific level can take place between federates publishing and subscribing to this level. However, to become compatible with and receive information from federates only publishing on the more general level, the receiving federate must subscribe to both class levels. Subscribers of the more general class receive information from publishers of the more specific class level.

Example: A national extension to the NETN FOM Modules subclasses existing NETN object classes and defines additional attributes. National models aware of this extension can publish and subscribe to the more specific level specified in the national FOM module extensions. Other existing federates not aware of the extension can still discover the object and receive updates, but only on the level, they subscribe. For the national federates to discover and receive information from other federates, they need to subscribe to the NETN class level as well as the national extension level. Note that the discovered object and attribute updates are on the NETN level.

### Initialization

In a NETN federation, the responsibility of modelling and simulation is allocated to participating federates. Optimally, each federate is selected to participate in the federation because it has intrinsic capabilities to represent certain aspects of entities, events and other phenomena in the simulated environment necessary to accomplish the purpose for which the federation exists. The federation design and development process allocate, describes, and documents the roles and responsibilities of all federates. The responsibility of modelling certain aspects can only be assigned to a federate with a capability that meets specified requirements. Agreements on how to define the initial and dynamic transfer of modelling responsibilities are important for all NETN federation design.

The NETN-FOM allows the initialization of a distributed simulation using a scenario data format defined in the NETN-ORG module. The NETN-ORG XML Schema defines a format that extends the SISO-STD-007-2008 Military Scenario Definition Language (MSDL), and valid MSDL files are also valid using the NETN-ORG schema. The original MSDL schema is extended with additional elements for the initial allocation of modelling responsibilities. 

The scenario information can be loaded directly by simulation applications, or a dedicated federate application publishes the NETN-ORG scenario data in the federation as HLA objects. The NETN-ORG FOM module defines the `Unit`, `EquipmentItem`, and `Installation` object classes that can be used in the federation to publish scenario data.

Example federation designs include:

* A single federate in the federation reads one or more scenario data files, publishes all the data, and potentially updating/deleting data during execution;
* Multiple federates in the federation reads one scenario data file each and publish all data included in the respective file. Preparation of scenario files must ensure that they are disjunct and do not contain overlapping information.
* Allocation of modelling responsibilities based on FederateName in the scenario file can be interpreted differently depending on federation agreements. 

### Communication Modelling

In the NETN-FOM, there are several different modules related to modelling and simulation of communications. 

* NETN-COM and its dependency to RPR-Communication for the representation of logical networks and physical networks.
* NETN-ORG for initialization of communication nodes.
* NETN-ETR for tasking units to disrupt communication or change state of network devices.

Communication can be modelled using different levels of fidelity.

Information and data communication is modelled as messages between simulated units and systems. If there is no representation of the actual connection status between communicating nodes, then all communication is perfect and without any disruption. 

If a representation of connection status is required in the simulation, the NETN-COM module can be used. It provides a representation of `CommunicationNode` and individual `Connection` objects used to determine the delivery of messages based on the status of connections. This approach allows the simulation to model the delivery of messages based on an aggregated view of a logical `CommunicationNetwork`.

In some cases, there is a requirement to model the characteristics of physical links in the network. These physical network models can be used to generate a more high-fidelity representation of aggregated communication network. The NETN-COM module provides the means to represent physical network devices used by a `CommunicationNode`, `PhysicalNetwork` and `LinkStates`. This representation is linked to the RPR-FOM RPR-Communication module objects for representing `RadioTranmitters` and `RadioReceivers` at a higher degree of fidelity. The status and location of transmitters is the basis for determining the `LinkStates`, and these can be used to model connections in the logical communication network.

The NETN-ORG module uses the MSDL schema for associating communication networks with units and equipment items. The corresponding NETN-ORG FOM module object classes `Unit` and `EquipmentItem` represents the equivalent information as attributes. This information is available to communication simulations and should be the basis for creating the `CommunicationNode` objects.

The NETN-COM can also be used to represent disruption effects on communication networks using `DisruptionEffect` objects. These objects can be created directly by some exercise control function in the exercise or by tasking simulated units to perform some disruption task. The NETN-ETR FOM module defines the `DisruptCommunication` task that can be sent to a simulated unit to perform some activity leading to the creation of one or more `DisruptionEffect` object.

### Transfer of Modelling Responsibility

In an advanced distributed simulation, the modelling and simulation responsibilities may change during the execution of the federation. The NETN FAFD provides a recommended design pattern for dynamic transfer of modelling responsibilities (TMR). The NETN-TMR FOM module defines a general-purpose pattern that supports multiple federation designs to handle situations where the dynamic change of modelling responsibility is required or requested. NETN-TMR works at the attribute level and can include all or a subset of attributes for a simulated entity.

NETN-TMR is recommended to support the following situations:
* Transfer of modelling responsibility from a high fidelity federate to a low fidelity federate or vice versa.
* Transfer of modelling responsibility from a Live simulation to a Constructive or Virtual simulation.
* Transfer of modelling responsibility from a Constructive to a Virtual simulation.
* Transfer of modelling responsibility from a Virtual to a Constructive simulation.
* Transfer of modelling responsibility to a fail-over federate in case of federate loss.
* Load balancing by transferring modelling responsibility to a less loaded federate.
* Transfer of modelling responsibility to a federate located geographically closer to another federate to reduce latency between them.

### Multi-Resolution Modelling 

Models of real-world objects, processes and phenomena are used to create a synthetic representation suitable for simulation. Depending on the purpose and requirements of the simulation, the models can have different levels of resolution and aggregation can be used to create representations of broader combined concepts. 

The NATO Education and Training Network Multi-Resolution Modelling (NETN-MRM) FOM Module is a specification of how to perform aggregation and disaggregation of aggregated representation of entities, e.g. units, into other levels of aggregation or individual entities, e.g. platforms, in a federated distributed simulation. 

The purpose of NETN-MRM is to support federations with entities represented at multiple levels of resolution and where the level of resolution can change dynamically during a simulation. It supports patterns for aggregation and disaggregation of units and division and merging of unit resources. The module provides a common standard interface for the aggregated representation of equipment, personnel and supplies in a federated distributed simulation. The aggregated representation can be used to model the state of organisations, such as military units, without the need to represent each resource as individual simulated entities. The module extends the existing RPR-FOM v2.0 `AggregateEntity` object class with attributes and can use the NETN-ORG representation of unit relationships to support aggregation, disaggregation of corresponding ground-truth representation.
