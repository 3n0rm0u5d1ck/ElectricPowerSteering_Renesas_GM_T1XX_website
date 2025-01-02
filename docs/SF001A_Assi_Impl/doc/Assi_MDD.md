---
layout: default
title: Assi_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Assist**

**VERSION: 2.0**

**DATE:** **09-AUG-2016**

**Prepared By:**

**Nick Saxton**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |            |             |             |
|-------------|-----------------|------------|-------------|-------------|
| **Sl. No.** | **Description** | **Author** | **Version** | **Date**    |
| 1           | Initial Version | SB         | 1.0         | 02-JUN-2015 |
| 2           | Quality update  | NS         | 2.0         | 09-AUG-2016 |
|             |                 |            |             |             |
|             |                 |            |             |             |
|             |                 |            |             |             |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 Assi & High-Level Description 7](#assi-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of Assi
8](#graphical-representation-of-assi)

[4.2 Data Flow Diagram 8](#data-flow-diagram)

[4.2.1 Module level DFD 8](#module-level-dfd)

[4.2.2 Sub-Module level DFD 8](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM 8](#component-flow-diagram)

[5 Variable Data Dictionary 9](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
9](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
9](#variable-definition-for-enumerated-types)

[6 Constant Data Dictionary 10](#constant-data-dictionary)

[6.1 Program(fixed) Constants 10](#programfixed-constants)

[6.1.1 Embedded Constants 10](#embedded-constants)

[6.1.1.1 Local 10](#local)

[6.1.1.2 Global 10](#global)

[6.1.2 Module specific Lookup Tables Constants
10](#module-specific-lookup-tables-constants)

[7 Software Module Implementation 11](#software-module-implementation)

[7.1 Sub-Module Functions 11](#sub-module-functions)

[7.2 Initialization Functions 11](#initialization-functions)

[7.3 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.3.1 Per: Assiper1 11](#per-assiper1)

[7.3.1.1 Design Rationale 11](#design-rationale)

[7.3.1.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies)

[7.3.1.3 (Processing of function)……… 11](#processing-of-function)

[7.3.1.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs)

[7.4 Non PERIODIC FUNCTIONS 11](#non-periodic-functions)

[7.5 Interrupt Functions 11](#__RefHeading___Toc421801385)

[7.6 Serial Communication Functions 12](#serial-communication-functions)

[7.7 Local Function/Macro Definitions
12](#local-functionmacro-definitions)

[7.8 GLObAL Function/Macro Definitions
12](#global-functionmacro-definitions)

[7.9 TRANSIENT FUNCTIONS 12](#transient-functions)

[8 Unit Test Considerations 13](#unit-test-considerations)

[9 Known Limitations With Design 14](#known-limitations-with-design)

[10 NoneAppendix 15](#__RefHeading___Toc421801392)

# Abbrevations And Acronyms

|              |                                         |
|--------------|-----------------------------------------|
| Abbreviation | Description                             |
| DFD          | Design functional diagram               |
| MDD          | Module design Document                  |
|              | \<ADD more to the table if applicable\> |
|              |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                                 |                                |
|---------|---------------------------------|--------------------------------|
| Sr. No. | Title                           | Version                        |
| \<1\>   | \<MDD Guidelines\>              | Process 4.00.00                |
| \<2\>   | \<Software Naming Conventions\> | Process 4.00.00                |
| \<3\>   | \<Coding standards\>            | Process 4.00.00                |
| \<4\>   | FDD - SF001A_Assi_Design        | See Synergy Subproject version |
|         | \<Add if more available\>       |                                |

# Assi & High-Level Description

Refer FDD

# Design details of software module

## Graphical representation of Assi

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF001A_Assi_Impl/doc/mediax/media/image2.png"
style="width:3.44861in;height:5.90694in" />

## Data Flow Diagram

## Module level DFD

## Sub-Module level DFD

## COMPONENT FLOW DIAGRAM

# Variable Data Dictionary

## User defined typedef definition/declaration 

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 31%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Typedef Name</td>
<td>Element Name</td>
<td>User Defined Type</td>
<td><p>Legal Range</p>
<p>(min)</p></td>
<td><p>Legal Range</p>
<p>(max)</p></td>
</tr>
<tr class="even">
<td>N/A</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

|           |                                          |                       |
|--------------------------------|-----------------------------|------------|
| Enum Name | Element Name                             | Value                 |
| N/A       | \<(Variable name qualified Refer\[2\])\> | \<Define the value \> |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

*\< All program specific constants will be defined in detail \>*

## Local

|                              |            |       |       |
|------------------------------|------------|-------|-------|
| Constant Name                | Resolution | Units | Value |
| Refer constants from .m file |            |       |       |

## Global

*\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>*

|                              |
|------------------------------|
| Constant Name                |
| Refer constants from .m file |
|                              |
|                              |

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| Refer .m file |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

*NONE*

## Initialization Functions

*None*

## PERIODIC FUNCTIONS 

## 

*(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “7.3 Periodic Functions” and follow the
same sub-section design shown below). If none required, place the text
“None”)\>*

## Per: Assiper1

## Design Rationale

*Fault Injection client call is conditional compiled based on
“FLTINJENA” build constant.*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

##  Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Non PERIODIC FUNCTIONS 

*None*

## Interrupt Functions

*None*

## Serial Communication Functions

*None*

## Local Function/Macro Definitions

None

## GLObAL Function/Macro Definitions

None

## TRANSIENT FUNCTIONS 

# Unit Test Considerations

None

# Known Limitations With Design

# Appendix

{% endraw %}