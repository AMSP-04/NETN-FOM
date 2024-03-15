# NETN FOM naming conventions

## Class names

An object class name should be a noun, i.e. a name of a thing that persists in time.

An interaction class name should be a name that describes an event that is temporal in time.

A class name starts with a capital letter. A class name may be in mixed case with the first letter of each internal word capitalized. A class name shall not start with an underscore, but underscores may be used within a class name, for example to create a prefix for a class name.

A class name should be simple and descriptive, using whole words. The use of acronyms and abbreviations should be avoided, unless the abbreviation is much more widely used than the long-form, such as `URL` or `HTML`.

Examples:

- Object class names:
  - `Unit` (NETN-ORG)
  - `Path` (NETN-SE)

- Interaction class names:
  - `AisMessage` (NETN-AIS)
  - `StopAtSideOfRoad` (NETN-ETR)

## Datatype names

A datatype name follows the same convention as for a class name, with the additions below.

Since the NETN FOM modules include many legacy datatypes (that will not be changed) and since the modules are built on existing datatypes  from the SISO RPR-FOM, exceptions to the naming convention may exist:

### Simple Datatype

The name of a simple datatype should end with the underlying  representation and size. If relevant the unit of the datatype can be included in the name. Examples: `AltitudeMeterFloat64` which includes Meter as the unit and `MassConcentrationFloat32` which excludes the unit kg/m3.

### Enumerated Datatype

An enumeration datatype name should end with the word `Enum` + size of the datatype, for example `AggregateMissionEnum16`. Enumeration values should be in capital letters; the use of underscores in the value is allowed.

### Array Datatype

If the name of an array datatype is an obvious sequence of data, for example a name, string, list, path or polygon, then no additional indication is  required. All other array datatypes should include the term `ArrayOf` +  the element datatype name, for example `ArrayOfWorldLocationStruct`. Some special array datatypes, such as `UUID`, do not follow this convention.

If an indication of the array cardinality is relevant, then the array datatype should end with the absolute or maximum size of the array. For example  `SymbolIdentifer15` or `Text255`.

### Fixed Record Datatype

Fixed record datatypes should end with the word `Struct`.

### Variant Record Datatype

Variant record datatypes should end with the word `VariantStruct`.

## Attribute and parameter names

A class attribute or a parameter name starts with a capital letter (in contrast to common coding practices). A name may be in mixed case with the first letter of each internal word capitalized. A name shall not start with an underscore, but underscores may be used within a name. A name should be short yet meaningful. The choice of a name should be mnemonic - that is, designed to indicate to the casual observer the intent of its use. One-character names should be avoided.

Common words may be abbreviated in the name. This includes currently:

- `Identifier` => `Id`

Examples:

- `UniqueId` (used in several NETN modules)
- `RulesOfEngagement` (in `SetRulesOfEngagement` task in NETN-ETR)