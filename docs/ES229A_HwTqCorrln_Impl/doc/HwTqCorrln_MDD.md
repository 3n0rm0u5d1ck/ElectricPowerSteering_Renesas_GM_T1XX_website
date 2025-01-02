---
layout: default
title: HwTqCorrln_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwTqCorrln**

**April** **14, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Nick Saxton,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                        |            |             |             |
|------------------------|------------|-------------|-------------|
| **Description**        | **Author** | **Version** | **Date**    |
| Initial Version        | SB         | 1.0         | 04-Aug-2015 |
| Updated to FDD v2.1.0  | NS         | 2.0         | 07-Oct-2015 |
| Anomaly EA4#1980 fixed | NS         | 3.0         | 20-Oct-2015 |
| Updated to FDD v3.0.0  | SV         | 4.0         | 14-Apr-2016 |

**  
**

<u>Table of Contents</u>

[1 HwTqCorrln & High-Level Description
[4](#hwtqcorrln-high-level-description)](#hwtqcorrln-high-level-description)

[2 Design details of software module
[5](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of HwTqCorrln
[5](#graphical-representation-of-hwtqcorrln)](#graphical-representation-of-hwtqcorrln)

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

[4.1.1 Init: HwTqCorrlnInit1
[8](#init-hwtqcorrlninit1)](#init-hwtqcorrlninit1)

[4.1.2 Per: HwTqCorrlnPer1
[8](#per-hwtqcorrlnper1)](#per-hwtqcorrlnper1)

[4.1.3 Per: HwTqCorrlnPer2
[8](#per-hwtqcorrlnper2)](#per-hwtqcorrlnper2)

[4.1.4 Per: HwTqCorrlnPer3
[8](#per-hwtqcorrlnper3)](#per-hwtqcorrlnper3)

[4.2 Server Runables [8](#server-runables)](#server-runables)

[4.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 Local Function \#1 [8](#local-function-1)](#local-function-1)

[4.4.1.1 Design Rationale [8](#design-rationale)](#design-rationale)

[4.4.1.2 Processing [8](#processing)](#processing)

[4.4.2 Local Function \#2 [9](#local-function-2)](#local-function-2)

[4.4.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[4.4.2.2 Processing [9](#processing-1)](#processing-1)

[4.5 GLOBAL Function/Macro Definitions
[9](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[10](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[11](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[12](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [13](#glossary)](#glossary)

[Appendix C References [14](#references)](#references)

# HwTqCorrln & High-Level Description

*Refer FDD*

# Design details of software module

*Refer FDD*

## Graphical representation of HwTqCorrln

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES229A_HwTqCorrln_Impl/doc/mediax/media/image2.png"
style="width:3.825in;height:5.00833in" />

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

| Constant Name                           | Resolution | Units    | Value |
|-----------------------------------------|------------|----------|-------|
| Refer .m file                           |            |          |       |
| HWTQCORRLNSTSSIGA_CNT_U08               | 1          | Cnt      | 0x01  |
| HWTQCORRLNSTSSIGB_CNT_U08               | 1          | Cnt      | 0x02  |
| HWTQCORRLNSTSSIGC_CNT_U08               | 1          | Cnt      | 0x04  |
| HWTQCORRLNSTSSIGD_CNT_U08               | 1          | Cnt      | 0x08  |
| MAXSTALL_CNT_U08                        | 1          | Cnt      | 255   |
| HWTQIDPTSIGALL_CNT_U08                  | 1          | Cnt      | 4     |
| HWTQIDPTSIGHALF_CNT_U08                 | 1          | Cnt      | 2     |
| HWTQIDPTSIGNZERO_CNT_U08                | 1          | Cnt      | 0     |
| HWTQCHCORRLNTRAERRMAXLMT\_ HWNWTMTR_F32 | 1          | HWNWTMTR | 10.0  |
| HWTQCHCORRLNTRAERRMINLMT\_ HWNWTMTR_F32 | 1          | HWNWTMTR | -10.0 |

# Software Component Implementation

Refer FDD

## Sub-Module Functions

## Init: HwTqCorrlnInit1

Refer FDD

## Per: HwTqCorrlnPer1

*Refer FDD*

## Per: HwTqCorrlnPer2

*Refer FDD*

## Per: HwTqCorrlnPer3

*Refer FDD*

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                          |          |               |               |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | CorrlnSigAvlChk          | Type     | Min           | Max           |
| **Arguments Passed** | SigRollgCnt_Cnt_T_u08    | uint8    | 0             | 255           |
|                      | SigQlfr_Cnt_T_enum       | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | MaxStallCnt_Cnt_T_u08    | Uint8    | 0             | 255           |
|                      | \* LstRollgCnt_Cnt_T_u08 | uint8    | 0             | 255           |
|                      | \* StallCnt_Cnt_T_u08    | uint8    | 0             | 255           |
| **Return Value**     | SigAvl_Cnt_T_lgc         | boolean  | FALSE         | TRUE          |

## Design Rationale

None

## Processing

Refer FDD CorrSigAvlChkRev1 State flow Chart

## Local Function \#2

|                      |                                     |         |       |      |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | ImdtCorrlnChk                       | Type    | Min   | Max  |
| **Arguments Passed** | Sig1Avl_Cnt_T_lgc                   | Booelan | FALSE | TRUE |
|                      | Sig2Avl_Cnt_T_lgc                   | Boolean | FALSE | TRUE |
|                      | HwTq1_HwNwtMtr_T_f32                | Float32 | -10.0 | 10.0 |
|                      | HwTq2_HwNwtMtr_T_f32                | Float32 | -10.0 | 10.0 |
|                      | ImdtCorrlnChkFailThd_HwNwtMtr_T_f32 | Float32 | 0.0   | 20.0 |
|                      | ImdtCorrlnChkPassThd_HwNwtMtr_T_f32 | Float32 | 0.0   | 20.0 |
|                      | NtcNr_T_enum                        | Enum    | 1     | 511  |
|                      | \*CorrlnSigAPass_Cnt_T_lgc          | Boolean | FALSE | TRUE |
|                      | \*CorrlnSigBPass_Cnt_T_lgc          | Boolean | FALSE | TRUE |
|                      | \*ImdtCorrlnChk_Cnt_T_lgc           | Boolean | FALSE | TRUE |
| **Return Value**     | ChAImdtCorrlnChk_Cnt_T_lgc          | boolean | FALSE | TRUE |

## Design Rationale

None

## Processing

Refer FDD ImdtCorrlnChk block

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | Process 04.02.00               |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | Process 04.02.00               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | Process 04.02.00               |
| 5           | FDD – ES229A_HwTqCorrln_Design                                                                                                                                        | See Synergy SubProject version |

{% endraw %}