---
layout: default
title: PwrLimr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**PwrLimr**

**August 14, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Nick Saxton,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |             |             |             |
|-----------------|-------------|-------------|-------------|
| **Description** | **Author**  | **Version** | **Date**    |
| Initial Version | Nick Saxton | 1.0         | 14-Aug-2015 |

**<u>Table of Contents</u>**

[1 PwrLimr High-Level Description
[4](#pwrlimr-high-level-description)](#pwrlimr-high-level-description)

[2 Design details of software module
[5](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of PwrLimr
[5](#graphical-representation-of-pwrlimr)](#graphical-representation-of-pwrlimr)

[2.2 Data Flow Diagram [5](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[5](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [5](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[6](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[6](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [6](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[7](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[7](#sub-module-functions)](#sub-module-functions)

[4.1.1 Init: PwrLimrInit1 [7](#init-pwrlimrinit1)](#init-pwrlimrinit1)

[4.1.1.1 Design Rationale [7](#design-rationale)](#design-rationale)

[4.1.1.2 Module Outputs [7](#module-outputs)](#module-outputs)

[4.1.2 Per: PwrLimrPer1 [7](#per-pwrlimrper1)](#per-pwrlimrper1)

[4.1.2.1 Design Rationale [7](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[7](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function)………
[7](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[7](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.1.3 Per: PwrLimrPer2 [7](#per-pwrlimrper2)](#per-pwrlimrper2)

[4.1.3.1 Design Rationale [7](#design-rationale-2)](#design-rationale-2)

[4.1.3.2 Store Module Inputs to Local copies
[7](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[4.1.3.3 (Processing of function)………
[7](#processing-of-function-1)](#processing-of-function-1)

[4.1.3.4 Store Local copy of outputs into Module Outputs
[7](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[4.2 Server Runables [8](#server-runables)](#server-runables)

[4.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 Local Function \#1 [8](#_Toc427318108)](#_Toc427318108)

[4.4.1.1 Design Rationale [8](#_Toc427318109)](#_Toc427318109)

[4.4.1.2 Processing [8](#_Toc427318110)](#_Toc427318110)

[4.5 GLOBAL Function/Macro Definitions
[8](#_Toc427318111)](#_Toc427318111)

[5 Known Limitations with Design
[9](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[10](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[11](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [12](#glossary)](#glossary)

[Appendix C References [13](#references)](#references)

# PwrLimr High-Level Description

*Refer FDD*

# Design details of software module

## Graphical representation of PwrLimr

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF019B_PwrLimr_Impl/doc/mediax/media/image1.PNG"
style="width:4.42361in;height:4.61775in" />

## Data Flow Diagram

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name      | Resolution             | Units | Value |
|--------------------|------------------------|-------|-------|
| MAXNRIVTRS_CNT_F32 | Single precision float | Cnt   | 2.0   |

-   For other constants, refer DataDict.m

# Software Component Implementation

## Sub-Module Functions

## Init: PwrLimrInit1

## Design Rationale

*Init function is present in DataDict.m file but not shown in FDD model.
Per the note in SF019B_PwrLimr/PwrLimr in the model, the init function
is responsible for updating the low pass filters used in the periodic
functions. Additionally, the init function starts up a timer used in the
‘Asst_Lmt_Condition_Determination’ block in the model.*

## Module Outputs

*Refer FDD*

###  [section]

## Per: PwrLimrPer1

## Design Rationale

*Refer FDD*

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Per: PwrLimrPer2

## Design Rationale

*GetTiSpan100MicroSec32bit returns elapsed time in counts where one
count is equal to 100 microseconds. Therefore, the value returned from
that function is divided by 10 to get the elapsed time in milliseconds.*

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

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
| 2           | MDD Guideline                                                                                                                                                           | EA4 01.00.00                   |
| 3           | EA4 [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 01.00.00                       |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc)   | 2.1                            |
| 5           | SF019B_PwrLimr_Design                                                                                                                                                   | See Synergy subproject version |

{% endraw %}