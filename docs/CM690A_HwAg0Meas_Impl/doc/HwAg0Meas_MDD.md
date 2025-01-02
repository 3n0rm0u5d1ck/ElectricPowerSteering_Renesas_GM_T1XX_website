---
layout: default
title: HwAg0Meas_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwAg0Meas**

**Jun 21, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI**

**Chennai** **  
<u>Change History</u>**

|                     |                    |             |              |
|---------------------|--------------------|-------------|--------------|
| **Description**     | **Author**         | **Version** | **Date**     |
| Initial Version     | Selva Sengottaiyan | 1.0         | 21-July-2015 |
| Updated for V1.5.0  | Selva Sengottaiyan | 2.0         | 9-Sep-2015   |
| Updated for v1.6.0  | Selva Sengottaiyan | 4.0         | 23-Dec-2015  |
| Updated for v1.11.0 | TATA               | 5.0         | 21-Jun-2016  |

**  
  
**

**  
**

<u>Table of Contents</u>

1 Introduction 6

1.1 Purpose 6

1.2 Scope 6

2 HwAg0Meas High-Level Description 7

3 Design details of software module 8

3.1 Graphical representation of HwAg0Meas 8

3.2 Data Flow Diagram 8

3.2.1 Component level DFD 8

3.2.2 Function level DFD 8

4 Constant Data Dictionary 9

4.1 Program (fixed) Constants 9

4.1.1 Embedded Constants 9

5 Software Component Implementation 10

5.1.1 Sub-Module Functions 10

5.1.2 Interrupt Service Routines 11

5.1.3 Server Runnable Functions 11

5.1.4 Module Internal (Local) Functions 11

5.1.4.1 Local Function \#1 11

5.1.4.2 Description 12

5.1.5 Transition Functions 12

6 Known Limitations with Design 13

7 UNIT TEST CONSIDERATION 14

Appendix A Abbreviations and Acronyms 15

Appendix B Glossary 16

Appendix C References 17

# Introduction

## Purpose

## Scope

# HwAg0Meas High-Level Description

*Refer to FDD*

# Design details of software module

## Graphical representation of HwAg0Meas

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM690A_HwAg0Meas_Impl/doc/mediax/media/image3.jpeg"
style="width:5.91667in;height:5.0625in"
alt="C:\Users\vignesh.l\Desktop\CM690.JPG" />

## Data Flow Diagram

### Component level DFD

Refer FDD

### Function level DFD

Refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name               | Value          |
|-----------------------------|----------------|
| MAXWAITININ_MICROSEC_U32    | ((uint32)2U)   |
| DATAAVLMAXWAIT_MICROSEC_U32 | ((uint32)300U) |
| COMSTSMAXWAIT_MICROSEC_U32  | ((uint32)5U)   |
| PRTCLFLTMASK_CNT_U32        | 0xFEU          |
| SNSRIDMASK_CNT_U08          | 0x00FU         |
| MSGSTSMASK_CNT_U08          | 0x01U          |
| COMSTSMASK_CNT_U32          | 0x30000000UL   |
| DATAMASK_CNT_U16            | 0xFFF0U        |

# Software Component Implementation

### Sub-Module Functions

#### Initialization sub-module {\_Init()}

HwAg0MeasInit1 (Refer FDD for details)

#### Periodic sub-module {\_Per()}

HwAg0MeasPer1 (Refer FDD for details)

#### Periodic sub-module {\_Per()}

HwAg0MeasPer2 (Refer FDD for details)

#### Periodic sub-module {\_Per()}

HwAg0MeasPer3 (Refer FDD for details)

#### Periodic sub-module {\_Per()}

HwAg0MeasPer4 (Refer FDD for details)

#### Periodic sub-module {\_Per()}

HwAg0MeasPer5 (Refer FDD for details)

Design Rationale:

The implementation brings in the block “HwAg0Final” inside the True
Condition of the “finalAbsAg” as the other error condition will just
retain the previous value and rolling counter will not change. It saves
extra instructions in the implementation to the match the FDD. Final
Functionality is still the same.

#### 

### Interrupt Service Routines

None

### Server Runnable Functions

#### Server Runnable: HwAg0MeasHwAg0AutTrim

Refer FDD for details

#### Server Runnable: HwAg0MeasHwAg0ClrTrim

Refer FDD for details

#### Server Runnable: HwAg0MeasHwAg0ReadTrim

Refer FDD for details

#### Server Runnable: HwAg0MeasHwAg0TrimPrfmdSts

Refer FDD for details

#### Server Runnable: HwAg0MeasHwAg0WrTrim

Refer FDD for details

### Module Internal (Local) Functions

## Local Function \#1

|                      |                      |         |      |     |
|----------------------|----------------------|---------|------|-----|
| **Function Name**    | CalcHwAgIdx          | Type    | Min  | Max |
| **Arguments Passed** | HwAgStep_HwDeg_T_f32 | float32 | -900 | 900 |
|                      |                      |         |      |     |
|                      |                      |         |      |     |
|                      |                      |         |      |     |
| **Return Value**     | Index_Cnt_T_u08      | uint16  | 0    | 22  |

## Description

The implementation deviates from the FDD block “Intpn” block. The
implementation finds the minimum of absolute values of the difference
between HwAg0Step with all the values from the Calibration table and
find the index associated with minimum value of the difference in the
calibration table.

## Local Function \#2

|                      |                             |      |     |     |
|----------------------|-----------------------------|------|-----|-----|
| **Function Name**    | ReadRegister                | Type | Min | Max |
| **Arguments Passed** | RegisterDummyRead_Cnt_T_u32 | N/A  | N/A | N/A |
| **Return Value**     | RegisterDummyRead_Cnt_T_u32 | N/A  | N/A | N/A |

## Design Rationale

This function can be used both for read-and-use and for read-and-discard

### Transition Functions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

-   Roll Over is intentional for

    -   \*Rte_Pim_HwAg0Snsr0ComStsErrCntr()

    -   \*Rte_Pim_HwAg0Snsr0IdErrCntr()

    -   \*Rte_Pim_HwAg0Snsr0IntSnsrErrCntr()

    -   \*Rte_Pim_HwAg0Snsr0NoMsgErrCntr()

    -   \*Rte_Pim_HwAg0Snsr1ComStsErrCntr()

    -   \*Rte_Pim_HwAg0Snsr1IdErrCntr()

    -   \*Rte_Pim_HwAg0Snsr1IntSnsrErrCntr()

    -   \*Rte_Pim_HwAg0Snsr1NoMsgErrCntr()

    -   (\*Rte_Pim_HwAg0PrevRollCnt).

-   Thus counter acts in circular

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description** |
|-----------------------------|-----------------|
|                             |                 |
|                             |                 |

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD - CM690A_HwAg0Meas_Design                                                                                                                                         | See Synergy sub project version |

{% endraw %}