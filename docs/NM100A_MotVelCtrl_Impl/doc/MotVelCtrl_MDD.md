---
layout: default
title: MotVelCtrl_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**MotVelCtrl**

**May 4, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Nick Saxton,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                   |                        |             |             |
|-------------------|------------------------|-------------|-------------|
| **Description**   | **Author**             | **Version** | **Date**    |
| Initial Version   | Sankardu Varadapureddi | 1           | 17-Feb-2016 |
| Input name change | Nick Saxton            | 2           | 04-May-2016 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 MotVelCtrl High-Level Description
[6](#motvelctrl-high-level-description)](#motvelctrl-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of MotVelCtrl
[7](#graphical-representation-of-motvelctrl)](#graphical-representation-of-motvelctrl)

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

[5.1.1 Init: MotVelCtrlInit1
[9](#init-motvelctrlinit1)](#init-motvelctrlinit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: MotVelCtrlPer1
[9](#per-motvelctrlper1)](#per-motvelctrlper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.2.1 GetCtrlPrm_Oper [9](#getctrlprm_oper)](#getctrlprm_oper)

[5.2.1.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.2.1.2 (Processing of function)………
[9](#processing-of-function-1)](#processing-of-function-1)

[5.2.2 SetCtrlPrm_Oper [9](#setctrlprm_oper)](#setctrlprm_oper)

[5.2.2.1 Design Rationale [9](#design-rationale-3)](#design-rationale-3)

[5.2.2.2 (Processing of function)………
[9](#processing-of-function-2)](#processing-of-function-2)

[5.2.3 StopCtrl_Oper [10](#stopctrl_oper)](#stopctrl_oper)

[5.2.3.1 Design Rationale
[10](#design-rationale-4)](#design-rationale-4)

[5.2.3.2 (Processing of function)………
[10](#processing-of-function-3)](#processing-of-function-3)

[5.2.4 StrtCtrl_Oper [10](#strtctrl_oper)](#strtctrl_oper)

[5.2.4.1 Design Rationale
[10](#design-rationale-5)](#design-rationale-5)

[5.2.4.2 (Processing of function)………
[10](#processing-of-function-4)](#processing-of-function-4)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [10](#local-function-1)](#local-function-1)

[5.4.1.1 Description [10](#description)](#description)

[5.5 GLOBAL Function/Macro Definitions
[11](#_Toc443471047)](#_Toc443471047)

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

# MotVelCtrl High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of MotVelCtrl

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/NM100A_MotVelCtrl_Impl/doc/mediax/media/image2.PNG"
style="width:2.68788in;height:2.29199in" />

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

## Init: MotVelCtrlInit1

## Design Rationale

Refer FDD

## Module Outputs

Refer FDD

## Per: MotVelCtrlPer1

## Design Rationale

Refer FDD

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

## GetCtrlPrm_Oper

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## SetCtrlPrm_Oper

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## StopCtrl_Oper

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## StrtCtrl_Oper

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                    |         |           |        |     |
|-----------|---------------------------------|----------|---------|--|--------|
| **Function Name**    | FPIDControl                        | Type    | Min       |        | Max |
| **Arguments Passed** | MotVelTarSlewed_MotRadPerSec_T_f32 | float32 | \- 183500 | 183500 |     |
|                      | MotVelCrf_MotRadPerSec_T_f32       | float32 | -1350     | 1350   |     |
| **Return Value**     | PIDCmdLimid_MotNwtMtr_T_f32        | float32 | -8.8      | 8.8    |     |

## Description

Blocks "F_PID Control_1" , "F_PID Control_2" and "F_PID Control_3" are
of same functionality in the FDD. This sub function corresponds to those
blocks implementation.

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 2.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD : NM100A\_ MotVelCtrl_Design                                                                                                                                      | See Synergy sub project version |

{% endraw %}