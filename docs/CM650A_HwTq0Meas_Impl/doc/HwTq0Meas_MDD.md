---
layout: default
title: HwTq0Meas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**\<Component Name\>**

**June 19, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**SEPGroup,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

<table>
<colgroup>
<col style="width: 46%" />
<col style="width: 18%" />
<col style="width: 10%" />
<col style="width: 12%" />
<col style="width: 12%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Description</strong></td>
<td><strong>Author</strong></td>
<td><strong>Version</strong></td>
<td><strong>Date</strong></td>
<td></td>
</tr>
<tr class="even">
<td>Initial Version</td>
<td>Rijvi Ahmed</td>
<td>1.0</td>
<td>15-Apr-2015</td>
<td></td>
</tr>
<tr class="odd">
<td><p>Updated per implementation of design change.</p>
<p>Updated to the latest template.</p></td>
<td>Rijvi Ahmed</td>
<td>2.0</td>
<td>09-Aug-2015</td>
<td></td>
</tr>
<tr class="even">
<td>Inplement Rack Limiter EOT</td>
<td>Rijvi Ahmed</td>
<td>3.0</td>
<td>03-Sep-2015</td>
<td></td>
</tr>
<tr class="odd">
<td>Updated for FDD v 1.6.0</td>
<td>Selva Sengottaiyan</td>
<td>4.0</td>
<td>14-Oct-2015</td>
<td></td>
</tr>
<tr class="even">
<td>CM650A HwTq0Meas Rev1.8.0 - Implementation(A3109) EA4#3156</td>
<td>Selva</td>
<td>5.0</td>
<td>21-Dec-15</td>
<td></td>
</tr>
</tbody>
</table>

<u>Table of Contents</u>

