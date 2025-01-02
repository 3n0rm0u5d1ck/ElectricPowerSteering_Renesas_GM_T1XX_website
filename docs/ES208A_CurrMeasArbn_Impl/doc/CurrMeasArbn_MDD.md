---
layout: default
title: CurrMeasArbn_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Current Measurement Arbitration**

**June 19, 20156**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**SEPG,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|                                                                    |            |             |              |
|------------------------|---------------------|--------------|--------------|
| **Description**                                                    | **Author** | **Version** | **Date**     |
| Initial Version                                                    | Selva      | 1.0         | 14- Apr-2015 |
| Updated for Anomoly EA4#1589 . Combined MDD for both sources files | Selva      | 2.0         | 17 -Sep 2015 |
| Updated for Anomoly EA4#2989                                       | Selva      | 3.0         | 18 -Mar 2016 |

<u>Table of Contents</u>

[**1** **Introduction 5**](#introduction)

[1.1 Purpose 5](#purpose)

[1.2 Scope 5](#scope)

[2 Current Measurement Arbitration & High-Level Description
6](#current-measurement-arbitration-high-level-description)

[3 Design details of software module
7](#design-details-of-software-module)

[3.1 Graphical representation of Current Measurement Arbitration
7](#graphical-representation-of-current-measurement-arbitration)

[3.2 Data Flow Diagram 7](#data-flow-diagram)

[3.2.1 Component level DFD 7](#component-level-dfd)

[3.2.2 Function level DFD 7](#function-level-dfd)

[4 Constant Data Dictionary 8](#constant-data-dictionary)

[4.1 Program (fixed) Constants 8](#program-fixed-constants)

[4.1.1 Embedded Constants 8](#embedded-constants)

[5 Software Component Implementation
9](#software-component-implementation)

[5.1 Sub-Module Functions 9](#sub-module-functions)

[5.1.1 Init: CurrMeasArbnInit1 9](#init-currmeasarbninit1)

[5.1.1.1 Design Rationale 9](#design-rationale)

[5.1.1.2 Module Outputs 9](#module-outputs)

[5.1.1.3 Per: 9](#per)

[5.1.1.4 CurrMeasARBNPer1 9](#currmeasarbnper1)

[5.1.1.5 Design Rationale 9](#design-rationale-1)

[5.1.1.6 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies)

[5.1.1.7 (Processing of function)……… 9](#processing-of-function)

[5.1.1.8 Store Local copy of outputs into Module Outputs
9](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables 9](#server-runables)

[5.3 Interrupt Functions 9](#interrupt-functions)

[5.4 Module Internal (Local) Functions
9](#module-internal-local-functions)

[5.5 Local Function/Macro Definitions
9](#local-functionmacro-definitions)

[5.5.1 Local Function \#1 SigAvlCheck 9](#local-function-1-sigavlcheck)

[5.5.1.1 Description 10](#description)

[5.5.2 Local Function \#2 ParkTransformation
10](#local-function-2-parktransformation)

[5.5.2.1 Description 10](#description-1)

[5.6 GLOBAL Function/Macro Definitions
10](#global-functionmacro-definitions)

[6 Known Limitations with Design 11](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 12](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 13](#abbreviations-and-acronyms)

[Appendix B Glossary 14](#glossary)

[Appendix C References 16](#references)

# Introduction

## Purpose

None

## Scope

-   None

# Current Measurement Arbitration & High-Level Description

The component contains two source files, both described in this MDD:
CDD\_ CurrMeasArbn.c contains the RTE init runnable;
CDD_CurrMeasArbn_MotCtrl.c contains the motor control runnable.

Refer the Design for high level Description

# Design details of software module

*None*

## Graphical representation of Current Measurement Arbitration

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES208A_CurrMeasArbn_Impl/doc/mediax/media/image1.png"
style="width:3.69167in;height:2.7in" />

## Data Flow Diagram

### Component level DFD

None

### Function level DFD

None

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                                                 |                                                 |                                                 |                                                 |
|---------------------------------|---------------|-----------|-------------|
| Constant Name                                   | Resolution                                      | Units                                           | Value                                           |
|                                                 |                                                 |                                                 |                                                 |
|                                                 |                                                 |                                                 |                                                 |
| MAXVALSIGSTALL_CNT_U08                          | 1                                               | Cnt                                             | 255                                             |
|                                                 |                                                 |                                                 |                                                 |
| Refer DataDict.m file for other local constants | Refer DataDict.m file for other local constants | Refer DataDict.m file for other local constants | Refer DataDict.m file for other local constants |

# Software Component Implementation

## Sub-Module Functions

## Init: CurrMeasArbnInit1

## Design Rationale

Init1 function is created so that it will allow a RTE model to be
created in the AUTOSAR tools which allows Per-Instance Memory and
calibration definition needs. The initialization function is doing
nothing

## Module Outputs

*None*

###  [section]

## Per: 

## CurrMeasARBNPer1

## Design Rationale

*Inputs and outputs are globals since its non RTE (MotorControl ISR)
function.*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function/Macro Definitions

## Local Function \#1 SigAvlCheck

|                      |                                      |          |               |               |
|-------------|------------------------------|--------|-----------|-----------|
| **Function Name**    | SigAvlCheck                          | Type     | Min           | Max           |
| **Arguments Passed** | CurrMeasSigQlfr_T_enum               | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | CurrMeasSigRollgCntr_Cnt_T_u08       | uint8    | 0             | 255           |
|                      | CurrMeasSigCorrlnChk_Cnt_T_u08       | uint8    | 0             | 255           |
|                      | \*PrevCurrMeasSigRollgCntr_Cnt_T_u08 | uint8    | 0             | 255           |
|                      | \*CurrMeasSigStall_Cnt_T_u08         | uint8    | 0             | 255           |
| **Return Value**     | SignalAvailable_Cnt_T_logl           | boolean  | FALSE         | TRUE          |

## Description

Refer FDD.

## Local Function \#2 ParkTransformation

|                      |                                        |         |        |       |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CurrMeasCorrlnChk                      | Type    | Min    | Max   |
| **Arguments Passed** | PhaseAMotCurrCorrd_Ampr_T_f32          | float32 | -200   | 200   |
|                      | PhaseBMotCurrCorrd_Ampr_T_f32          | float32 | -200   | 200   |
|                      | PhaseCMotCurrCorrd_Ampr_T_f32          | float32 | -200   | 200   |
|                      | MotCtrlCurrMeasMotAgCorrd_Rad_T_f32    | float32 | -6.282 | 6.282 |
|                      | MotCtrlMotElecMeclPolarity_Uls_T_s08\* | sint8   | -1     | 1     |
| **Return Value**     | MotCurrDax_Ampr_T_f32                  | float32 | -200   | 200   |
|                      | MotCurrQax_Ampr_T_f32                  | float32 | -200   | 200   |

## Description

Refer FDD.

MotCtrlMotElecMeclPolarity_Cnt_T_s08\* takes two values (-1 and 1)

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

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**            |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2      |
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.01           |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                    |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.1                    |
| 5           | FDD - ES208A Current Measurement Arbitration                                                                                                                  | See synergy subversion |

{% endraw %}