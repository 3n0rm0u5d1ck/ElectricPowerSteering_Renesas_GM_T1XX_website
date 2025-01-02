---
layout: default
title: MotAg0Meas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Motor Angle 0 Measurement**

**Module Design Document**

**VERSION: 5.0**

**DATE:** **08-Dec-2015**

**Revision History**

|             |                                  |             |             |             |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description**                  | **Author**  | **Version** | **Date**    |
| 1           | Initial Version                  | Rijvi Ahmed | 1.0         | 09-Jun-2015 |
| 2           | Updated for anomaly EA4#1233 fix | Rijvi Ahmed | 2.0         | 10-Sep-2015 |
| 3           | Updated for FDD rev. 03.00.00    | Rijvi Ahmed | 3.0         | 04-Oct-2015 |
| 4           | Updated for FDD rev. 03.01.00    | Rijvi Ahmed | 4.0         | 07-Oct-2015 |
| 5           | Updated per FDD rev. 03.03.00    | Rijvi Ahmed | 5.0         | 08-Dec-2015 |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 MotAg0Meas High-Level Description
7](#motag0meas-high-level-description)

[3.1 Design details of software module
7](#design-details-of-software-module)

[3.2 Graphical representation of CDD_MotAg0Meas
7](#graphical-representation-of-cdd_motag0meas)

[3.3 Data Flow Diagram 7](#data-flow-diagram)

[3.3.1 Module level DFD 7](#module-level-dfd)

[3.3.2 Sub-Module level DFD 7](#sub-module-level-dfd)

[3.4 COMPONENT FLOW DIAGRAM 7](#component-flow-diagram)

[4 Variable Data Dictionary 8](#variable-data-dictionary)

[4.1 User defined typedef definition/declaration
8](#user-defined-typedef-definitiondeclaration)

[4.2 Variable definition for enumerated types
8](#variable-definition-for-enumerated-types)

[5 Constant Data Dictionary 9](#constant-data-dictionary)

[5.1 Program(fixed) Constants 9](#programfixed-constants)

[5.1.1 Embedded Constants 9](#embedded-constants)

[5.1.1.1 Local 9](#local)

[5.1.1.2 Global 9](#global)

[5.1.2 Module specific Lookup Tables Constants
9](#module-specific-lookup-tables-constants)

[6 Software Module Implementation 10](#software-module-implementation)

[6.1 Sub-Module Functions 10](#sub-module-functions)

[6.1.1 Motor Control Periodic: MotAg0MeasPer1
10](#motor-control-periodic-motag0measper1)

[6.1.1.1 Design Rationale 10](#design-rationale)

[6.2 Initialization Functions 10](#initialization-functions)

[6.2.1 Init: MotAg0MeasInit1 10](#init-motag0measinit1)

[6.2.1.1 Design Rationale 10](#design-rationale-1)

[6.2.1.2 Module Outputs 10](#module-outputs)

[6.2.1.3 Module Internal 10](#module-internal)

[6.3 PERIODIC FUNCTIONS 10](#periodic-functions)

[6.3.1 Per: MotAg0MeasPer2 10](#per-motag0measper2)

[6.3.1.1 Design Rationale 10](#design-rationale-2)

[6.3.1.2 Store Module Inputs to Local copies
10](#store-module-inputs-to-local-copies)

[6.3.1.3 (Processing of function)……… 10](#processing-of-function)

[6.3.1.4 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs)

[6.4 Interrupt Functions 10](#interrupt-functions)

[6.5 Server runnables 11](#server-runnables)

[6.5.1.1 MotAg0MeasMotAg0CoeffTblRead_Oper
11](#motag0measmotag0coefftblread_oper)

[6.5.1.1.1 Design Rationale 11](#design-rationale-3)

[6.5.1.1.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies-1)

[6.5.1.1.3 (Processing of function)……… 11](#processing-of-function-1)

[6.5.1.1.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs-1)

[6.5.1.2 MotAg0MeasMotAg0CoeffTblWr_Oper
11](#motag0measmotag0coefftblwr_oper)

[6.5.1.2.1 Design Rationale 11](#design-rationale-4)

[6.5.1.2.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies-2)

[6.5.1.2.3 (Processing of function)……… 11](#processing-of-function-2)

[6.5.1.2.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs-2)

[6.6 Local Function/Macro Definitions
11](#local-functionmacro-definitions)

[6.6.1 Local Function \#1 11](#local-function-1)

[6.6.1.1 Design Rationale 11](#design-rationale-5)

[6.7 GLObAL Function/Macro Definitions
12](#global-functionmacro-definitions)

[6.8 TRANSIENT FUNCTIONS 12](#transient-functions)

[7 Known Limitations With Design 13](#known-limitations-with-design)

[8 UNIT TEST CONSIDERATION 14](#unit-test-consideration)

[9 Appendix 15](#appendix)

# Abbrevations And Acronyms

|              |                            |
|--------------|----------------------------|
| Abbreviation | Description                |
| DFD          | Design functional diagram  |
| MDD          | Module design Document     |
| FDD          | Functional Design Document |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                               |                                   |
|----------|----------------------------------------------|-----------------|
| Sr. No. | Title                         | Version                           |
| \<1\>   | MDD Guidelines                | Software Process Release 04.20.00 |
| \<2\>   | Software Naming Conventions   | Software Process Release 04.20.00 |
| \<3\>   | Design and Coding standards   | Software Process Release 04.20.00 |
| \<4\>   | FDD: CM620A_MotAg0Meas_Design | See Synergy subproject version    |

# MotAg0Meas High-Level Description

The CDD_MotAg0Meas component is the complex driver for the motor angle 0
measurement subsystem. This function initializes the registers for CSIH1
SPI channel for communicating with the motor angle 0 measurement sensor
board. The SPI transmission is triggered periodically by DMA component.
This function receives the RAW sensor data at 62.5uS rate. The component
contains two source files, both described in this MDD: CDD_MotAg0Meas.c
contains the RTE runnables and services; CDD_MotAg0Meas_MotCtrl.c
contains the motor control runnable.

## Design details of software module

*See FDD.*

## Graphical representation of CDD_MotAg0Meas

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM620A_MotAg0Meas_Impl/doc/mediax/media/image1.png"
style="width:3.23611in;height:1.70903in" />

## Data Flow Diagram

*See FDD.*

## Module level DFD

*See FDD.*

## Sub-Module level DFD

*See FDD.*

## COMPONENT FLOW DIAGRAM

*See FDD.*

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
<td><p>&lt;(Name given for the user defined typdef of type
struct/union)</p>
<p>(Variable name as qualified Refer[2])&gt;</p></td>
<td>&lt;(Variable name qualified Refer[2])&gt;</td>
<td>&lt;(Variable name qualified Refer[2&gt;</td>
<td>&lt;Min range allowed for the element in the Typedef &gt;</td>
<td>&lt;Max range allowed for the element in the Typedef&gt;</td>
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
|           |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

*\< All program specific constants will be defined in detail \>*

## Local

|                                                          |            |       |           |
|---------------------------------|---------------|-----------|-------------|
| Constant Name                                            | Resolution | Units | Value     |
| ARYIDXRAWERRREG_CNT_U08                                  | 1          | Cnt   | 0u        |
| ARYIDXRAWTURNCNTRREG_CNT_U08                             | 1          | Cnt   | 1u        |
| ARYIDXRAWAGREG_CNT_U08                                   | 1          | Cnt   | 2u        |
| SIXTEENBITMAXVAL_CNT_U16                                 | 1          | Cnt   | 65535U    |
| MOTAGRAWRESHILIM_CNT_U32                                 | 1          | Cnt   | 67108863U |
| **Also see see FDD – CM620A_MotAg0Meas_DataDict.m file** |            |       |           |

## Global

*\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Constant Name</td>
</tr>
<tr class="even">
<td><blockquote>
<p>See FDD – CM620A_MotAg0Meas_DataDict.m file</p>
</blockquote></td>
</tr>
<tr class="odd">
<td></td>
</tr>
<tr class="even">
<td></td>
</tr>
</tbody>
</table>

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|                                            |                                |                                |                                |
|------------------------------|----------------|--------------|--------------|
| Constant Name                              | Resolution                     | Value                          | Software Segment               |
| \<Refer Constant name qualified in \[2\]\> | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> |

# Software Module Implementation

## Sub-Module Functions

## Motor Control Periodic: MotAg0MeasPer1

See FDD MotAg0MeasPer1 model block.

## Design Rationale

> For run time efficiency in the motor control loop the **Compensate
> MechMtrPos** block is implemented in a optimized way in the code by
> letting a uint16 variable be overflown.

## Initialization Functions

## Init: MotAg0MeasInit1

## Design Rationale

All register initialization that is allowed at the register level (see
Register/Field coloumn of the
CM620A_MotAg0Meas_RegisterConfiguration.xlsm spreadsheet in the FDD) is
done at the register level to save execution time as compared to the
read/modify/writes that would be needed to initialize at the field
level. Field level initialization done only where required by the
spreadsheet.

## Module Outputs

See FDD: MotAg0MeasInit1 model block.

## Module Internal 

See FDD: MotAg0MeasInit1 model block for Per Instance Memory.

## PERIODIC FUNCTIONS 

##  Per: MotAg0MeasPer2

## Design Rationale

None

## Store Module Inputs to Local copies

See FDD: MotAg0MeasPer2 model block.

## (Processing of function)………

See FDD: MotAg0MeasPer2 model block.

## Store Local copy of outputs into Module Outputs

See FDD: MotAg0MeasPer2 model block

## Interrupt Functions

None

## Server runnables

## MotAg0MeasMotAg0CoeffTblRead_Oper

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*See* MotAg0MeasMotAg0CoeffTblRead *block in the FDD*

## Store Local copy of outputs into Module Outputs

*See* MotAg0MeasMotAg0CoeffTblRead *block in the FDD*

## MotAg0MeasMotAg0CoeffTblWr_Oper

## Design Rationale

*None*

## Store Module Inputs to Local copies

*See* MotAg0MeasMotAg0CoeffTblWr *in the FDD*

## (Processing of function)………

*See* MotAg0MeasMotAg0CoeffTblWr *in the FDD*

## Store Local copy of outputs into Module Outputs

*See* MotAg0MeasMotAg0CoeffTblWr*in the FDD*

## Local Function/Macro Definitions

##  Local Function \#1

|                      |              |      |     |     |
|----------------------|--------------|------|-----|-----|
| **Function Name**    | CalcCorrnTbl | Type | Min | Max |
| **Arguments Passed** | None         | N/A  | N/A | N/A |
| **Return Value**     | N/A          | N/A  | N/A | N/A |

## Design Rationale

See “Calculate Correction Table” block in the Simulink model of the
design.

## GLObAL Function/Macro Definitions

None

## TRANSIENT FUNCTIONS 

None

# Known Limitations With Design

> None.

# UNIT TEST CONSIDERATION

Following variables are used as rolling counters, so the overflow of
these variables is intentional.

Rte_Pim_MotAg0ErrParFltCntPrev

Rte_Pim_MotAg0VltgFltCntPrev

Rte_Pim_MotAg0ParFltCntPrev

Rte_Pim_MotAg0MeclRollgCntrPrev

There is an unreachable code in the SinCos_f32() function, because the
input of this function is always positive. This is ok as the
SinCos_f32() is a library function.

# Appendix

*\<This section is for appendix\>*

{% endraw %}