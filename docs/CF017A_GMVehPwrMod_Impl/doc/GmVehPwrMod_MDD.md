---
layout: default
title: GmVehPwrMod_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**GmVehPwrMod**

**VERSION:6.0**

**Dec 13, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Matthew Leser**

**Saginaw, MI, USA**

**<u>Change History</u>**

|                                                                    |            |             |             |
|------------------|----------------|----------|----------------------------|
| **Description**                                                    | **Author** | **Version** | **Date**    |
| Initial Version                                                    | N. Saxton  | 1.0         | 28-Sep-2015 |
| Updated with new graphical representation and local function       | N. Saxton  | 2.0         | 01-Oct-2015 |
| New graphical representation                                       | N. Saxton  | 3.0         | 12-Nov-2015 |
| Changes to local constants and functions                           | N. Saxton  | 4.0         | 15-Apr-2016 |
| Updated as per design rev. 2.1.0                                   | TATA       | 5.0         | 22-Nov-2016 |
| Updated as per design rev. 2.2.0/2.3.0 and to fix Anomaly EA4#8982 | M. Leser   | 6.0         | 13-Dec-2016 |

<u>Table of Contents</u>

[1 GmVehPwrMod & High-Level Description
[5](#gmvehpwrmod-high-level-description)](#gmvehpwrmod-high-level-description)

[2 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of GmVehPwrMod
[6](#graphical-representation-of-gmvehpwrmod)](#graphical-representation-of-gmvehpwrmod)

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

[4.1.1 Per: GmVehPwrModPer1
[8](#per-gmvehpwrmodper1)](#per-gmvehpwrmodper1)

[4.1.1.1 Design Rationale [8](#design-rationale)](#design-rationale)

[4.1.1.2 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.1.3 (Processing of function)………
[8](#processing-of-function)](#processing-of-function)

[4.1.1.4 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runables [8](#server-runables)](#server-runables)

[4.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 Local Function \#1 [8](#local-function-1)](#local-function-1)

[4.4.1.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[4.4.1.2 Created to reduce static path count and cyclomatic complexity
of periodic function. Processing [9](#_Toc467580596)](#_Toc467580596)

[4.4.2 Local Function \#2 [9](#local-function-2)](#local-function-2)

[4.4.2.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[4.4.2.2 Processing [9](#processing)](#processing)

[4.4.3 Local Function \#3 [9](#local-function-3)](#local-function-3)

[4.4.3.1 Design Rationale [9](#design-rationale-3)](#design-rationale-3)

[4.4.3.2 Processing [9](#processing-1)](#processing-1)

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

# GmVehPwrMod & High-Level Description

*This GM specific function runs periodically to determine whether to
enable assist (if not previously enabled) or to disable assist based on
the inputs provided to the function.*

# Design details of software module

## Graphical representation of GmVehPwrMod

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CF017A_GMVehPwrMod_Impl/doc/mediax/media/image2.png"
style="width:4.3021in;height:4.427in" />

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

| Constant Name                     | Units | Value |
|-----------------------------------|-------|-------|
| LOOKUPTBLSIZE_CNT_U16             | CNT   | 512   |
| Refer .m file for other constants | N/A   | N/A   |

# Software Component Implementation

## Sub-Module Functions

## Per: GmVehPwrModPer1

## Design Rationale

None

## Store Module Inputs to Local copies

*Refer to FDD*

##  (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | GetTblIdx                      | Type    | Min   | Max  |
| **Arguments Passed** | GetGpioMcuEna_Cnt_T_logl       | Boolean | FALSE | TRUE |
|                      | SysPwrModRun_Cnt_T_logl        | Boolean | FALSE | TRUE |
|                      | EngRunActv_Cnt_T_logl          | Boolean | FALSE | TRUE |
|                      | VehSpdAssiKeepMin_Cnt_T_logl   | Boolean | FALSE | TRUE |
|                      | PrpnSysActvMsgInvld_Cnt_T_logl | Boolean | FALSE | TRUE |
|                      | VehSpdSnsrVld_Cnt_T_logl       | Boolean | FALSE | TRUE |
|                      | SysPwrModMsgInvld_Cnt_T_logl   | Boolean | FALSE | TRUE |
|                      | BusOffHiSpd_Cnt_T_logl         | Boolean | FALSE | TRUE |
|                      | HwTq_HwNwtMtr_T_f32            | Float32 | -10   | 10   |
| **Output**           | TblIdxNr_Cnt_T_u16             | Uint16  | 0     | 511  |

*  
*

## Design Rationale

<span id="_Toc467580596" class="anchor"></span>Created to reduce static
path count and cyclomatic complexity of periodic function. Processing

Refer FDD

## Local Function \#2

|                      |                       |         |       |      |
|----------------------|-----------------------|---------|-------|------|
| **Function Name**    | GetMotTqCmdSca        | Type    | Min   | Max  |
| **Arguments Passed** | AssiEna_Cnt_T_logl    | Boolean | FALSE | TRUE |
| **Output**           | MotTqCmdSca_Cnt_T_f32 | Boolean | 0.0   | 1.0  |

## Design Rationale

Created to reduce static path count and cyclomatic complexity of
periodic function.

## Processing

Sets MotTqCmdSca to 1.0 if AssiEna is TRUE and sets it to 0.0 otherwise.

## Local Function \#3

|                      |                       |         |     |     |
|----------------------|-----------------------|---------|-----|-----|
| **Function Name**    | KeepAssiHwTqTmr       | Type    | Min | Max |
| **Arguments Passed** | HwTq_HwNwtMtr_T_f32   | Float32 | -10 | 10  |
|                      | \* TblIdxNr_Cnt_T_u16 | Uint16  | 0   | 511 |

## Design Rationale

Created to reduce static path count and cyclomatic complexity of local
function \#2.

\*TblIdxNr_Cnt_T_u16 is an output of this function.

## Processing

Refer ‘KeepAssi_HwTqTmr’ block in model.

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

| **Ref. \#** | **Title**                                                                                                                                                               | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                      | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                           | EA4 04.02.01                   |
| 3           | EA4 [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 04.02.01                       |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc)   | 2.1                            |
| 5           | FDD: CF017A_GmVehPwrMod_Design                                                                                                                                          | See Synergy subproject version |

{% endraw %}