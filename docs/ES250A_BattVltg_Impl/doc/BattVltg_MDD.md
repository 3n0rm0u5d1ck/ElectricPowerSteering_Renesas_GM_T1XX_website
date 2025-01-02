---
layout: default
title: BattVltg_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**ForBattery or Switched Voltage Measurement**

**and Arbitration**

**VERSION: 3.0**

**DATE:** **03-JUN-2016**

**Prepared By:**

**Nick Saxton**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                      |            |             |             |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description**                      | **Author** | **Version** | **Date**    |
| 1           | Initial Version                      | SB         | 1.0         | 13-Mar-2015 |
| 2           | Fixed the typo in Per1 function name | SB         | 2.0         | 09-Apr-2015 |
| 3           | Updated for FDD v2.0.0               | NS         | 3.0         | 03-Jun-2016 |
|             |                                      |            |             |             |
|             |                                      |            |             |             |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 BattVltg & High-Level Description
7](#battvltg-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of BattVltg
8](#graphical-representation-of-battvltg)

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

[7.1.1 Initialization Functions 11](#initialization-functions)

[7.1.2 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.1.2.1 Per: BattVltgPer1 11](#per-battvltgper1)

[7.1.2.2 Design Rationale 11](#design-rationale)

[7.1.2.3 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies)

[7.1.2.4 (Processing of function)……… 11](#processing-of-function)

[7.1.2.5 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs)

[7.2 Interrupt Functions 11](#interrupt-functions)

[7.3 Serial Communication Functions 12](#serial-communication-functions)

[7.4 Local Function/Macro Definitions
12](#local-functionmacro-definitions)

[7.4.1 Local Function \#1 12](#local-function-1)

[7.4.1.1 Description 12](#description)

[7.5 GLObAL Function/Macro Definitions
12](#global-functionmacro-definitions)

[7.5.1 GLObAL Function \#1 12](#global-function-1)

[7.5.1.1 Description 12](#description-1)

[7.6 TRANSIENT FUNCTIONS 12](#transient-functions)

[8 Known Limitations With Design 13](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION 14](#unit-test-consideration)

[10 Appendix 15](#appendix)

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

|         |                                                                          |                                |
|----------|----------------------------------------------|-----------------|
| Sr. No. | Title                                                                    | Version                        |
| \<1\>   | \<MDD Guidelines\>                                                       | Process 3.06.00                |
| \<2\>   | \<Software Naming Conventions\>                                          | Process 3.06.00                |
| \<3\>   | \<Coding standards\>                                                     | Process 3.06.00                |
| \<4\>   | \<FDD - ES250A Battery or Switched Voltage Measurement and Arbitration\> | See Synergy subproject version |
|         | \<Add if more available\>                                                |                                |

# BattVltg & High-Level Description

This function scales the Battery and Switched Battery voltages used in
the EA4.0 architecture. The module determines which of the three voltage
inputs (battery or switched battery 1 or switched battery 2) should be
used by the software application.

The function provides some generic logic to decide between the switched
battery voltage 1 and switched battery voltage 2 to effective utilize
the switched voltage in case one of the switched voltages fails.

# Design details of software module

## Graphical representation of BattVltg

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES250A_BattVltg_Impl/doc/mediax/media/image2.png"
style="width:2.72986in;height:3.28125in" />

## Data Flow Diagram

## Module level DFD

*N/A*

## Sub-Module level DFD

*N/A*

## COMPONENT FLOW DIAGRAM

*N/A*

# Variable Data Dictionary

## User defined typedef definition/declaration 

*\<This section documents any user types uniquely used for the
module.\>*

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

|           |              |       |
|-----------|--------------|-------|
| Enum Name | Element Name | Value |
| N/A       |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

*\< All program specific constants will be defined in detail \>*

## Local

|                                        |            |       |       |
|----------------------------------------|------------|-------|-------|
| Constant Name                          | Resolution | Units | Value |
| BATTVLTGCORRLNSTSSWD2FLT_CNT_T_U08     | 1          | CNT   | 3     |
| BATTVLTGCORRLNSTSSWD1FLT_CNT_T_U08     | 1          | CNT   | 5     |
| BATTVLTGCORRLNSTSBATTVLTGFLT_CNT_T_U08 | 1          | CNT   | 6     |
| BATTVLTGCORRLNSTSNOFLT_CNT_T_U08       | 1          | CNT   | 7     |

## Global

*\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>*

|               |
|---------------|
| Constant Name |
| N/A           |
|               |
|               |

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|                                            |                                |                                |                                |
|------------------------------|----------------|--------------|--------------|
| Constant Name                              | Resolution                     | Value                          | Software Segment               |
| \<Refer Constant name qualified in \[2\]\> | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> |

# Software Module Implementation

## Sub-Module Functions

None

## Initialization Functions

*None*

## PERIODIC FUNCTIONS 

## 

*(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “7.1.2 Periodic Functions” and follow the
same sub-section design shown below). If none required, place the text
“None”)\>*

## Per: BattVltgPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Interrupt Functions

*None*

## Serial Communication Functions

*None*

## Local Function/Macro Definitions

\<If these are numerous and defined in a separate source file then
reference the source file only.\>

## Local Function \#1

|                      |                   |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | (Exact name used) | Type                          | Min                           | Max                           |
| **Arguments Passed** | None              | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      |                   |                               |                               |                               |
| **Return Value**     | N/A               |                               |                               |                               |

## Description

None

## GLObAL Function/Macro Definitions

## GLObAL Function \#1

|                      |                   |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | (Exact name used) | Type                          | Min                           | Max                           |
| **Arguments Passed** | None              | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      |                   |                               |                               |                               |
| **Return Value**     | N/A               |                               |                               |                               |

## Description

N/A

## TRANSIENT FUNCTIONS 

*None*

# Known Limitations With Design

1.  None

# UNIT TEST CONSIDERATION

*None*

# Appendix

*None*

{% endraw %}