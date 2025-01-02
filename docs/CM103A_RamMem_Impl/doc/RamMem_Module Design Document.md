---
layout: default
title: RamMem_Module Design Document
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**RamMem**

**Aug 23, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                             |                    |             |            |
|------------------------|---------------------|--------------|--------------|
| **Description**                                             | **Author**         | **Version** | **Date**   |
| Initial Version                                             | Selva Sengottaiyan | 1           | 04/06/16   |
| Created local functions for reducing cyclometric complexity | Selva Sengottaiyan | 2           | 06/26/2016 |
| Changed SPI ECC handling from interrupt to polling          | Avinash James      | 3           | 08/23/2016 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 RamMem & High-Level Description
[6](#rammem-high-level-description)](#rammem-high-level-description)

[*3* Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of RamMem
[7](#graphical-representation-of-rammem)](#graphical-representation-of-rammem)

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

[5.1.1 Init: RamMemInit1 [9](#init-rammeminit1)](#init-rammeminit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: RamMemPer1 [9](#per-rammemper1)](#per-rammemper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Module Outputs [9](#module-outputs-1)](#module-outputs-1)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.2.1 SpiDblBitEcc [9](#section)](#section)

[5.2.1.1 Design Rationale [9](#section-1)](#section-1)

[5.2.1.2 Processing [9](#section-2)](#section-2)

[5.2.2 RamMemLclRamSngBitEcc
[9](#rammemlclramsngbitecc)](#rammemlclramsngbitecc)

[5.2.2.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.2.2.2 Processing [9](#processing)](#processing)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [10](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale
[10](#design-rationale-3)](#design-rationale-3)

[5.4.1.2 Processing [10](#processing-1)](#processing-1)

[5.4.2 Local Function \#2 [10](#local-function-2)](#local-function-2)

[5.4.2.1 Design Rationale
[10](#design-rationale-4)](#design-rationale-4)

[5.4.2.2 Processing [10](#processing-2)](#processing-2)

[5.4.3 Local Function \#3 [10](#local-function-3)](#local-function-3)

[5.4.3.1 Design Rationale
[10](#design-rationale-5)](#design-rationale-5)

[5.4.3.2 Processing [10](#processing-3)](#processing-3)

[5.4.4 Local Function \#4 [11](#local-function-4)](#local-function-4)

[5.4.4.1 Design Rationale
[11](#design-rationale-6)](#design-rationale-6)

[5.4.4.2 Processing [11](#processing-4)](#processing-4)

[5.4.5 Local Function \#5 [11](#local-function-5)](#local-function-5)

[5.4.5.1 Design Rationale
[11](#design-rationale-7)](#design-rationale-7)

[5.4.5.2 Processing [11](#processing-5)](#processing-5)

[5.5 GLOBAL Function/Macro Definitions
[11](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [11](#global-function-1)](#global-function-1)

[5.5.1.1 Design Rationale
[11](#design-rationale-8)](#design-rationale-8)

[5.5.1.2 Processing [11](#processing-6)](#processing-6)

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

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# RamMem & High-Level Description

*See FDD*

# Design details of software module

## Graphical representation of RamMem

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM103A_RamMem_Impl/doc/mediax/media/image1.png"
style="width:2.80833in;height:2.28333in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name             | Resolution | Units | Value       |
|---------------------------|------------|-------|-------------|
| LCLRAMBASADR_CNT_U32      | 1          | Cnt   | 0xFEB80000U |
| VLDADRTESTBITMASK_CNT_U32 | 1          | Cnt   | 0xFFFE0000U |
| VLDADRTESTRES_CNT_U32     | 1          | Cnt   | 0x00060000U |
| WORDLINEADRMASK_CNT_U32   | 1          | Cnt   | 0xFFFFFF1FU |
| BNK0ERRCLRMASK_CNT_U32    | 1          | Cnt   | 0x00000001U |
| BNK1ERRCLRMASK_CNT_U32    | 1          | Cnt   | 0x00000002U |
| BNK2ERRCLRMASK_CNT_U32    | 1          | Cnt   | 0x00000004U |
| BNK3ERRCLRMASK_CNT_U32    | 1          | Cnt   | 0x00000008U |
| BNK0SNGBITERRMASK_CNT_U32 | 1          | Cnt   | 0x00000001U |
| BNK1SNGBITERRMASK_CNT_U32 | 1          | Cnt   | 0x00000100U |
| BNK2SNGBITERRMASK_CNT_U32 | 1          | Cnt   | 0x00010000U |
| BNK3SNGBITERRMASK_CNT_U32 | 1          | Cnt   | 0x01000000U |
|                           |            |       |             |

# Software Component Implementation

## Sub-Module Functions

## Init: RamMemInit1

## Design Rationale

## Module Outputs

*Refer to FDD*

## Per: RamMemPer1

## Design Rationale

## Module Outputs

*Refer to FDD*

## Server Runables 

## 

## 

## 

## RamMemLclRamSngBitEcc

## Design Rationale

Refer the FDD

## Processing

Refer the FDD

## Interrupt Functions

## Module Internal (Local) Functions

## Local Function \#1

|                      |                      |      |     |     |
|----------------------|----------------------|------|-----|-----|
| **Function Name**    | RamFailrModClassnChk | Type | Min | Max |
| **Arguments Passed** | None                 |      |     |     |
|                      |                      |      |     |     |
| **Return Value**     |                      |      |     |     |

## Design Rationale

Refer the FDD

## Processing

Refer the FDD

## Local Function \#2

|                      |                          |        |     |            |
|----------------------|--------------------------|--------|-----|------------|
| **Function Name**    | RamMemLclRamFailrChk     | Type   | Min | Max        |
| **Arguments Passed** | LclRamFailrAdr_Cnt_T_u32 | uint32 | 0   | 4294967295 |
|                      |                          |        |     |            |
| **Return Value**     |                          |        |     |            |

## Design Rationale

Refer the FDD

## Processing

Refer the FDD

## Local Function \#3

|                      |           |      |     |     |
|----------------------|-----------|------|-----|-----|
| **Function Name**    | SpiEccErr | Type | Min | Max |
| **Arguments Passed** | None      |      |     |     |
|                      |           |      |     |     |
| **Return Value**     |           |      |     |     |

## Design Rationale

Refer the FDD

## Processing

Refer the FDD

## Local Function \#4

|                      |          |      |     |     |
|----------------------|----------|------|-----|-----|
| **Function Name**    | FrEccErr | Type | Min | Max |
| **Arguments Passed** | None     |      |     |     |
|                      |          |      |     |     |
| **Return Value**     |          |      |     |     |

## Design Rationale

Refer the FDD

## Processing

Refer the FDD

## Local Function \#5

|                      |           |      |     |     |
|----------------------|-----------|------|-----|-----|
| **Function Name**    | CanEccErr | Type | Min | Max |
| **Arguments Passed** | None      |      |     |     |
|                      |           |      |     |     |
| **Return Value**     |           |      |     |     |

## Design Rationale

Refer the FDD

## Processing

Refer the FDD

## GLOBAL Function/Macro Definitions

## GLOBAL Function \#1

|                      |                   |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | (Exact name used) | Type                          | Min                           | Max                           |
| **Arguments Passed** | None              | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      |                   |                               |                               |                               |
| **Return Value**     |                   |                               |                               |                               |

## Design Rationale

## Processing

# Known Limitations with Design

Local RAM Single bit PIM for address store will be overwritten for each
banks which can be avoided by defining Pims for each memory block. Will
be reviewed POST IVER build

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01      |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1               |

{% endraw %}