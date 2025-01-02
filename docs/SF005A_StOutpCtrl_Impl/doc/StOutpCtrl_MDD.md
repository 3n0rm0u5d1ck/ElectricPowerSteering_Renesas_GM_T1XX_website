---
layout: default
title: StOutpCtrl_MDD
nav_order: 4
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**StOutpCtrl**

**VERSION: 3**

**DATE:** **5-Dec-2016**

**Prepared By:**

**Matthew Leser**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                     |                       |             |              |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description**                     | **Author**            | **Version** | **Date**     |
| 1           | Initial Version                     | Akilan Rathakrishnan  | 1.0         | 02-June-2015 |
| 2           | Implementation of input name change | Basavaraja Ganeshappa | 2.0         | 30-June-2016 |
| 3           | Updated to fix Anomaly EA4#7767     | Matthew Leser         | 3.0         | 05-Dec-2016  |
|             |                                     |                       |             |              |
|             |                                     |                       |             |              |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 StOutpCtrl - High-Level Description
7](#stoutpctrl---high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of StOutpCtrl
8](#graphical-representation-of-stoutpctrl)

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

[7.1.1.1 INIT: StOutpCtrlInit1 11](#init-stoutpctrlinit1)

[7.1.1.2 Design Rationale 11](#design-rationale)

[7.1.1.3 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies)

[7.1.1.4 (Processing of function)……… 11](#processing-of-function)

[7.1.1.5 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs)

[7.1.2 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.1.2.1 Per: StOutpCtrlPer1 11](#per-stoutpctrlper1)

[7.1.2.2 Design Rationale 11](#design-rationale-1)

[7.1.2.3 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies-1)

[7.1.2.4 (Processing of function)……… 11](#processing-of-function-1)

[7.1.2.5 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs-1)

[7.2 Interrupt Functions 11](#interrupt-functions)

[7.3 Serial Communication Functions 11](#serial-communication-functions)

[7.4 Local Function/Macro Definitions
12](#local-functionmacro-definitions)

[7.4.1 Local Function \#1: RateLimit 12](#local-function-1-ratelimit)

[7.4.1.1 Description 12](#description)

[7.4.1.2 Design Rationale 12](#design-rationale-2)

[7.4.2 Local Function \#1: RateSource 12](#local-function-2-ratesource)

[7.4.2.1 Description 12](#description-1)

[7.4.2.2 Design Rationale 12](#design-rationale-3)

[7.5 GLObAL Function/Macro Definitions
12](#global-functionmacro-definitions)

[7.5.1 GLObAL Function \#1 12](#global-function-1)

[7.5.1.1 Description 12](#description-2)

[7.6 TRANSIENT FUNCTIONS 13](#transient-functions)

[8 Known Limitations With Design 14](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION 15](#unit-test-consideration)

[10 Appendix 16](#appendix)

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

|         |                                  |                                |
|----------|----------------------------------------------|-----------------|
| Sr. No. | Title                            | Version                        |
| \<1\>   | \<MDD Guidelines\>               | Process 4.02.01                |
| \<2\>   | \<Software Naming Conventions\>  | Process 4.02.01                |
| \<3\>   | \<Coding standards\>             | 2.1                            |
| \<4\>   | \<FDD SF005A_StOutpCtrl_Design\> | See Synergy Subproject version |
|         | \<Add if more available\>        |                                |

# StOutpCtrl - High-Level Description

*Refer FDD*

# Design details of software module

## Graphical representation of StOutpCtrl

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF005A_StOutpCtrl_Impl/doc/mediax/media/image2.png"
style="width:3.3in;height:4.11667in" />

## Data Flow Diagram

N/A

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

|               |            |       |       |
|---------------|------------|-------|-------|
| Constant Name | Resolution | Units | Value |
| N/A           |            |       |       |

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

## INIT: StOutpCtrlInit1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## PERIODIC FUNCTIONS 

*(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “7.1.2 Periodic Functions” and follow the
same sub-section design shown below). If none required, place the text
“None”)\>*

## Per: StOutpCtrlPer1

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

## Local Function \#1: RateLimit

|                      |                                 |         |     |       |
|----------------------|---------------------------------|---------|-----|-------|
| **Function Name**    | RateLimit                       | Type    | Min | Max   |
| **Arguments Passed** | SysOperRampRate_UlspS_T_f32     | float32 | 0.1 | 500.0 |
|                      | LoaRateLim_UlspS_T_f32          | float32 | 0.1 | 500.0 |
|                      | VehStrtStopRampRate_UlspS_T_f32 | float32 | 0.1 | 500.0 |
| **Return Value**     | SelRampRate_UlspS_T_f32         | float32 | 0.1 | 500.0 |

## Description

Implements "Rate Limit" model block in FDD -- selects ramp rate from
input rate limits.

## Design Rationale

FDD does not show a default case on the switch/case block in this
function because none is required – all possible values of the switch
variable (which is internal to this component) are covered by the cases
shown. However a default clause is required by MISRA Rule 15.3.
Therefore the default label was placed with the final case label in the
code; this is functionally equivalent to the FDD and satisfies the MISRA
rule.

## Local Function \#2: RateSource

|                      |                                  |         |     |     |
|----------------------|----------------------------------|---------|-----|-----|
| **Function Name**    | RateSource                       | Type    | Min | Max |
| **Arguments Passed** | SysOperMotTqCmdSca_Uls_T_f32     | float32 | 0.0 | 1.0 |
|                      | LoaSca_Uls_T_f32                 | float32 | 0.0 | 1.0 |
|                      | VehStrtStopMotTqCmdSca_Uls_T_f32 | float32 | 0.0 | 1.0 |
|                      | SelectedState_Cnt_T_u08          | uint8   | 1   | 3   |
| **Return Value**     | SelectedTqCmdSca_Uls_T_f32       | float32 | 0.0 | 1.0 |

## Description

Implements "Rate Source" model block in FDD -- selects scale factor from
input rate scales.

## Design Rationale

FDD does not show a default case on the switch/case block in this
function because none is required – all possible values of the switch
variable (which is internal to this component) are covered by the cases
shown. However a default clause is required by MISRA Rule 15.3.
Therefore the default label was placed with the final case label in the
code; this is functionally equivalent to the FDD and satisfies the MISRA
rule.

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