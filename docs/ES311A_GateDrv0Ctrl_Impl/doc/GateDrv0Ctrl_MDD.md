---
layout: default
title: GateDrv0Ctrl_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Gate Drive 0 Control**

**VERSION:** **2**

**DATE:** **21-Jan-2017**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                  |               |              |
|--------|---------------------------------------|---------------|-----------|
| **Version** | **Description**                  | **Author**    | **Date**     |
| 1           | Initial version                  | Rijvi Ahmed   | 07-July-2016 |
| 2           | Updated to design revision 1.8.0 | Avinash James | 21-Jan-2017  |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 GATEDRV0CTRL & High-Level Description
7](#gatedrv0ctrl-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of GATEDRV0CTRL
8](#graphical-representation-of-gatedrv0ctrl)

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

[7.2.1 Per: GateDrv0CtrlInit1 11](#per-gatedrv0ctrlinit1)

[7.3 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.3.1 Per: GateDrv0CtrlPer1 11](#per-gatedrv0ctrlper1)

[7.3.1.1 Design Rationale 11](#design-rationale)

[7.3.1.2 Processing of Function 11](#processing-of-function)

[7.3.2 Per: GateDrv0CtrlPer2 11](#per-gatedrv0ctrlper2)

[7.3.2.1 Design Rationale 11](#design-rationale-1)

[7.3.2.2 Processing of Function 11](#processing-of-function-1)

[7.4 Interrupt Functions 11](#interrupt-functions)

[7.5 Serial Communication Functions 11](#serial-communication-functions)

[7.6 Local Function/Macro Definitions
11](#local-functionmacro-definitions)

[7.6.1 Local Function \#1 11](#local-function-1)

[7.6.1.1 Description 11](#description)

[7.6.2 Local Function \#2 12](#local-function-2)

[7.6.2.1 Description 12](#description-1)

[7.6.3 Local Function \#3 12](#local-function-3)

[7.6.3.1 Description 12](#description-2)

[7.6.4 Local Function \#4 12](#local-function-4)

[7.6.4.1 Description 12](#description-3)

[7.6.5 Local Function \#5 12](#local-function-5)

[7.6.5.1 Description 12](#description-4)

[7.6.6 Local Function \#6 12](#local-function-6)

[7.6.6.1 Description 12](#description-5)

[7.6.7 Local Function \#7 13](#local-function-7)

[7.6.7.1 Description 13](#description-6)

[7.6.8 Local Function \#8 13](#local-function-8)

[7.6.8.1 Description 13](#description-7)

[7.6.9 Local Function \#9 13](#local-function-9)

[7.6.9.1 Description 13](#description-8)

[7.7 GLObAL Function/Macro Definitions
13](#global-functionmacro-definitions)

[8 Known Limitations With Design 14](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION 15](#unit-test-consideration)

# Abbrevations And Acronyms

|              |                           |
|--------------|---------------------------|
| Abbreviation | Description               |
| DFD          | Design functional diagram |
| MDD          | Module design Document    |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                             |                                 |
|---------|-----------------------------|---------------------------------|
| Sr. No. | Title                       | Version                         |
| 1       | MDD Guidelines              | Process 04.02.01                |
| 2       | Software Naming Conventions | Process 04.02.01                |
| 3       | Software Coding Standards   | Process 04.02.01                |
| 4       | FDD – ES311A GateDrv0Ctrl   | See synergy sub project version |

# GATEDRV0CTRL & High-Level Description

This module configures the GateDrive0 connected with SPI channel CSIH2.
It also does the diagnostics for GateDrive0 using SPI interface.

# Design details of software module

## Graphical representation of GATEDRV0CTRL

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES311A_GateDrv0Ctrl_Impl/doc/mediax/media/image1.png"
style="width:3.85833in;height:3.63333in" />

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
<td>None</td>
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
| None      |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local

|                             |            |       |                                                               |
|---------------------------------|---------------|-----------|-------------|
| Constant Name               | Resolution | Units | Value                                                         |
| GATEDRVOFFSTCHKSIZE_CNT_U08 | 1U         | Cnt   | ((TblSize_m(ELECGLBPRM_GATEDRVOFFSTCHKDATA_CNT_U16)/8U) - 1U) |

## Global

|                  |
|------------------|
| Constant Name    |
| Refer to the FDD |

## Module specific Lookup Tables Constants

|                     |            |       |                  |
|---------------------|------------|-------|------------------|
| Constant Name       | Resolution | Value | Software Segment |
| Refer to the design |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

None

## Initialization Functions

## Per: GateDrv0CtrlInit1

## PERIODIC FUNCTIONS

## Per: GateDrv0CtrlPer1

## Design Rationale

None

## Processing of Function

See design model for details.

## Per: GateDrv0CtrlPer2

## Design Rationale

None

## Processing of Function

See design model for details.

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

## Local Function \#1

|                      |                    |                  |     |      |
|----------------------|--------------------|------------------|-----|------|
| **Function Name**    | SpiAsyncTx         | Type             | Min | Max  |
| **Arguments Passed** | Channel_Cnt_T_u08  | Spi_ChannelType  | 0   | Full |
|                      | TxData_Cnt_T_u16   | Spi_DataType     | 0   | Full |
|                      | Sequence_Cnt_T_u08 | Spi_SequenceType | 0   | Full |
| **Return Value**     | None               |                  |     |      |

## Description

(void) Spi_WriteIB( Channel_Cnt_T_u08, &TxData_Cnt_T_u16 );

(void) Call_Spi_AsyncTransmit( Sequence_Cnt_T_u08 );

## Local Function \#2

|                      |             |      |     |     |
|----------------------|-------------|------|-----|-----|
| **Function Name**    | OffStVrfySt | Type | Min | Max |
| **Arguments Passed** | None        |      |     |     |
| **Return Value**     | None        |      |     |     |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/OffState Verification State**block in design model.

## Local Function \#3

|                      |                |         |       |      |
|----------------------|----------------|---------|-------|------|
| **Function Name**    | OffStVrfyData  | Type    | Min   | Max  |
| **Arguments Passed** | None           |         |       |      |
| **Return Value**     | Flt_Cnt_T_logl | Boolean | FALSE | TRUE |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/OffState Verification State/OffSt Verification Chk and Transition
to Config State/OffStChk Incomplete/Offstate Verification /OffState
Verification Check** block in design model.

\*It is optimized in the implementation to reduce the high static path
count.

## Local Function \#4

|                      |       |      |     |     |
|----------------------|-------|------|-----|-----|
| **Function Name**    | CfgSt | Type | Min | Max |
| **Arguments Passed** | None  |      |     |     |
| **Return Value**     | None  |      |     |     |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Configuration State** block in design model.

## Local Function \#5

|                      |              |      |     |     |
|----------------------|--------------|------|-----|-----|
| **Function Name**    | ReadBackRegs | Type | Min | Max |
| **Arguments Passed** | None         |      |     |     |
| **Return Value**     | None         |      |     |     |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Configuration State/Read back Registers** block in design model.

## Local Function \#6

|                      |               |      |     |     |
|----------------------|---------------|------|-----|-----|
| **Function Name**    | OperFltMonrSt | Type | Min | Max |
| **Arguments Passed** | None          |      |     |     |
| **Return Value**     | None          |      |     |     |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Operate Fault Monitor State** block in design model.

## Local Function \#7

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | GateDrvDetermineOnStSngFETFlt | Type    | Min   | Max  |
| **Arguments Passed** | None                          |         |       |      |
| **Return Value**     | GenGateDrvFlt_Cnt_T_logl      | Boolean | FALSE | TRUE |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Operate Fault Monitor State/Determine Faults/Status Register
indicates Fault/Determine OnState Single FET Fault** block in design
model.

## Local Function \#8

|                      |                          |         |       |      |
|----------------------|--------------------------|---------|-------|------|
| **Function Name**    | GateDrvDetermineVltgFlt  | Type    | Min   | Max  |
| **Arguments Passed** | None                     |         |       |      |
| **Return Value**     | GenGateDrvFlt_Cnt_T_logl | Boolean | FALSE | TRUE |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Operate Fault Monitor State/Determine Faults/Status Register
indicates Fault/Determine VREG/Bootstrap Voltage Fault** block in design
model.

## Local Function \#9

|                      |                            |         |       |        |
|----------------------|----------------------------|---------|-------|--------|
| **Function Name**    | GateDrvDetermineGenericFlt | Type    | Min   | Max    |
| **Arguments Passed** | GateDrvAllSts_Cnt_T_u16    | Uint16  | 0     | 0xFFFF |
| **Return Value**     | GenGateDrvFlt_Cnt_T_logl   | Boolean | FALSE | TRUE   |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Operate Fault Monitor State/Determine Faults/Status Register
indicates Fault/Determine Generic Gate Drive Fault** block in design
model.

## GLObAL Function/Macro Definitions

None

# Known Limitations With Design

“Operate Fault Monitor State” block need to be revisited and optimized.

# UNIT TEST CONSIDERATION

None

{% endraw %}