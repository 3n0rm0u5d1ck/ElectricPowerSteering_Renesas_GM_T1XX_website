---
layout: default
title: DataAndAdrPar Module Design Document
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**DataAndAdrPar**

**Mar 15, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |               |             |          |
|-----------------|---------------|-------------|----------|
| **Description** | **Author**    | **Version** | **Date** |
| Initial Version | Avinash James | 1           | 03/15/16 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 DataAndAdrPar & High-Level Description
[6](#dataandadrpar-high-level-description)](#dataandadrpar-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[*3.1* Graphical representation of DataAndAdrPar
[7](#graphical-representation-of-dataandadrpar)](#graphical-representation-of-dataandadrpar)

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

[5.1.1 Init:DataAndAdrParInit1
[9](#initdataandadrparinit1)](#initdataandadrparinit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Init:DataAndAdrParInit2
[9](#initdataandadrparinit2)](#initdataandadrparinit2)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Module Outputs [9](#module-outputs-1)](#module-outputs-1)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 ChkForECMBit28 [9](#chkforecmbit28)](#chkforecmbit28)

[5.4.1.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.4.1.2 Processing [9](#processing)](#processing)

[5.4.2 WrTestModeCtrReg [9](#wrtestmodectrreg)](#wrtestmodectrreg)

[5.4.2.1 Design Rationale
[10](#design-rationale-3)](#design-rationale-3)

[5.4.2.2 Processing [10](#processing-1)](#processing-1)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [10](#global-function-1)](#global-function-1)

[5.5.1.1 Design Rationale
[10](#design-rationale-4)](#design-rationale-4)

[5.5.1.2 Processing [10](#processing-2)](#processing-2)

[6 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# Introduction

## Purpose

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# DataAndAdrPar & High-Level Description

*See FDD*

# Design details of software module

## Graphical representation of DataAndAdrPar

## Data Flow Diagram

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM108A_DataAndAdrPar_Impl/doc/mediax/media/image1.png"
style="width:2in;height:1.3in" />

### Component level DFD

**N/A**

### Function level DFD

**N/A**

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                | Resolution | Units    | Value              |
|------------------------------|------------|----------|--------------------|
| VCIFERRSETBFRTEST_CNT_U32    | 1          | Counts   | ((uint32)1U\<\<0U) |
| ECMERRSETBFRTEST_CNT_U32     | 1          | Counts   | ((uint32)1U\<\<1U) |
| READOPERECMERR_CNT_U32       | 1          | Counts   | ((uint32)1U\<\<2U) |
| WROPERECMERR_CNT_U32         | 1          | Counts   | ((uint32)1U\<\<3U) |
| WROPERADRPARERR_CNT_U32      | 1          | Counts   | ((uint32)1U\<\<4U) |
| CLRERRSTSFLGFAIL_CNT_U32     | 1          | Counts   | ((uint32)1U\<\<5U) |
| TESTMODCTRLREGWRFAIL_CNT_U32 | 1          | Counts   | ((uint32)1U\<\<6U) |
| TOUT_MICROSEC_U32            | 1          | MicroSec | 2U                 |

# Software Component Implementation

## Sub-Module Functions

## Init:DataAndAdrParInit1

## Design Rationale

*Non-RTE Init function to verify the Data Parity Data Transfer Path
micro diagnostic. Refer FDD for more details*

## Module Outputs

*None*

## Init:DataAndAdrParInit2

## Design Rationale

*RTE empty Init function*

## Module Outputs

*None*

## Server Runables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## ChkForEcmBit28

|                      |                   |         |     |     |
|----------------------|-------------------|---------|-----|-----|
| **Function Name**    | ChkForEcmBit28    | Type    | Min | Max |
| **Arguments Passed** | None              |         |     |     |
| **Return Value**     | RetVal_Cnt_T_logl | Boolean | 0   | 1   |

## Design Rationale

Static function to check whether ECM bit was set or not within a time
out interval of max 2uSec

## Processing

To be called from DataAndAdrParInit1 function

## WrTestModeCtrReg

|                      |                  |        |     |            |
|----------------------|------------------|--------|-----|------------|
| **Function Name**    | WrTestModCtrlReg | Type   | Min | Max        |
| **Arguments Passed** | Val              | Uint32 | 0   | 0xFFFFFFFF |
|                      | ErrFlg_Cnt_T_u32 | Uint32 | 0   | 0xFFFFFFFF |
| **Return Value**     | None             |        |     |            |

## Design Rationale

Static function to write to the Test Mode Control register and verify
the write was successful

## Processing

To be called from DataAndAdrParInit1 function

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**       |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2 |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00      |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.0               |

{% endraw %}