---
layout: default
title: MotDrvDiagc_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**MotDrvDiagc**

**Apr 18, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Sankardu Varadapureddi,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                      |                        |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                                      | **Author**             | **Version** | **Date**    |
| Initial Version                                      | Sankardu Varadapureddi | 1           | 19-Aug-2015 |
| ‘MotDrvDiagcInit1’ design rational updated           | Sankardu Varadapureddi | 2           | 21-Aug-2015 |
| Updating MDD to incorporate the changes in FDD 1.4.0 | Basavaraja Ganeshappa  | 3           | 18-Apr-2016 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 MotDrvDiagc High-Level Description
[6](#motdrvdiagc-high-level-description)](#motdrvdiagc-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of MotDrvDiagc
[7](#graphical-representation-of-motdrvdiagc)](#graphical-representation-of-motdrvdiagc)

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

[5.1.1 Init: MotDrvDiagcInit1
[9](#init-motdrvdiagcinit1)](#init-motdrvdiagcinit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: MotDrvDiagcPer1
[9](#per-motdrvdiagcper1)](#per-motdrvdiagcper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

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
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [10](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale
[10](#design-rationale-2)](#design-rationale-2)

[5.4.1.2 Processing [10](#processing)](#processing)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

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

## Scope

# MotDrvDiagc High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of MotDrvDiagc

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES320A_MotDrvDiagc_Impl/doc/mediax/media/image1.png"
style="width:3.23194in;height:5.32014in"
alt="C:\Users\fzd2x9\Desktop\Capture.PNG" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name            | Resolution | Units    | Value       |
|--------------------------|------------|----------|-------------|
| BITMASK0_CNT_U08         | 1          | Cnt      | 0x01        |
| BITMASK2_CNT_U08         | 1          | Cnt      | 0x04        |
| BITMASK4_CNT_U08         | 1          | Cnt      | 0x10        |
| MOTDRVERRMIN_NANOSEC_F32 | 1          | NoanoSec | 0.0F        |
| MOTDRVERRMAX_NANOSEC_F32 | 1          | NoanoSec | 40000000.0F |

# Software Component Implementation

## Sub-Module Functions

## Init: MotDrvDiagcInit1

## Design Rationale

*Refer FDD for the functionality.*

## Module Outputs

*Refer FDD*

## Per: MotDrvDiagcPer1

## Design Rationale

1.  In blocks ‘MeasdPhaFltChkABC’ and ‘MeasdPhaFltChkDEF’, inputs to
    filters are in integer datatypes. They are converted to float type
    in order to be compatible with filter SW library functions*.*

2.  As per discussion with FDD owner, ‘BitsetStsA’ block sets bit 0 of
    ‘NtcStInfoA’. ‘BitsetStsA1’ sets bit 1 of ‘NtcStInfoA’.
    ‘DetermineBitsetA1’ block resets both bit0 and bit1. Same is
    applicable for phase B (bits 2 and 3) and phase C (bits 4 and 5).

In SW implementation, since NTC state info (NtcStInfoABC_Uls_T_u08) is
initialized to ‘0’, clearing of state bits logic (DetermineBitsetA1) is
not implemented. It is redundant.

Same logic repeated in case of phase D, E and F signals.

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

|                      |                             |         |          |            |
|---------------|---------------------------|------------|---------|-----------|
| **Function Name**    | SetNtcStInfo                | Type    | Min      | Max        |
| **Arguments Passed** | PhaOnTiMeasd_NanoSec_T_u32  | uint32  | 0        | 4294967295 |
|                      | PhaOnTiSumExp_NanoSec_T_u32 | uint32  | 0        | 4294967295 |
|                      | Err_NanoSec_T_f32           | float32 | -3.4E+38 | +3.4E+38   |
|                      | BitMask_Cnt_u08             | uint8   | 0x01     | 0x10       |
|                      | \*NtcStInfo_Uls_T_u08       | uint8   | 0x00     | 0x1F       |
| **Return Value**     | Flt_Uls_T_lgc               | boolean | FALSE    | TRUE       |

## Design Rationale

‘BitMask_Cnt_u08’ takes only 0x01, 0x04 and 0x10.

## Processing

Determines ‘NTC State Info’ for Phase on time signals. Corresponds to
implementation of 'MeasdPhaFltChkABC' and ‘MeasdPhaFltChkDEF’ functional
blocks.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | Process 4.02.01 |
| 2           | MDD Guideline                                                                                                                                                         | Process 4.02.01 |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | Process 4.02.01 |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | Process 4.02.01 |

{% endraw %}