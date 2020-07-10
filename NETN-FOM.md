The NATO Education and Training Network (NETN) Federation Object Model (FOM).

Copyright (C) 2020 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

## Introduction

The NETN FOM is an identified set of HLA Evolved FOM Modules. The NETN FOM modules are recommended for use when implementing NATO AMSP-04 NETN FAFD compliant distributed simulation. 

The modules have inter-dependencies and are designed to maximize re-use and interoperability with legacy systems using existing standards, and those having requirements for new patterns of simulation interoperability. The NETN FOM is the complete set of NETN modules and all other modules they depend on, e.g. the SISO RPR-FOM.

### Purpose
The NETN FOM provides standard interfaces for the representation of simulated entities, events, and other models of real-world objects, processes and phenomenon. It also provides standard interfaces and patterns for simulation interplay between systems in a federated distributed simulation to allow multi-resolution modelling, transfer of modelling responsibilities, tasking and simulation control.

### Scope

<img src="./images/NETN FOM v3.0 Draft.png"/>

|Module|Dependency|Description|
|---|---|---|
|NETN-BASE| RPR-Base | The NETN-BASE FOM Module provides common definitions of datatypes and extends the RPR-BASE FOM Module.|
|NETN-Physical| RPR-Physical, NETN-BASE|The NETN-Physical FOM Module provides a standard interface for the representation of Physical Entities in a federated distributed simulation. All RPR-FOM `PhysicalEntity` object classes have been extended with additional attributes to support NETN based federation. It includes a unique identifier that provides better support for initialization, NETN-TMR and other advanced design patterns requiring unique pre-defined identifiers for simulated entities. NETN federations still allow pure RPR-FOM based federates in the federation but with limited ability to interoperate in some NETN design aspects. |
|NETN-CBRN| NETN-BASE| NETN-CBRN provides a common standard interface for the representation of CBRN release, detection, effects, and protective measures in a federated distributed simulation. E.g the exposure effect on individual humans in a CBRN contaminated Hazard area where the human is represented in one simulation and the effect is modelled in another federate simulation.|
|NETN-METOC| NETN-BASE| The purpose of the NETN METOC module is to provide a standard way to exchange data related to weather conditions and primary effects of weather on terrain, on water surfaces, in the atmosphere and subsurface water conditions. The main objective is to provide a reference model that represents a core common subset of METOC related aspects and to allow extension of the module to incorporate additional detail if required. Therefore, the NETN METOC module shall be viewed as a reference FOM module where extensions are not only allowed but encouraged to fully meet federation specific requirements. However, any extension should also be considered as candidates for improving the NETN METOC module or candidates for new standard NETN modules. |
|NETN-LOG| NETN-BASE| |
|NETN-TMR| NETN-BASE| |
|NETN-MRM| NETN-BASE | The purpose of NETN-MRM is to support federations with entities represented at multiple levels of resolution and where the level of resolution can change dynamically during a simulation. It supports patterns for aggregation and disaggregation of units, and division and merging of unit resources. |
|NETN-AIS|NETN-BASE | |
|NETN-ETR|NETN-BASE | |
|NETN-ORG|NETN-BASE | |
|NETN-SE| NETN-BASE| |
|NETN-COM| NETN-BASE| |

## Using the NETN FOM

A NETN Federations may extend the reference FOM with additional FOM Modules when appropriate. These FOM modules can be used in combination and extended to support NETN federation design. A specific federation may choose to include additional FOM modules, extend the NETN modules or select to use only a subset of the provided modules depending on the needs and requirements of the federation. 

The basic FOM Module rules, as defined in HLA, shall be applied. When extending the FOM with additional modules, the naming of classes, data-types and other identifiers must be de-conflicted.

The modular concept allows, federates, to load only those modules necessary for the federation instance. It also allows extension of other FOM modules by sub-classing or re-use of information from other modules.

Registered objects and interactions are always discovered/received at the most specific subscribed class level. Extending a FOM Module with additional subclasses provides the possibility to add extra attributes/parameters at the more specific class level. Exchange of information using this more specific level can take place between federates publishing and subscribing to this level. However, to become compatible with and receive information from federates only publishing on the more general level, the receiving federate must subscribe to both class levels. Subscribers of the more general class receive information from publishers of the more specific class level.

Example: A national extension to the NETN FOM Modules subclasses existing NETN object classes and defines additional attributes. National models aware of this extension can publish and subscribe to the more specific level defined in the national FOM module extensions. Other existing federates not aware of the extension can still discover the object and receive updates, but only on the level, they subscribe. For the national federates to discover and receive information from other federates, they need to subscribe to the NETN class level as well as the national extension level. Note that the discovered object and attribute updates are on the NETN level.

## Background
In 2006, NATO Allied Command Transformation (ACT) requested NATO Modelling
and Simulation Group (NMSG) to explore the concepts of a NATO Education and Training Network capability. An exploratory team (ET-025) was created to analyze the requirement, and it proposed a technical activity to develop NETN concepts. 

In 2007, the NMSG technical activity **MSG-068 NETN** was started. The group was led by NATO Joint Warfare Center (JWC) and with participants from NATO HQ-SACT, NATO Joint Forces Training Center (JFTC), NATO Consultancy, Command and Control Agency (NC3A) and 13 Nations (Australia, Bulgaria, France, Germany, Hungary, Netherlands, Romania, Slovenia, Spain, Sweden, Turkey, UK, USA). MSG-068 assessed the distributed simulation and learning capabilities that could contribute to the development of a NETN capability and drafted standards to enable better re-use and sharing of national Modelling and Simulation systems. The capabilities were demonstrated at I/ITSEC 2010, and the group ended its work in 2011. A NETN Federation Architecture and FOM Design specification (NETN FAFD) was produced which included the **NETN-FOM v1.0** published in February 2012. 

In early 2012, the NMSG technical activity **MSG-106 SPHINX** was started as a follow-on to MSG-068 but with a slightly larger scope. The technical subgroup of MSG-106 continued to work on the NETN FAFD specification and delivered a draft NETN-FOM v2.0 which included several new FOM modules and other improvements. The updated FOM was also included in the draft Allied Modelling and Simulation Publication (AMSP-04) NATO Education and Training Network Federation Architecture and FOM Design (NETN FAFD).

In late 2014, the NMSG technical activity **MSG-134 NATO Distributed Simulation Architecture & Design, Compliance Testing and Certification** was started as a follow-on for continued maintenance of the NETN FAFD and to continue work on establishing the NATO HLA certification process identified in STANAG 4603. The group did not add any new modules to the NETN-FOM, but it assisted NMSG in updating the draft AMSP-04 to a final version including an official **NETN-FOM v2.0** release. The group ended its work in late 2017, and the AMSP-04 was later promulgated and published by NATO in March 2018 and is covered by NATO STANREC 4800.

In early 2018, the NMSG technical activity **MSG-163 Evolving NATO Standards for Federated Simulation** started as a follow-on to MSG-134. In late 2020 the group delivered a draft updated AMSP-04 Ed B NETN FAFD document including **NETN-FOM v3.0** with new modules and several updates based on NATO and national experiences using the NETN-FOM.