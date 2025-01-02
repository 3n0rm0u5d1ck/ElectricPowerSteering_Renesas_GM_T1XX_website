---
layout: default
title: GmRoadWhlInQlfr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**GmRoadWhlInQlfr**

**March 2, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Nick Saxton,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |            |             |             |
|-----------------|------------|-------------|-------------|
| **Description** | **Author** | **Version** | **Date**    |
| Initial Version | N. Saxton  | 1.0         | 02-Mar-2016 |

<u>Table of Contents</u>

[1 GmRoadWhlInQlfr High-Level Description
[5](#gmroadwhlinqlfr-high-level-description)](#gmroadwhlinqlfr-high-level-description)

[2 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of GmRoadWhlInQlfr
[6](#graphical-representation-of-gmroadwhlinqlfr)](#graphical-representation-of-gmroadwhlinqlfr)

[2.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [6](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[4.1.1 Init: GmRoadWhlInQlfrInit1
[8](#init-gmroadwhlinqlfrinit1)](#init-gmroadwhlinqlfrinit1)

[4.1.1.1 Design Rationale [8](#design-rationale)](#design-rationale)

[4.1.1.2 Module Outputs [8](#module-outputs)](#module-outputs)

[4.1.2 Per: GmRoadWhlInQlfrPer1
[8](#per-gmroadwhlinqlfrper1)](#per-gmroadwhlinqlfrper1)

[4.1.2.1 Design Rationale [8](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function)………
[8](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runables [8](#server-runables)](#server-runables)

[4.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 Local Function \#1 [8](#local-function-1)](#local-function-1)

[4.4.1.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[4.4.1.2 Processing [9](#processing)](#processing)

[4.4.2 Local Function \#2 [9](#local-function-2)](#local-function-2)

[4.4.2.1 Design Rationale [9](#design-rationale-3)](#design-rationale-3)

[4.4.2.2 Processing [9](#processing-1)](#processing-1)

[4.4.3 Local Function \#3 [9](#local-function-3)](#local-function-3)

[4.4.3.1 Design Rationale
[10](#design-rationale-4)](#design-rationale-4)

[4.4.3.2 Processing [10](#processing-2)](#processing-2)

[4.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# GmRoadWhlInQlfr High-Level Description

*Refer FDD*

# Design details of software module

## Graphical representation of GmRoadWhlInQlfr

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CF018A_GmRoadWhlInQlfr_Impl/doc/mediax/media/image1.PNG"
style="width:3.15669in;height:3.64634in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

Refer FDD

### Function level DFD

Refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

Refer DataDict.m for constants

# Software Component Implementation

## Sub-Module Functions

Refer FDD

## Init: GmRoadWhlInQlfrInit1

## Design Rationale

*Refer FDD*

## Module Outputs

*Refer FDD*

## Per: GmRoadWhlInQlfrPer1

## Design Rationale

Refer FDD

## Store Module Inputs to Local copies

Refer FDD

##  (Processing of function)………

Refer FDD

## Store Local copy of outputs into Module Outputs

Refer FDD

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                       |         |       |           |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CalcLeWhlFrqAndFrqVld                 | Type    | Min   | Max       |
| **Arguments Passed** | WhlRotlStsTiStampResl_SecPerCnt_T_f32 | Float32 | 2e-09 | 4.084e-06 |
|                      | WhlLeDstPlsCntr_Cnt_T_u16             | Uint16  | 0     | 1023      |
|                      | WhlLeDstTiStamp_Cnt_T_u16             | Uint16  | 0     | 65535     |
|                      | WhlPlsPerRev_CntPerRoadWhlRev_T_u08   | Uint08  | 1     | 127       |
|                      | \*LeWhlFrqVld_Cnt_T_logl              | Boolean | FALSE | TRUE      |
|                      | \*WhlLeFrq_Hz_T_f32                   | Float32 | 0.01  | 60        |
|                      | \*LeFrqOutOfRng_Cnt_T_logl            | Boolean | FALSE | TRUE      |
|                      | \*LeFrqChgOutOfRng_Cnt_T_logl         | Boolean | FALSE | TRUE      |
|                      | \*LeWhlDiagFlg_Cnt_T_logl             | Boolean | FALSE | TRUE      |

*\** LeWhlFrqVld_Cnt_T_logl, \* WhlLeFrq_Hz_T_f32,
\*LeFrqOutOfRng_Cnt_T_logl, \*LeFrqChgOutOfRng_Cnt_T_logl and
\*LeWhlDiagFlg_Cnt_T_logl *are outputs of this function*

## Design Rationale

Implementation of "Chk Curr and Prev LeWhlDstTiStamp" block

## Processing

Refer FDD

## Local Function \#2

|                      |                                       |         |       |           |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CalcRiWhlFrqAndFrqVld                 | Type    | Min   | Max       |
| **Arguments Passed** | WhlRotlStsTiStampResl_SecPerCnt_T_f32 | Float32 | 2e-09 | 4.084e-06 |
|                      | WhlRiDstPlsCntr_Cnt_T_u16             | Uint16  | 0     | 1023      |
|                      | WhlRiDstTiStamp_Cnt_T_u16             | Uint16  | 0     | 65535     |
|                      | WhlPlsPerRev_CntPerRoadWhlRev_T_u08   | Uint08  | 1     | 127       |
|                      | \*RiWhlFrqVld_Cnt_T_logl              | Boolean | FALSE | TRUE      |
|                      | \*WhlRiFrq_Hz_T_f32                   | Float32 | 0.01  | 60        |
|                      | \*RiFrqOutOfRng_Cnt_T_logl            | Boolean | FALSE | TRUE      |
|                      | \*RiFrqChgOutOfRng_Cnt_T_logl         | Boolean | FALSE | TRUE      |
|                      | \*RiWhlDiagFlg_Cnt_T_logl             | Boolean | FALSE | TRUE      |

*\** RiWhlFrqVld_Cnt_T_logl, \* WhlRiFrq_Hz_T_f32,
\*RiFrqOutOfRng_Cnt_T_logl, \*RiFrqChgOutOfRng_Cnt_T_logl and
\*RiWhlDiagFlg_Cnt_T_logl *are outputs of this function*

## Design Rationale

Implementation of "Chk Curr and Prev RiWhlDstTiStamp" block

## Processing

Refer FDD

## Local Function \#3

|                      |                             |         |       |      |
|----------------------|-----------------------------|---------|-------|------|
| **Function Name**    | NTCDiag                     | Type    | Min   | Max  |
| **Arguments Passed** | LeWhlDiagFlag_Cnt_T_logl    | Boolean | FALSE | TRUE |
|                      | RiWhlDiagFlag_Cnt_T_logl    | Boolean | FALSE | TRUE |
|                      | LeFrqOutOfRng_Cnt_T_logl    | Boolean | FALSE | TRUE |
|                      | RiFrqOutOfRng_Cnt_T_logl    | Boolean | FALSE | TRUE |
|                      | LeFrqChgOutOfRng_Cnt_T_logl | Boolean | FALSE | TRUE |
|                      | RiFrqChgOutOfRng_Cnt_T_logl | Boolean | FALSE | TRUE |

## Design Rationale

Implementation of "NTC Diag" block and immediately preceding logic

## Processing

Refer FDD

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

-   None

# UNIT TEST CONSIDERATION

-   None

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

| **Ref. \#** | **Title**                                                                                                                                                               | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                      | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                           | EA4 01.00.00                   |
| 3           | EA4 [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 01.00.00                       |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc)   | 2.1                            |
| 5           | CF018A_GmRoadWhlInQlfr_Design                                                                                                                                           | See Synergy subproject version |

{% endraw %}