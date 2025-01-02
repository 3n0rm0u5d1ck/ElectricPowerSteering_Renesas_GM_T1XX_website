---
layout: default
title: HwAgTrajGenn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwAgTrajGenn**

**Feb 4, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Sankardu Varadapureddi,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |                        |             |            |
|-----------------|------------------------|-------------|------------|
| **Description** | **Author**             | **Version** | **Date**   |
| Initial Version | Sankardu Varadapureddi | 1           | 4-Feb-2016 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 HwAgTrajGenn High-Level Description
[6](#hwagtrajgenn-high-level-description)](#hwagtrajgenn-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of HwAgTrajGenn
[7](#graphical-representation-of-hwagtrajgenn)](#graphical-representation-of-hwagtrajgenn)

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

[5.1.1 Init: None [9](#init-hwagtrajgenninit1)](#init-hwagtrajgenninit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: HwAgTrajGennPer1
[9](#per-hwagtrajgennper1)](#per-hwagtrajgennper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.2.1 SetTrajTarPrm_Oper [9](#settrajtarprm_oper)](#settrajtarprm_oper)

[5.2.1.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.2.1.2 (Processing of function)………
[9](#processing-of-function-1)](#processing-of-function-1)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [9](#local-function-1)](#local-function-1)

[5.4.1.1 Description [10](#description)](#description)

[5.4.2 Local Function \#2 [10](#local-function-2)](#local-function-2)

[5.4.2.1 Description [10](#description-1)](#description-1)

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

# HwAgTrajGenn High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of HwAgTrajGenn

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF021A_HwAgTrajGenn_Impl/doc/mediax/media/image1.png"
style="width:2.50833in;height:2.51667in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

| Constant Name          | Resolution | Units | Value |
|------------------------|------------|-------|-------|
| ONEOVERTWOMPLR_ULS_F32 | 1          | Cnt   | 0.5   |

For other constants, refer .m file.

#### Local Constants

# Software Component Implementation

## Sub-Module Functions

## Init: HwAgTrajGennInit1

## Design Rationale

Dummy init function created to meet coding standards.

## Module Outputs

## Per: HwAgTrajGennPer1

## Design Rationale

Refer FDD for the overall functionality.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

## SetTrajTarPrm_Oper

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                |         |       |      |     |
|--------------|-----------------------|-------------|------------|--|-----------|
| **Function Name**    | HwAgTrajInitVaris              | Type    | Min   |      | Max |
| **Arguments Passed** | HwPosn_HwDeg_T_f32             | float32 | -1440 | 1440 |     |
|                      | CalcFlg_Cnt_T_logl             | boolean | FALSE | TRUE |     |
|                      | HwATar_HwDegPerSecPerSec_T_f32 | float32 | 10    | 2000 |     |
|                      | HwAgTar_HwDeg_T_f32            | float32 | -800  | 800  |     |
|                      | HwVelTar_HwDegPerSec_T_f32     | float32 | 10    | 1000 |     |
| **Return Value**     | None                           |         |       |      |     |

## Description

"Initialize Variables" block implementation.

## Local Function \#2

|                      |                               |         |       |      |     |
|--------------|-----------------------|-------------|------------|--|-----------|
| **Function Name**    | HwAgTrajGenSigs               | Type    | Min   |      | Max |
| **Arguments Passed** | HwPosn_HwDeg_T_f32            | float32 | -1440 | 1440 |     |
|                      | CalcFlg_Cnt_T_logl            | boolean | FALSE | TRUE |     |
| **Return Value**     | HwAgTrakgServoCmd_HwDeg_T_f32 | float32 | -1440 | 1440 |     |

## Description

"Generate Signals" block implementation.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None.

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
| 2           | MDD Guideline                                                                                                                                                         | Process 4.02.01                 |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | Process 4.02.01                 |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | Process 4.02.01                 |
| 5           | FDD : SF021A\_ HwAgTrajGenn_Design                                                                                                                                    | See Synergy sub project version |

{% endraw %}