## AMSP-04 NATO Education and Training Network Federation Architecture and Federation Object Model Design (NETN FAFD)
## Edition A Version 1.0
## March 2018

# Executive Summary
The NATO Education and Training Network (NETN) Federation Architecture and FOM (Federation Object Model) Design (FAFD) document is a reference document intended to provide architecture and design guidance for developing distributed simulation and training systems in the context of Computer Assisted Exercises (CAX). The guidance provided by the FAFD has been developed to support the NETN vision and is applicable to NATO CAX, national CAX and to some extent to distributed modelling and simulation in general.
The FAFD focuses mainly on technical interoperability issues in distributed simulation. It is not a complete guide on how to design a distributed simulation to support CAX but will provide key architecture and design patterns and proposed solutions. The FAFD provides architecture and design guidelines on network infrastructure, simulation infrastructure, simulation data exchange models (SDEM) and how to design a robust, scalable, interoperable and high performing federation of distributed simulation to support CAX. The document also addresses domain specific requirements of modelling aspects of units, platforms, activities and other events. Areas specifically included in this version of the NETN FAFD are CBRN, Logistics, and NETN compatibility with RPR-FOM and German Maritime FOM (GMF).

Key recommendations include:
* Use of NATO STANAG 4603 (High Level Architecture);
* Use of NATO NETN FOM and associated standard and NATO NETN developed FOM Modules;
* Use of RPR-FOM v2.0 (Modularized) and German Maritime FOM (GMF);
* Use of Transfer of Modelling Responsibilities Design Pattern;
* Use of MSDL to support Initialization;
* Use of C-BML to support Simulation-to-C2 interoperability; and
* Use of Multi-Resolution Modelling.

# Introduction
## Purpose
1.1. PURPOSE
The NATO Education and Training Network (NETN) Federation Architecture and FOM Design (FAFD) document is a reference document intended to provide architecture and design guidance for developing distributed simulation and training systems in the context of Computer Assisted Exercises (CAX). The guidance provided by the FAFD has been developed to support the NETN vision and is applicable to NATO CAX, national CAX and to distributed modelling and simulation in general.

> “To deliver to NATO and Partners a persistent, distributed combined joint training capability able to support training from the operational to the tactical level across the full spectrum of operations, through leveraging existing national expertise and capabilities.” - NATO ACT NETN Vision

The FAFD focuses mainly on technical interoperability issues in distributed simulation. It is not a complete guide on how to design a distributed simulation to support CAX but will provide key architecture and design patterns and proposed solutions.

As a reference document, the FAFD is not intended to replace design and agreements documents authored to support each particular instance of federation development and use.

## Background
The first version of the FAFD was developed by NATO Modelling and Simulation Group MSG-068. This task group was created to support the ACT Snow Leopard Program, establishing a NATO-wide network for education and training (NETN).

A technical subgroup of MSG-068, Federation Architecture and FOM Design (FAFD), was created with representatives from the participating NATO and partner nations. This group represented a broad community of practice with respect to federation architecture and design. Major systems, federations and training networks were represented in the FAFD group. The input provided and the harmonization of federation architecture and design agreements formed the first version of this document.

The second version of these federation agreements were developed by a second NMSG task group, namely the MSG-106 "Enhanced CAX architecture, design and methodology - SPHINX" technical (TEK) subgroup. This group modified the original agreements based on practical experiences in using the NETN recommendations in major exercises and experiments and included clarifications,recommendations and agreements resulting from work accomplished during the tenure of MSG-106.

## Summary of changes
* Modularization of RPR-FOM.
* New NETN Base FOM Module.
* New NETN Physical FOM Module.
* New NETN Aggregate FOM Module.
* New NETN Logistics FOM Modules.
* New MRM FOM Module.
* New C-BML FOM Module.
* New CBRN FOM Module.
* New TMR FOM Module.