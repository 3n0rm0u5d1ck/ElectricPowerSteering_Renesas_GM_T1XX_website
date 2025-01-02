---
layout: default
title: McuDiagc_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**McuDiagc**

**June 19, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**SEPGroup,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|                                                                               |                    |             |             |
|-------------------------------------|----------------|---------|-----------|
| **Description**                                                               | **Author**         | **Version** | **Date**    |
| Initial Version                                                               | Selva Sengottaiyan | 1.0         | 29-Mar-2016 |
| Updated for the 2Millisecond to MotorControl Diagnostic and changed NTC logic | Avinash James      | 2.0         | 22-Jun-2016 |
| Optimized the diagniostics and removed periodic 3                             | Avinash James      | 3.0         | 28-Sep-2016 |

<u>Table of Contents</u>

[**1** **Introduction 5**](#introduction)

[1.1 Purpose 5](#purpose)

[2 McuDiagc & High-Level Description
6](#component-name-high-level-description)

[3 Design details of software module
7](#design-details-of-software-module)

[3.1 Graphical representation of McuDiagc
7](#graphical-representation-of-mcudiagc)

[3.2 Data Flow Diagram 7](#data-flow-diagram)

[3.2.1 Component level DFD 7](#component-level-dfd)

[3.2.2 Function level DFD 7](#function-level-dfd)

[4 Constant Data Dictionary 8](#constant-data-dictionary)

[4.1 Program (fixed) Constants 8](#program-fixed-constants)

[4.1.1 Embedded Constants 8](#embedded-constants)

[5 Software Component Implementation
9](#software-component-implementation)

[5.1 Sub-Module Functions 9](#sub-module-functions)

[5.1.1 Init: McuDiagcInit1 9](#init-mcudiagcinit1)

[5.1.1.1 Design Rationale 9](#design-rationale)

[5.1.1.2 Module Outputs 9](#module-outputs)

[5.1.2 Per: McuDiagcPer1 9](#per-mcudiagcper1)

[5.1.2.1 Design Rationale 9](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)……… 9](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
9](#store-local-copy-of-outputs-into-module-outputs)

[5.1.3 Per: McuDiagcPer2 9](#per-mcudiagcper2)

[5.1.3.1 Design Rationale 9](#design-rationale-2)

[5.1.3.2 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies-1)

[5.1.3.3 (Processing of function)……… 9](#processing-of-function-1)

[5.1.3.4 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs-1)

[5.2 Server Runnable 10](#server-runnable)

[5.3 Interrupt Functions 10](#interrupt-functions)

[5.4 Module Internal (Local) Functions
10](#module-internal-local-functions)

[5.5 GLOBAL Function/Macro Definitions
10](#global-functionmacro-definitions)

[6 Known Limitations with Design 11](#known-limitations-with-design)

[7 *Outputs are not range limited as it is intentional and it is
expected to go full range as it is a rolling counter*UNIT TEST
CONSIDERATION 12](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 13](#abbreviations-and-acronyms)

[Appendix B Glossary 14](#glossary)

[Appendix C References 16](#references)

# Introduction

## Purpose

Module design document for Micro Controller Diagnostics

# \<Component Name\> & High-Level Description

Refer the Design.

# Design details of software module

## Graphical representation of McuDiagc

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES002A_McuDiagc_Impl/doc/mediax/media/image1.png"
style="width:6.03403in;height:3.18333in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                                         |            |       |        |
|-----------------------------------------|------------|-------|--------|
| Constant Name                           | Resolution | Units | Value  |
| FASTLOOPCNTRENGMAX_CNT_U16              | 1          | Cnt   | 65535  |
| FASTLOOPCNTRENGMIN_CNT_U16              | 1          | Cnt   | 0      |
| ROLLOVROFFS_CNT_U16                     | 1          | Cnt   | 65535U |
| ROLLOVRCHK_CNT_U16                      | 1          | Cnt   | 32767U |
|                                         |            |       |        |
| LOOPCNTR2MILLISECMOTCTRLDIFFMIN_CNT_U16 | 1          | Cnt   | 0U     |
| Refer .m file                           |            |       |        |

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: McuDiagcInit1

## Design Rationale

*Refer to FDD*

## Module Outputs

*Refer to FDD*

###  [section]

### Per: McuDiagcPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD0*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

### Per: McuDiagcPer2

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD0*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

### 

## 

## 

## 

## 

### 

## Server Runnable 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

*None*

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

Outputs are not range limited as it is intentional and it is expected to
go full range as it is a rolling counter

# UNIT TEST CONSIDERATION

Overflow for the variable Rte**\_Pim_FastLoopCntrPrev,**
**Rte_Pim_LoopCntr2MilliSecStore** is intentional as this is used as a
rolling counter.

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**           |
|-----------------------------|---------------------------|
| DFD                         | Design functional diagram |
| MDD                         | Module design Document    |

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

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.01                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.1                            |
| 5           | FDD – ES002A McuDiagc                                                                                                                                         | See Synergy subproject version |

{% endraw %}