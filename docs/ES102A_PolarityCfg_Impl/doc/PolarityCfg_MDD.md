---
layout: default
title: PolarityCfg_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**‘PolarityCfg’**

**VERSION: 1.0**

**DATE: 26-May-2015**

**Prepared By:**

**Sankardu Varadapureddi,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |                        |             |             |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description** | **Author**             | **Version** | **Date**    |
| 1           | Initial Version | Sankardu Varadapureddi | 1.0         | 26-May-2015 |
|             |                 |                        |             |             |
|             |                 |                        |             |             |
|             |                 |                        |             |             |
|             |                 |                        |             |             |

**<u>  
Table of Contents</u>**

[1 Abbrevations And Acronyms
[5](#abbrevations-and-acronyms)](#abbrevations-and-acronyms)

[2 References [6](#references)](#references)

[3 Power Disconnect High-Level Description
[7](#power-disconnect-high-level-description)](#power-disconnect-high-level-description)

[4 Design details of software module
[8](#design-details-of-software-module)](#design-details-of-software-module)

[4.1 Graphical representation of POWER DISCONNECT
[8](#graphical-representation-of-power-disconnect)](#graphical-representation-of-power-disconnect)

[4.2 Data Flow Diagram [8](#data-flow-diagram)](#data-flow-diagram)

[4.2.1 Module level DFD [8](#module-level-dfd)](#module-level-dfd)

[4.2.2 Sub-Module level DFD
[8](#sub-module-level-dfd)](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM
[8](#component-flow-diagram)](#component-flow-diagram)

[5 Variable Data Dictionary
[9](#variable-data-dictionary)](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
[9](#user-defined-typedef-definitiondeclaration)](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
[9](#variable-definition-for-enumerated-types)](#variable-definition-for-enumerated-types)

[6 Constant Data Dictionary
[10](#constant-data-dictionary)](#constant-data-dictionary)

[6.1 Program(fixed) Constants
[10](#programfixed-constants)](#programfixed-constants)

[6.1.1 Embedded Constants
[10](#embedded-constants)](#embedded-constants)

[6.1.1.1 Local [10](#local)](#local)

[6.1.1.2 Global [10](#global)](#global)

[6.1.2 Module specific Lookup Tables Constants
[10](#module-specific-lookup-tables-constants)](#module-specific-lookup-tables-constants)

[7 Software Module Implementation
[12](#software-module-implementation)](#software-module-implementation)

[7.1 Sub-Module Functions
[12](#sub-module-functions)](#sub-module-functions)

[7.1.1 Initialization Functions
[12](#initialization-functions)](#initialization-functions)

[7.1.1.1 INIT: PolarityCfgInit
[12](#init-polaritycfginit)](#init-polaritycfginit)

[7.1.1.1.1 Design Rationale [12](#design-rationale)](#design-rationale)

[7.1.1.1.2 Module Outputs [12](#module-outputs)](#module-outputs)

[7.1.1.1.3 Module Internal [12](#module-internal)](#module-internal)

[7.1.2 PERIODIC FUNCTIONS
[12](#periodic-functions)](#periodic-functions)

[7.1.3 Interrupt Functions
[12](#interrupt-functions)](#interrupt-functions)

[7.1.4 Server runnables [13](#server-runnables)](#server-runnables)

[7.1.4.1 PolarityCfgRead [13](#polaritycfgread)](#polaritycfgread)

[7.1.4.1.1 Design Rationale
[13](#design-rationale-1)](#design-rationale-1)

[7.1.4.1.2 Store Module Inputs to Local copies
[13](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[7.1.4.1.3 (Processing of function)………
[13](#processing-of-function)](#processing-of-function)

[7.1.4.1.4 Store Local copy of outputs into Module Outputs
[13](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[7.1.4.2 PolarityCfgWr [13](#polaritycfgwr)](#polaritycfgwr)

[7.1.4.2.1 Design Rationale
[13](#design-rationale-2)](#design-rationale-2)

[7.1.4.2.2 Store Module Inputs to Local copies
[13](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[7.1.4.2.3 (Processing of function)………
[13](#processing-of-function-1)](#processing-of-function-1)

[7.1.4.2.4 Store Local copy of outputs into Module Outputs
[13](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[7.1.5 Local Function/Macro Definitions
[13](#local-functionmacro-definitions)](#local-functionmacro-definitions)

[7.1.5.1 Local Function \#1 [13](#local-function-1)](#local-function-1)

[7.1.5.2 Description [13](#description)](#description)

[7.1.6 GLObAL Function/Macro Definitions
[13](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[7.1.7 Tranisition FUNCTIONS
[14](#tranisition-functions)](#tranisition-functions)

[8 Known Limitations With Design
[15](#known-limitations-with-design)](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION
[16](#unit-test-consideration)](#unit-test-consideration)

[10 Appendix [17](#appendix)](#appendix)

# Abbrevations And Acronyms

| Abbreviation | Description                |
|--------------|----------------------------|
| DFD          | Design functional diagram  |
| MDD          | Module design Document     |
| FDD          | Functional Design Document |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| Sr. No. | Title                                | Version                         |
|----------|----------------------------------------------|-----------------|
| 1       | MDD Guidelines                       | Process 3.06.00                 |
| 2       | Software Naming Conventions          | Process 3.06.00                 |
| 3       | Software Design and Coding standards | Process 3.06.00                 |
| 4       | FDD – ES102A_PolarityCfg_Design      | See Synergy sub project version |
|         |                                      |                                 |

# Power Disconnect High-Level Description

*This function will identify polarity control settings for certain
points in the design.*

# Design details of software module

## Graphical representation of POWER DISCONNECT

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES102A_PolarityCfg_Impl/doc/mediax/media/image1.png"
style="width:2.39167in;height:4.925in" />

## Data Flow Diagram

*Refer FDD*

## Module level DFD

*Refer FDD*

## Sub-Module level DFD

*Refer FDD*

## COMPONENT FLOW DIAGRAM

*Refer FDD*

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
<thead>
<tr class="header">
<th>Typedef Name</th>
<th>Element Name</th>
<th>User Defined Type</th>
<th><p>Legal Range</p>
<p>(min)</p></th>
<th><p>Legal Range</p>
<p>(max)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>None</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

| Enum Name | Element Name | Value |
|-----------|--------------|-------|
| None      |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local 

| Constant Name          | Resolution    | Units | Value       |
|------------------------|---------------|-------|-------------|
| HWAG0POL_CNT_U32       | Bitfield Mask | NA    | 0x00000001U |
| HWAG1POL_CNT_U32       | Bitfield Mask | NA    | 0x00000002U |
| HWAG2POL_CNT_U32       | Bitfield Mask | NA    | 0x00000004U |
| HWAG3POL_CNT_U32       | Bitfield Mask | NA    | 0x00000008U |
| HWAG4POL_CNT_U32       | Bitfield Mask | NA    | 0x00000010U |
| HWAG5POL_CNT_U32       | Bitfield Mask | NA    | 0x00000020U |
| HWAG6POL_CNT_U32       | Bitfield Mask | NA    | 0x00000040U |
| HWAG7POL_CNT_U32       | Bitfield Mask | NA    | 0x00000080U |
| HWTQ0POL_CNT_U32       | Bitfield Mask | NA    | 0x00000100U |
| HWTQ1POL_CNT_U32       | Bitfield Mask | NA    | 0x00000200U |
| HWTQ2POL_CNT_U32       | Bitfield Mask | NA    | 0x00000400U |
| HWTQ3POL_CNT_U32       | Bitfield Mask | NA    | 0x00000800U |
| HWTQ4POL_CNT_U32       | Bitfield Mask | NA    | 0x00001000U |
| HWTQ5POL_CNT_U32       | Bitfield Mask | NA    | 0x00002000U |
| HWTQ6POL_CNT_U32       | Bitfield Mask | NA    | 0x00004000U |
| HWTQ7POL_CNT_U32       | Bitfield Mask | NA    | 0x00008000U |
| MOTAGMECL0POL_CNT_U32  | Bitfield Mask | NA    | 0x00010000U |
| MOTAGMECL1POL_CNT_U32  | Bitfield Mask | NA    | 0x00020000U |
| MOTAGMECL2POL_CNT_U32  | Bitfield Mask | NA    | 0x00040000U |
| MOTAGMECL3POL_CNT_U32  | Bitfield Mask | NA    | 0x00080000U |
| MOTAGMECL4POL_CNT_U32  | Bitfield Mask | NA    | 0x00100000U |
| MOTAGMECL5POL_CNT_U32  | Bitfield Mask | NA    | 0x00200000U |
| MOTAGMECL6POL_CNT_U32  | Bitfield Mask | NA    | 0x00400000U |
| MOTAGMECL7POL_CNT_U32  | Bitfield Mask | NA    | 0x00800000U |
| MOTELECMECLPOL_CNT_U32 | Bitfield Mask | NA    | 0x01000000U |
| ASSIMECHPOL_CNT_U32    | Bitfield Mask | NA    | 0x02000000U |

## Global

| Constant Name |
|---------------|
|               |

## Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

# Software Module Implementation

## Sub-Module Functions 

## Initialization Functions

*PolarityCfgInit*

## INIT: PolarityCfgInit

## Design Rationale

*Design follows implemenetation in FDD.*

## Module Outputs

*Refer ‘PolarityCfgInit’ block in FDD*

## Module Internal 

None

## PERIODIC FUNCTIONS 

None

## Interrupt Functions

*None*

##  Server runnables

##  PolarityCfgRead

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer ‘PolarityCfgRead’ block in FDD*

## Store Local copy of outputs into Module Outputs

*None*

## PolarityCfgWr

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer* ‘*PolarityCfgWr’ block in FDD*

## Store Local copy of outputs into Module Outputs

*None*

## Local Function/Macro Definitions

## Local Function \#1

|                      |                        |        |            |            |
|---------------|-------------------------|----------|---------------|---------|
| **Function Name**    | GetPolarity            | Type   | Min        | Max        |
| **Arguments Passed** | Polarity_Cnt_T_u32     | uint32 | 0          | 0xFFFFFFFF |
|                      | PolarityMask_Cnt_T_u32 | uint32 | 0x00000001 | 0x02000000 |
| **Return Value**     | Polarity_Cnt_T_s08     | sint08 | -1         | 1          |

## Description

-   **Design:**

if ( (Polarity_Cnt_T_u32 & PolarityMask_Cnt_T_u32) ==
PolarityMask_Cnt_T_u32 )

set ‘Polarity_Cnt_T_s08’ to ‘1’

else

set ‘Polarity_Cnt_T_s08’ to ‘-1’

-   **Note:** ‘PolarityMask_Cnt_T_u32’ is a bit field mask and takes
    values mentioned in table at sec 6.1.1.1

## GLObAL Function/Macro Definitions

None

## Tranisition FUNCTIONS 

None

# Known Limitations With Design

None

# UNIT TEST CONSIDERATION

None

# Appendix

*None*

{% endraw %}