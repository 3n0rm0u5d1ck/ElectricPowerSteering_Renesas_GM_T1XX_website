---
layout: default
title: GmFctDiArbn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**GmFctDiArbn**

**June 30, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Nick Saxton**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |             |             |              |
|-----------------|-------------|-------------|--------------|
| **Description** | **Author**  | **Version** | **Date**     |
| Initial Version | Nick Saxton | 1           | 30-June-2016 |

**  
**

**<u>Table of Contents</u>**

[1 GmStrtStop High-Level Description
[5](#gmstrtstop-high-level-description)](#gmstrtstop-high-level-description)

[2 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of GmStrtStop
[6](#graphical-representation-of-gmstrtstop)](#graphical-representation-of-gmstrtstop)

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

[4.1.1 Init: None [8](#init-none)](#init-none)

[4.1.2 Per: GmStrtStopPer1
[8](#per-gmstrtstopper1)](#per-gmstrtstopper1)

[4.1.2.1 Design Rationale [8](#design-rationale)](#design-rationale)

[4.1.2.2 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function)………
[8](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runables [8](#server-runables)](#server-runables)

[4.3 Interrupt Functions [8](#gmfctdireq_oper)](#gmfctdireq_oper)

[4.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 Local Function \#1 [8](#local-function-1)](#local-function-1)

[4.4.1.1 Description [8](#description)](#description)

[4.4.2 Local Function \#2 [8](#local-function-2)](#local-function-2)

[4.4.2.1 Description [9](#description-1)](#description-1)

[4.4.3 Local Function \#3 [9](#local-function-3)](#local-function-3)

[4.4.3.1 Description [9](#description-2)](#description-2)

[4.5 GLOBAL Function/Macro Definitions
[9](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[10](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[11](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[12](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [13](#glossary)](#glossary)

[Appendix C References [14](#references)](#references)

# GmStrtStop High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of GmStrtStop

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CF025A_GmFctDiArbn_Impl/doc/mediax/media/image1.png"
style="width:4.25833in;height:4.49167in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

Refer .m file

# Software Component Implementation

## Sub-Module Functions

## Init: None

## Per: GmStrtStopPer1

## Design Rationale

Refer FDD for the overall functionality.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

### GmFctDiReq_Oper

## Design Rationale

Refer FDD for the overall functionality.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                            |         |       |          |     |
|--------------|---------------------|--------------|------------|--|-----------|
| **Function Name**    | GetElpdTi                  | Type    | Min   |          | Max |
| **Arguments Passed** | FctDi_Cnt_T_logl           | boolean | FALSE | TRUE     |     |
|                      | FctDiStrtTi_MicroSec_T_u32 | uint32  | 0     | 10000000 |     |
| **Return Value**     | ElpdTi_Sec_T_f32           | float32 | 0     | 10000000 |     |

## Description

Implementation of ‘FcnDi_ElpdTi’ block in the model.

## Local Function \#2

|                      |                       |                 |                     |                            |     |
|---------|----------------|------------|----------------|--|--------------------|
| **Function Name**    | ChkEotPosInRng        | Type            | Min                 |                            | Max |
| **Arguments Passed** | FctDi_Cnt_T_logl      | boolean         | FALSE               | TRUE                       |     |
|                      | HwAgFinal_HwDeg_T_f32 | float32         | -1440               | 1440                       |     |
|                      | CwEot_HwDeg_T_f32     | float32         | 360                 | 900                        |     |
|                      | CcwEot_HwDeg_T_f32    | float32         | -900                | -360                       |     |
| **Return Value**     | GmFctDiSts_Cnt_T_enum | GmFctDiArbnSts1 | GMFCTDIARBNSTS_WAIT | GMFCTDIARBNSTS_TIMEOUTFAIL |     |

## Description

Implementation of 'CheckEotPosInRng' block in the model.

## Local Function \#3

|                      |                        |         |       |      |     |
|----------------------|------------------------|---------|-------|------|-----|
| **Function Name**    | ChkHwTqZeroAndHwAgZero | Type    | Min   |      | Max |
| **Arguments Passed** | HwAgFinal_HwDeg_T_f32  | float32 | -1440 | 1440 |     |
|                      | HwTq_HwNwtMtr_T_f32    | float32 | -10   | 10   |     |
| **Return Value**     | OnCenterEna_Cnt_T_logl | boolean | FALSE | TRUE |     |

## Description

Implementation of 'CheckHwTqZeroAndHwAgZero' block in the model.

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | EA4 01.00.00                    |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD : CF025A\_ GmFctDiArbn_Design                                                                                                                                     | See Synergy sub project version |

{% endraw %}