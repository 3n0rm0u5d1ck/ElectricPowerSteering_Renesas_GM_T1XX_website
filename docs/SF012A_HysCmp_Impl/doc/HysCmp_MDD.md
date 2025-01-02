---
layout: default
title: HysCmp_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HysCmp**

**Jan** **04, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Matthew Leser,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                |            |             |             |
|--------------------------------|------------|-------------|-------------|
| **Description**                | **Author** | **Version** | **Date**    |
| Initial Version                | SB         | 1.0         | 04-Aug-2015 |
| Updated per Design vers. 1.2.0 | ML         | 2.0         | 04-Jan-2017 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 HysCmp & High-Level Description
[6](#hyscmp-high-level-description)](#hyscmp-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of HysCmp
[7](#graphical-representation-of-hyscmp)](#graphical-representation-of-hyscmp)

[3.2 Data Flow Diagram [8](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[8](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [8](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[9](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[9](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [9](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[10](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[10](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: HysCmpInit1 [10](#init-hyscmpinit1)](#init-hyscmpinit1)

[5.1.2 Per: HysCmpPer1 [10](#per-hyscmpper1)](#per-hyscmpper1)

[5.2 Server Runables [10](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [10](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale [10](#design-rationale)](#design-rationale)

[5.4.1.2 Processing [10](#processing)](#processing)

[5.4.2 Local Function \#1
[10](#local-function-1-1)](#local-function-1-1)

[5.4.2.1 Design Rationale
[10](#design-rationale-1)](#design-rationale-1)

[5.4.2.2 Processing [11](#processing-1)](#processing-1)

[5.4.3 Local Function \#1
[11](#local-function-1-2)](#local-function-1-2)

[5.4.3.1 Design Rationale
[11](#design-rationale-2)](#design-rationale-2)

[5.4.3.2 Processing [11](#processing-2)](#processing-2)

[5.5 GLOBAL Function/Macro Definitions
[11](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[12](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[13](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[14](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [15](#glossary)](#glossary)

[Appendix C References [16](#references)](#references)

# Introduction

## Purpose

## Scope

#  HysCmp & High-Level Description

*Refer FDD*

# Design details of software module

*Refer FDD*

## Graphical representation of HysCmp

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF012A_HysCmp_Impl/doc/mediax/media/image2.png"
style="width:3.83333in;height:6.83333in" />

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

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| Refer .m file |            |       |       |

# Software Component Implementation

Refer FDD

## Sub-Module Functions

## Init: HysCmpInit1

Refer FDD

## Per: HysCmpPer1

*Refer FDD*

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                           |         |     |     |
|----------------------|---------------------------|---------|-----|-----|
| **Function Name**    | MoreCmp                   | Type    | Min | Max |
| **Arguments Passed** | TqChg_HwNwtMtr_T_f32      | Float32 | 0   | 20  |
|                      | \*RiseXPtr_HwNwtMtr_T_f32 | Float32 | 0   | 1   |
|                      | \*RiseXFac_HwNwtMtr_T_f32 | Float32 | 0   | 1   |
| **Return Value**     | RiseY_Uls_T_f32           | Float32 | 0   | 1   |

## Design Rationale

None

## Processing

Refer ‘MoreCmp’ block in Simulink model

## Local Function \#1

|                      |                           |         |     |     |
|----------------------|---------------------------|---------|-----|-----|
| **Function Name**    | LessCmp                   | Type    | Min | Max |
| **Arguments Passed** | TqChg_HwNwtMtr_T_f32      | Float32 | 0   | 20  |
|                      | \*RiseYPtr_Uls_T_f32      | Float32 | 0   | 1   |
|                      | \*RiseXFac_HwNwtMtr_T_f32 | Float32 | 0   | 1   |
| **Return Value**     | RiseY_Uls_T_f32           | Float32 | 0   | 1   |

## Design Rationale

None

## Processing

Refer ‘LessCmp’ block in Simulink model

## Local Function \#1

|                      |                               |         |      |     |
|----------------------|-------------------------------|---------|------|-----|
| **Function Name**    | CalcAvlCmp                    | Type    | Min  | Max |
| **Arguments Passed** | HwTqFildVal_HwNwtMtr_T_f32    | Float32 | -10  | 10  |
|                      | AssiCmdFildVal_HwNwtMtr_T_f32 | Float32 | -352 | 352 |
| **Return Value**     | HysCmpAvl_HwNwtMtr_T_f32      | Float32 | -8.8 | 8.8 |

## Design Rationale

None

## Processing

Refer ‘CalcAvlCmp’ block in Simulink model

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
| 5           | FDD – SF012A_HysCmp_Design                                                                                                                                            | See Synergy SubProject version |

{% endraw %}