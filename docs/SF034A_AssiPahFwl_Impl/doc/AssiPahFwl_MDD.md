---
layout: default
title: AssiPahFwl_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**AssiPahFwl**

**Feb 05, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Sarika Natu,**

**KPIT Technologies,**

**India**

**  
<u>Change History</u>**

| **Description** | **Author**                     | **Version** | **Date**    |
|-----------------|--------------------------------|-------------|-------------|
| Initial Version | Sarika Natu(KPIT Technologies) | 1.0         | 05-Feb-2016 |

**  
**

**<u>Table of Contents</u>**

[1 AssiPahFwl & High-Level Description
[5](#assipahfwl-high-level-description)](#assipahfwl-high-level-description)

[2 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of AssiPahFwl
[6](#graphical-representation-of-assipahfwl)](#graphical-representation-of-assipahfwl)

[2.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [6](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[4.1.1 Init: AssiPahFwl_Init1
[8](#init-assipahfwl_init1)](#init-assipahfwl_init1)

[4.1.1.1 Design Rationale [8](#design-rationale)](#design-rationale)

[4.1.1.2 Module Outputs [8](#module-outputs)](#module-outputs)

[4.1.2 Per: AssiPahFwl_Per1
[8](#per-assipahfwl_per1)](#per-assipahfwl_per1)

[4.1.2.1 Design Rationale [8](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function)………
[8](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runables [8](#server-runnables)](#server-runnables)

[4.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 Local Function \#1 [8](#local-function-1)](#local-function-1)

[4.4.1.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[4.4.1.2 Processing [9](#processing)](#processing)

[4.4.2 Local Function \#2 [9](#local-function-2)](#local-function-2)

[4.4.2.1 Design Rationale [9](#design-rationale-3)](#design-rationale-3)

[4.4.2.2 Processing [9](#processing-1)](#processing-1)

[4.4.3 Local Function \#3 [9](#local-function-3)](#local-function-3)

[4.4.3.1 Design Rationale [9](#design-rationale-4)](#design-rationale-4)

[4.4.3.2 Processing [10](#processing-2)](#processing-2)

[4.4.4 Local Function \#4 [10](#local-function-4)](#local-function-4)

[4.4.4.1 Design Rationale
[10](#design-rationale-5)](#design-rationale-5)

[4.4.4.2 Processing [10](#processing-3)](#processing-3)

[4.4.5 Local Function \#5 [10](#local-function-5)](#local-function-5)

[4.4.5.1 Design Rationale
[10](#design-rationale-6)](#design-rationale-6)

[4.4.5.2 Processing [10](#processing-4)](#processing-4)

[4.5 GLOBAL Function/Macro Definitions
[11](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[12](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[13](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[14](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [15](#glossary)](#glossary)

[Appendix C References [16](#references)](#references)

# AssiPahFwl & High-Level Description

Refer FDD

# Design details of software module

## Graphical representation of AssiPahFwl

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF034A_AssiPahFwl_Impl/doc/mediax/media/image1.png"
style="width:3.47917in;height:5.02083in" />

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

| Constant Name     | Resolution | Units | Value  |
|-------------------|------------|-------|--------|
| NODEBSTEP_CNT_U16 | NA         | NA    | 65535U |

# Software Component Implementation

## Sub-Module Functions

## Init: AssiPahFwl_Init1

## Design Rationale

*Refer FDD*

## Module Outputs

*Refer FDD*

## Per: AssiPahFwl_Per1

## Design Rationale

Refer FDD

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runnables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                |           |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | Dynamic_Assi_Boundary          | Type      | Min   | Max  |
| **Arguments Passed** | VehSpd_Kph_T_u9p7              | Uint16    | 0     | 511  |
|                      | HwTq_HwNwtMtr_T_f32            | Float32   | -10.0 | 10.0 |
|                      | LoFrqInp_MotNwtMtr_T_f32       | Float32   | -16   | 16   |
|                      | \*LowrBndLpFil_MotNwtMtr_T_f32 | Float32\* | -16   | 16   |
|                      | \*UpprBndLpFil_MotNwtMtr_T_f32 | Float32\* | -16   | 16   |
| **Return Value**     | HiFrqAssiLimd_MotNwtMtr_T_f32  | Float32   | -16   | 16   |

## Design Rationale

LowrBndLpFil_MotNwtMtr_T_f32 and UpprBndLpFil_MotNwtMtr_T_f32 will be
updated in this function.

## Processing

Refer to the subsystems 'Determine HiFreqAsst Boundaries' and 'Low pass
filter boundaries' in FDD.

## Local Function \#2

|                      |                                |           |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | Base_Assi_Boundary             | Type      | Min   | Max  |
| **Arguments Passed** | HwTrq_HwNwtMtr_T_f32           | Float32   | -20.0 | 20.0 |
|                      | VehSpd_Kph_T_u9p7              | Uint16    | 0     | 511  |
|                      | AssiCmdBas_MotNwtMtr_T_f32     | Float32   | -8.8  | 8.8  |
|                      | BasAssiLowrBnd_MotNwtMtr_T_f32 | float32\* | -16   | 16   |
|                      | BasAssiUpprBnd_MotNwtMtr_T_f32 | float32\* | -16   | 16   |
| **Return Value**     | BasAssiLimd_MotNwtMtr_T_f32    | Float32   | -16   | 16   |

## Design Rationale

BasAssiLowrBnd_MotNwtMtr_T_f32 and BasAssiUpprBnd_MotNwtMtr_T_f32 will
be updated in this function

## Processing

Refer the subsystem ‘Determine_BaseAsst_Boundaries’ implementation in
FDD.

## Local Function \#3

|                      |                                 |           |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | Det_Boundary_Lim                | Type      | Min   | Max  |
| **Arguments Passed** | AssiCmdBas_MotNwtMtr_T_f32      | Float32   | -8.8  | 8.8  |
|                      | BasAssiUpprBnd_MotNwtMtr_T_f32  | Float32   | -16   | 16   |
|                      | BasAssiLowrBnd_MotNwtMtr_T_f32  | Float32   | -16   | 16   |
|                      | LowrBndLpFil_MotNwtMtr_T_f32    | Float32   | -16   | 16   |
|                      | UpprBndLpFil_MotNwtMtr_T_f32    | Float32   | -16   | 16   |
|                      | LoFrqInp_MotNwtMtr_T_f32        | Float32   | -16   | 16   |
|                      | HiFrqOverBnd_MotNwtMtr_T_Logl   | Boolean\* | FALSE | TRUE |
|                      | BasAssiOverBnd_MotNwtMtr_T_Logl | Boolean\* | FALSE | TRUE |
| **Return Value**     | AssiFwlFailSts_Cnt_T_Logl       | Boolean   | FALSE | TRUE |

## Design Rationale

HiFrqOverBnd_MotNwtMtr_T_Logl and BasAssiOverBnd_MotNwtMtr_T_Logl will
be updated in this function.

## Processing

Refer to the section ‘Check both command paths for reaching boundary
limits, if so begin de bounce counters’ in FDD.

## Local Function \#4

|                      |                                 |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | Assist_Recovery_Cond            | Type    | Min   | Max  |
| **Arguments Passed** | AssiCmdBas_MotNwtMtr_T_f32      | Float32 | -8.8  | 8.8  |
|                      | DftAssi_MotNwtMtr_T_f32         | Float32 | -8.8  | 8.8  |
|                      | AssiFwlFailSts_Cnt_T_Logl       | Boolean | FASLE | TRUE |
|                      | SumInp_MotNwtMtr_T_f32          | Float32 | -17.6 | 17.6 |
|                      | BasAssiLimd_MotNwtMtr_T_f32     | Float32 | -16   | 16   |
|                      | HiFrqInp_MotNwtMtr_T_f32        | Float32 | -16   | 16   |
|                      | HiFrqAssiLimd_MotNwtMtr_T_f32   | Float32 | -16   | 16   |
|                      | BasAssiOverBnd_MotNwtMtr_T_Logl | Boolean | FALSE | TRUE |
|                      | HiFrqOverBnd_MotNwtMtr_T_Logl   | Boolean | FALSE | TRUE |
|                      | \*AssiPahLimrActv_Uls_T_f32     | Float32 | FASLE | TRUE |
| **Return Value**     | CombdAssiDft_MotNwtMtr_T_f32    | Float32 | -8.8  | 8.8  |

## Design Rationale

AssiPahLimrActv_Uls_T_f32 will be updated in this function

## Processing

Refer to the section ‘Check Input commands vs. Fwl Output command for
Assist Recovery Conditions’ in FDD.

## Local Function \#5

|                      |                                 |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | Set_Faults                      | Type    | Min   | Max  |
| **Arguments Passed** | HiFrqOverBnd_MotNwtMtr_T_Logl   | Boolean | FASLE | TRUE |
|                      | BasAssiOverBnd_MotNwtMtr_T_Logl | Boolean | FASLE | TRUE |
| **Return Value**     | None                            |         |       |      |

## Design Rationale

None

## Processing

Refer ‘Set_Faults’ subsystem in FDD.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**       |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2 |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00      |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 2.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1               |

{% endraw %}