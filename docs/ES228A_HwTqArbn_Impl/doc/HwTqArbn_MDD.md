---
layout: default
title: HwTqArbn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Handwheel Torque Arbitration**

**VERSION: 1.0**

**DATE: 11-MAY-2015**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |             |             |             |
|-------------|-----------------|-------------|-------------|-------------|
| **Sl. No.** | **Description** | **Author**  | **Version** | **Date**    |
| 1           | Initial Version | Rijvi Ahmed | 1.0         | 11-May-2015 |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 MDD HWTQARBN & High-Level Description
7](#mdd-hwtqarbn-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of HWTQARBN
8](#graphical-representation-of-hwtqarbn)

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

[7.3.1 Per: HwTqArbnPer1 11](#per-hwtqarbnper1)

[7.3.1.1 Design Rationale 11](#design-rationale)

[7.3.1.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies)

[7.3.1.3 (Processing of function)……… 11](#processing-of-function)

[7.3.1.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs)

[7.4 Interrupt Functions 11](#interrupt-functions)

[7.5 Serial Communication Functions 12](#serial-communication-functions)

[7.6 Local Function/Macro Definitions
12](#local-functionmacro-definitions)

[7.6.1 Local Function \#1 12](#local-function-1)

[7.6.1.1 Description 12](#description)

[7.7 GLObAL Function/Macro Definitions
12](#global-functionmacro-definitions)

[7.7.1 GLObAL Function \#1 12](#global-function-1)

[7.7.1.1 Description 12](#description-1)

[7.8 TRANSIENT FUNCTIONS 12](#transient-functions)

[8 Known Limitations With Design 13](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION 14](#unit-test-consideration)

[1 Appendix 15](#appendix)

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

|         |                             |                                 |
|---------|-----------------------------|---------------------------------|
| Sr. No. | Title                       | Version                         |
| 1       | MDD Guidelines              | Process 03.06.00                |
| 2       | Software Naming Conventions | Process 03.06.00                |
| 3       | Software Coding Standards   | Process 03.06.00                |
| 4       | FDD – ES228A/HwTqArbn       | See synergy sub project version |

# MDD HWTQARBN & High-Level Description

> None

# Design details of software module

## Graphical representation of HWTQARBN

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES228A_HwTqArbn_Impl/doc/mediax/media/image1.png"
style="width:2.88333in;height:3.38333in" />

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
</tbody>
</table>

## Variable definition for enumerated types

|           |              |       |
|-----------|--------------|-------|
| Enum Name | Element Name | Value |
|           |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

*\< All program specific constants will be defined in detail \>*

## Local

|                           |            |       |       |
|---------------------------|------------|-------|-------|
| Constant Name             | Resolution | Units | Value |
| CORRLNSTSMASKSIGA_CNT_U08 | 1          | Cnt   | 0x01u |
| CORRLNSTSMASKSIGB_CNT_U08 | 1          | Cnt   | 0x02u |
| CORRLNSTSMASKSIGC_CNT_U08 | 1          | Cnt   | 0x04u |
| CORRLNSTSMASKSIGD_CNT_U08 | 1          | Cnt   | 0x08u |
| MAXSTALLCNTR_CNT_U08      | 1          | Cnt   | 255u  |

## Global

*\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>*

|               |
|---------------|
| Constant Name |
|               |

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| N/A           |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

*None*

## Initialization Functions

*\<(Note: For multiple init functions, insert new headers at the “Header
2” level – subset of “ Initialization Function section above” and follow
the same sub-section design shown below . If none required, place the
text “None”))\>*

*None*

## PERIODIC FUNCTIONS 

*(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “7.3 Periodic Functions” and follow the
same sub-section design shown below). If none required, place the text
“None”)\>*

## Per: HwTqArbnPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## 

## Interrupt Functions

*None*

## Serial Communication Functions

*None*

## Local Function/Macro Definitions

\<If these are numerous and defined in a separate source file then
reference the source file only.\>

## Local Function \#1

|                      |                          |          |     |     |
|----------------------|--------------------------|----------|-----|-----|
| **Function Name**    | SigAvlChkRev             | Type     | Min | Max |
| **Arguments Passed** | SigRollgCntr_Cnt_T_u08   | Uint8    | 0   | 255 |
|                      | SigQlfr_Cnt_T_enum       | SigQlfr1 | 0   | 2   |
|                      | kMaxStallCnt_Cnt_T_u08   | Uint8    | 0   | 255 |
|                      | \*LstRollgCntr_Cnt_T_u08 | Uint8    | 0   | 255 |
|                      | \*StallCntr_Cnt_T_u08    | Uint8    | 0   | 255 |
| **Return Value**     | SigAvl_Cnt_T_lgc         | boolean  | 0   | 1   |

## Description

> *Refer to FDD*

## GLObAL Function/Macro Definitions

\<If these are numerous and defined in a separate source file then
reference the source file only.\>

## GLObAL Function \#1

|                      |      |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | None | Type                          | Min                           | Max                           |
| **Arguments Passed** | None | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      |      |                               |                               |                               |
| **Return Value**     | None |                               |                               |                               |

## Description

N/A

## TRANSIENT FUNCTIONS 

*None*

# Known Limitations With Design

None

# UNIT TEST CONSIDERATION

None

# Appendix

*None*

{% endraw %}