---
layout: default
title: AdcDiagc_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**AdcDiagc**

**Aug 25, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                               |               |             |             |
|-------------------------------|---------------|-------------|-------------|
| **Description**               | **Author**    | **Version** | **Date**    |
| Initial Version               | Rijvi Ahmed   | 1.0         | 02-Feb-2016 |
| Updated per design rev. 1.1.0 | Rijvi Ahmed   | 2.0         | 23-Mar-2016 |
| Updated per design rev. 1.4.0 | Avinash James | 3.0         | 21-Jun-2016 |
| Updated per design rev. 1.6.0 | Avinash James | 4.0         | 15-Jul-2016 |
| Updated per design rev. 1.7.0 | Avinash James | 5.0         | 25-Aug-2016 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 AdcDiagc & High-Level Description
[6](#adcdiagc-high-level-description)](#adcdiagc-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of AdcDiagc
[7](#graphical-representation-of-adcdiagc)](#graphical-representation-of-adcdiagc)

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

[5.1.1 Init: AdcDiagcInit1 [9](#init)](#init)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: AdcDiagcPer1 [9](#per)](#per)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.2.1 SetAdcParFlt [9](#section-1)](#section-1)

[5.2.1.1 Design Rationale [9](#section-2)](#section-2)

[5.2.1.2 (Processing of function)………
[9](#_Toc446502886)](#_Toc446502886)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [10](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale
[10](#design-rationale-2)](#design-rationale-2)

[5.4.1.2 Processing [10](#processing)](#processing)

[5.4.2 Local Function \#2 [10](#local-function-2)](#local-function-2)

[5.4.2.1 Design Rationale
[10](#design-rationale-3)](#design-rationale-3)

[5.4.2.2 Processing [10](#processing-1)](#processing-1)

[5.4.3 Local Function \#3 [10](#local-function-3)](#local-function-3)

[5.4.3.1 Design Rationale
[11](#design-rationale-4)](#design-rationale-4)

[5.4.3.2 Processing [11](#processing-2)](#processing-2)

[5.4.4 Local Function \#4 [11](#local-function-4)](#local-function-4)

[5.4.4.1 Design Rationale
[11](#design-rationale-5)](#design-rationale-5)

[5.4.4.2 Processing [11](#processing-3)](#processing-3)

[5.4.5 Local Function \#5 [11](#local-function-5)](#local-function-5)

[5.4.5.1 Design Rationale
[11](#design-rationale-6)](#design-rationale-6)

[5.4.5.2 Processing [11](#processing-4)](#processing-4)

[5.4.6 Local Function \#6 [11](#local-function-6)](#local-function-6)

[5.4.6.1 Design Rationale
[12](#design-rationale-7)](#design-rationale-7)

[5.4.6.2 Processing [12](#processing-5)](#processing-5)

[5.5 GLOBAL Function/Macro Definitions
[12](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[13](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[14](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[15](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [16](#glossary)](#glossary)

[Appendix C References [17](#references)](#references)

# Introduction

## Purpose

MDD for AdcDiagc

## Scope

# AdcDiagc & High-Level Description

*Refer to FDD.*

# Design details of software module

## Graphical representation of AdcDiagc

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM340A_AdcDiagc_Impl/doc/mediax/media/image1.png"
style="width:6.10833in;height:4.70833in" />

## Data Flow Diagram

None.

### Component level DFD

Refer FDD.

### Function level DFD

Refer FDD.

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name         | Resolution | Units | Value |
|-----------------------|------------|-------|-------|
| MAXADCDIAGCST_CNT_U08 | 1          | CNT   | 7U    |
| Refer to the FDD      |            |       |       |
| MASKFLTCNTR_CNT_U08   | 1          | CNT   | 127U  |

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: 

## Design Rationale

*None*

## Module Outputs

*None*

###  [section]

### Per: 

## Design Rationale

*Refer FDD.*

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD.*

## Server Runables 

### 

## 

## 

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                         |         |     |     |
|----------------------|-------------------------|---------|-----|-----|
| **Function Name**    | St2Proc                 | Type    | Min | Max |
| **Arguments Passed** | AdcSelfDiag0_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag2_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag4_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcDiagcSt_Uls_T_u08    | Uint8   | 0   | 3   |
|                      | \*RollgCntr_Cnt_T_u08   | \*uint8 | 0   | 255 |
| **Return Value**     | AdcNtcStInfo_Uls_T_u08  | Uint8   | 0   | 255 |

## Design Rationale

## Processing

See “State 2” block in the Simulink model of the design.

## Local Function \#2

|                      |                         |         |     |     |
|----------------------|-------------------------|---------|-----|-----|
| **Function Name**    | St4Proc                 | Type    | Min | Max |
| **Arguments Passed** | AdcSelfDiag0_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag2_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag4_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcDiagcSt_Uls_T_u08    | Uint8   | 0   | 3   |
|                      | \*RollgCntr_Cnt_T_u08   | \*uint8 | 0   | 255 |
| **Return Value**     | AdcNtcStInfo_Uls_T_u08  | Uint8   | 0   | 255 |

## Design Rationale

## Processing

See “State 4” block in the Simulink model of the design.

## Local Function \#3

|                      |                         |         |     |     |
|----------------------|-------------------------|---------|-----|-----|
| **Function Name**    | St6Proc                 | Type    | Min | Max |
| **Arguments Passed** | AdcSelfDiag0_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag2_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag4_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcDiagcSt_Uls_T_u08    | Uint8   | 0   | 3   |
|                      | \*RollgCntr_Cnt_T_u08   | \*uint8 | 0   | 255 |
| **Return Value**     | AdcNtcStInfo_Uls_T_u08  | Uint8   | 0   | 255 |

## Design Rationale

## Processing

See “State 6” block in the Simulink model of the design.

## Local Function \#4

|                      |                         |         |     |      |
|----------------------|-------------------------|---------|-----|------|
| **Function Name**    | St0Proc                 | Type    | Min | Max  |
| **Arguments Passed** | AdcSelfDiag0_Volt_T_f32 | float32 | 0.0 | 5.0  |
|                      | AdcSelfDiag2_Volt_T_f32 | float32 | 0.0 | 5.0  |
|                      | AdcSelfDiag4_Volt_T_f32 | float32 | 0.0 | 5.0  |
|                      | \*RollgCntr_Cnt_T_u08   | \*uint8 | 00  | 3255 |
|                      |                         | \*uint8 | 0   | 255  |
| **Return Value**     | AdcNtcStInfo_Uls_T_u08  | Uint8   | 0   | 255  |

## Design Rationale

## Processing

See “State 0” block in the Simulink model of the design.

## Local Function \#5

|                      |                      |       |     |     |
|----------------------|----------------------|-------|-----|-----|
| **Function Name**    | Adc0StBasdProc       | Type  | Min | Max |
| **Arguments Passed** | Adc0ParFlt_Cnt_T_u08 | uint8 | 0   | 255 |
| **Return Value**     | None                 | N/A   | N/A | N/A |

## Design Rationale

## Processing

See “Adc0 State Based Processing” block in the Simulink model of the
design.

## Local Function \#6

|                      |                      |       |     |     |
|----------------------|----------------------|-------|-----|-----|
| **Function Name**    | Adc1StBasdProc       | Type  | Min | Max |
| **Arguments Passed** | Adc1ParFlt_Cnt_T_u08 | uint8 | 0   | 255 |
| **Return Value**     | None                 | N/A   | N/A | N/A |

## Design Rationale

## Processing

See “Adc1 State Based Processing” block in the Simulink model of the
design.

## Local Function \#7

|                      |                 |      |     |     |
|----------------------|-----------------|------|-----|-----|
| **Function Name**    | AdcDiagcPtrProc | Type | Min | Max |
| **Arguments Passed** | None            | N/A  | N/A | N/A |
| **Return Value**     | None            | N/A  | N/A | N/A |

## Design Rationale

## Processing

See “Adc Daigc Pointer” block in the Simulink model of the design.

## Local Function \#8

|                      |                                   |         |     |     |
|----------------------|-----------------------------------|---------|-----|-----|
| **Function Name**    | ScanGroupAccrcyChk                | Type    | Min | Max |
| **Arguments Passed** | AdcScanGroupInpRefVltg_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcScanGroupRefVltg_Volt_T_f32    | float32 | 0.0 | 5.0 |
|                      | AdcScanGroupInpRefPrm_Cnt_T_u08   | Uint8   | 0   | 255 |
| **Return Value**     | ScanGroupAccrcyChkRefPrm_Cnt_u08  | Uint8   | 0   | 255 |

## Design Rationale

## Processing

See “Scan Group Accuracy Check” block in the Simulink model of the
design.

## Local Function \#9

|                      |                        |       |     |     |
|----------------------|------------------------|-------|-----|-----|
| **Function Name**    | SetAdcParFlt           | Type  | Min | Max |
| **Arguments Passed** | \*Adc0ParFlt_Cnt_T_u08 | Uint8 | 0   | 255 |
|                      | \*Adc1ParFlt_Cnt_T_u08 | Uint8 | 0   | 255 |
|                      |                        |       |     |     |
| **Return Value**     |                        |       |     |     |

## Design Rationale

## Processing

See “Adc Parity Fault” block in the Simulink model of the design.

## GLOBAL Function/Macro Definitions

Note: The server runnable of this component are non-rte. So they are
actually global functions which should belong to this section. But as
they are already described under Server Runnable section so it’s omitted
here.

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

The overflow for the following PIMs are intentional as they are used as
rolling counter.

Rte_Pim_Adc0FltCntSt0

Rte_Pim_Adc0FltCntSt2

Rte_Pim_Adc0FltCntSt4

Rte_Pim_Adc0FltCntSt6

Rte_Pim_Adc1FltCntSt0

Rte_Pim_Adc1FltCntSt2

Rte_Pim_Adc1FltCntSt4

Rte_Pim_Adc1FltCntSt6

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
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD - CM340A_AdcDiagc_Design                                                                                                                                          | See Synergy sub project version |

{% endraw %}