[**1** **Introduction 5**](#introduction)

[1.1 Purpose 5](#purpose)

[2 HwTq0Meas & High-Level Description
6](#component-name-high-level-description)

[3 Design details of software module
7](#design-details-of-software-module)

[3.1 Graphical representation of HwTq0Meas
7](#graphical-representation-of-hwtq0meas)

[3.2 Data Flow Diagram 7](#data-flow-diagram)

[3.2.1 Component level DFD 7](#component-level-dfd)

[3.2.2 Function level DFD 7](#function-level-dfd)

[4 Constant Data Dictionary 8](#constant-data-dictionary)

[4.1 Program (fixed) Constants 8](#program-fixed-constants)

[4.1.1 Embedded Constants 8](#embedded-constants)

[5 Software Component Implementation
9](#software-component-implementation)

[5.1 Sub-Module Functions 9](#sub-module-functions)

[5.1.1 Init: HwTq0MeasInit1 9](#init-hwtq0measinit1)

[5.1.1.1 Design Rationale 9](#design-rationale)

[5.1.1.2 Module Outputs 9](#module-outputs)

[5.1.2 Per: HwTq0MeasPer1 9](#per-hwtq0measper1)

[5.1.2.1 Design Rationale 9](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)……… 9](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
9](#store-local-copy-of-outputs-into-module-outputs)

[5.1.3 Per: HwTq0MeasPer2 9](#per-hwtq0measper2)

[5.1.3.1 Design Rationale 9](#design-rationale-2)

[5.1.3.2 Store Module Inputs to Local copies
10](#store-module-inputs-to-local-copies-1)

[5.1.3.3 (Processing of function)……… 10](#processing-of-function-1)

[5.1.3.4 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs-1)

[5.2 Server Runables 10](#server-runables)

[5.2.1 HwTq0MeasHwTq0AutTrim_oper 10](#hwtq0meashwtq0auttrim_oper)

[5.2.1.1 Design Rationale 10](#design-rationale-3)

[5.2.1.2 (Processing of function)……… 10](#processing-of-function-2)

[5.2.2 HwTq0MeasHwTq0ClrTrim_Oper 10](#hwtq0meashwtq0clrtrim_oper)

[5.2.2.1 Design Rationale 10](#design-rationale-4)

[5.2.2.2 (Processing of function)……… 10](#processing-of-function-3)

[5.2.3 HwTq0MeasHwTq0ReadTrim_Oper 10](#hwtq0meashwtq0readtrim_oper)

[5.2.3.1 Design Rationale 10](#design-rationale-5)

[5.2.3.2 (Processing of function)……… 10](#processing-of-function-4)

[5.2.4 HwTq0MeasHwTq0TrimPrfmdSts_Oper
11](#hwtq0meashwtq0trimprfmdsts_oper)

[5.2.4.1 Design Rationale 11](#design-rationale-6)

[5.2.4.2 (Processing of function)……… 11](#processing-of-function-5)

[5.2.5 HwTq0MeasHwTq0WrTrim_Oper 11](#hwtq0meashwtq0wrtrim_oper)

[5.2.5.1 Design Rationale 11](#design-rationale-7)

[5.2.5.2 (Processing of function)……… 11](#processing-of-function-6)

[5.2.6 HwTq0MeasTrigStrt_Oper 11](#hwtq0meastrigstrt_oper)

[5.2.6.1 Design Rationale 11](#design-rationale-8)

[5.2.6.2 (Processing of function)……… 11](#processing-of-function-7)

[5.3 Interrupt Functions 11](#interrupt-functions)

[5.4 Module Internal (Local) Functions
11](#module-internal-local-functions)

[5.4.1 Local Function \#1 11](#local-function-1)

[5.4.1.1 Design Rationale 11](#design-rationale-9)

[5.4.2 Local Function \#2 12](#__RefHeading___Toc438496808)

[5.4.2.1 Design Rationale 12](#__RefHeading___Toc438496809)

[5.5 GLOBAL Function/Macro Definitions
12](#global-functionmacro-definitions)

[6 Known Limitations with Design 13](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 14](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 15](#abbreviations-and-acronyms)

[Appendix B Glossary 16](#glossary)

[Appendix C References 18](#references)

# Introduction

## Purpose

Module design document for Hand Wheel Torque 0 Measurement Function.

# \<Component Name\>& High-Level Description

This module configures and processes the RSENT0 peripheral, which is
connected to the handwheel torque 0 sensor. The module configures the
peripheral, triggers transfers, and processes the received data.

This module also reads and provides the rack limiter EOT information
which is stored in torque sensor 0 scratchpad.

# Design details of software module

## Graphical representation of HwTq0Meas

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM650A_HwTq0Meas_Impl/doc/mediax/media/image2.png"
style="width:4.79167in;height:2.73333in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                               |                        |       |              |
|---------------------------------|---------------|-----------|-------------|
| Constant Name                 | Resolution             | Units | Value        |
|                               |                        |       |              |
| TQDATAMASK_CNT_U32            | 1                      | Cnt   | 0x00000FFFUL |
| SENTSYNCTRIG_CNT_U32          | 1                      | Cnt   | 16UL         |
| REGCFGWAITTI_CNT_U32          | 1                      | Cnt   | 2UL          |
| RACKLIMREOTSIGHILIM_HWDEG_F32 | Single Precision float | HwDeg | (800.0F)     |
| RACKLIMREOTSIGLOLIM_HWDEG_F32 | Single Precision float | HwDeg | (-800.0F)    |
| RACKLIMRCCWEOTSCA_ULS_F32     | Single Precision float | Uls   | (-0.1953F)   |
| RACKLIMRCWEOTSCA_ULS_F32      | Single Precision float | Uls   | (0.1953F)    |
| EOTCSMASK_CNT_U32             | 1                      | Cnt   | 0x00000700UL |
| EOTIDTWO_CNT_U08              | 1                      | Cnt   | 2U           |
| EOTIDTHREE_CNT_U08            | 1                      | Cnt   | 3U           |
| EOTIDFOUR_CNT_U08             | 1                      | Cnt   | 4U           |
| EOTDATAMASK_CNT_U32           | 1                      | Cnt   | 0x00000FF0UL |
| EOTIDMASK_CNT_U32             | 1                      | Cnt   | 0x0000000FUL |
| FRSMASK_CNT_U32               | 1                      | Cnt   | 0x00000001UL |
| CSMASK_CNT_U32                | 1                      | Cnt   | 0x000000FEUL |
| FCCNMASK_CNT_U32              | 1                      | Cnt   | 0x30000000UL |
| SLOWMSGDATAMASK_CNT_U32       | 1                      | Cnt   | 0x80000000UL |

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

## Init: HwTq0MeasInit1

## Design Rationale

Magic numbers are used due to the large number of numeric values (for
peripheral register configuration), it is more readable and easier to
maintain without using embedded constants for these values. The values
are shown in code comments, and line up exactly with the definitions
given in the design module (a special spreadsheet was included in the
design for this purpose).

See CM650A_HwTq0Meas_RSENTPeripheralCfg.xlsx in design module.

## Module Outputs

*Refer to FDD*

###  [section]

## Per: HwTq0MeasPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Per: HwTq0MeasPer2

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runables 

## HwTq0MeasHwTq0AutTrim_oper

## Design Rationale

*None*

##  (Processing of function)………

*See block “*HwTq0MeasHwTq0AutTrim*” in the Simulink model of the
design.*

## HwTq0MeasHwTq0ClrTrim_Oper

## Design Rationale

*None*

##  (Processing of function)………

*See block “*HwTq0MeasHwTq0ClrTrim*” in the Simulink model of the
design.*

## HwTq0MeasHwTq0ReadTrim_Oper

## Design Rationale

*None*

##  (Processing of function)………

*See block “HwTq0MeasHwTq0ReadTrim” in the Simulink model of the
design.*

## HwTq0MeasHwTq0TrimPrfmdSts_Oper

## Design Rationale

*None*

##  (Processing of function)………

*See block “HwTq0MeasHwTq0TrimPrfmdSts” in the Simulink model of the
design.*

## HwTq0MeasHwTq0WrTrim_Oper

## Design Rationale

*None*

##  (Processing of function)………

*See block “HwTq0MeasHwTq0WrTrim” in the Simulink model of the design.*

##  HwTq0MeasTrigStrt_Oper

## Design Rationale

*None*

##  (Processing of function)………

*See block “HwTq0MeasTrgStrt” in the Simulink model of the design.*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                    |      |     |     |
|----------------------|--------------------|------|-----|-----|
| **Function Name**    | RackLimrEotSigRead | Type | Min | Max |
| **Arguments Passed** | None               | N/A  | N/A | N/A |
| **Return Value**     | N/A                | N/A  | N/A | N/A |

## Design Rationale

See RackLimrEot/RackLimrEotSigRead2 block in the Simulink model of the
design.

## Local Function \#2

|                      |                             |      |     |     |
|----------------------|-----------------------------|------|-----|-----|
| **Function Name**    | ReadRegister                | Type | Min | Max |
| **Arguments Passed** | RegisterDummyRead_Cnt_T_u32 | N/A  | N/A | N/A |
| **Return Value**     | RegisterDummyRead_Cnt_T_u32 | N/A  | N/A | N/A |

## Design Rationale

This function can be used both for read-and-use and for read-and-discard

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

Overflow for the variables **Rte_Pim_HwTq0MeasPrevRollgCntr,**
**Rte_Pim_HwTq0MsgMissRxCnt,** **Rte_Pim_HwTq0ComStsErrCntr,
Rte_Pim_HwTq0IntSnsrErrCntr** are intentional as these are used as
rolling counters.

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**           |
|-----------------------------|---------------------------|
| DFD                         | Design functional diagram |
| MDD                         | Module design Document    |

####### Glossary

**Note**: Terms and definitions from the source “Nexteer Automotive”
take precedence over all other definitions of the same term. Terms and
definitions from the source “Nexteer Automotive” are formulated from
multiple sources, including the following:

-   ISO 9000

-   ISO/IEC 12207

-   ISO/IEC 15504

-   Automotive SPICE® Process Reference Model (PRM)

-   Automotive SPICE® Process Assessment Model (PAM)

-   ISO/IEC 15288

-   ISO 26262

-   IEEE Standards

-   SWEBOK

-   PMBOK

-   Existing Nexteer Automotive documentation

| **Term** | **Definition**         | **Source** |
|----------|------------------------|------------|
| MDD      | Module Design Document |            |
| DFD      | Data Flow Diagram      |            |

####### References

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.0                            |
| 5           | FDD – CM650A HwTq0Meas                                                                                                                                        | See Synergy subproject version |

{% endraw %}