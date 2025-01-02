---
layout: default
title: MotAgArbn_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**MotAgArbn**

**Aug 5, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Spandana Balani,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |            |             |             |
|-----------------|------------|-------------|-------------|
| **Description** | **Author** | **Version** | **Date**    |
| Initial Version | SB         | 1.0         | 05-Aug-2015 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 MotAgArbn & High-Level Description
[6](#motagarbn-high-level-description)](#motagarbn-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of MotAgArbn
[7](#graphical-representation-of-motagarbn)](#graphical-representation-of-motagarbn)

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

[5.1.1 Init: MotAgArbnInit1
[9](#init-motagarbninit1)](#init-motagarbninit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: MotAgArbnPer1 [9](#per-motagarbnper1)](#per-motagarbnper1)

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
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [9](#local-function-1)](#local-function-1)

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

# MotAgArbn & High-Level Description

*Refer FDD.*

# Design details of software module

*\<The Data Flow Diagrams should be created in the absence of this
representation with the FDD.\>*

## Graphical representation of MotAgArbn 

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES248A_MotAgArbn_Impl/doc/mediax/media/image1.png"
style="width:1.875in;height:1.61458in" />

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

| Constant Name             | Resolution | Units | Value |
|---------------------------|------------|-------|-------|
| Refer .m file             |            |       |       |
| CORRLNSTSMASKSIGA_CNT_U08 | 1          | Cnt   | 0x01  |
| CORRLNSTSMASKSIGB_CNT_U08 | 1          | Cnt   | 0x02  |
| MAXSTALLCNTR_CNT_U08      | 1          | Cnt   | 255   |

# Software Component Implementation

## Sub-Module Functions

## Init: MotAgArbnInit1

## Design Rationale

Init1 function is created so that it will allow a RTE model to be
created in the AUTOSAR tools which allows Per-Instance Memory and
calibration definition needs. The initialization function is doing
nothing

## Module Outputs

*None*

## Per: MotAgArbnPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*MotCtrlMotAgAMecl_MotRev_T_u0p16 = MOTCTRLMGR_MotCtrlMotAgAMecl;*

*MotCtrlMotAgBMecl_MotRev_T_u0p16 = MOTCTRLMGR_MotCtrlMotAgBMecl;*

*MotCtrlMotAgMeclCorrlnSt_Cnt_T_u08 =
MOTCTRLMGR_MotCtrlMotAgMeclCorrlnSt;*

*MotCtrlMotAgAMeclRollgCntr_Cnt_T_u08 =
MOTCTRLMGR_MotCtrlMotAgAMeclRollgCntr;*

*MotCtrlMotAgBMeclRollgCntr_Cnt_T_u08 =
MOTCTRLMGR_MotCtrlMotAgBMeclRollgCntr;*

*MotCtrlMotAgAMeclQlfr_T_enum = MOTCTRLMGR_MotCtrlMotAgAMeclQlfr;*

*MotCtrlMotAgBMeclQlfr_T_enum = MOTCTRLMGR_MotCtrlMotAgBMeclQlfr;*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*MOTCTRLMGR_MotCtrlMotAgMecl = MotCtrlMotAgMecl_MotRev_T_u0p16*

## Server Runables 

None

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                          |          |               |               |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | SigAvlChkRev             | Type     | Min           | Max           |
| **Arguments Passed** | SigCorrChk_Cnt_T_u08     | uint8    | 0             | 255           |
|                      | SigRollgCnt_Cnt_T_u08    | uint8    | 0             | 255           |
|                      | SigQlfr_Cnt_T_enum       | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | \* LstRollgCnt_Cnt_T_u08 | uint8    | 0             | 255           |
|                      | \* StallCnt_Cnt_T_u08    | uint8    | 0             | 255           |
| **Return Value**     | SigAvl_Cnt_T_lgc         | boolean  | 0             | 1             |

## Design Rationale

None

## Processing

Refer FDD SigAvlChkRev2 State flow Chart

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.0                            |
| 5           | FDD – ES248A_MotAgArbn_Design                                                                                                                                         | See Synergy Subproject verison |

{% endraw %}