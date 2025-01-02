---
layout: default
title: SinVltgGenn_MDD
nav_order: 4
parent: Component Implementation
---
{% raw %}
Module Design Document

**For**

**\<Component Name\>**

**Mar 20, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**SEPG,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**<u>Change History</u>**

|         |                                        |                        |             |
|----------|-----------------------------|------------|-----------------------|
| Version | Description                            | Author                 | Date        |
| 1       | Initial version                        | Sankardu Varadapureddi | 2-May-2015  |
| 2       | Updated to fix A1587                   | Selva Sengottaiyan     | 17-Sep-2015 |
| 3       | Updated for v1.30 and 1.4.0 of the FDD | Selva Sengottaiyan     | 20-Mar-2016 |

<u>Table of Contents</u>

[1 Introduction 5](#introduction)

[1.1 Purpose 5](#purpose)

[1.2 Scope 5](#scope)

[2 SinVltgGenn & High-Level Description
6](#sinvltggenn-high-level-description)

[3 Design details of software module
7](#design-details-of-software-module)

[3.1 Graphical representation of SinVltgGenn
7](#graphical-representation-of-sinvltggenn)

[3.2 Data Flow Diagram 7](#data-flow-diagram)

[3.2.1 Component level DFD 7](#component-level-dfd)

[3.2.2 Function level DFD 7](#function-level-dfd)

[4 Constant Data Dictionary 8](#constant-data-dictionary)

[4.1 Program (fixed) Constants 8](#program-fixed-constants)

[4.1.1 Embedded Constants 8](#embedded-constants)

[5 Software Component Implementation
9](#software-component-implementation)

[5.1 Sub-Module Functions 9](#sub-module-functions)

[5.2 Initialization Functions 9](#initialization-functions)

[5.2.1 Init: SinVltgGennInit1 9](#init-sinvltggenninit1)

[5.2.1.1 Design Rationale 9](#design-rationale)

[5.2.1.2 Module Internal 9](#module-internal)

[5.3 PERIODIC FUNCTIONS 9](#periodic-functions)

[5.3.1 Per: SinVltgGennPer1 9](#per-sinvltggennper1)

[5.3.1.1 Design Rationale 9](#design-rationale-1)

[5.3.1.2 Processing of Function 9](#processing-of-function)

[5.3.2 Per: SinVltgGennPer2 9](#per-sinvltggennper2)

[5.3.2.1 Design Rationale 9](#design-rationale-2)

[5.3.2.2 Processing of Function 9](#processing-of-function-1)

[5.4 Server Runables 9](#server-runables)

[5.5 Interrupt Functions 10](#interrupt-functions)

[5.6 Module Internal (Local) Functions
10](#module-internal-local-functions)

[5.6.1 Local Function \#1 10](#local-function-1)

[5.6.1.1 Description 10](#description)

[5.7 GLOBAL Function/Macro Definitions
10](#global-functionmacro-definitions)

[6 Known Limitations with Design 11](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 12](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 13](#abbreviations-and-acronyms)

[Appendix B Glossary 14](#glossary)

[Appendix C References 15](#references)

# Introduction

## Purpose

None

## Scope

-   None

# SinVltgGenn & High-Level Description

The component contains two source files, both described in this MDD:
CDD\_ SinVltgGenn.c contains the RTE init runnable;
CDD_SinVltgGenn_MotCtrl.c contains the motor control runnable.

Refer the Design for high level Description

# Design details of software module

## Graphical representation of SinVltgGenn 

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES300A_SinVltgGenn_Impl/doc/mediax/media/image2.png"
style="width:2.50833in;height:1.08333in" />

## Data Flow Diagram

None

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| None          |            |       |       |

# Software Component Implementation

**Note:** All the non RTE signals defined in m file are implemented as
global varibles managed by motor control manager. RTE can not manage
motor control runnables inputs and outputs.

## Sub-Module Functions

None

## Initialization Functions

## Init: SinVltgGennInit1

## Design Rationale

None

## Module Internal

See design model for details.

## PERIODIC FUNCTIONS 

## Per: SinVltgGennPer1

## Design Rationale

*Inputs and outputs are globals since its non RTE (MotorControl ISR)
function.*

Note: Instead of division operation, multiplication with
‘NXTRFIXDPT_P16TOFLOAT_ULS_F32’ used.

## Processing of Function

See design model for details.

## Per: SinVltgGennPer2

## Design Rationale

*Inputs and outputs are globals since its non RTE (MotorControl ISR)
function.*

Note: outputs are not limited in SW as max limit is set to U32 range in
design.

## Processing of Function

See design model for details.

## Server Runables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                               |                                               |        |       |
|-------------|------------------------------|-----------|----------|----------|
| **Function Name**    | MotCtrlPhaOnTiCal             | Type                                          | Min    | Max   |
| **Arguments Passed** | CmuOffs_NanoSec_T_u32         | uint32                                        | 45454  | 71429 |
|                      | MotAgElec_MotRevElec_T_u0p16  | uint16 (used as a fixed point representation) | 0      | 0.999 |
|                      | MotPhaAdv_MotRevElec_T_u0p16  | uint16 (used as a fixed point representation) | 0      | 0.999 |
|                      | PhaDptOffsX_MotRevElec_T_f32  | float32                                       | -0.999 | 0.999 |
|                      | MotModlnIdx_Uls_T_f32         | float32                                       | 0      | 1     |
|                      | PwmPerd_NanoSec_T_u32         | uint32                                        | 45454  | 71429 |
| **Return Value**     | MotCtrlPhaOnTiX_NanoSec_T_u32 | uint32                                        | 0      | 71429 |

## Description

Function corresponds to 'Subsystem1/Subsystem2/Subsystem3' block
implementation. Subsystems 1 through 3 have common processing.

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

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.01                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.1                             |
| 5           | FDD – ES300A_SinVltgGenn_Design                                                                                                                               | See Synergy sub project version |

{% endraw %}