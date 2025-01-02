---
layout: default
title: Dampg_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Dampg**

**July 1, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Sankardu Varadapureddi<span class="mark">,</span>**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |                        |             |              |
|-----------------|------------------------|-------------|--------------|
| **Description** | **Author**             | **Version** | **Date**     |
| Initial Version | Sankardu Varadapureddi | 1.0         | 01-July-2015 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 Dampg High-Level Description
[5](#dampg-high-level-description)](#dampg-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of \<Component Name\>
[6](#_Toc423614359)](#_Toc423614359)

[3.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [7](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[8](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[8](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [8](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[9](#software-component-implementation)](#software-component-implementation)

[5.1.1 Sub-Module Functions
[9](#sub-module-functions)](#sub-module-functions)

[5.1.2 Interrupt Service Routines
[9](#interrupt-service-routines)](#interrupt-service-routines)

[5.1.3 Server Runnable Functions
[9](#server-runnable-functions)](#server-runnable-functions)

[5.1.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.1.4.1 Local Function \#1 [9](#local-function-1)](#local-function-1)

[5.1.4.2 Description [9](#description)](#description)

[5.1.4.3 Local Function \#2 [9](#local-function-2)](#local-function-2)

[5.1.4.4 Description [9](#description-1)](#description-1)

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

## Scope

# Dampg High-Level Description

*Refer to FDD*

# Design details of software module

## Graphical representation of Dampg

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF003A_Dampg_Impl/doc/mediax/media/image1.png"
style="width:2.69167in;height:6.01667in" />

## Data Flow Diagram

### Component level DFD

Refer FDD

### Function level DFD

Refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

None

# Software Component Implementation

### Sub-Module Functions

#### Initialization sub-module {\_Init()}

DampgInit1 (Refer FDD for details)

#### Periodic sub-module {\_Per()}

DampgPer1 (Refer FDD for details)

### Interrupt Service Routines

None

### Server Runnable Functions

None

### Module Internal (Local) Functions

## Local Function \#1

|                      |                              |         |       |      |
|----------------------|------------------------------|---------|-------|------|
| **Function Name**    | MotVelDampgCmd               | Type    | Min   | Max  |
| **Arguments Passed** | MotVelCrf_MotRadPerSec_T_f32 | float32 | -1350 | 1350 |
|                      | HwTq_HwNwtMtr_T_f32          | float32 | -10   | 10   |
|                      | TSca_Uls_T_f32               | float32 | 0     | 10   |
|                      | VehSpd_Kph_T_f32             | float32 | 0     | 511  |
| **Return Value**     | ActvDampg_MotNwtMtr_T_f32    | float32 | -176  | 176  |

## Description

‘MotVelDampgCmd’ block implementation.

## Local Function \#2

|                      |                              |         |       |      |
|----------------------|------------------------------|---------|-------|------|
| **Function Name**    | HydPwrSteerDampgCmd          | Type    | Min   | Max  |
| **Arguments Passed** | VehSpd_Kph_T_f32             | float32 | 0     | 511  |
|                      | TSca_Uls_T_f32               | float32 | 0     | 10   |
|                      | AssiCmdBas_MotNwtMtr_T_f32   | float32 | -8.8  | 8.8  |
|                      | MotVelCrf_MotRadPerSec_T_f32 | float32 | -1350 | 1350 |
| **Return Value**     | HydDampg_MotNwtMtr_T_f32     | float32 | -8.8  | 8.8  |

## Description

‘HydPwrSteerDampgCmd’ block implementation.

### Transition Functions

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.0                             |
| 5           | FDD - SF003A_Dampg_Design                                                                                                                                             | See Synergy sub project version |

{% endraw %}