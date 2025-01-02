---
layout: default
title: GmStrtStop_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**GmStrtStop**

**June 27, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Nick Saxton**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                     |                        |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                     | **Author**             | **Version** | **Date**    |
| Initial Version                     | Sankardu Varadapureddi | 1           | 1-Oct-2015  |
| Added local function GetTmrElpsdThd | Nick Saxton            | 2           | 4-Feb-2016  |
| Updated for FDD v1.3.0              | Nick Saxton            | 3           | 27-Jun-2016 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 GmStrtStop High-Level Description
[6](#gmstrtstop-high-level-description)](#gmstrtstop-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of GmStrtStop
[7](#graphical-representation-of-gmstrtstop)](#graphical-representation-of-gmstrtstop)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [7](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[8](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[8](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [8](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[9](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[9](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: None [9](#init-none)](#init-none)

[5.1.2 Per: GmStrtStopPer1
[9](#per-gmstrtstopper1)](#per-gmstrtstopper1)

[5.1.2.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [9](#local-function-1)](#local-function-1)

[5.4.1.1 Description [9](#description)](#description)

[5.4.2 Local Function \#2 [9](#local-function-2)](#local-function-2)

[5.4.2.1 Description [10](#description-1)](#description-1)

[5.4.3 Local Function \#3 [10](#local-function-3)](#local-function-3)

[5.4.3.1 Description [10](#description-2)](#description-2)

[5.4.4 Local Function \#4 [10](#local-function-4)](#local-function-4)

[5.4.4.1 Description [10](#description-3)](#description-3)

[5.4.5 Local Function \#5 [11](#local-function-5)](#local-function-5)

[5.4.5.1 Description [11](#description-4)](#description-4)

[5.4.6 Local Function \#6 [11](#local-function-6)](#local-function-6)

[5.4.6.1 Description [11](#description-5)](#description-5)

[5.4.6.2 Design Rationale
[11](#design-rationale-1)](#design-rationale-1)

[5.5 GLOBAL Function/Macro Definitions
[11](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[13](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[14](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[15](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [16](#glossary)](#glossary)

[Appendix C References [17](#references)](#references)

# Introduction

## Purpose

## Scope

# GmStrtStop High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of GmStrtStop

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CF012A_GmStrtStop_Impl/doc/mediax/media/image2.PNG"
style="width:3.01693in;height:4.24203in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

Refer .m file

# Software Component Implementation

## Sub-Module Functions

## Init: None

## Per: GmStrtStopPer1

## Design Rationale

Refer FDD for the overall functionality.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                     |         |     |     |     |
|----------|-------------------------------------------|--------|------|--|------|
| **Function Name**    | DtrmnRateLim                        | Type    | Min |     | Max |
| **Arguments Passed** | ActSt_Cnt_T_u08                     | uint8   | 0   | 5   |     |
|                      | VehStrtStopSt_Cnt_T_u08             | uint8   | 0   | 5   |     |
| **Return Value**     | VehStrtStopRampRate_UlsPerSec_T_f32 | float32 | 0   | 5   |     |

## Description

Determination of 'VehStrtStopRampRate_UlsPerSec_T_f32' for different
mode transitions.

## Local Function \#2

|                      |                                    |         |     |      |     |
|-----------|------------------------------------|----------|--------|--|--------|
| **Function Name**    | NormModExitCdnsChk                 | Type    | Min |      | Max |
| **Arguments Passed** | EngSpd_Rpm_T_f32                   | float32 | 0   | 5110 |     |
|                      | VehSpd_Kph_T_f32                   | float32 | 0   | 511  |     |
|                      | \*VehStrtStopSt_Cnt_T_u08          | uint8   | 0   | 5    |     |
|                      | \*VehStrtStopMotTqCmdSca_Uls_T_f32 | float32 | 0   | 1    |     |
| **Return Value**     | None                               |         |     |      |     |

## Description

This function validates conditions for all state transitions from
'Normal mode'. ‘\*VehStrtStopSt_Cnt_T_u08’ and
‘\*VehStrtStopMotTqCmdSca_Uls_T_f32’ are outputs of this function.

## Local Function \#3

|                      |                                    |         |       |      |     |
|-----------|------------------------------------|----------|--------|--|--------|
| **Function Name**    | Inter1ModExitCdnsChk               | Type    | Min   |      | Max |
| **Arguments Passed** | EngSpd_Rpm_T_f32                   | float32 | 0     | 5110 |     |
|                      | VehSpd_Kph_T_f32                   | float32 | 0     | 511  |     |
|                      | HwVel_HwRadPerSec_T_f32            | float32 | -42   | 42   |     |
|                      | HwTq_HwNwtMtr_T_f32                | float32 | -10   | 10   |     |
|                      | ToStopModFlg_T_logl                | boolean | FALSE | TRUE |     |
|                      | \*VehStrtStopSt_Cnt_T_u08          | uint8   | 0     | 5    |     |
|                      | \*VehStrtStopMotTqCmdSca_Uls_T_f32 | float32 | 0     | 1    |     |
| **Return Value**     | None                               |         |       |      |     |

## Description

This function validates conditions for all state transitions from
‘Intermediate 1 mode’.

‘\*VehStrtStopSt_Cnt_T_u08’ and ‘\*VehStrtStopMotTqCmdSca_Uls_T_f32’ are
outputs of this function.

## Local Function \#4

|                      |                                    |         |     |      |     |
|-----------|------------------------------------|----------|--------|--|--------|
| **Function Name**    | StopModExitCdnsChk                 | Type    | Min |      | Max |
| **Arguments Passed** | EngSpd_Rpm_T_f32                   | float32 | 0   | 5110 |     |
|                      | VehSpd_Kph_T_f32                   | float32 | 0   | 511  |     |
|                      | \*VehStrtStopSt_Cnt_T_u08          | uint8   | 0   | 5    |     |
|                      | \*VehStrtStopMotTqCmdSca_Uls_T_f32 | float32 | 0   | 1    |     |
| **Return Value**     | None                               |         |     |      |     |

## Description

This function validates conditions for all state transitions from ‘Stop
mode’. ‘\*VehStrtStopSt_Cnt_T_u08’ and
‘\*VehStrtStopMotTqCmdSca_Uls_T_f32’ are outputs of this function.

## Local Function \#5

|                      |                                    |         |       |      |     |
|-----------|------------------------------------|----------|--------|--|--------|
| **Function Name**    | Inter2ModExitCdnsChk               | Type    | Min   |      | Max |
| **Arguments Passed** | EngSpd_Rpm_T_f32                   | float32 | 0     | 5110 |     |
|                      | VehSpd_Kph_T_f32                   | float32 | 0     | 511  |     |
|                      | HwVel_HwRadPerSec_T_f32            | float32 | -42   | 42   |     |
|                      | HwTq_HwNwtMtr_T_f32                | float32 | -10   | 10   |     |
|                      | ToStopModFlg_T_logl                | boolean | FALSE | TRUE |     |
|                      | \*VehStrtStopSt_Cnt_T_u08          | uint8   | 0     | 5    |     |
|                      | \*VehStrtStopMotTqCmdSca_Uls_T_f32 | float32 | 0     | 1    |     |
| **Return Value**     | None                               |         |       |      |     |

## Description

This function validates conditions for all state transitions from
'Intermediate 2 mode'.

‘\*VehStrtStopSt_Cnt_T_u08’ and ‘\*VehStrtStopMotTqCmdSca_Uls_T_f32’ are
outputs of this function.

## Local Function \#6

|                      |                          |         |       |            |     |
|--------------|---------------------|--------------|------------|--|-----------|
| **Function Name**    | GetTmrElpsdThd           | Type    | Min   |            | Max |
| **Arguments Passed** | StrtStopStChk_Cnt_T_u08  | uint8   | 0     | 5          |     |
|                      | \*RefTmr_Cnt_T_u32       | uint32  | 0     | 4294967295 |     |
|                      | ModTmrThd_MilliSec_T_f32 | float32 | 0     | 5000       |     |
| **Return Value**     | TmrElpsdThd_Cnt_T_logl   | boolean | FALSE | TRUE       |     |

## Description

This function determines whether exit conditions for states Mod1 and
Mod2 have been valid for a long enough period of time.

## Design Rationale

This function was created to avoid duplicate code and lower static path
count and cyclomatic complexity.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

# UNIT TEST CONSIDERATION

None

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | EA4 01.00.00                    |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD : CF012A\_ GmStrtStop_Design                                                                                                                                      | See Synergy sub project version |

{% endraw %}