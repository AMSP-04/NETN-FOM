# NETN FOM naming conventions

## Class names

An object class name should be a noun, i.e. a name of a thing that persists in time.

An interaction class name should be a name that describes an event that is temporal in time.

A class name starts with a capital letter. A class name may be in mixed case with the first letter of each internal word capitalized. A class name shall not start with underscore, but underscores may be used within a class name, for example to create a prefix for a class name.

A class name should be simple and descriptive, using whole words. The use of acronyms and abbreviations should be avoided, unless the abbreviation is much more widely used than the long form, such as `URL` or `HTML`.

Examples:

- Object class names:
  - `Unit` (NETN-ORG)
  - `Path` (NETN-SE)

- Interaction class names:
  - `AisMessage` (NETN-AIS)
  - `StopAtSideOfRoad` (NETN-ETR)

## Datatype names

A datatype name follows the same convention as a class name, with the addition below.

Since the NETN FOM modules include many legacy datatypes (that will not be changed) and since the modules are built on existing datatypes from the SISO RPR-FOM, the following applies to **new** datatypes:

- A datatype name should end with the word `Type`.

- An enumeration datatype name should end with the word `EnumType`.
- Enumeration values shall be in capital letters; use of underscores in the value is allowed.
- If the underlying data representation is relevant for the datatype, then the data representation and the number of bits may be reflected in the datatype name.

By adding the word `Type` in the datatype name, an attribute or parameter name may use the same name as the datatype, without the word `Type`. This corresponds to some extent with current coding practices.

Examples of a legacy datatype name:

- `AltitudeMeterFloat64` (NETN-BASE)

Example of new datatype names:

- `MIDType` (NETN-BASE)
- `DesignatedAreaCodeType` (NETN-AIS)
- `NavigationStatusEnumType` (NETN-AIS)

## Attribute and parameter names

A class attribute or a parameter name starts with a capital letter (in contrast to common coding practices). A name may be in mixed case with the first letter of each internal word capitalized. A name shall not start with underscore, but underscores may be used within a name. A name should be short yet meaningful. The choice of a name should be mnemonic - that is, designed to indicate to the casual observer the intent of its use. One-character names should be avoided.

Common words may be abbreviated in the name. This includes currently:

- `Identifier` => `Id`

Examples:

- `UniqueId` (used in several NETN modules)
- `RulesOfEngagement` (in `SetRulesOfEngagement` task in NETN-ETR)