# NETN FOM
NATO Education and Training Network (NETN) Federation Object Model (FOM)

## Acknowledgement
The following individuals have, in some way, participated in the development of this standard or its earlier versions.

Adam Brook, Adrian Voiculet, Alexander Jung, Allan Gillis, Amy Grom, André Geiger, Andrew Poulter, Andy Bowers, Angel San Jose Martin, Antony Hubervic, Anthony Jones, Bharat Patel, Birol Güvenç, Björn Löfstrand, Brian Gregg, Brian Horn, Cem Kumsal, Ceri Pritchard, Christopher Struselis, Christian Mårtensson, Clive Wood, Craig Pepper, Darren McFarlane, David Culley, David Desert, Dieter Steinkamp, Duncan E Rogers, Elena Bravo, Elisseos Mavratzotis, Ercan Atalay, Erdal Cayirci, Erich Schmid, Erik Solum, Frank Bertling, Franz Schubert, Fredrik Jonsson, Gareth M. Pugh, Gilberto Burgio, Gokay Sursal, Gunnar Öhlund, Gustav Schulz, Göran Bergström, Hannu Outila, Hans Jense, Heliodoro Ruiperez, Henk Hendersen, Herbert Tietje, Horst Behner, Ionel Vlasie, Jacek Sumislawski, Jack Bramhill, James Boulet, Jan Hodicky, Jan van Geest, Jean-Pierre Faye, Jens Kåregren, Jeppe Nyløkke, Jerome Martinet, Jochen Siebeneicher, Johannes Mulder, John Loughhead, Jose Mimbrero, Jose Ruiz, Juan José Ruiz Pérez, Karl-Heinz Neumann, Kjell Magne Fauske, Klaus Greiwe, Konradin Keller, Kwok Wong, Lars Jansson, Lars Lindberg, Laurent Lesage, Leif Almgren, Lena Beier, Lennart Olsson, Leon Golob, Lesley Jacobs, Linus Lindholm, Lubomir Chylik, Malcolm Pigott, Magnus Karperyd, Manuel Dogaru, Marco Picollo, Mark Shelford, Martin Adelantado, Martin Eklöf, Martin Jones, Massimo Baleani, Michael Jobson, Michael Mifsud, Miles Patterson, Mimi Nguyen, Morten Ottesen, Nathan Newton, Neil Morris, Neil Smith, Nico de Reus, Nicolas Pitrat, Nigel Jones, Nils Smedberg, Ola Wall, Oliver Henne, Orlin Nikolov, Oscar Bergman, Özlem Yavanoglu, Osmo Forsten, Panagiotis Balaskas, Patrice Guillou, Patricio Jimenez, Per-Philip Sollin, Petar Savkov Petrov, Peter Lindskog, Peter Meyer zu Drewer, Peter Jackson, Rachid El Abdouni Khayari, Radovan Sernec, Raniero Castrogiovanni, Regis Mauget, Reinhard Herzog, Robert B. Kean, Robert Paledau, Robert Wittman, Roberto Censori, Roger Jansen, Rolf Engsvang, Ron Caprio, Russell Mills, Sam Hall, Sergio Galán, Simon Morris, Stefan Vrieler, Stephane Devaud, Stephen Ballard, Steven Blackstone, Stuart Robin, Søren Larsen, Thomas Orichel, Tobias Kuhn, Tom van den Berg, Torbjörn Hultén, Ulf Björkman, Ulf Jinnestrand, Uwe Gaertner, Vincenzo Brucato, Vito Čuček, Vladimir Manda, Wim Huiskamp, Xavier Coste, Xavier Cuneo, Yuri Fedulov, Zeynep Cakir.
 
## Executive Summary

Efficient and effective use of NATO and national Modelling & Simulation (M&S) capabilities, to support training, requires standards for connecting and integrating M&S components across the training system enterprise.

The NATO Education and Training Network Federation Object Model (NETN-FOM) document provides architecture and design guidance for developing distributed simulation and training systems, including support for Computer Assisted Exercises (CAX). The standard applies to NATO CAX, national CAX and distributed modelling and simulation in general.

The NETN-FOM focuses on technical interoperability issues in distributed simulation and provides architecture and design patterns and proposed solutions. However, it is not a complete guide on how to design a distributed simulation system. It includes architecture and design guidelines on network infrastructure, simulation infrastructure, simulation data exchange models and how to create a robust, scalable, interoperable and high performing federation of distributed simulation to support CAX. 

Full on-line documentation and all related data models and files are provided through http://www.github.org/AMSP-04


## Licence

Copyright (C) 2020 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md). 

The work includes all the NETN FOM Modules and related [documentation](NETN-FOM.md).

Above licence gives you the right to use and redistribute the NETN FOM (XML files and Documentation) in its entirety without modification. You are also allowed to develop new FOM Modules (in separate XML files and separate documentation) that build-on/extends the NETN FOM by reference and including necessary scaffolding classes. You are NOT allowed to modify the NETN FOM or its documentation without prior permission by the NATO Modelling and Simulation Group. 

## Versions, updates and extensions

All updates and versioning of this work is coordinated by the NATO Modelling and Simulation Coordination Office (MSCO), managed by the NATO Modelling and Simulation Group (NMSG) and performed as NATO Science and Technology Organization (STO) technical activities in support of the NMSG Modelling and Simulation Standards Subgroup (MS3).

Feedback on the use of this work, suggestions for improvements and identified issues are welcome and can be provided using GitHub issue tracking. To engage in the development and update of NETN FOM, please contact your national NMSG representative.

Version numbering of the NETN FOM and associated documentation is based on the following principles:

* New official version number is assigned and in effect only when a new release is made in the Master branch.
* Updates in the Develop branch will not change the version number.
* Update of the major version number is made if the change constitutes a major restructuring, merging, addition or redefinition of semantics that breaks backward compatibility or cover entirely new concepts.
* Update of the minor version number is made if the change constitutes minor additions to existing concepts and editorial changes that do not break backward compatibility but may require updates of software to use new concepts.
* Patches are released to fix minor issues that do not break backward compatibility.

|Version|Description|
|---|---|
|v1.0|Initial release of NETN FOM as developed by MSG-068 |
|v2.0|Release of NETN FOM included in AMSP-04 Ed A|
|v3.0|Release of NETN FOM included in AMSP-04 Ed B|

[Changelog](changelog.md)

## Maintenance on GitHub
* The master branch of each NETN FOM Module repository contains the official public releases of the module.
* The develop branch of each NETN FOM Module repository contains the intermediate baseline releases of the module and the lasest build/merge of other feature branches/forks used by members of the maintenance team to update the module.

[Work Flow](flow.md)

[Naming Conventions](NamingConventions.md)

## Documentation

[Full Documentation](NETN-FOM.md)

