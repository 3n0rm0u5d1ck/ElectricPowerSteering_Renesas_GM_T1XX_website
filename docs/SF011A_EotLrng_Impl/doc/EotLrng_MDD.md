---
layout: default
title: EotLrng_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**EotLrng (SF011A)**

**DEC 05, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI,**

> **CHENNAI, INDIA**

**<u>Change</u>** History

|                           |                   |             |             |
|---------------------------|-------------------|-------------|-------------|
| **Description**           | **Author**        | **Version** | **Date**    |
| Initial Version           | Akhil Krishna N D | 1.0         | 30-Sep-2015 |
| Updated for v2.0.0 of FDD | Nick Saxton       | 2.0         | 19-May-2016 |
| Updated for v2.1.0 of FDD | Nick Saxton       | 3.0         | 16-Jun-2016 |
| Updated for v3.1.0 of FDD | TATA              | 4.0         | 05-Dec-2016 |

<u>Table of Contents</u>

[**1** **End of Travel Learning & High-Level Description**
**5**](#eotlrng-sf011a-high-level-description)

[2 Design details of software module
6](#design-details-of-software-module)

[2.1 Graphical representation of End of Travel Learning
6](#graphical-representation-of-eotlrng-sf011a)

[2.2 Data Flow Diagram 6](#data-flow-diagram)

[2.2.1 Component level DFD 6](#component-level-dfd)

[2.2.2 Function level DFD 6](#function-level-dfd)

[3 Constant Data Dictionary 7](#constant-data-dictionary)

[3.1 Program (fixed) Constants 7](#program-fixed-constants)

[3.1.1 Embedded Constants 7](#embedded-constants)

[4 Software Component Implementation
8](#software-component-implementation)

[4.1 Sub-Module Functions 8](#sub-module-functions)

[4.1.1 Init: EotLrngInit1 8](#init-eotlrnginit1)

[4.1.1.1 Design Rationale 8](#design-rationale)

[4.1.1.2 Module Outputs 8](#module-outputs)

[4.1.2 Per: EotLrngPer1 8](#per-eotlrngper1)

[4.1.2.1 Design Rationale 8](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
8](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function)……… 8](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
8](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runnable 8](#server-runnable)

[4.2.1 SerlComRstEot 8](#serlcomrsteot)

[4.2.1.1 Design Rationale 8](#design-rationale-2)

[4.2.1.2 (Processing of function)……… 8](#processing-of-function-1)

[4.3 Interrupt Functions 8](#interrupt-functions)

[4.3.1 RtnMaxHwAgCwAndCcw 9](#rtnmaxhwagcwandccw)

[4.3.1.1 Design Rationale 9](#design-rationale-3)

[4.3.1.2 (Processing of function)……… 9](#processing-of-function-2)

[4.4 Interrupt Functions 9](#interrupt-functions-1)

[4.4.1 RstMaxHwAgCwAndCcw 9](#rstmaxhwagcwandccw)

[4.4.1.1 Design Rationale 9](#design-rationale-4)

[4.4.1.2 (Processing of function)……… 9](#processing-of-function-3)

[4.5 Interrupt Functions 9](#interrupt-functions-2)

[4.5.1.3 (Processing of function)……… 9](#__RefHeading___Toc468712057)

[4.6 Interrupt Functions 9](#__RefHeading___Toc468712058)

[4.6.1.3 (Processing of function)……… 9](#__RefHeading___Toc468712059)

[4.7 Interrupt Functions 9](#__RefHeading___Toc468712060)

[4.7.1.3 (Processing of function)……… 10](#__RefHeading___Toc468712061)

[4.8 Interrupt Functions 10](#__RefHeading___Toc468712062)

[4.9 Module Internal (Local) Functions
10](#module-internal-local-functions)

[4.9.1 Local Function \#1 10](#local-function-1)

[4.9.1.1 Design Rationale 10](#design-rationale-8)

[4.9.1.2 Processing 10](#processing)

[4.9.2 Local Function \#2 10](#local-function-2)

[4.9.2.1 Design Rationale 11](#design-rationale-9)

[4.9.2.2 Processing 11](#processing-1)

[4.10 GLOBAL Function/Macro Definitions
11](#global-functionmacro-definitions)

[4.10.1 GLOBAL Function \#1 11](#global-function-1)

[4.10.1.1 Design Rationale 11](#design-rationale-10)

[4.10.1.2 Processing 11](#processing-2)

[5 Known Limitations with Design 12](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION 13](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 14](#abbreviations-and-acronyms)

[Appendix B Glossary 15](#glossary)

[Appendix C References 16](#references)

# EotLrng (SF011A)& High-Level Description

Please refer FDD.

# Design details of software module

## Graphical representation of EotLrng (SF011A)

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF011A_EotLrng_Impl/doc/mediax/media/image2.jpeg"
style="width:4.11458in;height:5.3125in" />

## Data Flow Diagram

Please refer FDD.

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                      |            |       |       |
|----------------------|------------|-------|-------|
| Constant Name        | Resolution | Units | Value |
| Please refer .m file |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: EotLrngInit1

## Design Rationale

None

## Module Outputs

Please refer FDD.

## Per: EotLrngPer1

## Design Rationale

None

## Store Module Inputs to Local copies

Please refer FDD.

##  (Processing of function)………

Please refer FDD and design rationale noted above.

## Store Local copy of outputs into Module Outputs

Please refer FDD.

## Server Runnable 

##  SerlComRstEot 

## Design Rationale

None

##  (Processing of function)………

Please refer SerlComRstEot block in FDD

## Interrupt Functions

None

##  RtnMaxHwAgCwAndCcw 

## Design Rationale

None

##  (Processing of function)………

Please refer RtnMaxHwAgCwAndCcw block in FDD

## Interrupt Functions

None

##  RstMaxHwAgCwAndCcw 

## Design Rationale

None

##  (Processing of function)………

Please refer RstMaxHwAgCwAndCcw block in FDD

## Interrupt Functions

None

#### GetHwAgOverTrvlCnt

#### Design Rationale

None

##  (Processing of function)………

Please refer GetHwAgOverTrvlCnt block in FDD

## Interrupt Functions

None

#### RstHwAgOverTrvlCnt

#### Design Rationale

None

##  (Processing of function)………

Please refer RstHwAgOverTrvlCnt block in FDD

## Interrupt Functions

None

#### SetHwAgOverTrvlCnt

#### Design Rationale

None

##  (Processing of function)………

Please refer SetHwAgOverTrvlCnt block in FDD

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                              |         |       |      |
|----------------------|------------------------------|---------|-------|------|
| **Function Name**    | LrngEotCmplSts               | Type    | Min   | Max  |
| **Arguments Passed** | HwAgAuthy_Uls_T_f32          | float32 | 0     | 1    |
|                      | HwTq_HwNwtMtr_T_f32          | float32 | -10   | 10   |
|                      | MotVelCrf_MotRadPerSec_T_f32 | float32 | -1350 | 1350 |
| **Return Value**     | None                         | \-      | \-    | \-   |

## Design Rationale

To reduce the static path count

## Processing

Please refer to the “LrngEotCmplSts” block of the Simulink model of the
design.

## Local Function \#2

|                      |                            |         |       |      |
|----------------------|----------------------------|---------|-------|------|
| **Function Name**    | ChkEotSigForNtc            | Type    | Min   | Max  |
| **Arguments Passed** | HwAgEotSig0Avl_Cnt_T_lgc   | boolean | FALSE | TRUE |
|                      | HwAgEotSig1Avl_Cnt_T_lgc   | boolean | FALSE | TRUE |
|                      | HwAgEotSig0Cw_HwDeg_T_f32  | float32 | 0     | 900  |
|                      | HwAgEotSig0Ccw_HwDeg_T_f32 | float32 | -900  | 0    |
|                      | HwAgEotSig1Cw_HwDeg_T_f32  | float32 | 0     | 900  |
|                      | HwAgEotSig1Ccw_HwDeg_T_f32 | float32 | -900  | 0    |
| **Return Value**     | None                       | \-      | \-    | \-   |

## Design Rationale

To reduce the static path count

## Processing

Please refer to the “ChkEotSigForNtc” block of the Simulink model of the
design.

## GLOBAL Function/Macro Definitions

## GLOBAL Function \#1

None

## Design Rationale

None

## Processing

None

# Known Limitations with Design

> None.

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

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.1                             |
| 5           | FDD : SF011A_EotLrng_Design                                                                                                                                   | See Synergy sub project version |

{% endraw %}