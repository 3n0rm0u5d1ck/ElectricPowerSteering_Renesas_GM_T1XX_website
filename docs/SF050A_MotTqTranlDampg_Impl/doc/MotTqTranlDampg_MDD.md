---
layout: default
title: MotTqTranlDampg_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Transistional Damping (SF-50A)**

**August 12, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Krishna Kanth Anne,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |                    |              |             |
|-----------------|--------------------|--------------|-------------|
| **Description** | **Author**         | **Version**  | **Date**    |
| Initial Version | Krishna Kanth Anne | EA4 01.00.01 | 12-Aug-2015 |

**  
**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 MotTqTranlDampg & High-Level Description
[6](#mottqtranldampg-high-level-description)](#mottqtranldampg-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of MotTqTranlDampg
[7](#_Toc427321562)](#_Toc427321562)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

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

[5.1.1 Init: MotTqTranlDampgInit1
[10](#init-mottqtranldampginit1)](#init-mottqtranldampginit1)

[5.1.1.1 Design Rationale [10](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [10](#module-outputs)](#module-outputs)

[5.1.2 Per: MotTqTranlDampgPer1
[10](#per-mottqtranldampgper1)](#per-mottqtranldampgper1)

[5.1.2.1 Design Rationale
[10](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[10](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [10](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [10](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale
[11](#design-rationale-2)](#design-rationale-2)

[5.4.1.2 Processing [11](#processing)](#processing)

[5.4.2 Local Function \#2 [11](#local-function-2)](#local-function-2)

[5.4.2.1 Design Rationale
[11](#design-rationale-3)](#design-rationale-3)

[5.4.2.2 Processing [11](#processing-1)](#processing-1)

[5.5 GLOBAL Function/Macro Definitions
[11](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [11](#global-function-1)](#global-function-1)

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

MDD for Motor Torque Transistional Damping.

## Scope

# MotTqTranlDampg & High-Level Description

Please refer FDD.

# Design details of software module

## Graphical representation of MotTqTranlDampg

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF050A_MotTqTranlDampg_Impl/doc/mediax/media/image1.png"
style="width:4.13958in;height:6.06944in" />

## Data Flow Diagram

Please refer FDD.

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name        | Resolution | Units | Value |
|----------------------|------------|-------|-------|
| Please refer .m file |            |       |       |

# Software Component Implementation

## Sub-Module Functions

### Init: MotTqTranlDampgInit1

## Design Rationale

None

## Module Outputs

None

###  [section]

## Per: MotTqTranlDampgPer1

## Design Rationale

None

## Store Module Inputs to Local copies

Please refer FDD

##  (Processing of function)………

Please refer FDD

## Store Local copy of outputs into Module Outputs

Please refer FDD

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                  |         |       |        |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | SwOpCtrlPart1                    | Type    | Min   | Max    |
| **Arguments Passed** | TranlDampgTiElpsd_MilliSec_T_f32 | float32 | 0.0   | 1000.0 |
|                      | AbslMotVelCrf_MotRadPerSec_T_f32 | float32 | 0.0   | 1350.0 |
| **Return Value**     | MotTqTranlDampgCmpl_Cnt_T_lgc    | boolean | FALSE | TRUE   |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “SwOutputCntrl” block of the Simulink model of the design.

## Local Function \#2

|                      |                                       |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | SwOpCtrlPart2                         | Type    | Min   | Max  |
| **Arguments Passed** | DiagcStsCtrldShtDwnFltPrsnt_Cnt_T_lgc | boolean | FALSE | TRUE |
|                      | CtrlDampTrq_MotNwtMtr_T_f32           | float32 | -3.0  | 3.0  |
|                      | SysSt_Cnt_T_enum                      | SysSt1  | 0     | 3    |
|                      | MotTqCmdCrf_MotNwtMtr_T_f32           | float32 | -8.8  | 8.8  |
|                      | MotTqTranlDampgCmpl_Cnt_T_lgc         | boolean | FALSE | TRUE |
| **Return Value**     | MotTqCmdCrfDampd_MotNwtMtr_T_f32      | float32 | -11.8 | 11.8 |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “SwOutputCntrl” block of the Simulink model of the design.

##  [section-1]

## GLOBAL Function/Macro Definitions

None

## GLOBAL Function \#1

|                      |      |      |     |     |
|----------------------|------|------|-----|-----|
| **Function Name**    | NA   | Type | Min | Max |
| **Arguments Passed** | None |      |     |     |
| **Return Value**     | NA   |      |     |     |

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
| 5           | FDD : SF050A_MotTqTranlDampg_Design (V 1.1.0)                                                                                                                         | See Synergy sub project version |

{% endraw %}