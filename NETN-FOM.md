The NATO Education and Training Network (NETN) Federation Object Model (FOM).

Copyright (C) 2020 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

## Introduction

The NETN FOM is an identified set of HLA Evolved FOM Modules. The NETN FOM modules are recommended for use when implementing NATO AMSP-04 NETN FAFD compliant distributed simulation. 

The modules have inter-dependencies and are designed to maximize re-use and interoperability with legacy systems using existing standards, and those having requirements for new patterns of simulation interoperability. The NETN-FOM is the complete set of NETN modules and all other modules they depend on, e.g. the SISO RPR-FOM.

### Purpose
The NETN FOM provides standard interfaces for the representation of simulated entities, events, and other models of real-world objects, processes and phenomenon. It also provides standard interfaces and patterns for simulation interplay between systems in a federated distributed simulation to allow multi-resolution modelling, transfer of modelling responsibilities, tasking and simulation control.

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
|NETN-TMR| v1.0 |NETN-BASE| Negotiated and coordinated transfer of attribute modelling responsibility between federates. |
|NETN-SE| v2.0 |NETN-BASE, RPR-SE| Representation of persistent abstact geographical objects that can be (re-)used and referenced for specifying locations, paths, etc. The module also include the representation of facilities with a function or capability to perform activities. |
|NETN-ETR|v2.0 |NETN-BASE | Interface for sending simulation tasks to entities represented in a federated distributed simulation.|
|NETN-ORG|v1.0 |NETN-BASE | Representation of the state of units including command structure and relationship between organizations. |
|NETN-AIS|v1.0 |NETN-BASE, RPR-Communication| Represent vessel traffic in a simulation using AIS messages.|

### History
In 2006, NATO Allied Command Transformation (ACT) requested NATO Modelling
and Simulation Group (NMSG) to explore the concepts of a NATO Education and Training Network capability. An exploratory team (ET-025) was created to analyze the requirement, and it proposed a technical activity to develop NETN concepts. 

In 2007, the NMSG technical activity **MSG-068 NETN** was started. The group was led by NATO Joint Warfare Center (JWC) and with participants from NATO HQ-SACT, NATO Joint Forces Training Center (JFTC), NATO Consultancy, Command and Control Agency (NC3A) and 13 Nations (Australia, Bulgaria, France, Germany, Hungary, Netherlands, Romania, Slovenia, Spain, Sweden, Turkey, UK, USA). MSG-068 assessed the distributed simulation and learning capabilities that could contribute to the development of a NETN capability and drafted standards to enable better re-use and sharing of national Modelling and Simulation systems. The capabilities were demonstrated at I/ITSEC 2010, and the group ended its work in 2011. A NETN Federation Architecture and FOM Design specification (NETN FAFD) was produced which included the **NETN-FOM v1.0** published in February 2012. 

In early 2012, the NMSG technical activity **MSG-106 SPHINX** was started as a follow-on to MSG-068 but with a slightly larger scope. The technical subgroup of MSG-106 continued to work on the NETN FAFD specification and delivered a draft NETN-FOM v2.0 which included several new FOM modules and other improvements. The updated FOM was also included in the draft Allied Modelling and Simulation Publication (AMSP-04) NATO Education and Training Network Federation Architecture and FOM Design (NETN FAFD).

In late 2014, the NMSG technical activity **MSG-134 NATO Distributed Simulation Architecture & Design, Compliance Testing and Certification** was started as a follow-on for continued maintenance of the NETN FAFD and to continue work on establishing the NATO HLA certification process identified in STANAG 4603. The group did not add any new modules to the NETN-FOM, but it assisted NMSG in updating the draft AMSP-04 to a final version including an official **NETN-FOM v2.0** release. The group ended its work in late 2017, and the AMSP-04 was later promulgated and published by NATO in March 2018 and is covered by NATO STANREC 4800.

In early 2018, the NMSG technical activity **MSG-163 Evolving NATO Standards for Federated Simulation** started as a follow-on to MSG-134. In late 2020 the group delivered a draft updated AMSP-04 Ed B NETN FAFD document including **NETN-FOM v3.0** with new modules and several updates based on NATO and national experiences using the NETN-FOM.

## Using the NETN FOM

A NETN Federations may extend the reference FOM with additional FOM Modules when appropriate. These FOM modules can be used in combination and extended to support NETN federation design. A specific federation may choose to include additional FOM modules, extend the NETN modules or select to use only a subset of the provided modules depending on the needs and requirements of the federation. 

The basic FOM Module rules, as defined in HLA, shall be applied. When extending the FOM with additional modules, the naming of classes, data-types and other identifiers must be de-conflicted.

The modular concept allows, federates, to load only those modules necessary for the federation instance. It also allows extension of other FOM modules by sub-classing or re-use of information from other modules.

Registered objects and interactions are always discovered/received at the most specific subscribed class level. Extending a FOM Module with additional subclasses provides the possibility to add extra attributes/parameters at the more specific class level. Exchange of information using this more specific level can take place between federates publishing and subscribing to this level. However, to become compatible with and receive information from federates only publishing on the more general level, the receiving federate must subscribe to both class levels. Subscribers of the more general class receive information from publishers of the more specific class level.

Example: A national extension to the NETN FOM Modules subclasses existing NETN object classes and defines additional attributes. National models aware of this extension can publish and subscribe to the more specific level defined in the national FOM module extensions. Other existing federates not aware of the extension can still discover the object and receive updates, but only on the level, they subscribe. For the national federates to discover and receive information from other federates, they need to subscribe to the NETN class level as well as the national extension level. Note that the discovered object and attribute updates are on the NETN level.

### Initialization of Simulation

### Communication Modelling

In the NETN-FOM there are a number of different modules related to modelling and simulation of communications. 

* NETN-COM and its dependency to RPR-Communication for the representation of logical networks and physical networks.
* NETN-ORG for initialization of communication nodes.
* NETN-ETR for tasking units to disrupt communication or change state of network devices.

Communication can be modelled on different levels of fidelity.

Information and data communication is simulated as messages between simulated units and systems. If there is no model to represent the actual connection status between communicating nodes, all communication is perfect and without any disruption. 
If the representation of connection status is required in the simulation, the NETN-COM module can provide a representation of `CommunicationNode` and individual `Connection` objects that can be used to determine delivery of messages based on the status of connections. This allows the simulation to model the delivery of messages based on an aggregated view of a logical `CommunicationNetwork`.

In some cases, there is a requirement to model the characteristics of physical links in the network. These physical network models can be used to generate a more high-fidelity representation of aggregated communication network. The NETN-COM module provides the means to represent physical network devices used by a `CommunicationNode`, `PhysicalNetwork` and `LinkStates`. This representation is also linked to the RPR-FOM RPR-Communication module objects for representing `RadioTranmitters` and `RadioReceivers` at a higher degree of fidelity. The status and location of transmitters is the basis for determining the `LinkStates` and these can, in turn, be used to model connections in the logical communication network.

To initialize the communication models, the NETN-ORG module uses the MSDL schema for associating communication networks with units and equipment items. The corresponding NETN-ORG FOM module object classes `Unit` and `EquipmentItem` represents the same information as attributes. This information is available to communication simulations and should be used as the basis for creating the `CommunicationNode` objects.

The NETN-COM can also be used to represent disruption effects on communication networks using `DisruptionEffect` objects. These object can be created directly by some exercise control function in the exercise or by tasking simulated units to perform some disruption task. The NETN-ETR FOM module defines the `DisruptCommunication` task that can be sent to a simulated unit in order to perform some activity leading to the creation of one or more `DisruptionEffect` object.