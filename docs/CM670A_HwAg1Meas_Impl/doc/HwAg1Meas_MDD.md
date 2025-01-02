---
layout: default
title: HwAg1Meas_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwAg1Meas**

**Jun 21,2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI**

**CHENNAI**

**  
<u>Change History</u>**

|                               |                    |             |              |
|------------------------|---------------------|--------------|--------------|
| **Description**               | **Author**         | **Version** | **Date**     |
| Initial Version               | Selva Sengottaiyan | 1.0         | 21-July-2015 |
| Updated to v1.2.0 of the FDD  | Selva Sengottaiyan | 2.0         | 11-Sep-15    |
| Updated to v1.4.0 of the FDD  | Selva Sengottaiyan | 3.0         | 23-Dec-15    |
| Updated to v1.11.0 of the FDD | Ramachandran       | 4.0         | 21-Jun-2016  |

**  
**

<u>Table of Contents</u>

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 HwAg1Meas High-Level Description
[5](#hwag1meas-high-level-description)](#hwag1meas-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of HwAg1Meas
[6](#_Toc429723453)](#_Toc429723453)

[3.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [6](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[5.1.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[5.1.2 Interrupt Service Routines
[8](#interrupt-service-routines)](#interrupt-service-routines)

[5.1.3 Server Runnable Functions
[9](#server-runnable-functions)](#server-runnable-functions)

[5.1.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.1.4.1 Local Function \#1 [9](#local-function-1)](#local-function-1)

[5.1.4.2 Description [9](#description)](#description)

[5.1.5 Transition Functions
[10](#transition-functions)](#transition-functions)

[6 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# Introduction

## Purpose

MDD for HwAg1.

## Scope

# HwAg1Meas High-Level Description

*Refer to FDD*

# Design details of software module

## Graphical representation of HwAg1Meas

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM670A_HwAg1Meas_Impl/doc/mediax/media/image3.jpeg"
style="width:5.09375in;height:4.58333in"
alt="C:\Users\vignesh.l\Desktop\CM670.JPG" />

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

HwAg1MeasInit1 (Refer FDD for details)

#### Periodic sub-module {\_Per()}

HwAg1MeasPer1 (Refer FDD for details)

#### Periodic sub-module {\_Per()}

HwAg1MeasPer2 (Refer FDD for details)

#### Periodic sub-module {\_Per()}

HwAg1MeasPer3 (Refer FDD for details)

#### Periodic sub-module {\_Per()}

HwAg1MeasPer4 (Refer FDD for details)

#### Periodic sub-module {\_Per()}

HwAg1MeasPer5 (Refer FDD for details)

Design Rationale:

The implementation brings in the block “HwAg1Final” inside the True
Condition of the “finalAbsAg” as the other error condition will just
retain the previous value and rolling counter will not change. It saves
extra instructions in the implementation to the match the FDD. Final
Functionality is still the same.

#### 

### Interrupt Service Routines

None

### Server Runnable Functions

#### Server Runnable: HwAg1MeasHwAg1AutTrim

Refer FDD for details

#### Server Runnable: HwAg1MeasHwAg1ClrTrim

Refer FDD for details

#### Server Runnable: HwAg1MeasHwAg1ReadTrim

Refer FDD for details

#### Server Runnable: HwAg1MeasHwAg1TrimPrfmdSts

Refer FDD for details

#### Server Runnable: HwAg1MeasHwAg1WrTrim

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
between HwAg1Step with all the values from the Calibration table and
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

    -   \*Rte_Pim_HwAg1Snsr0ComStsErrCntr()

    -   \*Rte_Pim_HwAg1Snsr0IdErrCntr()

    -   \*Rte_Pim_HwAg1Snsr0IntSnsrErrCntr()

    -   \*Rte_Pim_HwAg1Snsr0NoMsgErrCntr()

    -   \*Rte_Pim_HwAg1Snsr1ComStsErrCntr()

    -   \*Rte_Pim_HwAg1Snsr1IdErrCntr()

    -   \*Rte_Pim_HwAg1Snsr1IntSnsrErrCntr()

    -   \*Rte_Pim_HwAg1Snsr1NoMsgErrCntr()

    -   (\*Rte_Pim_HwAg1PrevRollCnt).

-   Thus counter acts in circular

-   

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
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.0                             |
| 5           | FDD - CM670A_HwAg1Meas_Design                                                                                                                                         | See Synergy sub project version |

{% endraw %}